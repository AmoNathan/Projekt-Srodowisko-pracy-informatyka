```mermaid

graph TD
    %% Główne węzły
    Start([START])
    Load["Załaduj Bazę Aut<br/>(Marka, Model, Rok, Cena, Zdjęcia)"]
    Decision{Czy dane auta<br/>są kompletne?}
    Error[Wyświetl Komunikat Błędu]
    Process["Przetwarzanie Aut<br/>(Filtry: cena, typ, rok, paliwo)"]
    GenView[Generowanie Widoku Przeglądania]

    %% Widoki aplikacji
    Swipe["Widok Swipe<br/>(Prawo: Lubię <br/>Lewo: Pomijam )"]
    Details["Widok Szczegółów Auta<br/>(Galeria, Specyfikacja)"]

    %% Akcje użytkownika
    Like["Dodaj do Ulubionych"]
    Match["Dopasowanie<br/>(Kontakt ze sprzedawcą)"]

    %% Węzły końcowe
    Save["Zapisz Preferencje<br/>i Historię Swipe"]
    EndNode([KONIEC SESJI])

    %% Połączenia
    Start --> Load
    Load --> Decision

    Decision -- NIE --> Error
    Decision -- TAK --> Process

    Process --> GenView

    %% Rozgałęzienie widoków
    GenView --> Swipe
    GenView --> Details

    %% Logika swipe
    Swipe -- Swipe Right --> Like
    Swipe -- Swipe Left --> Save

    Like --> Match
    Match --> Save

    Details --> Swipe

    Save --> EndNode
