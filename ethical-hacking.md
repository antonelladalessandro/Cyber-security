# ETHICAL HACKING

L'ethical hacking, o hacking etico, è il processo di valutazione della sicurezza di un sistema o di una rete attraverso tecniche e strumenti simili a quelli utilizzati dai malintenzionati, con l'obiettivo di identificare vulnerabilità e migliorare la sicurezza. Le fasi principali dell'ethical hacking possono essere suddivise come segue:

1. **Pianificazione e Ricognizione**:
- In questa fase, l'hacker etico definisce l'ambito del test e raccoglie informazioni sui sistemi target. Vengono utilizzati strumenti di scansione, analisi delle reti e social engineering per ottenere informazioni rilevanti.
2. **Scansione (banner grabbing)**:
- Si tratta di identificare attivamente le porte aperte, i servizi in esecuzione e le vulnerabilità nei sistemi. Gli strumenti di scansione, come Nmap e Nessus, possono essere utilizzati per questa fase.

3. **Accesso**:
- In questa fase, l'hacker etico tenta di sfruttare le vulnerabilità identificate per guadagnare accesso non autorizzato ai sistemi. Questo può includere l'uso di exploit e tecniche di offuscamento.

4. **Mantenimento dell'Accesso**:
- Dopo aver ottenuto l'accesso, gli hacker etici possono implementare metodi per mantenere l'accesso al sistema e testare la sicurezza delle contromisure in atto.

5. **Analisi e Reporting**:
- Infine, vengono analizzati i risultati delle fasi precedenti e redatto un rapporto dettagliato. Questo rapporto dovrebbe includere le vulnerabilità trovate, le tecniche utilizzate e le raccomandazioni per migliorare la sicurezza.

6. **Risoluzione e Verifica**:
- Dopo la presentazione del rapporto, il team di sicurezza del cliente risolve le vulnerabilità e implementa le raccomandazioni. Successivamente, l'hacker etico può effettuare un secondo test per verificare che le vulnerabilità siano state corrette.

Ogni fase richiede un approccio etico e una collaborazione con il cliente per garantire che le attività di hacking non causino danni e rispettino le leggi e le normative vigenti.



# RICOGNIZIONE

La **ricognizione** (o "recon") è una fase preliminare per raccogliere informazioni su un bersaglio, e rappresenta il primo passo della "Unified Kill Chain" per ottenere un punto d'accesso iniziale. La ricognizione si divide in:

1. Ricognizione Passiva: si basa su informazioni pubblicamente accessibili senza interazione diretta con il bersaglio, come consultare record DNS pubblici di un dominio o leggere articoli sul target. <br>
2. Ricognizione Attiva: comporta un’interazione diretta con il bersaglio, come connettersi ai server dell'azienda o simulare un contatto per ottenere informazioni. Dato il suo carattere invasivo, la ricognizione attiva può portare a problemi legali senza un’autorizzazione formale. <br>

## RICOGNIZIONE PASSIVA



### WHOIS

**WHOIS** è un protocollo di richiesta e risposta che segue la specifica RFC 3912. Un server WHOIS ascolta sulla porta TCP 43 le richieste in arrivo. Il registrar di un dominio è responsabile della gestione dei record WHOIS per i nomi di dominio che sta affittando. Il server WHOIS risponde con varie informazioni relative al dominio richiesto. Di particolare interesse, possiamo scoprire: 

• Registrar: tramite quale registrar è stato registrato il nome di dominio? <br>
• Informazioni di contatto del registrante: nome, organizzazione, indirizzo, telefono, e altro (a meno che non siano nascosti tramite un servizio di privacy). <br>
• Date di creazione, aggiornamento e scadenza: quando è stato registrato per la prima volta il nome di dominio? Quando è stato aggiornato l'ultima volta? E quando deve essere rinnovato? <br>
• Name Server: a quale server chiedere di risolvere il nome di dominio? <br>
 
Per ottenere queste informazioni, dobbiamo usare un client whois o un servizio online. Molti servizi online forniscono informazioni WHOIS; tuttavia, è generalmente più veloce e conveniente usare il client whois locale. Puoi facilmente accedere al tuo client whois tramite terminale. La sintassi è:

