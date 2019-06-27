---
title: Dynamische Sicherheit auf Zeilenebene mit dem tabellarischen Modell von Analysis Services in Power BI
description: Dynamische Sicherheit auf Zeilenebene mit dem tabellarischen Modell von Analysis Services
author: selvarms
manager: amitaro
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/28/2019
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 28fe39788dab6f22845d3ffcb7115fb1da5cb268
ms.sourcegitcommit: c122c1a8c9f502a78ccecd32d2708ab2342409f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66826653"
---
# <a name="dynamic-row-level-security-with-analysis-services-tabular-model"></a>Dynamische Sicherheit auf Zeilenebene mit dem tabellarischen Modell von Analysis Services

In diesem Tutorial verwenden Sie ein Beispieldataset, um die unten aufgeführten Schritte durchzuführen. Dabei erhalten Sie Informationen zur [**Sicherheit auf Zeilenebene**](service-admin-rls.md) in einem **Analysis Services-Tabellenmodell** und verwenden dieses in einem Power BI-Bericht. 

* Erstellen einer neuen Sicherheitstabelle in der [**AdventureworksDW2012**-Datenbank](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Erstellen des tabellarischen Modells mit erforderlichen Fakten- und Dimensionstabellen
* Definieren von Benutzerrollen und -berechtigungen
* Bereitstellen des Modells auf einer **Analysis Services-Tabelleninstanz**
* Erstellen eines Power BI Desktop-Berichts, der Daten anzeigt, die genau auf den Benutzer zugeschnitten sind, der auf den Bericht zugreift
* Bereitstellen des Berichts im **Power BI-Dienst**
* Erstellen eines neuen Dashboards basierend auf dem Bericht
* Freigeben des Dashboards an Ihre Kollegen 

Für dieses Tutorial ist die [**AdventureworksDW2012**-Datenbank](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) erforderlich.

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Aufgabe 1: Erstellen einer Benutzersicherheitstabelle und Definieren der Datenbeziehung

Es gibt viele Artikel, in denen das Definieren der dynamischen Sicherheit auf Zeilenebene mit dem **SQL Server Analysis Services-Tabellenmodell** beschrieben wird. In unserem Beispiel folgen wir dem Artikel [Implement Dynamic Security by Using Row Filters (Implementieren dynamischer Sicherheit mithilfe von Zeilenfiltern)](https://msdn.microsoft.com/library/hh479759.aspx). 

Für die hier aufgeführten Schritte ist die relationale Datenbank **AdventureworksDW2012** erforderlich.

1. Erstellen Sie in **AdventureworksDW2012** wie unten gezeigt die Tabelle **DimUserSecurity**. Sie können [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) zum Erstellen der Tabelle verwenden.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

2. Nachdem Sie die Tabelle erstellt und gespeichert haben, müssen Sie die Beziehung zwischen der **SalesTerritoryID**-Spalte der **DimUserSecurity**-Tabelle und der **SalesTerritoryKey**-Spalte der **DimSalesTerritory**-Tabelle erstellen. Dies wird in der folgenden Abbildung gezeigt. 

   Klicken Sie in **SSMS** mit der rechten Maustaste auf die Tabelle **DimUserSecurity**, und klicken Sie auf **Design** (Entwurf). Klicken Sie dann auf **Table Designer > Relationships...** (Tabellen-Designer > Beziehungen...). Speichern Sie anschließend die Tabelle.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

3. Fügen Sie der Tabelle Benutzer hinzu. Klicken Sie dazu mit der rechten Maustaste auf die Tabelle **DimUserSecurity**, und wählen Sie **Edit Top 200 Rows** (Oberste 200 Zeilen bearbeiten) aus. Wenn Sie Benutzer hinzugefügt haben, sollte die Tabelle **DimUserSecurity** in etwa wie folgt aussehen, nur mit eigenen Benutzern:
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   Sie werden in den nächsten Aufgaben zu diesen Benutzern zurückkehren.

4. Als Nächstes führen wir einen *inneren Join* mit der **DimSalesTerritory**-Tabelle durch, die Details zur Region anzeigt, die dem Benutzer zugeordnet ist. Der folgende SQL-Code führt den *inneren Join* durch, und das folgende Bild zeigt, wie die Tabelle danach aussieht.
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)

   Auf dem Bild wird gezeigt, wer für jede Vertriebsregion zuständig ist. Dies ist aufgrund der in **Schritt 2** erstellten Beziehung möglich. Sie sehen z. B., dass **Jon Dow** für **Australien** zuständig ist. 

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Aufgabe 2: Erstellen des tabellarischen Modells mit Fakten- und Dimensionstabellen

1. Sobald Ihr relationales Data Warehouse vorhanden ist, müssen Sie das Tabellenmodell definieren. Das Modell kann mit [**SQL Server Data Tools (SSDT)** ](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools) erstellt werden. Weitere Informationen finden Sie unter [Create a New Tabular Model Project (Erstellen eines neuen Tabellenmodells)](https://msdn.microsoft.com/library/hh231689.aspx).

2. Importieren Sie alle erforderlichen Tabellen so wie unten dargestellt in das Modell.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

3. Nachdem Sie die erforderlichen Tabellen importiert haben, müssen Sie eine Rolle namens **SalesTerritoryUsers** mit **Leseberechtigung** definieren. Klicken Sie in SSDT auf das Menü **Model** (Modell) und anschließend auf **Roles** (Rollen). Klicken Sie im Dialogfeld **Role Manager** (Rollen-Manager) auf **New** (Neu).

4. Fügen Sie auf der Registerkarte **Members** (Mitglieder) im **Rollen-Manager** die Benutzer hinzu, die Sie in der **DimUserSecurity**-Tabelle in **Aufgabe 1 – Schritt 3** definiert haben.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

5. Fügen Sie anschließend die korrekten Funktionen für die Tabellen **DimSalesTerritory** und **DimUserSecurity** hinzu, wie unten unter der Registerkarte **Zeilenfilter** gezeigt.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

6. In diesem Schritt verwenden wir die **LOOKUPVALUE**-Funktion zum Zurückgeben von Werten für eine Spalte, in der der Windows-Benutzername dem von der Funktion **USERNAME** zurückgegebenen Benutzernamen entspricht. Dann können Sie die Abfrage einschränken, sodass die von **LOOKUPVALUE** zurückgegebenen Werte den Werten in derselben oder einer verwandten Tabelle entsprechen. Geben Sie in der Spalte **DAX Filter** die folgende Formel ein:
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])

    In dieser Formel gibt die **LOOKUPVALUE**-Funktion alle Werte für die Spalte **DimUserSecurity[SalesTerritoryID]** zurück, wobei **DimUserSecurity[UserName]** dem Namen des gegenwärtig eingeloggten Windowsbenutzers und **DimUserSecurity[SalesTerritoryID]** **DimSalesTerritory[SalesTerritoryKey]** entspricht.
   
    > [!IMPORTANT]
    > Beachten Sie, dass die DAX-Funktion [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax) nicht unterstützt wird, wenn Sie Sicherheit auf Zeilenebene verwenden.

   Die Rückgabe von **LOOKUPVALUE** von SalesTerritoryKey wird verwendet, um die Zeilen, die in **DimSalesTerritory** angezeigt werden, zu beschränken. Es werden nur Zeilen angezeigt, in denen sich der **SalesTerritoryKey**-Wert in den IDs befindet, die von der **LOOKUPVALUE**-Funktion zurückgegeben werden.

