---
title: Festlegen von Datenwarnungen im Power BI-Dienst
description: "Erfahren Sie, wie Sie Warnungen festlegen, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen im Microsoft Power BI-Dienst festgelegten Grenzen überschreiten."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: JbL2-HJ8clE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/06/2017
ms.author: mihart
ms.openlocfilehash: cfbd7d124784b15b432921554c8ac5bbe321846c
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2017
---
# <a name="data-alerts-in-power-bi-service"></a>Datenwarnungen im Power BI-Dienst
Legen Sie Warnungen fest, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen festgelegten Grenzen überschreiten. Warnungen können nur für Kacheln, die über Berichtsvisuals angeheftet wurden, und nur für Messgeräte, KPIs und Karten eingerichtet werden. Warnungen können für aus Streamingdatasets erstellte Visuals festgelegt werden, die aus einem Bericht an ein Dashboard angeheftet wurden. Sie können jedoch nicht für Streamingkacheln festgelegt werden, die mit **Kachel hinzufügen** > **Benutzerdefinierte Streamingdaten** direkt im Dashboard erstellt wurden. Die Warnungen werden nur Ihnen angezeigt, auch wenn Sie das Dashboard freigeben. Datenwarnungen werden mit allen Plattformen synchronisiert. Sie können Datenwarnungen daher [in den mobilen Power BI-Apps](mobile-set-data-alerts-in-the-mobile-apps.md) und im Power BI-Dienst festlegen und anzeigen. Für Power BI Desktop sind keine Datenwarnungen verfügbar. Warnungen können auch [automatisiert und in Microsoft Flow integriert werden](https://flow.microsoft.com) -  – [probieren Sie es einfach aus](service-flow-integration.md).

![](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Datengesteuerte Warnungsbenachrichtigungen liefern Informationen über Ihre Daten. Wenn Sie Power BI-Daten auf einem mobilen Gerät anzeigen und das Gerät gestohlen wird, sollten Sie mithilfe des Power BI-Diensts alle Regeln für datengesteuerte Warnungen deaktivieren.
> 
> 

## <a name="set-data-alerts-in-power-bi-service"></a>Festlegen von Datenwarnungen im Power BI-Dienst
Sehen Sie sich an, wie Amanda einige Datenwarnungen zu Karten auf ihrem Dashboard hinzufügt. Befolgen Sie dann die schrittweisen Anleitungen unter dem Video, um es selbst ausprobieren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

In diesem Beispiel wird eine Kartenkachel aus dem Beispieldashboard zur Einzelhandelsanalyse verwendet.

1. Zunächst benötigen Sie ein Dashboard. Wählen Sie auf einer Messgerät-, KPI- oder Kartenkachel eines Dashboards die Auslassungspunkte aus.
   
   ![](media/service-set-data-alerts/powerbi-card.png)
2. Wählen Sie das Glockensymbol ![](media/service-set-data-alerts/power-bi-bell-icon.png) aus, um eine oder mehrere Warnungen für **Läden gesamt** hinzuzufügen.
   
   ![](media/service-set-data-alerts/powerbi-set-alert.png)
3. Stellen Sie zunächst sicher, dass der Schieberegler auf **Ein** festgelegt ist, und geben Sie der Warnung einen Titel. Durch Titel lassen sich Warnungen schnell einordnen.
   
   ![](media/service-set-data-alerts/powerbi-alert-title.png)
4. Scrollen Sie nach unten, und geben Sie die Warnungsdetails ein.  In diesem Beispiel erstellen wir eine Warnung, die uns einmal täglich benachrichtigt, wenn die Gesamtzahl der Läden die Zahl 100 überschreitet. Warnungen werden in der Mitteilungszentrale angezeigt. Und außerdem lassen wir uns von Power BI eine E-Mail senden.
   
   ![](media/service-set-data-alerts/powerbi-set-alert-details.png)
5. Wählen Sie **Speichern**.

## <a name="receiving-alerts"></a>Empfangen von Warnungen
Wenn die nachverfolgten Daten einen der von Ihnen festgelegten Schwellenwerte erreichen, erfolgen mehrere Aktionen. Power BI überprüft zunächst, ob seit dem Senden der letzten Warnung mehr als eine Stunde oder mehr als 24 Stunden (je nach der von Ihnen ausgewählten Option) verstrichen sind. Solange die Daten den Schwellenwert überschreiten, erhalten Sie eine Warnung.

Anschließend sendet Power BI eine Warnung an Ihre Mitteilungszentrale und optional an Ihre E-Mail-Adresse. Jede Warnung enthält einen direkten Link zu den entsprechenden Daten. Wählen Sie den Link aus, um die entsprechende Kachel aufzurufen, die Sie durchsuchen und freigeben können und auf der Sie weitere Informationen erhalten.  

1. Wenn Sie festgelegt haben, dass bei einer Warnung eine E-Mail an Sie gesendet wird, enthält Ihr Posteingang etwa Folgendes.
   
   ![](media/service-set-data-alerts/powerbi-alerts-email.png)
2. Power BI fügt der **Mitteilungszentrale** eine Nachricht und der entsprechenden Kachel das Symbol für eine neue Warnung hinzu.
   
   ![](media/service-set-data-alerts/powerbi-alert-notifications.png)
3. Öffnen Sie die Mitteilungszentrale, um die Warnungsdetails anzuzeigen.
   
    ![](media/service-set-data-alerts/powerbi-alert-notfication.png)
   
   > [!NOTE]
   > Warnungen erfolgen nur für Daten, die aktualisiert werden. Wenn Daten aktualisiert werden, überprüft Power BI, ob eine Warnung für diese Daten festgelegt ist. Wenn die Daten einen Warnungsschwellenwert erreicht haben, wird eine Warnung ausgelöst.
   > 
   > 

## <a name="managing-alerts"></a>Verwalten von Warnungen
Es gibt drei Möglichkeiten zum Verwalten von Warnungen: in der Dashboardkachel, im Menü für Power BI-Einstellungen und auf einer einzelnen Kachel in der [mobilen Power BI-App auf dem iPhone](mobile-set-data-alerts-in-the-mobile-apps.md) oder in der [mobilen Power BI-App für Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>In der Kachel
1. Wenn Sie eine Warnung für eine Kachel ändern oder entfernen müssen, öffnen Sie das Fenster **Warnungen verwalten** erneut, indem Sie das Glockensymbol ![](media/service-set-data-alerts/power-bi-bell-icon.png) auswählen. Alle Warnungen, die Sie für diese Kachel festgelegt haben, werden angezeigt.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts.png).
2. Um eine Warnung zu ändern, wählen Sie den Pfeil links neben dem Namen der Warnung.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts-arrow.png).
3. Um eine Warnung zu löschen, wählen Sie den Papierkorb rechts neben dem Namen der Warnung.
   
      ![](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Im Menü für Power BI-Einstellungen
1. Wählen Sie das Zahnradsymbol auf der Power BI-Menüleiste.
   
    ![](media/service-set-data-alerts/powerbi-gear-icon.png).
2. Wählen Sie unter **Einstellungen** die Option **Warnungen** aus.
   
    ![](media/service-set-data-alerts/powerbi-alert-settings.png)
3. Hier können Sie Warnungen aktivieren und deaktivieren, das Fenster **Warnungen verwalten** öffnen, um Änderungen vorzunehmen, oder die Warnung löschen.

## <a name="tips-and-troubleshooting"></a>Tipps und Problembehandlung
* Für Bing-Kacheln und für Kartenkacheln mit Datum/Uhrzeit-Measures werden Warnungen derzeit nicht unterstützt.
* Warnungen können nur für numerische Datentypen ausgelöst werden.
* Warnungen erfolgen nur für Daten, die aktualisiert werden. Sie können nicht für statische Daten ausgelöst werden.
* Warnungen können für Streamingdatasets nur erfolgen, wenn Sie ein KPI-/Karten-/Messgerät-Visual erstellen und dieses dann an das Dashboard anheften.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen eines Flows in Microsoft Flow, der eine Datenwarnung enthält](service-flow-integration.md)    
[Festlegen von Datenwarnungen auf Ihrem mobilen Gerät](mobile-set-data-alerts-in-the-mobile-apps.md)    
[Erste Schritte mit Power BI](service-get-started.md)    
Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
