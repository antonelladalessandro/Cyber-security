# DIFFERENZA TRA LAN E WAN

**LAN (Local Area Network)** 
È una rete locale che connette dispositivi vicini fisicamente, come in un edificio, appartamento, o ufficio. I dispositivi connessi alla LAN (come computer, telefoni e tablet) comunicano tra loro all'interno della rete locale. Ogni dispositivo deve essere identificato tramite un indirizzo IP univoco all'interno della rete, assegnato dal router. Gli indirizzi IP sono unici per ogni dispositivo nella LAN e possono essere visualizzati tramite comandi come `ifconfig` (su Mac) o `ipconfig` (su Windows).

**WAN (Wide Area Network)**: È una rete estesa che copre aree geografiche ampie e consente di connettersi a Internet. Il WAN si trova all'esterno del router e permette ai dispositivi della LAN di accedere a risorse esterne, come siti web o server remoti.

# IP

Ogni dispositivo in una rete ha un indirizzo IP che può essere **privato** o **pubblico**:
  - **IP privato**: Visibile solo all'interno della LAN e non accessibile dall'esterno. Questo tipo di IP è utilizzato per la comunicazione tra dispositivi interni alla stessa rete locale.
  - **IP pubblico**: Visibile su Internet, quindi accessibile a chiunque sia connesso alla WAN. È univoco e assegnato dal provider di servizi internet (ISP). 

Gli indirizzi IP sono formati da quattro blocchi di numeri (IPv4) separati da punti, e ogni blocco varia tra 0 e 255 (IPv4).


**Tipi di IP pubblico**:

- **Dinamico**: Cambia periodicamente, generalmente assegnato dal provider a ogni nuova connessione o sessione. È meno stabile ma solitamente più economico.
- **Statico**: Rimane fisso e non cambia, rendendo più semplice la configurazione di servizi che richiedono un IP costante.

**Protocollo IP**

Il **protocollo IP (Internet Protocol)** è l'insieme di regole che definisce come i dati sono inviati e ricevuti su una rete. Identifica ogni dispositivo connesso tramite un indirizzo IP. Le versioni più comuni sono:
- **IPv4**: Usa indirizzi a 32 bit, suddivisi in quattro blocchi numerici tra 0 e 255.
- **IPv6**: Una versione avanzata con indirizzi a 128 bit, utilizzata per soddisfare la crescente domanda di nuovi indirizzi IP.


# NAT (Network Address Translation) 
Il NAT è una tecnica utilizzata per trasformare gli indirizzi IP privati di una rete locale in indirizzi IP pubblici, permettendo ai dispositivi all'interno di una LAN di comunicare con l'esterno (Internet) e viceversa. Il NAT funziona come una sorta di tabella che tiene traccia delle richieste e degli indirizzi IP dei dispositivi interni, traducendoli in un unico indirizzo pubblico visibile su Internet. Questo consente di risparmiare indirizzi IP pubblici e fornisce un livello base di sicurezza, in quanto nasconde gli indirizzi privati dietro l’IP pubblico.

# Firewall
Un firewall è un sistema di sicurezza che può essere implementato sia a livello software che hardware. La sua funzione è filtrare il traffico in entrata e in uscita, decidendo cosa bloccare e cosa consentire in base a regole predefinite. I firewall proteggono la rete da accessi non autorizzati e attacchi informatici, regolando quali connessioni sono consentite o bloccate.

# Porte
Le porte sono "sottoindirizzi" associati agli indirizzi IP e rappresentano canali specifici per la trasmissione e ricezione di dati. Ogni porta è identificata da un numero univoco (da 0 a 65535) e associata a un protocollo o servizio. Per comunicare con un servizio specifico su un dispositivo, è necessario conoscere sia l'indirizzo IP sia il numero di porta. Alcuni numeri di porta sono riservati a servizi ben noti, rendendo le comunicazioni standardizzate.

