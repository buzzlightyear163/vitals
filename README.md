# VITALS ($VITALS) · Every coin has a pulse.

En bedside-monitor för pump.fun-coins. Man klistrar in en CA och sajten läser coinets senaste timme som en sjukhusmonitor. Monitorn är loggan i 3D, en kub med skärm, och allt på den drivs av riktig data:

- **HR**: trades senaste 5 min. EKG:t på skärmen slår i den takten.
- **NIBP**: köp/sälj senaste timmen. Visas som tryckmätaren på kubens sida.
- **SpO₂**: köpandel senaste 5 min. Styr hur starkt skärmen lyser.
- **TEMP**: prisändring 1h. Varma coins glöder i kanterna, kalla får frost.
- **Triage**: Stable, Elevated, Critical eller Flatline, från fasta regler. Hela monitorn tar färgen.

**The Ward** lägger in nya pump.fun-launches live. När ett coin slutar handlas plattas monitorn ut och sidan sätter en "time of death". Patientkortet (1200×675) är gjort för att delas på X.

All data är gratis och kräver inga nycklar:
- DexScreener public API (`api.dexscreener.com/tokens/v1/solana/...`) för vitals.
- PumpPortals launch-ström (`wss://pumpportal.fun/api/data`) för nya launches och graduations.

Om strömmen inte går att nå visar Ward en tydligt märkt **Preview** med simulerade launches.

## Filer

- `index.html`: hela sajten i en fil (3D-motorn är egen WebGL, inga bibliotek). Utan WebGL visas pixel-loggan i stället.
- `og.jpg`: delningsbild för X och Discord (1200×630).

## Fyll i vid launch

Överst i scriptet i `index.html` (sök på `const CONFIG`):

| Fält | Vad |
|---|---|
| `ca` | $VITALS mint-adress. Tom visar "Posted here and on X at launch". Ifylld sätter alla köpknappar till `pump.fun/coin/<ca>`, gör CA-rutorna kopierbara och låter token-sektionen visa $VITALS egna live-vitals. |
| `x` | Länk till X-kontot, t.ex. `https://x.com/...` |
| `dexscreener` | Valfri DexScreener-länk |
| `site` | Domän som skrivs på patientkorten, t.ex. `vitals.fun` |
| `refreshSec` | Hur ofta ett öppet chart uppdateras (standard 15 s) |
| `fees` | Fördelningen av creator fees som visas i token-sektionen |

## Deploy

1. Skapa ett nytt repo på GitHub och lägg in `index.html` och `og.jpg` i roten.
2. På Vercel: New Project, välj repot, sätt Framework Preset till **Other** och låt build vara tom. Deploy.
3. Koppla domänen om du har en.

## Kolla efter deploy

- Att intron spelar: kuben växer fram, EKG:t tänds på skärmen, mätaren fylls och de gröna ledningarna till panelerna tonar in.
- Att lampan uppe till höger visar **Ward live** (grön). Gul "Preview" betyder att PumpPortal inte gick att nå.
- Klistra in en CA du känner till och kolla att siffrorna stämmer med DexScreener.
- Att typsnitten laddar: Lora (rubriker, gröna kursiva ord), Geist och Geist Mono.
- X-förhandsvisningen, t.ex. genom att posta länken i ett utkast.
- På mobil: att 3D:n flyter och att de två låsta scroll-sekvenserna (Why och How) känns bra.
