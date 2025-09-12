# 🎮 Nepal Government Simulation Game - Complete Development Guide

## 🎯 **Game Overview**

This is a sophisticated text-based simulation game that challenges players to navigate the complex political landscape of modern Nepal while adhering to constitutional principles. The game serves as both entertainment and educational tool about Nepal's governance challenges.

## 🔧 **Advanced Game Mechanics**

### **Core Metrics System (0-100 scale):**
- **Political Stability**: Trust in institutions, government effectiveness
- **Economic Prosperity**: GDP growth, citizen wealth, employment 
- **Public Morale**: National unity, happiness, hope
- **Systemic Stress**: Hidden accumulation score (0-100) representing corruption, division, decay

### **Constitutional Framework (Rule of Law Mechanic):**
- Every choice flagged as `constitutional: true/false`
- Unconstitutional choices trigger severe penalties (-25 stability, +10 stress)
- Educational explanations reference Nepal Constitution 2015
- Visual warnings (red borders, warning icons) for unconstitutional options

### **Dynamic Event System:**
- Events selected based on current game state and prerequisites
- Tagged system (`economic`, `judiciary`, `foreign_policy`) for logical flow
- Historical context provided for each scenario

### **Crisis Trigger System:**
- **Stress Level 25+**: Public protests erupt
- **Stress Level 50+**: No-confidence motion filed  
- **Stress Level 75+**: Constitutional crisis declared

## 📊 **Content Generation Plan - 30 Scenarios**

### **Step 1: Research Framework**

For each scenario, research from **two sources**:

1. **Current Events (2022-2024)**: 
   - Search Nepal news from Kathmandu Post, MyRepublica, Rising Nepal
   - Focus on: judicial appointments, coalition politics, foreign relations, economic policy
   - Document real articles and their URLs

2. **Historical Precedents**:
   - Research similar past events: 1990 Jana Andolan, 2006 People's Movement, 2015 Constitution crisis
   - Identify patterns and outcomes from Nepal's political history
   - Connect current events to historical context

### **Step 2: Scenario Categories (5 scenarios each)**

1. **Judicial Independence** (5 scenarios)
   - Supreme Court appointments
   - Court rulings vs government policy
   - Judicial review of legislation

2. **Coalition Politics** (5 scenarios)
   - Provincial government crises
   - Federal coalition management
   - Party defections and floor-crossing

3. **Foreign Relations** (5 scenarios)  
   - India-China balancing act
   - Border disputes
   - International development partnerships

4. **Economic Policy** (5 scenarios)
   - Budget allocation decisions
   - Foreign investment approvals
   - Development vs environmental protection

5. **Federal-Provincial Relations** (5 scenarios)
   - Resource sharing conflicts
   - Concurrent jurisdiction disputes  
   - Local government coordination

6. **Constitutional Crises** (5 scenarios)
   - Emergency power usage
   - Presidential discretionary powers
   - Constitutional amendment attempts

### **Step 3: Scenario Data Structure**

Each scenario must follow this exact JSON format:

```json
{
  "id": "event_XX",
  "title": "Descriptive Event Title",
  "description": "2-3 sentence neutral description of situation",
  "source_article": "URL of real news article this is based on",
  "image_search_query": "Specific search term for real photo",
  "image_source_credit": "Photographer/Agency name",
  "tags": ["category1", "category2"],
  "historical_context": "Reference to similar past event with analysis",
  "prerequisites": { 
    "min_stability": 0, 
    "max_stability": 100, 
    "required_turn": 1 
  },
  "choices": [
    {
      "text": "Choice description",
      "outcome": "Detailed consequence explanation", 
      "is_constitutional": true/false,
      "constitutional_implication": "Reference to specific constitutional articles/principles",
      "effects": { 
        "stability": 0, 
        "economy": 0, 
        "morale": 0, 
        "stress": 0 
      }
    }
  ]
}
```

### **Step 4: Real Scenario Examples**

#### **Research Example 1: Supreme Court vs Executive**
- **Current Event**: Search "Nepal Supreme Court government conflict 2023"
- **Historical Context**: 2020 Cholendra Rana appointment controversy
- **Constitutional Issue**: Article 128 (Judicial Independence)

#### **Research Example 2: Provincial Coalition Crisis**  
- **Current Event**: Search "Nepal provincial government collapse 2023"
- **Historical Context**: 2021 Gandaki Province government changes
- **Constitutional Issue**: Article 168 (Provincial Assembly)

### **Step 5: Image Sourcing Guidelines**

Use specific search queries for authentic photos:
- "Nepal Supreme Court building Kathmandu"
- "Nepal Parliament Singha Durbar"
- "Nepal Prime Minister office"
- "Nepal President Shital Niwas"

**Credit Requirements**: Always attribute to photographer/news agency

## 🛠 **Implementation Steps**

### **Step 1: Generate All 30 Scenarios**
1. Research each category systematically
2. Create JSON data following exact format
3. Ensure constitutional accuracy for each choice
4. Include historical context for educational value

### **Step 2: Source and Credit Images**  
1. Use image_search_query to find relevant photos
2. Paste URLs into scenario data
3. Add proper source_credit for ethical usage
4. Prefer government/news agency photos

### **Step 3: Deploy Complete Game Engine**
The provided HTML file (`nepal-government-simulator.html`) includes:

**✅ Complete Features:**
- All 4 metrics with visual progress bars
- Dynamic event selection based on game state
- Constitutional warning system with red borders
- Crisis trigger system at stress thresholds
- Historical context display for each event
- Mobile-responsive design with Nepal flag theme

**✅ Advanced Mechanics:**
- Prerequisite checking for event flow
- Effects calculation and bounds checking
- Game over conditions (stability ≤ 0, morale ≤ 0, stress ≥ 100)
- Crisis alert system with animations

### **Step 4: Educational Integration**

**Constitutional Education:**
- Each unconstitutional choice explains WHY it violates the constitution
- References specific articles (e.g., Article 128, Article 168)
- Historical precedents provide context for decisions

**Political Literacy:**
- Real-world scenarios teach about Nepal's governance challenges
- Coalition dynamics reflect actual party politics
- Foreign policy choices mirror Nepal's geopolitical reality

## 🎯 **Testing and Refinement**

### **Balance Testing:**
- Ensure no single strategy dominates
- Constitutional choices should be viable but challenging  
- Crisis events should feel impactful but not overwhelming

### **Educational Accuracy:**
- Verify all constitutional references
- Check historical context accuracy
- Ensure political scenarios reflect real complexities

## 🚀 **Integration with Nepal Office Tracker**

The game can be integrated into your existing Nepal Office Tracker website:

1. **Add to navigation menu**: "Government Simulator"
2. **Link from analytics page**: "Experience governing Nepal yourself!"
3. **Educational context**: Complement citizen feedback with leadership perspective

## 📈 **Success Metrics**

**Educational Outcomes:**
- Players understand constitutional principles
- Increased awareness of governance challenges
- Historical literacy about Nepal's political evolution

**Engagement Metrics:**
- Average session length
- Scenario completion rates  
- Constitutional vs unconstitutional choice ratios

This comprehensive framework creates a sophisticated, educational, and entertaining simulation that honors Nepal's constitutional democracy while teaching players about the complexities of governance.

---

**🇳🇵 Ready to experience the challenges of governing Nepal!**