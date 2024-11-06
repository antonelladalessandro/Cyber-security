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

