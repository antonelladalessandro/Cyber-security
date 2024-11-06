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

### Porte più comuni:
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
