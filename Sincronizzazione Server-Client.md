Prendiamo a tale scopo come caso d'esempio i trasferimenti bancari:
![[bank-scenario.png]]

Ci sono, in tale contesto, due scenari di sincronizzazione possibili:
## Sincronizzazione **Lato Client**
> Ciò significa che ci è richiesto che tutte le operazioni effettuate dalla Banca sugli account X non blocchino gli accounts *(clients)* Y dal poter fare le stesse operazioni.  ***(Finché X $\cap$ Y $=\emptyset$)***
> 
> **Spesso**, la sincronizzazione lato client prevede di modificare il **corpo delle funzioni** interessate (X) del **client**.

## Sincronizzazione **Lato Server**
> Ciò significa che ci è richiesto che la Banca possa eseguire l'operazione X richiesta per un account A solo se nessun altro account ha richiesto di eseguire X prima. Nel caso in cui un account B necessiti di eseguire l'operazione X, quando essa è già in esecuzione per A, B **attenderà il suo turno**.
>
> Spesso, la sincronizzazione lato server prevede di modificare la **firma della funzione** interessata (X) dal **server**.


<br>

### Per un **esempio**, si veda [qui](luglio-2024.pdf).