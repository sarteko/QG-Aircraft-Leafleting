📄 Arma 3 - Sistema Rilascio Volantini / Leaflet Drop System
🇮🇹 Descrizione Italiana
Sistema completo per il rilascio di volantini da aerei ed elicotteri in Arma 3. Permette di avvisare la popolazione civile durante operazioni militari attraverso il lancio aereo di volantini informativi.
✨ Caratteristiche

Rilascio realistico: 400 volantini per volta con dispersione naturale
Sistema di ricarica: 1200 volantini totali, ricaricabili a terra con motore spento
Multi-equipaggio: Utilizzabile da pilota, copilota e mitragliere
Ottimizzazione prestazioni: Auto-cancellazione volantini dopo 1.5 ore
Fisica realistica: I volantini ereditano la velocità del veicolo e cadono naturalmente
Dispersione dinamica: Fascia di rilascio di ±6 metri per effetto più realistico

📋 Requisiti

Arma 3 (vanilla, nessuna mod richiesta)
Oggetto volantino: Leaflet_05_New_NATO_F (presente nel gioco base)
Veicoli compatibili: Qualsiasi aereo o elicottero

🚀 Installazione

Apri l'Editor di Arma 3
Posiziona un aereo o elicottero sulla mappa
Tasto destro sul veicolo → Attributes
Nel campo Init, incolla lo script completo
Salva la missione

🎮 Utilizzo In-Game
Rilascia Volantini

Condizioni: Aereo in volo o elicottero in hovering
Quantità: 400 volantini per rilascio
Modalità: Apri il menu azioni (rotellina del mouse) → "Rilascia Volantini"
Effetto: I volantini vengono rilasciati dalla coda/parte posteriore del veicolo

Controlla Volantini

Funzione: Visualizza quanti volantini rimangono a bordo
Formato: "Volantini rimanenti: X/1200"

Ricarica Volantini

Condizioni obbligatorie:

✅ Veicolo a terra (isTouchingGround)
✅ Motore spento (!isEngineOn)


Effetto: Ripristina 1200 volantini
Messaggio: Conferma ricarica completata

⚙️ Parametri Tecnici
sqf// Configurazione rilascio
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
_fallSpeed = -4 to -8;          // Velocità caduta (m/s)

// Timing
_releaseDelay = 0.02;           // Secondi tra ogni volantino (50/secondo)
🔧 Personalizzazione
Modificare la quantità di volantini
sqfthis setVariable ["volantini_rimanenti", 2400, true];  // Cambia da 1200 a 2400
_releaseAmount = 600;  // Cambia rilascio da 400 a 600
Modificare la dispersione
sqf_spreadX = (random 20 - 10);  // Aumenta da ±6 a ±10 metri
_spreadY = (random 20 - 10);
Modificare il tempo di cancellazione
sqfsleep 7200;  // Cambia da 1.5 ore (5400s) a 2 ore (7200s)
Adattare per elicotteri
sqf_offsetX = -3 * sin(_dir);     // Riduce offset da -8 a -3 metri
_offsetY = -3 * cos(_dir);
_velX = (_planeVel select 0) * 0.6;  // Riduce eredità velocità
_velZ = -3 - (random 3);       // Riduce velocità caduta

🇬🇧 English Description
Complete leaflet drop system for aircraft and helicopters in Arma 3. Allows warning civilian population during military operations through aerial leaflet drops.
✨ Features

Realistic drop: 400 leaflets per release with natural dispersion
Reload system: 1200 total leaflets, reloadable on ground with engine off
Multi-crew: Usable by pilot, copilot, and gunner
Performance optimization: Auto-deletion after 1.5 hours
Realistic physics: Leaflets inherit vehicle velocity and fall naturally
Dynamic dispersion: ±6 meter drop spread for realistic effect

📋 Requirements

Arma 3 (vanilla, no mods required)
Leaflet object: Leaflet_05_New_NATO_F (included in base game)
Compatible vehicles: Any aircraft or helicopter

🚀 Installation

