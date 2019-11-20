---
title: Was sind Power BI-Vorlagen-Apps?
description: Dieser Artikel enthält eine Übersicht über Vorlagen-Apps in Power BI. Erfahren Sie, wie Sie Power BI-Apps ohne oder mit nur wenig Code erstellen, und diese dann für Power BI-Kunden bereitstellen.
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: tebercov
ms.openlocfilehash: 4b4e32f787d2d262d604ff0745f8c028e9fff949
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871318"
---
# <a name="what-are-power-bi-template-apps"></a>Was sind Power BI-Vorlagen-Apps?

Mit den neuen *Vorlagen-Apps* von Power BI können Power BI-Partner Power BI-Apps ohne oder mit nur wenig Code erstellen und für Power BI-Kunden bereitstellen.  Dieser Artikel enthält eine Übersicht über Vorlagen-Apps in Power BI.

Vorlagen-Apps sind ein Ersatz für die aktuellen Dienstinhaltspakete. Als Power BI-Partner erstellen Sie sofort verfügbare Inhalte für Ihre Kunden und veröffentlichen diese selbst.  

Sie können Vorlagen-Apps erstellen, mit denen Ihre Kunden eine Verbindung mit ihren eigenen Konten herstellen und diese instanziieren können. Als Domänenexperten können sie die Daten so freigeben, dass diese von ihren Geschäftskunden mühelos genutzt werden können.  

Sie übermitteln Ihre Vorlagen-Apps an das Cloud-Partnerportal. Die Apps werden dann im Power BI-App-Katalog (app.powerbi.com/getdata/services) und in Microsoft AppSource (appsource.microsoft.com) öffentlich zur Verfügung gestellt. Hier erhalten Sie einen Überblick über die Erstellung von öffentlichen Vorlagen-Apps.  

## <a name="process"></a>Verfahren
Der allgemeine Prozess zum Entwickeln und Übermitteln einer Vorlagen-App umfasst mehrere Phasen. Manche Phasen umfassen mehr als eine Aktivität zur gleichen Zeit.


| Phase | Power BI Desktop |  |Power BI-Dienst  |  |Cloud-Partnerportal  |
|---|--------|--|---------|---------|---------|
| **Eins** | Erstellen Sie ein Datenmodell und einen Bericht in einer PBIX-Datei. |  | Erstellen Sie einen Arbeitsbereich, importieren Sie die PBIX-Datei, und erstellen Sie ein komplementäres Dashboard.  |  | Registrieren Sie sich als Partner |
| **Zwei** |  |  | Erstellen Sie ein Testpaket, und führen Sie die interne Validierung aus.        |  | |
| **Drei** | |  | Stufen Sie das Testpaket auf die Präproduktion für die Validierung außerhalb Ihres Power BI-Mandanten auf, und übermitteln Sie es an AppSource.  |  | Erstellen Sie ein Angebot für Ihre Power BI-Vorlagen-App mit Ihrem Präproduktionspaket, und starten Sie den Validierungsprozess. |
| **Vier** | |  | Stufen Sie das Präproduktionspaket zur Produktion auf. |  | Schalten Sie die App „Live“. |

## <a name="before-you-begin"></a>Vorbereitung

Zum Erstellen der Vorlagen-App benötigen Sie zunächst die erforderlichen Berechtigungen. Informationen dazu finden Sie in den Vorlagen-App-Einstellungen im Power BI-Verwaltungsportal. 

Zum Veröffentlichen einer Vorlagen-App im Power BI-Dienst und in AppSource müssen Sie die Anforderungen unter [Weg zum Cloud Marketplace-Herausgeber](https://docs.microsoft.com/azure/marketplace/become-publisher) erfüllen.
 
## <a name="high-level-steps"></a>Allgemeine Schritte

Im Folgenden werden die allgemeinen Schritte aufgeführt. 

1. [Überprüfen Sie die Anforderungen](#requirements), um sicherzustellen, dass Sie sie erfüllen. 

1. Erstellen Sie einen Bericht in Power BI Desktop. Verwenden Sie Parameter, damit Sie den Bericht als Datei speichern können, die von anderen benutzt werden kann. 

1. Erstellen Sie einen Arbeitsbereich für Ihre Vorlagen-App in Ihrem Mandanten im Power BI-Dienst (app.powerbi.com). 

1. Importieren Sie Ihre PBIX-Datei, und fügen Sie Inhalte, z.B. ein Dashboard, zu Ihrer App hinzu. 

1. Erstellen Sie ein Testpaket, um die Vorlagen-App innerhalb Ihrer Organisation selbst zu testen. 

1. Stufen Sie die Test-App zur Präproduktion hinauf, um die App für die Validierung an AppSource zu übermitteln und sie außerhalb Ihres eigenen Mandanten zu testen. 

1. Übermitteln Sie den Inhalt zur Veröffentlichung an das Cloud-Partnerportal. 

1. Stellen Sie Ihr Angebot in AppSource „Live“, und verschieben Sie Ihre App in Power BI in die Produktion.
2. Sie können jetzt mit der Entwicklung der nächsten Version im gleichen Arbeitsbereich in der Präproduktion beginnen. 

## <a name="requirements"></a>Anforderungen

Zum Erstellen der Vorlagen-App benötigen Sie zunächst die erforderlichen Berechtigungen. Details finden Sie unter Power BI-[Verwaltungsportal > Vorlagen-App-Einstellungen](service-admin-portal.md#template-apps-settings). 

Zum Veröffentlichen einer Vorlagen-App im Power BI-Dienst und in AppSource müssen Sie die Anforderungen unter [Weg zum Cloud Marketplace-Herausgeber](https://docs.microsoft.com/azure/marketplace/become-publisher) erfüllen.
 > [!NOTE] 
 > Übermittelte Vorlagen-Apps werden im [Cloud-Partnerportal](https://cloudpartner.azure.com) verwaltet. Verwenden Sie für die Anmeldung dasselbe Microsoft Developer Center-Registrierungskonto. Sie sollten nur über ein Microsoft-Konto für Ihre AppSource-Angebote verfügen. Konten sollten nicht speziell für einzelne Dienste oder Angebote geführt werden.

## <a name="tips"></a>Tipps 

- Stellen Sie sicher, dass Ihre App Beispieldaten enthält, damit sie mit nur einem Klick verwendet werden kann. 
- Überprüfen Sie Ihre Anwendung sorgfältig, indem Sie sie in Ihrem Mandanten und einem sekundären Mandanten installieren. Stellen Sie sicher, dass Kunden nur das angezeigt bekommen, was sie sehen sollen. 
- Verwenden Sie AppSource als Onlineshop zum Hosten Ihrer Anwendung. Auf diese Weise können alle Power BI-Benutzer Ihre App finden. 
- Erwägen Sie die Bereitstellung mehrerer Vorlagen-Apps für verschiedene spezifische Szenarios. 
- Aktivieren Sie die Datenanpassung, um beispielsweise benutzerdefinierte Verbindungs- und Parameterkonfiguration durch den Installer zu unterstützen.

Weitere Vorschläge finden Sie unter [Tips for authoring template apps in Power BI (Tipps für die Erstellung von Vorlagen-Apps in Power BI)](service-template-apps-tips.md).

## <a name="support"></a>Support
Unterstützung während der Entwicklung finden Sie unter [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Diese Website wird aktiv überwacht und verwaltet. Kundenanfragen werden schnell an das entsprechende Team weitergeleitet.

## <a name="next-steps"></a>Nächste Schritte

[Create a template app (Erstellen einer Vorlagen-App)](service-template-apps-create.md)
