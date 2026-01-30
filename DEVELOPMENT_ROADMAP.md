# 🎭 IL TEATRO DELLE OMBRE - Roadmap di Sviluppo

## 📊 Stato Attuale del Progetto

### ✅ Sistemi Implementati
- [x] Sistema di movimento (WASD)
- [x] Sistema di dialogo con typewriter effect
- [x] Sistema di scelte con karma
- [x] Sistema di combattimento/minigame (6 tipi: QTE, Balance, Rhythm, Hold, Breath, Focus)
- [x] Sistema di salvataggio (LocalStorage)
- [x] Sistema maschere/tentazione
- [x] Transizioni tra mappe
- [x] Modalità Endless
- [x] UI del menu principale
- [x] Sistema NPC con interazioni
- [x] Sprite procedurali per personaggi

---

## 🎯 FEATURES DA IMPLEMENTARE

### 1. ⭐⭐⭐⭐⭐ SISTEMA AUDIO - **[PRIORITÀ ALTA]**
**Status:** ❌ Non iniziato  
**Tempo stimato:** 2-3 giorni  
**Critico per l'atmosfera teatrale**

#### Cosa implementare:
- [ ] AudioManager class centrale
- [ ] Musica di sottofondo per ogni scena:
  - Menu principale (orchestrale, misteriosa)
  - Teatro (drammatica, crescendo)
  - Vicolo (tesa, inquietante)
  - Casa del padre (malinconica)
- [ ] Effetti sonori:
  - Dialoghi (typewriter tick)
  - Selezione menu (click elegante)
  - Minigame (feedback successo/fallimento)
  - Transizioni tra mappe (whoosh)
  - Passi del personaggio
  - Apertura/chiusura porte

#### Files da creare:
- `src/systems/AudioManager.ts`
- `public/audio/bgm/` (cartella musiche)
- `public/audio/sfx/` (cartella effetti)

#### Note:
- Usare formati `.mp3` per compatibilità
- Implementare fade in/out per transizioni musicali
- Volume controllabile da settings

---

### 2. ⭐⭐⭐⭐⭐ SISTEMA DI PAUSA - **[PRIORITÀ ALTA]**
**Status:** ❌ Non iniziato  
**Tempo stimato:** 1 giorno  
**Standard per ogni gioco**

#### Cosa implementare:
- [ ] PauseScene con overlay trasparente
- [ ] Tasto ESC per attivare/disattivare
- [ ] Menu pausa con opzioni:
  - Riprendi
  - Impostazioni
  - Torna al menu principale
  - Esci dal gioco
- [ ] Pausa automatica quando finestra perde focus
- [ ] Salvataggio automatico quando si mette in pausa

#### Files da creare:
- `src/scenes/PauseScene.ts`

---

### 3. ⭐⭐⭐⭐ IMPOSTAZIONI/OPZIONI
**Status:** ❌ Non iniziato  
**Tempo stimato:** 2 giorni  
**Accessibilità importante**

#### Cosa implementare:
- [ ] SettingsScene completa
- [ ] Controlli:
  - Slider volume musica (0-100%)
  - Slider volume effetti (0-100%)
  - Slider velocità testo dialoghi
  - Toggle schermo intero
  - Selector lingua (IT/EN)
- [ ] Salvataggio preferenze persistente
- [ ] Preview in tempo reale delle modifiche

#### Files da creare:
- `src/scenes/SettingsScene.ts`
- `src/ui/Slider.ts`
- `src/ui/Toggle.ts`

---

### 4. ⭐⭐⭐⭐ FEEDBACK VISIVO
**Status:** ⚠️ Parziale (solo tint su movimento)  
**Tempo stimato:** 2-3 giorni  
**Migliora la "game feel"**

#### UI Mancante:
- [ ] Barra della salute/energia (se implementi sistema vita)
- [ ] **Indicatore Karma visuale** (medaglione che cambia colore)
  - Bianco/dorato = karma positivo
  - Grigio/nero = karma negativo
  - Animazione pulse quando cambia
- [ ] Contatore stage/round migliorato
- [ ] Minimappa (opzionale)

#### Effetti da aggiungere:
- [ ] Shake camera quando prendi danno
- [ ] Flash schermo per eventi importanti
- [ ] Particelle quando vinci minigame
- [ ] Trail/ombra quando corri veloce
- [ ] Glow sui personaggi interattivi
- [ ] Indicatore "!" sopra NPC con nuovi dialoghi

#### Files da modificare/creare:
- `src/systems/EffectsManager.ts`
- Aggiornare `GameScene.ts` con HUD

---

