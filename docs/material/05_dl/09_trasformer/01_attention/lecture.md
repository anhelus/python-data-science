<!-- https://www.geeksforgeeks.org/ml-attention-mechanism/ -->
# 5.9.1 - L'attention

Per descrivere il meccanismo dell'attention, possiamo usare una semplice ed efficace analogia.

Immaginiamo di interrompere lo studio di Python e del machine learning per andare a una festa. Una volta arrivati, nonostante il gran numero di persone presenti, ci mettiamo a discutere con un nostro amico di quello che abbiamo appreso durante il corso di Python. Grazie alle nostre incredibili capacità di concentrazione, riusciamo a concentrarci esclusivamente sulla conversazione con il nostro amico, ignorando il rumore di sottofondo della festa. In questo (estremamente irrealistico) scenario, il nostro sistema uditivo esercita una attenzione selettiva nei confronti della conversazione con il nostro amico, focalizzandosi esclusivamente sulle informazioni rilevanti in quel momento. In altre parole, il nostro cervello "migliora" la comprensione del parlato dando una priorità maggiore ai suoni che ci interessano e ignorando, per quanto possibile, quelli di background.

Questo meccanismo, che ci permette di dare una certa priorità a informazioni specifiche in determinati contesti, è detto meccanismo di attention. L'attention viene utilizzata, ad esempio, nel natural language processing per allineare porzioni pertinenti di una frase in ingresso. Senza affidarsi necessariamente a concetti come il reinforcement learning, i meccanismi di attention permettono alle reti neurali di assegnare vari pesi a diversi elementi in ingresso, migliorando la loro capacità di catturare informazioni cruciali e aumentare le performance in una varietà di compiti. Un esempio di questo, in ambito computer vision, è Google Street View, in particolare nell'identificazione dei numeri delle case.

## Meccanismo di attention

Un meccanismo di attention è un'architettura basata su rete neurale in un Encoder-Decoder che permette al modello di focalizzarsi su specifiche sezioni dell'input mentre esegue un compito. Assegna dinamicamente i pesi a diversi elementi nell'input, indicando la loro importanza o rilevanza. Incorporando l'attention, il modello può selettivamente focalizzarsi ed elaborare le informazioni più rilevanti, catturando dipendenze e relazioni nei dati. Questo meccanismo è particolarmente utile nei compiti che coinvolgono dati sequenziali o strutturali, come il natural language processing o la computer vision, in quanto permette al modello di gestire dipendenze a lungo termine e migliorare le performance osservando selettivamente le feature importanti o il contesto.

I modelli ricorrenti di visual attention utilizzano il reinforcement learning per focalizzare l'attenzione su aree chiave dell'immagine. Una RNN governa la peek network, che seleziona dinamicamente certe locazioni da esplorare nel tempo. Nei compiti di classificazione, questo metodo supera le CNN. Inoltre, questo framework va oltre l'identificazione delle immagini e può essere utilizzato per una varietà di applicazioni di reinforcement learning visivo, come aiutare i robot a scegliere i comportamenti per eseguire compiti specifici. Anche se l'uso più basilare di questa strategia è l'apprendimento supervisionato, l'uso del reinforcement learning permette decisioni più adattabili e flessibili basate su feedback di eventi passati e ricompense apprese durante il processo di apprendimento.

L'applicazione dei meccanismi di attention all'image captioning ha sostanzialmente migliorato la qualità e l'accuratezza delle caption generate. Incorporando l'attention, il modello impara a focalizzarsi su regioni pertinenti dell'immagine mentre crea ogni caption. Il modello può sincronizzare le modalità testuali e visive focalizzandosi su diverse aree dell'immagine in ogni momento grazie al meccanismo di attention. Focalizzandosi su oggetti importanti o su aree specifiche dell'immagine, il modello può produrre caption più dettagliate e appropriate nel contesto delle immagini. I modelli di image captioning basati sull'attention funzionano meglio nell'individuare dettagli più fini, gestire scene complesse e fornire caption coesive e informative che rispecchiano da vicino il materiale visivo.

Il meccanismom di attention è quindi una tencia usata nel machine learning e nel natural language processing per aumentare l'accuratezza del modello focalizzandosi sui dati rilevanti. Permette al modello di focalizzarsi su certe aree dei dati in ingresso, dando più peso a feature cruciali e non considerando quelle poco importanti. Ad ogni attributo in ingresso viene dato un certo peso, a secondao di qunato è imporante per l'output. Le perfomrance dei task che richiedono l'utilizzo dei meccanismi di attention sono state singificativamente migliori in diverse aree, incluse speech recognition, image captioning, e machine translation.

