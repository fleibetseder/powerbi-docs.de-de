---
title: Herstellen einer Verbindung mit Planview Enterprise mithilfe von Power BI
description: Planview Enterprise für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 64b8b0cce79e2c859ea4d926e1f0d3dfc0c1b83b
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185850"
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Herstellen einer Verbindung mit Planview Enterprise mithilfe von Power BI
Mit dem Planview Enterprise-Inhaltspaket können Sie Ihre Ressourcen- und Arbeitsverwaltungsdaten auf ganz neue Weise direkt in Power BI visualisieren. Verwenden Sie Ihre Planview Enterprise-Anmeldeinformationen, um auf interaktive Weise Ihre Portfolio-Investitionsausgaben anzuzeigen und zu sehen, welche Ihrer Projekte sich oberhalb und welche unterhalb des Budgetrahmens befinden und wie gut sich diese im Einklang mit den strategischen Prioritäten des Unternehmens befinden. Sie können das Standarddashboard und die Berichte auch erweitern, um diejenigen Einblicke zu erhalten, die für Sie am wichtigsten sind.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie eine Verbindung mit dem [Planview Enterprise-Inhaltspaket](https://app.powerbi.com/getdata/services/planview-enterprise) für Power BI her.

>[!NOTE]
>Damit Sie Ihre Planview Enterprise-Daten in Power BI importieren können, müssen Sie ein Planview Enterprise-Benutzer sein, für dessen Rolle das Feature zum Anzeigen des Berichtsportals aktiviert ist. Sehen Sie sich auch die zusätzlichen Anforderungen weiter unten an.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
    ![](media/service-connect-to-planview/get.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
    ![](media/service-connect-to-planview/services.png)
3. Wählen Sie auf der Power BI-Seite **Planview Enterprise** und dann **Abrufen** aus:  
    ![](media/service-connect-to-planview/planview.png)
4. Geben Sie im Textfeld „Planview Enterprise-URL“ die URL für den Planview Enterprise-Server ein, den Sie verwenden möchten. Geben Sie im Textfeld „Planview Enterprise-Datenbank“ den Namen der Planview Enterprise-Datenbank ein, und klicken Sie dann auf „Weiter“.  
    ![](media/service-connect-to-planview/params.png)
5. Wählen Sie in der Liste „Authentifizierungsmethode“ die Option **Standard** aus, wenn diese nicht bereits ausgewählt ist. Geben Sie den **Benutzernamen** und das **Kennwort** für Ihr Konto ein, und wählen Sie **Anmelden**aus.  
   ![](media/service-connect-to-planview/creds.png)
6. Wählen Sie im linken Bereich in der Liste der Dashboards „Planview Enterprise“ aus.  
     Power BI importiert Planview Enterprise-Daten in das Dashboard. Beachten Sie, dass das Laden der Daten einige Zeit dauern kann.  
    ![](media/service-connect-to-planview/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Damit Sie Ihre Planview Enterprise-Daten in Power BI importieren können, müssen Sie ein Planview Enterprise-Benutzer sein, für dessen Rolle das Feature zum Anzeigen des Berichtsportals aktiviert ist. Sehen Sie sich auch die zusätzlichen Anforderungen weiter unten an.

Dieses Verfahren setzt voraus, dass Sie sich bereits auf der Startseite von Microsoft Power BI mit einem Power BI-Konto angemeldet haben. Wenn Sie über kein Power BI-Konto verfügen, wechseln Sie zu [powerbi.com](https://powerbi.microsoft.com/get-started/), und klicken Sie unter **Power BI – Zusammenarbeit und Freigabe in der Cloud** auf **Kostenlos testen**. Klicken Sie anschließend auf **Daten abrufen**.

## <a name="next-steps"></a>Nächste Schritte:

[Was ist Power BI?](power-bi-overview.md)

[Abrufen von Daten in Power BI](service-get-data.md)