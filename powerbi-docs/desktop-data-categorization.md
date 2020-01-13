---
title: Datenkategorisierung in Power BI Desktop
description: Datenkategorisierung in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ef3191d77e2aeb89ff97468bd4bfdc07b0d7afb8
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761339"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Festlegen von Datenkategorien in Power BI Desktop
In **Power BI Desktop** können Sie die Kategorie der Daten für eine Spalte angeben, damit Power BI Desktop weiß, wie es seine Werte in einer Visualisierung behandeln soll.

Beim Importieren von Daten in Power BI Desktop werden nicht nur die eigentlichen Daten abgerufen, sondern auch Informationen, wie z. B. die Tabellen- und Spaltennamen, ob es sich um einen primären Schlüssel handelt usw.  Diese Informationen nutzt Power BI Desktop, um einige Annahmen darüber aufzustellen, welche Standardbedingungen bei der Erstellung einer Visualisierung für Sie von Vorteil sein könnten. 

Beispiel: Wenn Power BI Desktop erkennt, dass eine Spalte numerische Werte enthält, die Sie wahrscheinlich auf irgendeine Weise aggregieren möchten, wird diese im Wertebereich platziert. Oder bei einer Spalte mit Datums- und Uhrzeitwerten wird davon ausgegangen, dass Sie diese wahrscheinlich als Zeit-Hierarchie-Achse in einem Liniendiagramm verwenden.

Es gibt jedoch einige Fälle, die etwas komplizierter sind, wie z. B. Geografie. Betrachten Sie die folgende Tabelle aus einem Excel-Arbeitsblatt:

![](media/desktop-data-categorization/datacategorizationtable.png)

Soll Power BI Desktop die Codes in der Spalte „GeoCode“ als Abkürzung für ein Land oder einen US-Bundesstaat behandeln?  Dies ist nicht klar, da ein solcher Code beides bedeuten kann.  Beispielsweise kann AL Alabama oder Albanien bedeuten, AR kann Arkansas oder Argentinien bedeuten, oder CA kann Kalifornien oder Kanada bedeuten. Dies macht einen Unterschied, wenn das Feld „GeoCode“ auf einer Karte dargestellt werden soll.  Soll Power BI Desktop ein Bild der Welt mit hervorgehoben angezeigten Ländern oder ein Bild der USA mit hervorgehoben angezeigten Bundesstaaten anzeigen?  Für solche Daten können Sie eine Datenkategorie angeben. Durch die Kategorisierung von Daten werden die Informationen, die Power BI-Desktop zur Bereitstellung der besten Visualisierung verwenden kann, noch weiter verfeinert.  

**So geben Sie eine Datenkategorie an**

1. In der Berichtsansicht oder der Datenansicht wählen Sie in der Liste **Felder** das Feld aus, das nach einer anderen Kategorisierung sortiert werden soll.
2. Klicken Sie im Menüband auf der Registerkarte **Modellierung** auf die Dropdownliste **Datenkategorie:** .  Daraufhin wird eine Liste der möglichen Kategorien angezeigt, die Sie für die Spalte auswählen können.  Möglicherweise sind einige Optionen deaktiviert, wenn sie mit dem aktuellen Datentyp der Spalte nicht funktionieren.  Beispiel: Bei einer Spalte mit einem binären Datentyp erlaubt Power BI Desktop Ihnen nicht, geografische Datenkategorien auszuwählen. 

![](media/desktop-data-categorization/datacategorization.gif)

Und das ist auch schon alles!  Jedes Verhalten, das normalerweise in ein visuelles Objekt einfließt, funktioniert jetzt automatisch.  

Möglicherweise möchten Sie auch das [geografische Filtern für mobile Power BI-Apps](desktop-mobile-geofiltering.md) kennenlernen.

