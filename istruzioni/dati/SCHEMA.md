# Scheda dei dati

## Entità: Evento

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `titolo` | stringa | `"Lettere in movimento"` |
| `data` | data in formato `AAAA-MM-GG` | `"2026-06-12"` |
| `orario` | ora in formato `HH:MM` | `"10:00"` |
| `categoria` | stringa | `"Incontro"` |
| `descrizione` | stringa | `"Come cambia un messaggio quando cambiano le lettere? Un incontro su tipografia, ritmo e comunicazione visiva."` |
| `immagine` | stringa, percorso del file | `"assets/lettere-in-movimento.svg"` |
| `immagine_alt` | stringa | `"Lettere geometriche disposte su una griglia"` |
| `sede_id` | numero intero | `1` |

## Entità: Sede

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `nome` | stringa | `"Sede centrale"` |
| `indirizzo` | stringa | `"Corso Duca degli Abruzzi 24, Torino"` |

## Chiavi

La chiave primaria di entrambe le entità è `id`: è numerica, univoca all’interno della propria entità e stabile. Gli identificativi esistenti non devono essere cambiati quando si modificano altri dati.

## Relazione

Una sede può ospitare più eventi; ogni evento si svolge in una sola sede. Il campo `Evento.sede_id` fa riferimento a `Sede.id`.

## Quantità

Il dataset contiene sei eventi e tre sedi.

## Aggiornamento dei dati

Chi mantiene il progetto aggiorna i dati modificando `eventi.json` e `sedi.json` nella repository. Dopo aver controllato che i file siano validi e che ogni `sede_id` corrisponda a un `id` presente in `sedi.json`, le modifiche vengono pubblicate insieme al sito.

## Che cosa mostra la pagina

La pagina Programma mostra gli appuntamenti con data, orario, categoria, descrizione, immagine e sede. La pagina Info e luoghi presenta le sedi, i relativi indirizzi e le informazioni utili per localizzarle. Il festival e gli eventi sono immaginari; le sedi reali sono utilizzate come riferimento per il progetto didattico.

## Schema Evento–Sede

```mermaid
erDiagram
    SEDE ||--o{ EVENTO : ospita
    SEDE {
        int id PK
        string nome
        string indirizzo
    }
    EVENTO {
        int id PK
        string titolo
        date data
        string orario
        string categoria
        string descrizione
        string immagine
        string immagine\_alt
        int sede\_id FK
    }