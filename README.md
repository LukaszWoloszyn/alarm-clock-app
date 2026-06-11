
**Praca projektowa technologie internetowe**

_Zegar z funkcją alarmu_

- **Zdefiniowanie problemu do realizacji**

Celem projektu Alarm Clock App jest stworzenie prostej aplikacji do zarządzania budzikiem, która umożliwia użytkownikom ustawianie, aktywowanie, dezaktywowanie i usuwanie alarmów z wykorzystaniem interfejsu użytkownika opartego na stronie internetowej. Projekt ten ma za zadanie zapewnić użytkownikom prosty, intuicyjny i skuteczny sposób zarządzania alarmami za pomocą interfejsu opartego na przeglądarce internetowej.

Struktura projektu składa się z plików HTML, CSS i JavaScript, które są odpowiedzialne za prezentację interfejsu użytkownika, stylizację oraz logikę biznesową aplikacji.

- **Sposób na rozwiązanie problemu**

Struktura HTML, CSS i JS:

- Plik HTML zdefiniuje strukturę interfejsu użytkownika i będzie głównym punktem wejścia do aplikacji. Obejmował będzie on elementy takie jak formularz ustawiania alarmów, wyświetlanie aktualnego czasu oraz listę aktywnych alarmów. Dodatkowo, zawierał będzie odwołania do plików CSS i JavaScript oraz inne metadane dokumentu.
- Plik CSS zdefiniuje stylizację interfejsu użytkownika, zapewniając atrakcyjny wygląd i czytelność aplikacji. Zawierał będzie reguły dotyczące formatowania elementów HTML, takich jak kolorystyka, rozmiar i układ.
- Plik JavaScript zawierał będzie logikę biznesową aplikacji oraz obsługę interakcji użytkownika. Funkcje, które będzie zawierał to: aktualizacja czasu, ustawianie, aktywowanie, dezaktywowanie i usuwanie alarmów, a także obsługa interakcji użytkownika, takich jak pokazywanie i ukrywanie okna modalnego.
- Aby umożliwić użytkownikom podglądanie i zarządzanie alarmami, dodany zostanie osobny plik HTML, który wyświetli listę wszystkich aktywnych alarmów.

- **Testowanie**

- Strona główna:
  - W pliku budzik.html będzie zawarta sekcja &lt;body&gt; która będzie miejscem, gdzie zawartość strony internetowej będzie prezentowana użytkownikowi. W tej sekcji znajdować się będą różne elementy, które utworzą interfejs użytkownika aplikacji budzika (Rysunek 1).
  - Na stronie będzie zawarty formularz, który umożliwi użytkownikowi ustawienie czasu i daty alarmu oraz wybór opcji powtarzania. Każde pole formularza jest opatrzone etykietą, aby łatwo było zrozumieć, co jest wymagane.
  - Przyciski do ustawiania alarmu i przeglądania alarmów będą umieszczone pod formularzem. Pierwszy przycisk służył będzie do ustawienia alarmu i wywoła funkcję JavaScript setAlarm(), a drugi przycisk otworzy nowe okno z listą alarmów.
  - Div #alarms-list: Będzie to kontener, w którym będą wyświetlane wszystkie zdefiniowane alarmy. Jest pusty na początku, ale zostanie wypełniony dynamicznie za pomocą JavaScript, gdy użytkownik doda nowe alarmy.
  - Modal: Ten element, o identyfikatorze myModal, zaprezentuje okno modalne, które pojawi się na ekranie w momencie aktywacji alarmu. Będzie to rodzaj powiadomienia dla użytkownika (Rysunek 2.).
  - Media Query: Zdefiniuje dodatkowe style dla urządzeń o szerokości ekranu mniejszej niż 600 pikseli. Zmniejszy padding dla kontenera .container i dostosuje szerokość elementów formularza oraz przycisków, aby lepiej skalować się na mniejszych ekranach (Rysunek 3).



Rysunek 1.



Rysunek 2.



