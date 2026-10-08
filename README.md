# Laboratorio Tailwind CSS — guida per il docente

Tecnologie Web 2026/2027 · Dott. Alex Testa

## Cos'è

Il materiale del laboratorio che accompagna il deck «Tailwind CSS · Laboratorio»: **11 mini esercizi** su **Tailwind CSS v4**, divisi in **5 livelli**, per **2 ore** in aula.

Tutti gli esercizi costruiscono pezzi dello stesso sito inventato, **TW Day 2027**, «la giornata dei progetti di Tecnologie Web». Si parte dal Tailwind «spartano», con poche utility di base direttamente nell'HTML, e si arriva all'approccio dei puristi: HTML con soli nomi semantici e CSS a parte.

Tailwind si carica **sempre e solo dal CDN**: niente npm, niente build. Bastano un browser moderno e la connessione a internet.

```text
laboratorio-tailwind/
├── README.md     ← questa guida
├── esercizi/     ← i file di partenza per gli studenti, con il loro README
└── soluzioni/    ← le stesse 11 cartelle, con i file completi
```

## Scaletta

| # | Cartella | Titolo | Livello | Minuti |
|---|---|---|---|---|
| — | — | Avvio | — | 10 |
| 01 | `01-primo-contatto` | Primo contatto | 1 · Spartano | 7 |
| 02 | `02-card-speaker` | La card dello speaker | 1 · Spartano | 8 |
| 03 | `03-navbar` | La navbar | 2 · Layout | 8 |
| 04 | `04-griglia-programma` | La griglia del programma | 2 · Layout | 10 |
| 05 | `05-mobile-first` | Mobile first | 3 · Responsive e stati | 10 |
| 06 | `06-form-e-stati` | Il form: stati e valori arbitrari | 3 · Responsive e stati | 8 |
| 07 | `07-colori-del-tema` | I colori del tema | 4 · Su misura | 7 |
| 08 | `08-font-e-token` | Font e token | 4 · Su misura | 8 |
| 09 | `09-componenti-apply` | Da utility a componenti | 5 · Per i puristi | 12 |
| 10 | `10-bottoni-varianti` | Bottoni: stati e varianti | 5 · Per i puristi | 10 |
| 11 | `11-css-separato` | Il CSS in un file a parte | 5 · Per i puristi | 12 |
| — | — | Chiusura | — | 10 |

Avvio 10′ + esercizi 100′ + chiusura 10′ = **120′**.

## Come distribuire

- Agli studenti si consegna **solo la cartella `esercizi/`**, per esempio in uno zip: dentro c'è anche il README per loro.
- `soluzioni/` resta al docente e si mostra **a fine livello**: stesse cartelle, stessi file e stessi testi, in versione completa.
- Le cartelle sono indipendenti: chi resta indietro può aprire direttamente l'esercizio successivo.

## Gli esercizi, uno per uno

### 01 · Primo contatto

- **Obiettivo**: collegare Tailwind dal CDN e usare le prime utility (colori, spaziature, tipografia).
- **Errori frequenti**: lo script messo nel `body`, oppure lo stupore per l'`h1` piccolo: è il Preflight.

### 02 · La card dello speaker

- **Obiettivo**: costruire una card con il box model di Tailwind: larghezza, spaziature, bordi, ombre e immagine rotonda.
- **Errori frequenti**: `w-24 h-24` invece di `size-24` va bene lo stesso. L'immagine è già `display:block` grazie al Preflight, quindi `mx-auto` la centra.

### 03 · La navbar

- **Obiettivo**: impaginare una barra di navigazione con flexbox e tenerla in alto con `sticky`.
- **Errori frequenti**: `flex` messo sul `nav` invece che sull'`header`; `sticky` senza `top-0` non resta in alto.

### 04 · La griglia del programma

- **Obiettivo**: una griglia di card con CSS grid e un badge posizionato con `relative` e `absolute`.
- **Errori frequenti**: senza `relative` sulla card il badge finisce nell'angolo della pagina; senza `overflow-hidden` la copertina esce dagli angoli.

### 05 · Mobile first

- **Obiettivo**: rendere responsive una pagina pensata solo per il desktop, partendo dal telefono e aggiungendo i breakpoint.
- **Errori frequenti**: `sm:` letto come «solo smartphone», mentre vuol dire «da 640px in su».

### 06 · Il form: stati e valori arbitrari

- **Obiettivo**: dare stati interattivi (hover, focus, active, disabled, placeholder) agli elementi del form e usare i valori arbitrari tra parentesi quadre.
- **Errori frequenti**: `focus:ring` senza `focus:outline-none` mostra due contorni; gli spazi dentro le parentesi quadre, come `text-[28 px]`, non funzionano.

### 07 · I colori del tema

- **Obiettivo**: definire i colori del sito con `@theme` nel blocco del CDN e cambiarli da un punto solo.
- **Errori frequenti**: una sfumatura usata ma non definita nel tema, come `brand-600`, produce una classe senza effetto.

### 08 · Font e token

- **Obiettivo**: aggiungere al tema font, dimensioni, raggi e ombre, e usare le classi che ne derivano.
- **Errori frequenti**: `font-bold` con Instrument Serif crea un grassetto finto; nel tema servono le virgolette sul nome della famiglia (`"DM Sans"`).

### 09 · Da utility a componenti

- **Obiettivo**: lasciare nell'HTML solo nomi semantici e spostare lo stile in `@layer components` con `@apply`, senza cambiare l'aspetto della pagina.
- **Errori frequenti**: `@apply` di una classe componente, oppure un refuso in `@apply` che ferma tutto Tailwind (si vede nella console).

### 10 · Bottoni: stati e varianti

- **Obiettivo**: creare un piccolo sistema di bottoni (base + varianti) con stati dentro `@apply`, e scoprire che le utility vincono sui componenti.
- **Errori frequenti**: senza `border-2 border-transparent` nella base, i bottoni pieni e quelli con il bordo hanno altezze diverse; `disabled` funziona solo sui `<button>`, non sui link.

### 11 · Il CSS in un file a parte

- **Obiettivo**: approccio purista estremo. L'HTML contiene solo nomi semantici e lo stile sta tutto in `style.css`, in CSS classico; Tailwind, sempre dal CDN, dà solo il Preflight e i token del tema come variabili CSS.
- **Errori frequenti**: `var()` di una variabile non dichiarata in `@theme static` resta vuota; il `link` messo prima dello script; `@apply` scritto nel file esterno.

## Nota tecnica

Il CDN `@tailwindcss/browser@4` è pensato per sviluppo e prototipi, **non per la produzione**. In laboratorio serve proprio a questo: lavorare subito, senza installare nulla.
