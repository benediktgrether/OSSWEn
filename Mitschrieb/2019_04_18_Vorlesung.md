# Vorlesung 18.04.2019

- Hashwerte -> Prüfsumme (40 stellige Hex-Zahl)
  - git verwendet den SHA-1 Algo

- Interne Datenbank des Repository besteht aus fünf Klassen:
  - Blobs -> Dokumente
  - Trees -> Verweise auf Blobs und andere Trees
  - Commits -> Ein Verweis auf einen Tree und einen Vorgänger
  - Branches und Tags -> Bezeichnung für einen Commit

## Tag erzeugen

```
git tag -a[versionsnummer (oder was im Tag drin stehen soll)] -m[git commit message (Warum haben wir dem Brief einen Tag gegeben)]
```

## Branch erzeugen

```
git branch [zweig]
```

- Wechsel zwischen Branches
```
git checkout [zweig]
```

## Branches zusammenführen

- Zielzweig als Arbeitskopie auschecken
```
git merge [zweig]
```
-> mit dem Quellzweig aufrufen
    -> Änderung werden automatisch committed

### Branches löschen

- Falls der Quellzweig gelöscht werden soll.
```
git branch -d [zweig]
```

## Commits rückgängig machen 

```
git reset --hard HEAD~[Anzahl der Commits die wir Rückgängig machen wollen]
```

## Rebasing 

```
git rebase master
```

## Merge oder Rebase

- Merge 
  - alle Commits in einem Quellzweig werden zu einem einzigen neuen Commit im Zielzweig zusammengefasst 

- Rebase
  - alle Commits werden einzeln auf den Zielzweig übertragen (für Fortgeschrittene: Commits können kombiniert werden)
  - nach einem Rebase muss immer eine fast-Forward-Merge ausgeführt werden (Vorteil: Bei diesem Merge sind keine Konflikte möglich!)

