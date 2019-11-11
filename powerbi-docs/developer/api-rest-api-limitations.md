---
title: Einschränkungen für Power BI-REST-API
description: 'Für die Power BI-REST-API gelten die folgenden Einschränkungen:'
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 730123ba86e00e944a543feda77308c545a5b53e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875923"
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