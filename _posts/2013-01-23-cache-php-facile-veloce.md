---
id: 246
title: Una cache PHP facile e veloce
date: 2013-01-23T09:44:37+00:00
author: Antonio Lanzolla
layout: post
guid: http://188.226.216.54/?p=246
permalink: /cache-php-facile-veloce/
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
  - 2778456356
twitter-text:
  - 'Una cache #PHP facile e veloce'
twitter-hashtag:
  - '#php #programming'
  - '#php #programming'
categories:
  - Programmazione
tags:
  - php
  - snippets
---
Capita molte volte che si sta lavorando ad un progetto progetto in PHP che non è costruito su una base già pronta es. CMS e/o Framework. Oppure stiamo lavorando su progetti molto semplici che non richiedono una grande complessità da dover necessariamente utilizzare CMS o affini, in questi casi può essere utile implementare un sistema di caching delle pagine spartano ma efficiente.

Questo semplice snippet permette di implementare un sistema di caching in maniera facile e veloce con appena 12 righe di codice.

    <?php 
    //definizione del percorso e del nome del file di cache
    $cachefile = 'cached-files/'.date('M-d-Y').'.php';
    // definizione in secondi del tempo di mantenimento della cache
    $cachetime = 18000;
    //Verifica se il file nella cache è ancora valido. Se è valido lo serve ed esce
    if (file_exists($cachefile) && time() - $cachetime->filemtime($cachefile)) {  
        include($cachefile);  
        exit;  
    }  
    // se il file è vecchio o non esiste cattura l'html  
        ob_start();  
    ?>;
    <html>
        output all your html here.
    </html>
    <?php 
    //Al termine salva la pagina in cache  
    $fp = fopen($cachefile, 'w');  
    fwrite($fp, ob_get_contents());  
    fclose($fp);  
    //invia l'output al browser  
    ob_end_flus() 
    ?>
    

Fonte: <a title="Simple php page caching technique" href="http://wesbos.com/simple-php-page-caching-technique/" target="_blank" rel="nofollow">http://wesbos.com/simple-php-page-caching-technique/</a>