Rysunek 3.

- JavaScript dla strony głównej:
  - getAlarms: Będzie tworzyć funkcję getAlarms(), która będzie zwracać obietnicę. Będzie sprawdzać, czy istnieją zapisane alarmy w localStorage i będzie rozwiązywać obietnicę z tablicą alarmów lub odrzucać ją w przypadku błędu. Funkcja będzie pobierać alarmy z localStorage
  - removeAlarm(index): Będzie definiować funkcję removeAlarm(index), która będzie usuwać alarm z localStorage na podstawie podanego indeksu. Będzie zwracać obietnicę, która będzie rozwiązywać się po pomyślnym usunięciu alarmu. Funkcja będzie usuwać alarm z localStorage.
  - setAlarm(): Będzie tworzyć funkcję setAlarm(), która będzie ustawiała nowy alarm na podstawie danych wprowadzonych przez użytkownika, takich jak godzina, data i powtarzalność. Będzie sprawdzać, czy data alarmu jest w przyszłości (jeśli nie, wyświetli alert (Rysunek 4.)), a następnie będzie dodawała alarm do localStorage.
  - displayAlarms(): Będzie definiować funkcję displayAlarms(), która będzie wyświetlać listę alarmów na stronie, pobierając alarmy z localStorage i tworząc odpowiednie elementy HTML dla każdego alarmu.
  - toggleAlarm(index): Będzie tworzyć funkcję toggleAlarm(index), która będzie zmieniała stan aktywności alarmu (aktywuj/dezaktywuj) na podstawie jego indeksu w tablicy alarmów, co pozwoli na wyłączenie alarmu, a nie jego całkowite usunięcie.
  - showModal(): Będzie określać funkcję showModal(), która będzie wyświetlała okno po wybiciu godziny alarmu. Okno modalne będzie zamykane po kliknięciu przycisku "x" lub po kliknięciu na obszarze poza oknem.
  - displayAlarms(): Będzie automatycznie wywoływać funkcję displayAlarms() po załadowaniu strony, aby wyświetlić aktualną listę alarmów.



Rysunek 4.

- Podstrona z alarmami:
  - Jeśli użytkownik na stronie głównej naciśnie przycisk „Zobacz alarmy", w nowej karcie wyświetli się podstrona z alarmami, która będzie wyświetlać listę alarmów. Jest to pusty element, który zostanie wypełniony dynamicznie za pomocą JavaScript (Rysunek 5).



Rysunek 5.

- JavaScript dla podstrony:
  - Będzie pobierał element HTML o identyfikatorze "alarms-list" i przypisywał go do zmiennej alarmsList.
  - Będzie definiować funkcję displayAlarms(), która będzie miała za zadanie wyświetlać listę alarmów na stronie.
  - Wewnątrz funkcji displayAlarms():
    - Będzie najpierw czyścił zawartość listy alarmów poprzez ustawianie innerHTML na pusty string.
    - Następnie będzie pobierał listę alarmów z pamięci lokalnej (localStorage) za pomocą JSON.parse(localStorage.getItem('alarms')). Jeśli lista nie będzie istnieć, będzie przypisywał pustą tablicę \[\].
    - Będzie iterował przez każdy alarm w tej liście, tworząc dla niego nowy element &lt;div&gt; za pomocą document.createElement('div').
    - Do każdego elementu &lt;div&gt; będzie dodawał informacje o godzinie, dacie i powtarzaniu alarmu w postaci elementu &lt;p&gt;.
    - Na koniec każdy nowo utworzony element &lt;div&gt; będzie dodawany do listy alarmów poprzez appendChild(alarmItem).
  - Na końcu kodu funkcja displayAlarms() będzie wywoływana, aby zainicjować wyświetlanie listy alarmów na stronie.

- **Dokumentacja kodu źródłowego w postaci JSDoc i KSS.**

