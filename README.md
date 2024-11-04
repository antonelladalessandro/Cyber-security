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

