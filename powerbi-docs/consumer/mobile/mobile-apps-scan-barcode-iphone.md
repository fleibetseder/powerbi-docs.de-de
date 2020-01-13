---
title: Scannen eines Barcodes aus der mobilen Power BI-App
description: Scannen Sie reale Barcodes, um direkt zu gefilterten BI-Informationen in der mobilen Power BI-App zu gelangen.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: painbar
ms.openlocfilehash: ee3cfec0c735ad52f9a036e75f61c1ab0400567b
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75217808"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>Scannen eines Barcodes aus der mobilen Power BI-App mit Ihrem Gerät
Scannen Sie reale Barcodes, um direkt zu gefilterten BI-Informationen in der mobilen Power BI-App zu gelangen.


Gilt für:

| ![iPhone](./media/mobile-apps-quickstart-view-dashboard-report/iphone-logo-30-px.png) | ![Android-](./media/mobile-apps-quickstart-view-dashboard-report/android-logo-30-px.png) | 
|:--- |:--- |
| iPhone | Android (Smartphone, Tablet) | 

Angenommen, ein Kollege hat [ein Barcodefeld in einem Bericht in Power BI Desktop markiert](../../desktop-mobile-barcodes.md) und den Bericht für Sie freigegeben. 

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Wenn Sie den Barcode eines Produkts mit dem Scanner in der Power BI-App auf Ihrem Gerät scannen, wird Ihnen der Bericht (oder eine Liste der Berichte) mit diesem Barcode angezeigt. Sie können den Bericht öffnen, der mit diesem Barcode herausgefiltert wurde.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Scannen eines Barcodes mit dem Power BI-Scanner
1. Tippen Sie auf der Navigationsleiste auf **Weitere Optionen** (...) und dann auf **Scanner**.

    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. Wenn die Kamera nicht aktiviert ist, müssen Sie der Power BI-App die Verwendung der Kamera gestatten. Eine einmalige Genehmigung ist erforderlich. 
4. Richten Sie den Scanner auf einen Barcode auf einem Produkt. Sie sehen eine Liste der Berichte, die diesem Barcode zugeordnet sind.
5. Tippen Sie auf den Namen des Berichts, der automatisch zu diesem Barcode herausgefiltert wurde, um ihn auf Ihrem Gerät zu öffnen.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Nach anderen Barcodes in einem Bericht filtern
Während ein Bericht angezeigt wird, der von einem Barcode auf Ihrem Gerät herausgefiltert wurde, sollten Sie denselben Bericht mit einem anderen Barcode herausfiltern.

* Wenn das Symbol „Barcode“ über einen Filter verfügt ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), ist der Filter aktiv, und der Bericht wird bereits von einem Barcode herausgefiltert. 
* Wenn das Symbol nicht über einen Filter verfügt ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), ist der Filter nicht aktiv, und der Bericht wird von keinem Barcode herausgefiltert. 

Tippen Sie in beiden Fällen auf das Symbol, um ein kleines Menü mit einem schwebenden Scanbereich zu öffnen.

* Fokussieren Sie den Scanner auf das neue Element, um den Filter des Berichts auf einen anderen Barcodewert zu ändern. 
* Wählen Sie **Clear barcode filter** (Barcodefilter löschen), um zurück zum ungefilterten Bericht zu gelangen.
* Wählen Sie **Filter by recent barcodes** (Filtern nach aktuellen Barcodes) aus, um den Berichtsfilter für eines Produkt-Barcodes zu ändern, den Sie während der aktuellen Sitzung gescannt haben.

## <a name="issues-with-scanning-a-barcode"></a>Probleme beim Scannen eines Barcodes
Nachstehend finden Sie einige Nachrichten, die beim Scannen eines Barcodes für ein Produkt angezeigt werden.

### <a name="couldnt-filter-report"></a>“Couldn’t filter report...” („Der Bericht...konnte nicht gefiltert werden.“)
Der Bericht, den Sie filtern möchten, basiert auf einem Datenmodell, in dem dieser Barcodewert nicht enthalten ist. Beispielsweise ist das Produkt „Mineralwasser“ nicht im Bericht enthalten.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Alle/mehrere der Visualisierungen im Bericht enthalten keinen Wert.
Der Barcodewert, den Sie gescannt haben, existiert in Ihrem Modell, jedoch enthalten alle/mehrere Visualisierungen in Ihrem Bericht diesen Wert nicht. So gibt der Filtervorgang einen leeren Zustand zurück. Versuchen Sie, in anderen Berichtsseiten zu suchen, oder bearbeiten Sie Ihre Berichte in Power BI Desktop, um diesen Wert hinzuzufügen. 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>„Offenbar verfügen Sie über keine Berichte, die nach Barcodes gefiltert werden können.“
Dies bedeutet, dass Sie keine Barcode-aktivierten Berichte besitzen. Der Barcodescanner kann nur Berichte filtern, die über eine Spalte verfügen, die als **Barcode** markiert ist.  

Stellen Sie sicher, eine Spalte von Ihnen oder dem Besitzer des Berichts als **Barcode** in Power BI Desktop markiert wurde. Erfahren Sie mehr über [das Markieren eines Barcodefelds in Power BI Desktop](../../desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>“Couldn’t filter report - Looks like this barcode doesn't exist in the report data.” („Der Bericht konnte nicht gefiltert werden. Dieser Barcode existiert womöglich nicht in den Berichtsdaten.“)
Der Bericht, den Sie filtern möchten, basiert auf einem Datenmodell, in dem dieser Barcodewert nicht enthalten ist. Beispielsweise ist das Produkt „Mineralwasser“ nicht im Bericht enthalten. Sie können ein anderes Produkt scannen, einen anderen Bericht auswählen (falls mehr als ein Bericht verfügbar ist) oder den ungefilterten Bericht anzeigen. 

## <a name="next-steps"></a>Nächste Schritte
* [Markieren eines Barcodefelds in Power BI Desktop](../../desktop-mobile-barcodes.md)
* [Dashboardkacheln in Power BI](../end-user-tiles.md)
* [Dashboards in Power BI](../end-user-dashboards.md)

