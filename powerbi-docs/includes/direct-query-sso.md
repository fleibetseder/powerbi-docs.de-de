---
title: Includedatei
description: Includedatei
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: davidi
ms.openlocfilehash: eec30d11c1bd99271416ab1a3a2dbb581687e315
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698308"
---
## <a name="single-sign-on"></a>Einmaliges Anmelden

Nachdem Sie ein Azure SQL DirectQuery-Dataset im Dienst veröffentlichen, können Sie einmaliges Anmelden (Single Sign-On, SSO) über Azure AD-OAuth2 (Azure Active Directory) für Endbenutzer aktivieren.

Um SSO zu aktivieren, rufen Sie die Einstellungen für das Dataset auf, öffnen die Registerkarte **Datenquellen**, und aktivieren Sie das Kontrollkästchen „SSO“.

![Dialogfeld zum Konfigurieren von Azure SQL-Datenquellen](media/direct-query-sso/sso-dialog.png)

Wenn die Option „SSO“ aktiviert ist und Benutzer auf Berichte zugreifen, die auf der Datenquelle beruhen, werden deren authentifizierte Azure AD-Anmeldeinformationen von Power BI in den Abfragen an die Azure SQL-Datenbank oder das Data Warehouse gesendet. Dadurch wird sichergestellt, dass die auf Datenquellenebene konfigurierten Sicherheitseinstellungen in Power BI berücksichtigt werden.

Die SSO-Option gilt für alle Datasets, die diese Datenquelle verwenden. Sie hat keine Auswirkungen auf das Authentifizierungsverfahren, das bei Importszenarien verwendet wird.

> [!Note]
> Azure Multi-Factor Authentication (MFA) wird nicht unterstützt. Benutzer, die SSO mit Azure SQL DirectQuery verwenden möchten, müssen von MFA ausgenommen werden.