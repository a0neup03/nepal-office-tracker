# 🧠 Nepal Political Strategy Engine - Algorithmic Design Document

## 🎯 **Core Innovation: Progressive Consequence System**

Unlike simple games where each choice is independent, this is a **true strategy simulation** where:
- **Every decision shapes future scenarios**
- **Reputation with factions determines available options** 
- **Player traits develop over time, affecting storylines**
- **Real images and current events create authentic experience**
- **Complex algorithms ensure unique gameplay each time**

---

## 🏗️ **Game Architecture**

### **1. Multi-Dimensional State Tracking**

```javascript
gameState = {
  // Core Performance Metrics (0-100)
  stability: 75,    // Government effectiveness 
  economy: 60,      // Economic performance
  morale: 70,       // Public satisfaction
  stress: 15,       // Accumulated crisis pressure
  
  // Reputation Matrix (0-100 with each faction)
  reputation: {
    military: 50,        // Armed forces loyalty
    judiciary: 50,       // Court system relationship
    media: 50,          // Press relations
    youth: 50,          // Young voter support
    international: 50,   // Foreign relations
    congress: 50,       // Major party relations
    uml: 50,
    maoist: 50
  },
  
  // Player Character Development (0-100)
  traits: {
    authoritarian: 0,   // Tendency toward control
    corrupt: 0,         // Willingness to abuse power
    reformist: 0,       // Drive for systematic change
    nationalist: 0,     // Focus on sovereignty
    populist: 0         // Appeal to mass sentiment
  },
  
  // Decision History (affects future scenarios)
  decisionHistory: [], 
  alliances: [],      // Political partnerships formed
  enemies: []         // Burned bridges
}
```

### **2. Dynamic Scenario Selection Algorithm**

```javascript
function selectNextEvent() {
  // Step 1: Filter based on unlock conditions
  const availableEvents = events.filter(event => {
    return checkUnlockConditions(event, gameState);
  });
  
  // Step 2: Weight scenarios based on current state
  const weightedEvents = availableEvents.map(event => ({
    event,
    weight: calculateRelevanceWeight(event, gameState)
  }));
  
  // Step 3: Select most contextually appropriate
  return selectWeightedRandom(weightedEvents);
}

function calculateRelevanceWeight(event, gameState) {
  let weight = 1;
  
  // Higher weight if player's traits align with event theme
  if (event.tags.includes('corruption') && gameState.traits.corrupt > 50) {
    weight *= 2;
  }
  
  // Higher weight if reputation creates natural conflict
  if (event.reputationRequirement) {
    weight *= calculateReputationTension(event, gameState);
  }
  
  return weight;
}
```

### **3. Progressive Choice Generation**

Choices aren't static - they change based on your reputation:

