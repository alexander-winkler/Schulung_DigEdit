# Digitale Edition

Lektürehinweise

* Sahle, Patrick. „Digitale Edition“. In Digital Humanities: Eine Einführung, herausgegeben von Fotis Jannidis, Hubertus Kohle, und Malte Rehbein, 234–49. Stuttgart: J.B. Metzler, 2017. https://doi.org/10.1007/978-3-476-05446-3_17.
* KONDE - Kompetenznetzwerk Digitale Edition, <https://www.digitale-edition.at/>
* Driscoll, Matthew James, Elena Pierazzo, und Open Book Publishers, Hrsg. Digital scholarly editing: theories and practices. Digital humanities series, v. 4. Cambridge: Open Book Publishers, 2016, <https://www.openbookpublishers.com/product/483/digital-scholarly-editing--theories-and-practices>.


## Begriffliches

- wissenschaftliche Edition: Historisch-kritische Rekonstruktion eines Werks unter Berücksichtigung der Entstehungs- und Überlieferungsgeschichte.
Vom Medium prinzipiell unabhängig, traditionell jedoch eine Printedition. Typischer Bestandteil ist ein Abriss über die Editionsprinzipien ("Editorische Notiz" oder "Praefatio") sowie ein textkritischer Apparat (im Fußnotenbereich oder als Anhang), der über die Überlieferungsvarianten oder vorgenommene editorische Eingriffe in den Text Rechnung ablegt.

- digitale Edition: eine wissenschaftliche Edition im Digitalen, insbesondere unter Ausnützung der besonderen Stärken der digitalen Kodierung und Repräsentation (Verlinkung -> Hypertext, Trennung von Inhalt und Darstellung, die eine vielschichtige Annotation ermöglicht, Maschinenlesbarkeit)

