```mermaid

graph TD
    User([Użytkownik: Kupujący / Sprzedawca])
    Input[/"Oferty aut (baza danych / API)"/]
    App{{Aplikacja Car Swipe}}
    
    subgraph "Przetwarzanie Danych (Dopasowanie)"
        Cars[/"Auta: Marka / Model"/]
        Params[/"Parametry: Cena / Rok / Przebieg"/]
    end
    
    Heatmap[Widok Swipe<br/>(Like  / Pass )]
    Report[Match / Zainteresowanie]
    
    User -->|Szukam auta| Input
    Input -->|Wczytanie ofert| App
    App --> Cars
    App --> Params
    Cars -->|Analiza preferencji| Swipe
    Params -->|Analiza preferencji| Swipe
    Swipe -->|Decyzja użytkownika| User
    Swipe -->|Polubione| Match
    
    style App fill:#f96,stroke:#333,stroke-width:2px
    style Swipe fill:#bbf,stroke:#333


