# ** QnA Maker **
## **I. Intro**
Usługa QnA pozwala na stworzenie automatycznej komunikacji w postaci odpowiedzi na pytania. W obecnych czas dużo ludzi kieruje pytanie do firm i organizacji, które są zbyt przeciążone by odpowiadać na wszystkie, w tym celu stosuje się modele które mają zapisaną w sobie bazę danych pytań i odpowiedzi, daje to efekt taki, że klient może zadać pytanie podobne, lub z lekkimi błędami (np literówkami) a usługa rozpoznaje sens wiadomości i wysyła zapisaną odpowiedź. W założeniu jest to dokładnie to samo co FaQ z tą różnicą, że jest dużo wygodniejsze dla użytkownika, który nie musi przeszukiwać wszystkich możliwości lub zadać pytanie podobne. Po stworzeniu bazy danych należy wytrenować model w serwisie azure i przetestować go przed upublicznieniem. W przypadku gdy baza jest gotowa, możemy z jej skorzystać poprzez REST API.
Bezpłatna opcja serwisu obejmuje 3 transakcje na sekundę, 100 transakcji na minutę oraz limit 50 000 transakcji w miesiącu w  trzech bazach o maksymalnym rozmiarze 1MB. Opcja płatna nie posiada miesięcznego limitu oraz ograniczeń dokumentu i kosztuje 8,433 euro.

## **II Use Cases**
Zastosowanie to głównie przypadki w których występuje duża ilość treści wprowadzanej przez ludzi, czyli np:
- Wszystkie firmy wykorzystujące komunikację z klientem
- Typowe pytania dotyczące produktów i usług
- Tańsze rozwiązanie niż ludzie realizujący odpowiedzi na typowe pytania.


## **III. How to**
Pierwszą rzeczą jest przygotowanie bazy pytań-odpowiedzi dla naszego bota. Kolejnie za pomocą portalu Q&A Maker portal stworzyć model i przetestować (po uprzednim wprowadzeniu bazy) i opublikować uzyskując klucz autoryzacyjny  i endpoint.

# **Azure Bot Service**


## **I. Intro**
Jest to serwis z botem, wykorzystujący bazę danych utworzoną poprzez QnA Maker'a i jego celem jest obsługiwanie wielu użytkowników chcących skorzystać z bazy w różnych lokalizacjach (kanałach) informacyjnych.


## **II. Use Cases**

Jest to rozwinięcie usługi QnA Maker, więc ma te same zastosowania + wspomnianą możliwość szerokiego wykorzystania.
## **III. How to**

Bota można można utworzyć bezpośrednio z QnA Maker'a tak, aby uzyskać bota do stworzonej bazy pytań i odpowiedzi. Po utworzeniu w Azure Bot Service, mamy możliwość kontrolowania osobnej usługi jaką jest bot (zmiana ustawień czy analiza działania). Następnym etapem jest podpięcie bota pod kanały informacyjne, strona www, skrzynka email czy produkty Microsoftu jak Teams czy Skype. Wykorzystanie w produktach Microsoftu oraz z publicznym API (np Facebook) są darmowe, inne wykorzystanie kosztują 4,22 euro za każde 10 000 wiadomości.

# **Bot Framework Composer**

## **I. Intro**

Jest to usługa pozwalająca stworzyć zaawansowanego bota, przez każdą osobę (nie programistę). Dzięki adaptive dialogs bot, może działać adaptacyjnie w zależności od rozwoju rozmowy, budowanego w formie grafu następujących sekwencji. Przykład to podanie pogody dla podanej lokalizacji, co nie jest już prostą rzeczą na zasadzie pytanie-odpowiedź. Usługa posiada szereg narzędzi pozwalających bardoz mocno rozwinać i dostosować bota. Dodatkowo wykorzystując Language Generation, można uzyskać bardziej spersonalizowana odpowiedź (aby próbować utrzymać rozmowę na zasadzie człowiek-człowiek a nie człowiek-maszyna)

## **II. Use Cases**
Zastosowanie jak w poprzednich punktach, z tym, że w tym przypadku można stworzyć bardziej "ludzkiego" bota.

## **III. How to**
Jest to usługa nieco inna od rzeczy produktów Microsoft Azure, dlatego, że nie jest konfigurowana przez Azure portal tylko przez aplikację na komputer, która należy pobrać i zainstalować a następnie dodać odpowiednie działanie bota. Usługa jest w pełni darmowa, płatne ewentualnie są usługi współpracujące jak LUIS.