Open Arma 3 Editor
Place an aircraft or helicopter on the map
Right-click on vehicle → Attributes
In the Init field, paste the complete script
Save the mission

🎮 In-Game Usage
Release Leaflets

Conditions: Aircraft in flight or helicopter hovering
Quantity: 400 leaflets per release
Method: Open action menu (scroll wheel) → "Rilascia Volantini"
Effect: Leaflets are released from tail/rear of vehicle

Check Leaflets

Function: Display remaining leaflets on board
Format: "Volantini rimanenti: X/1200" (Remaining leaflets: X/1200)

Reload Leaflets

Required conditions:

✅ Vehicle on ground (isTouchingGround)
✅ Engine off (!isEngineOn)


Effect: Restores 1200 leaflets
Message: Reload confirmation

⚙️ Technical Parameters
sqf// Release configuration
_releaseAmount = 400;           // Leaflets per release
_totalLeaflets = 1200;          // Total capacity
_deleteTime = 5400;             // Seconds before deletion (1.5 hours)

// Release physics
_offsetBack = -8;               // Meters behind aircraft
_spreadLateral = ±6;            // Lateral dispersion (meters)
_spreadLongitudinal = ±6;       // Forward/backward dispersion (meters)
_verticalSpread = ±1;           // Vertical variation (meters)

// Velocity inheritance
_velocityInheritance = 0.7;     // 70% of vehicle velocity
_randomVelocity = ±3;           // Random variation (m/s)
_fallSpeed = -4 to -8;          // Fall speed (m/s)

// Timing
_releaseDelay = 0.02;           // Seconds between each leaflet (50/second)
🔧 Customization
Change leaflet quantity
sqfthis setVariable ["volantini_rimanenti", 2400, true];  // Change from 1200 to 2400
_releaseAmount = 600;  // Change release from 400 to 600
Change dispersion
sqf_spreadX = (random 20 - 10);  // Increase from ±6 to ±10 meters
_spreadY = (random 20 - 10);
Change deletion time
sqfsleep 7200;  // Change from 1.5 hours (5400s) to 2 hours (7200s)
Adapt for helicopters
sqf_offsetX = -3 * sin(_dir);     // Reduce offset from -8 to -3 meters
_offsetY = -3 * cos(_dir);
_velX = (_planeVel select 0) * 0.6;  // Reduce velocity inheritance
_velZ = -3 - (random 3);       // Reduce fall speed
```

---

## 📊 Script Structure / Struttura Script

### Variables / Variabili
- `missione_volantini` (boolean): Sistema attivo / System active
- `volantini_rimanenti` (integer): Contatore volantini / Leaflet counter

### Actions / Azioni
1. **Rilascia Volantini** (Release Leaflets)
   - Priority: 1.5
   - Condition: In crew + alive
   
2. **Controlla Volantini** (Check Leaflets)
   - Priority: 1.5
   - Condition: In crew + alive
   
3. **Ricarica Volantini** (Reload Leaflets)
   - Priority: 1.5
   - Condition: In crew + alive + engine off + on ground

### Physics System / Sistema Fisico
```
┌─────────────────┐
│    Aircraft     │ Velocity inherited 70%
│   (velocità)    │ Velocità ereditata 70%
└────────┬────────┘
         │
         ▼
    ┌────────┐
    │Leaflet │ + Random spread ±6m
    │        │ + Dispersione casuale ±6m
    └────┬───┘
         │
         ▼ Fall -4 to -8 m/s
           Caduta -4 a -8 m/s
         │
         ▼
    ═══════════ Ground / Terreno
