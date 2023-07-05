Rozdzial 1
============

.. toctree::
   :maxdepth: 4
   

Planowanie konserwacji
-----------------------------------------------------------
Planowanie konserwacji obejmuje określenie harmonogramu w którym przeprowadzane będą działania mające na celu utrzymanie bazy danych w optymalnym stanie. To co trzeba mieć na uwadze podczas planowania konserwacji to:

* Określenie harmonogramu
* Tworzenie backupów
* Monitorowanie wydajności
* Optymalizacja danych

Ważne jest, aby planowanie konserwacji było elastyczne i uwzględniało zmienne czynniki, takie jak obciążenie bazy danych, ważność danych, polityki bezpieczeństwa czy dostępność zasobów. Regularne przeglądy planu konserwacji i dostosowywanie go do zmieniających się potrzeb pomoże utrzymać bazę danych w optymalnym stanie i zminimalizować ryzyko awarii.


Uruchamianie, zatrzymywanie i restartowanie serwera bazy danych
------------------------------------------------------------------------------------------------------------------------
Uruchamianie, zatrzymywanie i restartowanie serwera bazy danych są kluczowymi operacjami w zarządzaniu bazami danych. Aby uruchomić serwer bazy danych, należy wywołać odpowiednią komendę lub skrypt, który jest dostarczany wraz z systemem zarządzania bazą danych. W przypadku PostgreSQL, można użyć komendy pg_ctl start, której wywołanie inicjuje proces serwera i umożliwia klientom nawiązywanie połączenia z bazą danych. Aby zatrzymać ten serwer, należy użyć odpowiedniej komendy lub skryptu. Podobnie jak w przypadku uruchamiania, komenda może się różnić w zależności od DBMS. W PostgreSQL można użyć komendy ``pg_ctl stop``. Wywołanie tej komendy powoduje zakończenie działania serwera bazy danych i rozłączenie wszystkich klientów. Restartowanie serwera bazy danych polega na zatrzymaniu i ponownym uruchomieniu serwera. Może być wykonywane w celu na przykład wczytania nowej konfiguracji, wdrożenia aktualizacji lub rozwiązania problemów. Aby zrestartować serwer bazy danych, można po prostu najpierw zatrzymać go, a następnie uruchomić ponownie, używając odpowiednich komend lub skryptów dostarczonych przez DBMS.


Proces VACUUM
---------------
Proces Vacuum odnosi się do operacji, które są wykonywane w celu zarządzania przestrzenią w bazach danych, zwłaszcza w systemach zarządzania bazami danych. Ma on na celu optymalizację wykorzystania miejsca na dysku poprzez np usuwanie martwych krotek, aktualizacja statystyk, reorganizacja danych. Częstotliwość i konfiguracja procesu vacuum zależy od charakterystyki danych i obciążenia systemu. Ważne jest, aby regularnie przeprowadzać procesy vacuum w celu utrzymania optymalnej wydajności bazy danych i zapobiegania nadmiernemu rozrostowi rozmiaru plików danych.
Przykład wykonania komendy VACUUM to:
``VACUUM`` nazwa_tabeli;
Komenda ta przeprowadzi proces czyszczący VACUUM na tabeli nazwa_tabeli.


Ograniczanie i rozłączanie użytkowników
------------------------------------------
Ograniczanie dostępu użytkowników polega na kontrolowaniu uprawnień, poziomu dostępu i operacji w bazie danych. Każdy użytkownik powinien mieć przypisane odpowiednie uprawnienia, które definiują, jakie czynności może wykonywać. To może obejmować np. uprawnienia administracyjne, uprawnienia specjalne. Rozłączanie użytkowników polega na przerwaniu połączenia między użytkownikiem a bazą danych. Może być wykonywane z różnych powodów, takich jak: Planowane prace konserwacyjne, niepożądane działania użytkownika, jeśli liczba aktywnych połączeń użytkowników przekracza określony limit. 


