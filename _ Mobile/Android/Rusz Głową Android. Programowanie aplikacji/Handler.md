#kotlin/handler
[[Looper]]


# Definicja 

W języku Kotlin, klasa `Handler` jest często używana w kontekście programowania na platformie Android. Klasa ta pochodzi z pakietu `android.os` i służy do współpracy z wątkami oraz planowania zadań do wykonania w przyszłości, zwłaszcza w kontekście interfejsu użytkownika.

>[!definition] Handler
>To klasa abstrakcyjna, która umożliwia:
>	- wysyłanie i 
>	- przetwarzanie 
> wiadomości oraz obiektów `Runnable` związanych z kolejką wiadomości wątku. 
> 
> Każda instancja `Handler` jest powiązana z pojedynczym wątkiem i kolejką wiadomości tego wątku. Gdy tworzysz nowy `Handler`, jest on powiązany z `Looper`. Dostarczy on wiadomości i obiektów `Runnable` do kolejki wiadomości tego `Looper` i wykona je na wątku tego `Looper`.

---------
# Konstruktory

Klasa `Handler` ma dwa konstruktory:

- `Handler()`: Tworzy nowy `Handler` przy użyciu `Looper` bieżącego wątku.
- `Handler(looper: Looper)`: Tworzy nowy `Handler` przy użyciu zadanego `Looper`.

----
# Metody

- `post(runnable: Runnable)` dodaje obiekt `Runnable` do kolejki wiadomośći. Obiekt `Runnable` zostanie wykonany na wątku, z którym powiązany jest `Handler`
- `postDelayed(runnable: Runnable, uptimeMillis: Long)` dodaje obiekt `Runnable` do kolejki wiadomości, aby został wykonany w określonym położeniu






----
# Główne zastosowania klasy `Handler` w Androidzie obejmują:

1. **Aktualizacja Interfejsu Użytkownika z Innych Wątków:**
    
    - W Androidzie, interfejs użytkownika (UI) może być aktualizowany tylko z głównego wątku (wątku interfejsu użytkownika). Aby zaktualizować UI z innego wątku, można użyć `Handler`, który umożliwia wysyłanie i obsługę wiadomości w głównym wątku.
    
1. **Planowanie Zadań w Przyszłości:**
    
    - Klasa `Handler` pozwala na planowanie zadań do wykonania z opóźnieniem lub okresowo. Na przykład, można użyć `postDelayed` do wysłania wiadomości z opóźnieniem w czasie.
    
1. **Obsługa Animacji i Efektów:**
    
    - Handler może być używany w obszarze animacji, gdzie planowanie kroków animacji w przyszłości jest kluczowe.
    
1. **Komunikacja Między Wątkami:**
    
    - Handler umożliwia komunikację między różnymi wątkami w aplikacji Android.
    
1. **Przetwarzanie Zdarzeń Wątku Głównego:**
    
    - W przypadku obsługi zdarzeń na wątku głównym, `Handler` jest często wykorzystywany do przetwarzania wiadomości w pętli komunikatów.

Przykład użycia `Handler` w Kotlinie na platformie Android:

kotlinCopy code
```kotlin

import android.os.Handler 
import android.os.Looper  

class MyActivity {     
	private val handler =Handler(Looper.getMainLooper())     
	fun someMethod() { 
	   handler.post {             // Kod, który zostanie wykonany w wątku głównym             
		   updateUI()         
	   }          
	   
	   handler.postDelayed({
	   // Kod, który zostanie wykonany z opóźnieniem             
		   doSomething()         
	   }, 1000)     
	}      
	
	private fun updateUI() {         
	// Aktualizacja interfejsu użytkownika     
	}      
	private fun doSomething() {        
	 // Wykonaj jakieś zadanie     
	 } 
	 
}
```

W tym przykładzie, `handler.post` umożliwia wykonanie kodu w wątku głównym, a `handler.postDelayed` pozwala na opóźnienie wykonania kodu o 1000 milisekund.