### Porte più comuni
- **80**: HTTP (traffico web non sicuro)
- **443**: HTTPS (traffico web sicuro, certificato di sicurezza)
- **22**: SSH (accesso sicuro alla shell)
- **21**: FTP (trasferimento di file)
- **25**: SMTP (posta elettronica in uscita)
- **587**: SMTP (altra porta per posta elettronica in uscita, sicura)
- **110**: POP3 (posta elettronica in entrata)
- **53**: DNS (risoluzione dei nomi di dominio)
- **3389**: RDP (Remote Desktop Protocol, accesso remoto al desktop di un altro computer)

**Well Known Ports**: da 1 a 1024, riservate per protocolli e servizi comuni (ad esempio, HTTP, FTP, DNS).

Ogni servizio utilizza porte specifiche per stabilire e mantenere connessioni. Ad esempio, per un server web sono necessarie le porte **80** (HTTP) e **443** (HTTPS) per garantire l’accesso alle pagine web, mentre altre porte (come **22** per SSH) permettono l’accesso sicuro remoto alla macchina.

### Port Forwarding
Il Port Forwarding una tecnica di rete che permette il trasferimento di dati tra dispositivi tramite una porta di comunicazione specifica. Viene utilizzata per consentire a utenti esterni di raggiungere un host con un indirizzo IP privato all'interno di una rete locale, utilizzando una porta specifica sull'IP pubblico del router della rete.

In altre parole, **il port forwarding consente di indirizzare traffico esterno verso un dispositivo o servizio specifico all'interno della rete**. Immagina di avere un dispositivo connesso al router di casa che esegue un servizio (come un server di gioco o una videocamera di sorveglianza) e a cui vuoi accedere dall'esterno, tramite internet. Normalmente, il router blocca le connessioni esterne per proteggere la rete, ma con il port forwarding puoi "aprire una porta" specifica, istruisce il router a reindirizzare tutto il traffico che arriva su quella porta verso un dispositivo specifico nella rete interna.

In pratica, il router agisce come un ponte, ricevendo le informazioni dall'esterno e reindirizzandole verso il dispositivo interno. Questo permette di accedere in modo sicuro e diretto a servizi interni alla rete, bypassando le limitazioni del firewall del router per la porta specifica.

# DHCP

Esistono delle macchine collegate nella rete locale alle quale viene assegnato un indirizzo ip . Chi assegna questi indirizzo è il meccanismo DHCP (Dynamic host configuration protocol - protocollo che assegna indirizzi alle macchine nella rete locale) e lo fa attraverso il router.

**DORA** (discover, offer, request, acknowledge): Quando un dispositivo (client) si connette a una rete, segue un processo DHCP a quattro fasi, noto anche come **DORA** : <br>
	1. Discover: Il client invia un messaggio broadcast (a tutti i dispositivi nella rete) per cercare server DHCP disponibili <br>
	2. Offer: I server DHCP che ricevono il messaggio Discover rispondono con un messaggio DHCP Offer, che include un indirizzo IP che il server è disposto ad assegnare al client, oltre ad altre informazioni di configurazione come il lease time (il tempo per cui l’indirizzo può essere utilizzato), il gateway predefinito, e i server DNS. <br>
	1. Request: Il client riceve una o più offerte e sceglie una. Poi invia un messaggio broadcast DHCP Request per informare tutti i server DHCP sulla scelta dell’offerta accettata e per richiedere l’indirizzo IP proposto. <br>
	2. Acknowledge: Il server DHCP selezionato risponde con un messaggio DHCP Acknowledge, confermando l’assegnazione dell’indirizzo IP e di altri parametri di configurazione al client. Se invece avviene un problema, il server invierà un messaggio DHCP Nak (negative acknowledgment), e il client dovrà iniziare nuovamente il processo. <br>


**Broadcast**: comando inviato a tutti quelli presenti nella rete

# MAC ADDRESS

In informatica, un **indirizzo MAC** (*Media Access Control*), noto anche come "indirizzo fisico" o "indirizzo Ethernet", è un identificatore univoco di 48 bit assegnato a ogni dispositivo di rete conforme allo standard Ethernet. Questo codice è composto da 12 cifre esadecimali, solitamente divise in coppie (ad esempio, 00:1A:2B:3C:4D:5E).

