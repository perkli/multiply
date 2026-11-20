# Gångertabellen

En liten app för att öva på multiplikationstabellen (1–10), gjord för iPad.
Allt ligger i `index.html`, utan beroenden och utan byggsteg.

## Lägen
- **Lugn övning:** ingen tid. Svarar man fel får man försöka igen. Efter två fel visas svaret och man skriver in det. Ett tal man svarat fel på kommer tillbaka efter ett par andra frågor, och tal man nyligen haft svårt med får ett extra kort i nästa varv.
- **Tidsutmaning:** slumpade uppgifter på tid. Antal uppgifter (5–100) och tid (0:30–10:00) ställs in på startsidan. Omgången tar slut när alla uppgifter är klara eller när tiden är ute. Rekord sparas per inställning.

- **Mina svåraste:** ett pass med 20 uppgifter på de tal man har svårast för, oavsett vilka tabeller som är valda. Blir tillgängligt när appen har sett minst 8 olika tal och 10 tidtagna svar.

### Hur "svårast" räknas ut
Appen mäter svarstiden för varje tal som besvaras rätt på första försöket, i alla lägen. Varje siffra efter den första ger ett avdrag på 0,35 s för skrivtiden, så att tvåsiffriga svar inte ser svårare ut bara för att de tar längre tid att skriva.

Varje tal får en poäng som bygger på två saker:
- **Fel:** andelen fel bland de 6 senaste svaren, utjämnad så att ett enda fel inte väger som 100 %.
- **Långsamhet:** talets mediantid (de 5 senaste) jämfört med barnets egen vanliga svarstid, som är medianen över alla tal. Bara tal som tar tydligt längre tid än vanligt räknas (från 1,2 gånger den vanliga tiden).

Uteliggare filtreras bort på tre sätt:
- Svar räknas inte om appen var i bakgrunden under frågan eller om det tog över 60 s.
- Svar som tar mer än 4 gånger den vanliga tiden (minst 8 s) ignoreras, eftersom man då troligen gjorde något annat.
- Medianer används i stället för medelvärden, så att enstaka långsamma svar inte slår igenom.

Passet består av upp till 10 tydligt svåra tal. Finns det färre än 5 fylls det på med de näst svåraste. De allra svåraste får extra kort i leken. Under "Resultat" finns en tabell över de svåraste talen med antal fel och svarstid.

### Hur talen slumpas
Talen delas ut som en blandad kortlek: varje tal kommer en gång per varv innan något tal upprepas (3×7 och 7×3 räknas som samma tal). Om det går undviks två frågor i rad med en gemensam siffra, och samma tal kommer aldrig inom de senaste fyra frågorna. Om bara den ena siffran hör till en vald tabell visas den oftast först (7 × 4 när man övar 7:ans tabell), annars är ordningen slumpad.

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
