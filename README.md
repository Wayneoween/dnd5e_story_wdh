# Abenteuer-Tagebuch: Waterdeep Dragon Heist

Zu unserem Vergnügen und damit wir alle immer auf dem Laufenden sein können, was
in der letzten Session passiert ist, welche Aufgaben offen sind und damit sich
niemand fragen muss "Wer war nochmal…?" pflegen wir dazu eine kleine Interetseite.

Wir planen damit keine Gewinne zu erziehlen und betrachten diese Seite als Fan-Seite
im Sinne der [Fan Content Policy](https://company.wizards.com/fancontentpolicy).

## Technisches

Wir verwenden GitHub Pages, um aus diesem Repository eine Website zu machen. Im
Hintergrund läuft dafür Jekyll. Wir haben das um einige Dinge erweitert, die uns
manche manuelle Schritte abnehmen sollen. Folgende Dinge gilt es dabei zu beachten:


### Glossar-Erstellung

Für jeden Glossar-Eintrag gibt es in `_glossary` eine Markdown-Datei. Der Dateiname
richtet sich dabei nach der kürzesten Repräsentation des Lemmas, d.h. lautet der
volle Name einer Person *Volothamp Geddarm*, ist als Dateiname *Volo* zu wählen,
da die Person unter diesem Namen bekannt ist.

Die Datei *muss* einen `type` im YAML-Front Matter haben, der unter
`_includes/icons` eine Entsprechung bei den Icons findet.

Die Datei *kann* weiterhin ein `title` Attribut haben, in der dann der ganze
Name *Volothamp Geddarm* ausgeschrieben drin steht.

Um im Code einen Verweis auf den Glossar einzubringen, verwenden wir `{%
include glossary_link.html title="Langes Lemma" name="Kurzes Lemma" %}`, wobei
`name` nicht angegeben werden muss, wenn das lange Lemma und das kurze bis auf
die Großschrift identisch sind. Bei manuellem Anlegen dieser Links muss darauf
geachtet werden, dass zwischen `{%` und `%}` kein Zeilenumbruch enthalten ist,
da sonst das Hilfsscript Dinge kaputtmacht.

Damit nicht alle Lemmas von Hand im Fließtext eines Beitrags verlinkt werden müssen,
gibt es das Hilfsscript `glossary_preproc.rb`. Dieses Script akzeptiert als erstes
Argument den Dateinamen eines Posts (`.md`) und durchsucht diesen nach Lemmas,
die noch nicht verlinkt sind, um diese mit dem Glossar zu verlinken. Dabei
sucht es sowohl nach den kurzen als auch den langen Lemmas.

### Questlog

Um über die Quests auf dem Laufenden zu bleiben, pflegen wir eine Liste von
Beiträgen in `_quests`. Dort liegen Markdown-Dateien, die drei Attribute in ihrem
Front-Matter haben können:

* `title`: Die Überschrift des Quests
* `status`: Kann die Werte `open` oder `done` haben, dient der Sortierung in der Übersicht.
* `reward`: Die Belohnung für das Quest als Freitext

### Infoboxen

Um besondere Informationen im Fließtext hervorzuheben, können Infoboxen verwendet
werden, die im aktuellen Design als Post-Its erscheinen. Es gibt drei Kategorien:

* `char`: Um Mitstreiter zu beschreiben
* `hint`: Für Hinweise allgemein
* `quest`: Um im Fließtext ein Quest zu erwähnen

Eine Infobox kann wie folgt hinzugefügt werden:

```html
<div class="infobox char">
  <h3>Name des Characters</h3>
  <p class="class">Charakterklasse und Rasse der Figur</p>
  <p>Beschreibung der Figur</p>
</div>

<div class="infobox hint">
  <h3>Überschrift</h3>
  <p>Inhalt des Hinweises</p>
</div>

<div class="infobox quest">
  <h3>Überschrift</h3>
  <p>Was zu erledigen ist</p>
  <p class="reward">Die Belohnung</p>
</div>
```
