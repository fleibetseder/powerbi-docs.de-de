---
title: Grundlegendes zur Sicherheit auf Zeilenebene (Row-Level Security; RLS) mit Power BI Desktop
description: Erfahren Sie, wie Sie die Sicherheit auf Zeilenebene für importierte Datasets und DirectQuery in Power BI Desktop konfigurieren.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 08/14/2019
LocalizationGroup: Create reports
ms.openlocfilehash: d3c3310b6fd60d0e6f30eabd4c5136af5b8c54ff
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73866012"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Sicherheit auf Zeilenebene (row-level security; RLS) mit Power BI Desktop

Sie können die RLS zusammen mit Power BI Desktop verwenden, um den Datenzugriff bestimmter Benutzer einzuschränken. Filter beschränken die Daten auf Zeilenebene. Sie können Filter für Rollen definieren.

Sie können RLS jetzt für Datenmodelle konfigurieren, die mithilfe von Power BI Desktop in Power BI importiert wurden. Außerdem können Sie die RLS für Datasets konfigurieren, die [DirectQuery](desktop-use-directquery.md) verwenden. Dies ist beispielsweise für SQL Server möglich. Bisher konnte die RLS nur in lokalen Analysis Services-Modellen außerhalb von Power BI implementiert werden. Für Liveverbindungen von Analysis Services konfigurieren Sie RLS auf dem lokalen Modell. Die Sicherheitsoption wird nicht für Liveverbindungsdatasets angezeigt.

> [!IMPORTANT]
> Wenn Sie im Power BI-Dienst Rollen und Regeln definiert haben, müssen Sie diese Rollen in Power BI Desktop neu erstellen und den Bericht im Dienst veröffentlichen.

Erfahren Sie mehr über die Optionen für [RLS innerhalb des Power BI-Diensts](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Nächste Schritte

[Sicherheit auf Zeilenebene (row-level security; RLS) mit Power BI](service-admin-rls.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)