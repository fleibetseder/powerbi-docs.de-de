---
title: Einführung in Q&A-Tools zum Trainieren von Power BI Q&A (Vorschau)
description: Einführung in Power BI Q&A-Tools
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/17/2019
ms.author: mohaali
ms.openlocfilehash: 17d0a68782f34c09286be5ebe020668a15061ee4
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874934"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>Einführung in Q&A-Tools zum Trainieren von Power BI Q&A (Vorschau)

Mithilfe von Power BI Q&A-*Tools* können Sie die Funktionen für natürliche Sprache für Ihre Benutzer verbessern. Als Designer oder Administrator interagieren Sie mit der Engine für natürliche Sprache und nehmen Verbesserungen in drei Bereichen vor: 

- Überprüfen von Fragen, die Benutzer stellen
- Trainieren der Q&A-Engine im Hinblick auf das Verstehen von Fragen
- Verwalten von Begriffen, die Sie der Q&A-Engine beigebracht haben

Zusätzlich zu diesen dedizierten Toolfunktionen finden Sie auf der Registerkarte **Modellierung** in Power BI Desktop weitere Optionen:  

- Synonyme
- Zeilenbeschriftungen
- Für Q&A ausblenden
- Konfigurieren des linguistischen Schemas (erweitert)

## <a name="get-started-with-qa-tooling"></a>Erste Schritte mit Q&A-Tools

Q&A-Tools sind nur in Power BI Desktop verfügbar und unterstützen derzeit ausschließlich den Importmodus.

1. Öffnen Sie Power BI Desktop, und verwenden Sie Q&A, um ein Visual zu erstellen. 
2. Klicken Sie am Rand des Visuals auf das Zahnradsymbol. 

    ![Q&A-Visual: Zahnradsymbol](media/qna-visual-gear.png)

    Dann wird die Seite „Erste Schritte“ geöffnet.  

    ![Q&A: „Erste Schritte“](media/qna-tooling-dialog.png)

### <a name="review-questions"></a>Fragen zur Überprüfung

Klicken Sie auf **Fragen prüfen**, um eine Liste der Datasets aufzurufen, die im Power BI-Dienst für Ihren Mandanten verwendet werden. Auf der Seite **Fragen prüfen** werden auch der Besitzer des Datasets, der Arbeitsbereich und das Datum der letzten Aktualisierung angezeigt. Auf dieser Seite können Sie ein Dataset auswählen und prüfen, welche Fragen die Benutzer gestellt haben. Außerdem werden Wörter angezeigt, die nicht erkannt wurden. Es werden alle Daten der letzten 28 Tage angezeigt.

