---
title: Auf Ausdrücken beruhende Titel in Power BI Desktop
description: Erstellen Sie dynamische Titel in Power BI Desktop, die geändert werden basierend auf den programmatischen Ausdrücken, bedingte programmgesteuerte Formatierung verwenden
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769746"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Auf Ausdrücken beruhende Titel in Power BI Desktop

Sie können dynamisch erstellen Titel für Ihre Power BI-Visualisierungen angepasst. Erstellen Sie die Data Analysis Expressions (DAX) basierend auf Feldern, Variablen und andere Programmierelemente, können Ihre Visualisierung Titel automatisch anpassen, je nach Bedarf. Diese Änderungen basieren auf Filtern, Auswahl, oder andere Benutzerinteraktionen und Konfigurationen.

![Screenshot von Power BI Desktop bedingte Formatierung-option](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Erstellen dynamische Titel, bezeichnet *Titel auf Ausdrücken beruhende*, ist einfach. 

## <a name="create-a-field-for-your-title"></a>Erstellen Sie ein Feld für den Titel

Der erste Schritt beim Erstellen eines Titels auf Ausdrücken beruhende ist zum Erstellen eines Felds in Ihrem Modell für den Titel zu verwenden. 

Es gibt diverse kreative Möglichkeiten, Ihre visual Titel widerspiegeln, was Sie sagen soll, oder was express werden soll. Werfen wir einen Blick auf einige Beispiele.

Sie können einen Ausdruck erstellen, den Änderungen anhand der Filterkontext, die das visuelle Element für den Namen des Produkts Marke empfängt. Die folgende Abbildung zeigt die DAX-Formel für ein solches Feld.

![Screenshot der DAX-Formel](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Ein weiteres Beispiel ist einen dynamische Titel verwenden, den Änderungen auf die Sprache oder Kultur des Benutzers basieren. Sie können sprachspezifische Titel in einem DAX-Measure erstellen, mit der `USERCULTURE()` Funktion. Diese Funktion gibt den Kulturcode für den Benutzer basierend auf deren Betriebssystem oder Browsereinstellungen. Sie können die folgende DAX-Switch-Anweisung verwenden, auf den richtigen Wert für die übersetzten. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Oder rufen Sie die Zeichenfolge aus einer Nachschlagetabelle, die alle die Übersetzungen enthält. Platzieren Sie diese Tabelle im Modell. 

Dies sind nur einige Beispiele, die Sie verwenden können, um dynamische, auf Ausdrücken beruhende Titel für Ihre Visualisierungen in Power BI Desktop zu erstellen. Was Sie tun können, mit Ihrem Titel werden nur durch Ihre Vorstellungskraft und Ihr Modell beschränkt.


## <a name="select-your-field-for-your-title"></a>Wählen Sie das Feld für den Titel

Nachdem Sie den DAX-Ausdruck für das Feld, die Sie in Ihrem Modell erstellen erstellt haben, müssen Sie sie auf den Titel des Visuals anwenden.

Wählen Sie das Feld, und wenden Sie es, wechseln Sie zu der **Visualisierungen** Bereich. In der **Format** wählen Sie im Bereich **Titel** um die Optionen für das visuelle Element anzuzeigen. 

Wenn Sie mit der rechten Maustaste **Titeltext**, ein Kontextmenü angezeigt, die Sie auswählen können ***fx* bedingte Formatierung**. Wenn Sie das Menüelement im Auswählen einer **Titeltext** Dialogfeld wird angezeigt. 

![Screenshot des Dialogfeld titeltextfeld](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Aus diesem Fenster können Sie das Feld auswählen, das Sie erstellt haben, um für den Titel zu verwenden.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Es gibt einige Einschränkungen bei der die aktuelle Implementierung von auf Ausdrücken beruhende Titel für visuelle Elemente:

* Auf Ausdrücken beruhende Formatierung wird derzeit auf Python-Visualisierungen, R-Visualisierungen oder die wichtigen Einflussfaktoren Visual nicht unterstützt.
* Das Feld für den Titel erstellten muss es sich um einen Zeichenfolgen-Datentyp sein. Measures, die Zahlen oder Datum/Uhrzeit (oder einen anderen Datentyp) zurückgeben werden derzeit nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel wurde beschrieben, wie DAX-Ausdrücke zu erstellen, die die Titel Ihrer Visuals in dynamischen Felder zu, die sich ändern können aktivieren, während Benutzer mit Ihren Berichten interagieren. In den folgenden Artikeln hilfreich auch sein.

* [Verwenden von Cross-Report-Drillthrough im Power BI Desktop](desktop-cross-report-drill-through.md)
* [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)