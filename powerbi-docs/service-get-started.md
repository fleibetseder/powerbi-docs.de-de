---
title: Erste Schritte mit dem Power BI-Dienst
description: Erste Schritte mit dem Power BI-Onlinedienst (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 007819ead82f558efa8179a49dfba9454558dfbb
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995169"
---
# <a name="tutorial-get-started-with-the-power-bi-service-apppowerbicom"></a>Tutorial: Erste Schritte mit dem Power BI-Dienst (app.powerbi.com)
Dieses Tutorial erleichtert Ihnen den Einstieg in den *Power BI-Dienst*. Damit Sie die Funktion des Power BI-Diensts im Hinblick auf die anderen Power BI-Angebote einordnen können, sollten Sie zunächst [Was ist Power BI?](power-bi-overview.md) lesen.

![Beziehung zwischen Power BI Desktop, dem Dienst und der mobilen Version](media/service-get-started/power-bi-components.png)

In diesem Tutorial führen Sie die folgenden Schritte aus:

> [!div class="checklist"]
> * Abrufen von Inhalten zu den ersten Schritten mit dem Power BI-Dienst.
> * Anmelden bei Ihrem Power BI-Onlinekonto oder Registrieren eines Kontos, wenn noch kein Konto vorhanden ist.
> * Öffnen des Power BI-Diensts.
> * Abrufen einiger Daten und Öffnen der Daten in der Berichtsansicht.
> * Verwenden dieser Daten, um Visualisierungen zu erstellen und als Bericht zu speichern.
> * Erstellen eines Dashboards, indem Kacheln aus dem Bericht angeheftet werden.
> * Hinzufügen einer weiteren Visualisierung zu Ihrem Dashboard mithilfe des Q&A-Tools für natürliche Sprache.
> * Bereinigen von Ressourcen durch Löschen des Datasets, des Berichts und des Dashboards.

## <a name="sign-up-for-the-power-bi-service"></a>Registrieren beim Power BI-Dienst
Wenn Sie noch kein Power BI-Konto besitzen, [registrieren Sie sich für eine kostenlose Power BI-Testversion](https://app.powerbi.com/signupredirect?pbi_source=web), bevor Sie beginnen.

Nachdem Sie ein Konto angelegt haben, geben Sie *app.powerbi.com* in Ihrem Browser ein, um den Power BI-Dienst zu öffnen. 

Hilfe zu Power BI Desktop finden Sie unter [Erste Schritte mit Power BI Desktop](desktop-getting-started.md). Hilfe zu Power BI-Version für Mobilgeräte finden Sie unter [Microsoft Power BI – Mobilgeräte](consumer/mobile/mobile-apps-for-mobile-devices.md).

> [!TIP]
> Sie möchten Ihre Trainingsgeschwindigkeit lieber selbst bestimmen? [Registrieren Sie sich auf EdX für unseren Kurs zur Datenanalyse und -visualisierung.](http://aka.ms/edxpbi)

Besuchen Sie unsere [Wiedergabeliste auf YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). Ein anschauliches Video zum Einstieg ist *Introduction to the Power BI service* (Einführung in den Power BI-Dienst):
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-the-power-bi-service"></a>Was ist der Power BI-Dienst?
Der Microsoft Power BI-Dienst wird gelegentlich auch als „Power BI Online“ oder „app.powerbi.com“ bezeichnet. Power BI hilft Ihnen, hinsichtlich der für Sie wichtigen Informationen auf dem neuesten Stand zu bleiben. Beim Power BI-Dienst verlieren Sie durch *Dashboards* nie den Überblick über Ihr Unternehmen. In Ihren Dashboards werden *Kacheln* angezeigt, die Sie auswählen können, um weitere Informationen in Form von *Berichten* zu erhalten. Stellen Sie Verbindungen mit mehreren *Datasets* her, um sämtliche relevanten Daten an einem Ort zusammenzuführen. Benötigen Sie Hilfe, um die Grundkomponenten zu verstehen, aus denen Power BI besteht? Weitere Informationen finden Sie unter [Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md).

Wenn Sie über wichtige Daten in Excel- oder CSV-Dateien verfügen, können Sie ein Power BI-Dashboard erstellen, um jederzeit informiert zu sein und Erkenntnisse mit anderen zu teilen.  Verfügen Sie über ein Abonnement für eine SaaS-Anwendung wie Salesforce?  Verschaffen Sie sich einen Vorsprung, indem Sie eine Verbindung mit Salesforce herstellen, um aus diesen Daten automatisch ein Dashboard zu erstellen, oder [sehen Sie sich die anderen SaaS-Anwendungen an](service-get-data.md), mit denen Sie eine Verbindung herstellen können. Wenn Sie einer Organisation angehören, überprüfen Sie, ob für Sie [Apps](service-create-distribute-apps.md) veröffentlicht wurden.

Informieren Sie sich über alle anderen Möglichkeiten zum [Abrufen von Daten für Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Schritt 1: Daten abrufen
Hier folgt ein Beispiel zum Abrufen von Daten aus einer CSV-Datei. Möchten Sie dieses Tutorial durchführen? [Herunterladen der CSV-Datei mit dem Finanzbeispiel](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Melden Sie sich bei Power BI an](http://www.powerbi.com/). Verfügen Sie über ein Konto? Keine Sorge: Sie können sich für eine kostenlose Testversion registrieren.
2. Power BI wird in Ihrem Browser geöffnet. Wählen Sie unten auf der linken Navigationsleiste **Daten abrufen** aus.

    Die Seite **Daten abrufen** wird geöffnet.   

3. Wählen Sie im Abschnitt **Neuen Inhalt erstellen** die Option **Dateien** aus. 
   
   ![Dateien abrufen](media/service-get-started/gs1.png)
4.  Wählen Sie **Lokale Datei** aus.
   
     ![Ansicht „Dateien abrufen > Dateien“](media/service-get-started/gs2.png)

5. Navigieren Sie zu der Datei auf Ihrem Computer, und wählen Sie dann **Öffnen** aus.

5. Für dieses Tutorial wählen Sie **Importieren** aus, um die Excel-Datei als Dataset hinzuzufügen, mit dem dann Berichte und Dashboards erstellt werden können. Wenn Sie **Hochladen** auswählen, wird die gesamte Excel-Arbeitsmappe in Power BI hochgeladen, sodass Sie sie öffnen und online in Excel bearbeiten können.
   
   ![Auswählen von „Importieren“](media/service-get-started/power-bi-import.png)
6. Wenn Ihr Dataset bereit ist, wählen Sie **Dataset anzeigen** aus, um es im Berichts-Editor zu öffnen. 

    ![Dialogfeld „Ihr Dataset ist bereit“](media/service-get-started/power-bi-gs.png)

    Da Sie noch keine Visualisierungen erstellt haben, ist der Zeichenbereich des Berichts leer.

    ![Leerer Zeichenbereich des Berichts](media/service-get-started/power-bi-report-editor.png)

7. Beachten Sie, dass es eine Option für die die **Leseansicht** in der oberen Navigationsleiste gibt. Da diese Option verfügbar ist, bedeutet dies, dass Sie sich zurzeit in der Bearbeitungsansicht befinden. 

    ![Option „Leseansicht“](media/service-get-started/power-bi-editing-view.png)

    In der Bearbeitungsansicht können Sie eigene Berichte erstellen und ändern, da Sie der *Besitzer* des Berichts sind. Das heißt, Sie sind ein *Ersteller*. Wenn Sie den Bericht für Kollegen freigeben, können diese mit dem Bericht nur in der Leseansicht interagieren. Dies bedeutet, dass sie *Anwender* sind. Weitere Informationen über [Leseansicht und Bearbeitungsansicht](consumer/end-user-reading-view.md).
    
    Ein [Überblick](service-the-report-editor-take-a-tour.md) stellt eine hervorragende Möglichkeit dar, sich mit dem Berichts-Editor vertraut zu machen.
 

## <a name="step-2-start-exploring-your-dataset"></a>Schritt 2: Untersuchen des Datasets
Nachdem die Verbindung mit den Daten hergestellt wurde, können Sie die Daten untersuchen.  Wenn Sie etwas gefunden haben, das für Sie von Interesse ist, können Sie ein Dashboard erstellen, um die Daten zu überwachen und Änderungen zu verfolgen. Sehen wir uns das einmal an.
    
1. Im Berichts-Editor verwenden Sie den Bereich **Felder** rechts auf der Seite, um eine Visualisierung zu erstellen. Aktivieren Sie die Kontrollkästchen **Gross Sales** (Bruttoumsatz) und **Date** (Datum).
   
   ![Liste „Felder“](media/service-get-started/fields.png)

    Power BI analysiert die Daten und erstellt eine Visualisierung. Wenn Sie zuerst **Date** ausgewählt haben, wird eine Tabelle angezeigt. Wenn Sie zuerst **Gross Sales** ausgewählt haben, wird ein Diagramm angezeigt. 

2. Wechseln Sie für Ihre Daten zu einer anderen Anzeigeart. Im Folgenden werden diese Daten als Liniendiagramm dargestellt. Wählen Sie im Bereich **Visualisierungen** das Symbol für das Liniendiagramm aus.
   
   ![Berichts-Editor mit ausgewähltem Liniendiagramm](media/service-get-started/gettingstart5new.png)

3. Dieses Diagramm sieht vielversprechend aus. *Heften wir es also an ein Dashboard an*. Zeigen Sie auf die Visualisierung, und wählen Sie das Stecknadelsymbol aus. Wenn Sie diese Visualisierung anheften, wird sie auf dem Dashboard gespeichert und fortlaufend aktualisiert, sodass Sie den aktuellen Wert auf einen Blick nachverfolgen können.
   
   ![Stecknadelsymbol](media/service-get-started/pinnew.png)

4. Da dieser Bericht neu ist, werden Sie aufgefordert, ihn zu speichern, bevor Sie eine Visualisierung an ein Dashboard anheften können. Weisen Sie dem Bericht einen Namen zu (z.B. *Umsatz im zeitlichen Verlauf*), und wählen Sie **Speichern und fortfahren** aus. 
   
   ![Dialogfeld „Bericht speichern“](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. Heften Sie das Liniendiagramm an ein neues Dashboard an, und nennen Sie es *Finanzbeispiel für Tutorial*. 
   
   ![Benennen des Berichts](media/service-get-started/power-bi-pin.png)
   
6. Wählen Sie **Anheften**aus.
   
    Eine Meldung (in der Nähe der oberen rechten Ecke) weist Sie darauf hin, dass die Visualisierung Ihrem Dashboard erfolgreich als Kachel hinzugefügt wurde.
   
    ![Dialogfeld „An das Dashboard angeheftet“](media/service-get-started/power-bi-pin-success.png)

7. Wählen Sie **Zum Dashboard wechseln** aus. Sie sehen, dass das Liniendiagramm als Kachel an das neue Dashboard angeheftet ist. Perfektionieren Sie das Dashboard, indem Sie weitere Visualisierungskacheln hinzufügen und [Kacheln umbenennen, verknüpfen, neu positionieren und in der Größe ändern](service-dashboard-edit-tile.md).
   
   ![Dashboard mit angehefteter Visualisierung](media/service-get-started/power-bi-new-dashboard.png)
   
8. Wählen Sie die neue Kachel auf dem Dashboard aus, um zum Bericht zurückzukehren. Sie kehren in Power BI zum Berichts-Editor in der Leseansicht zurück. Um erneut in die Bearbeitungsansicht zu wechseln, wählen Sie auf der oberen Navigationsleiste **Bericht bearbeiten** aus. Wenn Sie sich in der Bearbeitungsansicht befinden, können Sie weiterhin das Durchsuchen und Anheften von Kacheln fortsetzen. 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>Schritt 3:  Fortsetzen der Untersuchung mithilfe von Q&A (Abfragen in natürlicher Sprache)
1. Stellen Sie im Feld für Fragen und Antworten eine Frage, um eine schnelle Untersuchung Ihrer Daten durchzuführen. Das Q&A-Fragefeld befindet sich oben auf dem Dashboard (**Stellen Sie eine Frage zu Ihren Daten**) und im Bericht auf der oberen Navigationsleiste (**Frage stellen**). Geben Sie z.B. Folgendes in das Q&A-Feld ein: *Welches Segment weist den höchsten Umsatz auf?*
   
   ![Q&A-Zeichenbereich](media/service-get-started/powerbi-qna.png)

2. Q&A sucht nach einer Antwort und präsentiert diese in Form einer Visualisierung. Wählen Sie das Anheftsymbol aus ![Stecknadelsymbol](media/service-get-started/pbi_pinicon.png) Zum Anzeigen dieser Visualisierung auf dem Dashboard.
3. Heften Sie die Visualisierung an das Dashboard **Financial Sample for tutorial** (Finanzbeispiel für das Tutorial) an.
   
    ![Dialogfeld „An das Dashboard anheften“](media/service-get-started/power-bi-pin2.png)

4. Kehren Sie zum Dashboard zurück, auf dem die neue Kachel angezeigt wird.

   ![Dashboard mit angeheftetem Diagramm](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen
Nachdem Sie das Tutorial abgeschlossen haben, können Sie das Dataset, den Bericht und das Dashboard löschen. 

1. Klicken Sie auf der linken Navigationsleiste auf **My Workspace** (Mein Arbeitsbereich).
2. Klicken Sie auf die Registerkarte **Dataset**, und suchen Sie nach dem Dataset, das Sie für dieses Tutorial importiert haben.  
3. Wählen Sie die Auslassungspunkte (...) und dann **Löschen** aus.

    ![Dataset löschen](media/service-get-started/power-bi-delete.jpg)

    Wenn Sie das Dataset löschen, löscht Power BI auch den Bericht und das Dashboard. 


## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Herstellen einer Verbindung mit den verwendeten Onlinediensten mi Power BI](service-connect-to-services.md)

