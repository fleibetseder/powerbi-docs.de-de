---
title: Landing Page
description: Hinzufügen einer Landing Page zu Power BI-Visuals
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 44cc9314b31803c97d3203d4aab846685d8f88fa
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424882"
---
# <a name="landing-page"></a>Landing Page

Mit API 2.3.0 können Sie dem Visual eine Landing Page hinzufügen. Dazu fügen Sie den Funktionen `supportsLandingPage` hinzu und legen dafür „true“ fest. Dadurch wird das Visual sogar initialisiert und aktualisiert, bevor Sie ihm Daten hinzufügen (d. h., es wird kein Wasserzeichen mehr angezeigt). So können Sie Ihre eigene Landing Page entwerfen und im Visual anzeigen lassen, solange es keine Daten enthält.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Beispiel

![Screenshot einer Landing Page](./media/landing-page.png)
