---
id: 434
title: Come ottimizzare il tuo sito minificando i file
date: 2015-04-02T08:00:42+00:00
author: Antonio Lanzolla
layout: post
guid: http://www.antoniolanzolla.com/?p=434
permalink: /ottimizzare-sito-minificando-file/
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
  - 3475718706
wordtwit_posted_tweets:
  - 'a:1:{i:0;i:464;}'
wordtwit_post_info:
  - 'O:8:"stdClass":13:{s:6:"manual";b:1;s:11:"tweet_times";s:1:"1";s:5:"delay";s:1:"0";s:7:"enabled";s:1:"1";s:10:"separation";i:60;s:7:"version";s:3:"3.7";s:14:"tweet_template";s:57:"Come ottimizzare il tuo sito minificando i file - [link] ";s:6:"status";i:2;s:6:"result";a:0:{}s:13:"tweet_counter";i:2;s:13:"tweet_log_ids";a:1:{i:0;i:464;}s:9:"hash_tags";a:0:{}s:8:"accounts";a:1:{i:0;s:6:"Lanz86";}}'
twitter-text:
  - "Come comprimere #css e #javascript fino all'85%"
twitter-hashtag:
  - '#webperf #webprf #seo #wpo'
categories:
  - WPO
tags:
  - web optimizzation
  - webperf
  - webprf
  - wpo
