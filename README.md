# Missione Matrimonio

Raccolta delle idee condivise nel gruppo WhatsApp del matrimonio, pubblicata su GitHub Pages.

- **Sito**: `index.html`, pagina statica senza build né dipendenze esterne.
- **Dati**: database Supabase (progetto `missionematrimonio`). Il sito legge le tabelle `categorie`, `idee`
  e `salvate` con la chiave pubblica, che può solo leggere e chiamare la funzione `toggle_salvata`.
  Le scritture (nuove idee, correzioni, costi) si fanno dal database, non dal repo.
- **Strutture**: `strutture.html`, le location individuate con mappa (Leaflet + OpenStreetMap), semafori,
  stato e diario. Tabelle `strutture` e `strutture_diario`; le modifiche passano da funzioni che verificano
  il PIN di famiglia (hash bcrypt nella tabella `impostazioni`, non leggibile dall'API). Coordinate ottenute
  con `.github/workflows/geocode.yml` (Nominatim) e caricate a mano.
- **Cuore "Salva"**: anonimo. Ogni telefono si genera un identificativo casuale salvato nel browser;
  la card mostra quante persone hanno salvato l'idea.
- **Ping**: `.github/workflows/keepalive.yml` interroga il database ogni tre giorni per evitare la pausa
  automatica del piano gratuito, e fa da test end-to-end (lettura, toggle, scrittura negata).

Tabelle predisposte per il seguito: `fornitori` e `costi`.

Pagine: `index.html` (idee) e `strutture.html` (strutture), collegate dal menu in alto.
