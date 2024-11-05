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
