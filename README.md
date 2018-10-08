# Kurs_HTML5_CSS3

## Tools / Infos
* Live Server Extension für VS code
* Emmet
  * `html:5` -> vollst. Seitenstruktur 
* https://caniuse.com - testen von html Sprachelementen & Nutzungsdaten nach Browsern und Ländern

## Grundstruktur
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

## Core-Attribute
* werden vererbt
  * lang
  * dir
* nur für das Element
  * id - muss eindeutig sein
  * class - gleiche Werte in einem Dokument zulässig
  * title - wird als Tooltip angezeigt
* ?
  * style

## Elemente
* \<meta xxx=""> 
* Blockelemente
  * h1, ..., h6
  * p
  * div (neutrales Element)
* Inlineelemente
  * strong, statt b
  * em, statt i
  * span (neutrales Element)
* Spezialelemente
  * script - lädt JS-Skript, blockierend, während Skript geladen wird
  * link - setzt referenz auf StyleSheet, nicht blockierend, möglichst weit oben

## Neuerungen mit HTML5
Neue semantische Elemente

* header, navigation, main, footer, aside, ...
* werden von älteren Browsern nicht unterstützt -> modernizr.2.6.2.js
* section - hierarchische Organisation des Dokumentes, Überschriften in sections immer h1!
* article - "neben" der Dokumentstruktur stehende Informationsblöcke - styling über class-Angabe
* video, iframe (Tipp: Einbettungscode kopieren)
* Formulare: 
  * Input-Types date, ...
  * label
  * tabindex als Attribut
  * pattern -> Prüfung erst bei Abschicken

```html
    <label for="vn">Vorname:</label>  
    <input id="vn" type="text" name="vorname" required tabindex="1">
```

  * Auto-Validierung bei GET oder GET novalidate
  * placeholder attribute
  * type range
  * type date, datetime, ...
  * datalist bei type text, statt select/option (mehr Eingaben möglich)
  * output-Element - 

## Barrierefreiheit
* "Komplexes Thema"
* tabindex: erst die Inputs mit tabindex, dann die ohne Angabe.

