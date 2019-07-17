---
title: 'Verwenden von Datasets in mehreren Arbeitsbereichen (Vorschau): Power BI'
description: Erfahren Sie, wie Sie ein Dataset mit Benutzern in der gesamten Organisation teilen können. Dann können diese in ihren eigenen Arbeitsbereichen Berichte erstellen, die auf Ihrem Dataset basieren.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 17a8e1c9e0d46a56d6b6ff3e46c0fda6da8ffe12
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567844"
---
# <a name="use-datasets-across-workspaces-preview"></a>Verwenden von Datasets in mehreren Arbeitsbereichen (Vorschau)

Business Intelligence ist eine gemeinschaftliche Aktivität. Es ist wichtig, standardisierte Datasets einzurichten, die als „eindeutig wahre Quelle“ fungieren können. Dann sind das Entdecken und Wiederverwenden solcher standardisierten Datasets ist von entscheidender Bedeutung. Wenn Experten für Datenmodellierung in Ihrer Organisation optimierte Datasets erstellen und teilen, können Berichtersteller von diesen Datasets ausgehen, um präzise Berichte zu erstellen. Dann verfügt Ihre Organisation über konsistente Daten für die Entscheidungsfindung und ist auf dem Weg zu einer gesunden Datenkultur.

![Freigegebenes Dataset auswählen](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI können Datasetersteller Datasets *zertifizieren* oder *höher stufen*, damit sie von anderen entdeckt werden können. Auf diese Weise können Berichtsautoren erkennen, welche Datasets hohe Qualität aufweisen und offiziell sind, und können diese Datasets für das Erstellen in Power BI verwenden. Datasetbesitzer können die Kontrolle über die zum Zugriff auf ihre Daten berechtigten Personen behalten, indem Sie die [Erstellungsberechtigung](service-datasets-build-permissions.md#build-permissions-for-shared-datasets) verwenden. Mandantenadministratoren verfügen über eine neue Mandanteneinstellung zum [Steuern der Arbeitsbereiche übergreifenden Verwendung von Datasets](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Freigeben von Datasets und die neue Arbeitsbereichsoberfläche

Das Erstellen von Berichten auf der Grundlage von Datasets in verschiedenen Arbeitsbereichen und das Kopieren von Berichten in verschiedene Arbeitsbereiche sind eng mit der [neuen Arbeitsbereichsoberfläche](service-create-the-new-workspaces.md) verknüpft:

- Wenn Sie im Dienst den Datasetkatalog aus einer neuen Arbeitsbereichsoberfläche öffnen, zeigt der Datasetkatalog Datsets an, die sich in Ihren Arbeitsbereichen „Mein Arbeitsbereich“ und in anderen Arbeitsbereichen mit der neuen Arbeitsbereichsoberfläche befinden. 
- Wenn Sie den Datasetkatalog aus einem klassischen Arbeitsbereich öffnen, sehen Sie nur die Datasets aus dem betreffenden Arbeitsbereich, keine in anderen Arbeitsbereichen.
- Auf dem Desktop können Sie Live Connect-Berichte in verschiedenen Arbeitsbereichen veröffentlichen, sofern ihre Datasets sich in Arbeitsbereichen mit der neuen Benutzeroberfläche befinden.
- Beim übergreifenden Kopieren von Berichten über Arbeitsbereiche hinweg muss es sich bei dem Zielarbeitsbereich um einen Arbeitsbereich mit der neuen Benutzeroberfläche handeln.

## <a name="build-permission-for-datasets"></a>Erstellungsberechtigung für Datasets

Mithilfe des Typs „Erstellungsberechtigung“ können Sie anderen in Ihrer Organisation das Erstellen neuer Inhalte, wie etwa Berichte, Dashboards und angeheftete Kacheln aus Q&A, auf der Grundlage eines vorhandenen Datasets erlauben. Sie können darüber hinaus außerhalb von Power BI neue Inhalte auf dem Dataset aufbauen, beispielsweise Excel-Datenblätter mithilfe von „In Excel analysieren“, von XMLA und durch Exportieren. Weitere Informationen zur [Erstellungsberechtigung](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Datasets entdecken (Vorschau)

Beim Erstellen eines Berichts auf der Grundlage eines vorhandenen Datasets besteht der erste Schritt im Herstellen der Verbindung mit dem Dataset, entweder im Power BI-Dienst oder in Power BI Desktop. Weitere Informationen zum [Entdecken von Datasets aus verschiedenen Arbeitsbereichen (Vorschau)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Kopieren eines Berichts

Wenn Sie in einem Arbeitsbereich oder einer App einen Bericht gefunden haben, der Ihnen gefällt, können Sie eine Kopie davon erstellen und ihn anschließend nach Ihrem Bedarf anpassen. Sie brauchen sich nicht mit der Erstellung des Datenmodells abzugeben. Das wurde bereits für Sie erstellt. Und es ist viel einfacher, einen vorhandenen Bericht zu ändern, als einen von Grund auf neuen zu erstellen. Weitere Informationen zum [Kopieren von Berichten](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Bewerbung und Zertifizierung

Wenn Sie beim Erstellen ein Dataset schaffen, von dem andere profitieren können, können Sie es ihnen leichter machen, Ihr Dataset zu finden, indem Sie [Ihr Dataset bewerben](service-datasets-promote.md). Sie können darüber hinaus anfordern, dass die Experten in Ihrer Organisation [Ihr Dataset zertifizieren](service-datasets-certify.md).

## <a name="licensing"></a>Lizenzierung

Die spezifischen Features und Erfahrungen, die auf der Grundlage geteilter Datasets erstellt werden, werden gemäß ihren bestehenden Szenarien lizenziert.  Beispiel:

- Im Allgemeinen stehen die Ermittlung von freigegebenen Datasets und Herstellen von Verbindungen mit ihnen allen Benutzern zur Verfügung. Benutzer ohne Pro-Lizenz können jedoch nur Verbindungen mit Datasets herstellen, die sich in ihrem persönlichen Arbeitsbereich oder in Premium-Arbeitsbereichen befinden.
- Für das Bewerben und Zertifizieren von Datasets außerhalb von persönlichen Arbeitsbereichen ist eine Pro-Lizenz erforderlich, da nur Inhaber einer Pro-Lizenz Mitglied in einem App-Arbeitsbereich werden können.
- Auch für das Kopieren zwischen Arbeitsbereichen ist eine Pro-Lizenz erforderlich, da nur Inhaber einer Pro-Lizenz Mitglied in einem App-Arbeitsbereich werden können.
- Für das Kopieren von Berichten aus einer App ist ebenfalls eine Pro-Lizenz erforderlich, wie sie es bisher schon für organisationsbezogene Inhaltspakete erforderlich war.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

- Das Erstellen eines Berichts auf der Grundlage eines Datasets in einem anderen Arbeitsbereich setzt die neue Arbeitsbereichsoberfläche an beiden Enden voraus: Der Bericht muss sich in einer neuen Arbeitsbereichsoberfläche befinden, und das Dataset muss sich in einer neuen Arbeitsbereichsoberfläche befinden.
- In einem klassischen Arbeitsbereich zeigt die Oberfläche zur Datasetermittlung nur die Datasets in dem betreffenden Arbeitsbereich an.
- Sie können Berichte in App-Arbeitsbereichen erstellen, die auf Datasets in einem anderen Arbeitsbereich basieren. Jedoch können Sie keine App für einen Arbeitsbereich erstellen, der diese Datasets enthält.
- Kostenlose Desktop-Benutzer sehen nur Datasets aus „Mein Arbeitsbereich“ und aus Premium-basierten Arbeitsbereichen.
- Wenn Sie einer App einen Bericht hinzufügen möchten, der auf einem freigegebenen Dataset basiert, müssen Sie Mitglied des Dataset-Arbeitsbereichs sein. Dies ist ein bekanntes Problem.
- „Im Web veröffentlichen“ funktioniert nicht für Berichte, die auf einem freigegebenen Dataset basieren. Dies ist beabsichtigt.
- Wenn zwei Personen Mitglieder eines Arbeitsbereichs sind, der auf ein freigegebenes Dataset zugreift, ist es möglich, dass nur eine von ihnen das zugehörige Dataset im Arbeitsbereich sieht. Nur Personen, die mindestens Lesezugriff auf das Dataset besitzen, können das freigegebene Dataset sehen. 

## <a name="next-steps"></a>Nächste Schritte

- [Höher Stufen von Datasets](service-datasets-promote.md)
- [Zertifizieren von Datasets](service-datasets-certify.md)
- [Steuern der Verwendung von Datasets in mehreren Arbeitsbereichen](service-datasets-admin-across-workspaces.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
