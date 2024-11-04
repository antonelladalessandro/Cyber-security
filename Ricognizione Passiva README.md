# RICOGNIZIONE PASSIVA

La **ricognizione** (o "recon") è una fase preliminare per raccogliere informazioni su un bersaglio, e rappresenta il primo passo della "Unified Kill Chain" per ottenere un punto d'accesso iniziale. La ricognizione si divide in:

1. Ricognizione Passiva: si basa su informazioni pubblicamente accessibili senza interazione diretta con il bersaglio, come consultare record DNS pubblici di un dominio o leggere articoli sul target. <br>
2. Ricognizione Attiva: comporta un’interazione diretta con il bersaglio, come connettersi ai server dell'azienda o simulare un contatto per ottenere informazioni. Dato il suo carattere invasivo, la ricognizione attiva può portare a problemi legali senza un’autorizzazione formale. <br>



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
