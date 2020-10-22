---
description: "Elektronische Stellwerke - Systemarchitektur & Zuverlässigkeit"
date: 2020-10-22T23:15:27+02:00
draft: false
katex: true
images: ["https://images.unsplash.com/photo-1582457494068-b850b2e126e5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3150&q=80"]
markup: "pandoc"
author: "Felix Klement"
tags:
  - Eisenbahnsicherungstechnik
  - Elektronische Stellwerke
  - Systemarchitektur
  - Zuverlässigkeit
---

![“Réserve Naturelle Nationale des Marais de Bruges, Bruges, France” by [Philippe Oursel](https://unsplash.com/@ourselp?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)](https://images.unsplash.com/photo-1582457494068-b850b2e126e5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3150&q=80)*“Réserve Naturelle Nationale des Marais de Bruges, Bruges, France” by [Philippe Oursel](https://unsplash.com/@ourselp?utm_source=medium&utm_medium=referral)*

This work was done in the seminar "Eisenbahnsicherungstechnik" from Prof. Dr. Katzenbeisser in SS2020 at the University of Passau. It was written in collaboration with Chris Weibel, Alexander Wittmann and Felix Klement. Currently the version is only available in German. A PDF of the article can be found below the text.

Abstract
============
Für Bahnbetreiber ist die Entwicklung elektronischer Stellwerke oft ein
sehr aufwändiges Unterfangen. Um für die Zukunft des Schienenverkehrs
sowie möglichem Wachstum in der Branche gewappnet zu sein, müssen die
System-Komponenten günstiger werden. Auch die Methodiken für den Betrieb
sowie die Wartung müssen besser und effizienter gestaltet werden, ohne
Einbußen im Bereich der Sicherheit sowie Ausfallsicherheit zu haben.
Daher ist es wichtig ein genaues Bild von Möglichkeiten zu erlangen, um
die aufgezeigten Problematiken zu beseitigen. In diesem Papier
beleuchten wir deshalb die Geschichte der ersten elektronischen
Stellwerke, erläutern den Aufbau sowie die Funktionsweise der
Systemarchitektur und beschreiben wie Redundanz in elektronischen
Stellwerken umgesetzt wird. Zum Schluss beleuchten wir noch die Zukunft
der Stellwerke im Allgemeinen.


Einleitung
==========

Die Eisenbahn als Transportmittel hat sich bereits Anfang des 19.
Jahrhunderts etabliert. Ganz zu Beginn wurden Pferde als Antriebsmittel
genutzt, doch dies änderte sich rapide, als 1804 Richard Trevithick die
erste Dampflokomotive in Betrieb nahm. Im Laufe der Zeit haben sich die
Zugmaschinen und die zugehörige Anlagen immer mehr weiterentwickelt als
auch das Schienennetz mehr und mehr ausgebaut wurde. Die Gesamtlänge für
das weltweite Schienennetz betrug im Jahr 2013 ungefähr 1.148.186
Kilometer @Factbook. Um den immensen Güter- und Personenverkehr tragen
zu können und um konkurrenzfähig zu bleiben, muss die Bahn immer
bessere, ausgeklügeltere und effizientere Anlagen entwickeln. Damit es
möglich ist mit mehreren Zügen auf dem gleichen Gleis zu fahren, muss
ein Zug wissen, ob der kommende Abschnitt der Strecke belegt ist, sowie
die Möglichkeit haben das Gleis zu wechseln. Die ersten mechanischen
Stellwerke für die Fahrtkontrolle wurden noch per Hand bedient. Mit dem
fortschreitenden Ausbau von elektrischen Leitungen Anfang des 19.
Jahrhunderts war es nun möglich die Stellwerke mit Hilfe von Motoren zu
bewegen und es sind die ersten elektromechanischen Stellwerke
entstanden. In den 1930er wiederum wurden dann die ersten
Relaisstellwerke eingeführt. Diese hatten den Vorteil dass sämtliche
Abhängigkeiten mit Relaisschaltungen realisiert werden konnten. Durch
die voranschreitende Modernisierung wurden in den 1980er Jahren die
ersten Computer gesteuerten Stellwerke, elektronische Stellwerke (ESTW),
erforscht. Im Folgenden werden die relevantesten ersten elektronischen
Stellwerke dargestellt und auf die Systemarchitektur sowie die
Zuverlässigkeit dieser eingegangen. Danach wird im letzten Kapitel ein
kurzer Ausblick auf neuartige Stellwerke gegeben.

Die ersten elektronischen Stellwerke
====================================

In den 1980er Jahren wurden europaweit viele unterschiedliche ESTW
realisiert und im Laufe der Jahrzehnte in das Schienennetz integriert.
Im Folgenden sind die wichtigsten ESTW, welche in dieser Zeit im
deutschsprachigen Raum (Deutschland/Österreich) entstanden sind,
aufgeführt.

Simis-C/ESTW EI S
-----------------

Bei Simis-C handelt es sich um das erste elektronische Stellwerk von
Siemens, welches für die Deutsche Bahn AG entwickelt wurde. Dieses
Stellwerk ist auch unter den Namen *EI S* (Elektronisches Stellwerk der
Bauform Siemens) bekannt, wurde aber intern mit *ESTW SIMIS-C*
bezeichnet. Hierbei steht *Simis* für ein sicheres Mikrocomputersystem
von Siemens.

Diese Stellwerke wurden als erstes im Jahr 1985 auf der Strecke München
- Garmisch-Partenkirchen umfassend erprobt. Hierbei wurde der Betrieb
ein Jahr lang gleichzeitig mit Signaltechnick sowie mit Simis-C
betrieben. Nach dem Ausmerzen anfänglicher Mängel, sowie dem nötigen
Sicherheitsnachweis, wurde Simis-C im Jahr 1988 in den Regelbetrieb
aufgenommen. Diese Art von Stellwerk wurde nicht nur innerhalb von
Deutschland eingesetzt, sondern auch in Österreich, der Schweiz, den
Niederlanden sowie in Finnland.

Simis-C Stellwerke werden mit einem von Siemens selbst entwickelten
Rechner betrieben. Hierbei gibt es die 2v2 und 2v3 Variante. Der
Datenaustausch erfolgte mit normierten Telegrammen. Bei Simis-C wurde
auf die Sichtgerät-Doppelsteuerung (SIDOS) verzichtet und wird
stattdessen von einem Lupenbildmonitor vom Bedienplatzrechner aus
gesteuert. Um die eingegebenen Befehle zu bestätigen, muss der
Bedienende die Kommandofreigabe-Taste bestätigen.@Ulrich

ESTW L90
--------

Hierbei handelt es sich um ein elektronisches Stellwerk von ALCATEL SEL,
welches auf der Spezifikationen der Deutschen Bahn AG beruht. Dieses
Stellwerk wurde zeitgleich zu Simis-C entwickelt. Die ersten Tests
erfolgten im Jahr 1989 und im Jahr 1992 wurde es auf der Neubaustrecke
Madrid - Sevilla in Spanien zum ersten mal eingesetzt. Auch heutzutage
werden diese Stellwerke in Deutschland, Spanien, Frankreich, Rumänien
und weiteren Ländern noch immer eingesetzt.

Auch dieses Stellwerk läuft auf dem Simis-Prinzip, da Siemens und
ALCATEL SEL diese gemeinsam in Deutschland entwickelt haben. Im
Gegensatz zu Simis-C, wurde in diesem Stellwerk eine abgewandelte 2v3
Variante verbaut. Dabei wechseln sich zwei Rechner zyklisch mit der
Ausgabe der Daten ab. Auf den dritten Rechner wird dann im Störfall
umgeschaltet. Dies funktioniert ohne Unterbrechung. Die verwendeten
Rechner sind hier handelsübliche Computer, im Gegensatz zu den extra
gebauten Rechnern für Simis-C. Für die interne Datenübertragung werden
entweder Einzel- oder Doppeltelegramme verwendet. Die Anzeige, sowie die
Kommandofreigabe-Taste sind identisch zu Simis-C.@Ulrich

ELEKTRA
-------

ELEKTRA ist ein Stellwerk welches die österreichische Bundesbahn bei der
Alcatel Austria AG in Auftrag gab. Hierbei wurde Alcatel größtmögliche
Freiheit in der Entwicklung gelassen. Dadurch konnten diese ihre bereits
bestehenden Basistechnologien von öffentlichen sowie privaten
Kommunikationssystemen übernehmen. Die Entwicklung dieser Stellwerke
fand zeitgleich zu Simis-C und ESTW L90 statt und ging im Jahre 1989 in
Österreich in den Betrieb.

Es bestehen Ähnlichkeiten zum ESTW L90, wie etwa die Verwendung
handelsüblicher Rechner oder auch die Art der internen Kommunikation.
Der Hintergrund dafür ist, dass die verantwortlichen Firmenteile von
ALCATEL ihre Ursprünge in der Kommunikationsbranche haben.

Während bei Simis-C und ESTW L90 auf Hardwareredundanz mit mehreren
Rechnern gesetzt wird, wird hier Redundanz auf Softwareebene realisiert.
Dabei hat das System einen Logikkanal und einen Sicherheitskanal (Saftey
Bag). Die eingegeben Befehle werden zuerst im Logikkanal auf die
Richtigkeit überprüft und dann für die Anzeige vorbereitet. Vorher aber
wird überprüft, ob das Ergebnis zu einem gefährlichen Zustand führen
kann oder nicht (Saftey Bag Verfahren). Sind beide Überprüfungen in
Ordnung, wird das Kommando ausgeführt.

Da bei Software nie davon ausgegangen werden kann, dass diese fehlerfrei
umgesetzt worden ist, wurden zwei verschiedene Programmiersprachen für
die beiden Känale verwendet. Im Logikkanal ist die Programmiersprache
CHILL verwendet worden und im Sicherheitskanal die regelorientierte
Sprache PAMELA. Da beide Teilbereiche unabhängig voneinander
programmiert wurden sind gemeinsame Fehler unwahrscheinlicher und das
System somit sicherer.

Damit ELEKTRA gegen Hardwareversagen abgesichert ist wurde das VOTRICS
(Voting Triple Modular Redundant Computing System) realisiert. Hierbei
wird ein 2v3 Vergleich von Rechenergebnissen mit 3 Rechnern vollzogen.
Dadurch ist es möglich einen defekten Rechner zu erkennen und die
Fehlertoleranz wird erhöht. Möglich ist aber auch eine 2v2 Variante.
Hierbei gibt es zusätzliche Entscheidungsparameter, mit denen sich ein
Rechner zuerst selber prüfen kann.@Ulrich

Systemarchitektur
=================

Um die Architektur des Systems besser zu verstehen, zeigen wir kurz zu
Beginn die Hierarchie des Gesamtsystems auf (siehe Abbildung
[fig:gesamtsystem]). In Zukunft wird das gesamte Netz der DB AG aus
sieben Betriebszentralen (BZ) am Ort der Niederlassungen gesteuert und
überwacht. Um den vollen Nutzen der Betriebszentralen zu erlangen,
werden die Stellwerke technisch an die BZ angebunden. Somit können sie
direkt das Betriebsgeschehen beeinflussen (ohne Umwege wie z.B. über das
Telefon) @DBAG. Daraus ergibt sich ein lückenloses, hierarchisches
Gesamtsystem von der Disposition bis zu den Elementen der Außenanlage.

![Hierarchie des Gesamtsystems @Mura](/misc/gesamtsystem.pdf "fig:")
[fig:gesamtsystem]

Die Systemarchitektur elektronischer Stellwerke wird in drei Ebenen
unterteilt. In Abbildung [fig:systemarchitektur] findet sich eine
vereinfachte bzw. verallgemeinerte Systemarchitektur eines
elektronischen Stellwerks.

Die erste dieser Ebenen ist das Segment für externe Geräte, in dieser
befindet sich der Leitstand. Hier wird auch der aktuelle Zustand des
jeweiligen Streckenbereichs beobachtet und gegebenenfalls anfallende
Änderungen durchgeführt. Sämtliche Aktionen werden in dieser Ebene von
einem/einer Fahrdienstleiter/in an einem der Bedienplätze ausgeführt.
Die Bedienplätze interagieren über ein Bediensystem mit der gesamten
Anlage. Dadurch haben alle Plätze kontinuierlich die gleiche Sicht auf
die jeweiligen Gleisabschnitte. Im Falle von Notfällen, kann man durch
diese Ebene den kompletten zugehörigen Streckenabschnitt manuell
steuern.

Ebene Nummer zwei ist die Sicherungs-/ Bedienverarbeitungsebene. Die
gesamte Logik des Stellwerks wird von einem oder mehreren zentralen
Sicherheitsbausteinen dargestellt. Sämtliche in dieser Ebene verbauten
Bauteile und Komponente sind im Generellen herstellerspezifisch und
werden kommerziell vertrieben. Je nach Größe der Stellwerke müssen die
Komponenten und Bausteine sowie deren Anzahl angepasst werden. Um dem
Sicherheitslevel gerecht zu werden und eine gewisse Ausfallsicherheit zu
gewährleisten, verfügen die Sicherungskomponenten über redundante
Datenleitungen. Bei modernen Bahnanlagen werden diese Datenleitungen als
Ringleitungen gelegt. Das bedeutet, dass sie jeweils an dem
Sicherungsbaustein starten und enden. Der Vorteil hierbei ist dass falls
eine der Leitungen an einer beliebigen Stelle beschädigt wird, die
Signale durch die entgegengesetzte Richtung trotzdem noch zum Empfänger
gelangen können. Diese Art von Ausfallsicherheit kann natürlich nur
gewährleistet werden, wenn nicht mehrere Stellen der Ringleitung defekt
sind. Falls das doch der Fall ist, kann es zu unerwarteten Nebeneffekten
kommen.

Die soeben beschriebenen Datenleitungen werden meistens mit einem
Steuergeräteschrank verbunden, welcher sich auf der dritten Ebene, der
sogenannten Stellebene befindet. In den Schränken befinden sich
Konzentratoren und Objektsteuergeräte. Konzentratoren ermitteln die
Steuersignale aus den Ringleitungen und dienen somit als Schnittstelle
zwischen Sicherungs- und Stellebene. Die Objektsteuergeräte sind jeweils
einer Feldeinheit zugeordnet und somit für die Steuerung einer Weiche
oder eines Signals verantwortlich. Für sehr komplexe Streckenabschnitte
werden viele dieser Steuergeräte benötigt. Es können ungefähr 300
Objektsteuergeräte über einen zentralen Sicherheitsbaustein gesteuert
werden. Für spezifische Anwendungen, z.B. um Informationen über die
Position eines Zuges zu bekommen, können auch Achszähler (Balisen) mit
den Steuergeräten verbunden werden. Auf diese Weise können so auch
Informationen an den Sicherheitsbaustein und damit auch an den
Bedienplatz zurück gesendet werden. Um eine redundant ausgelegte
Architektur zu erlangen können die zentralen Sicherheitsbausteine
mehrfach angelegt werden. Dabei werden sämtliche Daten an alle
redundanten Bausteine geschickt. Das hat zum Vorteil, dass sich
sämtliche Reservesysteme immer im gleichen Zustand wie das operierende
System befinden. Wenn nun ein System ausfällt, kann das Rückfallsystem
ohne Verzögerung einspringen und übernehmen. Dieses System der Redundanz
wird auch heiße Redundanz genannt, da die Komponenten währen des
Normalbetriebs arbeiten. Im Falle von kalter Redundanz müsste ein
Verfahren vorhanden sein, welches das Ersatzsystem erst im Fehlerfall in
Betrieb nimmt.

Im Falle einer Weichenänderung muss ein/e Fahrdienstleiter/in am
Bedienplatz das jeweilige Element im Gleisschaltbild modifizieren. Im
darunterliegenden Bediensystem werden die Eingaben ausgewertet und
überprüft und dann anschließend an den zuständigen Sicherheitsbaustein
weitergeleitet. Bei der Überprüfung wird getestet, ob die Änderung
valide ist und systemkonform durchgeführt werden kann. Der zuständige
Baustein prüft dabei auch, ob es durch die zu ausführende Aktion zu
einer Gefährdung im laufenden Betrieb kommen kann. Falls nun eine
Änderung vom System als in Ordnung angesehen wird, so wird über die
Übertragungsschleife der zugehörige Steuergeräteschrank selektiert und
das passende Objektsteuergerät führt dann den Schaltvorgang aus. Im
Falle eines Fehlers bzw. einer Ablehnung durch den Sicherheitsbaustein
wird der/die Fahrdienstleiter/in informiert und die Aktion wird nicht
ausgeführt. Es gibt jedoch eine Möglichkeit sich über die
Sicherungsmaßnahmen des Systems hinwegzusetzen und die Änderung zu
erzwingen. Dieser Vorgang der Außerkraftsetzung der
Sicherheitskomponente führte auch zum Zugunglück in Bad Aiblingen @Wiki.
Akzeptierte Instruktionen werden dann an die passenden
Steuergeräteschranke weiter geleitet, dazu wird die Stellanweisung
kodiert und auf einer der Ringleitungen versendet. Die kodierten
Anweisungen werden dann im zuständigen Steuergeräteschrank vom
Konzentrator extrahiert. Der Konzentrator schaltet anschließend die
Stellanweisung und die notwendigen Objektsteuergeräte. Diese Geräte sind
dann mit den physikalischen Gerätschaften (Signale, Weichen, Schranken
...) am Gleis verbunden. Interessant hierbei ist, dass die
Objektsteuergeräte nicht zusätzlich gegen mögliche Ausfälle abgesichert
sind. Wenn nun eines der Geräte ausfällt, muss der komplette Abschnitt
und sämtliche davon abhängige Bereiche gesperrt werden, bis der Fehler
behoben wurde.

In aktuellen Anlagen ist es möglich, dass Stellwerke Informationen
austauschen können. Hierzu ist es notwendig, dass diese Kommunikation
gesichert abläuft und ein Empfangen der Nachrichten sichergestellt
werden kann @Hinrichs.

![Systemarchitektur eines elektronischen
Stellwerks](/misc/systemarchitektur.pdf "fig:") [fig:systemarchitektur]

Zuverlässigkeit
===============

Wie auch bei mechanischen Stellwerken trifft die Zuverlässigkeit des
Systems eine hohe Wichtigkeit, da im Falle einer Störung oder eines
Fehlers Personen und somit Leben bedroht sind. Für die Gewährleistung
der Zuverlässigkeit werden Maßnahmen in verschiedenen Bereichen
getroffen. Die Anwendungsbereiche lassen sich grob unterteilen in
Datenverarbeitung, Datenübertragung und Bedienung.

Datenverarbeitung
-----------------

Zur Datenverarbeitung zählen alle Prozesse, die eine Berechnung unter
Rücksichtnahme von Eingabewerten durchführen und das daraus
resultierende Ergebnis als Ausgabewert zurückliefern. Die
Zuverlässigkeit solcher Berechnungen kann durch Redundanz erhöht werden.
Diese Redundanz wird erreicht indem mehrere identische Rechner
zeitgleich die selbe Software ausführen und anschließend deren
Ausgabewerte verglichen werden.
Das *ESTW SIMIS-C* und weitere Rechnersysteme, die nach dem
*SIMIS*-Prinzip konfiguriert sind, nutzen mindestens zwei (2v2)
voneinander unabhängige, baugleiche, taktsynchron arbeitende und
identisch programmierte Mikrocomputer (siehe Abbildung[fig:2v2]). Die
Eingabewerte erreichen alle beteiligten Rechner, welche diese unabhängig
verarbeiten. Ein Hardware-Vergleicher liest den Speicher der jeweiligen
Rechner aus und sichert somit die Übereinstimmung der Eingabewerte und
Ergebnisse. Nur wenn die Mehrheit der Rechner ein übereinstimmendes
Ergebnis vorweist werden diese ausgegeben.
Bei *ESTW L90* wird die Redundanz innerhalb des Sicherheitsbausteins
*SELMIS* umgesetzt. Hier wird vorrangig die 2v3 Konfiguration (siehe
Abbildung[fig:2v3]) eingesetzt bei der zwei der drei Rechner abwechselnd
Daten ausgeben und der dritte Rechner ebenfalls das Programm durchläuft,
aber keine Ausgabe tätigt. Bei einem Ausfall einer der ersten beiden
Rechnern wird automatisch auf den dritten umgeschaltet um weiterhin zwei
parallel arbeitende Rechner zur Verfügung zu haben. Wie beim
*SIMIS*-Prinzip werden auch hier Eingabe- und Ausgabedaten mittels
Software vergleichen.@Ulrich

![2v2 Konfiguration @Ulrich](/misc/2v2.png "fig:") [fig:2v2]

![2v3 Konfiguration @Ulrich](/misc/2v3.png "fig:") [fig:2v3]

Datenübertragung
----------------

Die Zuverlässigkeit der internen Kommunikation wird mittels Prüfsummen
und Zwei-Kanal Datenübertragung sichergestellt. Das *ESTW SIMIS-C* nutzt
für den internen Datenaustausch normierte Telegramme. An diese wird eine
redundante Prüfsumme angehängt, die vom Empfänger ebenfalls berechnet
wird. Eine Nicht-Übereinstimmung der Prüfsummen indiziert Fehler in der
Übertragung, z.B. verursacht durch eine zufällige Störung des Signals.
Diese äußern sich in Bitflips, d.h. ein oder mehrere Bits der
Übertragungsdaten kehren ihren Wert um. Bei *ESTW SIMIS-C* werden für
die Prüfsumme zwei Byte verwendet, was die Identifizierung von bis zu
vier gleichzeitig in einem Telegramm auftretenden Bitfehler garantiert.
Beim Auftreten einer Störung bei einem Kommunikationskanal wird dieser
abgeschaltet und die Kommunikation läuft vorübergehen auf nur einem
Kanal weiter. Wenn dieser Fall eintritt werden Langtelegramme verwendet,
welche die doppelte Länge eines Normaltelegramms haben. Die Nachricht
des gewöhnlichen Telegramms wird kopiert und invertiert und anschließend
an die ursprüngliche Nachricht angehängt. Die Prüfsumme wird weiterhin
am Ende des Telegramms angefügt.
Eine weitere Sicherheitsmaßnahme dient dem Prüfen der Verbindung
zwischen einzelnen Rechnern. Durch das Versenden von sogenannten
Betriebsfähigkeitstelegrammen wird die ordnungsgemäße Kommunikation
überprüft ohne dass ein betrieblicher Datenaustausch stattfindet.@Ulrich

Bedienung
---------

Da bei elektronischen Stellwerken Bedienung durch den Menschen
unabdingbar ist muss die Schnittstelle zwischen Mensch und Maschine
ausreichend gesichert sein. Dies beinhaltet die Bedienung durch den
Mitarbeiter, beginnt aber bereits bei der sicherheitsrelevanten
Darstellung der Bedienungsoberfläche. Um zu vermeiden dass falsche
Eingaben aufgrund einer inkorrekten Anzeige der Daten auf einem
Bildschirm getätigt werden, wird erneut auf Redundanz zurückgegriffen.
Die sogenannte Sichtgeräte-Doppelsteuerung *SIDOS* sorgt dafür, dass die
anzuzeigenden Bilder immer zweikanalig, also von zwei verschiedenen
Grafikkarten, eingespeist werden. Zwischen diesen beiden Signalen wird
in kurzen Abständen alterniert, was bei abweichenden Signalen zu einem
Blinken im Betroffenen Bildteil führt und damit auf einen Fehler
aufmerksam macht. Bei neueren Bedienplätzen wird von einer visuellen
Lösung abgesehen und stattdessen ein parallelgeschalteter
Referenzrechner hinzugefügt der bei fehlerfreiem Betrieb die gleiche
Speicherbelegung wie der Bedienplatzrechner vorweisen kann.
Auch bei korrekter Anzeige aller Bedienelemente können Fehler passieren,
die auf Unachtsamkeit des Mitarbeiters zurückzuführen sind. Um dieser
Fehlerquelle entgegenzuwirken wurde das Kommandofreigabe/*KF*-verfahren
entwickelt. Bei kritischen Befehlen muss die Aufmerksamkeit erhöht sein
und versehentliche Eingaben müssen verhindert werden. Hierfür muss der
Mitarbeiter bei der Eingabe eines solchen Befehls zusätzlich zur
normalen Bedienung die KF-Taste drücken, welche direkt mit dem Stellwerk
verbunden ist und nicht mit dem Bedienplatzrechner kommuniziert.
Zusammen mit einer Zeitverzögerung bis zur Annahme des kritischen
Befehls beim Stellwerk soll damit sichergestellt werden dass die Eingabe
bedacht und gewollt geschehen ist. Bei modernen Implementierungen wird
auf eine isoliert verbaute KF-Taste verzichtet, ihre Funktion wird durch
zwei in die Bedienoberfläche integrierte KF-Tasten übernommen. Bei
Eingabe eines kritischen Befehls muss der Mitarbeiter die KF1 Taste
mitbetätigen, analog zur vorher beschrieben Implementierung,
anschließend gelangt das Signal zum Stellwerk, wird ausgelesen und an
das Bedienplatzsystem zurückgeschickt, wo verglichen wird ob der
empfangene Befehl mit dem gesendeten Befehl übereinstimmt. Hier sind
Bedienplatzrechner und der oben genannte Referenzrechner
beteiligt.@Ulrich

Zukunft der Stellwerke
======================

Durch die stetige Verbesserung von Computern und dem allgemeinen Ausbau
des Internets in Deutschlands, eröffnen sich neue Wege für Stellwerke.
Zudem wurden ältere Stellwerkmodelle modernisiert und mit bereits
vorhanden Technologien kombiniert.

Simis-D
-------

Bei Simis-D handelt es sich um die Weiterentwicklung von Simis-C. Hier
wurde von der grundlegenden Systemarchitektur und
Sicherheitsvorkehrungen wenig geändert, sondern mehr im Hinblick auf
Wirtschaftlichkeit und Kostenersparnis.

Im Jahr 2005 ging Simis-D in die Testphase über und wurde auf der
Strecke Annaberg - Buchholz eingesetzt. Hier wurde sowohl die Hardware
als auch die Software modularer aufgebaut. Somit ist es einfacher
Stellwerkanlagen in unterschiedlichen Größen zu realisieren. Zudem
besitzt diese Version bessere Schnittstellen, wodurch die Signale,
Weichen und Blockeinrichtungen besser gesteuert werden können. Die
größte Verbesserung in Hinblick auf die Wirtschaftlichkeit und Kosten
ist die Reduzierung der benötigten Kabel. Durch ein optimiertes Konzept
der Anbindung von Außenanlagen, dezentral platzierter Elektronik, sowie
das Verwenden von vorhanden Leitungswegen für die Kommunikation, ist es
möglich bis zu 35% Kabel zu sparen im Hinblick auf andere
Stellwerksysteme. Außerdem ist es nun möglich Hardware, wie etwa
Rechner, durch handelsübliche Ware zu ersetzen. Zudem konnte durch den
Einsatz neuer ESTW-Techniken, und einen modularen dezentralen
Stellteile, eine Erhöhung der Streckengeschwindigkeit um 30% erreicht
werden.@Siemens

Digitale Stellwerke
-------------------

Bei digitalen Stellwerken handelt es sich um die Weiterentwicklung von
elektronischen Stellwerken. Dabei ist der Unterschied zwischen beiden
die Ansteuerung der Stelleinheit im Schienennetz. Hierbei verwendet die
digitale Variante ein IT-Datenkabel um über ein IP-Netzwerk die nötigen
Signale zu übermitteln. Somit entfallen zum einen die Kosten für die
Kupferkabel und zum anderen kann das neue Netz mit einer dezentralen
Energieversorgung auskommen, wodurch weitere Kabeleinsparungen möglich
sind. Zudem können die Stellwerke nun über willkürlich große Distanz
gesteuert werden, da die vorher notwendige individuelle Verbindung von
Stellwerk zu Stellelement nicht mehr gegeben sein muss. Außerdem kann
der Zugbetreiber bereits bestehende Telekommunikations- und
Energieinfrastrukturen verwenden. Durch die Digitalisierung ist es zudem
möglich leichter Fehler zu finden. Außerdem verringert sich der
Wartungsaufwand, was wiederum die Nachhaltigkeit fördert.

Zudem wird mit dem Einzug der Digitalen Stellwerke versucht alle
Stellwerke zu vereinheitlichen, da in Deutschland im Schienennetz immer
noch eine Vielzahl an verschiedenen Stellwerken (mechanische,
elektro-mechanische, Relais-Bauweisen und ESTW) verwendet werden. Somit
wäre es auch einfacher Fachkräfte und Wartungspersonal auszubilden und
die Deutsche Bahn allgemein wettbewerbsfähiger zu machen.@digital

EULYNX
------

Bei EULYNX handelt es sich um einen europäischen Zusammenschluss von 13
Zugbetreibern wie unter anderem die Deutsche Bahn oder die
Österreichische Bundesbahn. Er wurde 2014 gegründet und befindet sich
nun in der dritten Phase für eine Grundlage der Vereinheitlichung. Dabei
ist das Ziel dieses Zusammenschlusses eine einheitliche
Bedienschnittstelle, digitale Steuerung sowie die Automatisierung des
Schienenverkehrs. Somit würde jedes europäische Schienennetz auf dem
gleichen Bau- und Sicherheitsstandard laufen. Diese Vereinheitlichung
bringt auch der Industrie seine Vorzüge, da Teile für das Schienennetz
nicht mehr nur spezifisch für einen Betreiber hergestellt werden müssen,
sondern alle Betreiber die gleichen Teile verwenden können.@eulynx Im
Hinblick auf die Zukunft der Stellwerke in Deutschland ist zu sagen,
dass es noch ein weiter Weg ist. Zum einen sind noch nicht alle älteren
Modelle durch elektronische Stellwerke ersetzt worden, zum anderen gibt
es bereits mit der Entwicklung von digitalen Stellwerken die nächste
Version. Interessant wird es zu beobachten, wie das EULYNX-Projekt den
Standard innerhalb von Europa setzt und somit die Kosten aller Betreiber
senken kann. Dadurch kann man davon ausgehen, dass die Modernisierung
des Schienennetzes wohl kostengünstiger und schneller vorangehen wird
als in den letzten Jahrzehnten.

<span>00</span> CIA. “The World Factbook - Railways”
“<https://www.cia.gov/library/publications/the-world-factbook/fields/384.html>”
Stand Oktober 2020 Ulrich Maschek. “Analyse zur Gestaltung
elektronischer Stellwerke” 1996 Diplomarbeit Technische Universität
Dresden DB AG. “Systemarchitektur und Vernetzung BZ/UZ” Lastenheft
415.9012, Stand F06/97/B3 Sigurd Mura. “Einbindung vorhandener
Stellwerke in das BZ-Konzept” Wikipedia “Eisenbahnunfall von Bad
Aibling” Stand Oktober 2020
“<https://de.wikipedia.org/wiki/Eisenbahnunfall_von_Bad_Aibling>” Torge
Hinrichs. “IT Sicherheit in künftigen digitalen Zugsicherungssystemen -
Potentielle Risiken und Analyseansätze” 2017 Masterarbeit Hochschule für
Angewandte Wissenschaften Hamburg Siemens. “Simis D - Neue
Stellwerksplattform” Broschüre 2008 Deutsche Bahn.
“<https://fahrweg.dbnetze.com/fahrweg-de/kunden/nutzungsbedingungen/digitale_lst/allgemein-3084902>”
Stand Oktober 2020 EULYNX. “www.eulynx.eu” Stand Oktober 2020




{{< pdf path="/slides/elektronische_stellwerke_systemarchitektur_und_zuverlaessigkeit.pdf" name="Elektronische Stellwerke - Systemarchitektur & Zuverlässigkeit" >}}


