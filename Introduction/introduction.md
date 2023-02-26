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
Si noti che i passi 3, 4, 5 e 7 coinvolgono tutti il software (editor, compilatore, linker, debugger). Sebbene sia possibile utilizzare programmi separati per ciascuna di queste attività, un pacchetto software noto come ambiente di sviluppo integrato (IDE) raggruppa e integra tutte queste funzionalità. 


