---
id: 423
title: Come ridurre la dimensione dei file sul tuo sito web
date: 2015-01-27T07:30:11+00:00
author: Antonio Lanzolla
layout: post
guid: http://www.antoniolanzolla.com/?p=423
permalink: /ridurre-dimensione-file-su-sito-web/
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
  - 3457849714
twitter-text:
  - Come risparmiare sulla bolletta della banda del tuo sito web
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
Nel precedente post ti ho mostrato come riducendo il <a title="Riduci il numero di file e sarai più veloce" href="http://www.antoniolanzolla.com/riduci-numero-file/" target="_blank">numero di chiamate al server</a> puoi ottimizzare i tempi di caricamento del tuo sito.

In questo post è arrivato il momento di capire come, puoi ottenere, comprimendo la dimensione dei file, ottimi risultati.

<img class=" size-full wp-image-443 aligncenter" src="http://www.antoniolanzolla.com/wp-content/uploads/2015/04/2-ridurre-dimensione.png" alt="Ridurre la dimensione dei file sul tuo sito web" width="680" height="350" srcset="http://www.antoniolanzolla.com/wp-content/uploads/2015/04/2-ridurre-dimensione-300x154.png 300w, http://www.antoniolanzolla.com/wp-content/uploads/2015/04/2-ridurre-dimensione.png 680w" sizes="(max-width: 680px) 100vw, 680px" />

Ridurre la dimensione dei file ti aiuterà ad avere un sito con tempi di caricamento migliori, ma anche, ti farà risparmiare sulla fattura della banda.

Hai tre armi per ottimizzare la dimensione dei file:

  1. La compressione **GZIP**
  2. La compressione dei file che metti a disposizione per il download.
  3. La minificazione di file CSS e JavaScript (Di questo te ne parlerò nel prossimo post)

## Compressione GZIP

Il modo più semplice e più efficace che hai per ottimizzare i tempi di caricamento è quello di attivare la compressione **GZIP** sul tuo _server web_.

Attivare la compressione **GZIP** ti permetterà, senza aggiungere nessuno sforzo nello sviluppo del sito, di migliorare i tempi del tuo sito. Ti basterà semplicemente attivarlo, modificando la configurazione del tuo _server web_.

Ti assicuro che resterai stupito dai risultati che puoi ottenere da questa semplice operazione.

Agli inizi della costruzione del portale _Netflix_ si sono accorti che sui loro server **GZIP** non era attivo

Puoi vedere, nel grafico sotto, come dell&#8217;attivazione di **GZIP** sui server sono riusciti a dimezzare la banda permettendogli di rendere il sito veloce e riducendo del 70% le spese della banda.

