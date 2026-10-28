# Unsere Kalender

Zwei Kalender für zwei: ein Adventskalender und ein Wochenkalender für das ganze Jahr. Die Seiten liegen hier nur verschlüsselt und lassen sich ausschließlich mit eurem gemeinsamen Passwort öffnen. Gemeinsam gespeichert wird über Firebase mit Google-Anmeldung.

Schritt 1 reicht, damit alles funktioniert. Die Schritte 2 bis 5 braucht ihr nur für das gemeinsame Speichern, ohne sie speichert jedes Handy für sich.

## 1. GitHub Pages einschalten

1. Im Repository **Settings → Pages** öffnen.
2. Bei **Source** „Deploy from a branch“ wählen, Branch **main**, Ordner **/ (root)**, dann **Save**.
3. Nach ein bis zwei Minuten ist die Seite unter https://olafkocanda.github.io/Paar-Minuten/ erreichbar.

## 2. Firebase-Projekt anlegen

1. https://console.firebase.google.com öffnen und mit Google anmelden.
2. **Projekt erstellen**, Name zum Beispiel `zu-zweit`. Google Analytics wird nicht gebraucht.
3. Es bleibt beim kostenlosen Spark-Tarif, eine Kreditkarte ist nicht nötig.

## 3. Web-App registrieren und Konfiguration eintragen

1. In der Projektübersicht auf das Web-Symbol **</>** tippen.
2. Einen Namen vergeben, „Firebase Hosting“ **nicht** ankreuzen, dann **App registrieren**.
3. Firebase zeigt einen Block `const firebaseConfig = { … }`.
4. Hier im Repository die Datei `firebase-config.js` öffnen, auf den Stift tippen und `null` durch diesen Block ersetzen, ungefähr so:

   ```js
   window.ZU_ZWEIT_FIREBASE = {
     apiKey: "…",
     authDomain: "zu-zweit-xxxx.firebaseapp.com",
     projectId: "zu-zweit-xxxx",
     storageBucket: "zu-zweit-xxxx.appspot.com",
     messagingSenderId: "…",
     appId: "…"
   };
   ```

5. **Commit changes**. Diese Angaben sind nicht geheim, sie sagen nur, welches Firebase-Projekt gemeint ist. Eure Daten schützen die Regeln aus Schritt 5.

## 4. Google-Anmeldung einschalten

1. In Firebase **Build → Authentication → Jetzt starten**.
2. Unter **Sign-in method** den Anbieter **Google** aktivieren, eine Support-E-Mail wählen und speichern.
3. Unter **Settings → Autorisierte Domains** die Domain `olafkocanda.github.io` hinzufügen.

## 5. Datenbank anlegen und absichern

1. **Build → Firestore Database → Datenbank erstellen**.
2. Standort **europe-west3 (Frankfurt)** und **Produktionsmodus** wählen.
3. Den Reiter **Regeln** öffnen, alles löschen und den Inhalt von `firestore.rules` aus diesem Repository einfügen.
4. Die beiden Beispieladressen durch eure echten Google-Adressen ersetzen und **Veröffentlichen**.

Danach dürfen nur diese beiden Konten lesen und schreiben.

## Fertig

Seite öffnen, Passwort eingeben und „Auf diesem Gerät merken“ ankreuzen. Dann in der Statuszeile **Mit Google anmelden**. Steht dort „Gemeinsam gespeichert, angemeldet als …“, läuft alles. Wer sich zuerst anmeldet, bringt den Stand seines Handys mit, zum Beispiel die Namen und das Jahr im Wochenkalender.

## Gut zu wissen

- Das Passwort steht nirgends in diesem Repository.
- Die Entwickleransicht öffnet ihr mit `#entwickler` am Ende der Adresse, zum Beispiel `…/advent.html#entwickler`. Sie speichert nur auf dem eigenen Gerät.
- Ein neues Passwort oder neue Inhalte heißen: Seiten neu verschlüsseln und hier ersetzen.
