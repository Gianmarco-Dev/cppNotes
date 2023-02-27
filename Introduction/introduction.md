## Introduzione allo sviluppo in C++
===============================


Prima di poter scrivere ed eseguire il nostro primo programma C++, dobbiamo capire più nel dettaglio come vengono sviluppati i programmi C++. Ecco un grafico che illustra un approccio semplicistico:

![Il processo di sviluppo del software](./img/image1.webp)

### Passo 1: Definire il problema che si desidera risolvere

Questa è la fase del "cosa", in cui si capisce quale problema si intende risolvere. L'idea iniziale di ciò che si vuole programmare può essere il passo più facile o più difficile. Ma concettualmente è il più semplice. Basta un'idea che possa essere ben definita e si è pronti per il passo successivo.

Ecco alcuni esempi:

- "Voglio scrivere un programma che mi permetta di inserire molti numeri e che calcoli la media".
- Voglio scrivere un programma che generi un labirinto in 2d e permetta all'utente di attraversarlo. L'utente vince se raggiunge la fine".
- Voglio scrivere un programma che legga un file con i prezzi delle azioni e preveda se le azioni saliranno o scenderanno".

### Fase 2: stabilire come risolvere il problema

Questa è la fase del "come", in cui si stabilisce come risolvere il problema proposto nella fase 1. È anche la fase più difficile da gestire. È anche la fase più trascurata nello sviluppo del software. Il nocciolo della questione è che ci sono molti modi per risolvere un problema, ma alcune di queste soluzioni sono migliori e altre peggiori. Troppo spesso abbiamo un'idea, ci sediamo e proviamo immediatamente a scrivere codice. Questo spesso genera una soluzione che rientra nella categoria delle cattive soluzioni.

In genere, le soluzioni valide hanno le seguenti caratteristiche:

- Sono semplici (non eccessivamente complicate o confuse).
- Sono ben documentate (soprattutto per quanto riguarda le ipotesi o le limitazioni).
- Sono costruite in modo modulare, in modo che le parti possano essere riutilizzate o modificate in seguito senza impattare su altre parti del programma.
- Sono robusti e possono recuperare o fornire messaggi di errore utili quando accade qualcosa di inaspettato.

Quando ci si siede e si inizia subito a programmare, di solito si pensa "voglio fare <qualcosa>", quindi si implementa la soluzione più veloce. Questo può portare a programmi fragili, difficili da modificare o estendere in seguito, o con molti bug.

Per inciso...

Il termine *bug* è stato usato per la prima volta da Thomas Edison nel 1870! Tuttavia, il termine è stato reso popolare negli anni '40 quando gli ingegneri trovarono una vera falena incastrata nell'hardware di un primo computer, causando un cortocircuito. Sia il registro in cui fu segnalato l'errore sia la falena fanno ora parte dello Smithsonian Museum of American History. È possibile consultarlo [qui] (https://americanhistory.si.edu/collections/search/object/nmah_334663).

