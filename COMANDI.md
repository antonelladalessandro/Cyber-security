# NMAP

Nmap (abbreviazione di "Network Mapper") è uno strumento open source utilizzato per la scansione e l’analisi di reti.

## COMANDI

```-v```
Questa opzione abilita la modalità verbose, aumentando il livello di dettagli mostrati durante l’esecuzione della scansione.

```-vv```
Fornisce un livello di dettaglio ancora maggiore.

```-A```
Esegue una scansione aggressiva, combinando varie tecniche (trova anche il sistema operativo).

```-sn```
Esegue solo il rilevamento degli host attivi senza effettuare la scansione delle porte.

```-Pn```
Lo usiamo quando si sospetta che un host possa essere configurato per non rispondere ai ping.

```-sL```
Mostra un elenco degli host da scansionare senza effettivamente eseguire alcuna scansione.

```-sV```
Identifica i servizi in esecuzione sulle porte aperte e cerca di determinare la versione specifica del servizio.

```--version-all```
Esegue una rilevazione completa, più approfondita, delle versioni dei servizi.

```-oN```
Salva i risultati della scansione in un file di testo leggibile.

```-oX```
Salva i risultati in formato XML.

```-sS```
Invia pacchetti SYN senza completare la connessione.

```-sF```
Invia pacchetti con il flag FIN.

```-sA```
Invia pacchetti con il flag ACK, senza tentare di aprire connessioni.

```-sM``` 
Invia pacchetti con i flag FIN/ACK.

```-sN```
Non imposta alcun flag nel pacchetto TCP.

```-sX```
Invia pacchetti con i flag FIN, PSH e URG attivi.

```--scanflags```
Consente di personalizzare i flag TCP del pacchetto, è una tecnica avanzata per impostare manualmente combinazioni di flag specifiche.

```-sU```
Esegue una scansione delle porte UDP.

```-sl```
Utilizza un "host zombie" (un dispositivo inattivo con indirizzo IP statico e prevedibile) per inviare pacchetti al target.

```-F```
Scansione veloce delle porte.

# LINUX

**Linux** è un sistema operativo open source, noto per la sua flessibilità, sicurezza e per essere altamente personalizzabile. Linux è gratuito ed è basato su **Unix**, un sistema operativo sviluppato negli anni '70, da cui eredita stabilità e solidità. 

**Caratteristiche principali di Linux**:
1. **Open Source**: Il codice sorgente di Linux è liberamente disponibile, e chiunque può modificarlo, migliorarlo o distribuirlo.
2. **Distribuzioni (distro)**: Linux non è un sistema operativo unico, ma piuttosto una base su cui sono costruite diverse versioni, dette distribuzioni, come Ubuntu, Fedora, Debian, CentOS e molte altre.
3. **Sicurezza e Stabilità**: Linux è noto per la sua sicurezza e affidabilità, motivo per cui è utilizzato per i server, i supercomputer e anche in ambienti sensibili.
4. **Multi-utente e Multi-tasking**: Linux permette a più utenti di lavorare sullo stesso sistema contemporaneamente e supporta il multitasking, eseguendo più processi insieme.

**Componenti principali di Linux**:
- **Kernel**: Il cuore del sistema operativo, gestisce le risorse hardware e l’interfacciamento con i componenti del sistema.
- **Shell**: L’interfaccia a riga di comando (CLI), che permette agli utenti di comunicare con il sistema tramite comandi.
- **File System**: Linux utilizza una struttura gerarchica di directory per organizzare i file e le cartelle.

## COMANDI

```pwd``` (Print Working Directory) Lo uso per capire dove mi trovo nell’albero.

```cd``` Lo uso per spostarmi da una cartella all'altra.

```cd ..``` Ti permette di andare su di un livello.

```cd../..``` Ti permette di tornare indietro di due cartelle.

```cd-``` Per tornare indietro.

```ls``` Fa vedere tutti i file e le cartelle in un percorso.

```ls -la``` Fornisce una vista completa e dettagliata del contenuto della directory, inclusi i file nascosti.

```clear``` Si usa per pulire la shell.

```touch``` Si usa per creare file.

```nano``` Si usa per aprire e scrivere nei file.

```mkdir``` Crea una directory.

```rm``` Si usa per rimuovere il file.

```rm dir``` Cancella le cartelle vuote.

```rm -r``` Cancella le cartelle e quello che c'è al loro interno.

```history``` Mostra tutti i comandi che hai usato.

```history !NUM``` Richiama un comando.

```tree``` Si usa per mostrare l'albero.

```man``` Ti indica come funzionano gli altri comandi.

```cp``` Si usa per copiare il file.

```cat``` Si usa per vedere il contenuto del file.

```diff``` Compara due file riga per riga.

```echo``` Stampa qualcosa a video.

```chmod``` Si usa per dare o togliere i permessi.

```./``` Si usa per aprire/eseguire un file sh.

```find``` Si usa per cercare file e directory in un percorso specificato.

per richiamare un comando

per spostare file e directory

dice chi ha loggato nel sistema

legge una stringa

ci permette di cercare un valore specifico all'interno dei file

word counter, conta le parole, ti ritorna di quante parole è fatto un documento

sospende un programma per una certa quantità di secondi

è utilizzato per terminare processi in esecuzione.



