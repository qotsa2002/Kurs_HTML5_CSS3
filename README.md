# HTML5

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

# CSS3

## Selektoren

Priorität:
* Spezifizität
  1. ID...
  1. Class... / Pseudo-Klassen... / Attribut...
  1. Type...
* Reihenfolge

### Spezifizität
Selektor        | ID | Class | Type
----------------|----|-------|------
* (Universell)  | 0  | 0     | 0
p               | 0  | 0     | 1
.lightblue      | 0  | 1     | 0
\#div1          | 1  | 0     | 0
p.yellow        | 0  | 1     | 1
a:hover (Zustand)        | 0  | 1     | 1
p:firstline (Struktur)    | 0  | 1     | 1
[title='...']   | 0  | 1     | 0
[title=]        | 0  | 1     | 0
div p           | 0  | 0     | 2
div#div1_id p   | 1  | 0     | 2
div#div1_id > p | 1  | 0     | 2
h1 + p          | 0  | 0     | 2
 
### Konnektoren
* \+ adjacent sibling
* ~ all siblings
* \> children


### strukturellen Pseudoklassen

:first-child
:last-child
:nth-child(even|odd) jedes gerade/ungerade Element
:nth-child(number) - das Element an Position number
:nth-child(n+2) - ab dem 2. Element alle
:nth-child(3n) - jedes 3. Element
:first-of-type

 
## Layout-Modi

### Flow-Layout

Standard-Layout

### Box-Modell

1. Inhalt (width, height)
1. Padding
1. Border
1. Margin - mit Margin Merge - überlagern der Margins, der größere gewinnt; body margin geht nach innen! 

#### Ränder & Schatten
* border
* border-radius
* box-shadow
```css
        #p1 {
            box-shadow: -5px -10px 5px darkgray; /* l(-)/r(+) t(-)/b(+) Verlauf */
        }
```
  * inset - Shadow nach innen
  * Listen von shadows - werden von rechts nach links "gemalt";

#### Hintergrund
* background: `url(special.gif);` oder `background-image: linear-gradient(155deg, 0%, red 100%);`
  
#### Sichtbarkeit
```css
        #p2 {
            background-color: rosybrown;
            _display: none; /* aus dem Flow herausnehmen */
            _visibility: hidden; /* unsichtbar, aber Layout bleibt erhalten */
            opacity: 0; /* 0 ... 1, Layout bleibt erhalten */
        }
```

#### Positionierung
 
position:   |  ist im Flow | ist positioniert
------------|--------------|-----------------
static      |   x          |    -
relative    |   x          |    x
absolute    |   -          |    x (relativ zum nächsten positionierten Parent)
fixed       |   -          |    x (relativ zum viewport)
sticky      |   -          |    x

* `float: left|right` - um divs z.B. nebeneinander zu positionieren & `clear: left|both|right` um das nächste Element im Flow *nach* den gefloateten Elementen zu positionieren [float.html](./css3/float.html) und [float02.html](./css3/float02.html)

### Tablelayout

* `display: table;` - optional, solange kein Zugriff auf die ganze Tabelle benötigt wird
* `display: table-row;` - optional, solange nur eine Zeile benötigt wird
* `display: table-cell;` - Element soll 1-n Zellen füllen

[layout_03.html](./css3/layout_03.html)

### Flexlayout

`display:flex`

Elemente im Flexcontainer richten sich aus nach:

Main Axis: links nach rechts
```css
justify-content: flex-start; /* | flex-start | flex-end | center | ... */
```

Cross Axis: oben nach unten
```css
align-items: center; /* | flex-start | flex-end | stretch (default) | ... */
```

Items haben
* order - Reihenfolge festlegen
* flex - relative Breite festlegen

[layout_04.html](./css3/layout_04.html)

[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)


### Gridlayout

`display:grid`

Es wird ein Gridtemplate definert, das Spalten un Zeilen festlegt

*Margins werden **nicht** gemerged, sondern addieren sich*

Von-/Bis-Angaben beziehen sich auf die (Trenn-)Linien der Zeilen und Spalten, d.h. bei 3 Spalten habe ich die Linien 1, 2, 3, 4

[layout_05.html](./css3/layout_05.html)

https://developer.mozilla.org/de/docs/Web/CSS/CSS_Grid_Layout


## Transitions

Gesteuertes Umschalten von einer Darstellung zu einer anderen.


Beispiel - Breite beim Übergang eine Sekunde lang ändern: 
```css
        .box:hover {
            width: 100px;
            height: 100px;
            background-color: yellow;
            transition: width 1s, height 1s, background-color 1s; /* = all 1s */
        }
```

Angabe: Attribut Dauer [Verzögerung]


## Hinweise

https://www.rechnerhaus.de/blog/unterschied-zwischen-css-scss-sass

https://scotch.io/tutorials/using-sass-with-the-angular-cli
