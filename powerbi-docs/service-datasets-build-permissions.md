---
title: Die Berechtigung „Erstellen“ für freigegebene Datasets (Vorschau)
description: Erfahren Sie, wie Sie die Kontrolle über die zum Zugriff auf ihre Daten berechtigten Personen behalten, indem Sie die Berechtigung „Erstellen“ verwenden.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 069ec5e0c767bcfcb0a4a41c2180ae78146800f2
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020897"
---
# <a name="build-permission-for-shared-datasets-preview"></a>Die Berechtigung „Erstellen“ für freigegebene Datasets (Vorschau)

Als Ersteller von *Datenmodellen* in Power BI Desktop können Sie sie als *Datasets* im Power BI-Dienst freigeben. Anschließend können Berichtersteller die von Ihnen freigegebenen Datasets auf einfache Weise finden und wiederverwenden. Erfahren Sie, wie Sie mithilfe der Berechtigung „Erstellen“ steuern, wer Zugriff auf die Daten hat.

Die Berechtigung „Erstellen“ ist nur für Datasets relevant. Wenn Sie Benutzern die Berechtigung „Erstellen“ erteilen, können sie neue Inhalte für ein Dataset erstellen, wie z. B. Berichte, Dashboards, angeheftete Kacheln aus dem Bereich „Fragen und Antworten“ und gewonnene Erkenntnisse. Sie können darüber hinaus außerhalb von Power BI neue Inhalte auf dem Dataset aufbauen, beispielsweise Excel-Datenblätter mithilfe von „In Excel analysieren“, XMLA und durch Exportieren zugrunde liegender Daten.

## <a name="ways-to-give-build-permission"></a>Möglichkeiten zum Erteilen der Berechtigung „Erstellen“

Es gibt verschiedene Möglichkeiten zum Erteilen der Berechtigung „Erstellen“:

- Mitglieder eines Arbeitsbereichs mit mindestens der Rolle „Mitwirkender“ haben automatisch die Berechtigung „Erstellen“ für Datasets in diesem Arbeitsbereich und die Berechtigung zum Kopieren eines Berichts.
 
