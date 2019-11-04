---
title: Herstellen einer Verbindung mit Ziosk Survey Analytics mithilfe von Power BI
description: Ziosk für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e16264c3cf5b6d361353c18ba9eb666fd00ce5d
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060462"
---
# <a name="connect-to-ziosk-survey-analytics-with-power-bi"></a>Herstellen einer Verbindung mit Ziosk Survey Analytics mithilfe von Power BI
Das Ziosk Survey Analytics-Inhaltspaket für Power BI bietet Restaurants mit Ziosk-Tablets beispiellosen Zugriff auf durch Ziosk Survey-Daten bereitgestellte Informationen, einschließlich der Segmentierung nach Tag, Ort, Mitarbeiter etc.

Stellen Sie eine Verbindung mit dem [Ziosk Survey Analytics-Inhaltspaket](https://app.powerbi.com/getdata/services/ziosk-survey-analytics) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.  
   
    ![](media/service-connect-to-ziosk/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.  
   
    ![](media/service-connect-to-ziosk/services.png)
3. Wählen Sie **Ziosk Survey Analytics** und anschließend **Abrufen** aus.  
   
    ![](media/service-connect-to-ziosk/ziosk.png)
4. Wählen Sie **OAuth 2** und anschließend **Anmelden** aus. Geben Sie Ihre Ziosk-Anmeldeinformationen an, wenn Sie dazu aufgefordert werden.
   
    ![](media/service-connect-to-ziosk/creds.png)
   
    ![](media/service-connect-to-ziosk/creds2.png)
5. Sobald Sie verbunden sind, werden ein Dashboard, ein Bericht und ein Dataset automatisch geladen. Anschließend werden die Kacheln mit Daten aus Ihrem Ziosk-Konto aktualisiert.
   
    ![](media/service-connect-to-ziosk/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Das Inhaltspaket umfasst Daten aus den folgenden Tabellen:  

    - Alcohol Category (Alkoholkategorie)  
    - Appetizer Category (Vorspeisenkategorie)  
    - CommentKeywords (Kommentarschlüsselwörter)  
    - Datum (Date)  
    - Daypart (Tageszeit)  
    - Dessert Category (Nachspeisenkategorie)  
    - FreeForm (Freiform)  
    - Kids Category (Kinderkategorie)  
    - Messages (Nachrichten)  
    - Premium Content Category (Premiuminhaltskategorien)  
    - Question (Frage)  
    - Store (Speicher)  
    - Surveys (Umfragen)  
    - Weekday (Wochentag)  


## <a name="system-requirements"></a>Systemanforderungen
Ein Ziosk-Konto mit Berechtigungen für die obigen Tabellen wird benötigt, um dieses Inhaltspaket zu instanziieren.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](fundamentals/power-bi-overview.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

