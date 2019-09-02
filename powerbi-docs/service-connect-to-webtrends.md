---
title: Herstellen einer Verbindung mit Webtrends mithilfe von Power BI
description: Webtrends für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 25339052c0ddf410dab473a5a4a2fd9bbe445120
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184619"
---
# <a name="connect-to-webtrends-with-power-bi"></a>Herstellen einer Verbindung mit Webtrends mithilfe von Power BI
Das Webtrends-Inhaltspaket für Power BI enthält eine Vielzahl von Metriken, die ohne Konfiguration verfügbar sind, wie etwa die Anzahl der Seitenaufrufe und die Besuche nach Verkehrsquelle. Das Visualisieren Ihrer Webtrends-Daten in Power BI beginnt mit dem Herstellen der Verbindung mit Ihrem Webtrends-Konto. Sie können die bereitgestellten Dashboards und Berichte verwenden oder sie anpassen, um die für Sie wichtigsten Informationen hervorzuheben.  Die Daten werden automatisch einmal täglich aktualisiert.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie die Verbindung mit dem [Webtrends-Inhaltspaket für Power BI](https://app.powerbi.com/getdata/services/webtrends) her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-webtrends/getdata3.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-webtrends/services.png)
3. Wählen Sie **Webtrends** \> **Abrufen** aus.
   
   ![](media/service-connect-to-webtrends/webtrends.png)
4. Das Inhaltspaket stellt eine Verbindung mit einer bestimmten Webtrends-Profil-ID her. Nachstehend finden Sie weitere Informationen zum [Suchen dieses Parameters](#FindingParams).
   
   ![](media/service-connect-to-webtrends/parameters.png)
5. Geben Sie Ihre Webtrends-Anmeldeinformationen ein, um die Verbindung herzustellen. Beachten Sie, dass im Feld „Benutzername“ die Eingabe Ihres Kontos und Ihres Benutzernamens erwartet wird. Nachstehend finden Sie [weitere Informationen](#FindingParams).
   
   ![](media/service-connect-to-webtrends/creds.png)
6. Nach der Genehmigung wird der Importvorgang automatisch gestartet. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
   ![](media/service-connect-to-webtrends/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
<a name="Included"></a>

Das Webtrends-Inhaltspaket ruft Daten aus den folgenden Berichten ab:  

| Berichtsname | Berichts-ID |
| --- | --- |
| Key Metrics (Schlüsselmetrik) | |
| On-Site Searches (On-site-Suchvorgänge) |34awBVEP0P6 |
| Exit Pages (Ausgangsseiten) |7FshY8eP0P6 |
| Next Pages (Nächste Seiten) |CTd5rpeP0P6 |
| Previous Pages (Vorherige Seiten) |aSdOeaUgnP6 |
| Site Pages (Websiteseiten) |oOEWQj3sUo6 |
| Onsite Ads Clickthroughs (Durchklicks für On-site-Werbung) |41df19b6d9f |
| Cities (Städte) |aUuHskcP0P6 |
| Länder |JHWXJNcP0P6 |
| Visitors (Besucher) |xPcmTDDP0P6 |
| Visit Duration (Besuchsdauer) |U5KAyqdP0P6 |
| Search Phrases (Suchausdrücke) |IKYEDxIP0P6 |
| Traffic Sources (Datenverkehrsquellen) |JmttAoIP0P6 |
| Search Engines (Suchmaschinen) |yGz3gAGP0P6 |
| Entry Pages (Eingangsseiten) |i6LrkNVRUo6 |

>[!NOTE]
>Für SharePoint-Profile weichen die Metriknamen möglicherweise ein bisschen von dem ab, was in der Webtrends-Benutzeroberfläche angezeigt wird. Die folgende Zuordnung erfolgt, um die Konsistenz zwischen SharePoint- und Web-Profilen zu erhalten:   

    - Sessions (Sitzungen) = Visits (Besuche)  
    - New Users (Neue Benutzer) = New Visitors (Neue Besucher)  
    - Views per Session (Ansichten pro Sitzung) = Page Views per Visit (Seitenansichten pro Besuch)  
    - Avg Daily User Duration (Durchschnittliche tägliche Benutzerdauer) = Avg Time on Site per Visitor (Durchschnittliche Zeit auf der Website pro Besucher)  

## <a name="system-requirements"></a>Systemanforderungen
Das Inhaltspaket benötigt Zugriff auf ein Webtrends-Profil, in dem der [richtige Satz an Berichten](#Included) aktiviert ist.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Suchen von Parametern
Ihre Webtrends-Profil-ID finden Sie in der URL, nachdem Sie ein Profil ausgewählt haben:

![](media/service-connect-to-webtrends/webtrendsparameters.png)

Ihre Anmeldeinformationen sind die gleichen, die Sie für die Anmeldung bei Webtrends verwenden, allerdings wird die Eingabe von Konto und Benutzername in der gleichen Zeile, getrennt durch einen umgekehrten Schrägstrich, erwartet:

![](media/service-connect-to-webtrends/webtrendscreds.png)

## <a name="troubleshooting"></a>Problembehandlung
Nachdem Sie Ihre Anmeldeinformationen angegeben haben, kann beim Laden des Inhaltspakets ein Problem auftreten. Wenn während des Ladens die Meldung „Entschuldigung“ angezeigt wird, überprüfen Sie die folgenden Vorschläge zur Problembehandlung. Wenn das Problem weiterhin besteht, erstellen Sie unter https://support.powerbi.com ein Support-Ticket.

1. Die richtige Profil-ID wird verwendet (weitere Informationen finden Sie im Abschnitt [Suchen von Parametern](#FindingParams)).
2. Der Benutzer hat Zugriff auf die im Abschnitt [„Inhalt“](#Included) aufgelisteten Berichte.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](power-bi-overview.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

