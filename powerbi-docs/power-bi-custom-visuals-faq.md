---
title: Häufig gestellte Fragen zu Power BI-Visuals
description: Durchsuchen Sie die Liste der häufig gestellten Fragen und Antworten zu benutzerdefinierten Visuals in Power BI.
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 58fa65abfa2d2cff5e02b34fe8db8aa10b36ee14
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415382"
---
# <a name="frequently-asked-questions-about-power-bi-visuals"></a>Häufig gestellte Fragen zu Power BI-Visuals

## <a name="organizational-custom-visuals"></a>Benutzerdefinierte Visuals für Organisationen

Mit dem Verwaltungsportal können Sie Power BI-Visuals für Ihre Organisation verwalten.

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>Wie kann der Administrator die benutzerdefinierten Visuals für Organisationen verwalten?

Im Administratorportal kann der Administrator auf der Registerkarte „Benutzerdefinierte Visuals für Organisationen“ [alle benutzerdefinierten Visuals im Unternehmen sehen und verwalten](service-admin-portal.md#organizational-visuals): hinzufügen, deaktivieren, aktivieren und löschen.
Diese Visuals müssen nicht mehr per E-Mail oder über einen freigegebenen Ordner weitergegeben werden. Nach der Bereitstellung im Repository der Organisation können die Benutzer in der Organisation diese benutzerdefinierten Visuals für Organisationen einfach finden und direkt über Power BI Desktop oder -Dienst in ihre Berichte importieren. Die benutzerdefinierten Visuals für Organisationen finden Sie im integrierten Store (in Desktop und Dienst) auf der Registerkarte *MEINE ORGANISATION*. Sobald der Administrator eine neue Version eines benutzerdefinierten Visuals hochlädt, erhält jeder in der Organisation die gleiche aktualisierte Version. Berichtsautoren müssen das Visual in ihren Berichten nicht löschen, um die neue Version zu erhalten, da alle Berichte, die diese Visuals verwenden, automatisch aktualisiert werden! Der Aktualisierungsmechanismus ist ähnlich wie bei den Visuals im Marketplace.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Wenn ein Administrator ein benutzerdefiniertes Visual vom öffentlichen Marketplace in den Unternehmensspeicher hochlädt, wird es dann automatisch aktualisiert, sobald ein Anbieter das Visual auf dem öffentlichen Marketplace aktualisiert?

Nein, es gibt keine automatische Aktualisierungen vom öffentlichen Marketplace.
Es liegt in der Verantwortung des Administrators, die Version der benutzerdefinierten Visuals zu aktualisieren.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>Gibt es eine Möglichkeit, den Store der Organisation zu deaktivieren?

Nein, die Registerkarte „MEINE ORGANIZATION“ aus Power BI Desktop und -Dienst wird für die Benutzer immer angezeigt. Der Administrator kann alle benutzerdefinierten Visuals für Organisationen im Administratorportal deaktivieren oder löschen, und der Speicher der Organisation ist dann leer.
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>Wenn der Administrator benutzerdefinierte Visuals über das Administratorportal deaktiviert (Mandanteneinstellungen), haben Benutzer dann noch Zugriff auf die benutzerdefinierten Visuals?

Ja, wenn der Administrator die benutzerdefinierten Visuals im Administratorportal deaktiviert, hat dies keine Auswirkungen auf den Speicher der Organisation. Einige Organisationen deaktivieren benutzerdefinierte Visuals und aktivieren nur handverlesene Visuals, die vom Power BI-Administrator importiert und in den Speicher der Organisation hochgeladen wurden. Das Deaktivieren der benutzerdefinierten Visuals über das Administratorportal wird in Power BI Desktop nicht erzwungen. Desktop-Benutzer können weiterhin benutzerdefinierte Visuals vom öffentlichen Marketplace in ihren Berichten hinzufügen und verwenden. Diese öffentlichen benutzerdefinierten Visuals beenden jedoch das Rendering nach der Veröffentlichung im Power BI-Dienst und geben einen entsprechenden Fehler aus. Wenn Sie den Power BI-Dienst verwenden, können Sie keine benutzerdefinierten Visuals vom öffentlichen Marketplace importieren. Es können nur Visuals aus dem Speicher der Organisation importiert werden, da die Einstellung für benutzerdefinierte Visuals im Administrationsportal im Power BI-Dienst erzwungen wird.

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>Warum sind der Store der Organisation und die benutzerdefinierten Visuals in Kombination eine großartige Unternehmenslösung?

* Jeder erhält die gleiche visuelle Ansicht, die vom Power BI-Administrator gesteuert wird. Sobald der Administrator die Version des Visuals im Administratorportal aktualisiert, erhalten alle Benutzer in der Organisation automatisch die aktualisierte Version.

* Sie müssen keine Visual-Dateien mehr per E-Mail oder einem freigegebenen Ordner mehr weitergeben! Eine zentrale Anlaufstelle, sichtbar für alle angemeldeten Mitglieder.

* Sicherheit und Unterstützung, neue Versionen von benutzerdefinierten Visuals werden ähnlich den Marketplace-Visuals automatisch in allen Berichten aktualisiert.

* Benutzer in der Organisation, die die benutzerdefinierten Visuals verwenden, müssen angemeldet sein, um diese Visuals zu sehen und zu verwenden, die ein Sicherheitselement für die Organisation darstellen.

* Administratoren können steuern, welche benutzerdefinierten Visuals in der Organisation verfügbar sein sollen.

* Administratoren können Visuals zu Testzwecken im Administratorportal aktivieren/deaktivieren. Es besteht eine bessere Sicherheitsdurchsetzung, da diese Visuals nur für Organisationsmitglieder erlaubt sind.

## <a name="certified-custom-visuals"></a>Zertifizierte benutzerdefinierte Visuals

### <a name="what-are-certified-custom-visuals"></a>Was sind zertifizierte benutzerdefinierte Visuals?

Zertifizierte benutzerdefinierte Visuals sind Visuals im [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals), die bestimmte [angegebene](power-bi-custom-visuals-certified.md) Codeanforderungen und Testkriterien des Power BI-Teams erfüllen.  Die durchgeführten Tests wurden entworfen, um zu überprüfen, ob das Visual nicht auf externe Dienste oder Ressourcen zugreift. Microsoft ist jedoch nicht der Autor benutzerdefinierter Drittanbietervisuals, und Kunden wird empfohlen, direkt mit dem Autor Kontakt aufzunehmen, um die Funktionalität eines solchen Visuals zu überprüfen.

### <a name="what-tests-are-done-during-the-certification-process"></a>Welche Tests werden während des Zertifizierungsprozesses durchgeführt?

Die Zertifizierungsprozesstests beinhalten u. a. Folgendes: Codebewertungen, statische Codeanalyse, Testen auf Datenlecks, Testen mit zufälligen Daten, Penetrationstests, XSS-Zugriffstests, Einschleusung schädlicher Daten, Eingabeüberprüfung und Funktionstests.
 
### <a name="do-you-certify-visuals-every-submission"></a>Werden Visuals bei jeder Einreichung zertifiziert?

Ja. Jedes Mal, wenn eine neue Version eines zertifizierten Visuals im Marketplace eingereicht wird, wird das Update der Visualversion denselben Zertifizierungsüberprüfungen unterzogen.

Hinweis für Entwickler: Wenn Sie ein Versionsupdate eines zertifizierten Visuals einreichen, müssen Sie keine separate E-Mail versenden. Dies ist nur für die [erstmalige Anforderung einer Zertifizierung](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification) erforderlich. Die Zertifizierung von Versionsupdates erfolgt automatisch. Für jegliche Verstöße, die zu einer Ablehnung führen, wird eine E-Mail mit den Details versendet, welche Probleme behoben werden müssen. 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>Ist es möglich, dass ein zertifiziertes Visual durch ein neues Update seine Zertifizierung verliert?

Nein, das ist nicht möglich. Einem zertifizierten Visual kann die Zertifizierung durch ein neues Update nicht entzogen werden. Das Update wird zurückgewiesen.
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>Muss ich meinen Code im öffentlichen Repository veröffentlichen, wenn ich ein Projekt dem Zertifizierungsprozess unterziehen möchte?

Nein, Sie müssen Ihren Code nicht veröffentlichen. Sie müssen uns jedoch Leseberechtigungen erteilen, damit der Code der Visuals überprüft werden kann. Beispiel: Privates Repository in GitHub.
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>Muss das Visual für die Zertifizierung im [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) [veröffentlicht](https://docs.microsoft.com/power-bi/developer/office-store) werden?

Ja. Für eine Zertifizierung ist es zwingend erforderlich, das Visual zuerst im Marketplace zu veröffentlichen.
Damit ein benutzerdefiniertes Visual zertifiziert werden kann, sollte es sich auf unseren Servern befinden. Es ist nicht möglich, private Visuals zu zertifizieren.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Wie lange benötigt die Zertifizierung eines Visuals?

Für eine aktualisierte Version dauert es bis zu 3 Wochen. Bei einer neuen Einreichung (erstmalige Zertifizierung) können bis zu 4 Wochen vergehen. 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>Garantiert der Zertifizierungsprozess, dass keine Datenlecks vorkommen?

Die durchgeführten Tests wurden entworfen, um zu überprüfen, ob das Visual nicht auf externe Dienste oder Ressourcen zugreift. Microsoft ist jedoch nicht der Autor benutzerdefinierter Drittanbietervisuals, und Kunden wird empfohlen, direkt mit dem Autor Kontakt aufzunehmen, um die Funktionalität eines solchen Visuals zu überprüfen.
 
### <a name="are-uncertified-custom-visuals-safe-to-use"></a>Ist es sicher, nicht zertifizierte Visuals zu verwenden?

Bei nicht zertifizierten benutzerdefinierten Visuals handelt es sich nicht zwangsläufig um unsichere Visuals.
Einige Visuals sind nicht zertifiziert, da sie mindestens einem Punkt der [Zertifizierungsanforderungen](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements) nicht entsprechen. Beispiele hierfür sind die Herstellung einer Verbindung zu einem externen Dienst wie Kartenvisuals oder Visuals, die kommerzielle Bibliotheken verwenden.
 
## <a name="visuals-with-additional-purchases"></a>Visuals mit zusätzlichen Käufen

### <a name="what-is-a-visual-with-additional-purchases"></a>Was ist ein Visual mit zusätzlichen Käufen?

Ein Visual mit zusätzlichen Käufen ähnelt Add-Ins mit In-App-Kauf (In-app purchase, IAP) im Marketplace. Das Preisschild dieser Add-Ins lautet **Möglicherweise sind zusätzliche Käufe erforderlich**.

Benutzerdefinierte IAP-Visuals sind kostenlose, herunterladbare benutzerdefinierte Visuals – die Benutzer zahlen nichts für den Download dieser benutzerdefinierten Visuals aus dem Marketplace. In IAP-Visuals stehen optionale In-App-Käufe für erweiterte Features zur Verfügung.  

### <a name="whats-the-benefit-to-developers"></a>Worin liegt der Vorteil für Entwickler?

Benutzerdefinierte IAP-Visuals werden in AppSource von den vielen täglichen Besuchern entdeckt und bedeuten für Ihre benutzerdefinierten IAP-Visuals und Sie als Entwickler wertvollen Datenverkehr und gesteigerte Bekanntheit.

Wenn Sie Ihre Visuals bis vor Kurzem über Ihre Website verwaltet haben, können Sie sie jetzt bei AppSource einreichen. Dadurch werden Auffindbarkeit und Sichtbarkeit der IAP-Visuals innerhalb der Power BI-Community gesteigert.

Visuals in AppSource nutzen einen direkten Feedbackkanal von Ihren Kunden, die das benutzerdefinierte IAP-Visual verwenden, für das Rezensions- und Bewertungssystem im Store.  

Nachdem Ihre IAP-Visuals vom AppSource-Validierungsteam genehmigt wurden, können Sie sie darüber hinaus zur Zertifizierung einreichen. Dies ist ein optionaler Vorgang.  

Nach erfolgter Zertifizierung können benutzerdefinierte IAP-Visuals in PowerPoint exportiert und in den empfangenen E-Mail angezeigt werden, wenn ein Benutzer Berichtsseiten abonniert. Durch Einreichen von IAP-Visuals beim Marketplace können benutzerdefinierte IAP-Visuals heute also auch zertifiziert werden und einen Satz zusätzlicher Features unterstützen.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Müssen IAP Visuals zertifiziert werden?

Der Zertifizierungsprozess ist optional. Ganz wie bei kostenlosen Visuals liegt es im Ermessen des Entwicklers, ob seine benutzerdefinierten IAP-Visuals zertifiziert werden sollen oder nicht.

### <a name="what-is-changing-in-the-submission-process"></a>Was ändert sich am Übermittlungsvorgang?

Der Übermittlungsvorgang von benutzerdefinierten IAP-Visuals an den Marketplace ist der gleiche wie bei kostenlosen Visuals. Er erfolgt über das Dashboard des Verkäufers.  Die einzige Änderung am Übermittlungsvorgang besteht darin, dass Entwickler in den Entwicklerkommentaren im Verkäuferdashboard folgende Angabe machen müssen: „Visual mit In-App-Kauf“. Außerdem müssen Sie ggf. einen Lizenzschlüssel/ein Token bereitstellen, um die kostenpflichtigen/erweiterten Funktionen zu validieren.  

Es wird keine neue Option *kostenlos mit In-App-Kauf* im Verkäuferdashboard geben, Sie müssen Ihre IAP-Visuals als *kostenlos* einreichen.

Teilen Sie den Benutzern darüber hinaus mit, was sie erwartet, indem Sie in der ausführlichen Beschreibung im Store angeben, welche Features kostenlos sind und welche zusätzlich erworben werden müssen.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>Was sollte ich vor dem Einreichen meines benutzerdefinierten IAP-Visuals unternehmen?

Wenn Sie an einem benutzerdefinierten IAP-Visual arbeiten oder bereits eins entwickelt haben, achten Sie darauf, dass es den Richtlinien entspricht.  

Wenn Sie im benutzerdefinierten Visual ein Logo verwenden, achten Sie darauf, dass es den Logorichtlinien genügt (Farbe, Platzierung, Größe und Aktionsauslösung).

In den Richtlinien finden Sie außerdem Hinweise zu bewährten Methoden.  
> [!Note]
> Alle kostenlosen Visuals sollten dieselben kostenlosen Features beibehalten, die zuvor angeboten wurden. Sie können kostenpflichtige, optionale erweiterte Features auf Grundlage der alten Features hinzufügen. Es wird empfohlen, die IAP-Visuals mit den erweiterten Features als neue Visuals zu veröffentlichen, anstatt die alten, kostenlosen Features zu aktualisieren.

### <a name="can-i-get-my-iap-custom-visual-certified"></a>Kann ich mein benutzerdefiniertes IAP-Visual zertifizieren lassen?

Ja, genau so wie kostenlose Visuals.  Sobald Ihr benutzerdefiniertes IAP-Visual vom AppSource-Team genehmigt wurde, können Sie es für den Zertifizierungsprozess einreichen.

Damit Ihr Visual zertifiziert werden kann, muss es die Zertifizierungsanforderungen erfüllen; beispielsweise darf das Visual nicht zur Lizenzüberprüfung auf externe Dienste zugreifen.

Bedenken Sie, dass die Zertifizierung ein optionaler Vorgang ist, es liegt bei Ihnen, ob Sie Ihr IAP-Visual zertifizieren lassen möchten.

## <a name="additional-questions"></a>Weitere Fragen

### <a name="how-to-get-support"></a>Wie erhalte ich Support?

Zögern Sie nicht, sich mit Fragen, Kommentaren oder Problemen an das Supportteam für benutzerdefinierte Visuals zu wenden: *pbicvsupport@microsoft.com*  .  

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie auf der Seite [Troubleshoot Power BI custom visuals (Problembehandlung für benutzerdefinierte Power BI-Visuals)](power-bi-custom-visuals-troubleshoot.md).