- Mitglieder des Arbeitsbereichs, in dem sich das Dataset befindet, können die Berechtigung im Berechtigungscenter bestimmten Benutzern oder Sicherheitsgruppen zuweisen. Wenn Sie Mitglied des Arbeitsbereichs sind, klicken Sie auf Auslassungspunkte (…) neben einem Dataset und dann auf **Berechtigungen verwalten**.

    ![Auswählen der Auslassungspunkte](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

    Dadurch wird das Berechtigungscenter für das Dataset geöffnet, in dem Sie Berechtigungen festlegen und ändern können.

    ![Berechtigungscenter](media/service-datasets-build-permissions/power-bi-dataset-remove-permissions-no-callouts.png)

- Ein Administrator oder Mitglied des Arbeitsbereichs, in dem das Dataset gespeichert ist, kann während des Veröffentlichens einer App entscheiden, dass Benutzer mit Berechtigung für die App außerdem die Erstellungsberechtigung für die zugrundeliegenden Datasets erhalten. Weitere Informationen finden Sie unter [Freigeben eines Datasets](service-datasets-share.md).

- Angenommen, Sie haben die Berechtigungen „Erneut freigeben“ und „Erstellen“ für ein Dataset. Beim Freigeben eines Berichts oder eines Dashboards, der bzw. das auf Grundlage dieses Datasets erstellt wurde, können Sie angeben, dass die Empfänger außerdem die Berechtigung „Erstellen“ für das zugrundeliegende Dataset erhalten sollen.

    ![Berechtigung „Erstellen“](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Sie können einer Person die Berechtigung „Erstellen“ für ein Dataset entziehen. Wenn Sie dies tun, können die betroffenen Personen immer noch den auf dem freigegebenen Dataset erstellten Bericht anzeigen, sie können ihn aber nicht mehr ändern. Weitere Informationen finden Sie im nächsten Abschnitt.

## <a name="remove-build-permission-for-a-dataset"></a>Entziehen der Berechtigung „Erstellen“ für ein Dataset

Es ist möglich, dass Sie irgendwann Benutzern eines freigegebenen Datensatzes die Berechtigung „Erstellen“ entziehen müssen. 

1. Wechseln Sie in einem Arbeitsbereich zur Listenseite **Datasets**. 
1. Klicken Sie auf die Auslassungspunkte (...) neben dem Dataset und dann auf **Berechtigungen verwalten**.

    ![Berechtigungen verwalten](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Klicken Sie auf die Auslassungspunkte (...) neben einem Namen und dann auf **Remove build** (Berechtigung „Erstellen“ entziehen).

    ![Berechtigung „Erstellen“ entziehen](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    Anschließend können die betroffenen Benutzer immer noch den anhand des freigegebenen Datasets erstellten Bericht anzeigen, ihn aber nicht mehr ändern.

### <a name="remove-build-permission-for-a-dataset-in-an-app"></a>Berechtigung „Erstellen“ entziehen für ein Dataset in einer App

Angenommen, Sie haben eine App aus einem Arbeitsbereich an eine Gruppe von Benutzern verteilt. Später beschließen Sie, einigen Benutzern den Zugriff auf die App zu entziehen. Durch das Entziehen des Zugriffs auf die App werden die Berechtigungen „Erstellen“ und „Erneut freigeben“ nicht automatisch aufgehoben. Dies erfordert einen zusätzlichen Schritt. 

1. Klicken Sie auf einer Listenseite im Arbeitsbereich auf **App aktualisieren**. 

    ![App aktualisieren](media/service-datasets-build-permissions/power-bi-app-update.png)

1. Klicken Sie auf der Registerkarte **Berechtigungen** auf **X**, um die Person oder Gruppe zu löschen. 

    ![Auf das X klicken](media/service-datasets-build-permissions/power-bi-app-delete-user.png)
1. Klicken Sie auf **App aktualisieren**.

    Sie erhalten die Meldung, dass Sie zu **Berechtigungen verwalten** wechseln müssen, um die Berechtigung „Erstellen“ Benutzern mit vorhandenem Zugriff zu entziehen. 

    ![Meldung zu „Berechtigungen verwalten“](media/service-datasets-build-permissions/power-bi-dataset-app-remove-message.png)

1. Klicken Sie auf **Aktualisieren**.

1. Wechseln Sie im Arbeitsbereich zur Listenseite **Datasets**. 
1. Klicken Sie auf die Auslassungspunkte (...) neben dem Dataset und dann auf **Berechtigungen verwalten**.

    ![Berechtigungen verwalten](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Klicken Sie auf die Auslassungspunkte (...) neben einem Namen und dann auf **Remove build** (Berechtigung „Erstellen“ entziehen).

    ![Berechtigung „Erstellen“ entziehen](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    Anschließend können die betroffenen Benutzer immer noch den anhand des freigegebenen Datasets erstellten Bericht anzeigen, ihn aber nicht mehr ändern.

## <a name="more-granular-permissions"></a>Feiner abgestimmte Berechtigungen

In Power BI wurde die Berechtigung „Erstellen“ im Juni 2019 als Ergänzung der vorhandenen Berechtigungen „Lesen“ und „Erneut freigeben“ eingeführt. Alle Benutzer, die zu diesem Zeitpunkt über App-Berechtigungen, Freigabe oder Arbeitsbereichszugriff bereits über die Berechtigung „Lesen“ für Datasets verfügten, erhielten für die gleichen Datasets außerdem die Berechtigung „Erstellen“. Sie erhielten die Erstellungsberechtigung automatisch, da ihnen die Leseberechtigung bereits das Recht zum Erstellen neuer Inhalte auf der Grundlage des Datasets einräumte, durch Verwendung von „In Excel analysieren“ oder Exportieren.

Mit dieser feiner abgestimmten Erstellungsberechtigung können Sie jetzt wählen, wer nur die Inhalte im vorhandenen Bericht oder Dashboard anzeigen und wer Inhalte erstellen kann, die mit den zugrundeliegenden Datasets verbunden sind.

Wenn Ihr Dataset von einem Bericht außerhalb des Arbeitsbereichs des Datasets verwendet wird, können Sie das Dataset nicht löschen. Stattdessen wird eine Fehlermeldung angezeigt.

Sie können die Berechtigung „Erstellen“ entziehen. In diesem Fall können die Personen, deren Berechtigungen Sie widerrufen haben, den Bericht immer noch anzeigen, ihn aber nicht mehr bearbeiten oder dessen zugrunde liegenden Daten exportieren. Benutzer, die nur über Leseberechtigung verfügen, können zusammengefasste Daten weiterhin exportieren. 

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden von Datasets in mehreren Arbeitsbereichen (Vorschau)](service-datasets-across-workspaces.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
