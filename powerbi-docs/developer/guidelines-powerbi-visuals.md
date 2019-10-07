---
title: Richtlinien für Power BI-Visuals
description: Erfahren Sie, wie Sie ein benutzerdefiniertes Visual in AppSource veröffentlichen, damit es von anderen gefunden und erworben werden kann.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 07/16/2019
ms.openlocfilehash: 4e17406b0b4e616a9857cf40298a7931e2b65427
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71944855"
---
# <a name="guidelines-for-power-bi-visuals"></a>Richtlinien für Power BI-Visuals
Bevor Sie Ihr Visual in AppSource [veröffentlichen](https://docs.microsoft.com/power-bi/developer/office-store), damit andere es verwenden können, stellen Sie sicher, dass Sie die Richtlinien befolgen, um Ihren Benutzern eine hohe Benutzerfreundlichkeit zu bieten. 

## <a name="context-menu"></a>Kontextmenü
Das Kontextmenü ist das Rechtsklickmenü, das angezeigt wird, wenn der Benutzer mit der Maus über ein Visual fährt.
Alle Power BI-Visuals sollten das Kontextmenü für eine einheitliche Darstellung aktivieren. Lesen Sie [diesen Artikel](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md), um zu erfahren, wie Sie ein Kontextmenü hinzufügen.


## <a name="logo-guidelines"></a>Richtlinien für Logos
> [!NOTE]
> Das Word--Logo in diesem Artikel steht stellvertretend für beliebige kommerzielle Firmenlogos, wie in den Abbildungen unten beschrieben. 

In diesem Abschnitt werden die Spezifikationen zum Hinzufügen von Logos in Power BI-Visuals erläutert. Logos sind nicht obligatorisch. Wenn sie hinzugefügt werden, müssen Sie diesen Richtlinien entsprechen. 

> [!IMPORTANT]
> Logos sind *nur im Bearbeitungsmodus* zulässig. Logos können im Anzeigemodus *nicht* dargestellt werden.


![Definitionen](media/guidelines-powerbi-visuals/definitions.png)

![Dinge, die Sie beachten sollten](media/guidelines-powerbi-visuals/things-to-keep-in-mind.png)

![Dinge, die Sie vermeiden sollten](media/guidelines-powerbi-visuals/things-to-avoid.png)

![Größe und Format](media/guidelines-powerbi-visuals/size-and-format.png)

![Ränder und Größenanpassung](media/guidelines-powerbi-visuals/margins-and-sizes.png)

![Bearbeitungsmodus](media/guidelines-powerbi-visuals/logos-in-edit-mode.png)


Informative Symbole, sofern vorhanden, sollten sich im Lesemodus nach den oben beschriebenen Richtlinien für Farbe, Größe und Position richten.

## <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Richtlinien für Power BI-Visuals mit zusätzlichen Käufen

Bis vor Kurzem wurden im Marketplace (AppSource) nur kostenlose Power BI-Visuals akzeptiert. Diese Vorgabe wurde geändert (Dezember 2018). Sie können also auch Visuals in AppSource anbieten, für die möglicherweise weitere Komponenten erworben werden müssen. 

Visuals, für die möglicherweise weitere Komponenten erworben werden müssen, ähneln den Add-Ins im Office Store, die per In-App-Kauf (IAP, In-App-Purchase) erworben werden. Entwickler können diese Visuals zudem zur Zertifizierung übermitteln, nachdem das AppSource-Team diese genehmigt hat und nachdem sichergestellt wurde, dass diese den Zertifizierungsanforderungen entsprechen. Weitere Informationen zu den Anforderungen finden Sie unter [Zertifizierte Power BI-Visuals](../power-bi-custom-visuals-certified.md).

> [!NOTE]
> Damit ein Visual zertifiziert werden kann, darf es nicht auf externe Dienste oder Ressourcen zugreifen.

>[!IMPORTANT]  
> Wenn Sie Ihr Visual von „Kostenlos“ zu „Möglicherweise sind zusätzliche Käufe erforderlich.“ aktualisieren, müssen den Benutzern im gleichen Umfang kostenlose Funktionen zur Verfügung stehen wie vor der Aktualisierung. Sie können zusätzlich zu den vorhandenen kostenlosen Features optionale erweiterte Features hinzufügen, die kostenpflichtig sind. Es wird empfohlen, die IAP-Visuals mit den erweiterten Features als neue Visuals zu veröffentlichen, anstatt die vorhandenen kostenlosen Features zu aktualisieren.

## <a name="what-changed-in-the-submission-process"></a>Was hat sich am Übermittlungsprozess geändert?

Entwickler laden ihre Visuals, die In-App-Käufe enthalten, genau wie kostenlose Visuals über das Seller-Dashboard in AppSource hoch. Um deutlich zu machen, dass das übermittelte Visual In-App-Käufe enthält, sollten Entwickler im Seller-Dashboard den Hinweis „Visual mit In-App-Käufen“ hinzufügen. Entwickler müssen außerdem einen Lizenzschlüssel oder ein Token angeben, damit das entsprechende Team die In-App-Käufe überprüfen kann. Sobald das Visual überprüft und genehmigt wurde, zeigt das AppSource-Listing für das Visual den Hinweis „Möglicherweise müssen weitere Komponenten erworben werden“ in den Preisoptionen an.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>Was ist ein Power BI-Visual mit In-App-Käufen?

Ein IAP-Visual ist ein *kostenloses* Visual, das *kostenlose Features* bietet. Ein solches Visual verfügt auch über einige erweiterte Features, für deren Nutzung zusätzliche Gebühren anfallen können. Entwickler müssen die Benutzer in der Beschreibung des Visuals über die Features informieren, für deren Funktionsweise möglicherweise zusätzliche Komponenten erworben werden müssen. Derzeit bietet Microsoft keine nativen APIs an, den Erwerb von Apps und Add-Ins unterstützen.

Entwickler müssen ein Zahlungssystem von einem Drittanbieter für diese Käufe verwenden. Weitere Informationen finden Sie in [den Richtlinien für unseren Store](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads).

> [!NOTE]
> Wasserzeichen sind in kostenlosen Features oder kostenlosen Visuals nicht zulässig. Wasserzeichen können nur in kostenpflichtigen Features verwendet werden, die ohne gültige Lizenz verwendet werden. Wenn die erweiterten kostenpflichtigen Features ohne gültige Lizenz verwendet werden, wird empfohlen, ein Popupfenster anzuzeigen, das alle Informationen zur Lizenz enthält.  


## <a name="best-practices"></a>Bewährte Methoden

### <a name="visual-landing-page"></a>Startseite für Visuals

Verwenden Sie die Startseite, um den Benutzern zu verdeutlichen, wie sie Visuals verwenden und wo Lizenzen erworben werden können. Fügen Sie keine Videos ein, die automatisch abgespielt werden. Fügen Sie nur Inhalte hinzu, die das Benutzererlebnis verbessern, z.B. Informationen oder Links zu den Details für den Erwerb von Lizenzen und zum Einsatz von In-App-Features.

### <a name="license-key-and-token"></a>Lizenzschlüssel und Token

Fügen Sie Felder für Lizenzschlüssel oder Token im oberen Teil des Formatierungsbereichs hinzu, sodass Benutzer diese leicht finden können.

## <a name="faq"></a>HÄUFIG GESTELLTE FRAGEN

Weitere Informationen und finden Sie in den [häufig gestellten Fragen zu Visuals mit zusätzlichen Käufen](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie ein benutzerdefiniertes Visual in [AppSource](office-store.md) veröffentlichen, damit es von anderen gefunden und verwendet werden kann.
