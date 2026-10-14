# 🎮 Tris – Tic Tac Toe con Vue.js

🌐 **Gioca online:** [https://melvinrosales.com/tris-vue/](https://melvinrosales.com/tris-vue/)

[![Vue.js](https://img.shields.io/badge/Vue.js-3-4FC08D?style=flat&logo=vuedotjs&logoColor=white)](https://vuejs.org/)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/it/docs/Web/JavaScript)
[![CSS](https://img.shields.io/badge/CSS-Grid-1572B6?style=flat&logo=css&logoColor=white)](https://developer.mozilla.org/it/docs/Web/CSS)
[![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=flat&logo=vite&logoColor=white)](https://vite.dev/)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=flat&logo=github&logoColor=white)](https://github.com/rack09/tris-vue)

Una mini web app per giocare a **Tris** con un amico, costruita con lo stato reattivo di Vue.

💻 **[Repository GitHub](https://github.com/rack09/tris-vue)**

## 🚀 Descrizione del progetto

Gioco del Tris per due persone che giocano sullo stesso dispositivo, realizzato per il Progetto Vue.js 1 di Start2Impact.

## ✨ Funzionalità principali

- 🧩 Tabellone con nove caselle disposte in una griglia 3 × 3.
- 🔄 Il giocatore X inizia ogni partita; le mosse si alternano tra X e O.
- 🛡️ Una casella occupata non può essere modificata e il clic non cambia il turno.
- 🏆 Riconoscimento delle otto combinazioni vincenti: tre righe, tre colonne e due diagonali.
- 🔒 Blocco delle mosse dopo una vittoria, anche tramite pulsanti disabilitati.
- 🤝 Pareggio quando tutte le caselle sono occupate e non esiste un vincitore.
- 🔁 Pulsante **Nuova partita** per svuotare il tabellone e ripartire da X.
- 🇮🇹 Interfaccia in italiano.

## 🌐 Demo online

Il gioco è stato pubblicato sul sito web personale ed è accessibile direttamente dal browser, senza installazione locale.

**[https://melvinrosales.com/tris-vue/](https://melvinrosales.com/tris-vue/)**

Nella demo, due persone giocano sullo stesso dispositivo e alternano le mosse tra X e O.

## 🛠️ Tecnologie utilizzate

| Tecnologia | Utilizzo |
| --- | --- |
| 🟢 Vue.js 3 | Componenti, Composition API, stato reattivo e `<script setup>`. |
| 🟨 JavaScript ES6+ | Regole del gioco, gestione dei turni e controllo delle combinazioni. |
| 🎨 CSS Grid | Tabellone su tre colonne e caselle quadrate. |
| ⚡ Vite | Server di sviluppo, build di produzione e anteprima locale. |
| 📦 Node.js e npm | Ambiente e gestione delle dipendenze. |
| 💻 Git e GitHub | Versionamento e pubblicazione del codice sorgente. |

## 💻 Installazione locale

Occorrono Node.js e npm. La compatibilità dichiarata in `package.json` è `^22.18.0 || >=24.12.0`.

Clonare il repository e aprire la cartella del progetto:

```bash
git clone https://github.com/rack09/tris-vue.git
cd tris-vue
```

Installare le dipendenze:

```bash
npm install
```

Avviare il server di sviluppo:

```bash
npm run dev
```

Aprire l'indirizzo indicato nel terminale. In Windows PowerShell è possibile usare `npm.cmd` al posto di `npm`.

## 📜 Comandi disponibili

| Comando | Descrizione |
| --- | --- |
| `npm run dev` | Avvia il server locale di sviluppo. |
| `npm run build` | Genera la versione ottimizzata nella cartella `dist`. |
| `npm run preview` | Mostra localmente la build di produzione. |

## 📦 Build e anteprima

Generare la versione di produzione:

```bash
npm run build
```

I file compilati vengono creati nella cartella `dist`.

Per controllare localmente la build:

```bash
npm run preview
```

Aprire l'indirizzo restituito dal comando. L'anteprima è un server locale per la verifica della build.

## 🧱 Organizzazione e scelte tecniche

Il componente `src/App.vue` contiene lo stato, le regole, il template e gli stili del gioco.

- **Stato con `ref`:** `caselle` conserva i nove valori del tabellone (`null`, `'X'` oppure `'O'`); `giocatoreAttuale` indica chi deve giocare.
- **Risultati con `computed`:** `vincitore` deriva dal confronto delle combinazioni vincenti; `pareggio` richiede sia l'assenza di un vincitore sia il tabellone pieno.
- **Rendering con `v-for`:** ogni elemento dell'array produce un pulsante. Gli indici sono chiavi stabili perché le nove posizioni non vengono riordinate.
- **Eventi con `@click`:** la funzione `gioca` riceve l'indice della casella e controlla che la mossa sia consentita.
- **Messaggi con `v-if`, `v-else-if` e `v-else`:** la vittoria ha precedenza sul pareggio; durante una partita viene mostrato il turno.
- **Ripristino:** `nuovaPartita` crea un nuovo array di nove valori `null` e imposta X come giocatore iniziale. I risultati calcolati si aggiornano in base al nuovo stato.
- **Layout:** CSS Grid distribuisce le caselle su tre colonne uguali; `aspect-ratio` mantiene la forma quadrata.

Per la dimensione di questo progetto, un unico componente mantiene vicine le regole e l'interfaccia e rende il funzionamento facile da seguire.

## 🗂️ Struttura principale del progetto

| File | Responsabilità |
| --- | --- |
| `src/App.vue` | Stato, regole del gioco, interfaccia e stili del componente. |
| `src/main.js` | Crea l'applicazione Vue e monta il componente principale. |
| `index.html` | Pagina HTML che ospita l'applicazione. |
| `vite.config.js` | Configurazione dell'ambiente Vite. |
| `package.json` | Script, dipendenze e compatibilità di Node.js. |
| `package-lock.json` | Versioni esatte delle dipendenze installate. |
| `.gitignore` | Esclude dipendenze, build e file temporanei dal versionamento. |
| `README.md` | Documentazione e istruzioni del progetto. |

## 🧪 Verifica manuale

Le caselle sono numerate da 0 a 8, da sinistra a destra e dall'alto verso il basso. Premere **Nuova partita** prima di ciascuna prova.

| Caso | Sequenza di clic | Risultato atteso |
| --- | --- | --- |
| 🏆 Vittoria di X sulla prima riga | `0, 3, 1, 4, 2` | `Ha vinto X!`; le mosse successive sono bloccate. |
| 🏆 Vittoria di O sulla seconda riga | `0, 3, 1, 4, 8, 5` | `Ha vinto O!`. |
| 🏆 Vittoria diagonale di X | `0, 1, 4, 2, 8` | `Ha vinto X!`. |
| 🤝 Pareggio | `0, 1, 2, 4, 3, 5, 7, 6, 8` | `Pareggio!`. |
| 🎯 Vittoria alla nona mossa | `0, 1, 4, 2, 6, 3, 7, 5, 8` | `Ha vinto X!`, anche con il tabellone pieno. |
| 🛡️ Clic su una casella occupata | `0, 0` | La casella resta X e il turno resta a O. |
| 🔁 Nuova partita | Premere il pulsante durante o dopo una partita. | Nove caselle vuote e `Turno di: X`. |

## 🔖 File versionati

Il repository include il codice sorgente, `package.json` e `package-lock.json`. La cartella `node_modules` contiene le dipendenze installate e `dist` contiene la build generata; entrambe sono escluse tramite `.gitignore`.

## 👨‍💻 Autore

**Melvin Rosales** - progetto didattico del Master Full Stack Development di Start2Impact.

- GitHub: [@rack09](https://github.com/rack09)
