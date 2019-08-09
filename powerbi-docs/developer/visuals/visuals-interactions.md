---
title: Visualinteraktionen
description: Überprüfen, ob Power BI-Visuals Visualinteraktionen zulassen
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424491"
---
# <a name="visuals-interactions"></a>Visualinteraktionen

Visuals können den Wert des allowInteractions-Flags abfragen, das angibt, ob das Visual Visualinteraktionen zulassen soll.
Beispielsweise sind Visuals während der Anzeige oder Bearbeitung von Berichten interaktiv, bei der Anzeige in einem Dashboard aber nicht.
Interaktionen können beispielsweise Klick-, Schwenk-, Zoom-, Auswahlaktionen und andere umfassen.
Beachten Sie, dass QuickInfos unabhängig von diesem Flag in allen Szenarien aktiviert werden sollten.

Das allowInteractions-Flag wird während der Initialisierung des Visuals in Form eines booleschen Werts als Member der IVisualHost-Schnittstelle übergeben.

In allen Power BI-Szenarien, in denen Visuals nicht interaktiv sein dürfen (beispielsweise in Dashboardkacheln), wird das allowInteractions-Flag auf „false“ festgelegt.
Andernfalls (z. B. bei Berichten) wird allowInteractions auf „true“ festgelegt.

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
