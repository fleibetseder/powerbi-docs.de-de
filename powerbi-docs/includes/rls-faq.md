---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560950"
---
## <a name="faq"></a>HÄUFIG GESTELLTE FRAGEN
**Frage:** Was passiert, wenn ich im Power BI-Dienst bereits Rollen und Regeln für ein Dataset erstellt habe? Werden sie weiterhin funktionieren, wenn ich sie so belasse?  
**Antwort:** Nein. Visuals werden nicht richtig gerendert. Sie müssen die Rollen und Regeln in Power BI Desktop neu erstellen und anschließend im Power BI-Dienst veröffentlichen.

**Frage:** Kann ich solche Rollen für Analysis Services-Datenquellen erstellen?  
**Antwort:** Das ist möglich, wenn Sie die Daten in Power BI Desktop importiert haben. Wenn Sie eine Liveverbindung verwenden, werden Sie RLS nicht im Power BI-Dienst konfigurieren können. Dies wird im lokalen Analysis Services-Modell definiert.

**Frage:** Kann ich mit der RLS die Spalten oder Measures einschränken, auf die Benutzer Zugriff haben?  
**Antwort:** Nein. Wenn ein Benutzer Zugriff auf eine bestimmte Datenzeile hat, sind alle Datenspalten dieser Zeile für ihn sichtbar.

**Frage:** Kann ich mit der RLS Detaildaten in Visuals ausblenden und Zugriff auf in Visuals zusammengefasste Daten erteilen?  
**Antwort:** Nein. Sie sichern einzelne Datenzeilen, für die Benutzer werden jedoch immer entweder die Details oder die zusammengefassten Daten angezeigt.

