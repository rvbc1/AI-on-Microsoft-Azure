# ** Evaluate text with Azure Cognitive Language Services **
## **I. Intro**
Usługa Content Moderator ma na celu automatyzacji moderacji treści. Jej głównym celem jest wynajdywanie elementów niepożądanych, których ręczne znalezienie byłoby bardzo czasochłonne. lub wręcz niemożliwe. Content Moderator wyłapuje z treści elementy podzielone na kategorie:
- Wulgaryzmy. Polega na wyszukiwaniu słów lub fraz uznanych jako wulgarne lub wymagające ręcznego sprawdzenia. Listę wyrażeń wulgarnych można konfigurować.
- Treści niewłaściwe. Dzielą się na trzy podkategorie i polegają na określeniu prawdopodobieństwa, że podane wyrażenie może należeć do danej podkategorii. Gdy podczas analizy dane wyrażenie przekroczy wartość progową prawdopodobieństwa to taka informacja jest zwraca. Podkategorie to treści o charakterze:
  * seksualnym
  * propozycji seksualnych
  * obraźliwym
- Dane osobowe(ang. Personally identifiable information - PII)). Polega na rozpoznaniu czy w podanej treści występują dane osobowe takie jako email, adres, IP, telefon itp.

Efektem działania usługi są dane w formacie JSON w których znajduje się pozycja wystąpienia, znalezienia, kategoria oraz ewentualne informacje dodatkowe, takie jak prawdopodobieństwo podkategorii treści niewłaściwej czy państwo kraju do jakiego należy znaleziony numer telefonu.

## **II Use Cases**
Zastosowanie to głównie przypadki w których występuje duża ilość treści wprowadzanej przez ludzi, czyli np:
- Portale społecznościowe
- Fora dyskusyjne
- Wiadomości email
W powyższych przykładach mamy (lub możemy mieć) sporą grupę użytkowników która można generować ogromne ilości treści, niemożliwe do sprawdzenia. Zastosowanie usługi Content Moderator pozwala na wyłapanie tylko interesujących nas fragmentów.

## **III. How to**
Usługę tworzy się podobnie do innych rzeczy dostępnych na platformie azure czyli tworzymy zasób, nazywamy, wybieramy subskrypcje, lokalizację, jak również RAM i CPU.
Usługa wykorzystuje własne API do wprowadzania tekstu w którym możliwe jest podane typu weryfikacji jakiemu ma być podany.
Bezpłatne wykorzystanie obejmuje 1 transakcje na sekundę oraz ograniczenie do 5 000 transakcji w miesiącu. Standardowa opcja płatna obejmuje 10 transakcji na sekundę oraz opłatę za 1000 transakcji zgodnie z cennikiem (ceny za 1000 transakcji zamieniają się w zależności od ich ilości - im więcej tym taniej)


# **Language Understanding Intelligent Service (LUIS)**


## **I. Intro**
Celem tej usługi jest zrozumienie sensu podanej wypowiedzi. W oparciu o uczynienie maszynowe usługa rozpoznaje wprowadzony tekst i zwraca dane po przeanalizowaniu, co jest zadaniem bardzo trudnym, gdyż na sens wypowiedzi maja wpływ takie elementy jak mowa potoczna, dziedzina rozmowy (w przypadku słów o różnych znaczeniach) czy jej okoliczności.
LUIS korzysta z trzech głównych elementów:
- utterance - dane wejściowe od użytkownika, które należy zinterpretować.
- intents: - zrozumiana intencja wiadomości.
- entities - wyraz lub fraza wewnątrz wypowiedzi, która jest ważna dla intencji, nadająca jej kontekstu.


## **II. Use Cases**

Zastosowanie tej usługi to przede wszystkim realizacjach prostych zadania takie jak np znaleźć, wyszukaj, wyślij. Przykładowe aplikacje w których można wykorzystać LUIS to zamawianie usług komunikacyjnych, kupowanie biletów, dokonywanie rezerwacji, informowanie o potrzebnych dokumentach do załatwienia danej sprawy, przeszukiwanie galerii w celu znalezienia konkretnych zdjęć czy interaktywnego FAQ.

