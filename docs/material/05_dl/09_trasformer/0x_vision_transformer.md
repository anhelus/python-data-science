# Vision Trasformer

<!-- https://www.geeksforgeeks.org/vision-transformers-vit-in-image-recognition/ -->

Le CNN sono state all'avanguardia dei progressi nella image recognition negli ultimi dieci anni. Tuttavia, il campo è stato profondamente trasformato dall'introduzione del *Vision Transofrmer* (ViT), che hanno portato i principi dell'architettura dei trasformer alkle immagini. I ViT hanno mostrato un grande successo ind iversi trask di image recognition, offrendo un nuovo punto di vistra sull'elaborazione di informazioni visive.

L'idea alla base del ViT è trattare immagini come sequenze, in modo simile a come le parole vengono trattate nel natural language processing. Questo approccio innovativo permette di applicare l'archioettura dei trasformer ai task di image recognition, cambiando in modo fondamentale come l'immagine viene elabroata. La struttura comprende un certo nuemro di elementi essenziali.

1. Image patching

Il primos tep nel ViT è l'ìimage patching, ovvero dividere l'immagine in patch di piccola dimensione predeterminata. Ad esempio, un'immagine 224 x 224 può essere segmentata in patch da 16x16, il che risulta in 196 patch. Ogni patch viene quindi vettorizzata, permettendo al modello di lavorare con questi pezzi di immagini più piccoli e gestibili.

2. Positional Encoding

Per mnantenere l'informazione posizionale sulle immagini, il positional encoding viene aggiunto agli embedding delle patch. Qeusto step fondamentale si assicura che il modello comprenda dove è collocata ciascuna patch nell'immagine originaria, permettendo di catturare le relaizoni spaziali in manier aefficace.

3. Multi-Layer Transformer Encoder

Il cuore del ViT è il suo *multi-layer transformer encoder*. Questa struttura consiste di:

* layer di self-attention, che permettono al modello div aluatre la relazione tra diverse patch, aiutandolo a comprendere come queste interagiscono tra loro;
* layer di feed-forward, che applicano trasformazioni non lineari all'output del meccanismo di self-attention, migliorando la capacità del modello di catturare pattern complessi nei dati.

4. Classification Head

La *classificaiton head* è una componente critica del ViT, utilzizata per generare predizioni per i task di image recognion. Un token spoeciale, spesso chiamato *classification token* (CLS), consolida l'informazione da tutte le patch, producendo le predizioni finali. Questa aggregazione di dati assicura che il modello sfrutti informazioni da tutta l'immagine piuttosto che da patch isolate.

## COme funzionano i ViT?

I ViT sfruttano un'architettura unica per elaborare le immagini, trattandole come sequenze di patch. Qeusto approccio permette al modello di sfruttare la potenza dei trasfomrere, particolarmente attraverso lì'uso di meccahinsmi di eself-attention. I ViT iniziano dividendo l'immaigini in patch di piccola dimensione prefissata. Ogni patch viene quindi elabroata in maniera individaurle come parte di una sequezna, permettendo al modello di analizzare l'intera immagine attraverso i suoi componenti.

Il meccanismo di self-attention è fondamentale per comprendere il funzionamento del ViT. Questo meccanismo permette ad ogni patch di influenzare la raprpsentazione di altre patch. Specificamente, calcola i punteggi di attention che determinaoo quanto focus ogni patch deve avere su ogni altra pathc. Questa capacità di pesare l'importanza di diverse patch permette ai ViT di comprendere dlele connessioni ed interdipendenze complesse nell'intera immagine. COnseguentemente, i ViT possono creare delle rappresentazioni più coimplete e dettagliate, catturando apttern compelssi che potrebbero essere persi dalle tradizionali reti convoluzionali.

Il processo di addestramento del ViT prevede il modificare i parametir del modello per minimizzare l'errore di predizione suin dataset etidcdhettati. Questo è simile al processo di addestramento di altre architetture di rete neurale, dove:

1. la loss function viene dfinita per 2unatificare la differenza tra gli output predetti ed il abel veri e propri
2. la backprogapagion viene usata dal modello per aggiornare i suoi pesi sulla base della loss calcolata, rifinendo la sua abilità di fare predizioni arccurate
3. ottimizzazione: varie algritmi di ottimizzazzione (ad esempio, Adam o SGD) sono usati per migliroare il processo di learning, assicurando che il modello converga in maniera efficace.

## ESEMPIO - Addestrare il vision trasformer per la image recognition

Addestrare un vision trasformer richiede grosse risorse computazionali ed un gross dataset. Facciamo un esempio usando il dataset CIFAR-10, che  contiene 60.000 immmagini a colori di dimension 23x23 diveise in 10 classi, ciascuna con 6000 immagini.

DA QUI
