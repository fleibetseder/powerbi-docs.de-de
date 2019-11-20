---
title: Herstellen einer Verbindung mit Datasets im Power BI-Dienst über Power BI Desktop
description: Verwenden eines gemeinsamen Datasets für mehrere Power BI Desktop-Berichte in mehreren Arbeitsbereichen und Verwalten des Berichtslebenszyklus
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d7d48b78ecced3e26a52df12bc8850ab8fed4c1e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877893"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Herstellen einer Verbindung mit Datasets im Power BI-Dienst über Power BI Desktop
Sie können eine Liveverbindung mit einem gemeinsam genutzten Dataset im Power BI-Dienst herstellen und auf Grundlage des gleichen Datasets viele verschiedene Berichte erstellen. Das bedeutet, dass Sie in Power BI Desktop Ihr perfektes Datenmodell erstellen und im Power BI-Dienst veröffentlichen können. Dann können Sie und andere Benutzer aus diesem einen, gemeinsam verwendeten Datenmodell mehrere unterschiedliche Berichte (als separate PBIX-Dateien) erstellen und in unterschiedlichen Arbeitsbereichen speichern. Das Feature heißt **Liveverbindung mit Power BI-Dienst**.

![Daten aus dem Power BI-Dienst abrufen](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

Dieser Artikel geht auf die zahlreichen Vorteile des Features sowie auf bewährte Methoden ein. Es sind allerdings auch ein paar Punkte und Einschränkungen zu berücksichtigen. Diese finden Sie am Ende des Artikels.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Verwenden einer Liveverbindung mit dem Power BI-Dienst für die Verwaltung des Berichtslebenszyklus
Eine der Herausforderungen im Zusammenhang mit der Beliebtheit von Power BI liegt in der Verbreitung von Berichten, Dashboards und den jeweils zugrunde liegenden Datenmodellen. Der Grund: Sie können ganz einfach eindrucksvolle Berichte in **Power BI Desktop** erstellen, im **Power BI-Dienst** freigeben ([veröffentlichen](desktop-upload-desktop-files.md)) und anschließend auf der Grundlage dieser Datasets erstklassige Dashboards erstellen. Da diese Vorgehensweise von so vielen genutzt wird und dabei häufig die gleichen (oder zumindest sehr ähnliche) Datasets verwendet werden, lässt sich nicht mehr so einfach nachvollziehen, welcher Bericht denn nun auf welchem Dataset basiert – und wie aktuell das jeweilige Dataset ist. Das Feature **Liveverbindung mit Power BI-Dienst** ist die Antwort auf dieses Problem und macht das Erstellen, Freigeben und Erweitern von Berichten und Dashboards mit einem gemeinsamen Dataset einfacher und konsistenter.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Erstellen und Freigeben eines von allen nutzbaren Datasets
Ein Beispiel: Anna ist Business Analyst in Ihrem Team und hat die entsprechenden Kenntnisse, um sehr gute Datenmodelle (häufig als Datasets bezeichnet) zu erstellen. Dank ihres Know-hows kann Anna ein Dataset und einen Bericht erstellen und diesen Bericht anschließend über den **Power BI-Dienst** freigeben.

![Veröffentlichen im Power BI-Dienst](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Alle sind von Annas Bericht und Dataset begeistert – und genau da beginnen die Probleme: Jeder in Annas Team versucht, eine *eigene Version* dieses Datasets zu erstellen und anschließend seine eigenen Berichte für das Team freizugeben. Plötzlich enthält der Arbeitsbereich Ihres Teams im **Power BI-Dienst** zahlreiche verschiedene Berichte, die jeweils auf unterschiedlichen Datasets basieren. Welches davon ist auf dem neuesten Stand? Waren die Datasets identisch, oder doch nur annähernd gleich? Wo lagen die Unterschiede? Mit dem Feature **Liveverbindung mit Power BI-Dienst** lässt sich all das vermeiden. Im nächsten Abschnitt erfahren Sie, wie andere Benutzer das von Anna veröffentlichte Dataset für ihre eigenen Berichte in Ihren eigenen Arbeitsbereichen verwenden können und wie Sie es allen Benutzern ermöglichen, ihre individuellen Berichte auf der Grundlage des gleichen fundierten, geprüften und veröffentlichten Datasets zu erstellen.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Herstellen einer Liveverbindung mit einem Dataset des Power BI-Diensts
Anna erstellt einen Bericht (und das zugrunde liegende Dataset) und veröffentlicht diesen dann im **Power BI-Dienst**, woraufhin er dort im Power BI-Dienst-Arbeitsbereich ihres Teams angezeigt wird. Wenn Anna den Bericht in einem *neuen Arbeitsbereich* speichert, kann sie die Berechtigung „Erstellen“ festlegen, um den Bericht für jeden Benutzer innerhalb und außerhalb ihres Arbeitsbereichs verfügbar und nutzbar zu machen.

Weitere Informationen zu den neuen Arbeitsbereichen finden Sie unter [Arbeitsbereiche](service-new-workspaces.md).

Andere Benutzer innerhalb und außerhalb des Arbeitsbereichs von Anna können nun mithilfe des Features **Liveverbindung mit Power BI-Dienst** eine Liveverbindung mit dem von Anna freigegebenen Datenmodell herstellen und eigene Berichte auf der Grundlage von *Annas ursprünglichem Dataset* in *ihren eigenen neuen Arbeitsbereichen* erstellen.

In der folgenden Abbildung sehen Sie, wie Anna einen **Power BI Desktop-Bericht** erstellt und ihn (einschließlich seines Datenmodells) für den **Power BI-Dienst** veröffentlicht. Daraufhin können andere Benutzer mithilfe des Features **Liveverbindung mit Power BI-Dienst** eine Verbindung mit Annas Datenmodell herstellen und eigene Berichte in ihren eigenen Arbeitsbereichen auf der Grundlage von Annas Dataset erstellen.

![Mehrere Berichte auf Grundlage eines Datasets](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Wenn Sie Ihr Dataset in einem [klassischen freigegebenen Arbeitsbereich](service-create-workspaces.md) speichern, können nur Mitglieder dieses Arbeitsbereichs Berichte basierend auf Ihrem Dataset erstellen. Wenn Sie eine Liveverbindung mit dem Power BI-Dienst herstellen möchten, muss sich das Dataset, mit dem Sie die Verbindung herstellen, in einem gemeinsam genutzten Arbeitsbereich befinden, dem Sie selbst angehören.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Schritt-für-Schritt-Anleitung zum Verwenden der Liveverbindung mit dem Power BI-Dienst
Nachdem Sie nun wissen, wie praktisch das Feature **Liveverbindung mit Power BI-Dienst** ist und wie Sie es als Best Practice für die Verwaltung des Berichtslebenszyklus verwenden können, erfahren Sie als Nächstes, welche Schritte erforderlich sind, um von Annas Bericht (und Dataset) zu einem freigegebenen Dataset zu gelangen, das von ihren Teamkollegen in ihrem Power BI-Arbeitsbereich verwendet werden kann.

### <a name="publish-a-power-bi-report-and-dataset"></a>Veröffentlichen eines Power BI-Berichts und eines Datasets
Für die Berichtslebenszyklusverwaltung mithilfe des Features **Liveverbindung mit Power BI-Dienst** wird zunächst ein für die Teamkollegen interessanter Bericht (und ein Dataset) benötigt. Anna muss den Bericht also zunächst aus **Power BI Desktop** **veröffentlichen**. Dazu wählt Anna in Power BI Desktop auf dem Menüband **Home** die Option **Veröffentlichen** aus.

![Veröffentlichen eines Berichts](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Ist Anna nicht bei dem Power BI-Dienst-Konto angemeldet, wird sie in einem Popupfenster dazu aufgefordert, sich anzumelden.

![Anmelden bei Power BI Desktop](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

Hier kann Anna den gewünschten Zielarbeitsbereich für die Veröffentlichung des Berichts und des Datasets auswählen. Denken Sie daran: Wenn Anna das Dataset in einem neuen Arbeitsbereich speichert, kann jeder mit Berechtigung zum Erstellen auf das Dataset zugreifen. Erstellberechtigungen werden im Power BI-Dienst nach der Veröffentlichung festgelegt. Wird Arbeit in einem klassischen Arbeitsbereich gespeichert, können nur Mitglieder mit Zugriff auf den Arbeitsbereich, in dem ein Bericht veröffentlicht wird, über das Feature **Liveverbindung mit Power BI-Dienst** auf das entsprechende Dataset zugreifen.

![Veröffentlichen im Power BI-Dienst](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

Der Veröffentlichungsprozess beginnt und kann in **Power BI Desktop** nachverfolgt werden.

![Veröffentlichungsfortschritt](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Nach Abschluss des Vorgangs werden in **Power BI Desktop** eine Erfolgsmeldung, einige Links zum eigentlichen Bericht im **Power BI-Dienst** sowie ein Link zu **Schnelleinblicken** für den Bericht angezeigt.

![Erfolgreiche Veröffentlichung](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Nachdem der Bericht mit seinem Dataset nun im Power BI-Dienst veröffentlicht wurde, können Sie ihn *bewerben*, um seine Qualität und Zuverlässigkeit zu bestätigen. Sie können zudem anfordern, dass er von zentralen Zertifizierungsstellen in Ihrem Power BI-Mandanten *zertifiziert* wird. Durch diese Empfehlungen wird Ihr Dataset immer oben in der Liste angezeigt, wenn Benutzer nach Datasets suchen. Weitere Informationen zu diesem Prozess finden Sie im Artikel zum [Bewerben Ihres Datasets](service-datasets-promote.md). 

Als letzten Schritt müssen Sie *Erstellberechtigungen* für das Dataset festlegen, auf dem der Bericht basiert. Erstellberechtigungen legen fest, wer Ihr Dataset sehen und verwenden darf. Sie können die Berechtigungen entweder direkt im Arbeitsbereich oder beim Freigeben einer App im Arbeitsbereich festlegen. Weitere Informationen finden Sie im Artikel zum [Erstellen und Freigeben von Datasets](service-datasets-build-permissions.md) im Abschnitt zur Erstellberechtigung.

Als Nächstes erfahren Sie, wie Teamkollegen mit Zugriff auf den Arbeitsbereich, in dem der Bericht und das Dataset veröffentlichten wurden, eine Verbindung mit dem Dataset herstellen und eigene Berichte erstellen können.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Herstellen einer Liveverbindung zwischen dem Power BI-Dienst und dem veröffentlichten Dataset
Wählen Sie in **Power BI Desktop** auf dem Menüband **Start** die Option **Daten abrufen** und anschließend im linken Bereich **Power BI** und **Power BI-Datasets** aus, um eine Verbindung mit dem veröffentlichten Bericht herzustellen und einen eigenen Bericht auf der Grundlage des veröffentlichten Datasets zu erstellen.

Falls Sie noch nicht bei Power BI angemeldet sind, erscheint eine Anmeldeaufforderung. In dem Fenster, das nach der Anmeldung angezeigt wird, sehen Sie die Arbeitsbereiche, denen Sie angehören. Hier können Sie den Arbeitsbereich mit dem Dataset auswählen, mit dem Sie eine **Liveverbindung mit dem Power BI-Dienst** herstellen möchten.

Die Datasets in der Liste sind alles freigegebene Datasets aller Arbeitsbereiche, für die Sie über Erstellberechtigungen verfügen. Sie können nach einem bestimmten Dataset suchen und dessen Namen, Besitzer und den entsprechenden Arbeitsbereich sowie die letzte Aktualisierung anzeigen. Außerdem werden *empfohlene* Datasets oben in der Liste angezeigt, die entweder zertifiziert oder beworben wurden. 

![Liste verfügbarer Datasets](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

Wenn Sie in dem Fenster die Option **Laden** auswählen, wird eine Liveverbindung mit dem ausgewählten Dataset hergestellt. Das bedeutet, dass die angezeigten Daten (also die Felder und ihre Werte) in Echtzeit in **Power BI Desktop** geladen werden.

![Datasetfelder im Bereich „Felder“](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

Nun können Sie (und andere) auf der Grundlage des gleichen Datasets benutzerdefinierte Berichte erstellen und freigeben. Dadurch kann ein einzelner kompetenter Benutzer (wie Anna aus unserem Beispiel) ein wohlgeformtes Dataset erstellen und zahlreichen Teamkollegen die Verwendung des freigegebenen Datasets ermöglichen, damit diese ihre eigenen Berichte erstellen können.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen
Beim Verwenden des Features **Liveverbindung mit Power BI-Dienst** sind einige Einschränkungen und Überlegungen zu berücksichtigen.

* Nur Benutzer mit Erstellberechtigungen für ein Dataset können mithilfe des Features **Liveverbindung mit Power BI-Dienst** eine Verbindung mit einem veröffentlichten Dataset herstellen. 
* Benutzer der kostenlosen Version sehen nur Datasets aus „Mein Arbeitsbereich“ und aus Premium-Arbeitsbereichen.
* Da es sich hierbei um eine Liveverbindung handelt, sind die Navigation nach links sowie die Modellierung deaktiviert, ähnlich dem Verhalten bei einer Verbindung mit **SQL Server Analysis Services**, und Sie können nur eine Verbindung mit einem Dataset in jedem Bericht herstellen.
* Da es sich hierbei um eine Liveverbindung handelt, werden RLS (Row- and Role-Level Security; Sicherheit auf Zeilen- und Rollenebene) und weitere solcher Verbindungsmerkmale erzwungen – genau wie bei einer Verbindung mit **SQL Server Analysis Services**.
* Wenn der Besitzer die freigegebene PBIX-Originaldatei ändert, werden das Dataset und der im **Power BI-Dienst** freigegebene Bericht überschrieben. Berichte, die auf diesem Dataset basieren, werden nicht überschrieben. Änderungen des Datasets werden jedoch im Bericht widergespiegelt.
* Die Mitglieder eines Arbeitsbereichs können den ursprünglich freigegebenen Bericht nicht ersetzen. Wenn Sie es dennoch versuchen, wird eine Warnung angezeigt, in der Sie zum Umbenennen der Datei und Veröffentlichen des Berichts aufgefordert werden.
* Wenn Sie das freigegebene Dataset im **Power BI-Dienst** löschen, funktionieren andere Berichte, die darauf basieren, nicht mehr ordnungsgemäß oder zeigen keine Visuals mehr an.
* Bei Verwendung von Inhaltspaketen müssen Sie zunächst eine Kopie des Inhaltspakets erstellen, bevor Sie es als Grundlage für die Freigabe eines PBIX-Berichts und Datasets für den **Power BI-Dienst** verwenden.
* Wenn Inhaltspakete aus *Meine Organisation* kopiert wurden, können Sie den im Dienst erstellten Bericht und/oder einen Bericht, der beim Kopieren eines Inhaltspakets mit einer Liveverbindung erstellt wurde, nicht ersetzen. Wenn Sie es dennoch versuchen, wird eine Warnung angezeigt, in der Sie zum Umbenennen der Datei und Veröffentlichen des Berichts aufgefordert werden. In diesem Fall können Sie nur veröffentlichte Berichte mit Liveverbindung ersetzen.
* Nach dem Löschen eines freigegebenen Datasets im **Power BI-Dienst** kann niemand mehr über **Power BI Desktop** auf dieses Dataset zugreifen.
* Berichte, die ein Dataset im Power BI-Dienst freigeben, unterstützen keine automatisierten Bereitstellungen mithilfe der REST-API von Power BI.

