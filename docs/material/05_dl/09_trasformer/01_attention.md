<!-- https://www.geeksforgeeks.org/ml-attention-mechanism/ -->
# 5.9.1 - L'attention

Per descrivere il meccanismo dell'*attention* possiamo usare una semplice ed efficace analogia.

Immaginiamo per un attimo di interrompere lo studio del Python e del machine learning per andare ad una festa. Una volta arrivati, nonostante il gran numero di persone presenti, decidiamo di metterci a discutere con un nostro amico di quello che abbiamo appreso durante il corso Python. Grazie alle nostre incredibili capacità di concentrazione, riusciamo a badare esclusivamente alla conversazione con il nostro amico, ignorando il rumore di sottofondo della festa. In questo (estremamente irrealistico) scenario, il nostro sistema uditivo sta esercitando una *attenzione selettiva* nei confronti della conversazione con il nostro amico, focalizzandosi esclusivamente sulle informazioni in quel momento rilevanti. In altre parole, il nostro cervello "migliora" la comprensione del parlato dando una priorità maggiore ai suoni che ci interessano, ed ignorando, per quanto possibile, quelli di background.

Questo meccanismo, che ci permette quindi di dare una certa priorità a date informazioni in specifici contesti, è detto *meccanismo di attention*.