## Come funziona l'attention

Il meccanismo di attention in una rete neurale si articola di solito nei seguenti step.

1. Input encoding: la sequenza di dati in ingresso viene rappresentata o integrata usando un insieem (collezione) di rappresentazioni. Questo step trasforma quindi l'input in un formato che può essere elaborato dal meccanismo di attention.
2. Query generation: un nuovo vettore delle query viene gerato sulla base dello stato attuale, o del contesto, del modello. Questo vettore delle query rappresenta l'informazione sulla quale il modello vuole focalizzarsi, o che vole recuperare dall'input.
3. Key-Value Pair Creation: le rappresentazioni ddell'input sono divise in coppie chiavi-valreo. Le chiavi catturano l'informazione che sarà usata per determinare l'importanza o rilevanza, mentre i valori contengono i dati o l'informazione vere e proprie.
4. Similarity Computation: la similitudine tra il vettore delle query ed ogni key è calcoalto per misurare la loro compatiobilità o rilevanza. Diverse metriche possono essere utilizzate, come il prodotto scalare, la similarità coseno, o lo scaled dot product.

$$
Score(s,i) = h_s^{(1)} \cdot y_i \\

Score(s,i) = (h_s^{(2)})^T W y_I \\

Score(s,i) = v^T tanh (W [\frac{h_s}{y_i}]) \\
$$

dove:

* $h_s$ è lo stato nascosto dell'encoder sorgente alla posizione $s$;
* $y_i$ è lo stato nascosto del target dell'encoder alla posizione $i$;
* W è la matrice dei pesi
* v è il vettore dei pesi

5. Calcolo dei pesi dell'attention: i punteggi di similarità passano attraverso una funzione softmax per ottnere i pesi dell'attention. Questi pesi indicano l'importanza o rilevanza di ogni coppia chiave valore.

$$
a(s,i) = softmax(s(s,i))
$$

dove $a$ sono i pesi dell'attention, mentre $s$ sono i punteggi di similarità.

6. Weighted sum: i pesi dell'attention sono applicati ai valori corrispondenti, generando una sommma pesata. Questo step aggrega le informaizoni rilevanti dall'input basato sulla loro importanza determinata dal meccanismo di attention.

$$
c_t = \sum_{i=1}^T_s \alpha(s, i)h_j^{(1)}
$$

Qui, $T_s$ è il numero totale di coppie chiave-valore (ovvero, gli stati nascosti della sorgente) nell'encoder.

7. Context Vector: la somma pesata serve come context vector, rappresentando le informazioni attese o su cui si focalizza l'input, cattura il contesto rilevante per lo step o task corrente.
8. Integrazione con il modello: il vector context viene combianato con lo stato o la rappresentazione nascosta corrente del modello, fornendo ulteriori informaizoni o contesto per gli step o layer successivi del modello.
9. Ripeter: gli step dal 2 all'8 devono essere ripetuti per ogni step o iterazione del modello, permettendo al meccanismo di attention di focalizzarsi dinameicamente su diverse parti della sequenza o dei dati di input.

Incorporando un meccanismo di attention, il modello può catturare in maniera efficace le dipendenze, enfatizzando l'informazione importante, e focalizzando adattivamente su diversi elementi dell'input, portando a performance migliroate in task come machine translation, text summarization o image recognition.

##### Un esempio: l'attention per la machine translation

Il meccanismo di attention nella machine translation prevede tre componenti principali: l'Encoder, l'Attention ed il Decoder. L'Encoder elabora la sequenza di input e genera gli stati nascosti. L'Attention calcola la rilevanza tra gli stati nascosti del target attuale e quelli dell'encoder, generando i pesi dell'attention. Questi sono usati per calcolare un vettore dei contesti che cattura l'informazione rilevante a partire dagli stati nascosti dell'encoder. Infine, il Decoder prende il context vector e genera la sequenza di output. Questa architettura permette al modello di focalizzarsi su diverse parti della sequenza di input durante il processo di traduzione, migliraondo l'allineamento e la qualità della traduzione. Possiamo soservare tre sotto-parti o componenti dell'architettura dell'Attention Mechanism:

* Encoder
* Attention
* Decoder

Consideriamo la seguente architettura Encoder-Decoder con l'Attention.

