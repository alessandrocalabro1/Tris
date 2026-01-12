---
description: Guida alla pubblicazione su App Store e Google Play Store
---

# Pubblicazione Mobile (Android & iOS)

Il tuo progetto è ora configurato come applicazione ibrida nativa utilizzando **Capacitor**. Questo significa che il tuo codice HTML/JS in `www` viene eseguito all'interno di un contenitore nativo.

## 1. Struttura del Progetto

- **`www/`**: Contiene il codice sorgente del tuo gioco (index.html). Ogni volta che modifichi questo file, devi sincronizzare le modifiche con i progetti nativi.
- **`android/`**: Progetto nativo Android.
- **`ios/`**: Progetto nativo iOS (richiede macOS).

## 2. Sincronizzare le Modifiche

Ogni volta che modifichi `www/index.html`, esegui questo comando nel terminale per aggiornare le app native:

```bash
npx cap sync
```

## 3. Build per Android (Google Play Store)

Poiché sei su Windows, puoi completare l'intero processo per Android qui.

### Prerequisiti
- Scarica e installa [Android Studio](https://developer.android.com/studio).

### Passaggi
1.  Apri il progetto Android in Android Studio:
    ```bash
    npx cap open android
    ```
    (Oppure apri manualmente la cartella `android` con Android Studio).
2.  Attendi che **Gradle** finisca la sincronizzazione (può richiedere alcuni minuti la prima volta).
3.  **Testa l'App**: Collega il tuo telefono Android via USB (o usa l'emulatore) e premi il tasto "Run" (triangolo verde) in alto.
4.  **Genera l'APK/Bundle per lo Store**:
    - Vai nel menu: **Build** > **Generate Signed Bundle / APK**.
    - Seleziona **Android App Bundle** (raccomandato per Play Store) o **APK**.
    - Crea una nuova "Key Store" (chiave di firma) e conservala in un luogo sicuro (senza questa non potrai aggiornare l'app in futuro).
    - Completa il wizard per generare il file `.aab` (Bundle).
5.  Carica il file `.aab` sulla [Google Play Console](https://play.google.com/console).

## 4. Build per iOS (Apple App Store)

Per compilare la versione finale per iOS, **hai bisogno di un Mac** con Xcode installato.

1.  Copia l'intera cartella del progetto su un Mac.
2.  Assicurati di aver fatto `npm install`.
3.  Esegui:
    ```bash
    npx cap sync ios
    npx cap open ios
    ```
4.  Si aprirà **Xcode**.
5.  Collega il tuo iPhone o seleziona un simulatore per testare.
6.  Per pubblicare:
    - Imposta il tuo Team di sviluppo nelle impostazioni del progetto (Signing & Capabilities).
    - Vai su **Product** > **Archive**.
    - Una volta archiviato, usa "Distribute App" per caricarlo su **App Store Connect**.

## Note Importanti

- **Icone e Splash Screen**: Per ora l'app ha le icone di default di Capacitor. Per cambiarle, sostituisci i file nelle cartelle `android/app/src/main/res` e `ios/App/App/Assets.xcassets`, oppure usa uno strumento come `capacitor-assets`.
- **Permessi**: Il gioco non richiede permessi speciali (internet, fotocamera, ecc.), quindi è pronto per essere conforme alle policy base.