```
whois NOME_DOMINIO
```

### NSLOOKUP

Per trovare l'indirizzo IP di un nome di dominio usando nslookup (Name Server Look Up). È necessario eseguire il comando nslookup:

```
nslookup NOME_DOMINIO
```

Per aggiungere il record:

```
nslookup -type=RECORD NOME_DOMINIO
```

### DIG

Per ricerche DNS avanzate e funzionalità aggiuntive, puoi usare dig (Domain Information Groper). Ecco come usare dig per cercare i record MX e confrontarli con nslookup. Si può usare: 
```
dig NOME_DOMINIO
```

Per specificare il tipo di record, usiamo:
```
dig NOME_DOMINIO RECORD
```

### TABELLA RIASSUNTIVA

![immagine](https://github.com/user-attachments/assets/28c97287-2147-4cb8-9f25-31e97e81ef82)

### SITI UTILI
shodan
dnsdumpster

## RICOGNIZIONE ATTIVA

Mentre la ricognizione passiva raccoglie informazioni senza contatto diretto, la ricognizione attiva implica un’interazione con il target, come una visita o una connessione diretta al sistema, per esempio verificando se una porta SSH è aperta. Tuttavia, prima di procedere, è essenziale ottenere un'autorizzazione legale dal cliente.

Durante la ricognizione attiva, ogni connessione può lasciare tracce nei log del target, mostrando dati come l'indirizzo IP e la durata della connessione. Alcune connessioni possono sembrare normali, come la semplice navigazione web, che può essere sfruttata dal red team per passare inosservati.


### PING

Il comando **ping** è uno strumento utile per verificare la connettività di rete tra due sistemi. In modo semplice, invia un pacchetto a un sistema remoto e riceve una risposta, permettendo di concludere che il sistema remoto è attivo e la rete funziona correttamente. 
Ping utilizza pacchetti ICMP (Internet Control Message Protocol), in particolare il tipo 8 per l'echo e il tipo 0 per la risposta. 

Puoi utilizzare il comando `ping` seguito dall'indirizzo IP o dal nome host del target, come `ping MACHINE_IP` o `ping HOSTNAME`. Se non specifichi un conteggio, il ping continuerà fino a quando non lo interrompi con CTRL+C. In Linux, puoi usare `ping -c 10 MACHINE_IP` per inviare dieci pacchetti.


Quando il comando viene eseguito correttamente, **l'output mostrerà il numero di pacchetti trasmessi e ricevuti**, il tempo di round trip e la perdita di pacchetti. Ad esempio, se ricevi cinque risposte su cinque pacchetti trasmessi, significa che il sistema target è online.

Se il target è spento, il comando ping non riceverà risposte, mostrando un messaggio di "Destination Host Unreachable". Le cause della mancata risposta possono includere:

- Il computer di destinazione è spento o non reattivo.
- È scollegato dalla rete o c'è un dispositivo di rete difettoso.
- Un firewall blocca i pacchetti ICMP (come nel caso del firewall di Windows, che lo fa di default).
- Il tuo sistema è scollegato dalla rete.

### TRACEROUTE

Il comando **traceroute** consente di tracciare il percorso dei pacchetti dal tuo sistema a un altro host, identificando gli indirizzi IP dei router (o "hop") che i pacchetti attraversano. Questo è utile per determinare il numero di router tra il tuo sistema e l'host di destinazione. Poiché molti router utilizzano protocolli di routing dinamici, il percorso può cambiare nel tempo.

Su **Linux** e **macOS**, il comando è:
```
traceroute IP
```

Mentre su **Windows** è:
```
tracert IP
```

Traceroute utilizza il protocollo ICMP per rivelare gli indirizzi IP dei router, inviando pacchetti con un valore **TTL** (Time To Live) inizialmente impostato a 1. Quando un router riceve un pacchetto, decrementa il TTL; se il TTL arriva a 0, il pacchetto viene scartato e il router invia un messaggio ICMP di errore.

# BANNER GRABBING

Il banner grabbing è una tecnica utilizzata per ottenere informazioni su un servizio o un'applicazione in esecuzione su una macchina remota, connettendosi a una specifica porta di rete e "leggendo" il banner, ossia il messaggio iniziale che il servizio invia alla connessione. Questo banner può includere dettagli come il tipo di servizio, la versione dell’applicazione o del sistema operativo, e talvolta altre informazioni rilevanti.

USIAMO: NMAP (-sV), TELNET E NETCAT.

### NMAP

Senza conoscere quali porte sono aperte su un server, è impossibile attaccarlo con successo. La scansione delle porte è quindi un passaggio cruciale per ogni attacco, solitamente realizzato con uno strumento chiamato nmap. Nmap esegue diverse scansioni delle porte, determinandone lo stato: aperte, chiuse o filtrate (spesso da un firewall). Una volta identificate le porte aperte, possiamo scoprire i servizi associati, sia manualmente che con nmap stesso.


Quando si esegue una scansione delle porte con **Nmap**, esistono tre tipi di scansioni di base:

1. **Scansioni TCP Connect** (`-sT`)
2. **Scansioni SYN "Half-open"** (`-sS`)
3. **Scansioni UDP** (`-sU`)

Ci sono anche tipi di scansione meno comuni:

- **Scansioni TCP Null** (`-sN`)
- **Scansioni TCP FIN** (`-sF`)
- **Scansioni TCP Xmas** (`-sX`)

#### SCANSIONI TCP

Per comprendere le **scansioni TCP Connect** (`-sT`) di Nmap, è importante conoscere la procedura del **three-way handshake** del protocollo TCP. Questo processo avviene in tre fasi: 
1. Il terminale di connessione invia una richiesta TCP al server target con il flag SYN attivato.
2. Il server risponde con un pacchetto TCP contenente i flag SYN e ACK.
3. La nostra macchina completa la stretta di mano inviando un pacchetto TCP con il flag ACK.

Nelle scansioni TCP Connect, Nmap usa questo processo per ogni porta target. Se la porta è chiusa, il server risponde con un pacchetto di reset (RST), indicando a Nmap che la porta è chiusa. Se la porta è aperta, il server risponde con un pacchetto SYN/ACK, e Nmap segna la porta come aperta, completando la stretta di mano.

Esiste una terza possibilità: se una porta è aperta ma protetta da un firewall, quest’ultimo può semplicemente bloccare il pacchetto in entrata, e Nmap non riceve alcuna risposta. In questo caso, la porta viene considerata “filtrata”.

Alcuni firewall possono essere configurati per rispondere con un pacchetto RST per confondere le scansioni, rendendo difficile ottenere una lettura accurata delle porte.

#### SCANSIONI SYN

Come le scansioni TCP, le **scansioni SYN** (`-sS`) sono usate per analizzare le porte TCP di un target, ma funzionano in modo leggermente diverso. Chiamate anche "Half-open" o "Stealth" scans, queste scansioni interrompono il three way handshake inviando un pacchetto di reset (RST) dopo aver ricevuto il SYN/ACK dal server. 

Vantaggi delle scansioni SYN:

- Possono bypassare i vecchi sistemi di rilevamento intrusioni (IDS), poiché questi cercano una stretta di mano completa.
- Non vengono spesso registrate dalle applicazioni poiché non si stabilisce una connessione completa, migliorando la "discrezione".
- Essendo più rapide delle scansioni TCP complete, non completando la stretta di mano per ogni porta.

Svantaggi delle scansioni SYN:

- Necessitano di permessi sudo su Linux, in quanto richiedono la creazione di pacchetti grezzi, privilegio riservato all'utente root.
- Possono destabilizzare servizi poco stabili, cosa rischiosa in ambienti di produzione.

#### SCANSIONE UDP

Le connessioni **UDP** non avviano una connessione con il three way handshake. UDP invia pacchetti alla porta target senza conferma, rendendolo ideale per applicazioni che privilegiano la velocità (come la condivisione video), ma difficile da analizzare. In Nmap, una scansione UDP si avvia con l’opzione `-sU`.

Se Nmap invia un pacchetto a una porta UDP aperta, di norma non riceve risposta. Questo stato viene registrato come "open|filtered", indicando che la porta potrebbe essere aperta o filtrata da un firewall. Se Nmap riceve una risposta UDP (evento raro), la porta è segnata come aperta. In caso contrario, Nmap ritenta, e se non riceve ancora nulla, passa alla porta successiva.

Se la porta UDP è chiusa, la risposta sarà un pacchetto ICMP che segnala la porta come irraggiungibile, permettendo a Nmap di identificarla come chiusa.

Poiché è complesso verificare se una porta UDP è effettivamente aperta, le scansioni UDP sono molto più lente rispetto a quelle TCP (fino a 20 minuti per le prime 1000 porte). È consigliabile limitare la scansione con `--top-ports <numero>` per i 20 port UDP più comuni, accelerando il processo.

#### NULL, FIN XMAS

Le scansioni TCP **NULL**, **FIN** e **Xmas** sono meno comuni e vengono utilizzate per ottenere un livello di discrezione maggiore rispetto alle scansioni SYN. Di seguito un breve riepilogo di ciascuna:

- **NULL Scan** (`-sN`): invia una richiesta TCP senza alcun flag. Se la porta è chiusa, il sistema risponde con un pacchetto RST (reset).
  
- **FIN Scan** (`-sF`): invia un pacchetto TCP con il flag FIN, usato di solito per chiudere una connessione. Anche qui, se la porta è chiusa, si riceve un pacchetto RST.
  
- **Xmas Scan** (`-sX`): invia un pacchetto con i flag PSH, URG e FIN impostati, dando un'apparenza simile a un "albero di Natale" quando visualizzato su Wireshark. Il server risponde con RST se la porta è chiusa.

In tutte queste scansioni, se una porta è aperta non viene ricevuta risposta. Tuttavia, questo comportamento si verifica anche se la porta è protetta da un firewall, perciò le porte risultano semplicemente "open|filtered" (aperte o filtrate).

È importante notare che, sebbene lo standard RFC 793 preveda che i dispositivi rispondano con un pacchetto RST a porte chiuse e non rispondano a porte aperte, non tutti i sistemi seguono questa regola. Ad esempio, Windows e molti dispositivi Cisco rispondono con RST a ogni pacchetto TCP non valido, facendo risultare tutte le porte chiuse.

L’obiettivo principale di queste scansioni è evitare i firewall, poiché molti firewall bloccano i pacchetti SYN (che avviano le connessioni), mentre permettono i pacchetti senza SYN. Tuttavia, i sistemi IDS moderni sono in grado di rilevare queste tecniche, quindi non sempre garantiscono il 100% di successo.

#### NSE

Il **Nmap Scripting Engine (NSE)** è una potente estensione di Nmap che ne amplia notevolmente le funzionalità. Gli **NSE Scripts** sono scritti in **Lua** e possono essere utilizzati per una varietà di scopi, come scansionare vulnerabilità o automatizzare gli exploit per queste. NSE è particolarmente utile per il **reconnaissance**, ma è importante considerare la vastità della sua libreria di script.

Esistono diverse categorie di script, alcune delle più utili includono:

- **safe:** Non influenzano il target
- **intrusive:** Non sicuri, possono influenzare il target
- **vuln:** Scansionano per vulnerabilità
- **exploit:** Tentano di sfruttare una vulnerabilità
- **auth:** Tentano di bypassare l'autenticazione di servizi attivi (ad esempio, accedere a un server FTP in modo anonimo)
- **brute:** Tentano di eseguire un attacco **brute force** per ottenere le credenziali dei servizi in esecuzione
- **discovery:** Tentano di raccogliere ulteriori informazioni sulla rete interrogando i servizi in esecuzione (ad esempio, interrogare un server **SNMP**).

Esempi di scripts:

Questi due script fanno parte dell’Nmap Scripting Engine (NSE) e servono per raccogliere informazioni su una rete Windows, in particolare per quanto riguarda il protocollo SMB (Server Message Block), che è usato per la condivisione di file, stampanti e altre risorse in rete.

```
smb-enum-users
```
- **Scopo**: Questo script è utilizzato per elencare gli utenti presenti su un server SMB.
- **Funzionamento**: Esegue una query al server SMB per richiedere informazioni sugli account utente configurati. Ritorna una lista di utenti, con alcuni dettagli se sono disponibili (come i nomi degli utenti).
- **Utilità**: Serve a raccogliere informazioni di base sugli utenti di un dominio o di un server Windows, utile per comprendere chi potrebbe avere accesso a determinate risorse e per valutare possibili target in una rete.


```
smb-enum-shares
```
- **Scopo**: Questo script individua e riporta le condivisioni di rete (o "shares") accessibili tramite SMB.
- **Funzionamento**: Tenta di connettersi alle condivisioni di rete, elencando le risorse che il server SMB mette a disposizione per l’accesso remoto. Le condivisioni possono includere cartelle pubbliche, file condivisi o altre risorse.
- **Utilità**: Utile per vedere quali risorse di rete sono esposte e potenzialmente accessibili agli utenti. Avere visibilità sulle condivisioni può aiutare a valutare eventuali vulnerabilità, soprattutto se qualche share contiene dati sensibili o è configurato con permessi eccessivamente permissivi.

#### FIREWALL EVASION

Esiste una configurazione firewall molto comune che è fondamentale sapere come bypassare il firewall.

I **host Windows** con il firewall predefinito bloccano tutti i pacchetti **ICMP**. Questo può essere un problema, poiché Nmap, per impostazione predefinita, utilizza **ping** per verificare se un host è attivo. Se il firewall blocca i pacchetti ICMP, Nmap potrebbe considerare un host come "morto" e non eseguire scansioni su di esso.

Per aggirare questa configurazione, possiamo utilizzare l'opzione **-Pn**, che indica a Nmap di non eseguire il ping iniziale prima di scansionare l'host. Questo fa sì che Nmap consideri sempre l'host come attivo, ma può allungare i tempi di scansione, poiché continuerà a verificare ogni porta, anche se l'host è effettivamente "morto".

Se siamo direttamente sulla rete locale, Nmap può utilizzare **ARP requests** per determinare l'attività dell'host.

### Altri switch utili per aggirare i firewall includono:
- **-f**: frammenta i pacchetti in pezzi più piccoli, riducendo la probabilità che vengano rilevati da un firewall o IDS.
- **--mtu <numero>**: consente un maggiore controllo sulla dimensione dei pacchetti, specificando la dimensione massima di trasmissione, che deve essere un multiplo di 8.
- **--scan-delay <tempo>ms**: introduce un ritardo tra l'invio dei pacchetti. Utile per reti instabili e per evitare il trigger di firewall/IDS basati sul tempo.
- **--badsum**: genera un checksum non valido per i pacchetti. Sebbene i veri stack TCP/IP scartino questi pacchetti, i firewall potrebbero rispondere automaticamente senza verificarne il checksum, aiutando a rilevare la presenza di un firewall/IDS.

### TELNET

Il protocollo TELNET, sviluppato nel 1969, permette di comunicare con un sistema remoto tramite interfaccia a riga di comando (CLI) e utilizza la porta predefinita 23. Dal punto di vista della sicurezza, TELNET non cripta i dati, quindi invia in chiaro credenziali come username e password, rendendole vulnerabili. SSH (Secure SHell) è un’alternativa più sicura.

Nonostante TELNET sia spesso evitato per l’amministrazione remota, è ancora utile per altri scopi, come la connessione a servizi su TCP per raccogliere informazioni sul sistema remoto (banner grabbing). Utilizzando il comando 
```
telnet IP PORTA
``` 
è possibile connettersi a un servizio TCP e inviare messaggi, purché il servizio non richieda crittografia.

Per esempio, per scoprire informazioni su un server web che ascolta sulla porta 80, si può inviare il comando `GET / HTTP/1.1` per richiedere la pagina principale (o specificare altre pagine). È necessario anche specificare un host, es. `host: esempio`, e premere invio due volte. In risposta, si riceveranno dettagli sul server, inclusi il tipo e la versione (ad esempio `Server: nginx/1.6.2`), utili per identificare il software installato.

### NETCAT

Netcat, o nc, è uno strumento versatile per i pentester, poiché supporta sia i protocolli TCP che UDP. Può agire sia come client per connettersi a una porta in ascolto, sia come server che ascolta su una porta scelta. Questo lo rende ideale come client o server semplice su TCP o UDP.

È possibile usare Netcat per connettersi a un server e raccogliere informazioni, come il banner del servizio. Ad esempio, il comando:
``` 
nc IP_DEST PORTA
``` 

è simile a `telnet IP_DEST PORTA` e permette di connettersi a una porta e richiedere una pagina HTTP con `GET / HTTP/1.1`. Specificando `host: netcat`, si ottiene una risposta con i dettagli del server, come la versione (es. `Server: nginx/1.6.2`).

Netcat può anche ascoltare su una porta TCP. Usando `nc -vnlp 1234`, un sistema può aprire la porta 1234 e attendere connessioni. I parametri -v, -n, -l e -p specificano rispettivamente output verboso, nessuna risoluzione DNS, modalità ascolto e numero della porta. La modalità echo è ottenibile avviando Netcat su due terminali, uno lato server in ascolto e uno lato client in connessione. Qualsiasi messaggio inviato da un lato viene trasmesso e visualizzato dall'altro tramite il tunnel TCP.

![immagine](https://github.com/user-attachments/assets/5f17036d-bfe1-4a62-b82a-13be288d9927)


### TABELLA RIASSUNTIVA

![immagine](https://github.com/user-attachments/assets/e06a364c-873d-444a-9598-98abf8cccb96)

# ACCESSO

Dopo aver trovato le vulnerabilità, utilizzo degli exploit come il tool **Metasploit**.

### METASPLOIT

Metasploit è il framework di exploit più utilizzato, uno strumento potente che supporta tutte le fasi di un test di penetrazione, dalla raccolta di informazioni fino al post-exploit.

Esistono due versioni principali di Metasploit:<br>
	1. **Metasploit Pro**: versione commerciale con interfaccia grafica (GUI) che facilita l’automazione e la gestione delle attività. <br>
	2. **Metasploit Framework**: versione open-source utilizzabile tramite riga di comando, focalizzata sui test di penetrazione su distribuzioni Linux. <br>
Il Metasploit Framework comprende strumenti per raccolta di informazioni, scansione, exploit, sviluppo di exploit e post-exploit. È utilizzato soprattutto per i test di penetrazione, ma anche per la ricerca e sviluppo di vulnerabilità.

I componenti principali sono:<br>
	• **msfconsole**: interfaccia principale a riga di comando.<br>
	• **Moduli**: includono exploit, scanner, payload e altro.<br>
	• **Tool**: strumenti autonomi per ricerca e valutazione delle vulnerabilità, come msfvenom (coperto in questo modulo), pattern_create e pattern_offset (utili nello sviluppo di exploit, ma fuori dall’ambito del modulo).<br>

Concetti chiave:<br>
	• **Vulnerabilità**: una falla nel sistema che può esporre informazioni riservate o permettere l’esecuzione di codice non autorizzato.<br>
	• **Exploit**: pezzo di codice che sfrutta una vulnerabilità su un sistema target.<br>
	• **Payload**: codice che esegue un'azione desiderata (ad es. accesso al sistema target) una volta sfruttata una vulnerabilità.<br>

Principali Moduli di Metasploit:<br>
	1. **Auxiliary**: presenti all'interno del framework metasploit, include scanner, crawler e altri strumenti di supporto.<br>
	2. **Encoders**: codifica exploit e payload per evitare che un antivirus li riconosca. Gli antivirus nasati sulla firma hanno un database di minacce conosciute, se la firma corrisponde allora è un virus. 
	3. **Evasion**: tentano di eludere gli antivirus.<br>
	4. **Exploits**: organizzati per tipo di sistema target (es. Linux, Windows). <br>
	5. **NOPs**: utilizzati come riempimento per standardizzare la dimensione dei payload.<br>
	6. **Payloads**: il codice che viene lanciato, quello che permette poi di dare i comandi.<br>
		○ Adapters: converte i payload in vari formati.<br>
		○ Singles: payload auto-contenuti che non richiedono download aggiuntivi.<br>
		○ Stagers e Stages: i “Stagers” creano una connessione al sistema target e poi scaricano il payload (Stage) completo.<br>
	7. **Post**: moduli usati nella fase post-exploit, per attività di controllo e raccolta informazioni sul sistema compromesso.

#### COMANDI METASPLOIT



# POST EXPLOITATION
La fase di **post-exploitation** è il momento in cui, dopo essere riusciti a ottenere l'accesso a un sistema target, il penetration tester (o ethical hacker) sfrutta questo accesso per raccogliere informazioni più dettagliate e consolidare il controllo sul sistema. Lo scopo è sia quello di valutare il potenziale impatto di un’intrusione sia di ottenere informazioni che possono essere usate per proseguire l’attacco, espandendosi a altre parti della rete.

Ecco le principali attività di post-exploitation:

 1. **Raccolta di Informazioni Sensibili**
   - **File e Documenti Importanti**: Esplorare cartelle, leggere file di configurazione o documenti che potrebbero contenere informazioni sensibili (come dati aziendali, informazioni sui dipendenti, credenziali di accesso, ecc.).
   - **Credenziali**: Cercare password o chiavi di accesso salvate in file di testo o nel sistema, a volte memorizzate nelle impostazioni del browser, nelle applicazioni o nelle cache.

 2. **Privilege Escalation (Escalation dei Privilegi)**
   - L'obiettivo è ottenere privilegi più alti (come i permessi di amministratore/root), che permettono un controllo maggiore del sistema e l’accesso a più risorse.
   - La privilege escalation può avvenire sfruttando vulnerabilità locali, errori di configurazione, o utilizzando strumenti di ricerca automatizzata delle vulnerabilità.

 3. **Persistenza**
   - Stabilire un accesso continuato al sistema anche in caso di riavvio o disconnessione dell’utente.
   - Si utilizzano backdoor, script di startup, o modifiche nei servizi di sistema che riavviano il punto di accesso compromesso.

 4. **Movimento Laterale**
   - Cercare e compromettere altri sistemi nella stessa rete (o vicini), approfittando dei permessi acquisiti e della posizione interna al network.
   - Usare il sistema compromesso come base per attaccare altri dispositivi, applicazioni o server collegati.

 5. **Raccolta di Informazioni sulla Rete e sull’Infrastruttura**
   - Esplorare la rete interna, mappare l’infrastruttura, raccogliere dettagli sui dispositivi e rilevare altri punti di vulnerabilità.
   - Moduli come **scanner**, **sniffer** e **parser** di Metasploit possono essere utilizzati per ottenere informazioni sulla topologia di rete, sugli indirizzi IP interni e sui servizi in esecuzione.

 6. **Rimozione delle Tracce**
   - Pulizia dei log di sistema, rimozione dei file temporanei e cancellazione delle tracce lasciate per ridurre le possibilità di rilevamento.
   - Anche se in ambito etico il penetration tester generalmente documenta il processo senza rimuovere tracce, in un contesto reale l'attaccante cercherebbe di farlo.

In Metasploit, i **moduli post** sono quelli dedicati al post-exploitation. Si trovano sotto categorie come:
- **gather** per raccogliere informazioni;
- **escalation** per il privilege escalation;
- **networking** per muoversi lateralmente;
- **persistence** per mantenere l'accesso.

Questa fase è cruciale perché rappresenta il vero valore di un attacco: permette di massimizzare l'accesso ottenuto e capire in che misura una vulnerabilità compromette la sicurezza complessiva di una rete.

