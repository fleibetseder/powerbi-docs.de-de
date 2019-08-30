---
title: Freigeben eines Datasets (Vorschau)
description: Als Datasetbesitzer können Sie Ihre Datasets erstellen und teilen, damit andere sie verwenden können. Erfahren Sie, wie Sie die Kontrolle über die zum Zugriff auf ihre Daten berechtigten Personen behalten, indem Sie die Erstellungsberechtigung verwenden.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/14/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c5b880132255fbdf37996273dc6c70029e548df6
ms.sourcegitcommit: 4a3afe761d2f4a5bd897fafb36b53961739e8466
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69654890"
---
# <a name="share-a-dataset-preview"></a>Freigeben eines Datasets (Vorschau)

Als Ersteller von *Datenmodellen* in Power BI Desktop können Sie sie als *Datasets* im Power BI-Dienst freigeben. Anschließend können Berichtersteller die von Ihnen freigegebenen Datasets auf einfache Weise finden und wiederverwenden. Erfahren Sie, wie Sie sie teilen, und wie Sie mithilfe der Erstellungsberechtigung steuern, wer Zugriff auf die Daten hat.

## <a name="steps-to-sharing-your-dataset"></a>Schritte zum Freigeben Ihres Datasets

1. Erstellen Sie zunächst eine PBIX-Datei mit einem Datenmodell in Power BI Desktop. Wenn Sie planen, dieses Dataset anderen Benutzern zum Erstellen von Berichten anzubieten, können Sie eventuell sogar auf das Entwerfen eines Berichts in der PBIX-Datei verzichten.

    Eine bewährte Methode besteht darin, die PBIX-Datei in einer Office 365-Gruppe zu speichern.

1. Veröffentlichen Sie die PBIX-Datei im Power BI-Dienst in einem [Arbeitsbereich mit neuer Benutzeroberfläche](service-create-the-new-workspaces.md).
    
    Damit können andere Mitglieder dieses Arbeitsbereichs bereits Berichte auf der Grundlage dieses Datasets in anderen Arbeitsbereichen erstellen.

