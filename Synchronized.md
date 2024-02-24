Il `synchronized` può essere usato in diverse maniere:
#### Firme di Metodi Dinamici:
> [!example] Esempio
> ```java
> public synchronized int getVal(){ /* ... */ }
> ```
 
 - Questi metodi richiedono il **lock sull'istanza** dell'oggetto da cui vengono chiamati. Essendoci solo un lock per ogni istanza, un **synchronized** effettuato da un altro Thread andrà in *waiting* sull'istanza stessa.
 --- 
#### Firme di Metodi Statici:
> [!example] Esempio
> ```java
> public class Esempio {
> 	private static int num = 0;
> 	
> 	public static synchronized void incrementNum() { /* ... */ }
> }
> ```

- Questi metodi richiedono il **lock della classe** di cui fa parte l'oggetto. Tutti gli oggetti della stessa classe condividono lo stesso lock di classe (separato da quello d'istanza), il quale ha la **precedenza** su tutti i lock delle singole istanze.
---
#### Blocchi di synchronized:
> [!example] Esempio
> ``` java
> synchronized (obj) {
> 	// ...
> }
> ```

- La sincronizzazione viene effettuata sul **lock** di `obj`, che è l'istanza di un oggetto. Pertanto ogni elemento che tenta di accedere ad una **sezione critica** (il blocco di codice definito dopo il `synchronized`) sullo stesso oggetto verrà messo in stato di *waiting*.

> [!info] Nota:
> Il blocco di `synchronized` può essere definito su `this`. Ciò permette di sincronizzare i metodi dinamici di un'oggetto sull'oggetto stesso, come nel caso dell'[appello d'esame di Febbraio 2024](febbraio-2024.pdf).