FIGURA 01

L'encoder applica la Recurrent Neural Netowrk (RNN) o del modello transformer-based per elabroare in maneira iterativa la sequenza di input. L'encoder crea uno stato nascosto ad ogni step che continee i dati dal precedente stato nascosto e dal token di input attuale. La completa sequenza di input viene rappresentata da questi stati nascosti presi insieme.

FIGURA 02

Per esempio, nel caso precedente ci sono 4 frasi, per cui l'input è $x_0, x_1, x_2, x_3$. Ogni input va attraverso un layer di embedding, che può essere una RNN, una LSTM, una GRU o un trasformer. Ogni input genera una rappresentazione nascosta. Questo genera l'output per l'encoder $h_0, h_1, h_2, h_3$.

Per quello che riguarda il componente di attention, questo calcola l'importanza o rilevanza di ogni stato nascost dell'encoder rispetto allo stato nascosto del target attuale. Viene generato un context vector che cattura le ifnormazioni rilevanti dagli stati nascosti dell'encoder. Il meccanismo di attention può essere rappresentato matematicamente come segue:

* il nostro obiettivo è generare i context vector
* per esempio, il context vector $C_1$ ci dice quanta importanza ed attention dovrebbe dare agli input $x_0, x_1, x_2, x_3$.
* questo layer conteine a sua volta tre parti: la rete feed forward, ilc aclo del softmax, e la generazione del context vector.

FIGURA 03

La feed forward network è responsabile per trasformare lo stato nascosto obiettivo in una rappresentazione che sia compatibile con il meccnaismo di attention. Prende lo strato nascosto del target $h_{t-1}$ ed applica una trasformazione lienare seguita da una funzione di attivazione non lineare, come ad esempio una ReLU, per ottenere una nuova rappresentazione.

FIGURA 04

Ogni $A_{00}, A_{01}, A_{02}, A_{03}$ è una semplice rete neurale feed forward con un layer nascosto. L'input per questa rete feed forward è datop dalo stato precedentre del decoder e dall'output dello stato dell'encoder.

Ogni unità genera gli output $e_{00}, e_{01}, e_{02}, e_{03}$. con $e_{0i}=g(S_0, h_i)$, e $g$ funzikone di attivazione.

Attention weights o softmax calculation.

Una funzione softmax viene quindi usata per convernite i punteggi di similarità in attention weights. Quest governaon l'importanaza o attention data a ciascuno degli stati nascosti nell'encoder. Pesiu più alti indicano una maggiore rilevanza o importnaza.

FIGURA 05

$$
E_{Oi} = \frac{exp(e_{0i})}{\sum_{i=0}^3 exp(e_{o_i})}
$$

Questi $E_{00}, E_{01}, E_{02}, E_{03}$ sono chiamati *attention weights*, e decidono quanta importanza dovrebbe essere data ai rispettivi input. 

Generazione del context vector

Il context vector è la somma pesata degli stati nascosti dell'encoder, dove gli attention weight sono i pesi per la sommatoria. Rappresenta una specifica disposizione degli stati nascosti dell'encoder pertinenti alla generazione del token attuale.

FIGURA 06

$C_0 = E_{00} * h_0 + E_{01} * h_1 + E_{02} * h_2 + E_{03} * h_3$

Troviamo $C_1, C_2, C_3$ allo stesso modo e mandandolo a diverse unità RNN del layer di decoding. Questo è il vettore finale che è iol prodotto della probabilità di distribuzione e degli output dell'encoder, che non è altro se non l'attenzione data alle parole di input.

DECODER

Il context vector viene inviato al decoder assieme allo stato nascosto corrente del decoder epr prediure il prossimo token nella sequenza di output. Fino a che il decoder non genera l'intera sequenza di oputput, questo processo viene fatto in modo ricorsivo. Mandiamo questi context vector alle RNN del layer del decodeer. Ogni decoder produce un output che è la traduzione delle parole di input.

CONCLUSIONI

Il meccanismo di attention permette al decoder di focalizzare dinamicamente su diversi segmenti della sequenza di input sulla base della loro importanza per il corrente step di decoding. Come risutlato, il modello può gestire sequenze di input lunghe facilemnte e catturare le dipendenze tra i vari componenti della sequenza di input ed output. I meccanismi di attention è una componente cruciale di molti modelli sequence-to-sequence allo stato dell'arte, in quanto migliroano singificativamente la qualità e la flujenza delle sequenze generate.
