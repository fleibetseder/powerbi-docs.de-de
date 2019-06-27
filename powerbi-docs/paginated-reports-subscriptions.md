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
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839546"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Abonnieren von paginierten Berichten für sich selbst und andere im Power BI-Dienst 

Sie können jetzt im Power BI-Dienst E-Mail-Abonnements für paginierte Berichte für sich selbst und andere einrichten. Im Allgemeinen ist dieser Vorgang identisch mit dem [Abonnieren von Berichten und Dashboards im Power BI-Dienst](service-report-subscribe.md). In diesem Artikel werden Unterschiede und Überlegungen aufgeführt. 

Durch das Einrichten von Abonnements können Sie entscheiden, ob Sie die E-Mails täglich, wöchentlich oder stündlich erhalten möchten. Wenn Sie täglich oder wöchentlich auswählen, können Sie die Zeit(en) bestimmen, wann das Abonnement ausgeführt werden soll. Insgesamt können Sie für jeden Bericht bis zu 24 verschiedene Abonnements pro Tag einrichten. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Überlegungen zu Abonnements von paginierten Berichten 

- Im Gegensatz zu Dashboards oder Power BI-Berichten enthält Ihr Abonnement eine Anlage mit der gesamten Berichtsausgabe.  Die folgenden Anlagetypen werden unterstützt: PDF, PowerPoint-Präsentation (.pptx), Excel-Arbeitsmappe (.xlsx), Word-Dokument (.docx), CSV-Datei und XML.

- Im E-Mail-Text wird kein Vorschaubild des Berichts angezeigt.  Es ist geplant, das Bild der ersten Seite des Berichts als optionales Element zur Verfügung zu stellen. 

- Die maximale Größe der Anlage eines Berichts beträgt 25 MB. 

- Sie können paginierte Berichte für andere Benutzer abonnieren, die eine Verbindung mit irgendwelchen derzeit unterstützten Datenquellen herstellt (einschließlich Azure Analysis Services oder Power BI-Datasets). Bedenken Sie, dass die Anlage des Berichts die Daten basierend auf Ihren Berechtigungen widerspiegelt (wie SQL Server Reporting Services heute). 

- Abonnements von Berichtseiten sind mit dem Namen des Berichts verknüpft.  

- E-Mail-Abonnements werden mit Standardparameterwerten des Berichts gesendet. 

- Die Option **After Data Refresh** (Nach der Datenaktualisierung) steht für die Häufigkeit mit paginierten Berichten nicht zur Verfügung. Sie erhalten immer die aktuellen Werte der zugrunde liegenden Datenquelle. 

## <a name="next-steps"></a>Nächste Schritte

[Subscribe yourself and others to reports and dashboards in the Power BI service (Abonnieren von Berichten und Dashboards im Power BI-Dienst für sich selbst und andere)](service-report-subscribe.md)

[Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