7. Fügen Sie für die Tabelle **DimUserSecurity** in der **DAX Filter**-Spalte die folgende Formel ein:
   
       =FALSE()

    Diese Formel gibt an, dass alle Spalten in `false` aufgelöst werden soll. Das bedeutet, dass Spalten in der Tabelle **DimUserSecurity** nicht abgefragt werden können.

8. Nun müssen Sie das Modell verarbeiten und bereitstellen. Weitere Informationen finden Sie im [Artikel zum Bereitstellen](https://msdn.microsoft.com/library/hh231693.aspx).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Aufgabe 3: Hinzufügen von Datenquellen im lokalen Datengateway

Sobald das tabellarische Modell bereitgestellt und für die Verwendung bereit ist, müssen Sie eine Datenquellenverbindung mit Ihrem lokalen tabellarischen Analysis Services-Server hinzufügen.

1. Sie müssen ein **[lokales Datengateway](service-gateway-onprem.md)** in Ihrer Umgebung installiert und konfiguriert haben, damit der **Power BI-Dienst** auf Ihren lokalen Analysedienst zugreifen kann.

2. Wenn das Gateway ordnungsgemäß konfiguriert wurde, müssen Sie eine Datenquellenverbindung für die **Analysis Services**-Tabelleninstanz erstellen. Weitere Informationen finden Sie unter [Verwalten Ihrer Datenquelle – Analysis Services](service-gateway-enterprise-manage-ssas.md).
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

  Wenn der vorherige Schritt abgeschlossen wurde, ist das Gateway konfiguriert und kann mit der lokalen **Analysis Services**-Datenquelle interagieren.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Aufgabe 4: Erstellen eines Berichts basierend auf einem Analysis Services-Tabellenmodell mit Power BI Desktop

1. Starten Sie **Power BI Desktop** , und wählen Sie **Daten abrufen > Database** aus.

2. Wählen Sie aus der Liste der Datenquellen die **SQL Server Analysis Services-Datenbank**, und klicken Sie auf **Verbinden**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

3. Geben Sie Ihre Details zur **Analysis Services**-Tabelleninstanz ein, und wählen Sie **Live verbinden** aus. Wählen Sie dann **OK** aus. Mit **Power BI** funktioniert die dynamische Sicherheit nur mit einer **Liveverbindung**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

4. Sie sehen, dass sich das bereitgestellte Modell in der **Analysis Services**-Instanz befindet. Wählen Sie das jeweilige Modell, und klicken Sie auf **OK**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   **Power BI Desktop** zeigt nun alle verfügbaren Felder rechts neben dem Zeichenbereich im Bereich **Felder** an.

5. Wählen Sie rechts im Bereich **Felder** das **SalesAmount**-Measure aus der **FactInternetSales**-Tabelle und die **SalesTerritoryRegion**-Dimension aus der **SalesTerritory**-Tabelle aus.

6. Wir wollen diesen Bericht einfach halten, also fügen wir im Moment keine weiteren Spalten hinzu. Ändern Sie die Visualisierung in ein **Ringdiagramm**, um die Datendarstellung aussagekräftiger zu gestalten.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

7. Wenn Ihr Bericht fertig ist, können Sie ihn direkt im Power BI-Portal veröffentlichen. Wählen Sie auf dem Menüband **Start** in **Power BI Desktop** **Veröffentlichen** aus.

## <a name="task-5-create-and-share-a-dashboard"></a>Aufgabe 5: Erstellen und Freigeben eines Dashboards

1. Sie haben bis jetzt einen Bericht erstellt und ihn im **Power BI-Dienst** veröffentlicht. Jetzt können Sie das vorherig erstellte Beispiel verwenden, um ein Szenario zum Sichern von Modellen zu veranschaulichen.
   
   In seiner Rolle als **Vertriebsleiter** kann Sumit Daten von allen verschiedenen Vertriebsregionen anzeigen. Er erstellt also diesen Bericht (der Bericht, der in den vorherigen Schritten erstellt wurde) und veröffentlicht ihn im Power BI-Dienst.
   
   Wenn er den Bericht veröffentlicht hat, erstellt er basierend auf diesem Bericht ein Dashboard im Power BI-Dienst namens **TabularDynamicSec**. Beachten Sie in der folgenden Abbildung, dass Sumit die Daten aus allen Vertriebsregionen anzeigen kann.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

2. Sumit gibt das Dashboard für seinen Kollegen Jon Doe frei, der für den Vertrieb in der Region Australien zuständig ist.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

3. Wenn Jon Doe sich im **Power BI-Dienst** anmeldet und das freigegebene Dashboard anzeigt, dass Sumit erstellt hat, sollte er **nur** den Vertrieb für seine Region sehen. 
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)

    Herzlichen Glückwunsch! Der **Power BI-Dienst** zeigt die dynamische Sicherheit auf Zeilenebene an, die im lokalen **Analysis Services**-Tabellenmodell definiert wurde. Power BI verwendet die Eigenschaft **EffectiveUserName**, um die aktuellen Power BI-Benutzeranmeldeinformationen zum Ausführen der Abfragen an die lokale Datenquelle zu senden.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Aufgabe 6: Verstehen der Hintergrundvorgänge

