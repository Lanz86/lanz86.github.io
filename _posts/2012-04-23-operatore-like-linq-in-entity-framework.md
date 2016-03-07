---
id: 242
title: Operatore LIKE con Linq in Entity Framework
date: 2012-04-23T18:56:59+00:00
author: Antonio Lanzolla
layout: post
guid: http://188.226.216.54/?p=242
permalink: /operatore-like-linq-in-entity-framework/
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
  - 2778454210
twitter-text:
  - 'Operatore LIKE con #Linq in #EntityFramework'
twitter-hashtag:
  - '#csharp #dotnet'
categories:
  - Programmazione
tags:
  - .net
  - 'C#'
  - Entity Framework
  - linq
  - SQL Server
---
In _Entity Framework_ si ha la necessità di effettuare delle query di ricerca su stringhe.
  
In questo post mostrerò i vari metodi utilizzabili e la query SQL prodotta per prelevare i dati dal database.
  
Come base di partenza sarà utilizzato il noto database di esempio fornito da Microsoft, <a title="Database di esempio Northwind e pubs per SQL Server" href="http://www.microsoft.com/en-us/download/details.aspx?id=23654" target="_blank">Northwind</a>

### L’operatore di uguaglianza (Uguale a …)

Se vogliamo effettuare una ricerca con l’operatore di uguaglianza possiamo usare la query:

    var q = from c in db.Customers where c.City == "Bruxelles" select c;
    

Che restituirà tutti i record presenti nella tabella **Customers** che hanno il campo **City** uguale a **_Bruxelles_**.
  
La query generata per richiamare i dati dal database sarà :

    SELECT * FROM Costumers WHERE 'Rome' = City;
    

### L’operatore Like

Per utilizzare l’operatore _Like_ con _Linq_ nelle tre diverse possibilità che ci vengono proposte (**_Inizia con, Finisce con, Contiene_**) si possono utilizzare i seguenti metodi:

#### Inizia con

Per ricercare tutti gli elementi che iniziano per una determinata stringa possiamo utilizzare la query:

    var q = from c in db.Customers where c.City.StartsWith("B") select c;
    

Che restituirà tutti i record presenti nella tabella **Customers** che hanno il campo **City** che inizia per **_B_**.
  
La query generata per richiamare i dati dal database sarà :

    SELECT * FROM Customers WHERE City LIKE 'B%';
    

#### Finisce con

Per ricercare tutti gli elementi che finiscono per una determinata stringa possiamo utilizzare la query:

    var q = from c in db.Customers where c.City.EndsWith("B") select c;
    

Che restituirà tutti i record presenti nella tabella **Customers** che hanno il campo **City** che finisce per **_B_**.
  
La query generata per richiamare i dati dal database sarà :

    SELECT * FROM Customers WHERE City LIKE '%B';
    

#### Contiene

Per ricercare tutti gli elementi che contengono una determinata stringa possiamo utilizzare la query:

    var q = from c in db.Customers where c.City.Contains("B") select c;
    

Che restituirà tutti i record presenti nella tabella **Customers** che hanno il campo **City** contenente la string **_B_**.
  
La query generata per richiamare i dati dal database sarà :

    SELECT * FROM Customers WHERE City LIKE '%B%'
    

Potete scaricare un progetto di test da questo <a title="LinqStringWhere.zip" href="http://sdrv.ms/MLxIPx" target="_blank">link</a> dove viene mostrato l’utilizzo di questi metodi, i risultati e le query SQL prodotte.