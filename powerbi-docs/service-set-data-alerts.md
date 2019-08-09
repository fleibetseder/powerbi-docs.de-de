---
title: Festlegen von Datenwarnungen im Power BI-Dienst
description: Erfahren Sie, wie Sie Warnungen festlegen, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen im Microsoft Power BI-Dienst festgelegten Grenzen überschreiten.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/28/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: a26cd6d654f9378d9fa09ae46b64762213b26089
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68522987"
---
# <a name="data-alerts-in-power-bi-service"></a>Datenwarnungen im Power BI-Dienst
Legen Sie Warnungen fest, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen festgelegten Grenzen überschreiten. 

Sie können Warnungen für Kacheln festlegen, wenn Sie über eine Power BI Pro-Lizenz verfügen oder wenn ein Dashboard über eine [Premium-Kapazität](service-premium-what-is.md) mit Ihnen geteilt wurde. Warnungen können nur für Kacheln, die über Berichtsvisuals angeheftet wurden, und nur für Messgeräte, KPIs und Karten festgelegt werden. Warnungen können für aus Streamingdatasets erstellte Visuals festgelegt werden, die aus einem Bericht an ein Dashboard angeheftet wurden. Sie können jedoch nicht für Streamingkacheln festgelegt werden, die mit **Kachel hinzufügen** > **Benutzerdefinierte Streamingdaten** direkt im Dashboard erstellt wurden. 

