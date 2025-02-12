# Meccanismo di attention

L'attention mechanism venne introdotto da Bahdanau nel 2014 (https://arxiv.org/abs/1409.0473) per risolvere il problema del collo di bottiglia che merge dall'uso di vettori di codifica a lunghezza fissa, con il decoder che ha accesso limitato all'informazione fornita dall'input. Questo diventa problematico specialmente nelc aso di sequenze lunghe o complesse, dove la dimensionalità della rappresentazionesarà forzata ad essere la stessa di quella di frasi più semplici o corte.

Da notare che il meccanismo di attention di Bahdanau è diviso nel calcolo passo passo di *alignment scores*, *weights*, e del *context vector*.

1. Alignment scores: il modello di allineamento prende gli stati nascosti del decoder $h_i$ ed il precedente output del decoder $s_{t-1}$ per calcolare uno score $e_{t,1}$ che indica quanto bene gli elementi della sequenza di input si allineano allk'oputput corrente alla posizione $t$. Il modello di allineamento è rappresentato da una funzione $a(\cdot)$ che può essere implementata usando una rete neurale feedforward:

$$
e_{t,i}=a(s_{t-1},h_i)
$$

2. pesi: i pesi $\alpha_{t,i}$ sono calcolati applicando un'operazione di softmax agli alignment score calcolati in precedenza:

$$
\alpha_{t,i} = softmax(e_{t,i})
$$

3. context vector: un context vector unic, $c_t$, viene inviato al decoder ad ogni step temporale. Viene calcolato come la somma pesata di tutti i $T$ stati nascosti codificati:

$$
c_t = \sum_{i=1}^T \alpha_{t,i} h_i
$$

In particolar,e nell'implementazione originale vi era un RNN sia per l'encoder sia per il decoder.

Ad ogni modo, il meccanismo di attention può essere riformulato in una forma generale che può essere applicata ad una qualsias task sequence-to-sequence (seq2seq), dove l'informazione potrebbe non necessariaemnte essere correlata in maniera sequenziale.
