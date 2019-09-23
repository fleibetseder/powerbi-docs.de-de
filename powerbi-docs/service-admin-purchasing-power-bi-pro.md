---
title: Erwerben und Zuweisen von Power BI Pro-Lizenzen
description: Erfahren Sie, wie Sie Power BI Pro-Lizenzen erwerben und zuweisen, damit Ihre Benutzer auf alle Inhalte und Funktionen im Power BI-Dienst zugreifen können.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 9e7cd025388a5ae21b73fe05fca0e1c8433b562d
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074882"
---
# <a name="purchase-and-assign-power-bi-pro-licenses"></a>Erwerben und Zuweisen von Power BI Pro-Lizenzen

Power BI Pro ist eine Einzellizenz, die Zugriff auf alle Inhalte und Funktionen im Power BI-Dienst ermöglicht, z.B. zur Freigabe von Inhalten und zur Zusammenarbeit mit anderen Benutzern mit Pro-Lizenz. Nur Pro-Benutzer können Inhalte in App-Arbeitsbereichen veröffentlichen, Dashboards freigeben sowie Dashboards und Berichte abonnieren. Weitere Informationen finden Sie unter [Power BI features by license type (Power BI-Features nach Lizenztyp)](service-features-license-type.md).

In diesem Artikel wird zunächst erläutert, wie Sie Power BI Pro-Lizenzen in Office 365 erwerben. Anschließend werden die zwei Optionen erklärt, die Ihnen zum Zuweisen dieser Lizenzen zu einzelnen Benutzern zur Verfügung stehen: Office 365 und Azure. (Entscheiden Sie sich für eine dieser Optionen.)

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen Mitglied der Rolle [**Globaler Administrator** oder **Abrechnungsadministrator**](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) in Office 365 sein.

Sie müssen Besitzer des Azure-Abonnements sein, das Power BI für Suchvorgänge in Active Directory verwendet, um Lizenzen in Azure zuzuweisen.

## <a name="purchase-licenses-in-office-365"></a>Erwerben von Lizenzen in Office 365

Führen Sie diese Schritte aus, um Power BI Pro-Lizenzen zu erwerben:

1. Öffnen Sie das [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage).

2. Wählen Sie im linken Navigationsbereich **Abrechnung** > **Abonnements** aus.

    ![Navigationsbereich](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Klicken Sie in der oberen rechten Ecke der Seite **Abonnements** auf **Abonnement hinzufügen**.

    ![Abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Suchen Sie das gewünschte Abonnementangebot:

    Klicken Sie unter **Enterprise Suite** auf **Office 365 Enterprise E5**.

    ![Office-E5-Abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Klicken Sie unter **Andere Pläne** auf **Power BI Pro**.

    ![Power BI-Abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Zeigen Sie auf die Auslassungspunkte ( **...** ) des gewünschten Abonnements, und wählen Sie **Jetzt kaufen** aus.

    ![Jetzt kaufen](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Klicken Sie je nach bevorzugter Zahlungsart auf **Monatlich bezahlen** oder auf **Für ein volles Jahr bezahlen**.

7. Geben Sie unter **Wie viele Benutzerlizenzen möchten Sie hinzufügen?** die gewünschte Anzahl von Lizenzen ein, und klicken Sie dann auf **Jetzt auschecken**, um die Transaktion abzuschließen.

8. Überprüfen Sie, ob das erworbene Abonnement jetzt auf der Seite **Abonnements** angezeigt wird.

   ![Erworbenes Abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Um nach dem ersten Kauf weitere Lizenzen hinzuzufügen, wählen Sie auf der Seite **Abonnements** nacheinander die Optionen **Power BI Pro** und **Lizenzen hinzufügen/entfernen** aus.

## <a name="assign-licenses-in-office-365"></a>Zuweisen von Lizenzen in Office 365

Führen Sie folgende Schritte aus, um einzelnen Benutzerkonten Power BI Pro-Lizenzen zuzuweisen:

1. Öffnen Sie das [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage).

2. Erweitern Sie im linken Navigationsbereich **Benutzer**, und wählen Sie dann **Aktive Benutzer** aus.

    ![Aktive Benutzer](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Wählen Sie einen Benutzer aus, und klicken Sie dann unter **Produktlizenzen** auf **Bearbeiten**.

    ![Bearbeiten von Produktlizenzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. Legen Sie in **Power BI Pro** die Einstellung auf **Ein** fest, und klicken Sie dann auf **Speichern**.

    ![Aktivierte Produktlizenzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Überprüfen Sie unter **Status** für das ausgewählte Konto, ob die Power BI Pro-Lizenz erfolgreich zugewiesen wurde.

    ![Überprüfen des Lizenzstatus](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

## <a name="assign-licenses-in-azure"></a>Zuweisen von Lizenzen in Azure

Führen Sie folgende Schritte aus, um einzelnen Benutzerkonten Power BI Pro-Lizenzen zuzuweisen:

1. Öffnen Sie das [Azure-Portal](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Wählen Sie in der linken Navigationsleiste **Azure Active Directory** aus.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Wählen Sie unter **Azure Active Directory** die Option **Lizenzen** aus.

    ![Lizenzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Wählen Sie unter **Lizenzen** die Option **Alle Produkte** und dann **Power BI Pro** aus, um die Liste der lizenzierten Benutzer anzuzeigen.

    ![Lizenzen – alle Produkte](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Klicken Sie auf **Zuweisen**, um einem weiteren Benutzerkonto eine Power BI Pro-Lizenz hinzuzufügen.

    ![Zuweisen einer Lizenz](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Lizenzen zugewiesen haben, informieren Sie sich eingehend über Power BI Pro.

[Power BI licensing in your organization (Power BI-Lizenzierung in Ihrem Unternehmen)](service-admin-licensing-organization.md)

[Suchen nach angemeldeten Power BI-Benutzern](service-admin-access-usage.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
