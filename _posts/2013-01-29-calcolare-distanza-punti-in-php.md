---
id: 250
title: Calcolare la distanza tra due punti in PHP
date: 2013-01-29T09:51:15+00:00
author: Antonio Lanzolla
layout: post
guid: http://188.226.216.54/?p=250
permalink: /calcolare-distanza-punti-in-php/
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
  - 2778456506
twitter-text:
  - 'Calcolare la distanza tra due punti in #PHP'
twitter-hashtag:
  - '#php #programming'
categories:
  - Programmazione
tags:
  - php
  - snippets
---
Vi presento una funzione che può essere molto utile nello sviluppo di nuove applicazioni in PHP.
  
Questo metodo permette di calcolare la distanza tra due punti su una mappa, restituendo il risultato in tre diverse unità di misura, miglia, chilometri o miglia nautiche.

    function distance($lat1, $lon1, $lat2, $lon2, $unit) {
    
        $theta = $lon1 - $lon2;
        $dist = sin(deg2rad($lat1)) * sin(deg2rad($lat2)) +  cos(deg2rad($lat1)) * cos(deg2rad($lat2)) * cos(deg2rad($theta));
        $dist = acos($dist);
        $dist = rad2deg($dist);
        $miles = $dist * 60 * 1.1515;
        $unit = strtoupper($unit);
    
        if ($unit == "K") {
            return ($miles * 1.609344);
        } else if ($unit == "N") {
            return ($miles * 0.8684);
        } else {
             return $miles;
        }
    
    
    }
    

Per usare questa funzione basterà richiamare la funzione in questa maniera

    echo distance(32,9697, -96,80322, 29,46786, -98,53506, "k");