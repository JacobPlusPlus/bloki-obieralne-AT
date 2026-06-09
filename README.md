# 🗺️ Mapa Specjalizacji — Program Studiów Informatycznych

Interaktywna aplikacja webowa w formie jednostronicowego dokumentu (SPA), służąca do wizualizacji, filtrowania i analizowania programu studiów inżynierskich dla kierunku **Informatyka** (semestry 3–7). 

Aplikacja pozwala studentom na dynamiczne sprawdzanie, które przedmioty są wspólne dla wielu ścieżek, a które są unikalne dla konkretnej specjalizacji, wraz z wglądem w punkty ECTS.

---

## 🚀 Funkcje aplikacji

* **Dynamiczne filtrowanie:**
    * **Według typu:** Przedmioty wspólne (dzielone przez $\ge$ 2 specjalizacje) oraz unikalne (dostępne tylko na jednej ścieżce).
    * **Według specjalizacji:** Filtrowanie przedmiotów przypisanych do konkretnych profili kształcenia (IST, IO, ID, ISI).
    * **Według wielu semestrów równocześnie:** Zaawansowany przełącznik semestrów (S3–S7) działający w trybie wielokrotnego wyboru (*multi-select*). Kliknięcie wielu semestrów sumuje widok, a ponowne kliknięcie odznacza dany semestr.
* **Wyszukiwarka tekstowa:** Filtrowanie bazy przedmiotów w czasie rzeczywistym na podstawie wpisywanej nazwy.
* **Licznik przedmiotów & Statystyki:** Globalny panel informujący o dokładnej liczbie przedmiotów wspólnych i unikalnych w całej bazie oraz dynamiczny licznik "w locie" pokazujący liczbę pozycji spełniających aktualne kryteria wyszukiwania.
* **Podział na semestry:** Czytelna struktura bloków semestralnych z automatycznym przeliczaniem liczby widocznych przedmiotów w każdym semestrze i ukrywaniem pustych sekcji.
* **Responsywny design (Mobile-First):** Interfejs zaprojektowany z myślą o urządzeniach mobilnych — paski filtrów transformują się na telefonach w wygodne, horyzontalnie przewijane panele dotykowe.

### 🕵️‍♂️ Zaawansowane funkcje ukryte
* **Analizator Kombinacji (Panel Venn):** Po trzykrotnym wciśnięciu klawisza **Spacji** na klawiaturze (poza polem wyszukiwania), nad listą przedmiotów odsłania się zaawansowany panel relacji. Pozwala on zaznaczyć minimum dwie dowolne specjalizacje i wyliczyć liczbę przedmiotów, które są dzielone **dokładnie** przez tę wybraną kombinację (z opcją natychmiastowego nałożenia filtru precyzyjnego).

---

## 🎓 Wspierane specjalizacje

Aplikacja w pełni mapuje cztery ścieżki dyplomowania:
1.  **IST** — Inżynieria Systemów Teleinformatycznych *(kolor jasnoniebieski)*
2.  **IO** — Inżynieria Oprogramowania *(kolor zielony)*
3.  **ID** — Inżynieria Danych *(kolor fioletowy)*
4.  **ISI** — Inżynieria Systemów Inteligentnych i IoT *(kolor pomarańczowy)*

---

## 🛠️ Architektura techniczna i poprawki

Projekt został wykonany w podejściu **Vanilla JS / No-framework**, co gwarantuje zerowy czas ładowania zewnętrznych bibliotek i maksymalną wydajność renderowania na silnikach przeglądarek.

* **UI/UX:** Mroczny, futurystyczny motyw cyber-technologiczny oparty na fontach *Syne* oraz *DM Mono*. Wykorzystuje efekty rozmytych sfer gradientowych (`backdrop-filter`) imitujących głębię interfejsu.
* **Struktura danych:** Cały program studiów zaimplementowany jest w formie płaskiej tablicy obiektów JSON (`RAW`), gdzie każdy obiekt przechowuje strukturę powiązań oraz zindywidualizowane punkty ECTS dla poszczególnych specjalizacji:
    ```javascript
    { 
      name: 'Uczenie maszynowe', 
      sem: 5, 
      specs: ['io', 'id', 'isi'], 
      ects: { io: 4, id: 5, isi: 4 } 
    }
    ```

### 🩹 Ostatnie kluczowe aktualizacje kodu:
1.  **Naprawa logiki semestrów:** Usunięto błąd ograniczający użytkownika do wyboru tylko jednego semestru. Filtry semestralne działają teraz jako niezależne flagi stanów (tablica `state.sems`). Można wybrać np. semestr 3 i 5 jednocześnie, aby porównać ramowe plany.
2.  **Korekta nazewnictwa w legendzie:** Zaktualizowano pełne rozwinięcia akronimów zgodnie z profilem kształcenia: **IST** jako *Inżynieria Systemów Teleinformatycznych* oraz **ISI** jako *Inżynieria Systemów Inteligentnych i IoT*.
3.  **Optymalizacja Mobile View:** Usunięto problem nachodzenia na siebie długich nazw przedmiotów z elementami punktacji ECTS na ekranach smartfonów (zmniejszenie skali fontu, relatywne pozycjonowanie plakietek, blokada ucinania wyrazów).

---

## 💻 Jak uruchomić projekt

Aplikacja nie wymaga serwera ani kompilacji węzłów Node.js. 

1. Pobierz plik `blcks.html` (lub skopiuj jego zawartość).
2. Zapisz plik na dysku komputera.
3. Kliknij dwukrotnie w plik `intes.html`, aby otworzyć go w dowolnej nowoczesnej przeglądarce internetowej (Chrome, Firefox, Edge, Safari).

---

## 📝 Licencja

Projekt stworzony na potrzeby własne jako interaktywna pomoc dydaktyczna w nawigowaniu po programie studiów. Można dowolnie modyfikować tablicę `RAW` w celu dopasowania do programów innych uczelni.