**Caratteristiche principali di un indirizzo MAC**
- **Univocità:** Ogni scheda di rete ha un indirizzo MAC che la identifica in modo univoco all'interno della rete locale (LAN).
- **Struttura:** Gli indirizzi MAC sono composti da due parti principali:
  -  le prime tre coppie di cifre identificano il produttore del dispositivo.
  -  le ultime tre coppie di cifre sono un identificativo specifico assegnato al dispositivo.
- **Visibilità:** Un indirizzo MAC è visibile solo all'interno della **rete locale**. Questo aiuta a preservare la sicurezza, evitando che gli indirizzi fisici siano esposti pubblicamente.

**Sicurezza e Spoofing dell’indirizzo MAC**
Pur essendo unico per ciascun dispositivo, l'indirizzo MAC può essere "spoofato" o falsificato, ovvero un dispositivo può modificare il proprio MAC per far credere alla rete di essere un altro dispositivo. Questo fenomeno è noto come **MAC spoofing** e può avere implicazioni di sicurezza:
  - **Accessi non autorizzati:** Alcuni sistemi di sicurezza, come firewall e access point, utilizzano indirizzi MAC per consentire o negare l'accesso alla rete. Se un dispositivo riesce a falsificare l’indirizzo MAC di un altro dispositivo autorizzato, potrebbe ottenere accesso a risorse altrimenti bloccate.
  - **Limitazioni del MAC Spoofing:** Questa tecnica funziona solo all'interno della LAN (rete locale), poiché gli indirizzi MAC non sono visibili al di fuori di essa.

---

# TCP e UDP 

TCP e UDP sono due protocolli fondamentali utilizzati per la trasmissione dei dati in rete, ciascuno con caratteristiche e utilizzi differenti:

### **TCP (Transmission Control Protocol):**
- **Connessione affidabile:** TCP è un protocollo orientato alla connessione. Prima di inviare i dati, stabilisce una connessione tra i dispositivi attraverso il processo chiamato *three-way handshake*.
- **Affidabilità:** Garantisce che i dati arrivino a destinazione nell'ordine giusto. Se un pacchetto viene perso o danneggiato, TCP lo rileva e lo ritrasmette.
- **Controllo di flusso:** Gestisce la velocità di trasmissione per evitare sovraccarichi della rete o del dispositivo ricevente.
- **Uso comune:** È utilizzato per applicazioni che richiedono affidabilità, come la navigazione web (HTTP/HTTPS), l'invio di email (SMTP), e il trasferimento di file (FTP).

### **UDP (User Datagram Protocol):**
- **Connessione non affidabile:** UDP è un protocollo senza connessione. Non stabilisce una connessione prima di inviare i dati e non garantisce che questi arrivino a destinazione.
- **Velocità:** Essendo un protocollo più semplice rispetto a TCP, UDP è più veloce, ma non offre meccanismi di controllo degli errori. Se i dati vengono persi o arrivano fuori ordine, non vengono corretti.
- **Uso comune:** Viene utilizzato in applicazioni che privilegiano la velocità e tollerano la perdita di alcuni dati, come lo streaming video, le chiamate VoIP, e i giochi online.

 **In breve:**
- **TCP:** Usato quando l'affidabilità è necessaria.
- **UDP:** Usato quando la velocità è prioritaria e si può tollerare la perdita di dati.

**Esempio TCP:** Quando navighi su un sito web, TCP è essenziale perché è importante che tutte le parti della pagina arrivino correttamente.  
**Esempio UDP:** Quando guardi un video in streaming o giochi online, UDP è usato perché è più importante che l'azione sia veloce, anche se qualche frammento di video o gioco potrebbe andare perso.

**In pratica:**  
- **TCP =** come una conversazione ordinata e attenta.  
- **UDP =** come inviare rapidamente dei messaggi senza preoccuparsi troppo di eventuali mancanze.

### **TCP Three-Way Handshake**

Il **Three-Way Handshake** è il processo con cui due dispositivi (un client e un server) stabiliscono una connessione TCP. Ecco come funziona:

