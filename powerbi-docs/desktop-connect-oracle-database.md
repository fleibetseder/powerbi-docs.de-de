---
title: Herstellen einer Verbindung mit einer Oracle-Datenbank
description: Erforderliche Schritte und Downloads zum Verbinden von Oracle mit Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7c91095cf321fed56a0cb1c3c6bd1113f380a524
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878510"
---
# <a name="connect-to-an-oracle-database"></a>Herstellen einer Verbindung mit einer Oracle-Datenbank
Um über **Power BI Desktop** eine Verbindung mit einer Oracle-Datenbank herzustellen, muss auf dem Computer, auf dem Power BI Desktop ausgeführt wird, die richtigen Oracle-Clientsoftware installiert sein. Welche Oracle-Clientsoftware Sie verwenden, hängt davon ab, ob Sie für Power BI Desktop die **32-Bit**-Version oder die **64-Bit**-Version installiert haben.

**Unterstützte Versionen**: Oracle 9 und höher, Oracle-Clientsoftware Version 8.1.7 und höher.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Ermitteln der installierten Version von Power BI Desktop
Um zu bestimmen, welche Version von Power BI Desktop installiert ist, klicken Sie auf **Datei > Hilfe > Info**, und überprüfen Sie die Zeile **Version:** . In der folgenden Abbildung ist eine 64-Bit-Version von Power BI Desktop installiert:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installieren des Oracle-Clients
Verwenden Sie für **32-Bit**-Versionen von Power BI Desktop den folgenden Link, um den **32-Bit**-Oracle-Client herunterzuladen und zu installieren:

* [32-Bit-Oracle Data Access Components (ODAC) mit Oracle Developer Tools für Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Verwenden Sie für **64-Bit**-Versionen von Power BI Desktop den folgenden Link, um den **64-Bit**-Oracle-Client herunterzuladen und zu installieren:

* [64-Bit-ODAC 12c-Version 4 (12.1.0.2.4) für Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Herstellen einer Verbindung mit einer Oracle-Datenbank
Nachdem der entsprechende Oracle-Clienttreiber installiert wurde, können Sie eine Verbindung mit einer Oracle-Datenbank herstellen. Gehen Sie wie folgt vor, um die Verbindung herzustellen:

1. Wählen Sie im Fenster „Daten abrufen“ die Befehlsfolge **Datenbank > Oracle-Datenbank**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Geben Sie im daraufhin angezeigten Dialogfeld **Oracle-Datenbank** den Namen des Servers ein, und wählen Sie **Verbinden**. Wenn eine SID erforderlich ist, können Sie dies über folgendes Format festlegen: *Servername/SID*, wobei SID dem eindeutigen Namen der Datenbank entspricht. Wenn das Format *Servername/SID* nicht funktioniert, versuchen Sie es mit *Servername/Dienstname*, wobei Dienstname der beim Herstellen der Verbindung verwendete Alias ist.


   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Wenn Sie während dieses Schritts Probleme mit der Verbindung haben, verwenden Sie versuchsweise das folgenden Format im Feld „Servername“: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))
   
3. Wenn Sie Daten mithilfe einer nativen Datenbankabfrage importieren möchten, können Sie Ihre Abfrage in das Feld **SQL-Anweisung** einfügen. Dieses wird angezeigt, wenn Sie im Dialogfeld **Oracle-Datenbank** die **Erweiterten Optionen** einblenden.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Nachdem Sie die erforderlichen Informationen in das Dialogfeld „Oracle-Datenbank“ eingegeben haben (einschließlich aller optionalen Informationen wie SID oder nativer Datenbankabfrage), wählen Sie **OK**, um die Verbindung herzustellen.
5. Wenn für die Anmeldung bei der Oracle-Datenbank Anmeldeinformationen erforderlich sind, geben Sie diese bei Aufforderung in das Dialogfeld ein.


## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Power BI Desktop aus dem Microsoft Store heruntergeladen haben, können Sie möglicherweise aufgrund eines Problems mit dem Oracle-Treiber keine Verbindung zu Oracle-Datenbanken herstellen. Wenn dieses Problem auftritt, wird die Fehlermeldung „Object reference not set“ (Der Objektverweis ist nicht festgelegt.) zurückgegeben. Führen Sie einen der folgenden Schritte aus, um das Problem zu beheben:

* Laden Sie stattdessen Power BI Desktop von https://powerbi.microsoft.com/desktop herunter.

* Wenn Sie die Version aus dem Microsoft Store verwenden möchten: Kopieren Sie auf Ihrem lokalen Computer die Datei „oraons.dll“ von _12.X.X.X\client_X_ nach _12.X.X.X\client_X\bin_. Das X steht für Versions- und Verzeichnisnummern.

Wenn Ihnen im Power BI Gateway beim Herstellen einer Verbindung mit einer Oracle-Datenbank die Fehlermeldung *Object reference not set* (Der Objektverweis ist nicht festgelegt) angezeigt wird, können Sie das Problem möglicherweise lösen, indem Sie die Anweisungen im Artikel [Verwalten der Datenquelle – Oracle](service-gateway-onprem-manage-oracle.md) befolgen.
