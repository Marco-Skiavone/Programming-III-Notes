# Wait and Notify

> I metodi `wait`, `notify` e `notifyall` fanno parte della classe **Object** di Java. Sono, pertanto, ereditati da ogni classe e permettono di mandare nello stato di **waiting** un Thread(`wait`), o di notificare i Thread che attendono su un'istanza  (rispettivamente `notify` e `notifyAll` notificano un **Thread** a caso oppure tutti i **Thread**, tra quelli in **waiting** su tale oggetto).

> [!example] Esempio: wait
> ``` java
> synchronized (obj) {
> 	while(/*condition*/) {
> 		obj.wait();
> 		 // ...
> 	}
> }
> ```

I metodi `notify` e `notifyAll` dovrebbero a loro volta essere **sempre** usati **all'interno di sezioni critiche**, effettuate sull'oggetto sui quali si vuole operare (vedi [documentazione](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html#notify--)):

> [!example] Esempio: notify
> ``` java
> synchronized (obj) {  // sincronizzazione sull'oggetto
> 	// ...
> 	obj.notifyAll();
> }
> ```
> 
> oppure
> 
> ``` java
> public static synchronized void update() {
> 	// ... /*updates on this*/
> 	this.notify();
> }
> ```

> [!warning] Attenzione!
> Non si può decidere quale **Thread** avrà l'uso della CPU. Il fatto che venga svegliato, non vuol dire che andrà in esecuzione per primo. Pertanto, si fa necessario l'uso di blocchi di [synchronized](<./Synchronized.md>).
> > *"The awakened thread will compete in the usual manner with any other threads that might be actively competing to synchronize on this object; for example, the awakened thread enjoys no reliable privilege or disadvantage in being the next thread to lock this object."* 
>
> \- cit. [docs.oracle](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html#notify--)