1. **SYN (Synchronize):** Il client invia un messaggio SYN al server per iniziare una connessione. È come dire: "Ciao, voglio parlare con te, sei disponibile?"
2. **SYN-ACK (Acknowledge):** Il server risponde con un messaggio SYN-ACK per indicare che è pronto a comunicare. "Ciao, ho ricevuto il tuo messaggio e sono pronto, sei pronto anche tu?"
3. **ACK (Acknowledge):** Il client risponde con un messaggio ACK, confermando che la connessione è stabilita. "Perfetto, ho ricevuto la tua risposta, possiamo iniziare."

**In sintesi:**
- **SYN:** "Posso parlare?"
- **SYN-ACK:** "Sì, possiamo parlare, sei pronto?"
- **ACK:** "Sì, sono pronto. Iniziamo!"

Dopo questo scambio, la connessione è stabilita e possono iniziare a scambiarsi dati.

---

### **TCP Wrapper**

**TCP Wrapper** è uno strumento di sicurezza usato nei sistemi Unix-like (Linux) per limitare l'accesso ai servizi di rete basati su TCP. Funziona come un livello di protezione tra i servizi di rete (es. SSH, FTP) e le connessioni esterne. Gli amministratori di sistema possono configurare regole per determinare quali host sono autorizzati ad accedere ai servizi di rete.

---

### **Flag dei pacchetti TCP**

In un pacchetto TCP, i flag sono utilizzati per controllare e gestire la comunicazione. I principali flag sono:

- **URG (Urgente):** Indica che i dati nel pacchetto devono essere trattati come urgenti e processati immediatamente.
- **ACK (Acknowledge):** Conferma la ricezione di segmenti.
- **PSH (Push):** Indica che i dati devono essere immediatamente inoltrati all'applicazione.
- **RST (Reset):** Resetta una connessione, interrompendo la comunicazione.
- **SYN (Synchronize):** Utilizzato per iniziare il processo di handshake TCP.
- **FIN (Finish):** Indica la fine di una connessione TCP, segnando che la comunicazione è terminata.