Zapobieganie nowym połączeniom
-------------------------------------------
Zapobieganie nowym połączeniom w bazach danych jest niekiedy wymagane w celu utrzymania kontroli nad dostępem do bazy danych lub w przypadku, gdy baza danych jest niedostępna z powodu różnych czynników. W większości systemów zarządzania bazami danych istnieją ustawienia konfiguracyjne, które kontrolują ilość jednoczesnych połączeń. Poprzez dostosowanie tych ustawień, można ograniczyć maksymalną liczbę jednoczesnych połączeń do jakiejkolwiek wartości. To uniemożliwi nowym użytkownikom nawiązywanie połączenia. 


SCHEMA - zastosowanie
------------------------------------------
Termin SCHEMA odnosi się do logicznej struktury organizacji danych wewnątrz bazy danych. Schema definiuje sposób, w jaki dane są zorganizowane, jakie tabele i relacje istnieją między nimi, a także jakie ograniczenia i reguły dotyczą danych. Schemat umożliwia organizację danych w logiczne grupy, co ułatwia zarządzanie i zrozumienie struktury bazy danych. Wewnątrz schematu można tworzyć tabele, widoki, indeksy, procedury składowane itp., które odnoszą się do określonej funkcjonalności. Wykorzystanie schematów pozwala na separację danych na różne poziomy lub obszary. Na przykład w bazie danych można utworzyć schematy dla różnych modułów aplikacji, zespołów użytkowników lub klientów. Każdy schemat może mieć swoje tabele i obiekty, co pozwala na ograniczenie dostępu do określonych obszarów.
Do stworzenia nowego schematu używamy komendy ``CREATE SCHEMA`` schemat, aby usunąć schemat używamy komendy ``DROP SCHEMA`` schemat.



Zarządzanie transakcjami
------------------------------------------
Transakcje to logiczne jednostki operacji, które muszą zostać wykonane atomowo, czyli albo wszystkie operacje zostaną zatwierdzone i zastosowane do bazy danych, albo żadna z nich nie zostanie zastosowana. Transakcje posiadają cztery podstawowe właściwości, znane jako ACID: 
Atomowość (Atomicity): Transakcja jest jednostką atomową, co oznacza, że ​​wszystkie operacje w ramach transakcji zostaną wykonane lub żadna z nich nie zostanie wykonana. Nie ma pośrednich stanów. Jeśli wystąpi jakikolwiek błąd lub przerwanie, transakcja jest wycofywana, a zmiany nie są wprowadzane do bazy danych. 
Spójność (Consistency): Transakcje muszą zachować spójność danych w bazie. Oznacza to, że przed i po zastosowaniu transakcji dane muszą spełniać określone zasady integralności, reguły walidacji i ograniczenia danych. 
Izolacja (Isolation): Transakcje powinny być odizolowane od siebie nawzajem. Oznacza to, że operacje wykonywane przez jedną transakcję nie są widoczne dla innych transakcji, dopóki transakcja nie zostanie zatwierdzona. Izolacja chroni przed konfliktami i zapewnia spójność danych. 
Trwałość (Durability): Po zatwierdzeniu transakcji jej wyniki muszą być trwałe i odporne na awarie systemu. To oznacza, że ​​wprowadzone zmiany zostaną zachowane nawet w przypadku przerwania zasilania lub innego rodzaju awarii.
Do rozpoczęcia nowej transakcji używamy komendy ``BEGIN``, aby zapisać zmiany w transakcji używamy komendy ``COMMIT``, do cofnięcia błędu służy komenda ``ROLLBACK``.


Zarządzanie indeksami
------------------------------------------
Zarządzanie indeksami jest istotnym elementem optymalizacji wydajności wyszukiwania danych. Indeksy to struktury, które przyspieszają wyszukiwanie rekordów w tabelach poprzez tworzenie dodatkowych struktur umożliwiających bezpośredni dostęp do danych na podstawie wartości indeksowanych kolumn. Indeksy są tworzone na podstawie jednej lub kilku kolumn w tabelach. Przez indeksowanie często używanych kolumn można znacznie przyspieszyć operacje wyszukiwania danych. Istnieje wiele rodzajów indeksów, które różnią się sposobem organizacji danych i sposobem wykorzystania w różnych operacjach. 
