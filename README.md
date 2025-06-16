# HydraBuddy
HydraBuddy


HydraBuddy
Beskrivning
HydraBuddy är en AI-driven app som skickar personliga påminnelser om att dricka vatten baserat på tid (t.ex. nu 14:14 CEST), aktivitetsnivå, väder och dagsljus. Appen lär sig dina vanor för att optimera påminnelserna, vilket gör den perfekt för studenter, yrkesverksamma och andra som vill hålla sig hydrerade under dagen.

Bakgrund
Problem: Många glömmer att dricka tillräckligt med vatten, vilket kan leda till uttorkning och trötthet, särskilt mitt på dagen som nu.
Hur vanligt?: Upp till 75% av människor i utvecklade länder kan vara kroniskt uttorkade, enligt hälsorapporter.
Personlig motivation: Jag vill förbättra min egen hälsa och hjälpa klasskamrater eller vänner som glömmer vatten efter skolarbete eller aktiviteter.
Varför viktigt?: Vatten är grundläggande för hälsan, och en AI-lösning gör det enkelt att hålla koll, vilket är både praktiskt och lärorikt för ett skolprojekt.

Data och AI-tekniker
Datakällor:
Tid: Klockslag från telefonen (t.ex. 14:14 CEST nu, mitt på dagen).
Användarinput: Loggning av vattenintag (t.ex. 2 dl vid 13:00).
Aktivitetsdata: Steg från telefon eller fitness-tracker (t.ex. 5000 steg idag).
Väderdata: Temperatur och fuktighet via OpenWeatherMap API.
Dagsljus: Ljusnivå vid 14:14 CEST (1-värde, dagtid).
Datakvalitet: Konsekvent loggning och pålitliga API-data är avgörande för exakta påminnelser.

AI-tekniker:
Logistisk regression: Predikterar behov baserat på tid, steg och dagsljus (t.ex. >50% = påminnelse).
Neuralt nätverk: Anpassar sig till vädertrender över tid.
Demokod: En enkel implementation med Python:
python

Kollapsa

Radbryt

Kör

Kopiera
from sklearn.linear_model import LogisticRegression
import numpy as np

# Exempeldata: Tid (0-24), Steg (0-10000), Dagsljus (0=mörkt, 1=ljus), Drick (0/1)
X = np.array([[10, 2000, 1], [14, 5000, 1], [20, 4000, 0]])
y = np.array([0, 1, 0])

model = LogisticRegression()
model.fit(X, y)
probability = model.predict_proba([[14, 5000, 1]])[0][1]
print(f"Sannolikhet för att dricka vid 14:14 och 5000 steg (dagtid): {probability:.2f}")

Sannolikhet för att dricka vid 14:14 och 5000 steg (dagtid): 1.00

Kör detta för att se en sannolikhet (t.ex. ~0.6-0.7 mitt på dagen).



Hur används det
Kontext: Används dagligen på smartphone, t.ex. under skoldagen, på jobbet eller fritiden (som nu 14:14 CEST).
Användare: Studenter, lärare, och aktiva personer som behöver påminnelser mitt på dagen.
Påverkan: Bättre hälsa för användare, mer fokuserade klassrum. Vissa kan tycka påminnelser är störande om de kommer för ofta.

Utmaningar
Vad löses inte?: Hanterar inte medicinska restriktioner eller akuta hälsotillstånd.
Begränsningar: Kräver regelbunden input; saknad loggning minskar precision. Dagsljusdata kan vara felaktig utan GPS.
Vad nästa
Tillväxt: Lägg till påminnelser om elektrolytdrycker efter träning, integration med smarta flaskor, och anpassade mål baserat på skol-schema.
Skalning: Bli en skoltjänst för hälsouppföljning eller en global app med lokala väderdata.
Tack
Källor: Inspirerad av open-source-projektet "Water Reminder" på GitHub och OpenWeatherMap API. Använder Scikit-learn (BSD-licens) – ge kredit i kod.
Inspiration: Hälsotips från Elements of AI-kursen och min egen dagliga rutin vid 14:14 CEST!
Installation
För att sätta upp projektet lokalt:

Klona repot: git clone https://github.com/ditt-användarnamn/HydraBuddy.git
Installera beroenden: pip install scikit-learn numpy
Kör demokoden ovan för att testa.

Bidrag
testa koden och ge oss feedback