![Q&A: Fragen prüfen](media/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>Q&A trainieren

Im Abschnitt **Q&A-Training** können Sie die Q&A-Engine im Hinblick auf das Erkennen von Wörtern trainieren. Geben Sie zunächst eine Frage ein, die mindestens ein Wort enthält, das die Q&A-Engine nicht erkannt hat. Q&A fordert Sie dazu auf, diesen Begriff zu definieren. Geben Sie entweder einen Filter oder einen Feldnamen ein, der zu diesem Begriff passt. Q&A interpretiert anschließend die ursprüngliche Frage neu. Wenn Sie mit den Ergebnissen zufrieden sind, speichern Sie Ihre Eingabe. Weitere Informationen finden Sie unter [Q&A-Training](q-and-a-tooling-teach-q-and-a.md).

![Q&A-Training: Synonymvorschau](media/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>Verwalten von Begriffen

Alle Elemente, die Sie dem Abschnitt „Q&A-Training“ entnommen und gespeichert haben, werden hier angezeigt, sodass Sie die von Ihnen definierten Begriffe prüfen oder löschen können. Derzeit ist es nicht möglich, vorhandene Definitionen zu bearbeiten. Wenn Sie einen Begriff neu definieren möchten, müssen Sie diesen löschen und einen neuen Eintrag erstellen.

![Q&A: Verwalten von Begriffen](media/qna-manage-terms.png)

## <a name="other-qa-settings"></a>Weitere Q&A-Einstellungen

### <a name="bulk-synonyms"></a>Mehrere Synonyme

Die Registerkarte **Modellierung** in Power BI Desktop umfasst noch weitere Optionen zur Verbesserung der Q&A-Funktionen. 

1. Klicken Sie in Power BI Desktop auf die Ansicht „Modellierung“.

2. Klicken Sie auf ein Feld oder eine Tabelle, um den Bereich **Eigenschaften** anzuzeigen.  In diesem Bereich, der auf der rechten Seite der Canvas angezeigt wird, finden Sie mehrere Q&A-Aktionen. Eine der Optionen heißt **Synonyme**. Im Feld **Synonyme** können Sie ganz einfach Alternativen für die ausgewählte Tabelle oder das ausgewählte Feld definieren. Sie können zwar auch im Abschnitt **Q&A-Training** des Dialogfelds „Tooling“ (Tools) Synonyme definieren, aber es geht häufig schneller, wenn Sie die Synonyme für mehrere Felder in einer Tabelle über dieses Feld festlegen.

    ![Q&A-Modellierung: Bereich „Synonyme“](media/qna-modelling-pane-synonyms.png)

3. Wenn Sie mehrere Synonyme für ein einzelnes Feld definieren möchten, trennen Sie die einzelnen Synonyme durch Kommas voneinander ab.

### <a name="hide-from-qa"></a>Für Q&A ausblenden

Sie können auch Felder und Tabellen ausblenden, damit sie nicht in den Q&A-Ergebnissen angezeigt werden. 

1. Klicken Sie in Power BI Desktop auf die Ansicht „Modellierung“.

2. Klicken Sie auf ein Feld oder eine Tabelle, um den Bereich **Eigenschaften** anzuzeigen, und legen Sie die Option **Ist verborgen** auf **On** (Ein) fest.

    Q&A berücksichtigt diese Einstellung und sorgt dafür, dass das Feld nicht erkannt wird. Sie sollten beispielsweise ID-Felder und Fremdschlüssel ausblenden, um unnötige Duplikate von Feldern mit demselben Namen zu vermeiden. Auch wenn Sie das Feld ausblenden, können Sie es weiterhin außerhalb von Q&A in Visuals in Power BI Desktop verwenden.

### <a name="set-a-row-label"></a>Festlegen einer Zeilenbeschriftung

Mithilfe einer Zeilenbeschriftung können Sie definieren, welche Spalte (oder welches *Feld*) eine einzelne Zeile in einer Tabelle am besten beschreibt. Für eine Tabelle mit dem Namen „Kunde“ lautet die Zeilenbeschriftung z. B. in der Regel „Anzeigename“. Durch die Angabe dieser zusätzlichen Metadaten kann Q&A nützlichere Visuals erstellen, wenn Benutzer z. B. die Aufforderung „Umsätze nach Kunden sortiert anzeigen“ eingeben. Q&A kann dann die Beschriftung „Anzeigename“ verwenden, anstatt den Begriff „Kunde“ als eine Tabelle zu behandeln, und ein Balkendiagramm mit den Umsätzen der einzelnen Kunden anzeigen. Sie können nur die Zeilenbeschriftung für die Ansicht „Modellierung“ festlegen. 

1. Klicken Sie in Power BI Desktop auf die Ansicht „Modellierung“.

2. Klicken Sie auf eine Tabelle, um den Bereich **Eigenschaften** anzuzeigen.

3. Wählen Sie im Feld **Zeilenbeschriftung** ein Feld aus.

## <a name="configure-the-linguistic-schema-advanced"></a>Konfigurieren des linguistischen Schemas (erweitert)

In Power BI können Sie die Engine für natürliche Sprache vollständig in Q&A trainieren und erweitern, einschließlich der Bewertung und Gewichtung der zugrunde liegenden Ergebnisse in natürlicher Sprache. Weitere Informationen finden Sie unter [Bearbeiten des linguistischen Schemas für Q&A und Hinzufügen von Ausdrücken](q-and-a-tooling-advanced.md).

## <a name="next-steps"></a>Nächste Schritte

Es gibt verschiedene bewährte Methoden zur Verbesserung der Engine für natürliche Sprache. Weitere Informationen finden Sie im folgenden Artikel:

* [Q&A: Bewährte Methoden](q-and-a-best-practices.md)