1. Sie können aus diesem Arbeitsbereich auch eine [App veröffentlichen](service-create-distribute-apps.md). Geben Sie in diesem Fall auf der Seite **Berechtigungen** an, wer über Berechtigungen verfügt und was er bzw. sie damit tun kann.

    > [!NOTE]
    > Wenn Sie **Gesamte Organisation** auswählen, hat niemand in der Organisation Erstellungsberechtigungen. Dieses Problem ist bereits bekannt. Geben Sie vielmehr E-Mail-Adressen in **Bestimmte Benutzer oder Gruppen** an.  Wenn Sie Erstellungsberechtigungen für Ihre gesamte Organisation festlegen möchten, geben Sie einen E-Mail-Alias für die gesamte Organisation an.

    ![Festlegen von App-Berechtigungen](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. Wählen Sie **App veröffentlichen** oder **App aktualisieren** aus, wenn sie bereits veröffentlicht wurde.

## <a name="build-permissions-for-shared-datasets"></a>Erstellungsberechtigungen für freigegebene Datasets

Der Erstellen-Berechtigungstyp ist nur für Datasets relevant. Mit ihm können Benutzer neue Inhalte auf einem Dataset aufbauen, beispielsweise Berichte, Dashboards, angeheftete Kacheln aus Q&A und Insights-Ermittlung. Sie können darüber hinaus außerhalb von Power BI neue Inhalte auf dem Dataset aufbauen, beispielsweise Excel-Datenblätter mithilfe von „In Excel analysieren“, XMLA und durch Exportieren zugrunde liegender Daten.

Benutzer erhalten die Erstellungsberechtigung auf unterschiedliche Weise:

- Wenn Sie mindestens in der Rolle „Mitwirkender“ Mitglied eines Arbeitsbereichs sind, haben Sie automatisch die Berechtigung zum Erstellen eines Datasets und die Berechtigung zum Kopieren eines Berichts.
 
- Ein Mitglied des Arbeitsbereichs, in dem sich das Dataset befindet, kann die Berechtigung im Berechtigungscenter bestimmten Benutzern oder Sicherheitsgruppen zuweisen. Wählen Sie die Auslassungspunkte (…) neben einem Dataset > **Berechtigungen verwalten** aus.

    ![Auswählen der Auslassungspunkte](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    Dadurch wird das Berechtigungscenter für das Dataset geöffnet, in dem Sie Berechtigungen festlegen und ändern können.

    ![Berechtigungscenter](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- Ein Administrator oder Mitglied des Arbeitsbereichs, in dem das Dataset gespeichert ist, kann während des Veröffentlichens einer App entscheiden, dass Benutzer mit Berechtigung für die App außerdem die Erstellungsberechtigung für die zugrundeliegenden Datasets erhalten. Weitere Informationen finden Sie unter [Schritte zum Freigeben Ihres Datasets](#steps-to-sharing-your-dataset) in diesem Artikel.

- Angenommen, Sie besitzen die Berechtigungen „Erneut freigeben“ und „Erstellen“ für ein Dataset. Beim Freigeben eines Berichts oder eines Dashboards, das auf der Grundlage dieses Datasets erstellt wurde, können Sie angeben, dass die Empfänger außerdem die Erstellungsberechtigung für das zugrundeliegende Dataset erhalten sollen.

    ![Erstellungsberechtigungen](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Sie können die Erstellungsberechtigungen einer Person für ein Dataset entfernen. Wenn Sie dies tun, können die betroffenen Personen immer noch den auf dem freigegebenen Dataset erstellten Bericht anzeigen, sie können ihn aber nicht mehr ändern.

## <a name="more-granular-permissions"></a>Feiner abgestimmte Berechtigungen

Power BI hat die Erstellungsberechtigung im Juni 2019 als Ergänzung der vorhandenen Berechtigungen „Lesen“ und „Erneut freigeben“ eingeführt. Alle Benutzer, die zu diesem Zeitpunkt durch die App-Berechtigungen, Freigabe oder Arbeitsbereichszugriff bereits über die Leseberechtigung für Datasets verfügten, erhielten für die gleichen Datasets außerdem die Erstellungsberechtigung. Sie erhielten die Erstellungsberechtigung automatisch, da ihnen die Leseberechtigung bereits das Recht zum Erstellen neuer Inhalte auf der Grundlage des Datasets einräumte, durch Verwendung von „In Excel analysieren“ oder Exportieren.

Mit dieser feiner abgestimmten Erstellungsberechtigung können Sie jetzt wählen, wer nur die Inhalte im vorhandenen Bericht oder Dashboard anzeigen und wer Inhalte erstellen kann, die mit den zugrundeliegenden Datasets verbunden sind.

Wenn Ihr Dataset von einem Bericht außerhalb des Arbeitsbereichs des Datasets verwendet wird, können Sie das Dataset nicht löschen. Stattdessen wird eine Fehlermeldung angezeigt.

Sie können Buildberechtigungen entfernen. In diesem Fall können die Personen, deren Berechtigungen Sie widerrufen haben, den Bericht immer noch anzeigen, ihn aber nicht mehr bearbeiten oder dessen zugrunde liegenden Daten exportieren. Benutzer, die nur über Leseberechtigung verfügen, können zusammengefasste Daten weiterhin exportieren. 

## <a name="track-your-dataset-usage"></a>Nachverfolgen der Verwendung Ihres Datasets

Wenn Sie über ein freigegebenes Dataset in Ihrem Arbeitsbereich verfügen, müssen Sie möglicherweise wissen, welche Berichte in anderen Arbeitsbereichen auf ihm aufbauen.

1. Wählen Sie in der Listenansicht der Datasets **Verwandte Inhalte anzeigen** aus.

    ![„Verwandte Inhalte anzeigen“](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. Im Dialogfeld **Verwandte Inhalte** werden alle verwandten Elemente angezeigt. In dieser Liste sehen Sie die verwandten Elemente in diesem Arbeitsbereich und in **Anderen Arbeitsbereichen**.
 
    ![Verwandte Inhalte (Dialogfeld)](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden von Datasets in mehreren Arbeitsbereichen (Vorschau)](service-datasets-across-workspaces.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
