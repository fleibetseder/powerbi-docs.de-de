---
title: Verwenden von Schaltflächen in Power BI
description: Durch Schaltflächen in Power BI Desktop können Sie Berichte und Dashboards erstellen, die sich wie Apps verhalten und die Einbindung von Benutzern verbessern.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a38b54bdacd0f60ee0151ad7c1a2084cebac2a37
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878709"
---
# <a name="using-buttons-in-power-bi"></a>Verwenden von Schaltflächen in Power BI
Durch das Verwenden von **Schaltflächen** in Power BI können Sie Berichte und Dashboards erstellen, die sich ähnlich wie Apps verhalten, und dadurch eine interaktive Umgebung erstellen, sodass die Benutzer auf Power BI-Elemente zeigen, klicken oder auf andere Weise mit diesen interagieren können. Sie können Schaltflächen zu Berichten in **Power BI Desktop** hinzufügen, und diese Berichte im Power BI-Dienst freigeben oder veröffentlichen, um Dashboards zu erstellen, die Benutzern ein App-ähnliches Verhalten bieten.

![Schaltflächen in Power BI](media/desktop-buttons/desktop-buttons_01.png)

Die Schaltflächen, die Sie in **Power BI Desktop** erstellen, stehen für die Verwendung in Berichten oder Dashboards zur Verfügung, die im **Power BI-Dienst** veröffentlicht werden.

## <a name="creating-buttons-in-reports"></a>Erstellen von Schaltflächen in Berichten
Klicken Sie für das Erstellen einer Schaltfläche in einem **Power BI Desktop**-Bericht auf das Menüband **Startseite** und dann auf **Schaltflächen**. Dadurch wird ein Dropdownmenü angezeigt, aus dem Sie die Schaltfläche wie in der folgenden Abbildung dargestellt aus mehreren Optionen auswählen können. 

![Hinzufügen einer Schaltfläche in Power BI Desktop](media/desktop-buttons/desktop-buttons_02.png)

Wenn Sie eine Schaltfläche erstellen und diese im Zeichenbereich des Berichts auswählen, zeigt der Bereich **Visualisierungen** Ihnen die Anpassungsmöglichkeiten der Schaltfläche an, um diese an Ihre Anforderungen anzupassen. Sie können beispielsweise den **Schaltflächentext** aktivieren oder deaktivieren, indem Sie den Schieberegler auf dieser Karte des Bereichs **Visualisierungen** bewegen. Sie können unter anderem das Symbol, die Füllung und den Titel der Schaltfläche ändern sowie die Aktion, die durchgeführt wird, wenn der Benutzer in einem Bericht oder Dashboard auf die Schaltfläche klickt.

![Formatieren einer Schaltfläche in Power BI Desktop](media/desktop-buttons/desktop-buttons_03.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Festlegen der Schaltflächeneigenschaften im Normalzustand, wenn darauf gezeigt wird oder wenn sie ausgewählt werden

Schaltflächen in Power BI können drei Zustände aufweisen: der Normalzustand (wenn nicht auf diese gezeigt wird und sie nicht ausgewählt sind), wenn darauf gezeigt oder wenn sie ausgewählt wird (häufig als *angeklickt* bezeichnet). Viele der Karten im Bereich **Visualisierungen** können auf Grundlage dieser drei Zustände geändert werden. Dadurch können Sie Ihre Schaltflächen flexibel anpassen.

Mithilfe folgender Karten im Bereich **Visualisierungen** können Sie die Formatierung oder das Verhalten einer Schaltfläche auf Grundlage der drei Zustände anpassen:

* Schaltflächentext
* Symbol
* Kontur
* Füllung

Erweitern Sie eine dieser Karten, und klicken Sie auf das Dropdownmenü, das im oberen Bereich der Karte angezeigt wird, um auszuwählen, wie die Schaltfläche für jeden Zustand angezeigt werden soll. Auf der folgenden Abbildung wird veranschaulicht, wie die erweiterte Karte **Gliederung** aussieht. Dabei zeigt das ausgewählte Dropdownmenü die drei Zustände an:

![Drei Zustände einer Schaltfläche in Power BI Desktop](media/desktop-buttons/desktop-buttons_04.png)


## <a name="select-the-action-for-a-button"></a>Auswählen der Aktion für eine Schaltfläche

Sie können auswählen, welche Aktion durchgeführt wird, wenn ein Benutzer auf eine Schaltfläche in Power BI klickt. Sie können über die Karte **Aktion** im Bereich **Visualisierungen** auf die Optionen für Schaltflächenaktionen zugreifen.

![Aktionen für eine Schaltfläche in Power BI](media/desktop-buttons/desktop-buttons_05.png)

Folgende Optionen sind für Schaltflächenaktionen verfügbar:

* Zurück
* Lesezeichen
* Q&A

Wenn der Benutzer auf **Zurück** klickt, wird zur vorherigen Seite des Berichts zurückgekehrt. Dies ist für Drilldownseiten besonders nützlich.

Wenn der Benutzer auf **Lesezeichen** klickt, wird die Berichtsseite angezeigt, die einem für den aktuellen Bericht definierten Lesezeichen zugeordnet ist. Lesen Sie [mehr über Lesezeichen in Power BI](desktop-bookmarks.md). 

Wenn der Benutzer im Dropdownmenü auf **Q&A** klickt, wird das Fenster **Q&A Explorer** (Q&A-Explorer) angezeigt. 

Für bestimmte Schaltflächen gibt es eine Standardaktion, die automatisch ausgewählt wird. Der Schaltflächentyp **Q&A** wählt beispielsweise automatisch **Q&A** als Standardaktion aus. Weitere Informationen zum **Q&A-Explorer** finden Sie in [diesem Blogbeitrag](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Sie können die Schaltflächen testen, die Sie für Ihren Bericht erstellen, indem Sie *STRG+Klick* auf die Schaltfläche anwenden, die Sie verwenden möchten. 

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Features, die Schaltflächen ähneln oder mit diesen interagieren, finden Sie in den folgenden Artikeln:

* [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)
* [Anzeigen einer Dashboardkachel oder eines Berichtsvisuals im Fokusmodus](consumer/end-user-focus.md)
* [Verwenden von Lesezeichen zum Teilen von Erkenntnissen und zum Erstellen von Präsentationen in Power BI](desktop-bookmarks.md)

