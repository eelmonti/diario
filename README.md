# Nota su GitHub Pages

Una sola pagina di testo, ospitata gratis su GitHub Pages. È un unico file (`index.html`), senza server.

**Come salva:** il testo viene **cifrato nel browser con la tua password** (AES-256) e scritto nel repository come file `nota.enc` tramite le API di GitHub. Il repository può quindi essere pubblico: chi lo guarda vede solo dati illeggibili. Senza la password non si legge nulla.

## Installazione (circa 5 minuti)

### 1. Crea il repository
- Su GitHub: **New repository**, nome a piacere (es. `nota`), **Public** (serve per Pages gratuito).
- Carica `index.html` nella radice (**Add file → Upload files**).

### 2. Attiva GitHub Pages
- **Settings → Pages → Build and deployment**: *Source* = **Deploy from a branch**, branch **main**, cartella **/ (root)** → Save.
- Dopo un minuto il sito è su `https://TUOUTENTE.github.io/nota/`.

### 3. Crea il token (serve per salvare)
- GitHub → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
- *Repository access*: **Only select repositories** → scegli solo questo repository.
- *Permissions → Repository permissions*: **Contents → Read and write**.
- Scegli la scadenza (es. 1 anno), genera e **copia il token** (inizia con `github_pat_`).

### 4. Primo accesso
- Apri il sito. Inserisci repository (`utente/nome`, spesso già precompilato), token e una **password** per la nota (ripetila per conferma).
- Fatto: scrivi, e il testo si salva da solo dopo pochi secondi di pausa.

Da un altro dispositivo: apri lo stesso sito e reinserisci repository, token e password (il token si salva nel browser solo la prima volta su ogni dispositivo).

## Cose da sapere

- **La password non si può recuperare**: se la perdi, il testo cifrato non è più leggibile. Scegline una di almeno 12 caratteri: essendo il file pubblico, la forza della password è l'unica protezione.
- **Token**: dà accesso in scrittura solo a questo repository. Chi ha il token può modificare/cancellare il file, ma non leggere la nota senza la password. Se lo perdi, revocalo da GitHub e creane un altro.
- **Ogni salvataggio è un commit** (con un paio di secondi di pausa tra l'uno e l'altro): la cronologia del repository funziona da storico delle versioni. Se vuoi tornare a una versione precedente, apri `nota.enc` → *History*; ma per leggerla va decifrata dalla pagina, quindi il modo più comodo è ripristinare quella versione del file.
- **Conflitti**: se modifichi da due dispositivi contemporaneamente, la pagina ti chiede quale versione tenere.
- **Limite**: circa 400 KB di testo (molte decine di pagine).
- Se hai altri siti sullo stesso `TUOUTENTE.github.io`, condividono lo spazio di memoria del browser, e quindi potrebbero leggere il token salvato. Se vuoi evitarlo usa un dominio personalizzato per questo sito.
- Se non vuoi salvare il token nel browser, usa "Dimentica repository e token su questo dispositivo" nella schermata di accesso quando hai finito.

## Cambiare password

Non è prevista una funzione dedicata. Il modo semplice: elimina `nota.enc` dal repository (dopo aver copiato il testo), poi riaccedi con la nuova password: verrà creata una nota nuova.
