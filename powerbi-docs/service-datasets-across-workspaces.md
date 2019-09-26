---
title: Einführung in die Verwendung von Datasets in mehreren Arbeitsbereichen (Vorschau)
description: Erfahren Sie, wie Sie ein Dataset mit Benutzern in der gesamten Organisation teilen können. Dann können diese in ihren eigenen Arbeitsbereichen Berichte erstellen, die auf Ihrem Dataset basieren.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/16/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ace40fed472dc516cce5a761544cc5365566f3cd
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074126"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Einführung in die Verwendung von Datasets in mehreren Arbeitsbereichen (Vorschau)

Business Intelligence ist eine gemeinschaftliche Aktivität. Es ist wichtig, standardisierte Datasets einzurichten, die als „eindeutig wahre Quelle“ fungieren können. Dann sind das Entdecken und Wiederverwenden solcher standardisierten Datasets ist von entscheidender Bedeutung. Wenn Experten für Datenmodellierung in Ihrer Organisation optimierte Datasets erstellen und teilen, können Berichtersteller von diesen Datasets ausgehen, um präzise Berichte zu erstellen. Dann verfügt Ihre Organisation über konsistente Daten für die Entscheidungsfindung und ist auf dem Weg zu einer gesunden Datenkultur.

![Freigegebenes Dataset auswählen](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI können Ersteller von Datasets mithilfe der [Erstellungsberechtigung](service-datasets-build-permissions.md#build-permissions-for-shared-datasets) steuern, wer Zugriff auf ihre Daten hat. Datasetersteller können Datasets auch *zertifizieren* oder *höher stufen*, damit andere sie finden können. Auf diese Weise können Berichtsautoren erkennen, welche Datasets hohe Qualität aufweisen und offiziell sind, und können diese Datasets für das Erstellen in Power BI verwenden. Mandantenadministratoren verfügen über eine neue Mandanteneinstellung zum [Steuern der Arbeitsbereiche übergreifenden Verwendung von Datasets](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Freigeben von Datasets und die neue Arbeitsbereichsoberfläche

Das Erstellen von Berichten auf der Grundlage von Datasets in verschiedenen Arbeitsbereichen und das Kopieren von Berichten in verschiedene Arbeitsbereiche sind eng mit der [neuen Arbeitsbereichsoberfläche](service-create-the-new-workspaces.md) verknüpft:

- Wenn Sie im Dienst den Datasetkatalog aus einer neuen Arbeitsbereichsoberfläche öffnen, zeigt der Datasetkatalog Datsets an, die sich in Ihren Arbeitsbereichen „Mein Arbeitsbereich“ und in anderen Arbeitsbereichen mit der neuen Arbeitsbereichsoberfläche befinden. 
- Wenn Sie den Datasetkatalog aus einem klassischen Arbeitsbereich öffnen, sehen Sie nur die Datasets aus dem betreffenden Arbeitsbereich, keine in anderen Arbeitsbereichen.
- In Power BI Desktop können Sie Live Connect-Berichte in verschiedenen Arbeitsbereichen veröffentlichen, sofern sich ihre Datasets in Arbeitsbereichen mit der neuen Benutzeroberfläche befinden.
- Beim übergreifenden Kopieren von Berichten über Arbeitsbereiche hinweg muss es sich bei dem Zielarbeitsbereich um einen Arbeitsbereich mit der neuen Benutzeroberfläche handeln.

## <a name="discover-datasets-preview"></a>Datasets entdecken (Vorschau)

Wenn Sie einen Bericht auf der Grundlage eines vorhandenen Datasets erstellen, besteht der erste Schritt darin, eine Verbindung mit dem Dataset herzustellen, entweder über den Power BI-Dienst oder Power BI Desktop. Weitere Informationen zum [Entdecken von Datasets aus verschiedenen Arbeitsbereichen (Vorschau)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Kopieren eines Berichts

Wenn Sie in einem Arbeitsbereich oder einer App einen Bericht gefunden haben, der Ihnen gefällt, können Sie eine Kopie davon erstellen und ihn anschließend nach Ihrem Bedarf anpassen. Sie brauchen sich nicht mit der Erstellung des Datenmodells abzugeben. Das wurde bereits für Sie erstellt. Und es ist viel einfacher, einen vorhandenen Bericht zu ändern, als einen von Grund auf neuen zu erstellen. Weitere Informationen zum [Kopieren von Berichten](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Erstellungsberechtigung für Datasets

Wenn Sie ein Datasetersteller sind, können Sie mit dem Erstellungsberechtigungstyp festlegen, wer in Ihrer Organisation neuen Inhalt in Ihren Datasets erstellen kann. Personen mit Erstellungsberechtigung können darüber hinaus außerhalb von Power BI neue Inhalte auf dem Dataset aufbauen, z. B. Excel-Datenblätter mithilfe von „In Excel analysieren“, von XMLA und durch Exportieren. Weitere Informationen zur [Erstellungsberechtigung](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="promotion-and-certification"></a>Bewerbung und Zertifizierung

Wenn Sie beim Erstellen von Datasets ein Dataset schaffen, von dem andere profitieren können, können Sie es ihnen leichter machen, Ihr Dataset zu finden, indem Sie [Ihr Dataset höher stufen](service-datasets-promote.md). Sie können darüber hinaus anfordern, dass die Experten in Ihrer Organisation [Ihr Dataset zertifizieren](service-datasets-certify.md).

## <a name="licensing"></a>Lizenzierung

Die spezifischen Features und Erfahrungen, die auf der Grundlage geteilter Datasets erstellt werden, werden gemäß ihren bestehenden Szenarien lizenziert. Beispiel:

- Im Allgemeinen stehen die Ermittlung von freigegebenen Datasets und Herstellen von Verbindungen mit ihnen allen Benutzern zur Verfügung. Benutzer ohne Pro-Lizenz können jedoch nur Verbindungen mit Datasets herstellen, die sich in ihrem persönlichen Arbeitsbereich befinden.
- Benutzer ohne eine Pro-Lizenz können Berichte und Dashboards, die auf einem freigegebenen Dataset basieren, nur nutzen, wenn beide Arbeitsbereiche (der Arbeitsbereich, der die Inhalte und der, der das Dataset enthält) in einer Premium-Kapazität gehostet sind.
- In Power BI Desktop können Benutzer ohne Pro-Lizenz nur Datasets aus ihrem persönlichen Arbeitsbereich sehen.
- Zum Kopieren von Berichten zwischen Arbeitsbereichen ist eine Pro-Lizenz erforderlich.
- Für das Kopieren von Berichten aus einer App ist ebenfalls eine Pro-Lizenz erforderlich, wie sie es bisher schon für organisationsbezogene Inhaltspakete erforderlich war.
- Zum Höherstufen und Zertifizieren von Datasets ist eine Pro-Lizenz erforderlich.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

- Das Erstellen eines Berichts auf der Grundlage eines Datasets in einem anderen Arbeitsbereich setzt die neue Arbeitsbereichsoberfläche an beiden Enden voraus: Der Bericht muss sich in einer neuen Arbeitsbereichsoberfläche befinden, und das Dataset muss sich in einer neuen Arbeitsbereichsoberfläche befinden.
- Angenommen, Sie erstellen einen Bericht in Arbeitsbereich A, der auf einem Dataset in Arbeitsbereich B basiert. Wenn Sie eine App für Arbeitsbereich A erstellen, können Sie diesen Bericht nur in die App für Arbeitsbereich A einschließen, wenn Sie auch Mitglied von Arbeitsbereich B sind.
- In einem klassischen Arbeitsbereich zeigt die Oberfläche zur Datasetermittlung nur die Datasets in dem betreffenden Arbeitsbereich an.
- Wenn Sie einer App einen Bericht hinzufügen möchten, der auf einem freigegebenen Dataset basiert, müssen Sie Mitglied des Dataset-Arbeitsbereichs sein. Dies ist ein bekanntes Problem.
- Prinzipbedingt funktioniert „Im Web veröffentlichen“ nicht für Berichte, die auf einem freigegebenen Dataset basieren.
- Wenn zwei Personen Mitglieder eines Arbeitsbereichs sind, der auf ein freigegebenes Dataset zugreift, ist es möglich, dass nur eine von ihnen das zugehörige Dataset im Arbeitsbereich sieht. Nur Personen, die mindestens Lesezugriff auf das Dataset besitzen, können das freigegebene Dataset sehen. 

## <a name="next-steps"></a>Nächste Schritte

- [Höher Stufen von Datasets](service-datasets-promote.md)
- [Zertifizieren von Datasets](service-datasets-certify.md)
- [Steuern der Verwendung von Datasets in mehreren Arbeitsbereichen](service-datasets-admin-across-workspaces.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)
