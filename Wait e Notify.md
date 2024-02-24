> I metodi `wait`, `notify` e `notifyall` fanno parte della classe **Object** di Java. Sono, pertanto, ereditati da ogni classe e permettono di mandare nello stato di **waiting** un Thread(`wait`), o di notificare i Thread che attendono su un'istanza  (rispettivamente `notify` e `notifyAll` notificano un **Thread** a caso oppure tutti i **Thread**, tra quelli in **waiting** su tale oggetto).

> [!example] Esempio
> ``` java
> synchronized (obj) {
> 	while(<condition>)
> 		obj.wait();
> 		 // ...
> 	}
> }
> ```