Bei dieser Aufgabe wird davon ausgegangen, dass Sie sich mit dem [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler) auskennen, da Sie eine SQL Server Profiler-Ablaufverfolgung auf Ihrer lokalen SSAS-Tabelleninstanz erfassen müssen.

1. Sobald der Benutzer (Jon Doe) auf das Dashboard im Power BI-Dienst zugreift, wird die Sitzung initialisiert. Wie Sie sehen, nimmt die **SalesTerritoryUsers**-Rolle unmittelbar den effektiven Benutzernamen **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>** an.
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>

2. Basierend auf den effektiven Anforderungen des Benutzernamens konvertiert Analysis Services die Anforderung in den tatsächlichen Benutzernamen moonneo\jondoe, nachdem die lokale Active Directory Domain Services-Instanz abgefragt wurde. Sobald **Analysis Services** die Anmeldeinformationen abgefragt hat, gibt **Analysis Services** die Daten zurück, die der Benutzer anzeigen und auf die er zugreifen darf.

3. Wenn im Dashboard weitere Aktivitäten auftreten, z.B. falls Jon Doe vom Dashboard auf den zugrundeliegenden Report zugreift, können Sie mit SQL Profiler eine spezifische Abfrage anzeigen, die als DAX-Abfrage wieder zum Analysis Services-Tabellenmodell zurückkehrt.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

4. Sie können unten auch die DAX-Abfrage sehen, die ausgeführt wird, um die Berichtsdaten aufzufüllen.
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Überlegungen

* Die lokale Sicherheit auf Zeilenebene mit Power BI ist nur mit einer Liveverbindung verfügbar.

* Alle Änderungen an Daten, die nach der Modellverarbeitung vorgenommen werden, stehen in Power BI unmittelbar allen Benutzern zur Verfügung, die über eine **Liveverbindung** auf den Bericht zugreifen.

