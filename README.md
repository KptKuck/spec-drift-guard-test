# Spec-Drift-Guard — Testprojekt

Testet ein System das verhindert, dass ein KI-Agent Spec-Aussagen als "erledigt" markiert
ohne echte Implementierung.

## Konzept

Jede verbindliche Aussage aus einer Spec wird ein GitHub Issue. Der Status wird ueber
Labels gesteuert. Eine GitHub Action erzwingt Regeln die der Agent nicht umgehen kann.

## Status-Labels

| Label | Bedeutung |
|---|---|
| `compliance:open` | Noch nicht implementiert |
| `compliance:in-progress` | In Arbeit |
| `compliance:verified` | Implementiert + Beweis vorhanden |
| `compliance:wont-fix` | Bewusst nicht umgesetzt |

## Regeln (erzwungen durch GitHub Action)

1. **Ein Status gleichzeitig** — nur ein `compliance:*`-Label pro Issue
2. **Verified ist endgueltig** — kann nicht entfernt oder zurueckgesetzt werden
3. **Verified braucht Beweis** — der Abschnitt "Beweis" im Issue-Body muss ausgefuellt sein
4. **Nur Spec-Issues betroffen** — Issues ohne Label `spec-assertion` werden ignoriert

## Neues Spec-Issue anlegen

Issues > New Issue > "Spec-Assertion" Template waehlen. Pflichtfelder:
- Spec (Dropdown)
- Verbindliche Aussage
- Akzeptanz-Kriterium

## Dieses Repo

Testprojekt — wird nach erfolgreicher Validierung geloescht.
Das System wird dann auf das echte Projekt uebertragen.
