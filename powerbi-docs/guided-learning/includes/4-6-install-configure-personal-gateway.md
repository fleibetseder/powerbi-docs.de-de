---
ms.openlocfilehash: ea958349988cade1045e80b073254ab1f29bbe9e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61263412"
---
In vorherigen Themen wurde erläutert, wie Sie mithilfe von Power BI Datenquellen verbinden können und wie Sie Ihre Datasets im Power BI-Dienst manuell aktualisieren. Da Sie aber vermutlich nicht bei jeder Änderung der Daten eine manuelle Aktualisierung durchführen möchten, können Sie Power BI verwenden, um eine geplante Aktualisierung einzurichten. Diese wird mit den Datenquellen verbunden, die dann automatisch im Power BI-Dienst veröffentlicht werden. Dies gibt Ihnen außerdem die Möglichkeit, den Dienst mit lokalen Datenquellen zu verbinden, einschließlich Excel-Dateien, Access-Datenbanken, SQL-Datenbanken und mehr.

Das System, das es Ihnen ermöglicht, lokale Datenquellen mit dem Power BI-Dienst zu verbinden, wird als **Datengateway** bezeichnet. Dabei handelt es sich um eine kleine Anwendung, die auf Ihrem Computer ausgeführt wird und die einen vordefinierten Zeitplan verwendet, um eine Verbindung mit Ihren Daten herzustellen und um Updates abzurufen und an den Power BI-Dienst zu übertragen. **Personal Gateway** ist eine Version von **Datengateway**, die ohne Administratorkonfiguration verwendet werden kann.

>[!NOTE]
>Der Computer mit Power BI Personal Gateway *muss* mit dem Internet verbunden sein, damit **Personal Gateway** ordnungsgemäß funktioniert.
> 

Melden Sie sich zum Einrichten von **Personal Gateway** zunächst beim Power BI-Dienst an. Wählen Sie das Symbol **Herunterladen** in der oberen rechten Ecke des Bildschirms und dann im Menü die Option **Datengateways** aus.

![](media/4-6-install-configure-personal-gateway/4-6_1b.png)

Von dort aus gelangen Sie zu einer Webseite, auf der Sie **Power BI Gateway - Personal** auswählen können, wie unten dargestellt.

![](media/4-6-install-configure-personal-gateway/4-6_2b.png)

Führen Sie die Anwendung aus, sobald der Download abgeschlossen ist, und folgen Sie dem Installations-Assistenten.

![](media/4-6-install-configure-personal-gateway/4-6_3a.png)

Sie werden dann aufgefordert, den Assistenten zum Einrichten des Gateways zu starten.

![](media/4-6-install-configure-personal-gateway/4-6_3b.png)

Sie werden aufgefordert, sich zunächst bei Ihrem Power BI-Dienstkonto und danach beim Windows-Konto des Computers anzumelden, da der Gatewaydienst unter Ihrem Konto ausgeführt wird.

![](media/4-6-install-configure-personal-gateway/4-6_3c.png)

Kehren Sie zum Power BI-Dienst zurück. Wählen Sie das Menü mit den drei Auslassungspunkten neben dem Dataset aus, das aktualisiert werden soll, und wählen Sie dann **Zeitplanaktualisierung** aus. Daraufhin wird die Seite **Aktualisierungseinstellungen** geöffnet. Power BI erkennt, dass Sie **Personal Gateway** installiert haben, und zeigt den entsprechenden Status an.

Wählen Sie neben jeder gewünschten Datenquelle **Anmeldeinformationen bearbeiten** aus, und richten Sie die Authentifizierung ein.

![](media/4-6-install-configure-personal-gateway/4-6_6.png)

Legen Sie schließlich die Optionen unter **Zeitplanaktualisierung** fest, um automatische Updates zu aktivieren und festzulegen, wann und wie häufig diese durchgeführt werden sollen.

![](media/4-6-install-configure-personal-gateway/4-6_7.png)

Und das ist auch schon alles. Zum festgelegten Zeitpunkt ruft Power BI diese Datenquellen unter Verwendung der angegebenen Anmeldeinformationen und der Verbindung mit dem Computer mit **Personal Gateway** ab und aktualisiert die Berichte und Datasets gemäß dem Zeitplan. Wenn Sie Power BI das nächste Mal öffnen, spiegeln diese Dashboards, Berichte und Datasets die Daten der letzten geplanten Aktualisierung wider.

## <a name="next-steps"></a>Nächste Schritte
**Herzlichen Glückwunsch!** Sie haben diesen Abschnitt **Durchsuchen von Daten** im Kurs **Geführtes Lernen** für Power BI abgeschlossen. Der Power BI-Dienst bietet viele interessante Möglichkeiten, um Daten zu durchsuchen, Erkenntnisse zu teilen und mit visuellen Elementen zu interagieren. Den Zugang zu allen diesen Funktionen erhalten Sie über einen Browser und über einen Dienst, zu dem Sie unabhängig von Ihrem Standort eine Verbindung herstellen können.

Ein leistungsstarker und bekannter Partner von Power BI ist **Excel**. Power BI und Excel sind hervorragend aufeinander abgestimmt. Ihre Arbeitsmappen können Sie nahtlos und ganz einfach in Power BI integrieren.

![](media/4-6-install-configure-personal-gateway/5-1_1.png)

Wie einfach? Das erfahren Sie im nächsten Abschnitt, **Power BI und Excel**.

Wir sehen uns im nächsten Abschnitt!

