---
title: Dokumentation
weight: 300
---

# Dokumentation

<p class="info">
Die OPUS 4 Dokumentation ist zur Zeit noch etwas verteilt. Das Nutzerhandbuch ist momentan noch ein PDF, dessen Inhalt
nach und nach in eine Onlineversion umgewandelt wird.
</p>

Unter <http://opus4.github.io> findet sich diese Anleitung, die momentan insbesondere für Administratoren und
Entwickler gedacht ist. Dokumentation für Entwickler findet sich auch in Source Code Kommentaren.

Auf dieser Seite finden sich Erläuterungen für die Arbeit mit der GitHub gehosteten Dokumentation.
Wir verwenden [GitHub Pages](https://help.github.com/categories/github-pages-basics/) um die Seiten zu erzeugen.
Der Source Code für diese Seiten hier findet sich im
Repository [opus4/opus4.github.io](https://github.com/opus4/opus4.github.io).

## Inhalte erstellen

Für die Inhalte wird Markdown verwendet. Für jede Seite wird eine `.md` Datei angelegt, z.B. `documentation.md` für
diese Seite. Informationen zum
[GitHub Markdown](https://help.github.com/articles/github-flavored-markdown/) das verwendet werden kann finden sich
auf den [Hilfeseiten](https://help.github.com/).

## Seitenkopf

Am Anfang jeder Seite muss ein Block wie folgender stehen.

{% highlight liquid %}
---
title: Name der Seite
weight: 20
---
{% endhighlight %}

Der **title** der Seite wird als HTML Titel der Seite verwendet und taucht in der Navigation auf.
Der **weight** Parameter bestimmt die Sortierreihenfolge der Seiten in der Navigation.

## Menü

Das Navigationsmenü wird automatisch generiert. Die `index.md` Dateien im Haupt- und in den Unterverzeichnissen werden
für die Überschriften der ersten Navigationsebene verwendet. Die Datei `index.md` ist **Home**, die Datei
`installation\index.md` ist **Installation**.

Die anderen Markdown Dateien im selben Verzeichnis werden als Menüpunkte der zweiten Ebene für die jeweilige
`index.md` Datei angezeigt. Die Datei `installation/requirements.md` wird so zum ersten Menüpunkt **Voraussetzungen**
unter **Installation**.

Die Reihenfolge der Dateien wird durch den **weight** Parameter im Kopf der Dateien bestimmt.
Hat eine Seite keinen **weight** Parameter landet sie automatisch ganz vorne, ansonsten wird aufsteigend sortiert.

## Einfache Elemente

### Überschriften

Überschriften können duch voranstellen von '#' erzeugt werden.

{% highlight liquid %}
# Überschrift 1
## Überschrift 2
### Überschrift 3
{% endhighlight %}

### Paragraphen

Paragraphen können einfach eingegeben werden.

Sie werden durch Leerzeilen von einanderen abgegrenzt.

{% highlight liquid %}
Paragraphen können einfach eingegeben werden.

Sie werden durch Leerzeilen von einanderen abgegrenzt.
{% endhighlight %}

### Texthervorhebung

Es ist möglich **fett**, *kursiv* oder auch `monospace` zur Hervorhebung von Text zu verwenden.

{% highlight liquid %}
Es ist möglich **fett**, *kursiv* oder auch `monospace`
zur Hervorhebung von Text zu verwenden.
{% endhighlight %}

Für die OPUS 4 Dokumentation verwenden wir dann noch zusätzliche Element. Die Technolgie die dahinter steht ist
[Jekyll](http://jekyllrb.com/).

## Code Blöcke

Für Code Blöcke verwenden wir das Highlight-Template.

{% highlight bash %}
$ sudo apt-get install php5
{% endhighlight %}

Das sieht in der Datei so aus:

{% highlight liquid %}
{% raw %}
{% highlight bash %}
$ sudo apt-get install php5
{% endhighlight %}
{% endraw %}
{% endhighlight %}

Dabei ist 'bash' die Sprache, die für die Hervorhebung verwendet werden soll. Die Liste der möglichen Sprachen findet
sich auf [Pygments Lexers Seite](http://pygments.org/docs/lexers/).

## Informationsboxen

Um hervorgehobene Boxen wie die folgenden zu erzeugen muss HTML direkt verwendet werden.

<p class="info">
Dies ist eine allgemeine Informationen.
</p>

<p class="note">
Dies ist ein wichtiger Hinweise.
</p>

<p class="warning">
Dies ist eine wichtige Warnung. Daten könnten z.B. verloren gehen.
</p>

Das HTML dafür sieht wie folgt aus und kann einfach in den Markdown Dateien verwendet werden:

{% highlight html %}
<p class="info">
Dies ist eine allgemeine Informationen.
</p>

<p class="note">
Dies ist ein wichtiger Hinweise.
</p>

<p class="warning">
Dies ist eine wichtige Warnung.
</p>
{% endhighlight %}

Manchmal ist es nützlich innerhalb einer solchen Box Markdown zu verwenden.

<p class="info" markdown="1">
Innerhalb einer Textbox kann Markdown verwendet werden, z.B. um etwas **fett** oder *kursiv* hervorzuheben.
Auch `code` ist möglich, aber ganz Code Blöcke sind momentan nicht machbar.
</p>

Dafür muss das **markdown** Attribut wie folgt gesetzt werden.

{% highlight html %}
<p class="info" markdown="1">
Innerhalb einer Textbox kann Markdown verwendet werden, z.B.
um etwas **fett** oder *kursiv* hervorzuheben. Auch `code`
ist möglich.
</p>
{% endhighlight %}

Ganz Code Blöcke sind momentan nicht innerhalb einer Textbox machbar.




