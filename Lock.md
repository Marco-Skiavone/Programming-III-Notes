> Ci sono diversi tipi di classi che implementano i **lock** (Esiste l'**interfaccia** `Lock`). Una delle più utili e facili da usare è il [ReentrantLock](https://docs.oracle.com/javase%2F7%2Fdocs%2Fapi%2F%2F/java/util/concurrent/locks/ReentrantLock.html). 

Per fare un esempio di ***ReentrantLock***, si veda come vengono facilmente usati metodi `lock()` e `unlock()`. Essi sostituiscono l'uso del **[[synchronized]]**, ma bisogna fare maggiore attenzione ai **deadlock**, che possono farsi presenti più facilmente, in caso di più istanze in uso:
``` java
public class Esempio {
   private final ReentrantLock lock = new ReentrantLock();

   public void m() {
     lock.lock();  // block until condition holds
     try {
       // ... 
     } finally {
       lock.unlock()
     }
   }
 }
```

---
# Condition:
> **Condition** è un'interfaccia di Java (reperibile [qui](https://docs.oracle.com/javase%2F7%2Fdocs%2Fapi%2F%2F/java/util/concurrent/locks/Condition.html)). Permette di creare diverse *"condizioni"* su cui sincronizzare l'attesa e la notifica dei **Thread**. Andando così a sostituire l'uso dei ***"monitor methods"*** di Object, che sono i metodi `wait`, `notify` e `notifyAll`.

> [!example] Esempio
> ``` java
> Lock lock = new ReentrantLock();
> Condition notFull  = lock.newCondition();
> Condition notEmpty = lock.newCondition();
> 
> // ...
> 
> while(<condition>)
> 	notFull.await();
> push();
> notEmpty.signal();
> 
> // ...
> 
> while(<condition>)
> 	notEmpty.await();
> pop();
> notFull.signal();
> ```

Per esempi più concreti o dettagliati, rifarsi ai link sulla documentazione ***docs.oracle***.

> [!warning] Attenzione:
> Un **Thread** in stato di attesa potrebbe svegliarsi *anche se non ancora notificato dalla condizione* di cui è in attesa. Pertanto, è buon uso inserire le istruzioni di `.await()` in un **ciclo**.
