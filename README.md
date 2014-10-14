Client - Server con Glassfish
=================
Configurazione minimale di due macchine virtuali Ubuntu.  
La prima e' un semplice client con Java 7. La seconda un server con Glassfish installato come un servizio.

Configurazione:

 * OS: Ubuntu LTS 10.2
 * Java JDK 7
 * Latest Open JDK
 * GlassFish V4 (installato come un servizio)
 
Configurazione di rete:

 * Client:  192.168.50.101
 * Server:  192.168.50.102	 
 

Vagrant
-------
Vagrant e' un sistema usato per creare e configurare macchine virtuali.  Per usare questo progetto e' necessario avere: 

 * download [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (used by Vagrant)
 * download [Vagrant](http://downloads.vagrantup.com/)

Avvio ed uso della macchina virtuale
----------------------------------
1. Fare il download che software appena menzionato (VirtualBox e Vagrant).
2. Clonare questo repository.
3. Lanciare il comando ```vagrant up``` dal repository che avete clonato
4. Dopo alcuni minuti la macchina virtuale verra' creata e avviata con Glassfish come servizio
5. E' possibile accedere nella macchina virtuale del server mediante ul comando ```vagrant ssh server```
6. E' possibile accedere nella macchina virtuale del client mediante ul comando ```vagrant ssh client```

**Accesso al server:**

 * Glassfish console: http://localhost:4848
 * Default domain: http://localhost:8080
 

**Comandi Glassfish:**

 * Start     sudo /etc/init.d/glassfish start
 * Stop      sudo /etc/init.d/glassfish stop
 * Restart   sudo /etc/init.d/glassfish restart
 
 
 **Info Aggiuntive**
 
 *L'installazione di Glassfish si trova nella cartella /opt
 *Per raggiungerla, dopo aver lanciato il comando ```vagrant ssh``` bisogna digitare direttamente  ```cd /opt/glassfish4/bin```
 *Successivamente, per modificare la configurazione, usare  ```asadmin``` in questo modo ```./asadmin COMANDO```
 
 #http://twostepsaheadtoday.wordpress.com/2014/02/07/glassfish-4-admin-console-login-problem/