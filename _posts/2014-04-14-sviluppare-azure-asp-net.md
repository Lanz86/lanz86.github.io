---
id: 253
title: Sviluppare con Azure e Asp.Net
date: 2014-04-14T09:57:24+00:00
author: Antonio Lanzolla
layout: post
guid: http://188.226.216.54/?p=253
permalink: /sviluppare-azure-asp-net/
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
  - null
twitter-text:
  - 'Sviluppare con #Azure e #Asp.Net'
twitter-hashtag:
  - '#aspnet #cloud'
categories:
  - Cloud
  - Programmazione
tags:
  - .net
  - asp.net
  - ASP.NET MVC
  - ASP.NET Web Forms
  - Azure
  - 'C#'
  - Entity Framework
  - SQL Server
---
Questa guida ti mostrerà come creare una applicazione web <a title="ASP.NET" href="http://www.asp.net/" target="_blank"><em>ASP.NET</em></a> ed effetturare il deploy su <a title="Azure Web Sites" href="http://azure.microsoft.com/it-it/solutions/web/" target="_blank"><em>Azure Web Sites</em></a> utilizzando <a title="Visual Studio 2013" href="http://www.visualstudio.com/downloads/download-visual-studio-vs" target="_blank"><em>Visual Studio 2013</em> </a>o <a title="Visual Studio 2013 Express per il Web" href="http://www.microsoft.com/it-it/download/details.aspx?id=40747" target="_blank"><em>Visual Studio 2013 Express per il Web</em></a>. La guida presuppone che tu non abbia mai avuto precedenti esperienze con <a title="Azure Site" href="http://azure.microsoft.com/" target="_blank"><em>Azure</em> </a>e/o _<a title="ASP.NET" href="http://www.asp.net" target="_blank">ASP.NET</a>_.

Al completamento della guida, avrai una semplice e funzionante applicazione web che gira sul cloud.

Puoi aprire un account *<a title="Azure Site" href="http://azure.microsoft.com/" target="_blank">Azure</a> *gratuitamente, se non disponi di <a title="Visual Studio 2013" href="http://www.visualstudio.com/downloads/download-visual-studio-vs" target="_blank"><em>Visual Studio 2013</em></a>, l’SDK viene automaticamente installato con <a title="Visual Studio 2013 Express per il Web" href="http://www.microsoft.com/it-it/download/details.aspx?id=40747" target="_blank"><em>Visual Studio 2013 Express per il Web</em></a>. Quindi si può cominciare a sviluppare per *<a title="Azure Site" href="http://azure.microsoft.com/" target="_blank">Azure</a> *totalmente gratis.

Cosa imparerai da questa guida:

  * Come configurare la macchina per lo sviluppo installando l’_<a title="Azure SDK per Visual Studio 2013" href="http://go.microsoft.com/fwlink/?linkid=324322" target="_blank">Azure SDK</a>_.
  * Come creare un progetto Web _<a title="ASP.NET" href="http://www.asp.net" target="_blank">ASP.NET</a>_ con <a title="Visual Studio" href="http://www.visualstudio.com/" target="_blank"><em>Visual Studio</em></a> ed effettuare il deploy su <a title="Azure Web Sites" href="http://azure.microsoft.com/it-it/solutions/web/" target="_blank"><em>Azure Web Sites</em></a>.
  * Come apportare modifiche al progetto e ripubblicarlo sul Cloud.

L’illustrazione seguente mostra come si presenterà l’applicazione completa.

