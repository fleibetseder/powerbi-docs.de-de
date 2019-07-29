---
title: Abonnieren von paginierten Berichten im Power BI-Dienst
description: In diesem Artikel erhalten Sie wichtige Informationen zum Abonnieren von paginierten Berichten im Power BI-Dienst.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 07/15/2019
ms.openlocfilehash: 2d48892450bbf6ab09a4bc88cd2be9a58bbdc863
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307080"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Abonnieren von paginierten Berichten für sich selbst und andere im Power BI-Dienst 

Sie können jetzt im Power BI-Dienst E-Mail-Abonnements für paginierte Berichte für sich selbst und andere einrichten. Im Allgemeinen ist dieser Vorgang identisch mit dem [Abonnieren von Berichten und Dashboards im Power BI-Dienst](service-report-subscribe.md). In diesem Artikel werden Unterschiede und Überlegungen aufgeführt. 

Durch das Einrichten von Abonnements können Sie entscheiden, ob Sie die E-Mails täglich, wöchentlich oder stündlich erhalten möchten. Wenn Sie täglich oder wöchentlich auswählen, können Sie die Zeit(en) bestimmen, wann das Abonnement ausgeführt werden soll. Insgesamt können Sie für jeden Bericht bis zu 24 verschiedene Abonnements pro Tag einrichten. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Überlegungen zu Abonnements von paginierten Berichten 

- Im Gegensatz zu Dashboards oder Power BI-Berichten enthält Ihr Abonnement eine Anlage mit der gesamten Berichtsausgabe.  Die folgenden Anlagetypen werden unterstützt: PDF, PowerPoint-Präsentation (.pptx), Excel-Arbeitsmappe (.xlsx), Word-Dokument (.docx), CSV-Datei und XML.

- Sie können im E-Mail-Text ein Vorschaubild des Berichts anzeigen.  Dies ist optional und kann sich je nach gewähltem Anhangformat leicht von der ersten Seite Ihres angehängten Berichtsdokuments unterscheiden. 

- Die maximale Größe der Anlage eines Berichts beträgt 25 MB. 

- Sie können paginierte Berichte für andere Benutzer abonnieren, die eine Verbindung mit irgendwelchen derzeit unterstützten Datenquellen herstellt (einschließlich Azure Analysis Services oder Power BI-Datasets). Bedenken Sie, dass die Anlage des Berichts die Daten basierend auf Ihren Berechtigungen widerspiegelt (wie SQL Server Reporting Services heute). 

- E-Mail-Abonnements können entweder mit den aktuell ausgewählten oder den Standardparametern für Ihren Bericht gesendet werden.  Sie können für jedes Abonnement, das Sie für Ihren Bericht erstellen, unterschiedliche Parameterwerte festlegen. 

- Wenn der Autor Ihres Berichts ausdrucksbasierte Parameter festgelegt hat (z.B. der Standardwert ist immer das heutige Datum), verwendet das Abonnement diesen als Standardwert. Sie können andere Parameterwerte ändern und die Verwendung aktueller Werte wählen. Wenn Sie diesen Wert jedoch nicht explizit ändern, verwendet das Abonnement den ausdrucksbasierten Parameter.

- Die Option **After Data Refresh** (Nach der Datenaktualisierung) steht für die Häufigkeit mit paginierten Berichten nicht zur Verfügung. Sie erhalten immer die aktuellen Werte der zugrunde liegenden Datenquelle. 

## <a name="next-steps"></a>Nächste Schritte

[Subscribe yourself and others to reports and dashboards in the Power BI service (Abonnieren von Berichten und Dashboards im Power BI-Dienst für sich selbst und andere)](service-report-subscribe.md)

[Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