### 5. ⭐⭐⭐⭐ TUTORIAL MIGLIORATO
**Status:** ⚠️ Basico implementato  
**Tempo stimato:** 2 giorni  
**Attualmente troppo basilare**

#### Miglioramenti:
- [ ] Tutorial interattivo step-by-step
- [ ] Overlay che evidenzia i controlli
- [ ] "Prima volta" per ogni meccanica (salvato in SaveSystem)
- [ ] Tooltip che appaiono sopra oggetti interattivi
- [ ] Frecce indicatrici
- [ ] Non bloccante ma sempre accessibile (menu aiuto)

#### Struttura suggerita:
```typescript
class TutorialStep {
    text: string;
    highlight?: GameObject;
    waitForAction?: 'move' | 'interact' | 'dialog' | 'choice';
    arrow?: {x: number, y: number};
    canSkip: boolean;
}
```

#### Files da modificare:
- `src/scenes/GameScene.ts`
- `src/systems/TutorialManager.ts` (nuovo)

---

### 6. ⭐⭐⭐ ANIMAZIONI PERSONAGGI
**Status:** ⚠️ Sprite statici con tint  
**Tempo stimato:** 3-5 giorni  
**Migliora l'aspetto visivo**

#### Opzioni:
1. **Sprite animati semplici** (2-3 frame per direzione)
2. **Effetti particellari** per simulare movimento
3. **Bob animation** più sofisticata

#### Da implementare:
- [ ] Walk cycle (2 frame min per direzione)
- [ ] Idle breathing animation
- [ ] Animazioni emotive per NPC (jump, shake, etc.)

#### Files da modificare:
- `src/scenes/BootScene.ts` (generazione sprite)
- `src/entities/Player.ts`
- `src/entities/NPC.ts`

---

### 7. ⭐⭐⭐ MENU PRINCIPALE MIGLIORATO
**Status:** ⚠️ Funzionale ma basilare  
**Tempo stimato:** 1-2 giorni  

#### Miglioramenti:
- [ ] Animazione titolo (fade in/pulse/lettere una alla volta)
- [ ] Preview del salvataggio:
  - Data e ora
  - Tempo totale giocato
  - Karma attuale
  - Mappa corrente
- [ ] Opzioni menu aggiuntive:
  - Crediti
  - Come giocare
  - Achievements/Trofei
  - Galleria (unlock con progressione)
- [ ] Transizione animata tra menu e gioco

#### Files da modificare:
- `src/scenes/MenuScene.ts`

---

### 8. ⭐⭐⭐⭐ HUD IN-GAME
**Status:** ⚠️ Solo prompt interazione  
**Tempo stimato:** 2 giorni  

#### Elementi da aggiungere:
```
┌─────────────────────────────────────────┐
│ ❤️ Vita: ████████░░ 80%               │
│ ⚖️ Karma: ●●●●○ (Buono)                │
│ 🎭 Controllo Maschera: [======---] 60% │
│ 📍 Atto II - Teatro San Carlo           │
│ 🎯 Obiettivo: Trova l'uscita            │
└─────────────────────────────────────────┘
```

- [ ] Barra vita (se implementi sistema combattimento con HP)
- [ ] Indicatore karma con icona
- [ ] Barra controllo maschera (tentazione)
- [ ] Testo mappa corrente
- [ ] Obiettivo attuale
- [ ] Mini-icone per stati (es: "Sotto effetto maschera")

#### Files da creare:
- `src/ui/HUD.ts`

---

### 9. ⭐⭐⭐ TRANSIZIONI TEATRALI
**Status:** ⚠️ Fade semplice  
**Tempo stimato:** 2 giorni  
**Perfetto per il tema teatro!**

#### Transizioni da implementare:
- [ ] **Sipario** che si apre/chiude (rosso velluto)
- [ ] **Iris in/out** (stile film muto)
- [ ] **Page turn** per cambio atti
- [ ] **Fade attraverso nero** con testo narrativo
- [ ] Transizione maschera (distorsione quando tentazione alta)

#### Files da creare:
- `src/effects/TransitionManager.ts`

---

### 10. ⭐⭐⭐ SISTEMA INVENTARIO
**Status:** ⚠️ Presente ma non usato  
**Tempo stimato:** 2-3 giorni  

#### Da implementare:
- [ ] UI inventario (griglia 4x6)
- [ ] Categorie: Chiavi, Oggetti, Lettere, Ricordi
- [ ] Descrizioni oggetti con lore
- [ ] Uso oggetti (consumabili se aggiungi HP)
- [ ] Oggetti chiave per sbloccare progressione
- [ ] Icone visive per ogni oggetto

