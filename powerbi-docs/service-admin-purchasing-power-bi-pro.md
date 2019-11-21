---
title: Erwerben und Zuweisen von Power BI Pro-Lizenzen
description: Erfahren Sie, wie Sie Power BI Pro-Benutzerlizenzen erwerben und zuweisen, damit Ihre Benutzer auf Inhalte zugreifen und mit Kollegen im Power BI-Dienst zusammenarbeiten können.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 72a158e2dca32d2199fcd48e2cc37bf4c90778ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873537"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Erwerben und Zuweisen von Power BI Pro-Benutzerlizenzen

Power BI Pro wird als Einzelbenutzerlizenz bereitgestellt, die es Benutzern ermöglicht, von anderen Benutzern im Power BI-Dienst veröffentlichte Berichte und Dashboards zu lesen und mit diesen zu interagieren. Außerdem ist es möglich, Inhalte freizugeben und mit anderen Power BI Pro-Benutzern zusammenzuarbeiten. Nur Benutzer mit einer Power BI Pro-Benutzerlizenz können Inhalte veröffentlichen oder für andere Benutzer freigeben und Inhalte nutzen, die von anderen Benutzern erstellt wurden – es sei denn, diese Inhalte werden in einer Power BI Premium-Kapazität bereitgestellt. Weitere Informationen finden Sie unter [Power BI features by license type (Power BI-Features nach Lizenztyp)](service-features-license-type.md).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Erwerben und Zuweisen von Power BI Pro-Benutzerlizenzen

In diesem Artikel wird erläutert, wie Sie Power BI Pro-Benutzerlizenzen im Microsoft 365 Admin Center erwerben können. Außerdem werden die zwei Optionen beschrieben, über die Administratoren die Lizenzen für einzelne Benutzer zuweisen können: im Microsoft 365 Admin Center und im Azure-Portal (wählen Sie eine Option).

### <a name="prerequisites"></a>Voraussetzungen

Um Lizenzen im Microsoft 365 Admin Center zu erwerben und zuzuweisen, müssen Sie Mitglied der Rolle **[Globaler Administrator oder Abrechnungsadministrator](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** in Microsoft 365 sein.

Für die Lizenzzuweisung im Azure-Portal müssen Sie ein Besitzer des Azure-Abonnements sein, das Power BI für Suchvorgänge in Active Directory verwendet.

### <a name="purchase-licenses-in-microsoft-365"></a>Erwerben von Lizenzen in Microsoft 365

Führen Sie diese Schritte aus, um Power BI Pro-Lizenzen im Microsoft 365 Admin Center zu erwerben:

1. Öffnen Sie das [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage).

2. Wählen Sie im Navigationsbereich **Abrechnung** > **Abonnements** aus.

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

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Zuweisen von Lizenzen im Microsoft 365 Admin Center

Führen Sie folgende Schritte aus, um einzelnen Benutzerkonten Power BI Pro-Lizenzen zuzuweisen:

1. Öffnen Sie das [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage).

2. Erweitern Sie im Navigationsbereich **Benutzer**, und wählen Sie dann **Aktive Benutzer** aus.

    ![Aktive Benutzer](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Wählen Sie einen Benutzer aus, und klicken Sie dann unter **Produktlizenzen** auf **Bearbeiten**.

    ![Bearbeiten von Produktlizenzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. Legen Sie in **Power BI Pro** die Einstellung auf **Ein** fest, und klicken Sie dann auf **Speichern**.

    ![Aktivierte Produktlizenzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Überprüfen Sie unter **Status** für das ausgewählte Konto, ob die Power BI Pro-Lizenz erfolgreich zugewiesen wurde.

    ![Überprüfen des Lizenzstatus](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Zuweisen von Lizenzen im Azure-Portal

Führen Sie folgende Schritte aus, um einzelnen Benutzerkonten Power BI Pro-Lizenzen zuzuweisen:

1. Öffnen Sie das [Azure-Portal](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Wählen Sie im Navigationsbereich **Azure Active Directory** aus.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Wählen Sie unter **Azure Active Directory** die Option **Lizenzen** aus.

    ![Lizenzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Wählen Sie unter **Lizenzen** die Option **Alle Produkte** und dann **Power BI Pro** aus, um die Liste der lizenzierten Benutzer anzuzeigen.

    ![Lizenzen – alle Produkte](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Klicken Sie auf **Zuweisen**, um einem Benutzerkonto eine Power BI Pro-Lizenz hinzuzufügen.

    ![Zuweisen einer Lizenz](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Lizenzen zugewiesen haben, informieren Sie sich eingehend über Power BI Pro.

[Power BI licensing in your organization (Power BI-Lizenzierung in Ihrem Unternehmen)](service-admin-licensing-organization.md)

[Suchen nach angemeldeten Power BI-Benutzern](service-admin-access-usage.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