Alcuni studi hanno dimostrato che solo il 20% del tempo di un programmatore viene effettivamente dedicato alla scrittura del programma iniziale. Il restante 80% è dedicato alla manutenzione, che può consistere nel debugging (eliminazione dei bug), negli aggiornamenti per far fronte ai cambiamenti dell'ambiente (ad esempio per funzionare su una nuova versione del sistema operativo), nei miglioramenti (piccole modifiche per migliorare l'usabilità o la capacità) o nei miglioramenti interni (per aumentare l'affidabilità o la manutenibilità).

Di conseguenza, vale la pena spendere un po' di tempo in più in anticipo (prima di iniziare la codifica) per pensare al modo migliore di affrontare un problema, alle ipotesi che si stanno facendo e a come si potrebbe pianificare il futuro, in modo da risparmiarsi molto tempo e problemi in futuro.

---
### Passo 3: scrivere il programma

I programmi che scriviamo utilizzando le istruzioni in C++ sono chiamati codice sorgente (spesso abbreviato in codice). È possibile scrivere un programma utilizzando qualsiasi editor di testo, anche un semplice blocco note di Windows o vi o pico di Unix. 

```
#include <iostream>

int main()
{
    std::cout << "Testo colorato!";
    return 0;
}
```


I programmi che si scrivono si chiamano in genere *qualcosa.cpp*, dove *qualcosa* è sostituito dal nome che si sceglie per il programma (ad esempio, calcolatrice, hi-lo, ecc.). L'estensione *.cpp* indica al compilatore (e a voi) che si tratta di un file di codice sorgente C++ che contiene istruzioni C++. Si noti che alcuni usano l'estensione .cc invece di .cpp, ma si consiglia di usare .cpp.

> **Best practice**

Nominare i file di codice *qualcosa.cpp*, dove *qualcosa* è un nome a vostra scelta e *.cpp* è l'estensione che indica che il file è un file sorgente C++.

Si noti inoltre che molti programmi C++ complessi hanno più file .cpp. Anche se la maggior parte dei programmi che creerete inizialmente avrà un solo file .cpp, è possibile scrivere programmi singoli con decine o centinaia di file .cpp.

Una volta scritto il nostro programma, i passi successivi consistono nel convertire il codice sorgente in qualcosa di eseguibile e nel verificare se se funziona.


---------------

## Introduzione a compilatore, linker e librerie

---------------

![Il processo di sviluppo del software](./img/image1.webp)


Discutiamo i passi da 4 a 7.

### Passo 4: Compilazione del codice sorgente

Per compilare un programma C++, si utilizza un compilatore C++. Il compilatore C++ esamina in sequenza ogni file di codice sorgente (.cpp) del programma e svolge due compiti importanti:

1) Innanzitutto, controlla il codice per verificare che segua le regole del linguaggio C++. In caso contrario, il compilatore segnala un errore (e il numero di riga corrispondente) per aiutare a individuare gli elementi da correggere. Il processo di compilazione viene interrotto finché l'errore non viene risolto.

In secondo luogo, traduce il codice sorgente C++ in un file di linguaggio macchina chiamato file oggetto (object file). I file oggetto sono in genere denominati *nome.o* o *nome.obj*, dove *nome* è lo stesso nome del file .cpp da cui è stato prodotto.

Se il programma ha 3 file .cpp, il compilatore genera 3 file oggetto:

![Il processo di compilazione](./img/image2.webp)


I compilatori C++ sono disponibili per molti sistemi operativi diversi. L'installazione di un compilatore verrà discussa a breve, quindi non è necessario farlo ora.

### Passo 5: Collegamento dei file oggetto e delle librerie

Dopo che il compilatore ha creato uno o più file oggetto, entra in gioco un altro programma chiamato **linker**. Il compito del `linker` è triplice:

1) Primo, prendere tutti i file oggetto generati dal compilatore e combinarli in un unico programma eseguibile.


![Il processo di linking](./img/image3.webp)

2) In secondo luogo, oltre a poter collegare i file oggetto, il `linker` è anche in grado di collegare i **file di libreria**. Un file di libreria è una raccolta di codice precompilato che è stato "impacchettato" per essere riutilizzato in altri programmi.

Il nucleo del linguaggio C++ è in realtà piuttosto piccolo e conciso (e in queste esercitazioni ne imparerete molto). Tuttavia, il C++ è dotato di un'ampia libreria chiamata C++ Standard Library (solitamente abbreviata in *standard library*) che fornisce funzionalità aggiuntive che possono essere utilizzate nei programmi. Una delle parti più comunemente utilizzate della libreria standard del C++ è la libreria *iostream*, che contiene funzionalità per la stampa di testo su un monitor e per ricevere input da tastiera da un utente. Quasi ogni programma C++ scritto utilizza la libreria standard in qualche forma, quindi è molto comune che la libreria standard venga collegata ai programmi. La maggior parte dei `linker` collega automaticamente la libreria standard non appena se ne utilizza una parte, quindi in genere non è un problema di cui preoccuparsi.

