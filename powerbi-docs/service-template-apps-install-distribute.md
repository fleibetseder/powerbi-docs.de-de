---
title: 'Verteilen von Vorlagen-Apps in Ihrer Organisation: Power BI'
description: Erfahren Sie mehr über das Installieren, Anpassen und Verteilen von Vorlagen-Apps in Ihrer Organisation mit Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 158345c44f8801a98e19dcd9b4c7dde14aa6126b
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264535"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>Installieren und Verteilen von Vorlagen-Apps in Ihrer Organisation: Power BI

Sind Sie Power BI-Analyst? Wenn dies der Fall ist, erfahren Sie in diesem Artikel, wie Sie *Vorlagen-Apps* installieren, um eine Verbindung mit den von Ihnen im Geschäftsalltag verwendeten Diensten wie Salesforce, Microsoft Dynamics und Google Analytics herzustellen. Sie können das Dashboard und Berichte gemäß den Anforderungen Ihrer Organisation ändern und als *App* an Ihre Kollegen verteilen. 

![Installierte Power BI-Apps](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Wenn Sie daran interessiert sind, Ihre eigenen Vorlagen-Apps zu erstellen und zu verteilen, finden Sie Informationen dazu unter [Create a template app in Power BI (Erstellen einer Vorlagen-App in Power BI)](service-template-apps-create.md). Power BI-Partner können Power BI-Apps ohne oder mit nur wenig Code erstellen, und diese dann für Power BI-Kunden bereitstellen. 

## <a name="prerequisites"></a>Voraussetzungen  

Dies sind die Anforderungen zum Installieren, Anpassen und Verteilen einer Vorlagen-App: 

- Eine [Power BI Pro-Lizenz](service-self-service-signup-for-power-bi.md)
- Vertrautheit mit den [grundlegenden Konzepten von Power BI](service-basic-concepts.md)
- Ein gültiger Installationslink vom Hersteller der Vorlagen-App oder von AppSource. 
- Berechtigungen zum Installieren von Vorlagen-Apps 

## <a name="install-a-template-app"></a>Installieren einer Vorlagen-App

Entweder Sie erhalten einen Link zu einer Vorlagen-App oder Sie suchen in AppSource nach einer Vorlagen-App, die Sie interessiert. In beiden Fällen können Sie sie nach der Installation anpassen und in Ihrer Organisation verteilen.

### <a name="search-appsource-from-a-browser"></a>Durchsuchen von AppSource im Browser

Klicken Sie im Browser auf den folgenden Link, um AppSource mit einem Filter für Power BI-Apps zu öffnen:

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>Durchsuchen von AppSource über den Power BI-Dienst

1. Klicken Sie im linken Navigationsbereich des Power BI-Diensts auf **Apps** > **Apps abrufen**.

    ![Apps abrufen](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. Klicken Sie in AppSource auf **Apps**.

    ![In AppSource suchen](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. Suchen Sie nach einer App, und klicken Sie dann auf **Jetzt holen**.

4. Klicken Sie im Dialogfeld auf **Installieren**.

    ![App installieren:](media/service-template-apps-install-distribute/power-install-dialog.png) Wenn Sie über eine Power BI Pro-Lizenz verfügen, wird die App mit dem zugehörigen App-Arbeitsbereich installiert. Sie können die App im zugehörigen Arbeitsbereich anpassen.

    Nach der Installation wird eine Benachrichtigung angezeigt, die angibt, dass Ihre App bereit ist.
4. Klicken Sie auf **Zu App wechseln**.
5. Wählen Sie unter **Erste Schritte mit Ihrer neuen App** eine der drei Optionen aus:

    ![Erste Schritte mit Ihrer neuen App](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **App erkunden:** Grundlegendes Beispiel für das Durchsuchen von Daten. Beginnen Sie hiermit, um sich mit der App vertraut zu machen. 
    - **Daten verbinden:** Hiermit können Sie die Datenquelle für die Beispieldaten in Ihre eigene Datenquelle ändern. Sie können die Datasetparameter und die Anmeldeinformationen für die Datenquelle neu definieren. Weitere Informationen finden Sie im Abschnitt [Known limitations (Bekannte Einschränkungen)](service-template-apps-tips.md#known-limitations) im Artikel mit Tipps zu Vorlagen-Apps. 
    - **Zu Arbeitsbereich wechseln** (die umfangreichste Option): Sie können beliebige Änderungen vornehmen, die vom App-Ersteller erlaubt werden.

    Alternativ können Sie dieses Dialogfeld überspringen und direkt über **Arbeitsbereiche** im linken Navigationsbereich auf den zugehörigen Arbeitsbereich zugreifen.
    >[!NOTE]
    >Durch das Installieren einer App wurden jeweils eine *Organisations-App* sowie ein *App-Arbeitsbereich* erstellt. Hier finden Sie weitere Informationen zum [Verteilen von Apps in Power BI](service-create-distribute-apps.md).
 
6. Bevor Sie die App für Ihre Kollegen freigeben, sollten Sie sie mit Ihren eigenen Daten verbinden. Möglicherweise sollten Sie den Bericht oder das Dashboard für Ihre Organisation anpassen. Zu diesem Zeitpunkt können Sie außerdem andere Berichte oder Dashboards hinzufügen.

   Wenn Sie einen Installationslink für eine App auswählen, die nicht in AppSource aufgeführt ist, müssen Sie in einem daraufhin angezeigten Dialogfeld Ihre Auswahl bestätigen.

   ![Installieren der App](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >Damit Sie Vorlagen-Apps installieren können, die nicht in AppSource aufgeführt sind, müssen Sie diese mithilfe Ihrer Administratorberechtigungen anfordern. Details finden Sie unter Power BI-[Verwaltungsportal > Vorlagen-App-Einstellungen](service-admin-portal.md#template-apps-settings).

## <a name="update-and-distribute-the-app"></a>Aktualisieren und Verteilen der App

Nachdem Sie die App für Ihre Organisation aktualisiert haben, können Sie sie veröffentlichen. Die Schritte gleichen dem Veröffentlichen jeder anderen App.

1. Wenn Sie die Anpassung abgeschlossen haben, klicken Sie in oberen rechten Ecke der Arbeitsbereichslistenansicht auf **App aktualisieren**.  

    ![App-Installation starten](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. Unter **Details** können Sie die Beschreibung und Hintergrundfarbe anpassen.

   ![App-Beschreibung und Farbe festlegen](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. Unter **Inhalt** können Sie das Dashboard oder den Bericht als Landing Page auswählen.

   ![Landing Page der App festlegen](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. Unter **Zugriff** können Sie ausgewählten Benutzern oder Ihrer gesamten Organisation Zugriff erteilen.  

   ![App-Zugriff festlegen](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. Klicken Sie auf **App aktualisieren**. 

6. Nachdem die App erfolgreich veröffentlicht wurde, können Sie den Link kopieren und den Personen mitteilen, denen Sie den Zugriff erteilt haben. Wenn Sie die App für sie freigegeben haben, wird sie ihnen auf der Registerkarte **Meine Organisation** in AppSource angezeigt.

## <a name="next-steps"></a>Nächste Schritte 

[Gemeinsames Erstellen von Arbeitsbereichen mit Ihren Kollegen in Power BI](service-create-workspaces.md)





. 

 
