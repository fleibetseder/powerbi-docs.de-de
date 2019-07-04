---
title: Aktualisieren, Löschen und Extrahieren einer Power BI-Vorlagen-App
description: 'Vorgehensweise: Aktualisieren, Löschen und Extrahieren einer Vorlagen-App.'
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 273734493c761739f9780e6a7fe6e781900723f9
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67125876"
---
# <a name="update-delete-and-extract-template-app"></a>Aktualisieren, Löschen und Extrahieren einer Vorlagen-App

Da sich Ihre App nun in der Produktionsphase befindet, können Sie in die Testphase zurückkehren, ohne den Status der App in der Produktionsphase ändern zu müssen.
## <a name="update-your-app"></a>Aktualisieren Ihrer App


1. Klicken Sie im **Release Management**-Bereich auf **Create app** (App erstellen).
2. Wechseln Sie zurück in den App-Erstellungsprozess.
3. Nachdem Sie die Kategorien **Branding**, **Content** (Inhalt), **Control** (Steuerung) und **Access** (Zugriff) eingestellt haben, klicken Sie erneut auf **Create app** (App erstellen).
4. Wählen Sie **Close** (Schließen) aus, und wechseln Sie zurück zu **Release Management**.

   Wie Sie sehen, haben Sie nun zwei Versionen: Die Version in der Produktionsphase und zusätzlich eine neue Version in der Testphase.

    ![Zwei Versionen einer Vorlagen-App](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. Wenn Sie bereit sind, Ihre App in die Präproduktionsphase höherzustufen, um Tests außerhalb Ihres Mandanten durchzuführen, wechseln Sie zurück in den Release Management-Bereich, und wählen Sie **App höher stufen** neben **Tests** aus.
6. Ihr Link ist nun live geschaltet. Senden Sie ihn noch mal an das Cloud-Partnerportal (CPP), indem Sie die Schritte unter [Aktualisieren eines Power BI-App-Angebots](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer) befolgen.
7. In CPP müssen Sie Ihr Angebot erneut **veröffentlichen** sowie erneut validieren lassen.

>[!NOTE]
>Stufen Sie Ihre App nur höher in die Produktionsphase, nachdem sie vom Cloud-Partnerportal genehmigt wurde und Sie sie veröffentlichen.

## <a name="extract-workspace"></a>Extrahieren des Arbeitsbereichs
Das Zurücksetzen auf die vorherige Version einer Template-App ist mit der Extraktionsfunktion einfacher denn je. Die folgenden Schritte extrahieren eine bestimmte App-Version aus verschiedenen Releasestufen in einen neuen Arbeitsbereich:

1. Wählen Sie im Bereich „Releaseverwaltung“ weiter **(...)** und dann **Extrahieren** aus.

    ![Extrahieren der Vorlagen-App-Version](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![Extrahieren der Vorlagen-App-Version](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. Geben Sie im Dialogfeld den Namen für den extrahierten Arbeitsbereich ein. Ein neuer Arbeitsbereich wird hinzugefügt.

Ihre neue Arbeitsbereichsversionierung wird zurückgesetzt, und Sie können die Vorlagen-App aus dem neu extrahierten Workspace weiter entwickeln und verteilen.

## <a name="delete-template-app-version"></a>Löschen der Vorlagen-App-Version
Ein Vorlagen-App-Arbeitsbereich ist die Quelle einer aktiven verteilten Vorlagen-App. Um die Benutzer der Vorlagen-App zu schützen, ist es nicht möglich, einen Arbeitsbereich zu löschen, ohne zuvor alle erstellten App-Versionen im Arbeitsbereich zu entfernen.
Das Löschen einer App-Version löscht auch die App-URL, die nicht mehr funktioniert.

1. Wählen Sie im Bereich „Releaseverwaltung“ die Auslassungspunkte **(...)** und dann **Löschen** aus.
 ![Löschen der Vorlagen-App-Version](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
  ![Löschen der Vorlagen-App-Version](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Achten Sie darauf, dass Sie keine App-Versionen löschen, die von Kunden oder **AppSource** verwendet werden, da sie sonst nicht mehr funktionieren.

## <a name="next-steps"></a>Nächste Schritte

Sehen Sie unter [Install, customize, and distribute template apps in your organization (Installieren, anpassen und verteilen von Vorlagen-Apps in Ihrer Organisation)](service-template-apps-install-distribute.md), wie Ihre Kunden mit Ihrer Vorlagen-App interagieren.

Weitere Informationen über die Verteilung Ihrer App finden Sie unter [Power BI Application offer (Angebot für Power BI-Anwendungen)](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
