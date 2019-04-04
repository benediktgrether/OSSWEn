# Vorlesung 04.04.2019

## 01 zentrales Versionsmanagment

- Repository liegt auf dem Server und wir können nicht einfach so drauf zugreifen.
- Wir benötigen Software wo mit wir auf das Repo zugreifen können


Repository vs Arbeitskopie !! **Wichtig**
siehe Seite 25


Repo Anlegen

```
svnadmin create Repository
```

Checkout
``` shell
svn checkout file:///Users/..../Repository/ .
```

Arbeitskopie aktualisieren
```
svn update
```

Änderungen vornehmen
```
svn status
```

```
svn add brief.txt
```

```
svn status
```

Änderungen veröffentlichen
```
svn commit -m "brief hinzugefügt"
```

LOG-Message
```
svn log brief.txt
```

### Arbeitszyklus

siehe Seite 32