#### Files da creare:
- `src/scenes/InventoryScene.ts`
- `src/types/items.ts`

---

### 11. ⭐⭐⭐ ACHIEVEMENTS/TROFEI
**Status:** ❌ Non implementato  
**Tempo stimato:** 2 giorni  

#### Achievements suggeriti:
- [ ] "Pacifista" - Completa il gioco senza scegliere opzioni aggressive
- [ ] "Dominatore" - Scegli sempre l'opzione maschera
- [ ] "Resistente" - Completa senza mai cedere alla tentazione
- [ ] "Esploratore" - Trova tutti i segreti
- [ ] "Velocista" - Completa in meno di 30 minuti
- [ ] "Collezionista" - Raccogli tutti gli oggetti
- [ ] "Tutti i finali" - Vedi tutti gli ending
- [ ] "Perfezionista" - Vinci tutti i minigame al primo tentativo

#### Files da creare:
- `src/systems/AchievementManager.ts`
- `src/scenes/AchievementsScene.ts`

---

### 12. ⭐⭐⭐ MINIGAME PIÙ RAFFINATI
**Status:** ⚠️ Funzionali ma basilari  
**Tempo stimato:** 3-4 giorni  

#### Miglioramenti per ogni minigame:
- [ ] Tutorial visivo prima volta
- [ ] Difficoltà più bilanciata
- [ ] Feedback audio/visivo più chiaro
- [ ] Combo system (bonus per sequenze perfette)
- [ ] Classifica personale (miglior tempo/punteggio)
- [ ] Ricompense per performance perfetta

#### Nuovi minigame da aggiungere:
- [ ] Memory (carte da teatro)
- [ ] Reaction (schiva attacchi)
- [ ] Pattern matching (sequenza movimenti)

#### Files da modificare:
- `src/systems/MinigameManager.ts`

---

### 13. ⭐⭐⭐ DIALOGHI PIÙ RICCHI
**Status:** ⚠️ Funzionali ma minimal  
**Tempo stimato:** 3-4 giorni  

#### Miglioramenti:
- [ ] **Ritratti dei personaggi** (anche semplici, stile visual novel)
- [ ] **Animazioni emotive** del ritratto:
  - Shake per rabbia
  - Bounce per gioia
  - Fade per tristezza
- [ ] **Scelte con timer** (10 secondi per decidere)
- [ ] **Memoria delle scelte** (NPC ricordano cosa hai detto)
- [ ] **Branching più complesso** (albero decisionale profondo)
- [ ] **Voice blips** (suoni per ogni personaggio)

#### Files da modificare:
- `src/systems/DialogManager.ts`
- `src/config/constants.ts` (più dialoghi)

---

### 14. ⭐⭐ SISTEMA GIORNO/NOTTE
**Status:** ❌ Non implementato  
**Tempo stimato:** 2-3 giorni  
**Opzionale ma interessante**

#### Features:
- [ ] Ciclo giorno/notte basato su progressione
- [ ] Lighting diverso per ogni fase:
  - Mattina (luce calda)
  - Pomeriggio (luce neutra)
  - Sera (arancione)
  - Notte (blu scuro, lanterne)
- [ ] NPC diversi in orari diversi
- [ ] Eventi speciali notturni
- [ ] Negozi/luoghi aperti solo in certi orari

#### Files da creare:
- `src/systems/TimeManager.ts`

---

### 15. ⭐⭐⭐⭐ GESTIONE ERRORI
**Status:** ⚠️ Minimale  
**Tempo stimato:** 1 giorno  

#### Da implementare:
- [ ] Try-catch su tutte le operazioni critiche
- [ ] Error boundaries per scene
- [ ] Fallback quando salvataggio corrotto
- [ ] Logging errori (console + file?)
- [ ] Messaggio user-friendly in caso di crash
- [ ] Auto-recovery quando possibile

#### Files da modificare:
- Tutti i manager principali
- `src/systems/ErrorHandler.ts` (nuovo)

---

### 16. ⭐⭐⭐ PERFORMANCE OPTIMIZATION
**Status:** ⚠️ Non ottimizzato  
**Tempo stimato:** 2 giorni  

#### Ottimizzazioni:
- [ ] Object pooling per particelle
- [ ] Destroy automatico oggetti fuori schermo
- [ ] Texture atlas per ridurre draw calls
- [ ] Limit particelle simultanee (max 100)
- [ ] Riuso sprite invece di creare/distruggere
- [ ] Profiling e identificazione bottleneck

#### Tools:
- Chrome DevTools Performance
- Phaser Debug Panel

---

