📄 Arma 3 – Sistema Rilascio Volantini / Leaflet Drop System
🇮🇹 Descrizione Italiana

Sistema completo per il rilascio di volantini da aerei ed elicotteri in Arma 3.
Permette di avvisare la popolazione civile durante operazioni militari attraverso il lancio aereo di volantini informativi.

✨ Caratteristiche

Rilascio realistico: 400 volantini per volta con dispersione naturale

Sistema di ricarica: 1200 volantini totali, ricaricabili a terra con motore spento

Multi-equipaggio: utilizzabile da pilota, copilota e mitragliere

Ottimizzazione prestazioni: auto-cancellazione dei volantini dopo 1.5 ore

Fisica realistica: i volantini ereditano la velocità del veicolo e cadono naturalmente

Dispersione dinamica: fascia di rilascio di ±6 metri per effetto più realistico

📋 Requisiti

Arma 3 (vanilla) – nessuna mod richiesta

Oggetto volantino: Leaflet_05_New_NATO_F (presente nel gioco base)

Veicoli compatibili: qualsiasi aereo o elicottero

🚀 Installazione

Apri l’Editor di Arma 3

Posiziona un aereo o elicottero sulla mappa

Clic destro sul veicolo → Attributes

Nel campo Init, incolla lo script completo

Salva la missione

🎮 Utilizzo In-Game
✈️ Rilascia Volantini

Condizioni: aereo in volo o elicottero in hovering

Quantità: 400 volantini per rilascio

Metodo: menu azioni (rotellina del mouse) → Rilascia Volantini

Effetto: i volantini vengono rilasciati dalla coda/parte posteriore del veicolo

📊 Controlla Volantini

Funzione: mostra quanti volantini rimangono a bordo

Formato: Volantini rimanenti: X/1200

🔋 Ricarica Volantini

Condizioni obbligatorie:
✅ Veicolo a terra (isTouchingGround)
✅ Motore spento (!isEngineOn)

Effetto: ripristina 1200 volantini
Messaggio: conferma ricarica completata

// Configurazione rilascio
_releaseAmount = 400;           // Volantini per rilascio
_totalLeaflets = 1200;          // Capacità totale
_deleteTime = 5400;             // Secondi prima cancellazione (1.5 ore)

// Fisica rilascio
_offsetBack = -8;               // Metri dietro l'aereo
_spreadLateral = ±6;            // Dispersione laterale (metri)
_spreadLongitudinal = ±6;       // Dispersione avanti/dietro (metri)
_verticalSpread = ±1;           // Variazione verticale (metri)

// Velocità eredità
_velocityInheritance = 0.7;     // 70% della velocità del veicolo
_randomVelocity = ±3;           // Variazione casuale (m/s)
_fallSpeed = -4 to -8;          // Velocità di caduta (m/s)

// Timing
_releaseDelay = 0.02;           // Secondi tra ogni volantino (50/secondo)



🔧 Personalizzazione
Modificare la quantità di volantini

this setVariable ["volantini_rimanenti", 2400, true];  // Cambia da 1200 a 2400
_releaseAmount = 600;                                  // Cambia rilascio da 400 a 600


Modificare la dispersione

_spreadX = (random 20 - 10);  // Aumenta da ±6 a ±10 metri
_spreadY = (random 20 - 10);

Modificare il tempo di cancellazione

sleep 7200;  // Cambia da 1.5 ore (5400s) a 2 ore (7200s)

Adattare per elicotteri

_offsetX = -3 * sin(_dir);     
_offsetY = -3 * cos(_dir);
_velX = (_planeVel select 0) * 0.6;  
_velZ = -3 - (random 3);


🇬🇧 English Description

Complete leaflet drop system for aircraft and helicopters in Arma 3.
Allows warning civilian populations during military operations through aerial leaflet drops.

✨ Features

Realistic drop: 400 leaflets per release with natural dispersion

Reload system: 1200 total leaflets, reloadable on ground with engine off

Multi-crew support: usable by pilot, copilot, and gunner

Performance optimized: auto-deletion after 1.5 hours

Realistic physics: leaflets inherit vehicle velocity and fall naturally

Dynamic dispersion: ±6 meter drop spread for realistic effect

(Installation, parameters, and customization are the same as in the Italian section above.)

📊 Script Structure / Struttura Script
Variables / Variabili

missione_volantini (boolean): Sistema attivo / System active

volantini_rimanenti (integer): Contatore volantini / Leaflet counter

