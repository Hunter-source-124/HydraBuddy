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



KODEN:

<!DOCTYPE html>
<html lang="sv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HydraBuddy Chatbot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .chat-container {
            width: 400px;
            height: 600px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
        }
        .chat-header {
            background-color: #36A2EB;
            color: white;
            padding: 10px;
            text-align: center;
            border-top-left-radius: 10px;
            border-top-right-radius: 10px;
        }
        .chat-messages {
            flex-grow: 1;
            padding: 20px;
            overflow-y: auto;
            background-color: #e9ecef;
        }
        .message {
            margin: 10px 0;
            padding: 10px;
            border-radius: 5px;
            max-width: 70%;
        }
        .bot-message {
            background-color: #36A2EB;
            color: white;
            margin-left: 20px;
        }
        .user-message {
            background-color: #dee2e6;
            margin-right: 20px;
            text-align: right;
        }
        .chat-input {
            display: flex;
            padding: 10px;
            background-color: #fff;
            border-top: 1px solid #ddd;
        }
        .chat-input input {
            flex-grow: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px 0 0 5px;
            outline: none;
        }
        .chat-input button {
            padding: 10px 20px;
            border: none;
            background-color: #36A2EB;
            color: white;
            border-radius: 0 5px 5px 0;
            cursor: pointer;
        }
        .chat-input button:hover {
            background-color: #1e87d8;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">
            <h3>HydraBuddy</h3>
        </div>
        <div class="chat-messages" id="chatMessages">
            <div class="message bot-message">Hej! Jag är HydraBuddy, din vattenpåminnare. Hur kan jag hjälpa dig idag? (Skriv 'status' för att kolla ditt behov)</div>
        </div>
        <div class="chat-input">
            <input type="text" id="userInput" placeholder="Skriv ditt meddelande...">
            <button onclick="sendMessage()">Skicka</button>
        </div>
    </div>

    <script>
        // AI-logik (baserat på tidigare kod)
        function predictDrinkNeed(hours, steps, daylight) {
            const X = [
                [10, 2000, 1], [14, 5000, 1], [20, 4000, 0], [20, 8000, 0]
            ];
            const y = [0, 1, 0, 1];

            // Simpel modell (eftersom vi inte har scikit-learn här, använder vi en dummy-prediktion)
            let probability = 0;
            if (hours >= 14 && hours <= 18 && steps > 4000 && daylight === 1) probability = 0.7;
            else if (hours >= 20 && steps > 6000) probability = 0.6;
            else probability = 0.2;

            return probability;
        }

        function sendMessage() {
            const input = document.getElementById('userInput').value.toLowerCase();
            const chatMessages = document.getElementById('chatMessages');
            const userMessage = document.createElement('div');
            userMessage.className = 'message user-message';
            userMessage.textContent = input;
            chatMessages.appendChild(userMessage);

            // Bot-svar
            const botMessage = document.createElement('div');
            botMessage.className = 'message bot-message';
            let response = '';

            if (input === 'status') {
                const currentTime = new Date().getHours();
                const currentSteps = 5000; // Simulerade steg
                const daylight = currentTime >= 6 && currentTime < 18 ? 1 : 0;
                const probability = predictDrinkNeed(currentTime, currentSteps, daylight);
                response = `Status vid ${new Date().toLocaleTimeString()}: Sannolikhet att du behöver dricka är ${probability.toFixed(2)}.`;
                if (probability > 0.5) {
                    response += ' Tid att dricka vatten! 💧';
                }
            } else {
                response = 'Skriv "status" för att kolla ditt vätskebehov!';
            }

            botMessage.textContent = response;
            chatMessages.appendChild(botMessage);

            // Rensa input och scrolla till botten
            document.getElementById('userInput').value = '';
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
    </script>
</body>
</html>