## **III. How to**
Aby utworzyć usługę, należy stworzyć zasób oraz aplikacje usługi w tej samej lokazacji za pomocą linków:
- North America: https://www.luis.ai/
- Europe: https://eu.luis.ai/
- Australia: https://au.luis.ai/

Po utworzeniu należy stworzyć listę intencji czyli czynności jakie możemy zrealizować np PokazObraz. Następnie należy podać wyrażenia jakie mogą być podane przez użytkownika w celu realizacji danej czynności czyli dla PokazObraz mogą to być np:
- Wyświetl zdjęcie domu
- Pokaż mi czerwone obrazy
- Znajdź zdjęcia z owczarkami niemieckimi

Następnie należy dodać słowa kluczowe jakie mogą wystąpić (entities). Kolejnym etapem jej dodanie powiązań między entities i intents (mapowanie) i przetrenować model. Po wykonaniu wszystkich kroków należy stworzyć endpoint do korzystania z wytrenowanego modelu.

Bezpłatne wykorzystanie obejmuje tylko wprowadzanie tekstu  oraz limit 5 transkacji na sekundę z ograniczeniem do 10 000 transakcji w miesiącu. Standardowa opcja płatna obejmuje 50 transakcji na sekundę oraz opłatę za 1000 transakcji zgodnie z cennikiem dla wprowadzanie tekstu i dla wprowadzania wypowiedzianej wypowiedzi.

Problematycznej dla tej usługi są ograniczenia regionalne.

# **Text Analytics API**

## **I. Intro**
Jest to usługa wykorzystująca przetrenowane już modele do analizy tekstu. Usługa jest częścią Cognitive Service czyli zbioru usług wykorzystujących wspomniane wcześniej wytrenowane modele do realizacji przeróżnych celów. Text Analytics API wykorzystywane jest do przetwarzania języka naturalnego przetwarzanie w tekście nieprzetworzonym. Za pomocą tej usługi można zidentyfikować użyty język, wykryć charakter wypowiedzi (pozytywny,, neutralny czy negatywny), słowa kluczowe kluczowe.

W podanym przykładzie pokazane było wykrywanie charakteru wypowiedzi, poprzez przypisanie mu wartości z zakresu 0-1, gdzie 1 oznaczało charakter pozytywny, 0 negatywny a 0,5 neutralny. Dzięki usłudze uzyskiwany był endpoint dzięki któremu można było uzyskać dla podanego tekstu jego charakter w formacie JSON.

## **II. Use Cases**
Usługę wykorzystać można przede wszystkim do analizowania odpowiedzi zwrotnej (feedback) oraz opnii. Dzięki automatycznemu poznaniu charakteru wypowiedzi można w bardzo łatwo analizować uzyskaną odpowiedzieć i dopasowywać usługi czy produkty do klienta na podstawie poprzednich odpowiedzi. Jest to bardzo cenne narzędzie w obecnych czas, gdzie bardzo dużo treści jest "targetowanych" co pozwala maksymalizować zyski i zadowolenie klientów.

## **III. How to**
Aby utworzyć usługę należy utworzyć zasób poprzez azure portal, następnie skopiować uzyskany klucz do testowania odpowiedzi usługi. W odpowiedzi otrzymywany jak poprzednio są dane w formacie JSON zawierające język, id oraz tekst. Tak utworzona usługe nastepnie należy wimplemnetowac w nasza apliakcje, która bedzie wykonywać zapytania do usługi.


Bezpłatne wykorzystanie obejmuje 5 000 zapytań w miesiącu. Następnie opcje płatne dzielą się w zależności od ilości zapytań (są podane przedziały) i przedstawione są w cenniku od 5 tys zapytań do 10 milionów w miesiącu wraz z cenami za przekroczony limit (nadwyżka zapytań).
