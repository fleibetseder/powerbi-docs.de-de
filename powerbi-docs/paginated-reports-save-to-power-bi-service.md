---
title: Veröffentlichen eines paginierten Berichts im Power BI-Dienst
description: In diesem Tutorial lernen Sie, einen paginierten Bericht durch Hochgeladen von Ihrem lokalen Computer im Power BI-Dienst zu veröffentlichen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: a7f0e6f08f25d47cd50789a3c8f296ae20c4cab0
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831197"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Veröffentlichen eines paginierten Berichts im Power BI-Dienst

In diesem Artikel erfahren Sie, wie Sie einen paginierten Bericht durch Hochgeladen von Ihrem lokalen Computer im Power BI-Dienst veröffentlichen. Sie können paginierte Berichte in Ihren Arbeitsbereich oder einen anderen Arbeitsbereich hochladen, sofern sich der Arbeitsbereich in einer Premium-Kapazität befindet. Suchen Sie nach dem Diamantsymbol ![Diamantsymbol in Power BI Premium-Kapazität](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) neben dem Namen des Arbeitsbereichs. 

Wenn Sie über eine lokale Berichtsdatenquelle verfügen, müssen Sie nach dem Hochladen des Berichts [ein Gateway erstellen](#create-a-gateway).

## <a name="add-a-workspace-to-a-premium-capacity"></a>Hinzufügen eines Arbeitsbereichs zu einer Premium-Kapazität

Wenn im Arbeitsbereich das Diamantsymbol ![Diamantsymbol in Power BI Premium-Kapazität](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) neben dem Namen nicht angezeigt wird, müssen Sie den Arbeitsbereich einer Premium-Kapazität hinzufügen. 

1. Wählen Sie **Arbeitsbereiche**, die Auslassungspunkte ( **...** ) neben dem Arbeitsbereichsnamen und dann **Arbeitsbereich bearbeiten** aus.

    ![Auswählen von „Arbeitsbereich bearbeiten“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Erweitern Sie im Dialogfeld **Arbeitsbereich bearbeiten** **Erweitert**, und ziehen Sie **Dedizierte Kapazität** dann auf **Ein**.

    ![Auswählen von „Dedizierte Kapazität“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Möglicherweise können Sie diese Einstellung nicht ändern. Wenn das der Fall ist, wenden Sie sich an Ihren Power BI Premium-Kapazitätsadministrator, damit er Ihnen die Berechtigung erteilt, Ihren Arbeitsbereich einer Premium-Kapazität hinzuzufügen.


## <a name="upload-a-paginated-report"></a>Hochladen eines paginierten Berichts

1. Erstellen Sie Ihren paginierten Bericht im Berichts-Generator, und speichern Sie ihn auf Ihrem lokalen Computer.

1. Öffnen Sie den Power BI-Dienst in einem Browser, und navigieren Sie zu dem Premium-Arbeitsbereich, in dem Sie den Bericht veröffentlichen möchten. Achten Sie auf das Diamantsymbol ![Diamantsymbol in Power BI Premium-Kapazität](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) neben dem Namen des Arbeitsbereichs. 

1. Wählen Sie **Daten abrufen** aus.

    ![„Daten abrufen“ in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Wählen Sie im Feld **Dateien** die Option **Abrufen**aus.

    ![Abrufen von Dateien in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Wählen Sie **Lokale Datei** aus, navigieren Sie zum paginierten Bericht, und wählen Sie **Öffnen** aus.

    ![Auswählen von „Lokale Datei“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Wählen Sie **Weiter** > **Anmeldeinformationen bearbeiten** aus.

    ![Auswählen von „Anmeldeinformationen bearbeiten“](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Konfigurieren Sie Ihre Anmeldeinformationen, und wählen Sie **Anmelden** aus.

    ![Anmeldeinformationen bearbeiten](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Ihr Bericht wird in der Liste der Berichte angezeigt.

    ![Paginierter Bericht in der Berichtsliste](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Wählen sie den Bericht aus, um ihn im Power BI-Dienst zu öffnen. Wenn er über Parameter verfügt, müssen Sie diese auswählen, bevor der Bericht angezeigt werden kann.
 
    ![Auswählen von Parametern](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Erstellen eines Gateways

Wie bei allen Power BI-Berichten müssen Sie im Falle einer lokalen Berichtsdatenquelle ein Gateway erstellen oder eine Verbindung mit diesem herstellen, um auf Daten zuzugreifen.

1. Wählen Sie neben dem Berichtsnamen **Verwalten** aus.

   ![Verwalten des paginierten Berichts](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Im Power BI-Artikel [Was ist ein lokales Datengateway](service-gateway-onprem.md) finden Sie weitere Informationen und Anleitungen.

### <a name="gateway-limitations"></a>Gatewayeinschränkungen

Derzeit unterstützen Gateways keine mehrwertigen Parameter.


## <a name="next-steps"></a>Nächste Schritte

- [Anzeigen eines paginierten Berichts im Power BI-Dienst](consumer/paginated-reports-view-power-bi-service.md)
- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)

