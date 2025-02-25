<!-- https://www.geeksforgeeks.org/getting-started-with-transformers/ -->

# I trasformer

I *trasformer* sono un modello di rete neruale usato per la prima volta nell'articolo del 2017 pubblicato da Vaswani e chiamato "Attention is All You Need", nel quale venne per la prima volta introdotta questa architettura. 

I trasformer sono un modello che usa un meccanismo chiamato *self attention* per trasformare una frase in un'altra. Questo rappresenta un grosso cambiamento dai modelli più vecchi, che lavoravano pezzo a pezzo, ed ha aiutato ad andare oltre i modelli come le RNN e le LSTM.

Infatti, i modelli tradizionali come le RNN soffrivano del cosiddetto problema del vanishing problem, che ha condotto alla *long-term memory loss*. Le RNN elaborano il testo in maniera sequenziale, il che significa che analizzano una parola alla volta.

Per esempio, nella frase "XYZ è andato in Francia nel 2019 quando non c'erano casi di COVID, ed incontrarono il presidente di quel paese", la parola "quel paese" si riferisce a Francia. Tuttavia, una RNN non riuscirebbe facilmente a collegare "quel paese" a "Francai", dal momento che elabora ogni parola nella sequenza, perdendo quindi il contesto in frasi molto lunghe. Questa limitazione fa in modo che le RNN non comprendano appieno il significato della frase.

Anche se aggiungere più celle di memoria in una configurazione LSTM aiuta a gestire il problema del vanishing gradient, questo tipo dir ete continua ad elaborare le parole una alla volta. Questa elaborazione sequenziale indica che le LSTM non possono analizzare una intera sequenza alla volta. Inoltre, gli *static embeddings* nelle LSTM non riescono a catturare il significato cangiante delle parole, e dipendentre dal contesto.

Ad esempio, la parola "principe" ha diversi ginficiati in diverse frasi:

* Il principe è stato invitato alla festa.
* TODO

Questo mostra come la stessa parola può avere diverse significati a seconda del contesto, con modelli tradizionali coome le RNN e le LSTM che non riescono a catturare. Il modello transformer, attraveros il meccanismo di self-attention, processa l'intera sequenza in parallelo, risovlendo questi problemi e rendendola significativamente più efficace nel comprendere il contesto.

## Archietttura e funzionamento dei trasformer

##### Positional encoding

I trasformer non hanno una comprensione intrinisca di un ordine sequenziale. Per risolvere questo problema, si usa la tecnica del *positional ecncodingf*, che permette di aggiungere questo tipo di encoding agli embedding, fornendo informazioni sulla posizioen di ogni token nella sequenza.

<!-- https://www.geeksforgeeks.org/positional-encoding-in-transformers/ -->

##### Position-wise Feed-Forward Networks

Le reti neurali feed forwards consiste di due trasformazioni lineari con un'attivazione ReLu. Questi layer sono presenti sia nellìencoderer sia nel ddecoder, elaborando le features ad ogni posizione nella sequenza. Matematicamente:

$$
FFN(x) = max(0, xW_1 + b_1) W_2 + b_2
$$

##### Meccanismo di attention

Il meccanismo di attention nei trasformer usa un approccio chiamato *scaled dot-product*, calcolando la somma pesata dei valori di query, key, e value. Per migliorare le performance del modello, la multi-head attention applica il meccanismo di attention più volte in parallelo, ognuno con una proiezione appresa univoca. Gli output sono  concatenati e trasformati per generare i risultait finali. Questo permette al modello dic atturare diverse relazioni e creare rappresentazioni più ricche e contestualizzate della sequenza di input. La multi-head attention migiora inotlre le capacità del trasformer di elabroare dati complessi.

<!-- https://www.geeksforgeeks.org/ml-attention-mechanism/ -->

##### Encoder-decoder architecture

La struttura encoder-decoder è la chiave dei modelli trasformer. L'encoder elabora la sequenza di input in un vettore, metnre il decoder converte questo vettore in una sequenza. Ogni layer di encoder e decoder include layer di self-attention e feed-forward. Nel decoder, un laeyr encoder-decoder viene aggiunto per focalizzarsi sulle parti rilevanti dell'intresso.

PEr esempio, una sequenza in italiano "Sono un alunno" viene tradotto in "I am a studewntr " in inglese.

L'encoder consiste di due layer: Self-Attention e Feed-Forward. L'input per prima cosa passa attraverso il layer di self-attention, dove il modello elabora le relazioni tra le parole. L'output di questo layer è quindi inviato ad una rete neurale feed-forward per ulteriori trasformazioni. I dati sequenziali hanno carattersitiche intrinsecamente temporali, il che significa che la posizione di ogni parola condiziona il suo significato.

Ad esempio, nella frase "Il gatto non ha preso il topo perché non era affamato", la parola "il" si rifersice a "gatto". Il meccanismo di self-attention aiuta il modello ad associare correttamente "il" con "gatto", permettendo quindi di rifomrlare la rappresentazione sulla base di tutte le parole nella frase.

L'architettura del decopder ha tre layer: Self Attention, Encoder-decoider attention,e  Feed Forward. Il decoder ha sia i layer di self attentione  feed forwad, che sono presenti anche nell'encoder, am tra di loro vi è un layer di attention che aitua il decoder a focalizzarsi su parti rilevnait della sequenza di input.

Vi sono sei layer di encodre e decoder nell'architettura trasformer. Nell'encoder più in basso, i word embeedding sono estratti, ed ogni parola è trasformarta in un vettore di 512 elementi. L'inptu agli altri encoder sarà l'outpui dell'encoder immediatamente precednete.

## Applicazioni

* compiti di NLP: usati per la machine translation, text summarization, named enityt recognition e sentiment analysis
* speech recognition: elaborazione di segnali audio per convertire il parlato in testo tradotto
* computer vision: applicati alla calssificazione delle immagini, object detection ed image generation
* recommendation systems: fornire raccomandazioni personalizzate sulla abse delle preferenze utente
* generazione testo e musica: usati per generare testo (articoli) e comporre muscia
