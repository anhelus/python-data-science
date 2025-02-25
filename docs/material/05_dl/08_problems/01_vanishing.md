# Il problema dei gradienti

Il processo di ottimizzazione gioca un ruolo cruciale nell'addestramento delle reti neurali. L'algoritmo a discesa di gradiente (*gradient descent*) può infatti alle volte scontrarsi con due problemi fondamentali, ovvero quello dei *vanishing gradients* e degli *exploding gradients*.

## Vanishing gradients

Il problema del *vanishing gradient* emerge durante la backpropagation, ed in pèarticoalre quando le derivate delle funzioni di attivazioni diventano sempre più piccole man mano che procediamo "all'indietro" nella rete neruale. Questo fenomeno è, come intuibile, estremamente rilevante nelle reti neurali con molti layer, e può compromettere l'addesteramnto del modello. In particoalre, i pesi vengono aggiornati in maniera estremamente lenta, prolungando significantivamente il tempo di addestramento e, nel caso peggiore, terminando il processo stesso.

<!-- https://www.geeksforgeeks.org/vanishing-and-exploding-gradients-problems-in-deep-learning/ -->