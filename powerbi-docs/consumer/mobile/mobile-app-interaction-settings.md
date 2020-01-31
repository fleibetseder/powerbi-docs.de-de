---
title: Konfigurieren der Interaktionseinstellungen für Berichte
description: Erfahren Sie, wie Sie Standardinteraktionseinstellungen für Berichte überschreiben.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: painbar
ms.openlocfilehash: fee89c65328b70e1f312b39fbad75d7148bd92f2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542287"
---
# <a name="configure-report-interaction-settings"></a>Konfigurieren der Interaktionseinstellungen für Berichte

## <a name="overview"></a>Übersicht

Die mobile Power BI-App verfügt über mehrere konfigurierbare Interaktionseinstellungen, mit denen Sie steuern können, wie Sie mit Ihren Daten interagieren, und mit denen Sie das Verhalten einiger Elemente der mobilen Power BI-App definieren können. Zurzeit gibt es Einstellungen für:
* [Interaktionen durch einfaches Tippen oder Doppeltippen in Berichtsvisuals](#single-tap)
* [Berichtsfußzeilen, die entweder angedockt oder dynamisch sind](#docked-report-footer-android-phones) (Android)
* [Aktualisierung der Berichte entweder per Klick auf die Schaltfläche oder durch Ziehen nach unten](#report-refresh-android-phones) (Android)

Damit Sie zu den Interaktionseinstellungen gelangen, tippen Sie auf Ihr Profilbild, um die [Seitenleiste](./mobile-apps-home-page.md#header) zu öffnen, wählen Sie dann **Einstellungen** aus, und suchen Sie den Abschnitt **Interaktion**.

![Interaktionseinstellungen](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

>[!NOTE]
>Die Interaktionseinstellungen für die Schaltfläche „Aktualisieren“ und für das Andocken der Berichtsfußzeile haben derzeit keinen Einfluss auf die Berichtsserverberichte. Dies ändert sich mit dem Berichtsserverrelease im Januar 2020.

## <a name="interaction-settings"></a>Interaktionseinstellungen

### <a name="single-tap"></a>Einfaches Tippen
Wenn Sie die mobile Power BI-App herunterladen, ist hierfür die Interaktion durch einfaches Tippen festgelegt. Das bedeutet, wenn Sie auf ein Visual tippen, um eine Aktion durchzuführen (z. B. die Auswahl eines Datenschnittelements, die übergreifende Hervorhebung, das Klicken auf einen Link oder eine Schaltfläche usw.), dass dann durch das Tippen sowohl das Visual ausgewählt und auch die gewünschte Aktion ausgeführt wird.

Wenn Sie möchten, können Sie die Interaktion durch einfaches Tippen deaktivieren. Sie müssen dann mit der Interaktion durch Doppeltippen arbeiten. Bei der Interaktion durch Doppeltippen tippen Sie zuerst auf das Visual, das Sie auswählen möchten, und dann in das Visual, um Ihre gewünschte Aktion auszuführen.

### <a name="docked-report-footer-android-phones"></a>Angedockte Berichtsfußzeilen (Android-Smartphones)

Die Einstellung zur angedockten Berichtsfußzeile bestimmt, ob die Berichtsfußzeile unten im Bericht angedockt bleibt (z. B. verankert und immer sichtbar), oder ob diese basierend auf Ihren Aktionen (z. B. Scrollen) im Bericht ausgeblendet wird oder nochmals eingeblendet wird.

Auf Android-Smartphones ist die Einstellung für die angedockte Berichtsfußzeile standardmäßig **on** (eingeschaltet), was bedeutet, dass die Berichtsfußzeile angedockt ist und unten im Bericht immer sichtbar ist. Legen Sie die Einstellung auf **off** (ausgeschaltet) fest, falls Sie eine dynamische Berichtsfußzeile haben möchten, die je nach Ihren Aktionen im Bericht ein- und ausgeblendet wird.

### <a name="report-refresh-android-phones"></a>Aktualisierung des Berichts (Android-Smartphones)

Die Einstellung zur Aktualisierung des Berichts definiert, wie Sie Ihre Aktualisierungen der Berichte initiieren. Sie können entweder eine Schaltfläche zum Aktualisieren in allen Berichtskopfzeilen wählen, oder Sie können die Aktion „Zum Aktualisieren nach unten ziehen“ (einfaches Ziehen von oben nach unten) auf der Berichtsseite verwenden, um den Bericht zu aktualisieren. Die untere Abbildung zeigt die beiden Alternativen. 

![Schaltfläche „Aktualisieren“ und die Aktion „Zum Aktualisieren nach unten ziehen“ gegenübergestellt](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

Auf Android-Smartphones ist die Schaltfläche „Aktualisieren“ standardmäßig hinzugefügt.

Navigieren Sie zum Symbol zum Aktualisieren des Berichts in den Interaktionseinstellungen, um die Einstellung zum Aktualisieren des Berichts zu ändern. Die aktuelle Einstellung wird dann angezeigt. Tippen Sie auf den Wert, um ein Popupfenster zu öffnen, in dem Sie einen neuen Wert auswählen können.

![Einstellung zum Aktualisieren](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Remotekonfiguration

Interaktionen können auch remote durch einen Administrator konfiguriert werden, indem ein MDM-Tool mit einer App-Konfigurationsdatei verwendet wird. Somit ist es möglich, die Interaktionseinstellungen für Berichte in der Organisation oder für spezifische Benutzergruppen der Organisation zu standardisieren. Weitere Informationen finden Sie unter [Konfigurieren der Interaktion mithilfe der mobilen Geräteverwaltung](./mobile-app-configuration.md).


## <a name="next-steps"></a>Nächste Schritte
* [Interagieren mit Berichten](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Konfigurieren der Interaktion mithilfe der mobilen Geräteverwaltung](./mobile-app-configuration.md)
