---
id: 398
title: Riduci il numero di file e sarai più veloce
date: 2015-01-19T07:00:58+00:00
author: Antonio Lanzolla
layout: post
guid: http://www.antoniolanzolla.com/?p=398
permalink: /riduci-numero-file/
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
  - 3433739863
twitter-text:
  - Riduci il numero di file e sarai più veloce
twitter-hashtag:
  - '#seo #wpo #webperf #webprf'
categories:
  - WPO
tags:
  - web optimizzation
  - webperf
  - webprf
  - wpo
---
Nei precedenti post ti ho introdotto nel mondo delle [ottimizzazioni dei tempi di caricamento](http://www.antoniolanzolla.com/ottimizza-i-tempi-di-caricamento-del-tuo-sito/ "Ottimizza i tempi di caricamento del tuo sito") e ti ho suggerito [due trucchi per ottimizzare il tuo sito](http://www.antoniolanzolla.com/rendere-piu-veloce-il-tuo-sito/ "2 trucchi per rendere più veloce il tuo sito"). In questo post ti illustrerò come, puoi ottimizzare i tempi di caricamento, riducendo il numero di file necessari alla visualizzazione del tuo sito.

[<img class=" size-full wp-image-411 aligncenter" src="http://www.antoniolanzolla.com/wp-content/uploads/2015/01/riduci.png" alt="Riduci il numero di file e sarai più veloce" width="680" height="350" srcset="http://www.antoniolanzolla.com/wp-content/uploads/2015/01/riduci-300x154.png 300w, http://www.antoniolanzolla.com/wp-content/uploads/2015/01/riduci.png 680w" sizes="(max-width: 680px) 100vw, 680px" />](http://www.antoniolanzolla.com/wp-content/uploads/2015/01/riduci.png)

&nbsp;

Per ottimizzare al meglio i tempi di caricamento devi analizzare il tuo sito e scoprire quanti file esterni vengono caricati per visualizzare la tua pagina web.

_Quali sono questi file esterni?_

Si tratta di tutti quei file che la tua pagina ha bisogno di scaricare oltre al codice HTML, quindi: **CSS**, **JavaScript**, **Font** e **Immagini.**

_Ora sicuramente mi dirai:_ 

> _Il mio sito ha tanti file ma tutti di piccole dimensioni. Come possono influire sulla velocità di caricamento?_

## Perché ridurre il numero di file.

La dimensione dei file è molto importante, minore è la dimensione di un file e minore è il tempo di download. Logicamente un file di _100kB_ sarà scaricato più velocemente di uno di _150kB_.

Ti consiglio, nei limiti, di mantenere la dimensione dei file bassa, ma ti farò vedere come molte volte, il peso di un file può essere un fattore marginale nell&#8217;ottimizzazione dei tempi di caricamento.

_Perchè?_ 

> **_Perchè per ogni file c&#8217;è un intestazione!_**

Ogni risposta **HTTP**, quindi ogni file richiesto dal _Browser_ al _server_, risponde con il suo contenuto (_Response Body_ ) e un&#8217;**intestazione** (_Response Header_).

Solitamente l&#8217;**intestazione** è di pochi _byte, _quindi per file di grandi dimensioni l&#8217;**intestazione** può essere considerata poco influente. Ma in casi dove si effettuano molte richieste con piccoli file l&#8217;**intestazione**_ _può essere un problema da non sottovalutare.

### Un esempio?

Prendiamo un file con una dimensione di circa **1kB**. Ora ipotizziamo di avere _un&#8217;_**intestazione** che si aggira intorno hai **500**_**byte**,_ capirai che per trasferire un file da **1kB** il browser dovrà scaricare anche l&#8217;**intestazione.** Quindi il browser scaricherà **1,5kB**. Questo può creare problemi perchè nel caso il tuo sito facesse uso di cookie l&#8217;**intestazione** potrebbe crescere.

> Nella mia esperienza ho incontrato alcuni casi dove l&#8217;**intestazione** era maggiore del file da scaricare.

Visto che ad ogni richiesta deve transitare l&#8217;**intestazione,** anche se con file di piccole dimensioni, aumenta il numero di byte da scaricare.

Questo può essere uno dei problemi che rende i tempi di caricamento del tuo sito alti.

Ora vedremo, come il problema dell&#8217;**intestazione** in molti casi è un problema minore.

Molte volte il collo di bottiglia si trova direttamente nel browser per il suo modo di gestire le connessioni.

## Browser e troppe connessioni HTTP

_Cosa succede quando digiti l&#8217;indirizzo di un sito web sul browser e premi invio?_

Il browser invia una richiesta al server.

_Quale server?_

Il browser per raggiungere il sito deve conoscere l&#8217;indirizzo IP del server, se non è presente nella sua cache dei DNS deve fare una ricerca sul server DNS, dopo aver stabilito la connessione al server attende il primo byte e comincia a ricevere il file.

Nell&#8217;immagine puoi vedere come queste operazioni sono rappresentate dal Tool <a title="Web Page Test" href="http://webpagetest.org" target="_blank">http://webpagetest.org</a> (Ti parlerò di questo Tool in altri post)

<img class="alignleft size-full wp-image-399" src="http://www.antoniolanzolla.com/wp-content/uploads/2015/01/connection.png" alt="Http richiesta pagina web" width="118" height="18" />

&nbsp;

  1. <span style="color: #007b84;">Ricerca del DNS</span>
  2. <span style="color: #ff7b00;">Connessione al Server</span>
  3. <span style="color: #00ff00;">TTFB (Time to first byte)</span>
  4. <span style="color: #007bff;">Download del file</span>

_Cosa possiamo capire da questa rappresentazione?_

Puoi notare come solo circa il _40%_ del tempo è stato utilizzato dal browser per scaricare il contenuto. Il restante _60%_ invece il browser si è occupato di operazioni collaterali.

> Ho incontrato situazioni dove le operazioni che vedi nei primi tre punti occupavano circa l&#8217;_80% _di tutta la richiesta.

Immagina che queste operazioni vengono effettuate per ogni file che la tua pagina scarica.
  
Quindi ogni **CSS**, **JavaScript**, **Immagine** o **Font** dovrà, prima di essere scaricata e resa disponibile all&#8217;utente, attendere queste operazioni.

_Cosa vuol dire questo?_

  1. Che una parte significativa del tempo viene spesa dal browser per attività diverse da quelle che sono il download dei file.
  2. File molto piccoli, probabilmente, avranno un tempo di download estremamente inferiore al tempo che il browser dedicherà per effettuare le altre operazioni.

_Non credi che sia un peccato?_

## Cosa fare.

Per ottimizzare i tempi di caricamento delle tue pagine devi ridurre il numero di file, così ridurrai i tempi di caricamento e pagherai meno le operazioni che servono per far cominciare il download.

_Come dovresti fare?_

### Elimina tutto quello che non serve!

Molte funzionalità presenti sul tuo sito non vengono utilizzate dagli utenti. Analizza le pagin, effettua dei test e rimuovi tutto quello che all&#8217;utente non è necessario o non viene utilizzato.

_Non credi che sia inutile rendere il sito più lento solo perché abbiamo paura di sbarazzarci di alcune funzionalità?_

### Combina i file

Ora che ti ho convinto a rimuovere tutto quello che è superfluo per l&#8217;utente, ti restano quei file necessari per il funzionamento del tuo sito. Puoi unirli in modo da ridurre il numero di richieste che il browser deve effettuare al server.

_Cosa vuol dire combinare i file?_

Devi trasformare tutti i piccoli file **JavaScript**, **CSS** e **Immagini** facendoli diventeranno un unico file. Così continuerai ad avere tutte le funzionalità del tuo sito ma ridurrai il numero di richieste al server.

#### Un esempio?

Ti faccio questo esempio con una lista di file JavaScript, puoi adottare la stessa tecnica anche per i file **CSS**.

Quindi una lista di script **JavaScript**.

<pre><span class="hl-brackets">&lt;</span><span class="hl-reserved">script</span> <span class="hl-var">src</span><span class="hl-code">=</span><span class="hl-quotes">"/scripts/</span><span class="hl-string">jquery.min.js</span><span class="hl-quotes">"</span><span class="hl-brackets">&gt;</span><span class="hl-brackets">&lt;/</span><span class="hl-reserved">script</span><span class="hl-brackets">&gt;
</span><span class="hl-brackets">&lt;</span><span class="hl-reserved">script</span> <span class="hl-var">src</span><span class="hl-code">=</span><span class="hl-quotes">"</span><span class="hl-string">/scripts/application.js</span><span class="hl-quotes">"</span><span class="hl-brackets">&gt;</span><span class="hl-brackets">&lt;/</span><span class="hl-reserved">script</span><span class="hl-brackets">&gt;
</span><span class="hl-brackets">&lt;</span><span class="hl-reserved">script</span> <span class="hl-var">src</span><span class="hl-code">=</span><span class="hl-quotes">"</span><span class="hl-string">/scripts/ui/minified/jquery.ui.all.min.js</span><span class="hl-quotes">"</span><span class="hl-brackets">&gt;</span><span class="hl-brackets">&lt;/</span><span class="hl-reserved">script</span><span class="hl-brackets">&gt;</span></pre>

Deve diventare

<pre>&lt;script src="/scripts/all.js"&gt;&lt;/script&gt;</pre>

Per le **immagini** ti consiglio di creare un solo file _PNG_ dove inserirai tutte le immagini che servono per il layout del tuo sito.
  
Questo file potrai utilizzarlo nel **CSS** utilizzando regole di _background_ con _posizionamento_ e _dimensione_ in modo da visualizzare dove vuoi solo le porzioni desiderate.

### Attivare il Keep-Alive sul server

Un altro consiglio è quello di attivare il [Keep-Alive](http://httpd.apache.org/docs/2.2/mod/core.html#keepalive "Keep-Alive Apache") sul server. Questa impostazione permette al server di non disconnettersi dal client e restare in attesa di altre richieste. Con questa impostazione il browser non dovrà più effettuare i passi 1 e 2 che abbiamo visto precedentemente.

## Conclusioni

Ridurre il numero di file richiesti da una pagina deve essere per te la priorità assoluta, ti permette di ottenere ottime prestazioni con poco sforzo.

Per ottimizzare i tempi di caricamento devi liberarti di tutte quelle funzionalità che non vengono utilizzate dagli utenti.

Ricorda ogni richiesta HTTP al server ha un costo, quindi riduci le chiamate ed accorpa i file per ridurne il numero.

## Dimmi cosa ne pensi.

Se ti va di seguirmi ed essere aggiornato sui prossimi post, nella colonna laterale destra, puoi trovare l’iscrizione alla newsletter.

E&#8217; molto importante la tua opinione. Cosa pensi delle tecniche che ti ho appena spiegato? Hai suggerimenti per ottimizzare il sito? Ti aspetto nei commenti.

Se ti va ed hai trovato utile questo post condividilo sui social.