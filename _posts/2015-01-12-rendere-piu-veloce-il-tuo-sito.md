---
id: 369
title: 2 trucchi per rendere più veloce il tuo sito
date: 2015-01-12T08:30:37+00:00
author: Antonio Lanzolla
layout: post
guid: http://www.antoniolanzolla.com/?p=369
permalink: /rendere-piu-veloce-il-tuo-sito/
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
  - 3411541264
twitter-text:
  - 2 trucchi per rendere più veloce il tuo sito
twitter-hashtag:
  - '#seo #wpo #webperf #webprf'
categories:
  - WPO
tags:
  - browser
  - css
  - javascript
  - web optimizzation
  - wpo
---
Ti ho introdotto, nel precedente [post](http://www.antoniolanzolla.com/ottimizza-i-tempi-di-caricamento-del-tuo-sito/ "Ottimizza i tempi di caricamento del tuo sito"), nel modo dell&#8217;ottimizzazione delle performance del tuo sito web. Ti ho spiegato perché è importante avere un sito che abbia dei tempi di caricamento bassi e come questo parametro può influire su traffico, vendite e conversioni.

In questo post ti suggerirò alcuni trucchetti che potrai adottare, da subito, per ottimizzare la velocità di caricamento del tuo sito.

<img class="aligncenter size-full wp-image-386" src="http://www.antoniolanzolla.com/wp-content/uploads/2015/01/2-trucchi-per.png" alt="2 trucchi per rendere più veloce il tuo sito" width="680" height="350" srcset="http://www.antoniolanzolla.com/wp-content/uploads/2015/01/2-trucchi-per-300x154.png 300w, http://www.antoniolanzolla.com/wp-content/uploads/2015/01/2-trucchi-per.png 680w" sizes="(max-width: 680px) 100vw, 680px" />

Per ottimizzare i tempi di caricamento, una cosa fondamentale è che tu sappia come funziona e quali operazioni vengono svolte dal _Browser _prima di visualizzare una pagina web.

Ho trovato questa [**ottima guida**](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/ "How Browser Work") che ti spiegherà in maniera esaustiva cosa succede dietro le quinte del _Browser_. E&#8217; un&#8217;articolo lungo, ma ti consiglio di leggerlo, ti permetterà di capire come sfruttare il comportamento del _Browser_ per ottimizzare al meglio i tempi di caricamento.

Intanto io ti darò una breve spiegazione su quali sono le operazioni effettuate dal _Browser_ prima di visualizzare una pagina. Questi punti ti serviranno per capire quali operazioni possono aiutarti a ottenere miglioramenti nei tempi di caricamento.

## Le operazioni del Browser per visualizzare una pagina

Per rendere più veloce il caricamento del tuo sito devi conoscere questi passaggi che ti elenco. Queste sono le operazioni effettuate dal _Browser_ dal momento in cui inserisci l&#8217;indirizzo a quando viene visualizzata la pagina sullo schermo:

  1. Il _Browser_ effettua una chiamata al server per richiedere la pagina.
  2. Il _Browser_, se la pagina esiste, riceve dal server, attraverso l&#8217;interfaccia di rete, il documento richiesto diviso in pezzi da **_8kB_**.
  3. Il _Browser_ comincia ad analizzare i dati ricevuti e il markup (**HTML**) e costruisce l&#8217;albero **DOM** (DOM = Document Object Model)
  4. Il _Browser _analizza il _**CSS,**_ sia esterno che interno, e costruisce l&#8217;albero **CSSOM** (CSSOM = CSS Object Model)
  5. Il _Browser_ prima di combinare **DOM** e l&#8217;albero **CSSOM** per costruire l&#8217;albero di _Render_, analizza ed esegue eventuali script _**JavaScript**_ che incontra.
  6. Il _Browser_ visualizza la pagina

Queste sono, in breve, le operazioni che effettua il _Browser_ per visualizzare una pagina web.

Ora che conosci questi passi, puoi capire quanto è importante ottimizzare _**CSS**_ e _**JavaScript** _e come, in molti casi, sono responsabili del degrado delle performance del tuo sito.

Una cosa importante che voglio sottolineare è che, il _Browser,_ nel momento in cui può disegnare una porzione della pagina, perché ha ricevuto tutti i dati necessari per costruire **DOM e** **CSSOM** lo fa**.**

Possiamo sfruttare questo, per cominciare a far visualizzare sullo schermo la porzione che viene subito caricata dall&#8217;utente, solitamente è la parte alta della pagina, questa parte si chiama **above the fold**.

Vedremo ora alcuni accorgimenti che ti permetteranno di far caricare più velocemente la parte **above the fold **del tuo sito.

## Ottimizza il CSS

I **CSS** possono essere i responsabili del calo di performance del tuo sito.

Quando il _Browser_ incontra, nella sua analisi, i tag di inclusione di un file **CSS,** deve effettuare una chiamata di rete, attendere che il file sia scaricato, analizzarlo e costruire l&#8217;albero **_CSSOM_**.

Capirai bene che l&#8217;attesa per scaricare il file e analizzarlo pò aumentare i tempi di caricamento.

Ti suggerisco 3 punti utili per ottimizzare questo comportamento:

  1. Sposta le regole _**CSS**_ che servono per visualizzare i contenuti **above the fold** direttamente inline tra due tag _<style></style>_ nell&#8217;_header_ della pagina.
  2. Rimuovi tutte le regole _**CSS** _che non vengono utilizzate.
  3. Ritarda il più possibile il caricamento degli altri file **CSS,** che non servono per visualizzare la parte **above the fold**. Di solito io carico questi file attraverso uno script **JavaScript** caricandoli al _ready_ della pagina.

### Qualche Tool?

Ti suggerisco alcuni Tool che ho trovato utili per analizzare le pagine ed avere suggerimenti su come ottimizzare il caricamento dell&#8217; **above the fold.**

Puoi utilizzare <a title="PageSpeed Insights" href="https://developers.google.com/speed/pagespeed/insights/?hl=it" target="_blank">PageSpeed Insight</a>, che ti suggerirà quali sono i file di stile che bloccano la visualizzazione della pagina.

Un&#8217; altro strumento che ho trovato utile per il mio lavoro, che ti consiglio di utilizzare, si chiama [Penthouse](https://github.com/pocketjoso/penthouse "Penthouse Critical Path CSS Generator"). Un progetto _OpenSource_ utilizzabile attraverso _NodeJs.
  
_ Questo strumento ha anche una versione_ _[On-Line](http://jonassebastianohlsson.com/criticalpathcssgenerator/ "Penthouse Critical Path CSS Generator OnLine") facile da utilizzare.
  
Penthouse analizza la tua pagina web e il **CSS** e ti suggerisce quali sono le regole di stile da caricare prima per ottimizzare i tempi di caricamento del tuo sito.

## Ottimizza il JavaScript

Come hai potuto vedere, anche **JavaScript** può degradare le prestazioni delle tue pagine web.
  
Quando il _Browser_ incontra uno file **JavaScript** è costretto ad interrompere l&#8217;analisi dell&#8217;**HTML**, scaricare il file ed eseguirlo.

Questo rallenta notevolmente il caricamento della pagina, specialmente se il codice **JavaScript** effettua operazioni complesse.

Ti suggerisco tre punti che ti permetteranno di ottimizzare il caricamento dei file **JavaScript**:

  1. **Utilizza l&#8217;attributo _async_**: aggiungendo l&#8217;attributo _async_ nel tag _<script></script>_ costringerai il _Browser_ a scaricare il file in contemporanea con l&#8217;analisi del codice **HTML** e ad eseguire lo script subito dopo che ha terminato il download.
  2. **Utilizza l&#8217;attributo _defer_**: l&#8217;attributo _defer_ invece effettua la stessa operazione di _async_ con la sola differenza che eseguirà il codice solo dopo aver terminato l&#8217;analisi del codice **HTML**.
  3. **Ritardare l&#8217;esecuzione e il caricamento dei file JS**: quando è possibile sposta la dichiarazione e i tag di _<script></script>_ subito prima la chiusura del tag _<body />_

> Attenzione: Anche se supportati da quasi tutti i _Browser_ ti consiglio di verificare la compatibilità degli attributi <a title="Compatibilità attributo Async" href="http://caniuse.com/#search=async" target="_blank">async</a> e <a href="http://caniuse.com/#search=defer" target="_blank">defer</a>.

## Conclusioni

Siamo arrivati alla fine di questo post, ti ho spiegato in maniera sintetica come funziona un _Browser,_ quali sono le operazioni che esegue prima di visualizzare una pagina del tuo sito e ti ho dato alcuni consigli per migliorare il caricamento di **CSS** e **JavaScript**_**.**_

Nei prossimi post ti darò altri suggerimenti importanti e ti farò scoprire alcuni Tool che possono facilitarti il lavoro.

Se ti va di seguirmi ed essere aggiornato sui prossimi articoli, nella colonna laterale destra, puoi trovare l’iscrizione alla newsletter.

Non dimenticare di farmi sapere la tua opinione scrivendo un commento. Se ti va ed hai trovato utile questo post condividilo sui social.