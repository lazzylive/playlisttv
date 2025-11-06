<div align="center">
    <a href="README.md">English</a> | <b>Italiano</b>
</div>
Questo progetto è liberamente tratto da https://github.com/ZapprTV. Probabilmente se vuoi ottenre il meglio conviene seguire direttamente lo sviluppatore di zappr. la playlist di lazzy ne deriva l'aspetto tecnico e personlizzerà poi i contenuti. la mente geniale dietro al progetto di sviluppo sarà sempre https://github.com/ZapprTV.

di seguito le informazioni per chi volesse creare un progetto simile:

# Informazioni sullo sviluppo locale
## Prepara l'ambiente di sviluppo
1. Clona la repo: `git clone https://github.com/ZapprTV/Zappr`
2. Installa le dipendenze: `npm install` (o `pnpm install`)
3. Modifica il file `public/config.json` se necessario

Il file `public/config.json` è il file dove, oltre agli URL delle API, sono anche presenti gli URL delle liste dei canali e ai loghi. Di default sono presenti quelli hostati da Zappr (`channels.zappr.stream`), ma se ti serve utilizzare una copia locale, clona la repo relativa:

`git clone https://github.com/ZapprTV/channels`

E poi modifica `public/config.json` per farlo puntare alla tua versione locale:
```json
    "channels": {
        "host": "/channels"
    },
    [...]
    "logos": {
        "host": "/channels/logos",
        [...]
    },
```

## Passaggi successivi
Se vuoi solo avviare un server locale per motivi di test, esegui `npm run dev` (o `pnpm run dev`).

Se invece vuoi eseguire una build, che verrà poi posizionata nella cartella `dist/`, esegui `npm run build` (o `pnpm run build`).
- La build userà la stessa configurazione che hai specificato in `config.json`, e di default includerà solo i file del frontend nella cartella della build. Se vuoi includere anche i file delle liste dei canali e dei loghi, aggiungi l'argomento da riga di comando `--bundleChannels`.
    - `--bundleChannels` di default scarica le liste dei canali e i loghi da `https://github.com/ZapprTV/channels`, ma se vuoi che le scarichi da un'altra repo Git oppure che le copi da una cartella locale, specifica il nome della cartella / l'URL della repo Git **(con .git alla fine)** nell'argomento `--channelsURL`.
        - Per esempio, `--channelsURL=Canali` copierà la cartella locale `Canali` e la inserirà nella build, mentre `--channelsURL=https://github.com/Utente123/Canali.git` clonerà la repo GitHub `Utente123/Canali` e la inserirà nella build.
    - **IMPORTANTE**: Per specificare gli argomenti da riga di comando con NPM bisogna scrivere `--` prima dei vari argomenti.
        - Quindi, per esempio, invece di scrivere `npm run build --bundleChannels` serve scrivere `npm run build -- --bundleChannels`.
        - **Questo problema non si presenta con PNPM.** Se stai usando PNPM va bene anche, per esempio, `pnpm run build --bundleChannels`.
