---
title: Verwenden von OneDrive for Business-Links in Power BI Desktop
description: Verwenden von OneDrive for Business-Links in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 226a5035ba6c93a7987d74ab0fea1dd4264df0b1
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73865309"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Verwenden von OneDrive for Business-Links in Power BI Desktop
Viele Anwender speichern Excel-Arbeitsmappen auf OneDrive for Business-Laufwerken, was auch für Power BI Desktop eine gute Praxis ist. Mit **Power BI Desktop** können Sie Hyperlinks für **Excel**-Dateien verwenden, die in **OneDrive for Business** gespeichert sind, um Berichte und visuelle Elemente zu erstellen. Sie können ein **OneDrive for Business**-Gruppenkonto oder Ihr persönliches **OneDrive for Business**-Konto verwenden.

Um einen Online-Link aus **OneDrive for Business** zu erstellen, sind einige zusätzliche Schritte erforderlich. In den folgenden Abschnitten werden diese Schritte beschrieben, mithilfe derer Sie den Dateilink zwischen Gruppen, verschiedenen Computern und mit Ihren Kollegen gemeinsam nutzen können.

## <a name="get-a-link-from-excel-starting-in-the-browser"></a>Abrufen eines Links in Excel, mit Start im Browser
1. Navigieren Sie mit einem Browser zu dem gewünschten OneDrive for Business-Speicherort. Klicken Sie mit der rechten Maustaste auf die Datei, die Sie verwenden möchten, und wählen Sie **In Excel öffnen** aus.
   
   > [!NOTE]
   > Ihre Browseroberfläche sieht möglicherweise nicht genau so aus, wie im folgenden Bild. Es gibt viele Methoden zur Auswahl von **In Excel öffnen** für Dateien auf Ihrer **OneDrive for Business**-Browseroberfläche. Sie können hierzu jede Option nutzen, mit der Sie die Datei in Excel öffnen können.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. Wählen Sie in **Excel** die Option **Datei > Info** aus, und wählen Sie den Link über der Schaltfläche **Arbeitsmappe schützen** aus. Wählen Sie **Link in die Zwischenablage kopieren** aus (möglicherweise wird in Ihrer Version auch **Pfad in die Zwischenablage kopieren** angezeigt).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_03.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Verwenden des Links in Power BI Desktop
Sie können den Link, den Sie gerade in die Zwischenablage kopiert haben, in Power BI Desktop verwenden. Führen Sie hierzu die folgenden Schritte aus:

1. Wählen Sie in Power BI Desktop **Daten abrufen > Web** aus.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_04.png)
2. Fügen Sie den Link im Dialogfeld **Aus dem Web** ein (wählen Sie noch **nicht** „OK“ aus).
   
    ![](media/desktop-use-onedrive-business-links/odb-links_05.png)
3. Beachten Sie die Zeichenfolge *?web = 1* am Ende des Links, und *entfernen Sie den Teil der Web-URL-Zeichenfolge* **bevor** Sie **OK** auswählen, damit **Power BI Desktop** ordnungsgemäß zu der gewünschten Datei wechseln kann.
4. Wenn **Power BI Desktop** Anmeldeinformationen anfordert, wählen Sie entweder **Windows** (für lokale SharePoint-Websites) oder **Organisationskonto** (für Office 365- oder OneDrive for Business-Websites) aus.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

Ein **Navigator**-Fenster wird angezeigt. es ermöglicht Ihnen die Auswahl aus der Liste der Tabellen, Arbeitsblätter und Bereiche in der Excel-Arbeitsmappe. Von dort können Sie die OneDrive für Business-Datei wie jede andere Excel-Datei verwenden, Berichte erstellen und sie in Datasets wie jede andere Datenquelle verwenden.

> [!NOTE]
> Um eine **OneDrive for Business**-Datei im Power BI-Dienst als Datenquelle zu verwenden, muss für diese Datei **Dienst aktualisieren** aktiviert sein, und Sie müssen **OAuth2** als **Authentifizierungsmethode** auswählen, wenn Sie die Aktualisierungseinstellungen konfigurieren. Andernfalls kann beim Verbindungsversuch oder Aktualisieren ein Fehler auftreten (wie *Fehler beim Aktualisieren der Datenquellen-Anmeldeinformationen*). Durch Auswahl der Authentifizierungsmethode **OAuth2** wird das Auftreten dieses Anmeldeinformationsfehlers vermieden.
> 
> 

