---
title: Filtern eines Berichts nach geografischem Standort in einer mobilen Power BI-App
description: Hier erfahren Sie, wie Sie in den mobilen Microsoft Power BI-Apps einen Bericht nach geografischem Standort filtern können, wenn der Besitzer des Berichts geografische Markierungen festgelegt hat.
author: mshenhav
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: mshenhav
ms.openlocfilehash: 1079b624ebab827b41f4da55095028796319fdcd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870635"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Filtern eines Berichts nach geografischem Standort in den mobilen Power BI-Apps
Gilt für:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android-Smartphone](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android-Tablet](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-Telefone |Windows 10-Smartphones |

Wird beim Betrachten eines Power BI-Berichts auf Ihrem mobilen Gerät in der rechten oberen Ecke ein kleines Nadelsymbol angezeigt? Wenn dies der Fall ist, können Sie diesen Bericht basierend auf Ihrem geografischen Standort filtern.

> [!NOTE]
> Sie können nur nach Ort filtern, wenn die geografischen Namen im Bericht Englisch sind, z. B. „New York City“ oder „Germany“. Auf Windows 10-Smartphones werden geografische Filter unterstützt, auf Windows 10-Tablets und -PCs nicht.
> 
> 

## <a name="filter-your-report-by-your-geographic-location"></a>Filtern Ihres Berichts nach Ihrem geografischen Standort
1. Öffnen Sie einen Bericht in der mobilen Power BI-App auf Ihrem mobilen Gerät.
2. Wenn der Bericht geografische Daten enthält, wird eine Meldung angezeigt, in der Sie aufgefordert werden, Power BI zu gestatten, auf Ihren Standort zuzugreifen. Klicken Sie auf **Zulassen**, und tippen Sie dann erneut auf **Zulassen**.
3. Tippen Sie auf das Stecknadelsymbol ![Stecknadelsymbol](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). Je nach den im Bericht enthaltenen Daten können Sie nach Stadt, Bundesland/Kanton oder Land/Region filtern. Der Filter listet nur die Optionen auf, die mit Ihrer aktuellen Position übereinstimmen.
   
    ![Stecknadel-Filter](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>Warum sehe ich im Bericht keine Positionsmarkierungen?
Alle drei der folgenden Bedingungen müssen erfüllt sein, damit Positionsmarkierungen angezeigt werden. 

* Der Ersteller des Berichts hat in Power BI Desktop in mindestens einer Spalte [geografische Daten kategorisiert](../../desktop-mobile-geofiltering.md) (wie Stadt, Bundesland, Land/Region).
* Sie befinden sich an einem Standort, für den Daten in einer dieser Spalten vorhanden sind.
* Sie verwenden eines dieser mobilen Geräte:
  * iOS (iPad, iPhone, iPod)
  * Android-Smartphone
  * Windows 10-Smartphone (andere Windows 10-Geräte wie PCs und Tablets unterstützten geografische Filter nicht)

Weitere Informationen finden Sie unter [Einrichten von geografischen Filtern](../../desktop-mobile-geofiltering.md) in Power BI Desktop.

### <a name="next-steps"></a>Nächste Schritte
* [Connect to Power BI data from the real world](mobile-apps-data-in-real-world-context.md) (Verbinden mit realen Power BI-Daten mit den Apps für mobile Geräte)
* [Datenkategorisierung in Power BI Desktop](../../desktop-data-categorization.md) 
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

