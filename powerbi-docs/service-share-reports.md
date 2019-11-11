---
title: Zwei Möglichkeiten zur Freigabe eines gefilterten Power BI-Berichts
description: Lernen Sie zwei Möglichkeiten kennen, einen Power BI-Bericht für Kollegen in Ihrer Organisation zu filtern und freizugeben.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 79f09b5018efcdae88d74ae26f099ff095fb161a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871442"
---
# <a name="two-ways-to-share-a-filtered-power-bi-report"></a>Zwei Möglichkeiten zur Freigabe eines gefilterten Power BI-Berichts
*Freigeben* ist eine gute Möglichkeit, einigen Personen Zugriff auf Ihre Dashboards und Berichte zu gewähren. Wie gehen Sie vor, wenn Sie eine gefilterte Version eines Berichts freigeben möchten? Dabei handelt es sich möglicherweise um einen Bericht, der nur Daten für einen bestimmten Ort, einen bestimmten Vertriebsmitarbeiter oder ein bestimmtes Jahr enthält. Versuchen Sie, einen Bericht zu filtern und freizugeben, oder erstellen Sie eine benutzerdefinierte URL. Der Bericht wird gefiltert, wenn Empfänger ihn erstmalig öffnen. Sie können den Filter entfernen, indem Sie die URL ändern. 

![Gefilterter Bericht](media/service-share-reports/power-bi-share-filter-pane-report.png)

Zudem bietet Power BI [andere Möglichkeiten zum gemeinsamen Bearbeiten und Verteilen Ihrer Berichte](service-how-to-collaborate-distribute-dashboards-reports.md). Zum Freigeben benötigen Sie und die Empfänger eine [Power BI Pro-Lizenz](service-features-license-type.md), oder es muss sich um Inhalte in einer [Premium-Kapazität](service-premium-what-is.md) handeln. 

## <a name="two-ways-to-filter-a-report"></a>Zwei Möglichkeiten zum Filtern eines Berichts

Für beide Filterverfahren verwenden wir die Beispielvorlagen-App „Marketing & Sales“. Möchten Sie es ausprobieren? Sie können die [Beispielvorlagen-App „Marketing & Sales“](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview) auch installieren.

### <a name="set-a-filter"></a>Festlegen eines Filters

Öffnen Sie einen Bericht in der [Bearbeitungsansicht](consumer/end-user-reading-view.md), und wenden Sie einen Filter an.

In diesem Beispiel filtern wir die Seite „YTD Category“ (Kategorie „Seit Jahresbeginn“) der Beispielvorlagen-App „Marketing & Sales“ so, dass Werte nur dort angezeigt werden, wo **Region** gleich **Central** (Mitte) ist. 
 
![Berichtsfilterbereich](media/service-share-reports/power-bi-share-report-filter.png)

Speichern Sie den Bericht.

### <a name="create-a-filter-in-the-url"></a>Erstellen eines Filters in der URL

Wenn Sie den Filter am Ende der Berichtsseiten-URL hinzufügen, ist das Verhalten etwas anders. Die gefilterte Seite sieht identisch aus. Power BI fügt den Filter jedoch dem gesamten Bericht hinzu und entfernt die anderen Werte aus dem Filterbereich.  

Fügen Sie am Ende der Berichtsseiten-URL Folgendes hinzu:
   
    ?filter=*tablename*/*fieldname* eq *value*
   
Das Feld muss den Typ „number“, „datetime“ oder „string" aufweisen. Die Werte *TableName* oder *FieldName* dürfen keine Leerzeichen enthalten.
   
In diesem Beispiel lautet der Name der Tabelle **Geo**, das Feld hat den Namen **Region**, und der Wert, nach dem gefiltert werden soll, lautet **Central**:
   
    ?filter=Geo/Region eq 'Central'

Durch den Browser werden Sonderzeichen hinzugefügt, die Schrägstriche, Leerzeichen und Apostrophe darstellen, sodass die URL schließlich etwa wie folgt lautet:
   
    app.powerbi.com/groups/xxxx/reports/xxxx/ReportSection4d00c3887644123e310e?filter=Geo~2FRegion%20eq%20'Central'

![Bericht mit URL-Filter](media/service-share-reports/power-bi-share-report-filter-url.png)

Speichern Sie den Bericht.

Weitere Informationen finden Sie im Artikel [Filtern eines Berichts mithilfe von Abfragezeichenfolgenparametern in der URL](service-url-filters.md).

## <a name="share-the-filtered-report"></a>Freigeben des gefilterten Berichts

1. Wenn Sie [den Bericht freigeben](service-share-dashboards.md), deaktivieren Sie das Kontrollkästchen **E-Mail-Benachrichtigungen an Empfänger senden**.

    ![Dialogfeld „Bericht freigeben“](media/service-share-reports/power-bi-share-report-dialog.png)

4. Senden Sie den Link mit dem zuvor erstellten Filter.

## <a name="next-steps"></a>Nächste Schritte
* [Freigeben Ihrer Arbeit in Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Freigeben eines Dashboards](service-share-dashboards.md)
* Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/).
* Feedback? Anregungen nehmen wir auf der [Power BI-Communitywebsite](https://community.powerbi.com/) entgegen.

