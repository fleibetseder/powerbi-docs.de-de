---
title: Migrieren von Inhalten aus Power BI Embedded-Arbeitsbereichsammlungen zu Power BI
description: "Erfahren Sie, wie Sie Inhalte aus Power BI Embedded in den Power BI-Dienst migrieren und die Vorteile für das Einbetten in Apps nutzen."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 07/21/2017
ms.author: asaxton
ms.openlocfilehash: 430f1d1a49e510bac66c448b2dceaad1f2537073
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-migrate-power-bi-embedded-workspace-collection-content-to-power-bi"></a>Migrieren von Inhalten aus Power BI Embedded-Arbeitsbereichsammlungen zu Power BI
Erfahren Sie, wie Sie Inhalte aus Power BI Embedded in den Power BI-Dienst migrieren und die Vorteile für das Einbetten in Apps nutzen.

Microsoft hat vor Kurzem [Power BI Premium vorgestellt](https://powerbi.microsoft.com/blog/microsoft-accelerates-modern-bi-adoption-with-power-bi-premium/), ein neues kapazitätsbasiertes Lizenzierungsmodell, das die Flexibilität der Benutzer beim Zugriff, der Freigabe und dem Verteilen von Inhalten erhöht. Das Angebot bietet zusätzliche Skalierbarkeit und Leistung für den Power BI-Dienst.

Mit der Einführung von Power BI Premium werden Power BI Embedded und der Power BI-Dienst zusammengeführt, um die Einbettung von Power BI-Inhalten in Apps zu optimieren. Dies bedeutet, dass Ihnen eine API-Oberfläche, ein einheitlicher Satz von Funktionen und Zugriff auf die neuesten Power BI-Funktionen (z.B. Dashboards, Gateways und App-Arbeitsbereiche) zur Verfügung stehen, wenn Sie Inhalte einbetten. In Zukunft können Sie mit Power BI Desktop beginnen und zu einer Bereitstellung mit Power BI Premium wechseln. Dies wird im zweiten Quartal 2017 allgemein verfügbar sein.

Der aktuelle Power BI Embedded-Dienst ist für einen begrenzten Zeitraum nach der allgemeinen Verfügbarkeit des zusammengeführten Angebots weiterhin verfügbar: Enterprise Agreement-Kunden haben bis zum Auslaufen ihrer vorhandenen Verträge Zugriff. Kunden, die Power BI Embedded über Direct- oder CSP-Kanäle erworben haben, haben nach der allgemeinen Verfügbarkeit von Power BI Premium ein Jahr lang Zugriff.  Dieser Artikel bietet hilfreiche Informationen zur Migration vom Azure-Dienst zum Power BI-Dienst sowie Erläuterungen zu den zu erwartenden Änderungen in Ihrer Anwendung.

> [!IMPORTANT]
> Für die Migration ist eine Abhängigkeit vom Power BI-Dienst vorhanden, die Benutzer Ihrer Anwendung sind aber nicht von Power BI abhängig, wenn sie ein **Einbettungstoken verwenden**. Sie müssen sich nicht für Power BI registrieren, um die eingebetteten Inhalte in der Anwendung anzuzeigen. Sie können diesen Einbettungsansatz verwenden, um Nicht-Power BI-Benutzern zuzuarbeiten.
> 
> 

![](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

## <a name="prepare-for-the-migration"></a>Vorbereiten der Migration
Es gibt einige Schritte, die Sie zur Vorbereitung der Migration vom Power BI Embedded Azure-Dienst zum Power BI-Dienst ausführen müssen. Sie benötigen einen verfügbaren Mandanten sowie einen Benutzer mit einer Power BI Pro-Lizenz.

1. Stellen Sie sicher, dass Sie Zugriff auf einen Azure Active Directory-Mandanten (Azure AD) haben.
   
    Sie müssen bestimmen, welches Mandantensetup verwendet werden soll.
   
   * Verwenden Sie Ihren vorhandenen, unternehmensbezogenen Power BI-Mandanten?
   * Verwenden Sie einen separaten Mandanten für Ihre Anwendung?
   * Verwenden Sie einen separaten Mandanten pro Kunde?
     
     Wenn Sie einen neuen Mandanten für Ihre Anwendung oder jeden Kunden erstellen möchten, finden Sie unter [Erstellen eines Azure Active Directory-Mandanten](create-an-azure-active-directory-tenant.md) oder [Vorgehensweise: Abrufen eines Azure Active Directory-Mandanten](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant) weitere Informationen dazu.
2. Erstellen Sie einen Benutzer in diesem neuen Mandanten, der als Ihr „Master“-Anwendungskonto fungiert. Das Konto muss für Power BI registriert werden und muss eine Power BI Pro-Lizenz zugewiesen bekommen.

## <a name="accounts-within-azure-ad"></a>Konten in Azure AD
Die folgenden Konten müssen in Ihrem Mandanten vorhanden sein.

> [!NOTE]
> Diese Konten benötigen Power BI Pro-Lizenzen, um App-Arbeitsbereiche nutzen zu können.
> 
> 

1. Ein Mandantenadministrator
   
    Dieser Benutzer sollte Mitglied aller App-Arbeitsbereiche sein, die zum Einbetten erstellt werden.
2. Konten für Analysten, die Inhalte erstellen
   
    Diese Benutzer sollten nach Bedarf App-Arbeitsbereichen zugewiesen werden.
3. Ein Anwendungs-*Master*-Benutzerkonto oder Dienstkonto.
   
    Das Back-End der Anwendung speichert die Anmeldeinformationen für dieses Konto und ruft damit ein Azure AD-Token für die Verwendung mit Power BI-APIs ab. Mit diesem Konto wird das Einbettungstoken für die Anwendung generiert. Dieses Konto muss einem Administrator der App-Arbeitsbereiche gehören, die für die Einbettung erstellt werden.
   
   > [!NOTE]
   > Dies ist lediglich ein herkömmliches Benutzerkonto in Ihrer Organisation, das für Einbettungszwecke verwendet wird.
   > 
   > 

## <a name="app-registration-and-permissions"></a>App-Registrierung und Berechtigungen
Sie müssen eine Anwendung in Azure AD registrieren und bestimmte Berechtigungen erteilen.

### <a name="register-an-application"></a>Registrieren einer Anwendung
Sie müssen Ihre Anwendung bei Azure AD registrieren, um REST-API-Aufrufe ausführen zu können. Dazu müssen Sie nicht nur die Power BI-Seite für die App-Registrierung besuchen, sondern auch im Azure-Portal weitere Konfigurationsschritte ausführen. Weitere Informationen finden Sie unter [Registrieren einer Azure AD-App zum Einbetten von Power BI-Inhalten](register-app.md).

Sie müssen die Anwendung mithilfe des **Hauptkontos** der Anwendung registrieren.

## <a name="create-app-workspaces-required"></a>Erstellen von App-Arbeitsbereichen (erforderlich)
Sie können App-Arbeitsbereiche nutzen, um eine bessere Isolation bereitzustellen, wenn Ihre Anwendung von mehreren Kunden verwendet wird. Dashboards und Berichte werden dann zwischen Ihren Kunden isoliert. Sie können anschließend ein Power BI-Konto pro App-Arbeitsbereich verwenden, um die Anwendungsnutzung für die Kunden noch weiter zu isolieren.

> [!IMPORTANT]
> Sie können in einem persönlichen Arbeitsbereich nicht das Einbetten in Nicht-Power BI-Benutzer nutzen.
> 
> 

Sie benötigen einen Benutzer, der über eine Pro-Lizenz verfügt, um einen App-Arbeitsbereich in Power BI zu erstellen. Der Power BI-Benutzer, der den App-Arbeitsbereich erstellt, ist standardmäßig der Administrator dieses Arbeitsbereichs.

> [!NOTE]
> Das *Hauptkonto* der Anwendung muss ein Administrator des Arbeitsbereichs sein.
> 
> 

## <a name="content-migration"></a>Migration von Inhalten
Das Migrieren Ihrer Inhalte aus Ihren Arbeitsbereichsammlungen für den Power BI-Dienst kann parallel zur aktuellen Projektmappe ausgeführt werden und erfordert keine Ausfallzeiten.

Ein **Migrationstool** steht Ihnen zur Verfügung, um Sie beim Kopieren von Inhalt aus Power BI Embedded in Power BI-Dienst zu unterstützen. Insbesondere, wenn Sie viel Inhalt haben. Weitere Informationen finden Sie unter [Power BI Embedded Migrationstool](migrate-tool.md).

Die Migration von Inhalten verwendet hauptsächlich zwei APIs.

1. Download PBIX: Diese API kann PBIX-Dateien herunterladen, die auf Power BI nach Oktober 2016 hochgeladen wurden.
2. Import PBIX: Diese API lädt alle PBIX in Power BI hoch.

Einige verbundene Codeausschnitte finden Sie unter [Codeausschnitte zum Migrieren von Inhalt von Power BI Embedded](migrate-code-snippets.md).

### <a name="report-types"></a>Berichtstypen
Es gibt mehrere Berichtstypen, jeder erfordert einen etwas anderen Migrationsflow.

#### <a name="cached-dataset--report"></a>Zwischengespeichertes Dataset & Bericht
Zwischengespeicherte Datasets finden Sie in PBIX-Dateien, die Daten im Gegensatz zu einer Liveverbindung oder DirectQuery-Verbindung importiert hatten.

**Flow**

1. Herunterladen PBIX-API Aufrufen im PaaS-Arbeitsbereich.
2. Speichern Sie die PBIX.
3. Rufen Sie Import PBIX SaaS-Arbeitsbereich auf.

#### <a name="directquery-dataset--report"></a>DirectQuery-Dataset & Bericht
**Flow**

1. Rufen Sie GET-https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources auf, und speichern Sie die empfangene Verbindungszeichenfolge.
2. Herunterladen PBIX-API Aufrufen im PaaS-Arbeitsbereich.
3. Speichern Sie die PBIX.
4. Rufen Sie Import PBIX SaaS-Arbeitsbereich auf.
5. Aktualisieren Sie die Verbindungszeichenfolge durch das Aufrufen von – POST https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections
6. Rufen Sie GW-ID und Datasource-ID auf, indem Sie GET https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources aufrufen
7. Aktualisieren Sie die Anmeldeinformationen eines Benutzers, indem Sie PATCH https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id} aufrufen.

#### <a name="old-dataset--reports"></a>Altes Dataset & Bericht
Hierbei handelt es sich um Datasets/Berichte, die vor Oktober 2016 erstellt wurden. Das Herunterladen von PBIX unterstützt keine PBIXs, die vor Oktober 2016 hochgeladen wurden

**Flow**

1. Rufen Sie PBIX aus Ihrer Entwicklungsumgebung (die interne Quellcodeverwaltung) ab.
2. Rufen Sie Import PBIX SaaS-Arbeitsbereich auf.

#### <a name="push-dataset--report"></a>Push-Dataset & Bericht
PBIX herunterladen unterstützt keine *Push-API*-Datasets. Daten von Datasets per Push-API können nicht von PaaS zu SaaS portiert werden.

**Flow**

1. Rufen Sie die „Create Dataset“-API (Dataset erstellen) mit Dataset-Json auf, um Datasets im Arbeitsbereich „SaaS“ zu erstellen.
2. Erstellen Sie für das erstellte Dataset * einen neuen Bericht.

Es ist möglich, einige Problemumgehungen zum Migrieren des Push-Vorgangs mit API-Bericht von PaaS zu SaaS zu verwenden, indem Sie das Folgende versuchen.

1. Hochladen von einigen Dummy-PBIX in den PaaS-Arbeitsbereich.
2. Klonen Sie den Push-API-Bericht, und verbinden Sie diesen mit dem Dummy-PBIX aus Schritt 1.
3. Push-API-Bericht mit dem Dummy-PBIX herunterladen.
4. Laden Sie den Dummy-PBIX in Ihren SaaS-Arbeitsbereich hoch.
5. Erstellen Sie ein Push-Dataset in Ihrem SaaS-Arbeitsbereich.
6. Binden Sie den Bericht erneut an das Push-API-Dataset.

## <a name="create-and-upload-new-reports"></a>Erstellen und Hochladen von Berichten
Zusätzlich zu dem Inhalt, den Sie vom Power BI Embedded Azure-Dienst migriert haben, können Sie Ihre Berichte und Datasets mit Power BI Desktop erstellen, und dann veröffentlichen Sie diese Berichte in einem App-Arbeitsbereich. Der Endbenutzer, der die Berichte veröffentlicht, muss über eine Power BI Pro-Lizenz verfügen, damit er einen App-Arbeitsbereich veröffentlichen kann.

## <a name="rebuild-your-application"></a>Erneutes Erstellen der Anwendung
1. Sie müssen Ihre Anwendung ändern, um die Power BI-REST-APIs und den Speicherort des Berichts in „powerbi.com“ zu verwenden.
2. Erstellen Sie die AuthN-/AuthZ-Authentifizierung unter Verwendung des *Masterkontos* für Ihre Anwendung neu. Sie können dabei ein [Einbettungstoken](https://msdn.microsoft.com/library/mt784614.aspx) verwenden, damit dieser Benutzer im Auftrag anderer Benutzer handeln kann.
3. Betten Sie Ihre Berichte auf „powerbi.com“ in Ihrer Anwendung ein.

## <a name="map-your-users-to-a-power-bi-user"></a>Zuordnen der Benutzer zu einem Power BI-Benutzer
Innerhalb Ihrer Anwendung ordnen Sie Benutzer, die Sie in der Anwendung verwalten, für Ihre Anwendung *Masteranmeldeinformationen* für Power BI zu. Die Anmeldeinformationen für dieses Power BI-*Masterkonto* werden in Ihrer Anwendung gespeichert und zum Erstellen von Einbettungstoken verwendet.

## <a name="what-to-do-when-you-are-ready-for-production"></a>Wenn Sie bereit für die Produktionsphase sind
Wenn Sie in die Produktionsphase wechseln möchten, müssen Sie die folgenden Schritte ausführen.

* Wenn Sie einen separaten Mandanten für die Entwicklung verwenden, müssen Sie sicherstellen, dass Ihre App-Arbeitsbereiche, zusammen mit Dashboards und Berichten, in der Produktionsumgebung verfügbar sind. Sie müssen zudem sicherstellen, dass Sie die Anwendung in Azure AD für Ihren Produktionsmandanten erstellt haben, und dass Sie die entsprechenden App-Berechtigungen zugewiesen haben, wie in Schritt 1 angegeben.
* Erwerben Sie eine Kapazität, die Ihren Anforderungen entspricht. Sie können das [Whitepaper zur Kapazitätsplanung der eingebetteten Analyse](https://aka.ms/pbiewhitepaper) nutzen, um zu erfahren, was Sie möglicherweise benötigen. Sie können das Produkt im [Administratorcenter von Office 365](https://portal.office.com/adminportal/home#/catalog) erwerben.
  
  > [AZURE.INFORMATION] Informationen zum Erwerb von Power BI Premium finden Sie unter [Erwerben von Power BI Premium](../service-admin-premium-purchase.md).
  > 
  > 
* Bearbeiten Sie den App-Arbeitsbereich, und weisen Sie diesen einer Premium-Kapazität unter „Erweitert“ zu.
  
    ![](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity.png)
* Stellen Sie die aktualisierte Anwendung für die Produktion bereit, und beginnen Sie mit dem Einbetten von Berichten aus dem Power BI-Dienst.

## <a name="after-migration"></a>Nach der Migration
Sie sollten in Azure einige Bereinigungsschritte ausführen.

* Entfernen Sie alle Arbeitsbereiche aus der bereitgestellten Lösung im Azure-Dienst von Power BI Embedded.
* Löschen Sie alle Arbeitsbereichsammlungen, die in Azure vorhanden sind.

## <a name="next-steps"></a>Nächste Schritte
[Einbetten mit Power BI](embedding.md)  
[Power BI Embedded-Migrationstool](migrate-tool.md)  
[Codeausschnitte zum Migrieren von Inhalt von Power BI Embedded](migrate-code-snippets.md)  
[Wie soll ich Power BI-Dashboards, -Berichte und -Kacheln einbetten?](embedding-content.md)  
[Power BI Premium – Beschreibung](../service-premium.md)  
[JavaScript-API-Git-Repository](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI-C#-Git-Repository](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript-Einbettungsbeispiel](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Whitepaper zur Kapazitätsplanung der eingebetteten Analyse](https://aka.ms/pbiewhitepaper)  
[Power BI Premium-Whitepaper](https://aka.ms/pbipremiumwhitepaper)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
