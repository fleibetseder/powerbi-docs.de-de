---
title: Herstellen einer Verbindung mit Projectplace mithilfe von Power BI
description: Projectplace für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: cd478abbac94c6b8aaf5aaa087dbfa4840e05fd7
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184569"
---
# <a name="connect-to-projectplace-by-planview-with-power-bi"></a>Herstellen einer Verbindung mit Projectplace von Planview mithilfe von Power BI
Mit dem Projectplace by Planview-Inhaltspaket können Sie Ihre kooperativen Projektdaten auf ganz neue Weise direkt in Power BI visualisieren. Verwenden Sie Ihre Projectplace-Anmeldeinformationen, um auf interaktive Weise wichtige Projektstatistiken anzuzeigen, Ihre aktivsten und produktivsten Teammitglieder zu ermitteln und risikoreiche Karten und Aktivitäten über sämtliche Projekte in Ihrem Projectplace-Konto hinweg zu identifizieren. Sie können das Standarddashboard und die Berichte auch erweitern, um diejenigen Einblicke zu erhalten, die für Sie am wichtigsten sind.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Herstellen einer Verbindung mit dem Projectplace-Inhaltspaket in Power BI](https://app.powerbi.com/getdata/services/projectplace)

>[!NOTE]
>Damit Sie Ihre Projectplace-Daten in Power BI importieren können, müssen Sie ein Projectplace-Benutzer sein. Sehen Sie sich auch die zusätzlichen Anforderungen weiter unten an.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
    ![](media/service-connect-to-projectplace/get.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
    ![](media/service-connect-to-projectplace/services.png)
3. Wählen Sie auf der Power BI-Seite **Projectplace by Planview** und dann **Abrufen** aus:  
   
    ![](media/service-connect-to-projectplace/projectplace.png)
4. Geben Sie im Textfeld „OData-Feed-URL“ die URL für den zu verwendenden Projectplace-OData-Feed ein, wie in der folgenden Abbildung dargestellt:
   
    ![](media/service-connect-to-projectplace/params.png)
5. Wählen Sie in der Liste „Authentifizierungsmethode“ die Option **OAuth** aus, wenn diese nicht bereits ausgewählt ist. Klicken Sie auf **Anmelden**, und befolgen Sie die Anweisungen bei der Anmeldung.  
   
   ![](media/service-connect-to-projectplace/creds.png)
6. Wählen Sie im linken Bereich in der Liste der Dashboards **Projectplace** aus. Power BI importiert Projectplace-Daten in das Dashboard. Beachten Sie, dass das Laden der Daten einige Zeit dauern kann.  
   
    Das Dashboard enthält Kacheln, auf denen Daten aus Ihrer Projectplace-Datenbank angezeigt werden. Die folgende Abbildung zeigt ein Beispiel des standardmäßigen Projectplace-Dashboards in Power BI.
   
    ![](media/service-connect-to-projectplace/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Damit Sie Ihre Projectplace-Daten in Power BI importieren können, müssen Sie ein Projectplace-Benutzer sein. Dieses Verfahren setzt voraus, dass Sie sich bereits auf der Startseite von Microsoft Power BI mit einem Power BI-Konto angemeldet haben. Wenn Sie über kein Power BI-Konto verfügen, wechseln Sie zu [powerbi.com](https://powerbi.microsoft.com/get-started/), und klicken Sie unter **Power BI – Zusammenarbeit und Freigabe in der Cloud** auf **Kostenlos testen**. Klicken Sie anschließend auf **Daten abrufen**.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](power-bi-overview.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