![immagine](https://github.com/user-attachments/assets/5ece7a05-55a8-4a6d-a6b8-053b62b1af69)

---

### **DNS (Domain Name System)**

Il **DNS (Domain Name System)** è un sistema che traduce i nomi di dominio in indirizzi IP, permettendo ai computer di comunicare tra loro. Ad esempio, quando digiti un URL come **www.google.it**, il DNS converte quel nome in un indirizzo IP (ad esempio, 172.217.9.142) che viene utilizzato per localizzare il sito web.

#### **Funzionamento del DNS:**
Quando digiti un nome di dominio, il tuo dispositivo invia una richiesta per scoprire l'indirizzo IP del sito:
1. Se il DNS non è stato configurato manualmente, la richiesta viene inviata al server DNS del provider (Internet Service Provider - ISP).
2. Il server DNS del provider può interrogare altri server DNS, in particolare quelli autoritativi, che contengono la risposta finale.

Puoi **modificare il DNS provider** (ad esempio, utilizzando OpenDNS o Google DNS) per ricevere risposte direttamente dai server autonomi.

#### **Porta DNS:** 
Il DNS opera sulla **porta 53**.

#### **Comandi Utili per il DNS:**
- **dig:** Permette di ottenere informazioni dettagliate, come gli indirizzi IP associati a un nome di dominio.
- **host:** Fornisce informazioni di base, come gli indirizzi IPv4/IPv6, e i server di posta elettronica (MX).

![immagine](https://github.com/user-attachments/assets/fabc6af5-fb55-43f1-9318-7196ab443dac)


**TLD (Top-Level Domain)**
Il **TLD** è la parte finale di un nome di dominio (es. **.com**, **.org**, **.it**). Esistono due tipi principali di TLD:
- **gTLD (Generic TLD):** Rappresentano un'area di interesse generico (es. **.com**, **.org**, **.edu**).
- **ccTLD (Country Code TLD):** Rappresentano aree geografiche (es. **.uk** per il Regno Unito, **.ca** per il Canada).

Con la crescente domanda, sono stati introdotti nuovi gTLD come **.club**, **.online**, **.website**, ecc.

**Dominio di Secondo Livello**
Il **Dominio di Secondo Livello** è la parte di un dominio che precede il TLD. Ad esempio, in **tryhackme.com**, **tryhackme** è il dominio di secondo livello. Quando registri un dominio, questo è limitato a **63 caratteri** e può contenere solo lettere (a-z), numeri (0-9), e trattini (non possono iniziare o terminare con trattini o averne consecutivi).

**Sottodominio**
Un **sottodominio** si trova a sinistra del dominio di secondo livello, separato da un punto. Ad esempio, in **admin.tryhackme.com**, **admin** è il sottodominio. Puoi creare più sottodomini (es. **jupiter.servers.tryhackme.com**) fino a un limite di **253 caratteri** per il nome completo.

### **Tipi di Record DNS**
Il DNS non si limita solo alla risoluzione degli indirizzi web. Esistono diversi tipi di record DNS:

- **Record A:** Risolvono gli indirizzi IPv4 (es. **104.26.10.229**).
- **Record AAAA:** Risolvono gli indirizzi IPv6 (es. **2606:4700:20::681a**).
- **Record CNAME:** Risolvono un nome di dominio a un altro (es. **store.tryhackme.com** potrebbe puntare a **shops.shopify.com**).
  - Funzione: crea alias per altri domini. Facilita la gestione e l'utilizzo di servizi esterni.
- **Record MX:** Risolvono i server di posta elettronica associati al dominio (es. **alt1.aspmx.l.google.com**).
  - Utilizzato per determinare dove inviare la posta elettronica.
- **Record TXT:** Permettono di memorizzare dati testuali. Utilizzati per la verifica del dominio e la protezione contro lo spam.

**Comandi DNS:**
- **nslookup:** Permette di ottenere l'indirizzo IP di un sito web.
  - Per ottenere i record MX: **nslookup -type=mx dominio.com**.

#### **DNS Inverso**
Il **DNS inverso** è il processo opposto rispetto al DNS normale: dato un indirizzo IP, risolve il nome di dominio associato. È utile per identificare l'origine di una connessione o per verificare se un IP corrisponde a un dominio specifico.

#### **Cache DNS**
La **cache DNS** è una memoria temporanea che conserva le risposte alle richieste DNS recenti. Quando visiti un sito, il tuo dispositivo memorizza l'indirizzo IP per velocizzare le successive richieste:
1. **Prima richiesta:** Il dispositivo chiede al server DNS l'indirizzo IP.
2. **Consultazione della cache:** Se il sito è già stato visitato, il dispositivo utilizza l'indirizzo salvato.
3. **Scadenza:** I record DNS hanno un tempo di vita (TTL). Quando scade, la cache si aggiorna.

**Tipi di Cache DNS:**
- **Cache locale:** Memorizzata sul dispositivo dell'utente.
- **Cache del router:** Memorizzata nel router per velocizzare l'accesso per tutta la rete domestica.
- **Cache dei server DNS:** Memorizzata sui server dei provider di rete, riducendo la necessità di interrogare server DNS autoritativi.

**Vantaggi della Cache DNS:**
- **Velocità:** Riduce il tempo di caricamento dei siti web già visitati.
- **Riduzione del traffico:** Minima la necessità di inviare richieste DNS.
- **Affidabilità:** Se un server DNS non è disponibile, la cache permette di accedere ai siti precedentemente visitati.

**Pulizia della Cache DNS:**
Se riscontri problemi nella navigazione (ad esempio, siti non caricati correttamente), è possibile cancellare la cache DNS con i seguenti comandi:
- **Su Windows:** `ipconfig /flushdns`
- **Su macOS:** `sudo killall -HUP mDNSResponder`
- **Su Linux:** `sudo systemd-resolve --flush-caches` o riavviare il servizio DNS.


---

### **Virtual Private Network (VPN)**

Una **VPN (Virtual Private Network)** è un sistema che permette di navigare su internet in modo sicuro e anonimo. Usare una VPN è come attraversare un tunnel privato: il tuo traffico viene criptato e instradato attraverso un server remoto, proteggendo la tua identità e rendendo più difficile tracciare la tua posizione o attività online.

**Come Funziona una VPN:**
1. **Connessione Sicura**: Una VPN cripta i dati che viaggiano tra il tuo dispositivo e il server VPN, rendendo questi dati illeggibili a chiunque tenti di intercettarli (come hacker o provider internet). Questo è particolarmente utile quando ti colleghi a reti Wi-Fi pubbliche, spesso più vulnerabili ad attacchi.
   
2. **Nascondi il tuo IP**: Una VPN nasconde il tuo indirizzo IP, sostituendolo con quello del server VPN. In questo modo, il sito o il servizio che stai visitando vedrà l'IP del server VPN (che puoi scegliere in un altro Paese), non il tuo vero indirizzo IP, nascondendo quindi la tua reale posizione geografica.

3. **Accesso a Contenuti Bloccati**: Con una VPN puoi accedere a siti o servizi bloccati nella tua area geografica. Collegandoti a un server situato in un Paese dove tali contenuti sono accessibili, la VPN ti permette di aggirare restrizioni geografiche.

**Perché Usare una VPN:**
- **Privacy**: Nasconde il tuo indirizzo IP e cifra i dati, proteggendo la tua identità online e impedendo a siti e servizi di tracciare le tue attività e posizione.
- **Sicurezza**: Protegge il traffico internet da intercettazioni, fondamentale per connessioni su reti pubbliche, come Wi-Fi di hotel, aeroporti e caffetterie.
- **Accesso a Contenuti Globali**: Una VPN consente di collegarsi a server in vari Paesi, permettendo di accedere a contenuti disponibili solo in alcune regioni (come piattaforme di streaming).

In Sintesi: Una VPN è uno strumento che migliora sicurezza e privacy online, creando un “tunnel” virtuale per navigare in modo sicuro e mascherando la tua posizione. È una soluzione accessibile e facile da usare per aggirare restrizioni geografiche e garantire una navigazione più privata.



# SMB

**SMB** (Server Message Block Protocol) è un protocollo di comunicazione client-server utilizzato per condividere l'accesso a file, stampanti, porte seriali e altre risorse su una rete. I server mettono a disposizione file system e altre risorse (come stampanti e API) per i client sulla rete, i quali possono accedere a queste risorse condivise, oltre che ai propri dischi locali.
L’SMB è un protocollo di richiesta-risposta, in cui vengono trasmessi più messaggi tra client e server per stabilire una connessione.
Una volta stabilita la connessione, i client inviano comandi (chiamati SMB) al server per accedere a file condivisi, aprire, leggere e scrivere file, e svolgere tutte le operazioni che si desidera fare con un file system, ma tramite la rete.

Tutti i sistemi operativi Microsoft Windows, a partire da Windows 95, includono il supporto per il protocollo SMB sia lato client che server. Inoltre, Samba, un server open-source che supporta il protocollo SMB, è stato rilasciato per i sistemi Unix.

**PORTE**: 139 e 445 (si chiamano netBIOS: 139 138 137, se trovo queste porte ho un computer di tipo windows)


### Enumerazione
L'enumerazione è il processo di raccolta di informazioni su un target per identificare potenziali attacchi e supportare l'exploitazione. Questo processo è fondamentale per il successo di un attacco, poiché permette di risparmiare tempo evitando exploit inefficaci o che possono bloccare il sistema. L'enumerazione può fornire informazioni utili all'attaccante come nomi utente, password, dati di rete, nomi di host, dati delle applicazioni e servizi.

### SMB
In un server ci sono spesso drive SMB condivisi che possono essere utilizzati per visualizzare o trasferire file. Gli SMB condivisi sono spesso il punto di partenza di un attacco, perché contengono informazioni sensibili accessibili tramite questi drive.

### Port Scanning
Il primo passo dell'enumerazione è condurre uno scan delle porte per scoprire servizi, applicazioni, struttura e sistema operativo della macchina target. Se non hai già familiarità con il port scanning, ti consiglio di dare un'occhiata alla sezione su Nmap.

### Enum4Linux
Enum4linux è uno strumento utilizzato per enumerare le condivisioni SMB su sistemi Windows e Linux. Funziona come una raccolta di strumenti Samba e consente di estrarre rapidamente informazioni SMB dal target.
La sintassi di Enum4Linux è semplice: enum4linux [opzioni] ip

**TAG E FUNZIONALITÀ**
	• -U — ottiene la lista utenti
	• -M — ottiene la lista delle macchine
	• -N — ottiene il dump della lista nomi (differente da -U e -M)
	• -S — ottiene la lista delle condivisioni
	• -P — ottiene informazioni sulla policy password
	• -G — ottiene la lista dei gruppi e dei membri
 	• -a — esegue tutte le opzioni sopra (enumerazione completa di base)

# WEB APPLICATI0N

Un'applicazione web può essere paragonata a un pianeta: come un astronauta esplora la superficie di un pianeta, un utente esplora una web app tramite un browser. La “superficie” rappresenta il front end, ciò che l’utente può vedere e con cui interagire, mentre il back end è il “sottosuolo” che svolge compiti invisibili ma essenziali per far funzionare l’app.

### Front End

Il front end è la parte visibile e interattiva dell'app, realizzata con:

- **HTML**: È il “DNA di base” della pagina web, dando istruzioni al browser su cosa mostrare.
- **CSS**: Aggiunge stile, colori e layout, come le caratteristiche visive di un organismo.
- **JavaScript**: Rende le pagine dinamiche, simile al “cervello” che consente agli elementi di reagire agli input dell’utente.

### Back End

Il back end comprende elementi nascosti ma cruciali:

- **Database**: Come una libreria del pianeta, conserva e gestisce informazioni per l’app.
- **Infrastruttura**: Include server e reti che supportano il funzionamento del sito, come strade e risorse del pianeta.
- **WAF (Web Application Firewall)**: Protegge il sito da minacce esterne, simile all'atmosfera del pianeta che scherma dai raggi dannosi.

## URL 

Un URL (Uniform Resource Locator) è l’indirizzo web che consente di accedere a contenuti online, come pagine web, video o immagini, guidando il browser alla risorsa corretta. È composto da varie parti:


1. **Schema (Protocollo)**: Specifica il protocollo usato per accedere alla risorsa, come HTTP o HTTPS, quest'ultimo crittografato per una maggiore sicurezza.

2. **Utente**: In casi rari, l’URL può includere informazioni di accesso come il nome utente, ma è sconsigliato per motivi di sicurezza.

3. **Host/Dominio**: È la parte principale dell’URL che identifica il sito. I domini sono unici e registrati attraverso enti specifici. Occorre fare attenzione a nomi di dominio falsi o simili (typosquatting), usati per truffe o phishing.

4. **Porta**: Indica il numero di porta per accedere ai servizi del server. Le porte più comuni sono la 80 per HTTP e la 443 per HTTPS.

5. **Percorso (Path)**: Specifica il file o la pagina da raggiungere sul server. Questo percorso deve essere sicuro per limitare l’accesso a risorse sensibili.

6. **Query String**: È la parte che inizia con il punto interrogativo (?) e può includere termini di ricerca o input di moduli. Deve essere trattata in modo sicuro per evitare attacchi, come iniezioni di codice.

7. **Fragmento**: Inizia con il simbolo “#” e punta a una sezione specifica della pagina, come un titolo o una tabella. Anche i frammenti devono essere gestiti in modo sicuro per prevenire attacchi.

### Codici di Stato e Categorie

I codici di stato si dividono in cinque categorie principali:

- **Risposte Informative** (100-199): indicano che il server ha ricevuto parte della richiesta e sta aspettando il resto.
- **Risposte di Successo** (200-299): indicano che la richiesta è stata processata con successo e i dati richiesti sono stati inviati.
- **Messaggi di Redirezione** (300-399): indicano che la risorsa è stata spostata e includono spesso un nuovo URL.
- **Errori del Client** (400-499): segnalano un problema con la richiesta, come un URL sbagliato o mancanza di autenticazione.
- **Errori del Server** (500-599): indicano che il server ha riscontrato un problema durante l'elaborazione della richiesta.
