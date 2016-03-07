---
id: 236
title: Installare Apache2 PHP e MySql su Ubuntu (LAMP)
date: 2012-03-18T13:55:04+00:00
author: Antonio Lanzolla
layout: post
guid: http://188.226.216.54/?p=236
permalink: /installare-apache2-php-e-mysql-su-ubuntu-lamp/
wp_review_location:
  - top
wp_review_desc_title:
  - Riassunto
wp_review_color:
  - '#FFCA00'
wp_review_fontcolor:
  - '#fff'
wp_review_bgcolor1:
  - '#151515'
wp_review_bgcolor2:
  - '#151515'
wp_review_bordercolor:
  - '#151515'
dsq_thread_id:
  - 2148559394
twitter-text:
  - 'Installare #Apache2 #PHP e #MySql su #Ubuntu'
twitter-hashtag:
  - '#apache #lamp'
categories:
  - Programmazione
tags:
  - apache
  - database
  - lamp
  - mysql
  - php
  - ubuntu
---
In questo articolo vedremo come installare e predisporre un ambiente di sviluppo **LAMP**, quindi un Web Server <a title="Apache2" href="http://httpd.apache.org/" target="_blank">Apache2</a> con il supporto a <a title="PHP" href="http://www.php.net/" target="_blank">PHP</a> e <a title="MySQL" href="http://www.mysql.com/" target="_blank">MySql</a> su <a title="Ubuntu" href="http://www.ubuntu.com/" target="_blank">Ubuntu</a> 11.10.
  
**LAMP** è l’acronimo di **L**inux **A**pache **M**ySql **P**HP.

## Premessa

Assumeremo di avere come host name _server.esempio.com_ con un indirizzo IP _192.168.0.11_. Se la tua configurazione è differente ti basterà sostituire i parametri con i tuoi.
  
Sarà necessario lanciare tutti i comandi a terminale con i permessi di _root_, quindi da _Terminale_ come prima cosa facciamo

    sudo su
    

## Installare MySQL 5

Per prima cosa installaremo MySQL 5, quindi da _Terminale_ digitare

    apt-get install mysql-server mysql-client
    

Durante l’installazione verrà chiesto di inserire una password per l’utente _root_ di MySQL, questa password sarà valida solo per l’utente _root@localhost_ e per _root@server.esempio.com_.

## Installazione di Apache2

Come secondo passo installiamo il Web Server Apache2, il pacchetto è già presente nei repository di Ubuntu quindi ci basterà dare il comando

    apt-get install apache2
    

Al termine dell’installazione per verificare se tutto è andato a buon fine basterà aprire il vostro browser e digitare l’indirizzo IP del Server, **http://192.168.0.11**, se tutto funziona vedrete la seguente immagine.

<img class="alignnone size-medium wp-image-96" title="it-works-apache" src="/public/images/it-works-apache-300x87.png" alt="" width="300" height="87" />

Nella configurazione base la radice dei documenti Apache2 in Ubuntu si trova in\* /var/www/\*, il file di configurazione è _/etc/apache2/apache2.conf._
  
Tutte le altre configurazioni vengono memorizzate in sottodirectory di _/etc/apache2_ come per esempio _/etc/apache2/mods-enabled_ (per i moduli abilitati di Apache) e _/etc/apache2/sites-enabled_ (per gli host virtuali).

## Installazione di PHP5

Installato il Web Server Apache2 siamo in grado di installare PHP5 ed il relativo modulo, quindi a _Terminale_ digitiamo

    apt-get install php5 libapache2-mod-php5
    

Per rendere attiva l’installazione del Modulo libapache2-mod-php5 è necessario riavviare il servizio

    /etc/init.d/apache2 restart
    

## Test di PHP5 e informazioni sull’installazione

Ora verificheremo se l’installazione di PHP e del modulo Apache sono andate a buon fine, inoltre potremo vedere la configurazione di PHP sul Web Server.
  
Nella radice di Apache, _/var/www_, creeremo uno script php con il comando per la visualizzazione della configurazione, quindi a _Terminale_ digitiamo

    gedit /var/www/info.php
    

Nel file di testo che si aprirà inseriamo il seguente codice

    <?php
        phpinfo();
    ?>
    

e salviamo il file.
  
Ora chiamando nel browser l’indirizzo **http://192.168.0.11/info.php** potremo vedere la configurazione di PHP

<img class="alignnone size-medium wp-image-99" title="phpinfo" src="/public/images/phpinfo-300x291.png" alt="" width="300" height="291" />

Come si può vedere PHP è attivo con il gestore Apache 2.0, mostrato nella riga Server API. Scorrendo tutta la configurazione si possono vedere i moduli che sono abilitati.
  
MySQL non viene menzionato tra questi, vuol dire che non è ancora presente il supporto.

## Installare il supporto MySQL e altri moduli in PHP5

Per ottenere il supporto MySQL in PHP, basta installare il pacchetto _php5-mysql_. E’ buona prassi installare anche altri moduli che solitamente vengono utilizzati nelle applicazioni.
  
Per cercare i moduli disponibili basta digitare nel _Terminale_ il comando

    apt-cache search php5
    

Scegli quelli che ti sono più utili per la tua configurazione, di solito io installo i seguenti con questo comando

    apt-get install php5-mysql php5-curl php5-gd php5-IDN php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
    

Ora si può riavviare Apache2

    /etc/init.d/apache2 restart
    

Ora ricaricando la pagina **http://192.168.0.11/info.php** e scorrendo alla sezione Moduli, potremo vedere tutti i nuovi moduli installati e le relative configurazioni

<img class="alignnone size-medium wp-image-100" title="info-mysql" src="/public/images/info-mysql-300x257.png" alt="" width="300" height="257" />

## Installiamo phpMyAdmin

Per gestire il nostro database MySQL abbiamo a disposizione una applicazione Web chiamata <a title="phpMyAdmin" href="http://www.phpmyadmin.net/" target="_blank">phpMyAdmin</a>.
  
Per installarla dare il comando

    apt-get install phpmyadmin
    

Durate l’installazione vi saranno poste le seguenti domande
  
**_Web server to reconfigure automatically: <– apache2_**
  
\*\\*\* Configure database for phpmyadmin with dbconfig-common? <– No\*\**

Successivamente, è possibile accedere a phpMyAdmin attraverso l’indirizzo **http://192.168.0.11/phpmyadmin/**

Complimenti, abbiamo installato una piattaforma _LAMP_ funzionante dove poter testare le nostre applicazioni.