Einen Überblick über digitale Editionen bietet der [Catalogue of Digital Editions](https://dig-ed-cat.acdh.oeaw.ac.at/).
Als *best-practice*-Beispiel einer digitalen Edition kann das [Deutsche Textarchiv (DTA)](https://www.deutschestextarchiv.de/) gelten.
Im Rahmen des Projekts wird mit dem [DTA-Basisformat](https://www.deutschestextarchiv.de/doku/basisformat/) eine Subset der TEI-P5-Richtlinien definiert und dokumentiert, das für den Einsatz im DTA optimiert ist, sich aber auch gut auf ähnliche Projekte übertragen lässt.
Die Format-Dokumentation ist eine solide Basis für eigene Editionsvorhaben.

## Geschichtliches

Der erste E-Book des [Gutenberg Projects](https://www.gutenberg.org/) entstand am 4. Juli 1971.

Die Text Encoding Initiative gibt es seit 1987, Version 1 der TEI-Richtlinien wurde 1990 veröffentlicht.^[Abrufbar unter <https://doi.org/10.5281/zenodo.3459202>]


## TEI: Der *de facto* Standard für textbasierte Editionen

Obwohl es auch graphbasierte Ansätze zur digitalen Edition gibt, ist die XML-Kodierung nach den TEI-Regeln der *de facto* Standard für digitale Editionen.

Kurz zur Geschichte von TEI

TEI erlaubt es, die logische Struktur sowie die physische Gestalt eines Überlieferungsträgers oder (abstrakter) eines Werks wiederzugeben.

## Beispiel: Goehtes Wanderes Nachtlied

Erklärung von TEI-XML anhand eines Beispiels.

### Druckausgabe 1827

<a title="Johann Wolfgang von Goethe
, Public domain, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:De_Goethe_Werke_LH_01_099.jpg"><img width="256" alt="De Goethe Werke LH 01 099" src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/45/De_Goethe_Werke_LH_01_099.jpg/256px-De_Goethe_Werke_LH_01_099.jpg"></a>

### Transkription des Textes

```
Ein gleiches
Über allen Gipfeln
Ist Ruh,
In allen Wipfeln
Spürest du
Kaum einen Hauch;
Die Vögelein schweigen im Walde.
Warte nur, balde
Ruhest du auch.
```

Dokumentation reiner Textinformation.

### TEI-Edition auf TextGrid

[Link zur Ressource](https://textgridlab.org/1.0/tgcrud-public/rest/textgrid:11h43.0/data)

#### Aufbau einer TEI-Edition

XML-Dateiformat: Textbasiert, hierarchisch verschachtelte Elemente in spitzen Klammern.

Grundstruktur:

Wurzelelement `<TEI>`

```xml
<TEI>
</TEI>
```

Header und Text

```xml
<TEI>
<teiHeader></teiHeader>
<text></text>
</TEI>
```

Der Header enthält Metadaten, d.h. Informationen über den Text, die Edition usw.
Die Entscheidung über die Detailtiefe der Metadaten obliegt den Herausgebenden.

Das `<text>`-Element enthält den Text.
Für jeden Text/jedes Editionsprojekt muss eine zweckmäßige Kodierungsform festgelegt werden.
Die Ausgestaltung der digitalen Edition hängt also vom Editionsobjekt ebenso ab wie vom Zweck und Zielpublikum der Edition.

Das konkrete Beispiel enthält im `<text>`-Knoten einen `<body>` und mehrere `<div>`-Hierarchieebenen, die das einzelne Textobjekt in einem größeren Editionszusammenhang verorten.
Über `id`-Attribute können alle Element eindeutig identifiziert werden.

Der für Gedichteditionen typische `<lg>`-Knoten (linegroup) enthält `<l>`-Elemente (lines).

Bei Prosa-Texten werden dagegen i.d.R. die Paragraphen (durch `<div>`) und die typographischen Zeilenumbrüche (durch `</lb>`) ausgezeichnet.


## Lesen/Benutzen ein digitalen Edition

Üblicherweise werden digitale Editionen nicht in Ihrer rohen XML-Form gelesen.
Vielmehr werden sie durch spezielle Transformationsskripte (üblicherweise XSLT) in andere Formate (html für Webseiten, pdf, docx etc.) überführt.

Online-Editionen sind oftmals mit einer bestimmten Visualisierungs- und Arbeitsumgebung verbunden,vgl. z.B. die [Edition der Alexander von Humboldt-Tagebücher der BBAW](https://edition-humboldt.de/).

Neben der traditionellen Lektüre gewinnen auch maschinelle Auswertungsverfahren bei digitalen (d.h. maschinenlesbaren) Editionen an Bedeutung.
Mit speziellen Programmen oder Verfahren können XML-Dateien analysiert werden.
Grundkenntnisse in [XPath](https://www.w3schools.com/xml/xpath_intro.asp) sind hierfür unerlässlich.

## Erstellen einer digitalen Edition

TEI ist ein textbasiertes Format, kann also selbst mit den einfachsten Editoren erstellt werden.
Die Verschachtelung wird jedoch rasch komplex und unübersichtlich.
Zudem können selbst kleine Fehler die Wohlgeformtheit der Elemente zerstören und die Funktionsfähigkeit der Edition beeinträchtigen.

Es gibt daher Programme, die die XML-Generierung erleichtern.
Der Marktführer ist das proprietäre Programm [OxyGen](https://www.oxygenxml.com/).
Es gibt jedoch auch freie Alternativen, wie etwa das [TEI-Plugin für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=e-editiones.tei-publisher-vscode).
Die Editoren Visual Studio Code und Atom unterstützen jedoch nativ zumindest die XML-Syntax.

Vor größeren Editionsprojekten sollte man sich jedoch unbedingt beraten und schulen lassen.

Digitale Editionen lassen sich auf vielen Ebenen annotieren.
Es lassen sich z.B. zu Wörtern im Text die Lemmata und/oder grammatische Informationen ergänzen.
Ort- und Personennamen lassen sich mit Normdatensätzen verknüpfen.
Es lassen sich Anspielungen und Zitate einbinden.

Einen Eindruck von den Erwartungen an eine wissenschaftliche digitale Edition liefern die [Criteria for Reviewing Scholarly Digital Editions, version 1.1](https://www.i-d-e.de/publikationen/weitereschriften/criteria-version-1-1/) von Sahle et al.

## Planung und Durchführung von Editionsprojekten

Bei digitalen Editionsprojekten umischtige Vorausplanung erforderlich:

1. Nötige technische Kompetenzen erwerben
2. Datenmodellierug (TEI-Vokabular)
3. Datenmanagementplanung
  1. Lizenz (z.B. CC-BY)
  2. FAIR (Archivierung auf Repositorium, permanente Referenzierbarkeit durch Identifikatoren)
  3. Dokumentation und Metadaten

## Bibliotheksservices

Die Bibliothek kann bei den technischen Grundlagen lediglich allgemein beraten.
In den spezifisch bibliothekarischen Kompetenzbereich fallen aber Fragen der Lizenzierung, Archivierung und Referenzierbarkeit.
Die Bibliothek kann dabei helfen, das richtige Repositorium zu finden.