# Synchronizacja
#SRC #Sem1 #MBP #wyklad
Wzorce synchronizacji:
- Atomicity:
	- używając blokad do sekcji krytycznych
		- sztuka polega na dobrym doborze blokad
		- zapobieganie/wykrywanie zakleszczeń
- Condition synchronzation
#TODO z prezentacji
- spinning (przestażałe, już nie działają):
	- przy spin lock TAS() musi być instrukcją maszynową atomową aby nie było konflików
- Safety and Livenes
- Prawo Ahmdala
- Pamięć
- Super że jest cache ale przy wielu wątkach trzeba cache uspójniać aby się nie rozjechały wartości zmiennych, są do tego protokoły (cache-cocheres (?)), ale nie robią tego idealnie. Nie gwarantują że zawsze w innym wątku przeczytasz dobrą wartość zmiennej. Poprawna synchronizacja zadba że nie będzie "dziwnych" rzeczy.
- Architektóra riskowa, szybsze ale mniejsza spójność cashe, dlatego M1 jest taki szybki.
- Cache miss - jeśli czegoś nie możemy odczytać z cache bierzemy z normalnej pamięci
- Czasami instrukcje nie wykonują się w tej samej kolejności jak w kodzie (komplikatory tak robią jeśli na jednym wątku nic to nie zmienia i zoptymalizuje to ten wątek, jednak może to prowadzić do problemów przy wielu)
- Dlatego stare algorytmy nie działają (nie ma niskopoziomowej synchronizacji)
- Relaxed memory modelu (x86 vs risk)
- Konstrukcja synchronizacji
- CAS na x86 <=> LL i SC na riskowych procesorach
- Atomowo spekulatywne -> bez zakładania blokad,  jeśli im się uda i nadpiszą CAS jeśli się nie uda próbują jeszcze raz aż do skutku
- dedlock - 4 warunki deadlocku
- Algorymt Bankiera
- Własności mówiąze że program jest poprawny
- Transakcje w programowaniu wspólbieznym:
	- tak jak na zamkach ale optymistycznie
- Fairness (sprawiedliwość) w przetwarzaniu wielowątkowym, faworyzowanie wątków
- Zagłodzenie jest przykładem braku sprawiedliwości w przetwarzaniu
- Algorytm Piekarniany (The "bakery" algorytm (Lamport))
- RCU - Read-copy update 
- Semafory:
	- zbudowane w oparciu o blokowanie, a nie aktywne czekanie jak spin locki, usypiane gdy czekają, przez co nie angażują procesora (stonks na zasobach procesorach)
- Monitory
	- w C++ i w Javie są trochę inne monitory, jego implementacja zgodna z teorią jest w ADA
	- Chcemy chronić struktóry danych
	- koncepcja polega na tym że wywołując metodę jeśli obiekt jest zdefiniowany jako monitor operacje są wykonywane Atomowo, nie ma sytuacji aby dwa wątki wykonywały te samą metodę w tym samym czasie.
	- Jeden zamek pre monitor
	- wait - pozwala zaczekać na spłenienie warunku w monitorze
	- signal - budzi uśpiony wątek
	- wait w monitorze usypia wątek i zwalnia zamek monitora, ale jaki wątek dostanie zamek to już zależy od monitora
	- [[Klasyczny Monitor]]
	