Kod został opatrzony dokumentacją JSDoc, co ułatwia zrozumienie jego funkcji i działania (Rysunek 6). Każda funkcja jest opisana za pomocą adnotacji @function, a także poszczególne parametry są opisane, co ułatwia korzystanie z tych funkcji. Na przykład, funkcja updateTime aktualizuje obecną godzinę na stronie, a getAlarms pobiera listę alarmów z lokalnego magazynu. Podobnie, funkcja removeAlarm usuwa wybrany alarm, a setAlarm ustawia nowy alarm na podstawie danych wprowadzonych przez użytkownika. Funkcja displayAlarms wyświetla listę alarmów na stronie, a toggleAlarm zmienia stan aktywności wybranego alarmu. Dodatkowo, funkcja showModal pokazuje okno modalne, a closeModal zamyka je. Ostatnio, window.onclick obsługuje kliknięcie myszy poza oknem modalnym, ukrywając je w takim przypadku. Dzięki tej dokumentacji, programiści mogą szybko zrozumieć działanie kodu i korzystać z jego funkcji w sposób bardziej efektywny.



Rysunek 5.

Dokumentacja CSS w postaci KSS (Keep Simple Stylesheets) została również stworzona, co pozwala na łatwiejsze zrozumienie i zarządzanie stylami. Każdy fragment kodu został opisany, zawierając informacje na temat jego zastosowania i efektów. Na przykład, dla sekcji "Ciało strony" określono, że tło jest w białym kolorze, a marginesy i wewnętrzne odstępy są usuwane. Analogicznie, dla sekcji formularza określono, że etykiety (label) formularza są ustawione jako bloki i mają odstęp na dole. Dzięki takiemu podejściu dokumentacyjnemu, zarówno programiści, jak i projektanci mogą łatwiej zrozumieć i korzystać z stylów CSS w projekcie.



Rysunek 6. Zdjęcie poglądowe KSS

- **Linki do źródeł**

- <https://www.w3schools.com/html/default.asp>
- <https://www.w3schools.com/css/default.asp>
- <https://www.w3schools.com/js/default.asp>
- <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide>

- **Raport SEO**



Rysunek 7. Raport SEO

**Raport SEO**

- **Metainformacje** (66%): Pomimo że wynik jest w granicach 66%, warto zwrócić uwagę na to, czy wszystkie strony mają odpowiednio zoptymalizowane meta tagi, takie jak meta tytuł, opis i tagi meta keywords.
- **Jakość strony** (48%): Wynik ten sugeruje, że istnieje miejsce na poprawę jakości treści. Możliwe, że zawartość wymaga bardziej szczegółowej analizy pod kątem wartości dodanej dla użytkowników i optymalizacji pod kątem wyszukiwarek.
- **Struktura strony** (74%): Ten wynik jest na ogół pozytywny, sugerując, że struktura strony jest dobrze zorganizowana i łatwa do nawigacji. Jednak warto zwrócić uwagę na wszelkie obszary, które mogą wymagać poprawy, takie jak ulepszenie architektury informacji lub uproszczenie nawigacji.
- **Struktura łącza** (61%): Wynik ten wskazuje na umiarkowaną skuteczność w zarządzaniu strukturą linków na stronie. Może być miejsce na optymalizację wewnętrznego linkowania, aby lepiej kierować ruch na stronie i poprawić indeksację przez wyszukiwarki.
- **Serwer** (0%): Ten wynik jest niepokojący, sugerując, że istnieją problemy związane z serwerem, które mogą wpływać na wydajność i dostępność strony dla użytkowników. Warto zbadać te problemy i podjąć odpowiednie działania naprawcze.
- **Czynniki zewnętrzne** (23%): Wynik ten wskazuje na to, że istnieje miejsce na poprawę czynników zewnętrznych, takich jak linki zwrotne, reputacja witryny i obecność w mediach społecznościowych. Istotne może być zwiększenie aktywności promocyjnej i budowanie wartościowych relacji z innymi witrynami w celu poprawy pozycji strony w wynikach wyszukiwania.