[<img class=" size-full wp-image-424 aligncenter" src="http://www.antoniolanzolla.com/wp-content/uploads/2015/01/netflix-fs8.png" alt="Netflix attivazione GZIP" width="616" height="199" srcset="http://www.antoniolanzolla.com/wp-content/uploads/2015/01/netflix-fs8-300x97.png 300w, http://www.antoniolanzolla.com/wp-content/uploads/2015/01/netflix-fs8.png 616w" sizes="(max-width: 616px) 100vw, 616px" />](http://www.antoniolanzolla.com/wp-content/uploads/2015/01/netflix-fs8.png)

&nbsp;

### Qualcosa su GZIP!

  1. In media puoi avere un file ridotto del 70% utilizzando la compressione **GZIP**.
  2. L&#8217; attivazione di **GZIP** aggiunge un piccolo costo computazionale sia sul server che deve comprimerlo che sul client che deve decomprimerlo.
  3. **GZIP** funziona su tutti i browser moderni.

_Come verifico se è già attivo sul mio server?_

Per verificare se sul tuo _server web_ è attivo **GZIP** puoi utilizzare gli strumenti che ti ho suggerito nel post [Ottimizza i tempi di caricamento del tuo sito](http://www.antoniolanzolla.com/ottimizza-i-tempi-di-caricamento-del-tuo-sito/ "Ottimizza i tempi di caricamento del tuo sito"), quindi <a title="GTMetrix" href="http://www.gtmetrix.com/" target="_blank">GTMetrix</a> o <a title="PageSpeed Insights" href="https://developers.google.com/speed/pagespeed/insights/" target="_blank">PageSpeed Insights</a> entrambi hanno una regola che ti segnalerà se la compressione **GZIP** non è attiva.

_Quali tipi di file puoi comprimere con GZIP?_

Tutti i file non binari:

  * JavaScript
  * CSS
  * Testo
  * HTML, XML, SVG
  * Risposte JSON

Puoi anche comprimere file @font come EOT, TTF, OTF l&#8217;unico formato font che non è possibile comprimere è WOFF. In media un file font compresso con **GZIP** è più piccolo del 60% a differenza del file originale.

### Come attivare la compressione GZIP su Apache

Per attivare la compressione **GZIP** ti basta modificare la configurazione del tuo _server web_.

Se ti trovi nella condizione di aver acquistato un hosting e non hai il pieno controllo delle impostazioni del _server web_ la maggior parte degli hosting provider ti darà la possibilità di attivare **GZIP** attraverso la modifica  del file _.htaccess_.

Se il tuo hosting provider non ti permette di attivare questa impostazione l&#8217;unico consiglio che posso darti è quello di cambiarlo.

Quindi ti basterà aggiungere al file _.htaccess_ questa parte di configurazione

<pre>&lt;ifModule mod_gzip.c&gt;
mod_gzip_on Yes
mod_gzip_dechunk Yes
mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
mod_gzip_item_include handler ^cgi-script$
mod_gzip_item_include mime ^text/.*
mod_gzip_item_include mime ^application/x-javascript.*
mod_gzip_item_exclude mime ^image/.*
mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
&lt;/ifModule&gt;</pre>

Così sarà attiva la compressione **GZIP** sul tuo _server web_

## Rezip

Non è possibile comprimere attraverso **GZIP** i file binari che metti a disposizione per il download ai tuoi utenti, in molti casi questi sono file sono già compressi sotto mentite spoglie.

Ti faccio qualche esempio:

  1. Documenti Ms Office DOCX, XLSX, PPTX
  2. Documenti Open Office o Libre Office ODT, ODP, ODS
  3. JAR
  4. Estensioni per Firefox XPI
  5. Applicazioni Silverlight XAP
  6. Ecc&#8230;

Questi file sono solitamente file compressi ma in incognito. Però, la loro compressione non è ottimale. Se hai sul tuo sito download di questi file ti consiglio di effettuare una compressione migliore.

Puoi ridurre, migliorando la compressione, la dimensione dei file tra l&#8217;_1%_ e il _30%_. Se hai l&#8217;accortezza di comprimerli, avrai con una semplice operazione, eseguita una sola volta,  benefici per tutti i tuoi utenti che scaricheranno quei file.

## Traffico non compresso

Può succede, su siti con un alto volume di traffico e utenza, che una grande parte del traffico, si stima circa il _15%_, anche se attivo **GZIP** sul tuo _server web_, venga comunque inviato non compressa. Questo succede perché alcuni _Proxy, Firewall e Antivirus_ &#8220;intrufolandosi&#8221; tra la scheda di rete e la connessione del Browser modificando l&#8217;intestazione _Accept-Encoding (che è quella che indica al server che il client accetta contenuto compresso)_. Questa intestazione viene modificata, da questi software, con valori non validi, quindi il _server web_ decide di non comprimere il file per assicurarsi che il client lo possa leggere.

Purtroppo questo comportamento lede sia gli utenti che la banda del tuo Server.

C&#8217;è un modo per rimediare, almeno in parte, a questo comportamento. Ed è nell&#8217;assicurarsi che, una parte dei contenuti, venga comunque inviata in forma compressa. Nel **prossimo post** ti illustrerò come puoi comprimere questi file attraverso la _minificazione_ e _l&#8217;offuscamento_ di CSS e JavaScript.

## Conclusioni

Hai visto come attraverso l&#8217;attivazione di un&#8217;impostazione sul tuo _server web_ puoi ridurre la dimensione di alcuni file, questo ti permetterà di ridurre i tempo di download per gli utenti che visiteranno il tuo sito ma anche, di risparmiare banda sul tuo _server web_.

Queste piccole tecniche ti permetteranno di avere un sito ottimizzato e quindi più veloce nel suo caricamento e ti porteranno anche a ridurre la fattura che paghi per la banda del tuo sito.

Cosa ne pensi di queste tecniche che ti ho indicato? Hai altri consigli per ottimizzare i tempi di caricamento? Fammelo sapere nei commenti.

Se questo post ti è stato utile condividilo sui social.