```javascript
function generateDynamicChoices(baseEvent, gameState) {
  return baseEvent.choices.map(choice => {
    // Modify choice availability based on reputation
    if (choice.requiresReputation) {
      const faction = choice.requiresReputation.faction;
      const minRep = choice.requiresReputation.minimum;
      
      if (gameState.reputation[faction] < minRep) {
        choice.disabled = true;
        choice.disabledReason = `${faction} doesn't trust you enough`;
      }
    }
    
    // Modify consequences based on established traits
    if (gameState.traits.authoritarian > 60) {
      choice.effects.morale *= 0.8; // People expect authoritarian behavior
      choice.reputationChanges.youth *= 1.5; // Youth more sensitive
    }
    
    return choice;
  });
}
```

---

## 📊 **Real Event Integration System**

### **Current Events Database (2024)**

**🔥 Breaking News Integration:**
- **Ex-Chief Justice → PM**: Real constitutional crisis
- **Social Media Bans**: Actual 2024 restrictions during protests  
- **Everest Deaths**: Ongoing permit corruption scandal
- **Ex-PM Beaten**: Recent political violence incidents
- **India Border Tensions**: Current China deal backlash

**📸 Real Image Sources:**
- Kathmandu Post archives
- Al Jazeera Nepal coverage  
- Nepali Times historical photos
- Online Khabar current events
- Reuters/AFP wire services

### **Dynamic Image Loading:**
```javascript
function loadEventImage(event) {
  // Primary source: Real news photos
  if (event.imageUrl && event.imageCredit) {
    return {
      src: event.imageUrl,
      credit: event.imageCredit,
      authentic: true
    };
  }
  
  // Fallback: Contextual placeholder
  return generateContextualPlaceholder(event.tags);
}
```

---

## 🎮 **Progressive Gameplay Mechanics**

### **Phase 1: Honeymoon Period (Turns 1-5)**
- **High starting reputation** across all factions
- **Easier scenarios** to establish player style
- **Broad choice availability**
- **Lower stakes consequences**

### **Phase 2: Reality Check (Turns 6-15)**  
- **Reputation differences emerge** based on early choices
- **Scenarios target player's weak spots**
- **Harder decisions with fewer "good" options**
- **Coalition building becomes essential**

### **Phase 3: Crisis Management (Turns 16+)**
- **High-stakes scenarios** based on accumulated stress
- **Limited choices** due to burned bridges
- **Reputation extremes** (strong allies, bitter enemies)
- **Legacy-defining moments**

### **Branching Narrative Example:**

**Turn 5 Choice:** Support ex-Chief Justice's political bid
- ✅ **Constitutional Path** → Judiciary reputation +15 → Unlocks "Judicial Reform" scenarios
- ❌ **Corrupt Deal Path** → Corruption trait +20 → Unlocks "Corruption Scandal" scenarios

**Turn 12 Consequence:**
- **If Constitutional:** Media exposes your opponent's corruption → Reputation boost
- **If Corrupt:** Your own corruption exposed → Crisis event triggered

---

## 🏆 **Winning Strategies & Algorithms**

### **1. The Constitutional Democrat**
```
Strategy: Always choose constitutional options
Algorithm: Maximize (stability + morale) while minimizing authoritarian traits
Unlocks: International support scenarios, democratic reform paths
Risk: May appear weak during crises
```

### **2. The Pragmatic Survivor**  
```
Strategy: Balance reputation across all factions
Algorithm: Maintain reputation variance < 30 points across factions
Unlocks: Coalition-building scenarios, compromise solutions
Risk: May lack strong support base when needed
```

### **3. The Populist Revolutionary**
```
Strategy: Maximize youth + media reputation, ignore elite factions
Algorithm: Prioritize (morale + youth_reputation) over stability
Unlocks: Mass movement scenarios, social media campaigns
Risk: Military/judiciary may turn against you
```

### **4. The Strongman**
```
Strategy: Build military support, control through authority
Algorithm: Maximize (military_reputation + authoritarian_traits)
Unlocks: Security state scenarios, rapid decision-making
Risk: International isolation, popular uprising
```

---

## 📈 **End-Game Analytics System**

### **Victory Conditions (Multiple Paths):**

**🏛️ Democratic Reformer Victory:**
- Stability > 70, Constitutional choices > 80%
- Strong media + international reputation
- Low authoritarian traits

**👑 Benevolent Strongman Victory:**  
- All metrics > 60, High military support
- Authoritarian but effective governance
- Public accepts trade-offs

**🔥 Populist Hero Victory:**
- Morale > 80, Youth reputation > 90
- High stress but strong popular support
- Revolutionary change achieved

**⚖️ Survival Victory:**
- Last 25+ turns without game over
- Any combination of metrics > 30
- Political longevity achievement

### **Failure Analysis:**
```javascript
function analyzeFailure(gameState, decisionHistory) {
  const failureReasons = [];
  
  if (gameState.stability <= 0) {
    const badDecisions = decisionHistory.filter(d => 
      !d.constitutional && d.effects.stability < -10
    );
    failureReasons.push(`Government collapsed due to ${badDecisions.length} major constitutional violations`);
  }
  
  if (gameState.morale <= 0) {
    const unpopularChoices = decisionHistory.filter(d => 
      d.effects.morale < -15
    );
    failureReasons.push(`Public uprising caused by ${unpopularChoices.length} deeply unpopular decisions`);
  }
  
  return failureReasons;
}
```

---

## 🔄 **Replayability Features**

### **1. Scenario Variations:**
- Same crisis, different choices based on reputation
- Historical events appear at different times
- Player's established character affects NPC reactions

### **2. Butterfly Effect System:**
```javascript
// Early choice affects late-game scenario
if (playerChose('supportCorruptJudge', turn: 5)) {
  addToQueue('corruptionScandalExposed', turn: 18);
  modifyScenario('internationalCrisis', severity: +20);
}
```

### **3. Multiple Ending Paths:**
- 15+ different ending scenarios
- Epilogue changes based on decision pattern
- Historical judgment varies by player style

---

## 🎯 **How to Play for Maximum Strategy**

### **Opening Moves (Turns 1-3):**
1. **Establish Character**: Pick consistent approach (reformist/pragmatic/populist)
2. **Build Key Alliance**: Focus on one faction while not alienating others
3. **Constitutional Baseline**: Avoid early constitutional violations

### **Mid-Game (Turns 4-15):**
1. **Reputation Management**: Strengthen chosen allies, manage enemies
2. **Crisis Preparation**: Keep stress below 50 to avoid cascading failures
3. **Trait Development**: Consciously develop coherent character profile

### **End-Game (Turns 16+):**
1. **Legacy Choices**: Make decisions that align with desired victory condition
2. **Coalition Maintenance**: Use built relationships to survive crises
3. **Strategic Sacrifice**: Accept short-term losses for long-term goals

---

## 🇳🇵 **Real Nepal Political Context**

**Why This Matters:**
- **Educational Value**: Learn actual constitutional principles and political history
- **Cultural Authenticity**: Real photos, actual events, genuine dilemmas
- **Contemporary Relevance**: Current events from 2020-2024
- **Historical Depth**: Connections to Nepal's democratic evolution

**Real Learning Outcomes:**
- Understand separation of powers challenges
- Appreciate complexity of coalition governance  
- Recognize international relations constraints
- Value constitutional democracy principles

---

### 🎮 **Ready to Govern Nepal Strategically?**

This isn't just a game - it's a **political strategy laboratory** where every decision matters, every relationship counts, and every choice reshapes your future options.

**Your political legacy awaits...** 🏛️

---

*Access the game: `nepal-strategy-simulator.html`*