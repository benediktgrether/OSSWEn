# Vorlesung 11.04.2019

## Neue Begriffe

- Blame
  - Wer hat was gemacht in einem Dokument.
- Release
  - Release Managment zum kennzeichnen was für den Release fertig ist.


## Branches

- Trunk
  - Trunk beschreibt den Hauptentwicklungszweig (vergl. Master-Branch in git)

- Branches
  - branches Ordner müssen manuell erstellt werden.
  - Danach wird ein neuer Unterordner mit alice-zweig angelegt und dort den Brief hineingelegt.


**Branches erstellen**

Neuer Ordner im Repository anlegen.
```
$ svn mkdir file:///Users/stefan/Temp/Repository/branches -m "branches erzeugt"
```

Kopieren des Trunks in den Branch Ordner.
```
$ svn copy file:///Users/stefan/Temp/Repository/trunk file:///Users/stefan/Temp/
Repository/branches/alice-zweig -m "alice zweig kopiert
```

Arbeitskopie aus dem Branches-Unterverzeichnis auschecken
```
$ svn checkout file:///Users/stefan/Temp/Repository/branches/alice-zweig ProjektA
```

## Re-Integration

Zielzweig als Arbeitskopie auschecken
```
$ svn checkout file:///Users/stefan/Temp/Repository/trunk ProjektA
```
  - svn merge mit dem Quellzweig aufrufen
  ```
  $ svn merge --reintegrate file:///Users/stefan/Temp/Repository/branches/alicezweig
  ```

Änderungen einchecken und branch löschen
```
$ svn commit -m "Alice Zweig re-integriert"
```

## Release-Branches

- Release-Branches bleiben immer bestehen damit wir auf alte Versionen zurück greifen können.

## Tags

- Revisionsnummer sollten nicht nach außen gegeben werden.
  
- Tags
  - definierten Zeitpunkt
    - die Software als konkrete Versionen veröffentlicht werden
  
- tags Ordner müssen manuell erstellt werden.
- Tags sind Verzeichniskopie 
- Tags unterscheide sich nur semantisch von branches, technisch ist es dasselbe
- Tags sollten nach der Erstellung nicht mehr geändert werden!
  - Keine commits mehr in den tag Ordner machen

tags -> version-1.0 -> brief.txt

Tag-Verzeichnis im Repository erzeugen
```
$ svn mkdir file:///Users/stefan/Temp/Repository/tags -m "tags erzeugt"
```

Trunk oder Branch in ein neues Tag-Unterverzeichnis kopieren
```
$ svn copy file:///Users/stefan/Temp/Repository/trunk file:///Users/stefan/Temp/
Repository/tags/brief-xp -m "brief.txt als XP getaggt"
```

**Tags sollten nicht als Arbeitskopie ausgecheckt werden**

## Head

Als Head bezeichnet man die aktuellste Revision des Repository
    - »svn update« aktualisiert z.B. per Default auf Head
    - »svn checkout« holt die aktuellste Revision

Bei vielen Subversion-Operationen kann aber auch mit dem
Parameter »-rREV« eine explizite Revisionsnummer angegeben
werden, z.B.:

```
svn checkout –r8 file:///Users/stefan/Temp/Repository/trunk ProjektA
$ cd ProjektA
/ProjektA $ svn update
```


## Blame

Mittels »svn blame Datei« wird für jede Zeile die Revisionsnummer (und Autor) der Änderung eingeblendet

```
svn blame brief.txt
```
