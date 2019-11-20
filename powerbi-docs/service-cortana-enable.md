---
title: Aktivieren von Cortana für Power BI
description: Verwenden Sie Cortana mit Power BI, um Antworten zu Ihren Daten zu erhalten. Aktivieren Sie Cortana für jedes Power BI-Dataset, und aktivieren Sie anschließend den Cortana-Zugriff auf Ihre Datasets von Windows-Geräten.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: a631bc37c193521b2acc367a0c6d8540419e3b79
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872907"
---
# <a name="enable-cortana-to-access-power-bi-reports-and-their-underlying-datasets"></a>Aktivieren von Cortana für den Zugriff auf Power BI-Berichte (und deren zugrunde liegende Datasets)
Sie haben die [Einführung in Cortana für Power BI](service-cortana-intro.md) gelesen (falls nicht, sollten Sie diese lesen und dann hierher zurückkehren). Und jetzt möchten Sie es selbst auszuprobieren.  Bevor Sie in Cortana Fragen in natürlicher Sprache stellen und Antworten anhand der in Power BI-***Berichten*** gespeicherten Daten erhalten können, müssen einige Anforderungen erfüllt sein. Insbesondere müssen Sie folgende Aktionen ausführen.

> [!IMPORTANT]
> Die Cortana-Integration in Power BI wird eingestellt. Ab dem 11. Juni funktioniert Cortana nicht mehr für Dashboards und Berichte.

Im Power BI-Dienst

* Aktivieren Sie ein oder mehrere Datasets für Cortana. (Berichte werden über Datasets erstellt, daher benötigt Cortana Zugriff auf diese Datasets.)

In Microsoft Windows

* Vergewissern Sie sich, dass Windows 10, Version 1511 oder höher, ausgeführt wird.
* Stellen Sie sicher, dass Power BI und Windows miteinander kommunizieren können. Dies bedeutet, dass Sie Ihr Konto mit Windows verbinden müssen.

## <a name="use-power-bi-service-to-enable-cortana-to-access-report-pages-in-power-bi"></a>Verwenden des Power BI-Diensts, um Cortana den Zugriff auf Berichtsseiten in Power BI zu ermöglichen
Das Einrichten des Zugriffs von Cortana auf Berichte in Power BI ist ein einfacher Prozess.  Sie müssen lediglich das zugrunde liegende Dataset des Berichts aktivieren, indem Sie die Option „Cortana den Zugriff auf dieses Dataset ermöglichen“ auswählen. Danach kann jeder Benutzer, der über reguläre Freigabe-, App- und Inhaltspaketfeatures von Power BI Zugriff auf das Dataset in Power BI hat, in Cortana unter Windows 10 Antworten anhand des Berichts erhalten.

Sie müssen sich für jedes Dataset, auf das Contana Zugriff haben soll, beim Power BI-Dienst (nicht bei Power BI Desktop) anmelden und diese Schritte wiederholen.

1. Bestimmen Sie, welche Datasets zu aktivieren sind. Wählen Sie in der Liste der Berichtsinhalte den Bericht aus, auf den Cortana Zugriff erhalten soll, und klicken Sie auf das Symbol **Verwandte Inhalte anzeigen** ![](media/service-cortana-enable/power-bi-cortana-view-related-icon.png).
   
    ![Verwandte Inhalte anzeigen](media/service-cortana-enable/power-bi-view-related.png)
2. Das diesem Bericht zugeordnete Dataset heißt **Contoso Vertrieb**.
   
    ![Dataset „Contoso Vertrieb“](media/service-cortana-enable/power-bi-identify-dataset.png)
3. Wählen Sie rechts neben dem Datasetnamen **Weitere Optionen** (...) > Einstellungen** aus.  
   
    ![„Einstellungen“ auswählen](media/service-cortana-enable/power-bi-settings-cortana.png)
4. Wählen Sie **Q&A und Cortana** > **Cortana den Zugriff auf dieses Dataset erlauben** > **Anwenden** aus.
   
   ![Dataset für Cortana-Zugriff](media/service-cortana-enable/power-bi-cortana-enable-new.png)
   
   In diesem Beispiel aktivieren wir den Cortana-Zugriff auf das Dataset „Contoso Vertrieb“.
   
   > [!NOTE]
   > Wenn ein neues Dataset oder eine neue Cortana-Antwortkarte zu Power BI hinzugefügt und für Cortana aktiviert wird, kann es bis zu 30 Minuten dauern, bis Ergebnisse angezeigt werden. Durch das Anmelden und Abmelden bei Windows 10 oder einen Neustart des Cortana-Prozesses in Windows 10 werden neue Inhalte sofort angezeigt.
   > 
   > Wenn Sie ein Dataset für Cortana aktivieren und dieses Dataset zu einem Ihrer Inhaltspakete oder einer Ihrer Apps gehört, müssen Sie es erneut veröffentlichen, damit Ihre Kollegen das Dataset mit Cortana verwenden können.
   > 
   > 

## <a name="add-your-power-bi-credentials-to-windows"></a>Hinzufügen Ihrer Power BI-Anmeldeinformationen zu Windows
Es muss Windows 10, Version 1511 oder höher, ausgeführt werden.

1. Bestimmen Sie, welche Windows 10-Version Sie ausführen. Öffnen Sie **Einstellungen**.
    ![Windows-Einstellungen öffnen](media/service-cortana-enable/power-bi-cortana-windows.png)

    Wählen Sie dann **System > Info** aus. Unten auf dem Bildschirm wird **Windows-Spezifikationen > Version** angezeigt.

   * Wenn Sie Windows 10, Version 1511 (Windows 10-Update vom November 2015), oder eine höhere Version vor Version 1607 verwenden, fügen Sie Ihr Geschäfts- oder Schulkonto und Ihr Microsoft-Konto hinzu (führen Sie Schritt 2 und 3 aus).
   * Wenn Sie Windows 10, Version 1607 (Windows 10-Update vom Juli 2016) oder eine höhere Version verwenden, fügen Sie Ihr Geschäfts- oder Schulkonto hinzu (führen Sie nur Schritt 2 aus).
1. Fügen Sie Ihr Geschäfts- oder Schulkonto für Cortana hinzu.
   
   * Öffnen Sie **Einstellungen** > **Konten**.
     
       ![Einstellungen – Konten](media/service-cortana-enable/power-bi-windows-accounts.png)
   * Führen Sie einen Bildlauf nach unten durch, und wählen Sie **Geschäfts- oder Schulkonto hinzufügen** aus. Sie können auch auf der Seite **Konten** die Option **Auf Arbeits- oder Schulkonto zugreifen > Verbinden** auswählen.
     
     ![Geschäftskonto hinzufügen](media/service-cortana-enable/power-bi-add-work-account2.png)

Cortana verwendet dieses Geschäfts- oder Schulkonto, um in Power BI nach möglichen Antworten auf Ihre Fragen in Cortana zu suchen.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen von *Antwortseiten* für Cortana in Power BI](service-cortana-answer-cards.md)

[Behandeln von Problemen bei Cortana für Power BI](service-cortana-troubleshoot.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

