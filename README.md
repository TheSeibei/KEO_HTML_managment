# KEO HTML Management

Dieses Repository verwaltet die HTML-Dateien, die auf der WordPress-Seite über das Plugin **KEO GitHub HTML Embed** eingebunden werden.

## Zweck

Statt HTML-Inhalte direkt in WordPress oder per FTP zu ändern, werden die Dateien hier im GitHub-Repository gepflegt. WordPress lädt die freigegebenen HTML-Dateien automatisch aus diesem Repository.

## Eingebundene Dateien

Aktuell sind folgende Dateien erlaubt:

```text
fachbetriebe.html
foerdernde_fachbetriebe.html
guetesiegel.html
```

Nur diese Dateien können über den Shortcode geladen werden.

## Verwendung in WordPress

Die HTML-Dateien werden mit folgendem Shortcode eingebunden:

```text
[keo_github_html file="fachbetriebe.html"]
```

Weitere Beispiele:

```text
[keo_github_html file="foerdernde_fachbetriebe.html"]
[keo_github_html file="guetesiegel.html"]
```

## Technische Funktionsweise

Das WordPress-Plugin lädt die Dateien von:

```text
https://raw.githubusercontent.com/TheSeibei/KEO_HTML_managment/main/
```

Die Inhalte werden für 10 Minuten zwischengespeichert. Änderungen im Repository können daher bis zu 10 Minuten brauchen, bis sie auf der Website sichtbar sind.

## Neue HTML-Datei hinzufügen

1. Neue `.html` Datei in dieses Repository legen.
2. Datei im WordPress-Plugin `keo-github-html.php` in `$allowed_files` ergänzen.
3. Änderung committen.
4. In WordPress per Shortcode einbinden.

Beispiel im Plugin:

```php
$allowed_files = [
    'fachbetriebe.html',
    'foerdernde_fachbetriebe.html',
    'guetesiegel.html',
    'neue-datei.html',
];
```

Shortcode:

```text
[keo_github_html file="neue-datei.html"]
```

## Sicherheit

Aus Sicherheitsgründen lädt das Plugin nur Dateien, die explizit in `$allowed_files` freigegeben sind. PHP-Dateien oder beliebige Dateinamen werden nicht ausgeführt und nicht geladen.

## Wichtig

Dieses Repository ist nur für statische HTML-Inhalte gedacht. WordPress-Plugins wie `helwacht-availability.php` gehören in ein eigenes Plugin-Repository und werden separat deployed.