```

### Spawn Pattern / Schema Rilascio
```
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
I volantini non cadono / Leaflets don't fall
Causa: Aereo troppo basso o a terra
Soluzione: Volare ad almeno 50m di altezza
Cause: Aircraft too low or on ground
Solution: Fly at least 50m altitude
L'azione non appare / Action doesn't appear
Causa: Non sei nell'equipaggio
Soluzione: Entra come pilota, copilota o mitragliere
Cause: Not in crew
Solution: Enter as pilot, copilot, or gunner
Non posso ricaricare / Can't reload
Causa: Motore acceso o in volo
Soluzione: Atterra e spegni il motore (tasto E)
Cause: Engine on or in flight
Solution: Land and turn off engine (E key)
Lag/Performance issues
Causa: Troppi volantini a terra
Soluzione: Riduci _deleteTime o aumenta sleep tra rilasci
Cause: Too many leaflets on ground
Solution: Reduce _deleteTime or increase sleep between releases

📝 Code Example / Esempio Codice
Full Script / Script Completo
sqfthis setVariable ["missione_volantini", true, true];  
this setVariable ["volantini_rimanenti", 1200, true];  
  
this addAction ["Rilascia Volantini", {  
    params ["_target", "_caller"];  
    if (_target getVariable "missione_volantini" && _target getVariable "volantini_rimanenti" > 0) then {  
        _startRemaining = _target getVariable "volantini_rimanenti";  
        _releaseAmount = 400;  
        if (_startRemaining < _releaseAmount) then {  
            _releaseAmount = _startRemaining;  
        };  
          
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
                  
                _leaflet setVectorDirAndUp [  
                    [random 2 - 1, random 2 - 1, -1],  
                    [random 2 - 1, random 2 - 1, 1]  
                ];  
                  
                [_leaflet] spawn {  
                    params ["_leaflet"];  
                    sleep 5400;  
                    if (!isNull _leaflet) then {  
                        deleteVehicle _leaflet;  
                    };  
                };  
                  
                _currentRemaining = _target getVariable "volantini_rimanenti";  
                _target setVariable ["volantini_rimanenti", _currentRemaining - 1, true];  
                  
                sleep 0.02;  
            };  
              
            _finalRemaining = _target getVariable "volantini_rimanenti";  
            systemChat format ["Rilasciati %1 volantini! Rimangono: %2", _releaseAmount, _finalRemaining];  
              
            if (_finalRemaining <= 0) then {  
                systemChat "Missione completata: tutti i volantini distribuiti!";  
                _target setVariable ["missione_volantini", false, true];  
            };  
        };  
    };  
}, [], 1.5, true, true, "", "(_this in [driver _target, gunner _target, _target turretUnit [0]]) && alive _target"];  
  
this addAction ["Controlla Volantini", {  
    params ["_target"];  
    _remaining = _target getVariable "volantini_rimanenti";  
    hint format ["Volantini rimanenti: %1/1200", _remaining];  
}, [], 1.5, true, true, "", "(_this in [driver _target, gunner _target, _target turretUnit [0]]) && alive _target"];  
  
this addAction ["Ricarica Volantini", {  
    params ["_target", "_caller"];  
     
    if (isEngineOn _target) exitWith { 
        hint "Spegni il motore prima di ricaricare i volantini!"; 
    }; 
     
    if (!isTouchingGround _target) exitWith { 
        hint "L'aereo deve essere a terra per ricaricare i volantini!"; 
    }; 
     
    _target setVariable ["volantini_rimanenti", 1200, true];  
    _target setVariable ["missione_volantini", true, true];  
    systemChat "Volantini ricaricati! 1200/1200 pronti per il lancio.";  
}, [], 1.5, true, true, "", "(_this in [driver _target, gunner _target, _target turretUnit [0]]) && alive _target && !(isEngineOn _target) && (isTouchingGround _target)"];

📜 License / Licenza
This script is free to use and modify for any Arma 3 mission or project.
Questo script è libero da utilizzare e modificare per qualsiasi missione o progetto di Arma 3.

🤝 Credits / Crediti

Script: Original leaflet drop system
Game: Bohemia Interactive - Arma 3
Asset: Leaflet_05_New_NATO_F (Vanilla Arma 3)


📧 Support / Supporto
For issues, suggestions, or improvements, please open an issue on GitHub.
Per problemi, suggerimenti o miglioramenti, apri una issue su GitHub.
