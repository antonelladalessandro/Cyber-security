# WHOIS

WHOIS è un protocollo di richiesta e risposta che segue la specifica RFC 3912. Un server WHOIS ascolta sulla porta TCP 43 le richieste in arrivo. Il registrar di un dominio è responsabile della gestione dei record WHOIS per i nomi di dominio che sta affittando. Il server WHOIS risponde con varie informazioni relative al dominio richiesto. Di particolare interesse, possiamo scoprire: 

• Registrar: tramite quale registrar è stato registrato il nome di dominio?

• Informazioni di contatto del registrante: nome, organizzazione, indirizzo, telefono, e altro (a meno che non siano nascosti tramite un servizio di privacy).

• Date di creazione, aggiornamento e scadenza: quando è stato registrato per la prima volta il nome di dominio? Quando è stato aggiornato l'ultima volta? E quando deve essere rinnovato?

• Name Server: a quale server chiedere di risolvere il nome di dominio?
 
Per ottenere queste informazioni, dobbiamo usare un client whois o un servizio online. Molti servizi online forniscono informazioni WHOIS; tuttavia, è generalmente più veloce e conveniente usare il client whois locale. Puoi facilmente accedere al tuo client whois tramite terminale. La sintassi è:

```
whois NOME_DOMINIO
```

# NSLOOKUP

Per trovare l'indirizzo IP di un nome di dominio usando nslookup (Name Server Look Up). È necessario eseguire il comando nslookup:

```
nslookup NOME_DOMINIO
```

Per aggiungere il record:

```
 nslookup -type=RECORD NOME_DOMINIO
```
