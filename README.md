# Angular Hello World

Ziel dieser Übung ist es, eine erste kleine Applikation in Angular zu bauen. Ähnlich wie bei der ersten Struts-Anwendung geht es darum,
einen Namen in ein Eingabefeld einzugeben und mit dem Klicken eines Buttons einen Begrüßungstext anzuzeigen.

Grundlage für das Projekt ist ein mit [Angular CLI](https://github.com/angular/angular-cli) generiertes Grundprojekt. Im Folgenden wird
deshalb kurz beschrieben, wie in dem Projekt mit Angular CLI terminalbasiert gearbeitet werden kann.

## Angular CLI Kommandos

### Entwicklungsserver

Der Server zum Testen der Anwendung kann durch Eingabe von `ng serve` gestartet werden. Die Applikation ist dann unter der Adresse
`http://localhost:4200/` verfügbar. Sobald Änderungen am Code durchgeführt werden, wird dieser neu kompiliert, und die Änderungen sind
anschließend direkt testbar.

### Erzeugung von Codestrukturen

Eine neue Angular-Komponente kann durch `ng generate component <component-name>` generiert werden. Weitere Möglichkeiten sind
`ng generate directive|pipe|service|class|guard|interface|enum|module`.

### Kompilieren

Die Anwendung kann durch `ng build` kompiliert werden. Die Artefakte befinden sich im Unterverzeichnis `dist/`. Wenn man die Option
`--prod` nutzt, wird ein produktiv nutzbare Anwendung kompiliert.

### Weitere Informationen

Hilfe zu den Kommandos kann man über `ng help` bekommen. Alternativ kann man die 
[Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md) studieren.

## Übung

Ähnlich wie die Struts Hello World-Application besteht auch die Angular-Version aus einem Formular, dass die Eingabe des
Namens erlaubt. Eine Schaltfläche führt dann dazu, dass die Grußformel dynamisch generiert und angezeigt wird.

Die folgenden Schritte sind dafür notwendig:
- Erzeugung einer neuen Komponente
- Erstellung der HTML-Seite
- Implementierung der View-Logik

### Erzeugung einer neuen Komponente

Die Angular Hello World-Applikation wird von einer Komponente gesteuert, die den View bereitstellt und die dazugehörige Logik
implementiert. Dabei nutzen wir Angular CLI, um die Komponente zu erzeugen.

*1. Öffnen Sie in der IntelliJ ein Terminal (Tastenkürzel `Alt+F12`).*

*2. Wechseln Sie im Terminal in das Projektunterverzeichnis `src/app`.*

*3. Erstellen Sie eine neue "HelloWorld"-Komponente durch folgenden Befehl: `ng generate component hello-world`.*

*4. Binden Sie die neue Komponente in die Root-Komponente ("App"-Komponente) der Angular-Anwendung ein.*

Sie erreichen dies, indem Sie den sogenannten Selektor der "HelloWorld"-Komponente (`<app-hello-world>`) in die 
Root-HTML-Seite (`src/app/app.component.html`) einbinden. Zusätzlich kann auch noch eine Überschrift angegeben werden:

```html
<h1>Welcome to Angular</h1>

<app-hello-world></app-hello-world>
```

### Erstellung der HTML-Seite

Als nächstes muss das HTML-Formular und die Anzeige der Grußformel im HTML-Template der "HelloWorld"-Komponente
(`hello-world.component.html`) implementiert werden.

*1. Erzeugen Sie ein Label, ein Text-Input und einen Button für das Formular.*

Das könnte bspw. folgendermaßen aussehen:

```html
<label for="name">Name:</label>
<input type="text" id="name">
<button>Say Hello!</button>
```

*2. Verbinden Sie die Eingabe des Eingabefeldes mit dem Attribut "name" der "HelloWorld"-Komponente.*

Wir benötigen hierfür ein sogenanntes Two-Way-Binding des "Models" des Eingabeelementes mit dem Attribut der Komponente. Hierfür
muss folgendes Attribut dem Eingabefeld hinzugefügt werden:

```html
[(ngModel)]="name"
```

*3. Stellen Sie sicher, dass ein Klicken der Schaltfläche die Methode `sayHello()` in der Komponente aufruft.*

Dies erreicht man über ein sogenanntes Event-Binding. Wir müssen hierfür das "Click"-Ereignis der Schaltfläche mit der
Methode der Komponente verbinden. Hierfür benötigen wir folgendes Attribut im Button:

```html
(click)="sayHello()"
```

*4. Als letztes müssen wir sicherstellen, dass der Wert des Komponentenattributs "greetings" im Formular angezeigt wird.*

Die Anzeige eines Wertes erreichen wir bspw. über eine sogenannte "Interpolation" - hierbei handelt es sich um ein "Property Binding".
Folgender Code muss hierfür dem Formular hinzugefügt werden:

```html
<h3>{{ greetings }}</h3>
```

### Implementierung der View-Logik

Als letztes müssen wir die Logik des Views in der Komponente (`hello-world.component.ts`) implementieren. 
Führen Sie bitte folgende Schritte durch.

*1. Erzeugen Sie zwei String-Attribute in der Komponentenklasse: `name` und `greetings`.*

*2. Erzeugen Sie eine Methode `sayHello(): void` in der Komponentenklasse.*

*3. Implementieren Sie die Methode, indem Sie die Grußformel mithilfe des `name`-Attributs zusammensetzen und in `greetings` speichern.*

### Testen

Testen Sie anschließend die Anwendung. Sie können den Server über den Befehl `ng serve` im Terminal starten. Der Server ist danach
unter der URL `http://localhost:4200` verfügbar.
