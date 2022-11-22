# Instructions  

## Tutorial
[Ruby on Rails Tutorial 7th edition Preview](https://www.learnenough.com/ruby-on-rails-7th-edition-tutorial)

RAILS TUTORIAL, 7th EDITION:

Gute Neuigkeiten: auf der Online-Plattform von O`Reilly ist nun die vollständige E-Book-Version erschienen: https://www.oreilly.com/member/login/?next=/library/view/ruby-on-rails/9780138050061/.

Das Tutorial ist auf der Plattform auch als Video-Serie verfügbar: https://www.oreilly.com/library/view/ruby-on-rails/9780138050351/.

Sie benötigen mindestens einen Trial-Zugang für O`Reilly. Dieser ist an eine beliebige E-Mail-Adresse gebunden und gilt für 10 Tage. Die E-Book-Version wird nicht über die Bibliothek bereitstehen können. Ich rege den Erwerb der Print-Version an. Diese erscheint jedoch erst Ende November.

Zum Vergleich: auf railstutorial.org kostet der Zugang mindestens $29 für einen Monat - ein fairer Preis, aber für Sie nicht notwendig, wenn Sie sich für die obige Version entscheiden.


# GIT + GITHUB (auf REPLIT)

Durch das verwendete Betriebssystem (nixOS) und die Containerisierung der Entwicklungsumgebung funktioniert auf Replit die standardmäßige Git-Konfiguration über die Kommandozeile nicht (dauerhaft), da sie nicht persistiert wird. Es ist notwendig, einige Umgebungsvariablen über das Secrets-Tab in Replit zu setzen.

Das sind:

```nix
  GIT_AUTHOR_NAME, 
  GIT_AUTHOR_EMAIL, 
  GIT_COMMITTER_NAME, 
  GIT_COMMITTER_EMAIL
```

Legen Sie für jede Variable einen (Key-Value-)Eintrag an. Nutzen Sie die GitHub-Zugangsdaten.

Als Passwort für den GitHub-Zugang sollten Sie sich ein Personal Access Token erzeugen: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token. Wir haben in der Veranstaltung besprochen, welche Vorteile diese Token ggü. Passwörtern bieten. 

Auf GitHub unter Profil > Settings > Developer settings > Personal access tokens können Sie ein neues Token erzeugen. Ich habe ein Fine-grained token erzeugt, dieses REPLIT_WS2022 genannt und die folgenden Rechte eingeräumt:

- Read access to metadata
- Read and Write access to code.

Sie werden beim "git push ..." zur Authetifizierung aufgefordert.

# HEROKU:

Bis Ende November können Sie die Free-Tier-Angebote nutzen. Danach ist etwas mehr Aufwand erforderlich - über das GitHub Student Pack jedoch auch weiter kostenfrei möglich: https://blog.heroku.com/github-student-developer-program.

Um das Heroku CLI, ähnlich wie im Tutorial beschrieben nutzen zu können, bin ich wie folgt vorgegangen:

### 1. Heroku Account anlegen und API-Key erzeugen (Manage Account > API-Key)
### 2. auf Replit: Datei replit.nix anpassen (Show hidden files, Zeile mit pkgs.heroku hinzufügen)

```
{ pkgs }: {
	deps = [
        pkgs.nano
        pkgs.ruby_3_0
        pkgs.rubyPackages_3_0.solargraph
        pkgs.rufo
        pkgs.sqlite
        pkgs.heroku
	];
}
```

### 3. Heroku Login

Sie benötigen den im Tutorial für die Cloud-IDE beschriebenen Weg (interaktives Kommandozeilen-Login mit API-Key als Passwort):

```
$ heroku login --interactive 
```

### 4. Passenden Heroku-Stack wählen

Leider sind die Versionen der Pakete nicht maximal kompatibel und begrenzt anpassbar. Heroku verlangt für den aktuellen Stack eine neuere Version der Programmiersprache Ruby, die Replit noch nicht als Paket bereitstellt. Daher muss auf Heroku explizit ein anderer Stack ausgewählt werden. Sie erfahren den aktuell gewählten Stack auf Heroku auf der Kommandozeile:

```shell
$ heroku stack
=== ⬢ example-app Available Stacks
  container
  heroku-18
  heroku-20
* heroku-22
```

Sie wählen einen kompatiblen Stack mit:

```
$ heroku stack:set heroku-20
```

[Quelle: https://devcenter.heroku.com/articles/stack]


## Rails Dokumentation
[Ruby on Rails Documentation](https://rubyonrails.org/)

## Andere (für Sie kostenfreie) Tutorials/Kurse
- [Rails Kurs auf LinkedIn](https://www.linkedin.com/learning/ruby-on-rails-6-essential-training/faster-better-less-painful-website-development) (über unsere Hochschulbibliothek)
- [Rails Kurs auf Udemy](https://www.udemy.com/course/ruby-on-rails-a-beginners-guide-free/) (setzt kostenfreies Udemy-Konto voraus)

## Background
- [HTTP-Protokoll](https://de.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
- [WebSocket](https://de.wikipedia.org/wiki/WebSocket)
- [Single Page Apps (SPA)](https://de.wikipedia.org/wiki/Single-Page-Webanwendung)
- [Heroku PaaS](https://www.heroku.com/)