### 17. ⭐⭐ MOBILE SUPPORT
**Status:** ❌ Non implementato  
**Tempo stimato:** 3-4 giorni  
**Solo se vuoi pubblicare su mobile**

#### Da implementare:
- [ ] Virtual joystick
- [ ] Touch controls per menu
- [ ] UI responsive (scala automatica)
- [ ] Gesture support (swipe, pinch)
- [ ] Ottimizzazione performance mobile
- [ ] Test su device reali

#### Files da creare:
- `src/ui/VirtualJoystick.ts`
- `src/utils/MobileDetector.ts`

---

### 18. ⭐⭐⭐ CREDITS SCENE
**Status:** ❌ Non implementato  
**Tempo stimato:** 1 giorno  

#### Sezioni:
- [ ] Sviluppatore/Team
- [ ] Musica e sound effects (con licenze)
- [ ] Assets grafici utilizzati
- [ ] Librerie (Phaser, TypeScript)
- [ ] Playtester e ringraziamenti
- [ ] Link social/website

#### Style:
- Scroll automatico
- Stile cinematografico
- Musica dedicata
- Easter egg nascosto?

#### Files da creare:
- `src/scenes/CreditsScene.ts`

---

### 19. ⭐⭐⭐ GAME DESIGN DOCUMENT
**Status:** ❌ Non creato  
**Tempo stimato:** Ongoing  
**Per te come riferimento**

#### Sezioni:
- [ ] Storia completa e lore
- [ ] Albero delle scelte completo
- [ ] Bilanciamento karma e endings
- [ ] Mappa della progressione
- [ ] Lista completa dialoghi
- [ ] Meccaniche di gioco dettagliate
- [ ] Art direction e mood board
- [ ] Sound design plan

#### File:
- `GAME_DESIGN.md`

---

## 🎯 ROADMAP SUGGERITA

### 📅 FASE 1 - CORE (2-3 settimane)
**Obiettivo:** Rendere il gioco giocabile e completo

1. ✅ AudioManager + musiche/SFX base
2. ✅ PauseScene funzionale
3. ✅ SettingsScene con controlli
4. ✅ HUD con karma e obiettivi visibili
5. ✅ Feedback visivo base (shake, flash, particles)

**Deliverable:** Gioco giocabile dall'inizio alla fine con audio

---

### 📅 FASE 2 - POLISH (2 settimane)
**Obiettivo:** Migliorare la presentazione

6. ✅ Transizioni teatrali (sipario)
7. ✅ Tutorial interattivo
8. ✅ Dialoghi con ritratti
9. ✅ Menu principale migliorato
10. ✅ Minigame refinement

**Deliverable:** Gioco rifinito e presentabile

---

### 📅 FASE 3 - CONTENT (Ongoing)
**Obiettivo:** Aggiungere contenuto e rigiocabilità

11. ✅ Più dialoghi e branching
12. ✅ Achievement system
13. ✅ Sistema inventario usabile
14. ✅ Endings multipli ben differenziati

**Deliverable:** Gioco con contenuto sostanzioso

---

### 📅 FASE 4 - FINAL (1-2 settimane pre-release)
**Obiettivo:** Preparare per il rilascio

15. ✅ Bug fixing completo
16. ✅ Performance optimization
17. ✅ Playtesting estensivo
18. ✅ Credits e polish finale
19. ✅ Build e packaging

**Deliverable:** Gioco pronto per release

---

## 📝 NOTE IMPLEMENTAZIONE

### Priority Legend:
- ⭐⭐⭐⭐⭐ = Critico (devi farlo)
- ⭐⭐⭐⭐ = Molto importante (migliora molto l'esperienza)
- ⭐⭐⭐ = Importante (aggiunge valore)
- ⭐⭐ = Nice to have (se hai tempo)

### Status Legend:
- ✅ = Completato
- ⚠️ = Parzialmente implementato
- ❌ = Non iniziato
- 🚧 = In lavorazione

---

## 🎮 COME USARE QUESTA ROADMAP

1. **Scegli un item** dalla lista
2. **Leggi i requisiti** e stima il tempo
3. **Crea un branch** git (es: `feature/audio-system`)
4. **Implementa** seguendo le note
5. **Testa** la feature
6. **Aggiorna questo file** con ✅
7. **Merge** e passa al prossimo

---

## 📞 PROSSIMI PASSI IMMEDIATI

**Consiglio di partire con questi 3:**

1. **AudioManager** (più impatto immediato sull'atmosfera)
2. **PauseScene** (standard necessario per ogni gioco)
3. **HUD con karma** (gameplay feedback essenziale)

**Vuoi che implementiamo uno di questi insieme?** 🎭
