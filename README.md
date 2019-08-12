# Phoenix Reisen Design System

Das Design System der [Phoenix Reisen GmbH](https://www.phoenixreisen.com). Es stellt allgemeine Styles für diverse autarke Web-Applikationen von Phoenix Reisen bereit - noch aber nicht für die Website selbst.

Unterstützt wird es durch diverse Drittbibliotheken (JS & CSS), die da wären:

- [KSS Knyle Style Sheets - CSS Dokumentationsgenerator](https://warpspire.com/kss/)
- [Tachyions.css - funktionales CSS Framework für unter der Haube](https://tachyons.io/)
- [Animate.css - Animationssammlung für auf der Haube](https://daneden.github.io/animate.css/)
- [Pikaday](https://pikaday.com/)

## Installation

Die Installation erfolgt via npm.

```
npm install @phoenixreisen/phoenix-design-system
```

## Entwicklung 

```
npm install     # Abhängigkeiten installieren

npm run dev     # Startet den "dev mode". Änderungen am SCSS werden direkt transpiliert.
                # Zudem wird ein lokaler Dev-Server gestartet.
```

Dokumentation lokal aufrufbar unter http://localhost:3027/.

Die HTML-Dokumentation wird durch KSS auf Grundlage des Ordners ```template``` generiert. Änderungen am SCSS in ```src``` sind nach einem *manuellen* Reload direkt ersichtlich.

## Deployment

### Build

Build für Produktion in den Ordner ```dist```:

```bash
npm run build       # reiner Build
npm run generate    # lintet den Code & generiert auch die Doku
```

### Deployment-Prozess

#### Code

Um die Änderungen für alle Projekte als neue Version zur Verfügung zu stellen, müssen sie auf npm veröffentlicht werden.

```bash
npm run generate                # baut den Code
npm version major|minor|patch   # erhöht die Version entsprechend
npm publish                     # veröffentlicht auf npm
```

#### Dokumenation

Deployed wird über & auf [Netlify](https://www.netlify.com). 

Im [Netlify-Backend](https://www.netlify.com) kann ein Deployment über Knopfdruck angestoßen werden.

Netlify zieht sich dazu selbstständig die Sourcen von [Github](https://github.com/phoenixreisen/design-system) und ruft danach den npm-Befehl `npm run generate` auf - siehe `package.json`.

Dieser kompiliert `src` nach `dist` und generiert mittels `kss` die HTML-Dokumentation (ebenfalls nach `dist`). Anschließend wird das Kompilat bei Netlify abgelegt und ersetzt das Bisherige.

## KSS Dokumentation

**SCSS**-Änderungen im Ordner ```template``` müssen ebefalls transpiliert werden.

```bash
npm run build:docs
```

## Kurz-Tutorials zum Umgang innerhalb einzelner Services

### Design-System ins Projekt einbinden

Für das Projekt sollte ein SCSS-Kontext eingerichtet sein. Möglichst vor den Projekt-Styles werden die Styles des Design-Systems eingebunden, um auf alle Variablen und Werte zugreifen zu können.

```scss
@import '@phoenixreisen/phoenix-design-system/src/index.scss';
```

### Font innerhalb eines Service installieren

Innerhalb eines mit Webpack aufgesetzten Service bietet das Design-System die Möglichkeit, angebotene Fonts auf folgende Weise in den Service zu inkludieren:

```js
// Bsp. für Titillium
require('@phoenixreisen/phoenix-design-system/src/fonts/titillium.css');
```

Wird im Service die index.js des Design-System inkludiert, so sind die Font-Imports bereits enthalten.

## Authors

* Fabian Marcus (<f.marcus@phoenixreisen.com>)
* Jan Hermanns (<j.hermanns@phoenixreisen.com>)
* Leon Schmitz (<l.schmitz@phoenixreisen.com>)