È anche possibile collegare facoltativamente altre librerie. Per esempio, se dovessimo scrivere un programma che riproduce suoni, probabilmente non vorremmo scrivere noi il codice per leggere i file sonori dal disco, controllare che siano validi o capire come indirizzare i dati sonori al sistema operativo o all'hardware per riprodurli attraverso l'altoparlante... sarebbe un sacco di lavoro inutile. Invece, probabilmente scaricheremo una libreria che sa già come fare queste cose e la userete. Parleremo di come collegare le librerie (e crearne di proprie) nell'appendice.

In terzo luogo, il linker si assicura che tutte le dipendenze tra file siano risolte correttamente. Ad esempio, se si definisce qualcosa in un file .cpp e poi lo si usa in un altro file .cpp, il linker collega i due file. Se il linker non è in grado di collegare un riferimento a qualcosa con la sua definizione, si otterrà un errore del linker e il processo di collegamento verrà interrotto.

Una volta che il linker ha finito di collegare tutti i file oggetto e le librerie (supponendo che tutto vada bene), si avrà un file eseguibile che potrà essere eseguito.



Per progetti complessi, alcuni ambienti di sviluppo utilizzano un **makefile**, ovvero un file che descrive come costruire un programma (ad esempio quali file compilare e collegare, o comunque elaborare in vari modi). Sono stati scritti interi libri su come scrivere e mantenere i makefile, che possono essere uno strumento incredibilmente potente. Tuttavia, poiché i makefile non fanno parte del nucleo del linguaggio C++ e non è necessario utilizzarli per procedere nello studio di C++, ne parleremo più avanti.

### Passi 6 e 7: test e debug

Questa è la parte più divertente (si spera). Possiamo eseguire il nostro eseguibile e vedere se produce l'output che ci aspettiamo.

Se il programma viene eseguito ma non funziona correttamente, è il momento di eseguire il debug per capire cosa c'è che non va. Parleremo presto di come testare i programmi e di come eseguirne il debug in modo più dettagliato.


---------------

## Ambienti di sviluppo integrati (IDE)

---------------
**Creare Progetti nell'IDE**

Per scrivere un programma C++ all'interno di un IDE, di solito si inizia creando un nuovo progetto. Un progetto è un contenitore che contiene tutti i file di codice sorgente, le immagini, i file di dati, ecc... necessari per produrre un eseguibile (o una libreria, un sito web, ecc...) da eseguire o utilizzare. Il progetto salva anche varie impostazioni dell'IDE, del compilatore e del linker, oltre a ricordare il punto in cui si è lasciato, in modo che quando si riapre il progetto in un secondo momento, lo stato dell'IDE può essere ripristinato al punto in cui si era lasciato. Quando si sceglie di compilare il programma, tutti i file .cpp del progetto vengono compilati e collegati.

Ogni progetto corrisponde a un programma. Quando si è pronti a creare un secondo programma, è necessario creare un nuovo progetto o sovrascrivere il codice di un progetto esistente (se non lo si vuole conservare). I file di progetto sono generalmente specifici per l'IDE, quindi un progetto creato per un IDE dovrà essere ricreato in un IDE diverso.

**Best practise**

> Creare un nuovo progetto per ogni nuovo programma scritto.

---
### Progetti via console

Quando si crea un nuovo progetto, generalmente viene chiesto quale tipo di progetto si vuole creare. Tutti i progetti che creeremo in questo tutorial saranno `progetti console`. Un progetto console significa che creeremo programmi che possono essere eseguiti dalla console di Windows, Linux o Mac.

Ecco una schermata della console di Windows:

![console Windows](./img/image4.webp)


