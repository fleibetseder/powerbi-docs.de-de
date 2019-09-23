---
title: Berichtsansicht in Power BI Desktop
description: Berichtsansicht in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: c76dfc45437fdc2406c89e41a4a076d9ef4e7a44
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71142177"
---
# <a name="report-view-in-power-bi-desktop"></a>Berichtsansicht in Power BI Desktop
Wenn Sie bereits mit Power BI gearbeitet haben, wissen Sie, wie einfach Berichte erstellt werden können, die dynamische Perspektiven und Einblicke in Ihre Daten bereitstellen. Power BI verfügt in Power BI Desktop zudem über weitere komplexe Funktionen. Mit Power BI Desktop können Sie komplexe Abfragen erstellen, Daten aus mehreren Quellen kombinieren, Beziehungen zwischen Tabellen erstellen usw.

Power BI Desktop enthält die **Berichtsansicht**, in der sich beliebig viele Berichtseiten mit Visualisierungen erstellen lassen. Die Berichtsansicht bietet größtenteils dieselbe Benutzererfahrung wie die Bearbeitungsansicht für Berichte im Power BI-Dienst. Sie können Visualisierungen verschieben, kopieren, einfügen, zusammenführen usw.

Der Unterschied besteht darin, dass Sie in Power BI Desktop mit Ihren Abfragen und Ihrem Modell arbeiten können, sodass Ihre Daten optimale Einblicke in Ihre Berichte ermöglichen. Sie können die Power BI Desktop-Datei dann jederzeit entweder auf dem lokalen Laufwerk oder in der Cloud speichern.

## <a name="lets-take-a-look"></a>Schauen wir uns das mal an!
Wenn Sie zum ersten Mal Daten in Power BI Desktop laden, wird die **Berichtsansicht** mit einem leeren Zeichenbereich angezeigt.

