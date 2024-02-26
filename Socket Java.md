Fonti: [Socket](https://docs.oracle.com/javase/8/docs/api/java/net/Socket.html) e [ServerSocket](https://docs.oracle.com/javase/8/docs/api/java/net/ServerSocket.html)
Bisogna importare il package `java.net.*`.
- La classe `java.net.Socket` implementa un **client socket** che:
	- richiede l’indirizzo IP e il numero della porta a cui vogliamo connetterci
- La classe `java.net.ServerSocket` implementa un **server socket** che:
	- richiede il numero della porta da usare 
	- crea un “server” che **attende** le richieste di connessione 
	- **restituisce un socket** nel momento in cui accetta un collegamento completamente istanziato nei parametri di collegamento (IP e Porta)

---
