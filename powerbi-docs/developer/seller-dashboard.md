---
title: Übermitteln eines Power BI-Visuals an AppSource über das Verkäuferdashboard
description: Übermitteln eines Power BI-Visuals an AppSource über das Verkäuferdashboard
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223665"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Übermitteln eines Power BI-Visuals an AppSource über das Verkäuferdashboard

Vor der Übermittlung an AppSource müssen Sie eine E-Mail mit der **PBIVIZ**-Datei und der **PBIX**-Datei an das Power BI-Team senden. Dies ist erforderlich, damit das Power BI-Team die Dateien auf den Server für die öffentliche Freigabe hochladen kann. Andernfalls kann der Store die Dateien nicht abrufen. Sie müssen die Dateien bei Übermittlungen neuer Power BI-Visuals, bei Aktualisierungen vorhandener Power BI-Visuals und bei Korrekturen abgelehnter Visuals senden.

>[!NOTE]
>Das [Verkäuferdashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) wird eingestellt. Es wird durch [Partner Center](https://docs.microsoft.com/partner-center/) ersetzt. Verwenden Sie das Verkäuferdashboard nur noch, wenn Sie sich mitten im Prozess der Übermittlung eines Power BI-Visuals befinden. Wenn Sie ein neues Power BI-Visual an AppSource übermitteln, verwenden Sie das [Partner Center](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Übermittlungsprozess auf dem Verkäuferdashboard

Sie benötigen ein gültiges Office-Entwicklerkonto, um sich bei [Office Developer Center](https://dev.office.com/) anzumelden. Das Office-Entwicklerkonto muss ein Microsoft-Konto mit Live-ID sein, z. B. hotmail.com oder outlook.com.

1. Navigieren Sie zu [Developer Center](https://sellerdashboard.microsoft.com/Application/Summary).

2. Wählen Sie **Neue App hinzufügen** aus.

    ![App hinzufügen](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Wählen Sie **Benutzerdefiniertes visuelles Power BI-Element** und dann **Weiter** aus.

4. Wählen Sie das Symbol **+** unter **App-Paket**, und wählen Sie im Dialogfeld „Datei öffnen“ die XML-Datei mit dem App-Paket aus, die Sie vom Power BI-Team erhalten haben.

    ![App-Paket](media/office-store/powerbi-custom-visual-apppackage.png)

5. Sie erhalten die Bestätigung, dass es sich um ein gültiges Power BI-App-Paket handelt.

    ![Manifest genehmigt](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Machen Sie die Angaben für **Allgemeine Informationen**.

   * *Titel der Übermittlung:* Der Name Ihrer Übermittlung in Developer Center.
   * *Version:* Die Versionsnummer wird automatisch aus dem Add-In-App-Paket übernommen.
   * *Veröffentlichungsdatum (UTC):* Wählen Sie das Datum aus, an dem die App im Store veröffentlicht werden soll. Bei Auswahl eines in der Zukunft liegenden Datums ist die App erst ab diesem Datum im Store verfügbar.
   * *Kategorie:* Als erste Kategorie wird automatisch „Datenvisualisierung und BI“ eingetragen. Auf diese Weise werden alle Power BI-Visuals gekennzeichnet. Um Benutzern die Suche nach Ihren Visuals zu erleichtern, können Sie bis zu zwei zusätzliche Kategorien angeben.
   * *Testhinweise:* Optionale Angabe, wenn Sie Anweisungen für Tester bei Microsoft bereitstellen möchten.
   * *In meiner App ist Kryptografie oder Verschlüsselung enthalten bzw. wird von dieser aufgerufen, unterstützt oder verwendet:* Lassen Sie diese Option deaktiviert.
   * *Dieses Add-In im Office-Add-In-Katalog auf iPad verfügbar machen:* Lassen Sie diese Option deaktiviert.
7. Laden Sie das Logo für Ihre Visualisierung hoch, indem Sie das Symbol **+** unter **App-Logo** auswählen. Wählen Sie dann im Dialogfeld „Datei öffnen“ die Symboldatei aus. Dies muss eine PNG-, JPG-, JPEG- oder GIF-Datei sein. Die Abmessung muss genau 300 px (Breite) × 300 px (Höhe) betragen, und die Datei darf nicht mehr als 512 KB groß sein.

    ![App-Logo](media/office-store/powerbi-custom-visual-app-logo.png)

8. Geben Sie die Details für **Supportdokumente** ein.

   * Link zum Supportdokument
   * Link zum Datenschutzdokument
   * Videolink
   * Lizenzbedingungen

       Sie müssen eine Datei mit den Lizenzbedingungen hochladen. Dabei kann es sich um Ihre eigenen Lizenzbedingungen oder die Standardlizenzbedingungen im Office Store für Power BI-Visuals handeln. Um die Standardlizenzbedingungen zu verwenden, fügen Sie die folgende URL in das Dialogfeld zum Hochladen der Datei mit Lizenzbedingungen im Verkäuferdashboard ein: [https://visuals.azureedge.net/app-store/Power BI – Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Wählen Sie **Weiter** aus, um zur Seite **Details** zu gelangen.

10. Wählen Sie **Sprache** aus, und wählen Sie eine Sprache aus der Liste.

    ![Sprache](media/office-store/powerbi-custom-visual-language.png)

11. Geben Sie die Details in „Beschreibung“ ein.

    * *App-Name (in dieser Sprache):* Geben Sie den Titel der App ein, der in der digitalen Ladenzeile angezeigt werden soll.
    * *Kurzbeschreibung:* Geben Sie die Kurzbeschreibung der App mit bis zu 100 Zeichen ein, die in der digitalen Ladenzeile angezeigt werden soll. Diese Beschreibung wird auf den Seiten erster Ebene gemeinsam mit dem Logo angezeigt. Sie können die Beschreibung aus dem PBIVIZ-Paket verwenden.
    * *Ausführliche Beschreibung:* Geben Sie eine ausführlichere Beschreibung der App ein. Diese wird für Kunden auf der Seite „App-Details“ angezeigt. Wenn Sie Ihr visuelles Element als Open Source-Element bereitstellen und so der Community die Möglichkeit geben möchten, Ihr Element zu verbessern, geben Sie hier den Link zu dem öffentlichen Repository (beispielsweise GitHub) an.

12. Laden Sie mindestens einen Screenshot hoch. Dabei kann es sich um eine PNG-, JPG-, JPEG- oder GIF-Datei handeln. Die Abmessung muss genau 1366 px (Breite) × 768 px (Höhe) betragen. Die Datei darf nicht mehr als 1024 KB groß sein. *Um den Nutzen der Screenshots zu erhöhen, fügen Sie Textblasen hinzu, die den Wertbeitrag wichtiger Features, die in den einzelnen Screenshots gezeigt werden, erläutern.*

12. Wenn Sie weitere Sprachen hinzufügen möchten, wählen Sie **Sprache hinzufügen** aus, und wiederholen Sie die Schritte 10 und 11. Durch das Hinzufügen weiterer Sprachen erhöhen Sie die Wahrscheinlichkeit, dass Benutzer die Details der benutzerdefinierten Visualisierung in der eigenen Sprache anzeigen können. Für Sprachen, die nicht aufgeführt werden, wird standardmäßig die erste ausgewählte Sprache verwendet.

13. Nachdem Sie das Hinzufügen von Sprachen abgeschlossen haben, wählen Sie **Weiter** aus, um zur Seite **Zugriff blockieren** zu gelangen.

14. Wenn Sie die Verwendung oder den Kauf Ihrer App durch Kunden in bestimmten Ländern oder Regionen verhindern möchten, aktivieren Sie das Kontrollkästchen, und treffen Sie eine Auswahl aus der Liste.

15. Wählen Sie **Weiter** aus, um zur Seite **Preise** zu gelangen.

16. Derzeit werden nur *kostenlose* Visuals unterstützt, und zusätzliche Käufe im Visual (In-App-Käufe) sind unzulässig. Wählen Sie **Diese App ist kostenlos** aus.

    > [!NOTE]
    > Wenn Sie eine andere als die kostenlose Option auswählen oder per In-App-Kauf zu erwerbende Inhalte im übermittelten Visual enthalten sind, wird die Übermittlung zurückgewiesen.

17. Sie können auf **Als Entwurf speichern** klicken und das benutzerdefinierte Visual später übermitteln oder es an den Office Store übermitteln, indem Sie auf **Zur Genehmigung übermitteln** klicken.

## <a name="seller-dashboard-certification-submission-process"></a>Übermittlungsprozess für die Zertifizierung auf dem Verkäuferdashboard

Befolgen Sie die Anweisungen in diesem Abschnitt, um ein Power BI-Visual im Verkäuferdashboard zur Zertifizierung zu übermitteln. Verwenden Sie diese Methode, wenn Sie zuvor bereits ein Power BI-Visual über das Verkäuferdashboard an AppSource übermittelt haben.

1. Senden Sie eine E-Mail an das Supportteam für Power BI-Visuals (pbicvsupport@microsoft.com). Fügen Sie der E-Mail die folgende Informationen hinzu:
    * Titel: Zertifizierungsanforderung für Visual
    * Link zum GitHub-Repository, in dem der vom Menschen lesbare Quellcode gehostet wird
    * [Befolgen der Anforderungen](power-bi-custom-visuals-certified.md#certification-requirements)
    * Übergeben des Codereviews

2. Das Microsoft-Team für Power BI-Visuals benachrichtigt Sie, wenn Ihr Power BI-Visual zertifiziert und der [Liste der zertifizierten Power BI-Visuals](power-bi-custom-visuals-certified.md#certified-power-bi-visuals) hinzugefügt wurde oder wenn es mit einem Bericht zu den zu behebenden Problemen abgelehnt wurde. Es ist Aufgabe des Entwicklers, eine offene Kommunikation mit Microsoft zu pflegen und seine zertifizierten Visuals bei Bedarf zu aktualisieren.

## <a name="tracking-submission-status-and-usage"></a>Nachverfolgen des Übermittlungsstatus und der Verwendung

Sie können sich mit den [Überprüfungsrichtlinien](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals) vertraut machen.

Nach der Übermittlung können Sie im [App-Dashboard](https://sellerdashboard.microsoft.com/Application/Summary/) den Übermittlungsstatus anzeigen.

## <a name="certify-your-visual"></a>Zertifizieren Ihrer Visualisierung

Sobald Ihr Visual erstellt wurde, können Sie es [zertifizieren](../developer/power-bi-custom-visuals-certified.md) lassen, wenn Sie möchten.

## <a name="next-steps"></a>Nächste Schritte

[Entwickeln eines benutzerdefinierten Visuals für Power BI](visuals/custom-visual-develop-tutorial.md)  
[Visualisierungen in Power BI](../visuals/power-bi-report-visualizations.md)  
[Benutzerdefinierte Visualisierungen in Power BI](../developer/power-bi-custom-visuals.md)  
[So lassen Sie sich ein Power BI-Visual zertifizieren](../developer/power-bi-custom-visuals-certified.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