![Power BI Desktop](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

Sie können zwischen der **Berichtsansicht**, der **Datenansicht** und der **Beziehungsansicht** wechseln, indem Sie auf die Symbole auf der linken Navigationsleiste klicken:

![Symbol für Berichtsansicht](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Nachdem Sie einige Daten hinzugefügt haben, können Sie Felder zu einer neuen Visualisierung im Zeichenbereich hinzufügen.

![Hinzufügen eines Visuals durch Ziehen aus dem Bereich „Felder“](media/desktop-report-view/pbid_reportview_addvis.gif)

Wenn Sie den Typ der Visualisierung ändern möchten, können Sie ihn auf dem Menüband über die Gruppe **Visualisierung** auswählen, oder Sie klicken mit der rechten Maustaste und wählen einen anderen Typ über das Symbol **Visualisierungstyp ändern** aus.

![Ändern eines Visuals durch Auswahl eines neuen Visuals](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Experimentieren Sie mit den verschiedenen Visualisierungstypen, um einen Eindruck zu erhalten. Es ist wichtig, dass die Visualisierungen die in Ihren Daten enthaltenen Informationen verständlich zum Ausdruck bringen.

Ein Bericht verfügt zu Beginn über mindestens eine leere Seite. Die Seiten werden im Navigationsbereich direkt links neben dem Zeichenbereich angezeigt. Sie können einer Seite beliebige Arten von Visualisierungen hinzufügen, aber es ist wichtig, dies nicht zu übertreiben. Zu viele Visualisierungen auf einer Seite wirken überladen und unübersichtlich, sodass entsprechende Informationen schwer zu finden sind. Sie können Ihrem Bericht neue Seiten hinzufügen. Klicken Sie im Menüband einfach auf **Neue Seite**.

![Symbol für neue Seite](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Klicken Sie auf das **X** auf der Registerkarte der Seite am unteren Rand der Berichtsansicht, um eine Seite zu löschen.

![Hinzufügen einer Seite zu einem Bericht](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Berichte und Visualisierungen können nicht an ein Dashboard aus Power BI Desktop angeheftet werden. Dazu müssen Sie eine [Veröffentlichung aus Power BI Desktop](desktop-upload-desktop-files.md) auf Ihre Power BI-Website durchführen.

## <a name="copy-and-paste-between-reports"></a>Kopieren und Einfügen zwischen Berichten

Sie können ein Visual in einem Power BI Desktop-Bericht auf einfache Weise kopieren und in einen anderen Bericht einfügen. Kopieren Sie hierzu einfach das Berichtvisual mit der Tastenkombination **STRG+C**, und fügen Sie es dann mit **STRG+V** in den anderen Power BI Desktop-Bericht ein. Sie können in einem Arbeitsschritt jeweils nur ein Visual auswählen, oder Sie wählen alle Visuals auf einer Seite zum Kopieren aus und fügen die Visuals anschließend in den Power BI Desktop-Zielbericht ein. 

Die Möglichkeit zum Kopieren und Einfügen ist nützlich für Benutzer, die häufig mehrere Berichte erstellen und aktualisieren müssen. Bei Kopiervorgängen zwischen Dateien werden alle explizit im Formatierungsbereich festgelegten Einstellungen und Formatierungen für das Ziel übernommen. Visuelle Elemente hingegen, die auf einem Design oder den Standardeinstellungen basieren, werden automatisch an das Thema des Zielberichts angepasst. Wenn Sie also über ein Visual verfügen, dass in Formatierung und Aussehen genau Ihren Anforderungen entspricht, können Sie dieses Visual einfach kopieren und in neue Berichte einfügen. Die gesamte Formatierungsarbeit bleibt erhalten.

Wenn sich die Felder in Ihrem Modell unterscheiden, wird ein Fehler zum Visual angezeigt, und Sie werden in einer Warnung darüber informiert, welche Felder nicht vorhanden sind. Der Fehler ähnelt der Meldung, die beim Löschen eines Felds im Modell für ein Visual angezeigt wird. 

![Fehler beim Kopieren/Einfügen eines Visuals: kein Datenfeld](media/desktop-report-view/report-view_07.png)

Um den Fehler zu beheben, ersetzen Sie einfach die fehlerhaften Felder durch Felder aus dem Modell des Berichts, in den Sie das Visual eingefügt haben. Wenn Sie ein benutzerdefiniertes Visual verwenden, müssen Sie auch dieses benutzerdefinierte Visual in den Zielbericht importieren.




## <a name="hide-report-pages"></a>Ausblenden von Berichtsseiten

Wenn Sie einen Bericht erstellen, können Sie Seiten aus diesem verbergen. Dies kann nützlich sein, wenn Sie zugrunde liegende Daten oder Visuals in einem Bericht erstellen müssen, diese Seiten jedoch nicht für Dritte sichtbar sein sollen, also wenn Sie z.B. Tabellen oder unterstützende Visuals erstellen, die auf anderen Berichtsseiten verwendet werden. Es gibt viele weitere kreative Gründe dafür, eine Berichtsseite zunächst zu erstellen und dann aus einem Bericht auszublenden, den Sie veröffentlichen möchten. 

Das Ausblenden einer Berichtsseite ist einfach. Klicken Sie einfach mit der rechten Maustaste auf die Registerkarte „Berichtsseite“, und klicken Sie im angezeigten Menü auf **Ausblenden**.

![Option zum Ausblenden der Seite](media/desktop-report-view/report-view_05.png)

Sie sollten Folgendes bedenken, wenn Sie eine Berichtsseite ausblenden:

* Eine ausgeblendete Berichtsansicht wird in **Power BI Desktop** weiterhin angezeigt. Der Titel der Seite ist allerdings abgeblendet. In der folgenden Abbildung ist Seite 4 ausgeblendet.

    ![Ausgeblendete Seite wird abgeblendet dargestellt](media/desktop-report-view/report-view_06.png)

* Eine ausgeblendete Berichtsseite wird Ihnen *nicht* angezeigt, wenn Sie den Bericht im **Power BI-Dienst** anzeigen.

* Beim Ausblenden einer Berichtsseite handelt es sich *nicht* um eine Sicherheitsmaßnahme. Benutzer können weiterhin auf die Seite zugreifen, und Inhalt ist weiterhin über Drillthroughs und andere Methoden verfügbar.

* Wenn eine Seite im Ansichtsmodus ausgeblendet ist, werden keine Navigationspfeile für den Ansichtsmodus angezeigt.