Per impostazione predefinita, le applicazioni per console non hanno un'interfaccia grafica (GUI), stampano testo sulla console, leggono input dalla tastiera e sono compilate in file eseguibili autonomi. Questo è perfetto per imparare il C++, perché mantiene la complessità al minimo e garantisce il funzionamento su un'ampia gamma di sistemi.

Non preoccupatevi se non avete mai usato una console o se non sapete come accedervi. Compileremo e lanceremo i nostri programmi attraverso i nostri IDE (che richiameranno la console quando necessario).

### Workspace / Solutions

Quando si crea un nuovo progetto per il proprio programma, molti IDE aggiungono automaticamente il progetto a un "workspace" o a una "solution" (il termine varia a seconda dell'IDE). Uno spazio di lavoro o una soluzione è un contenitore che può contenere uno o più progetti correlati. Ad esempio, se si sta scrivendo un videogame e si vuole avere un eseguibile separato per il giocatore singolo e per il multigiocatore, è necessario creare due progetti. Non avrebbe senso che entrambi i progetti fossero completamente indipendenti: dopo tutto, fanno parte dello stesso gioco. Molto probabilmente, ognuno di essi sarà configurato come progetto separato all'interno di un singolo spazio di lavoro/soluzione.

---
Anche se è possibile aggiungere più progetti a una singola soluzione, in genere si consiglia di creare un nuovo spazio di lavoro o una nuova soluzione per ogni programma, soprattutto durante l'apprendimento. È più semplice e ci sono meno possibilità che qualcosa vada storto.


---

### Hello World
Ora creiamo un nuovo file chiamato helloworld.cpp e incolliamo questo codice sorgente:
```
#include <iostream>

int main()
{
	std::cout << "Hello, world!";
	return 0;
}
```


Ora compiliamo con il compiler installato (ad esempio MYI2 su VSCODE). Verra' creato un file .exe che potremmo eseguire anche in console.



----


## Differenze tra le opzioni compile, build, rebuild, clean e run/start nel mio IDE

Prima abbiamo visto come per produrre un file eseguibile, ogni file di codice di un programma viene compilato in un file oggetto e poi i file oggetto vengono collegati in un eseguibile.

Quando un file di codice viene compilato, l'IDE può memorizzare il file oggetto risultante. In questo modo, se il programma viene compilato di nuovo in futuro, qualsiasi file di codice che non è stato modificato non deve essere ricompilato: il file oggetto memorizzato nella cache dall'ultima volta può essere riutilizzato. Questo può accelerare notevolmente i tempi di compilazione (al costo di un po' di spazio su disco).

Con questo in mente, ecco cosa fa di solito ciascuna delle opzioni:

- **Build** compila tutti i file di codice *modificati* nel progetto o nell'area di lavoro/soluzione, quindi collega i file oggetto in un eseguibile. Se nessun file di codice è stato modificato dall'ultima compilazione, questa opzione non fa nulla.
- **Clean** rimuove tutti gli oggetti e gli eseguibili memorizzati nella cache, in modo che alla successiva compilazione del progetto tutti i file vengano ricompilati e venga prodotto un nuovo eseguibile.
- **Rebuild** esegue una "pulizia", seguita da una "compilazione".
- **Compile** ricompila un singolo file di codice (indipendentemente dal fatto che sia stato memorizzato nella cache in precedenza). Questa opzione non richiama il linker né produce un eseguibile.
- **Run/start** esegue l'eseguibile di una precedente compilazione. Alcuni IDE (ad esempio Visual Studio) invocano un "build" prima di eseguire un "run", per assicurarsi di eseguire l'ultima versione del codice. Altri (ad esempio Code::Blocks) eseguono semplicemente l'eseguibile precedente.

Anche se parliamo informalmente di "compilazione" dei nostri programmi, per compilarli effettivamente scegliamo l'opzione "build" (o "run") nel nostro IDE.



---
## Configurazione del compilatore

Una configurazione di compilazione (chiamata anche target di compilazione) è un insieme di impostazioni del progetto che determina il modo in cui l'IDE costruirà il progetto. La configurazione di compilazione include tipicamente elementi come il nome dell'eseguibile, le directory in cui l'IDE cercherà altri file di codice e di libreria, se mantenere o eliminare le informazioni di debug, quanto ottimizzare il programma da parte del compilatore, ecc. In genere, si consiglia di lasciare queste impostazioni ai valori predefiniti, a meno che non ci sia una ragione specifica per cambiare qualcosa.

Quando si crea un nuovo progetto nell'IDE, la maggior parte degli IDE imposta due diverse configurazioni di compilazione: una configurazione di rilascio e una configurazione di debug.

**La configurazione di debug** è progettata per aiutare l'utente a eseguire il debug del programma ed è generalmente quella che si usa quando si scrivono i programmi. Questa configurazione disattiva tutte le ottimizzazioni e include le informazioni di debug, rendendo i programmi più grandi e più lenti, ma molto più facili da debuggare. La configurazione di debug è di solito selezionata come configurazione attiva per impostazione predefinita. Parleremo meglio delle tecniche di debug in una lezione successiva.

**La configurazione release** è pensata per essere usata quando si rilascia il programma al pubblico. Questa versione è tipicamente ottimizzata per le dimensioni e le prestazioni e non contiene le informazioni di debug aggiuntive. Poiché la configurazione di rilascio include tutte le ottimizzazioni, questa modalità è utile anche per testare le prestazioni del codice (cosa che verrà mostrata più avanti nella serie di esercitazioni).

Se ad esempio prendessimo il programma *Hello World* costruito con Visual Studio, l'eseguibile prodotto nella configurazione di debug sarebbe di 65kb, mentre l'eseguibile costruito nella versione di rilascio di 12kb. La differenza è in gran parte dovuta alle informazioni di debug in più conservate nella build di debug.

Anche se è possibile creare configurazioni di compilazione personalizzate, raramente se ne ha motivo, a meno che non si vogliano confrontare due compilazioni realizzate con impostazioni diverse del compilatore.

> **La best practise**: Durante lo sviluppo dei programmi, utilizzare la configurazione di compilazione *debug*. Quando si è pronti a rilasciare l'eseguibile ad altri o si vogliono testare le prestazioni, utilizzare la configurazione di compilazione *release*.


==============================================

## Estensioni del compilatore

Lo standard C++ definisce le regole su come i programmi devono comportarsi in determinate circostanze. Nella maggior parte dei casi, i compilatori seguono queste regole. Tuttavia, molti compilatori implementano le proprie modifiche al linguaggio, spesso per migliorare la compatibilità con altre versioni o per ragioni storiche. Questi comportamenti specifici del compilatore sono chiamati *estensioni del compilatore*.

La scrittura di un programma che fa uso di un'estensione del compilatore consente di scrivere programmi incompatibili con lo standard C++. I programmi che utilizzano estensioni non standard generalmente non vengono compilati da altri compilatori (che non supportano le stesse estensioni) o, se lo fanno, potrebbero non essere eseguiti correttamente.

È frustrante che le estensioni del compilatore siano spesso abilitate per impostazione predefinita. Questo è particolarmente dannoso per i nuovi programmatori, che possono pensare che un comportamento che funziona faccia parte dello standard ufficiale di C++, mentre in realtà il loro compilatore è semplicemente troppo permissivo.

Poiché le estensioni del compilatore non sono mai necessarie e causano la non conformità dei programmi agli standard C++, si consiglia di disattivare le estensioni del compilatore.

> Best practise: Disattivare le estensioni del compilatore per garantire che i programmi (e le pratiche di codifica) siano conformi agli standard C++ e funzionino su qualsiasi sistema.