Die Warnungen werden nur Ihnen angezeigt, auch wenn Sie das Dashboard freigeben. Datenwarnungen werden mit allen Plattformen synchronisiert. Sie können Datenwarnungen daher [in den mobilen Power BI-Apps](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) und im Power BI-Dienst festlegen und anzeigen. Für Power BI Desktop sind keine Datenwarnungen verfügbar. Warnungen können auch [automatisiert und in Microsoft Flow integriert werden](https://flow.microsoft.com) -  – [probieren Sie es einfach aus](service-flow-integration.md).

![Kacheln](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Datengesteuerte Warnungsbenachrichtigungen liefern Informationen über Ihre Daten. Wenn Sie Power BI-Daten auf einem mobilen Gerät anzeigen und das Gerät gestohlen wird, sollten Sie mithilfe des Power BI-Diensts alle Regeln für datengesteuerte Warnungen deaktivieren.
> 
> 

## <a name="set-data-alerts-in-power-bi-service"></a>Festlegen von Datenwarnungen im Power BI-Dienst
Sehen Sie sich an, wie Amanda einige Datenwarnungen zu Kacheln auf dem Dashboard hinzufügt. Befolgen Sie dann die schrittweisen Anleitungen unter dem Video, um es selbst ausprobieren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

In diesem Beispiel wird eine Kartenkachel aus dem Beispieldashboard zur Einzelhandelsanalyse verwendet.

1. Zunächst benötigen Sie ein Dashboard. Wählen Sie auf einer Messgerät-, KPI- oder Kartenkachel eines Dashboards die Auslassungspunkte aus.
   
   ![Kachel „Filialen insgesamt“](media/service-set-data-alerts/powerbi-card.png)
2. Wählen Sie das Glockensymbol ![Warnungssymbol](media/service-set-data-alerts/power-bi-bell-icon.png) aus, um eine oder mehrere Warnungen für **Filialen insgesamt** hinzuzufügen.
   
1. Wählen Sie zunächst **+ Warnungsregel hinzufügen** aus, stellen Sie sicher, dass der Schieberegler auf **Ein** festgelegt ist, und geben Sie der Warnung einen Titel. Durch Titel lassen sich Warnungen schnell einordnen.
   
   ![Fenster „Warnungen verwalten“](media/service-set-data-alerts/powerbi-alert-title.png)
4. Scrollen Sie nach unten, und geben Sie die Warnungsdetails ein.  In diesem Beispiel erstellen wir eine Warnung, die uns einmal täglich benachrichtigt, wenn die Gesamtzahl der Läden die Zahl 100 überschreitet. Warnungen werden in der Mitteilungszentrale angezeigt. Und außerdem lassen wir uns von Power BI eine E-Mail senden.
   
   ![Fenster „Warnungen verwalten“, Festlegen des Schwellenwerts](media/service-set-data-alerts/power-bi-set-alert-details.png)
5. Wählen Sie **Speichern**.

## <a name="receiving-alerts"></a>Empfangen von Warnungen
Wenn die nachverfolgten Daten einen der von Ihnen festgelegten Schwellenwerte erreichen, erfolgen mehrere Aktionen. Power BI überprüft zunächst, ob seit dem Senden der letzten Warnung mehr als eine Stunde oder mehr als 24 Stunden (je nach der von Ihnen ausgewählten Option) verstrichen sind. Solange die Daten den Schwellenwert überschreiten, erhalten Sie eine Warnung.

Anschließend sendet Power BI eine Warnung an Ihre Mitteilungszentrale und optional an Ihre E-Mail-Adresse. Jede Warnung enthält einen direkten Link zu den entsprechenden Daten. Wählen Sie den Link aus, um die entsprechende Kachel aufzurufen, die Sie durchsuchen und freigeben können und auf der Sie weitere Informationen erhalten.  

1. Wenn Sie festgelegt haben, dass bei einer Warnung eine E-Mail an Sie gesendet wird, enthält Ihr Posteingang etwa Folgendes.
   
   ![Warnungs-E-Mail](media/service-set-data-alerts/powerbi-alerts-email.png)
2. Power BI fügt der **Mitteilungszentrale** eine Nachricht und der entsprechenden Kachel das Symbol für eine neue Warnung hinzu.
   
   ![Benachrichtigungssymbol in Power BI](media/service-set-data-alerts/powerbi-alert-notifications.png)
3. Öffnen Sie die Mitteilungszentrale, um die Warnungsdetails anzuzeigen.
   
    ![Warnung lesen](media/service-set-data-alerts/powerbi-alert-notification.png)
   
   > [!NOTE]
   > Warnungen erfolgen nur für Daten, die aktualisiert werden. Wenn Daten aktualisiert werden, überprüft Power BI, ob eine Warnung für diese Daten festgelegt ist. Wenn die Daten einen Warnungsschwellenwert erreicht haben, wird eine Warnung ausgelöst.
   > 
   > 

## <a name="managing-alerts"></a>Verwalten von Warnungen
Es gibt viele Möglichkeiten zum Verwalten von Warnungen: in der Dashboardkachel, im Menü für Power BI-Einstellungen, auf einer einzelnen Kachel in der [mobilen Power BI-App auf dem iPhone](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) oder in der [mobilen Power BI-App für Windows 10](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>In der Kachel
1. Wenn Sie eine Warnung für eine Kachel ändern oder entfernen müssen, öffnen Sie das Fenster **Warnungen verwalten** erneut, indem Sie auf das Glockensymbol ![Warnungssymbol](media/service-set-data-alerts/power-bi-bell-icon.png) klicken. Alle Warnungen, die Sie für diese Kachel festgelegt haben, werden angezeigt.
   
    ![Fenster „Warnungen verwalten“](media/service-set-data-alerts/powerbi-see-alerts.png).
2. Um eine Warnung zu ändern, wählen Sie den Pfeil links neben dem Namen der Warnung.
   
    ![Pfeil neben dem Namen der Warnung](media/service-set-data-alerts/powerbi-see-alerts-arrow.png).
3. Um eine Warnung zu löschen, wählen Sie den Papierkorb rechts neben dem Namen der Warnung.
   
      ![Papierkorbsymbol](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Im Menü für Power BI-Einstellungen
1. Wählen Sie das Zahnradsymbol auf der Power BI-Menüleiste.
   
    ![Zahnradsymbol](media/service-set-data-alerts/powerbi-gear-icon.png).
2. Wählen Sie unter **Einstellungen** die Option **Warnungen** aus.
   
    ![Registerkarte „Warnungen“ im Fenster „Einstellungen“](media/service-set-data-alerts/powerbi-alert-settings.png)
3. Hier können Sie Warnungen aktivieren und deaktivieren, das Fenster **Warnungen verwalten** öffnen, um Änderungen vorzunehmen, oder die Warnung löschen.

## <a name="tips-and-troubleshooting"></a>Tipps und Problembehandlung
* Für Bing-Kacheln und für Kartenkacheln mit Datum/Uhrzeit-Measures werden Warnungen derzeit nicht unterstützt.
* Warnungen können nur für numerische Datentypen ausgelöst werden.
* Warnungen erfolgen nur für Daten, die aktualisiert werden. Sie können nicht für statische Daten ausgelöst werden.
* Warnungen können für Streamingdatasets nur erfolgen, wenn Sie ein KPI-/Karten-/Messgerät-Visual erstellen und dieses dann an das Dashboard anheften.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen eines Flows in Microsoft Flow, der eine Datenwarnung enthält](service-flow-integration.md)    
[Festlegen von Datenwarnungen auf Ihrem mobilen Gerät](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)    
[Was ist Power BI?](power-bi-overview.md)    
Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)