---
Nel precedente post ti ho mostrato come [abilitando la compressione GZIP](http://www.antoniolanzolla.com/ridurre-dimensione-file-su-sito-web/ "Abilitando la compressione GZIP") puoi ottimizzare i tempi di caricamento del tuo sito.  Ti ho spiegato come, in molte occasioni, la compressione **GZIP** non viene abilitata sul client perché, alcuni software di sicurezza, inibiscono la possibilità di richiedere contenuto compresso al browser.

[<img class=" size-full wp-image-455 aligncenter" src="http://www.antoniolanzolla.com/wp-content/uploads/2015/04/minify-file.png" alt="Come ottimizzare il tuo sito minificando i file" width="680" height="350" srcset="http://www.antoniolanzolla.com/wp-content/uploads/2015/04/minify-file-300x154.png 300w, http://www.antoniolanzolla.com/wp-content/uploads/2015/04/minify-file.png 680w" sizes="(max-width: 680px) 100vw, 680px" />](http://www.antoniolanzolla.com/wp-content/uploads/2015/04/minify-file.png)

In questo post vedremo come è possibile comprimere alcuni file attraverso la minificazione di **JavaScript** e **CSS** e ti illustrerò, come utilizzare il tool **YUI Compressor,** per ottenere i file _minificati_.

## Cosa vuol dire minificazione

La _minificazione_ è quella tecnica che permette di comprimere i file, **CSS** e **JavaScript**, rimuovendo dal file sorgente caratteri non necessari per la corretta esecuzione e interpretazione del file. Con questo processo rimuoverai _commenti, spazi inutili, interruzioni di riga_ per **JavaScript** e **CSS**. Invece nei soli file **JavaScript** potrai ottimizzare ulteriormente riducendo il nome di funzioni e variabili.

Questa operazione, se fatta a mano, è molto complessa, in questo post, ti suggerirò alcuni tool e ti spiegherò in maniera dettagliata il funzionamento di **YUI Compressor** che ti permetterà di automatizzare questo processo.

## Minificazione del JavaScript

Alcuni strumenti che ho trovato utili per minificare i file **JavaScript** sono:

  * <a title="YUI Compressor" href="http://yui.github.io/yuicompressor/" target="_blank">YUI Compressor</a>
  * <a title="Packer Compressor" href="http://dean.edwards.name/packer/" target="_blank">Packer</a>
  * <a title="JSMin " href="http://crockford.com/javascript/jsmin" target="_blank">JSMin</a>

_Quale vantaggio ottengo minificando i file JavaScript?_ 

Per rispondere a questa domanda ho fatto una comparazione tra gli strumenti che ti ho suggerito, comprimendo il file di <a title="jQuery 1.11.2" href="http://jquery.com/download/" target="_blank"><em>jQuery 1.11.2</em></a> e confrontando le dimensioni prima/dopo,  con/senza <a title="Compressione GZIP" href="http://www.antoniolanzolla.com/ridurre-dimensione-file-su-sito-web/" target="_blank"><strong>GZIP</strong></a>.

La tabella seguente elenca i risultati che ho ottenuto.

[table id=1 /]

Come puoi vedere dalla tabella, <a title="Abilitare compressione GZIP" href="http://www.antoniolanzolla.com/ridurre-dimensione-file-su-sito-web/" target="_blank">abilitando la compressione GZIP</a>, puoi ridurre il tuo file del _70%._ Associando anche l&#8217;operazione di _minificazione_, puoi raggiungere una compressione del _85%_. Capisci perché conviene _minificare_ i file.
  
Non è importante quale strumento utilizzerai, ti consiglio di scegliere quello che ritieni più comodo e che ti permette di automatizzare al meglio queste operazioni in base alla piattaforma che utilizzi abitualmente.

## Minificazione del CSS

Puoi effettuare la stessa operazione di minificazione con i file **CSS**, devi sapere, però, che con il **CSS** questo tipo di compressione è meno potente, a differenza di quella fatta sui file **JavaScript**. Questo dipende dalla natura del **CSS**, l&#8217;operazione di _minificazione_, non può effettuare alcune operazioni, che invece sono permesse in **JavaScript** come rinominare proprietà, spostare parte del contenuto del file o comprimere il nome di una regola, se eseguite sui **CSS** queste operazioni potrebbero non permettere il corretto funzionamento del foglio di stile.

In giro per il web non ho trovato molti _minifier_ per **CSS**, alcuni producono un risultato che non assicura il funzionamento su tutti i browser. Questo perché in molti casi i file **CSS** contengono _hack_ per risolvere incompatibilità tra browser, alcuni _minifier_ non riconoscono questi **hack** e quindi gli eliminano credendo di ottimizzare il **CSS,** ma producono un risultato non funzionante su tutti i Browser.

Gli strumenti che posso consigliarti sono

  * <a title="Yui Compressor" href="http://yui.github.io/yuicompressor/" target="_blank">YUI Compressor</a>: lo stesso che ti ho indicato per la _minificazione_ **JavaScript**
  * <a title="CSS Tidy" href="http://csstidy.sourceforge.net/" target="_blank">CSSTidy</a> : ci sono due versioni una in PHP utilizzabile direttamente sul tuo server web e una in C per i desktop.

_Minificando_ i file **CSS** possiamo ottenere circa il _10%_ di ottimizzazione, questo per quello che ti ho spiegato in precedenza, ma se associato alla <a title="Compressione GZIP" href="http://www.antoniolanzolla.com/ridurre-dimensione-file-su-sito-web/" target="_blank">compressione GZIP</a> riusciamo a comprimere il file fino all&#8217;_80%_.

## Come usare YUI Compressor

Il tool che utilizzo di solito per effettuare la _minificazione_ dei file **CSS** e **JavaScript** è _YUI Compressor._ Questo strumento è stato creato da Yahoo e come recita il sito Web:

> _YUI Compressor_ è sicuro, comprime i file assicurando al 100% il funzionamento previsto dai sorgenti.

_YUI Compressor_ è scritto in Java, ed è un progetto OpenSource, quindi puoi anche spulciare il codice sorgente per capire come funziona.

Quando _minifica_ un file **JavaScript**, _YUI Compressor_, analizza il file e rimuove tutti quei caratteri che sono ritenuti superflui per il corretto funzionamento dello script. _YUI Compressor_ riesce anche ad offuscare i file **JavaScript** cercando di sostituire, dove è possibile, i nomi delle variabili e dei metodi con nomi composti da massimo 3 caratteri.

L&#8217;algoritmo di compressione del **CSS**, invece, utilizza espressioni regolari per comprimere il file, rimuovendo i caratteri non necessari.

_YUI Compressor_ può essere utilizzato attraverso la riga di comando, ma non spaventarti, il suo utilizzo è veramente semplice.

Per poter comprimere un file **JavaScript** ti basterà, dopo aver effettuato il download di <a title="YUI Compressor Download" href="https://github.com/yui/yuicompressor/downloads" target="_blank">YUI Compressor</a> dal sito ufficiale, lanciare il comando

<pre>java -jar yuicompressor-<strong>xyzjar</strong> myfile.js -o myfile-min.js</pre>

>  xyzjar indica il numero di versione di _YUI Compressor_ scaricato

Con questo comando creerai, partendo da un file sorgente, _myfile.js_, che sarà il tuo file **JavaScript**, un file con il codice _minificato_ con il nome _myfile-min.js._

Per poter minificare un file **CSS** ti basta effettuare la stessa operazione utilizzando semplicemente un file _.css._

Se l&#8217;utilizzo da riga di comando di _YUI Compressor_ ti spaventa, non preoccuparti, ti consiglio un altro tool che utilizza _YUI Compressor_ ma ti permette di comprimere i file attraverso il browser <a href="http://refresh-sf.com/yui/" target="_blank">http://refresh-sf.com/yui/</a> questo tool ti permette, in maniera semplice e attraverso un interfaccia web, di creare le versioni _minificate_ dei file.

## Conclusioni

Abbiamo visto come è possibile ridurre ulteriormente la dimensione di file **JavaScript** e **CSS** utilizzando la tecnica della _minificazione_, ti consiglio di adottare questa tecnica, anche se hai <a title="Attivare GZIP" href="http://www.antoniolanzolla.com/ridurre-dimensione-file-su-sito-web/" target="_blank">già attivato GZIP</a>, questo ti permette di ridurre il peso dei tuoi file di circa il _10%_.

Utilizzare questa tecnica ti permette di ottenere un sito ottimizzato e più veloce con un&#8217;operazione da fare una sola volta ma che porta benefici ad ogni utente che vista il tuo sito.

_**Cosa ne pensi di queste tecniche che ti ho indicato? Hai altri consigli per ottimizzare i tempi di caricamento? Fammelo sapere nei commenti.**_

_**Se questo post ti è stato utile condividilo sui social.**_