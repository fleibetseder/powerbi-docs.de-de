---
title: Visuals in Power BI
description: Benutzerdefinierte Visualisierungen in Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: a8b1be9157fa34e9ed4c987628f0b67624b4c826
ms.sourcegitcommit: 549401b0e1fad15c3603fe7f14b9494141fbb100
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72307475"
---
# <a name="visuals-in-power-bi"></a>Visuals in Power BI

Beim Erstellen oder Bearbeiten eines Power BI-Berichts stehen Ihnen viele verschiedene Typen von Visuals zur Verfügung. Die Symbole für diese Visuals werden im Bereich **Visualisierungen** angezeigt. Diese Visuals sind vorkonfiguriert, wenn Sie [Power BI Desktop](https://powerbi.microsoft.com/desktop/) herunterladen oder den [Power BI-Dienst](https://app.powerbi.com) öffnen.

![Visualisierungen](media/power-bi-custom-visuals/power-bi-visualizations.png)

Allerdings sind Sie nicht auf diesen Satz Visuals beschränkt. Wenn Sie die Auslassungspunkte (...) am unteren Rand auswählen, wird eine andere Quelle von Berichtsvisuals verfügbar: *Power BI*.

Entwickler erstellen Power BI-Visuals mithilfe des Power BI Visuals SDK. Diese Visuals ermöglichen es Geschäftskunden, ihre Daten in der Weise anzuzeigen, die sich am besten für ihr Geschäft eignet. Berichtsautoren können die Dateien der benutzerdefinierten Visuals dann in ihre Berichte importieren und diese wie die anderen Power BI-Visuals verwenden. Power BI-Visuals sind wichtige Bestandteile und können in Power BI unter anderem gefiltert, hervorhoben, bearbeitet und freigegeben werden.

Power BI-Visuals werden auf drei verschiedene Arten bereitgestellt:

* Benutzerdefinierte Visualdateien
* Visuals für Organisationen
* Visuals im Marketplace

## <a name="custom-visual-files"></a>Benutzerdefinierte Visualdateien

Bei Power BI-Visuals handelt es sich um Pakete, die Code zum Rendern der Daten enthalten, die für diese bereitgestellt werden. Jeder Benutzer kann ein benutzerdefiniertes Visual erstellen und dieses in eine einzelne `.pbiviz`-Datei packen, die in einen Power BI-Bericht importiert werden kann.

> [!WARNING]
> Ein benutzerdefiniertes Visual dann unter Umständen Code mit Sicherheits- oder Datenschutzrisiken enthalten. Vergewissern Sie sich, dass Sie dem Autor und der Quelle des benutzerdefinierten Visuals vertrauen, bevor Sie es in Ihren Bericht importieren.

## <a name="organizational-visuals"></a>Visuals für Organisationen

Power BI-Administratoren genehmigen Power BI-Visuals in ihren Organisationen und stellen sie bereit, damit sie von Berichtsautoren komfortabel ermittelt, aktualisiert und verwendet werden können. Administratoren können diese Visuals komfortabel verwalten (beispielsweise die Version aktualisieren oder ein Visual aktivieren/deaktivieren).

 [Weitere Informationen zu Visuals für Organisationen](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Visuals im Marketplace

Communitymitglieder und Microsoft haben beide ihre Power BI-Visuals zum allgemeinen Nutzen beigetragen und sie im [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)-Marketplace veröffentlicht. Sie können diese Visuals herunterladen und sie Ihren Power BI-Berichten hinzufügen. Microsoft hat diese Power BI-Visuals auf Funktionalität und Qualität getestet und genehmigt.

Was ist [AppSource](developer/office-store.md)? Es ist der Ort, an dem Sie Apps, Add-Ins und Erweiterungen für Microsoft-Software finden. In AppSource finden Millionen von Benutzern Produkte, z.B. Office 365, Azure, Dynamics 365, Cortana und Power BI, mit denen sie effizienter, besser informiert und eleganter als zuvor arbeiten können.

### <a name="certified-visuals"></a>Zertifizierte Visuals

Bei zertifizierten Power BI-Visuals handelt es sich um Marketplace-Visuals, die zusätzlichen strengen Qualitätstests unterzogen wurden. Diese werden für zusätzliche Szenarios unterstützt, z.B. für [E-Mail-Abonnements](service-report-subscribe.md) und die Option [Nach PowerPoint exportieren](service-publish-to-powerpoint.md).
Die Liste der zertifizierten Power BI-Visuals sowie eine Anleitung zum Einreichen eigener Power BI-Visuals finden Sie unter [Zertifizierte Power BI-Visuals](power-bi-custom-visuals-certified.md).

Sind Sie Webentwickler und möchten eigene Visualisierungen erstellen und zu AppSource hinzufügen? Lesen Sie [Entwickeln eines benutzerdefinierten Visuals für Power BI](developer/visuals/custom-visual-develop-tutorial.md), und erfahren Sie, wie [benutzerdefinierte Visuals in AppSource veröffentlicht werden](developer/office-store.md).

### <a name="import-a-custom-visual-from-a-file"></a>Importieren eines benutzerdefinierten Visuals aus einer Datei

1. Wählen Sie am unteren Rand des Bereichs **Visualisierungen** die Auslassungspunkte aus.

    ![visualisierungen2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Wählen Sie in der Dropdownliste **Aus Datei importieren** aus.

    ![Aus Datei importieren](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. Klicken Sie im Menü **Datei öffnen** auf die `.pbiviz`-Datei, die Sie importieren möchten, und klicken Sie dann auf **Öffnen**. Am unteren Ende des Bereichs **Visualisierungen** wird das Symbol für das benutzerdefinierte Visual hinzugefügt, und dieses kann jetzt in Ihrem Bericht verwendet werden.

    ![benutzerdefiniertes Visual importiert](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importieren von Visuals für Organisationen

1. Wählen Sie am unteren Rand des Bereichs **Visualisierungen** die Auslassungspunkte aus.

    ![Visual für Organisationen 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. Wählen Sie in der Dropdownliste **Aus Marketplace importieren** aus.

    ![Visual für Organisationen 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Klicken Sie auf dem Menü der oberen Registerkarte auf **MEINE ORGANISATION**.

    ![Visual für Organisationen 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Scrollen Sie in der Liste, um das Visual zu suchen, das Sie importieren möchten.

    ![Visual für Organisationen 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Wählen Sie **Hinzufügen** aus, um das benutzerdefinierte Visual zu importieren. Am unteren Ende des Bereichs **Visualisierungen** wird sein Symbol hinzugefügt, und es kann jetzt in Ihrem Bericht verwendet werden.

    ![Visual für Organisationen 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-power-bi-visuals-from-microsoft-appsource"></a>Herunterladen oder Importieren von Power BI-Visuals aus Microsoft AppSource

Sie haben zwei Möglichkeiten zum Herunterladen und Importieren von Power BI-Visuals: in Power BI und über die [AppSource-Website](https://appsource.microsoft.com/).

### <a name="import-power-bi-visuals-from-within-power-bi"></a>Importieren von Power BI-Visuals in Power BI

1. Wählen Sie am unteren Rand des Bereichs **Visualisierungen** die Auslassungspunkte aus.

    ![Visualisierungen 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Wählen Sie in der Dropdownliste **Aus Marketplace importieren** aus.

    ![Visual für Organisationen 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Scrollen Sie in der Liste, um das Visual zu suchen, das Sie importieren möchten.

    ![Visual importieren](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Wenn Sie zu einem der Visuals weitere Informationen erhalten möchten, markieren Sie es, und wählen Sie es aus.

    ![Auswählen](media/power-bi-custom-visuals/power-bi-select.png)

5. Auf der Detailseite können Sie Screenshots, Videos, ausführliche Beschreibungen und weitere Elemente anzeigen.

    ![Synoptic](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Scrollen Sie nach unten, um Bewertungen anzuzeigen.

    ![Überprüfungen](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Wählen Sie **Hinzufügen** aus, um das benutzerdefinierte Visual zu importieren. Am unteren Ende des Bereichs **Visualisierungen** wird sein Symbol hinzugefügt, und es kann jetzt in Ihrem Bericht verwendet werden.

    ![Visual importiert](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-power-bi-visuals-from-microsoft-appsource"></a>Herunterladen und Importieren von Power BI-Visuals aus Microsoft AppSource

1. Wählen Sie in [Microsoft AppSource](https://appsource.microsoft.com) die Registerkarte für **Apps** aus.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Wechseln Sie zur Seite [App-Ergebnisse](https://appsource.microsoft.com/marketplace/apps), auf der Sie die beliebtesten Apps in den einzelnen Kategorien, einschließlich *Power BI-Apps*, anzeigen können. Wir suchen nach Power BI-Visuals. Wählen wir also in der linken Navigationsliste **Power BI-Visuals** aus, um die Ergebnisse stärker einzugrenzen.

    ![AppSource-Visuals](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. In AppSource wird für jedes benutzerdefinierte Visual eine Kachel angezeigt.  Jede Kachel enthält eine Momentaufnahme eines benutzerdefinierten Visuals mit einer kurzen Beschreibung und einem Downloadlink. Wählen Sie die Kachel aus, um weitere Details anzuzeigen.

    ![Benutzerdefiniertes Visual auswählen](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Auf der Detailseite können Sie Screenshots, Videos, ausführliche Beschreibungen und weitere Elemente anzeigen. Wählen Sie **Jetzt anfordern** aus, und stimmen Sie den Nutzungsbedingungen zu, um das benutzerdefinierte Visual herunterzuladen.

    ![Anfordern über AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Wählen Sie den Link aus, um das benutzerdefinierte Visual herunterzuladen.

    ![Herunterladen](media/power-bi-custom-visuals/powerbi-custom-download.png)

    Die Downloadseite enthält auch Anweisungen zum Importieren des benutzerdefinierten Visuals in Power BI Desktop und den Power BI-Dienst.

    Sie können auch einen Beispielbericht herunterladen, der das benutzerdefinierte Visual enthält und dessen Funktionen veranschaulicht.

    ![Beispiel ausprobieren](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Speichern Sie die `.pbiviz`-Datei, und öffnen Sie dann Power BI.

7. Importieren Sie die `.pbiviz`-Datei in Ihren Bericht. (Siehe obigen Abschnitt [Importieren eines benutzerdefinierten Visuals aus einer Datei](#import-a-custom-visual-from-a-file).)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

* Beim Importieren wird eine benutzerdefinierte Visualisierungen einem bestimmten Bericht hinzugefügt. Wenn Sie die Visualisierung in einem anderen Bericht verwenden möchten, müssen Sie sie in diesen Bericht ebenfalls importieren. Wenn ein Bericht mit einer benutzerdefinierten Visualisierung mit der Option **Speichern unter** gespeichert wird, wird eine Kopie der benutzerdefinierten Visualisierung mit dem neuen Bericht gespeichert.

* Wenn der Bereich **Visualisierungen** nicht angezeigt wird, bedeutet dies, dass Sie über keine Bearbeitungsberechtigungen für den Bericht verfügen.  Sie können Power BI-Visuals nur Berichten hinzufügen, die Sie bearbeiten können, und keinen Berichten, die lediglich für Sie freigegeben wurden.

## <a name="troubleshoot"></a>Problembehandlung

Informationen zur Problembehandlung finden Sie unter [Problembehandlung bei Power BI-Visuals in Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>HÄUFIG GESTELLTE FRAGEN

Weitere Informationen und Antworten auf Fragen finden Sie in den [häufig gestellten Fragen zu Power BI-Visuals in Power BI](power-bi-custom-visuals-faq.md#organizational-visuals).

## <a name="next-steps"></a>Nächste Schritte

* [Visualisierungen in Power BI-Berichten](visuals/power-bi-report-visualizations.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/).
