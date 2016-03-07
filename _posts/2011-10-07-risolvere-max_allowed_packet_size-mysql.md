---
id: 223
title: Risolvere l’errore max_allowed_packet_size dividendo il file di dump MySQL
date: 2011-10-07T13:25:18+00:00
author: Antonio Lanzolla
layout: post
guid: http://188.226.216.54/?p=223
permalink: /risolvere-max_allowed_packet_size-mysql/
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
  - 2778448419
twitter-text:
  - 'Risolvere l’errore max_allowed_packet_size #MySQL'
twitter-hashtag:
  - '#php'
categories:
  - Programmazione
tags:
  - database
  - mysql
  - php
  - sql
---
Una delle cose molto antipatiche e frustranti quando si lavora con MySQL è l’importazione di grandi file di Dump sql. In molti casi si ottengono due errori, “max execution time exceeded” di PHP oppure “Max\_allowed\_packet_size” da MySQL.

Una soluzione a questo problema potrebbe essere quella di dividere le query di inserimento (“INSERT”) più corposi in file di dimensioni più piccole. Farlo manualmente porterebbe ad un grande spreco di tempo e al rischio di esporsi a diversi errori, la migliore soluzione è quella di scrivere un piccolo script che si occupi di dividere le istruzioni di “INSERT” in file più piccoli. Dividere un file con “INSERT” estese è abbastanza complesso quindi si rende necessario creare un Dump in un formato semplice, dove ogni istruzione deve essere sulla propria linea come illustrato di seguito.

    INSERT INTO `tabella` VALUES... 
    INSERT INTO `tabella` VALUES ... 
    INSERT INTO `tabella` VALUES ...
    

E’ possibile creare il file iniziale in formato semplice utilizzando phpMyAdmin o il seguente comando.

    mysqldump -u USER -p PASS --databases NOME_DATABASE --tables NOME TABELLA --extended-insert = FALSE > dump.sql
    

Una volta ottenuto il file di DUMP è possibile utilizzare il seguente script PHP per dividere in porzioni più piccole il file. Modificando la variabile “$max\_lines\_per_split” si imposta il numero massimo di linee contenute da ogni file di

    <?php    
      set_time_limit(600);    /* Numero di istruzioni 'insert' per file*/     
      $max_lines_per_split = 50000;   
      $dump_file = "dump.sql";    
      $split_file = "dump-split-%d.sql";      
      $dump_directory = "./sql-dump/";    
      $line_count = 0;    
      $file_count = 1;    
      $total_lines = 0;   
      $handle = @fopen($dump_file, "r");      
      $buffer = "";   
      if ($handle) {          
        while(($line = fgets($handle)) !== false) {             /* Legge solo le righe che contengono "Insert" */                  
          if(!preg_match("/insert/i", $line)) continue;               
          $buffer .= $line; $line_count++;                /* Copia il buffer nei file divisi */                                 
            if($line_count --> split. = $max_lines_per_split) { 
              $file_name = $dump_directory . sprintf($split_file, $file_count); 
              $out_write = @fopen($file_name, "w+"); 
              fputs($out_write, $buffer); 
              fclose($out_write); 
              $buffer = ''; 
              $line_count = 0; 
              $file_count++; 
            } 
        } 
        if($buffer) 
        { 
          /* Scrive le righe rimanenti */ 
          $file_name = $dump_directory . sprintf($split_file, $file_count); 
          $out_write = @fopen($file_name, "w+"); 
          fputs($out_write, $buffer); 
          fclose($out_write); 
        } 
        fclose($handle); 
        echo "done."; 
      } 
    ?>
    

Una volta che il file Dump è stato suddiviso in file più piccoli, si può ridurre ulteriormente la loro dimensione comprimendoli in gzip con il seguente comando.

    gzip dump-split-* 
    

Fonte: <http://www.codediesel.com/php/splitting-large-mysql-dump-files/>