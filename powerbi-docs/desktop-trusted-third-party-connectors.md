---
title: Vertrauenswürdige Connectors von Drittanbietern in Power BI
description: Vorgehensweise beim Anerkennen der Vertrauenswürdigkeit eines signierten Drittanbieterconnectors in Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: ac3f795d6a80d5f143daf68436f41f5771b3c2bb
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876163"
---
# <a name="trusting-third-party-connectors"></a>Anerkennen von Drittanbieterconnectors als vertrauenswürdig

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Warum benötigen Sie vertrauenswürdige Connectors von Drittanbietern?

Es wird grundsätzlich empfohlen, in Power BI eine höhere Sicherheitsstufe für die Datenerweiterung zu verwenden, um zu verhindern, dass nicht von Microsoft zertifizierter Code geladen wird. Es kann jedoch häufiger der Fall sein, dass Sie bestimmte Connectors laden möchten, die Sie geschrieben haben, oder die Ihnen ein Berater oder Anbieter außerhalb des Microsoft-Zertifizierungspfads bereitgestellt wurden.

Der Entwickler eines bestimmten Connectors kann diesen mit einem Zertifikat signieren und Ihnen die erforderlichen Informationen bereitstellen, wie Sie den Connector sicher laden können, ohne die Sicherheitseinstellungen zu senken.

Wenn Sie mehr über die Sicherheitseinstellungen erfahren möchten, können Sie sich [hier](https://docs.microsoft.com/power-bi/desktop-connector-extensibility) informieren.

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Verwenden der Registrierung zum Einrichten von vertrauenswürdigen Drittanbieterconnectors

Das Zulassen von vertrauenswürdigen Drittanbieterconnectors in Power BI erfolgt durch Auflisten des Zertifikatfingerabdrucks, dem Sie vertrauen möchten, in einem angegebenen Registrierungswert. Wenn dieser Fingerabdruck mit dem Zertifikatsfingerabdruck auf dem Connector übereinstimmt, den Sie laden möchten, können Sie ihn in der „empfohlenen“ Sicherheitsstufe von Power BI laden. 

Der Registrierungspfad lautet HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Stellen Sie sicher, dass der Pfad vorhanden ist, oder erstellen Sie ihn. Dieser Speicherort wurde ausgewählt, da er in erster Linie durch IT-Richtlinien gesteuert wird und zu dessen Bearbeitung auf die Verwaltung des lokalen Computers zugegriffen werden muss. 

![Registrierung von Power BI Desktop ohne vertrauenswürdige Schlüssel von Drittanbietern](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Fügen Sie unter dem oben angegebenen Pfad einen neuen Wert hinzu. Der Typ muss ein „mehrteiliger Zeichenfolgenwert“ (REG_MULTI_SZ) sein, und er muss als „TrustedCertificateThumbprints“ bezeichnet werden. 

![Registrierung von Power BI Desktop mit einem Eintrag für vertrauenswürdige Drittanbieterconnectors ohne Schlüssel](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Fügen Sie die Fingerabdrücke der Zertifikate hinzu, die Sie als vertrauenswürdig einstufen möchten. Sie können mehrere Zertifikate hinzufügen, indem Sie „\ 0“ als Trennzeichen verwenden. Sie können auch im Registrierungs-Editor mit der rechten Maustaste klicken, und Änderungen vornehmen, indem Sie jeden Fingerabdruck in einer neuen Zeile ablegen. Der Beispielfingerabdruck stammt von einem selbstsignierten Zertifikat. 

 ![Registrierung von Power BI Desktop mit vertrauenswürdigen Schlüsseln von Drittanbietern](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Wenn Sie die Anweisungen korrekt befolgt haben und den richtigen Fingerabdruck vom Entwickler erhalten haben, sollten Sie nun den mit dem zugehörigen Zertifikat signierten Connectors vertrauen können.

## <a name="how-to-sign-connectors"></a>Signieren von Connectors

Wenn Sie über einen Connector verfügen, den Sie oder ein Entwickler signieren müssen, können Sie die entsprechenden Informationen in der Power Query-Dokumentation [hier](https://docs.microsoft.com/power-query/handlingconnectorsigning) nachlesen.