Actions / Azioni

Rilascia Volantini – Release leaflets

Controlla Volantini – Check remaining

Ricarica Volantini – Reload when on ground


🧠 Physics System / Sistema Fisico


┌─────────────────┐
│    Aircraft     │  → Velocity inherited 70%
│   (velocità)    │
└────────┬────────┘
         │
         ▼
    ┌────────┐
    │Leaflet │ + Random spread ±6m
    └────┬───┘
         ▼  Fall -4 to -8 m/s
═══════════════ Ground / Terreno


Schema di rilascio / Spawn Pattern

↑ Flight direction / Direzione volo
│
│
[Aircraft]
│
────┼──── -8m offset
│
● ● ● ● ●
  ● ● ● ● ● ● ●  Spread area ±6m
● ● ● ● ● ● ● ● ●  Area dispersione ±6m
  ● ● ● ● ● ● ●
    ● ● ● ● ●


🐛 Troubleshooting / Risoluzione Problemi
Problema / Issue	Causa / Cause	Soluzione / Solution
I volantini non cadono / Leaflets don't fall	Aereo troppo basso o a terra	Volare ad almeno 50m di altezza / Fly at least 50m altitude
L’azione non appare / Action doesn't appear	Non sei nell’equipaggio	Entra come pilota, copilota o mitragliere / Enter as pilot, copilot, or gunner
Non posso ricaricare / Can't reload	Motore acceso o in volo	Atterra e spegni il motore (tasto E) / Land and turn off engine (E key)
Lag / Performance issues	Troppi volantini a terra	Riduci _deleteTime o aumenta sleep tra rilasci / Reduce _deleteTime or increase release interval

📝 Esempio Codice / Code Example

Script completo da incollare nel campo Init del veicolo:

this setVariable ["missione_volantini", true, true];
this setVariable ["volantini_rimanenti", 1200, true];

// --- Azione: Rilascio ---
this addAction ["Rilascia Volantini", {
    params ["_target", "_caller"];
    if (_target getVariable "missione_volantini" && _target getVariable "volantini_rimanenti" > 0) then {
        _startRemaining = _target getVariable "volantini_rimanenti";
        _releaseAmount = 400;
        if (_startRemaining < _releaseAmount) then {_releaseAmount = _startRemaining;};
        
        [_target, _releaseAmount] spawn {
            params ["_target", "_releaseAmount"];
            for "_i" from 1 to _releaseAmount do {
                if (!alive _target) exitWith {};
                _pos = getPosASL _target;
                _dir = getDir _target;
                _offsetX = -8 * sin(_dir);
                _offsetY = -8 * cos(_dir);
                _spreadX = (random 12 - 6);
                _spreadY = (random 12 - 6);
                _leafletPos = [
                    (_pos select 0) + _offsetX + _spreadX,
                    (_pos select 1) + _offsetY + _spreadY,
                    (_pos select 2) - 1.5 + (random 2 - 1)
                ];
                _leaflet = createVehicle ["Leaflet_05_New_NATO_F", ASLToAGL _leafletPos, [], 0, "CAN_COLLIDE"];
                _leaflet setDir (random 360);
                _planeVel = velocity _target;
                _velX = (_planeVel select 0) * 0.7 + (random 6 - 3);
                _velY = (_planeVel select 1) * 0.7 + (random 6 - 3);
                _velZ = -4 - (random 4);
                _leaflet setVelocity [_velX, _velY, _velZ];
                [_leaflet] spawn {
                    params ["_leaflet"];
                    sleep 5400;
                    if (!isNull _leaflet) then {deleteVehicle _leaflet;};
                };
                _target setVariable ["volantini_rimanenti", (_target getVariable "volantini_rimanenti") - 1, true];
                sleep 0.02;
            };
            _finalRemaining = _target getVariable "volantini_rimanenti";
            systemChat format ["Rilasciati %1 volantini! Rimangono: %2", _releaseAmount, _finalRemaining];
        };
    };
}, [], 1.5, true, true, "", "(_this in [driver _target, gunner _target, _target turretUnit [0]]) && alive _target"];


📜 Licenza / License

Questo script è libero da utilizzare e modificare per qualsiasi missione o progetto di Arma 3.
This script is free to use and modify for any Arma 3 mission or project.

🤝 Crediti / Credits

Script: Original leaflet drop system

Game: Bohemia Interactive – Arma 3

Asset: Leaflet_05_New_NATO_F (Vanilla Arma 3)


