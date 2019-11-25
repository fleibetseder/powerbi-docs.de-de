---
title: Einschränkungen für Power BI-REST-API
description: 'Für die Power BI-REST-API gelten die folgenden Einschränkungen:'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 97745d93de771d4888dd97717a5e8a8d2d6f5c7c
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265641"
---
# <a name="power-bi-rest-api-limitations"></a>Einschränkungen für Power BI-REST-API  
  
**Bereitstellen von Zeilen mit POST**
  
* Max. 75 Spalten
* Max. 75 Tabellen
* Max. 10.000 Zeilen pro einzelner POST-Zeilenanforderung  
* 1\.000.000 Zeilen pro Stunde und Dataset hinzugefügt  
* Max. 5 ausstehende POST-Zeilenanforderungen pro Dataset  
* 120 POST-Zeilenanforderungen pro Minute und Dataset
* 120 POST-Zeilenanforderungen pro Stunde und Dataset, wenn die Tabelle aus mindestens 250.000 Zeilen besteht
* Max. 200.000 Zeilen pro Tabelle im FIFO-Dataset gespeichert
* Max. 5.000.000 Zeilen pro Tabelle in einem Dataset ohne Aufbewahrungsrichtlinie gespeichert  
* 4\.000 Zeichen pro Wert für Zeichenfolgenspalten in POST-Zeilenvorgängen
  
## <a name="see-also"></a>Siehe auch

[Dienst- und andere Einschränkungen für Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Übersicht über Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/)