[<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/deployedandazure.png" alt="Web site home page" width="648" height="398" />](https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.win…/articles/web-sites-dotnet-get-started/20140331024459/deployedandazure.png)

> ##### NOTA:
> 
> Per completare questa guida, è necessario che registri un account Azure. Se non disponi di un account, puoi attivare i <a title="Benefici di Azure per gli abbonati MSDN" href="http://azure.microsoft.com/it-it/pricing/member-offers/msdn-benefits-details/" target="_blank">Benefici di Azure per gli abbonati MSDN</a> o creare un a<a title="Abbonamento di prova gratuito" href="http://azure.microsoft.com/en-us/pricing/free-trial" target="_blank">bbonamento di prova gratuito</a>.

### Sommario:

  * Impostare l’ambiente di sviluppo
  * Creare un progetto Web _<a title="ASP.NET" href="http://www.asp.net" target="_blank">ASP.NET</a>_ in <a title="Visual Studio" href="http://www.visualstudio.com/" target="_blank"><em>Visual Studio</em></a>
  * Distribuire l’applicazione su _<a title="Azure Site" href="http://azure.microsoft.com/" target="_blank">Azure</a>_
  * Modificare il progetto e ridistribuire l’applicazione su _<a title="Azure Site" href="http://azure.microsoft.com/" target="_blank">Azure</a>_

## Impostare l’ambiente di sviluppo

Per cominciare bisogna impostare l’ambiente di sviluppo installando l’_<a title="Azure SDK per Visual Studio 2013" href="http://go.microsoft.com/fwlink/?linkid=324322" target="_blank">Azure SDK</a>_ per .Net

  1. Per installare l’SDK, clicca sul link sottostante. Questa guida utilizza <a title="Visual Studio 2013" href="http://www.visualstudio.com/downloads/download-visual-studio-vs" target="_blank"><em>Visual Studio 2013</em></a>. Se non l’avete ancora installato ed installerete <a title="Visual Studio 2013 Express per il Web" href="http://www.microsoft.com/it-it/download/details.aspx?id=40747" target="_blank"><em>Visual Studio 2013 Express per il Web</em></a> l’SDK verrà installato assieme allo stesso. 
      * <a title="Azure SDK per Visual Studio 2013" href="http://go.microsoft.com/fwlink/?linkid=324322" target="_blank">Azure SDK per Visual Studio 2013<br /> </a>
    
    \*\*Nota: \*\*A seconda delle dipendenze già installate nel vostro PC l’installazione dell’SDK potrebbe richiedere molto tempo, da pochi minuti a una mezzora circa.
    
      * Quando viene richiesto di eseguire o salvare l’eseguibile, fai click su **Esegui**.
      * Si aprirà una finestra di _Web Platform Installer_, fai click su **Install** e procedi con l’installazione
  
        <img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/includes/install-sdk-2013-only/webpi46.png" alt="Web Platform Installer" width="617" height="419" />Quando l’installazione è completa avrai tutto il necessario per iniziare a sviluppare.

## Creare un’applicazione Web ASP.NET

Il primo passo è quello di creare un nuovo progetto web. <a title="Visual Studio" href="http://www.visualstudio.com/" target="_blank"><em>Visual Studio</em></a> crea in maniera automatica il template del progetto e il collegamento al <a title="Azure Web Sites" href="http://azure.microsoft.com/it-it/solutions/web/" target="_blank"><em>Azure Web Sites</em></a>.

  1. Apri <a title="Visual Studio 2013" href="http://www.visualstudio.com/downloads/download-visual-studio-vs" target="_blank"><em>Visual Studio 2013</em></a> o <a title="Visual Studio 2013 Express per il Web" href="http://www.microsoft.com/it-it/download/details.aspx?id=40747" target="_blank"><em>Visual Studio 2013 Express per il Web</em></a>.
  2. Dal menù **File**, clicca sulla voce **New Project<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13newproj.png" alt="Nuovo progetto dal menu File" width="800" height="450" />**
  3. Nella finestra di dialogo, espandi **C# \*\*o \*\*Visual Basic** e seleziona **Web** tra i modelli installati, quindi seleziona **ASP.NET Web Application**.
  4. Assicurati di selezionare come framework di destinazione **.NET Framework 4.5**.
  5. Rinomina l’applicazione come M**yExample** e clicca su **OK**.
  
    **<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13newproj.png" alt="Nuovo progetto dal menu File" width="800" height="450" />**
  6. Nella finestra di dialogo **New ASP.NET Project**, seleziona il modello di applicazione che vuoi realizzare tra **MVC** o **Web Forms** e quindi clicca su **Change Autentication**.
  
    > **MVC** e **Web Forms** sono due diversi framework per la creazione di Web Application. Se non hai preferenze o requisiti stringenti ti consiglio di utilizzare **MVC**, perchè troverai diversi tutorial basati su questo framework.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13changeauth.png" alt="Finestra di dialogo Nuovo progetto ASP.NET" width="770" height="575" />

  7. Nella finestra di dialogo **Change Authentication** fai click sull’opzione **No Authentication** e quindi clicca sul pulsante **OK**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13noauth.png" alt="Nessuna autenticazione" width="576" height="256" />
  
    > L’applicazione che utilizzeremo in questo esempio non sfrutta alcun sistema di autenticazione per questo possiamo impostare **No Authentication**.

  8. Nella finestra di dialogo lascia spuntata la casella di controllo **Host in the cloud** o **Create remote resources \*\*e il menu a discesa impostato su \*\*Web Site**. Queste impostazioni indicano che Visual Studio crea un **Web Site Azure** per il vostro progetto web.
  9. Nella finestra **New ASP.NET** **Project** clicca su **OK**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13newaspnetprojdb.png" alt="Finestra di dialogo Nuovo progetto ASP.NET" width="770" height="575" />
  
    > La schermata mostra la selezione del modello **MVC**; se hai scelto **Web Forms** si vedrai esso selezionato.

 10. Se non ti sei loggato su Azure, Visual Studio ti chiederà di farlo. Clicca sul pulsante **Sign In**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/signin.png" alt="Accedi a Azure" width="621" height="382" />
 11. Inserisci il tuo UserId e la tua password dell’accont Azure.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/signindb.png" alt="Accedi a Azure" width="581" height="451" />Effettuato l’accesso, verrà visualizzata una finestra di dialogo **Configure Windows Azure Site** dove devi impostare le risorse che desideri utilizzare o creare.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/configuresitesettings.png" alt="Configure Windows Site Azure" width="579" height="440" />
 12. Visual Studio fornisce di default un **Site Name** che verrà utilizzato da Azure come prefisso per l’URL dell’applicazione. Se preferisci puoi inserire un nome diverso.L’url completo sarà composto dal site name più il dominio che si vede accanto al campo **Site Name**. Ad esempio se il **Site Name** è `MyExample6442`, l’URL dell’applicazione sarà `MyExample6442.azurewebsites.net`. Se il **Site Name** scelto è già stato utilizzato, viene visualizzato un punto esclamativo rosso alla destra invece di un segno di spunta verde, quindi bisognerà scegliere un nome diverso.
 13. L’elenco a discesa **Region** scegli la posizione più vicina alla tua.
  
    > Questa impostazione specifica in quale Data Center Azure verrà eseguita l’applicazione.

 14. Lascia il campo database invariato.
  
    Per questa guida non si utilizzerà un database.
 15. Fai click su **OK**.In pochi secondi, Visual Studio crea un **Web Project** nella cartella specificata e un sito **Azure Web** nel Data Center specificato.Il Solution Explorer mostra i file e le cartelle del nuovo progetto creato. (L’immagine sottostante è di un progetto **Web Forms**, un progetto **MVC**, ha diversi file e cartelle.)<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/solutionexplorer.png" alt="Solution Explorer" width="320" height="637" />
  
    La finestra **Web Publish Activity** indica che il progetto è stato creato.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13sitecreated1.png" alt="Sito Web creato" width="332" height="198" />

## Distribuire l’applicazione su Azure

  1. Nella finestra **Web Publish Activity** clicca sul link **Publish MyExample to this site now**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13sitecreated.png" alt="Sito Web creato" width="332" height="198" />
  
    In pochi secondi appare la finestra **Publish Web**. Da questa finestra è possibile, attraverso una procedura guidata, creare un nuovo _profilo di pubblicazione_, che contiene le impostazioni che permettono a Visual Studio di distribuire il progetto su Azure. Il profilo viene salvato automaticamente in modo che l’apporto di ulteriori modifiche al progetto siano facilmente ridistribuibili.
  2. Nella scheda **Connection** della finestra di configurazione guidata **Publish Web** clicca sul pulsante **Validate** **Connection** per assicurarti che Visual Studio sia in grado di connettersi ad Azure.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13validateconnection.png" alt="Convalida connessione" width="720" height="565" />
  
    Se la connessione è valida verrà visualizzato un segno di spunta verde accanto al pulsante **Validate Connection**.
  3. Fare click su **Next**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13validateconnectionsuccess.png" alt="Collegamento validato con successo" width="718" height="141" />
  4. Nella scheda **Settings** fai click su **Next**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13settingstab.png" alt="Scheda Impostazioni" width="720" height="565" />
  
    È possibile accettare le impostazioni predefinite in questa scheda. In questo caso si stà pubblicando un build di produzione e quindi non è necessario eliminare i file dal server di destinazione, precompilare l’applicazione, o escludere i file nella cartella App_Data.
  5. Nella scheda **Preview** fare click sul pulsante **Start Preview**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13preview.png" alt="Start Preview" width="720" height="565" />
  
    Questa scheda visualizza l’elenco dei file che verranno copiati sul server. Questa funzione non pubblica i file sul server, ma permette di visualizzare quali file saranno aggiunti e/o modificati.
  6. Fare click sul pulsante **Publish**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13previewoutput.png" alt="Publish Visual Studio Azure" width="720" height="565" />
  
    Visual Studio inizierà il processo di pubblicazione dell’applicazione sul server di Azure. Le schede **Output** e **Web Publish Activity** mostrano la situazione della pubblicazione.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/publishoutput.png" alt="Web Publish Activity and Output" width="608" height="401" />
  
    Appena termina il processo di pubblicazione, se è andato tutto a buon fine, viene aperto automaticamente il browser predefinito che punta al sito web appena pubblicato. In questo momento l’applicazione e stata distribuita ed è in esecuzione sul cloud. L’URL nella barra degli indirizzi dimostra che il sito viene caricato dal Web.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/gs13deployedsite.png" alt="Sito Web in esecuzione in Azure" width="668" height="397" />
  7. Chiudi il browser.

## Fare una modifica è ridistribuire l’applicazione

In questa sezione, vedremo como modificare il progetto web, eseguirlo localmente sul computer di sviluppo per verificare che la modifica sia effettiva e funzionante e poi pubblicare questa modifica su Azure.

  1. Se hai creato un progetto **MVC**, apri da Solution Explorer il file _Views/Home/Index.cshtml_ o .vbhtml. modifica il contenuto del tag **H1** da “ASP.NET” a “ASP.NET e Azure” e salva il file.
  
    <img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/index.png" alt="Mvc Index" width="226" height="217" />
  
    <img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/mvcandazure.png" alt="Modifica tag H1" width="565" height="154" />
  2. Se invece hai creato un progetto di tipo **Web Forms**, apri il file _Default.aspx_ in **Solution Explorer**, e modifica il tag **H1** da “ASP.NET” a “ASP.NET e Azure” e salva il file.
  
    <img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/default.png" alt="Web Forms Default.aspx" width="222" height="212" /><img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/wfandazure.png" alt="Variazione Web Form h1" width="587" height="119" />
  3. Premi CTRL + F5 per testare la modifica eseguendo l’applicazione sul tuo computer.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/localandazure.png" alt="Sito Web esecuzione locale" width="670" height="398" />
  
    Di default l’esecuzione dell’applicazione in locale con Visual Studio 2013 avviene attraverso IIS Express che è una versione leggera di IIS progettata per l’utilizzo durante lo sviluppo di applicazioni web.
  4. Chiudi il browser.
  5. In **Solution Explorer**, clicca con il tasto destro del mouse sul progetto e scegli **Publish**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/choosepublish.png" alt="Publish Solution Explorer" width="526" height="355" />
  
    Viene visualizzata la finestra **Publish Web** già impostata sulla scheda **Preview**.\*\* \*\*Se vuoi puoi modificare le impostazioni di pubblicazione, ma in questo caso pubblicheremo gli aggiornamenti con le stesse impostazioni.
  6. Nella finestra **Publish Web** fai click sul pulsante **Publish**.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/clickpublish.png" alt="Publish update" width="720" height="565" />Visual Studio pubblica il progetto su Azure e apre il browser predefinito.<img class="aligncenter" src="https://wacomdpsstorage.blob.core.windows.net/articlesmedia/content-ppe.windowsazure.com/en-us/documentation/articles/web-sites-dotnet-get-started/20140331024459/deployedandazure.png" alt="Sito moficato su Azure" width="648" height="398" />

In questa guida hai visto come è facile creare una semplice applicazione web e pubblicarla sul Cloud di Azure.

Puoi trovare la versione completa in inglese di questa guida all’URL <a title="Azure Begin" href="http://azure.microsoft.com/en-us/documentation/articles/web-sites-dotnet-get-started/" target="_blank" rel="nofollow">http://azure.microsoft.com/en-us/documentation/articles/web-sites-dotnet-get-started/</a>