# Gångertabellen

En liten app för att öva på multiplikationstabellen (1–10), gjord för iPad.
Allt ligger i `index.html`, utan beroenden och utan byggsteg.

## Lägen
- **Lugn övning:** ingen tid. Svarar man fel får man försöka igen. Efter två fel visas svaret och man skriver in det. Missade tal kommer tillbaka några frågor senare, och tal som ofta blir fel dyker upp oftare.
- **Tidsutmaning:** slumpade uppgifter på tid. Antal uppgifter (5–100) och tid (0:30–10:00) ställs in på startsidan. Omgången tar slut när alla uppgifter är klara eller när tiden är ute. Rekord sparas per inställning.

Man väljer själv vilka tabeller som ingår. Under "Hur går det?" finns en färgkodad översikt över alla tal och en lista med de senaste utmaningarna.
Allt sparas lokalt i webbläsaren (`localStorage`) på enheten.

## Publicera med GitHub Pages
1. Gå till *Settings → Pages* i repot.
2. Välj *Deploy from a branch*, branch `main` och mappen `/ (root)`.
3. Efter någon minut ligger appen på `https://<användare>.github.io/multiply/`.

## Installera på iPaden
1. Öppna adressen i **Safari**.
2. Tryck på dela-knappen och välj **Lägg till på hemskärmen**.
3. Appen startar nu i helskärm från hemskärmen och fungerar även utan nät.

Obs: statistiken sparas separat för hemskärmsappen och för Safari, så använd alltid hemskärmsikonen.

## Uppdatera
När något ändras i filerna: höj versionen i `CACHE` i `sw.js`, så hämtar iPaden den nya versionen nästa gång appen öppnas med nät.
