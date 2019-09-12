---
title: Visuelle Interaktionen in Power BI-Visuals
description: In diesem Artikel wird erläutert, wie Sie überprüfen können, ob Power BI-Visuals visuelle Interaktionen zulassen sollten.
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f2fb2d451deb63b5e9c08472654e28d0e1a469db
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236628"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Visuelle Interaktionen in Power BI-Visuals

Visuals können den Wert des `allowInteractions`-Flags abfragen, das angibt, ob das Visual visuelle Interaktionen zulassen soll. Beispielsweise sind Visuals während der Anzeige oder Bearbeitung von Berichten interaktiv, bei der Anzeige in einem Dashboard aber nicht. Interaktionen können beispielsweise *Klick*-, *Schwenk*-, *Zoom*- und *Auswahlaktionen* umfassen. 

> [!NOTE]
> Sie sollten QuickInfos in allen Szenarios aktivieren, unabhängig davon, welches Flag angegeben wird.

Das `allowInteractions`-Flag wird während der Initialisierung des Visuals in Form eines booleschen Werts als Member der IVisualHost-Schnittstelle übergeben.

In allen Power BI-Szenarios, in denen Visuals nicht interaktiv sein dürfen (beispielsweise in Dashboardkacheln), ist das `allowInteractions`-Flag auf `false` festgelegt. Ansonsten (beispielsweise in einem Bericht) ist das `allowInteractions`-Flag auf `true` festgelegt.

Weitere Informationen finden Sie im [SampleBarChart-Visualrepository](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
