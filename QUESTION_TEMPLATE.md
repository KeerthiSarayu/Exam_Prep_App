# Question Template & Content Addition Guide

## 📝 How to Add New Questions

This guide helps you add questions to the platform without technical knowledge.

---

## Question Format Template

```javascript
{
  id: 'unique_question_id',           // Example: 'phy_thermodynamics_q1'
  question: 'Your question text here?',
  options: [
    'Option A',                        // Index 0
    'Option B',                        // Index 1
    'Option C',                        // Index 2
    'Option D'                         // Index 3
  ],
  correct: 1,                          // Index of correct answer (0, 1, 2, or 3)
  concept: 'Specific Concept Name'     // Must match concept in topic definition
}
```

---

## Step-by-Step: Adding Questions

### Step 1: Identify the Topic

First, decide which topic your question belongs to. Current topics:

**Physics:**
- kinematics
- newtons-laws
- work-energy

**Chemistry:**
- atomic-structure

**Mathematics:**
- trigonometry

### Step 2: Write Your Question

Use this template:

```javascript
{
  id: 'k6',  // Next available ID for this topic
  question: 'A ball is thrown vertically upward with speed 40 m/s. What is the time taken to reach maximum height? (g = 10 m/s²)',
  options: [
    '2 seconds',
    '4 seconds',
    '6 seconds',
    '8 seconds'
  ],
  correct: 1,  // Option B (4 seconds) is correct
  concept: 'Equations of Motion'  // From topic's concept list
}
```

### Step 3: Add to the Code

1. Open `index.html` in a text editor
2. Find the `quizQuestions` object (around line 500)
3. Locate your topic (e.g., `'kinematics'`)
4. Add your question to the array:

```javascript
const quizQuestions = {
  'kinematics': [
    // ... existing questions ...
    {
      id: 'k6',
      question: 'Your new question?',
      options: ['A', 'B', 'C', 'D'],
      correct: 1,
      concept: 'Your Concept'
    }
  ]
};
```

### Step 4: Save and Test

1. Save the file
2. Refresh the browser
3. Login and test the quiz
4. Verify your question appears and works correctly

---

## Physics Questions to Add

### Priority Topics for Expansion

#### 1. Thermodynamics (Needed)
```javascript
'thermodynamics': [
  {
    id: 'thermo1',
    question: 'In an adiabatic process, which of the following remains constant?',
    options: [
      'Heat',
      'Temperature',
      'Internal energy',
      'Entropy'
    ],
    correct: 3,
    concept: 'Adiabatic Process'
  },
  {
    id: 'thermo2',
    question: 'The efficiency of a Carnot engine operating between 400K and 300K is:',
    options: [
      '25%',
      '33%',
      '50%',
      '75%'
    ],
    correct: 0,
    concept: 'Carnot Cycle'
  }
]
```

#### 2. Electrostatics (Needed)
```javascript
'electrostatics': [
  {
    id: 'elec1',
    question: 'Two point charges +Q and -Q are separated by distance d. The electric field at the midpoint is:',
    options: [
      'Zero',
      '2kQ/d²',
      '4kQ/d²',
      '8kQ/d²'
    ],
    correct: 3,
    concept: 'Electric Field'
  }
]
```

#### 3. Gravitation (Needed)
```javascript
'gravitation': [
  {
    id: 'grav1',
    question: 'At what height above Earth\'s surface is the gravitational acceleration g/4? (R = radius of Earth)',
    options: [
      'R/2',
      'R',
      '2R',
      '3R'
    ],
    correct: 1,
    concept: 'Variation of g'
  }
]
```

---

## Chemistry Questions to Add

### Organic Chemistry
```javascript
'organic-chemistry': [
  {
    id: 'org1',
    question: 'Which of the following is an example of nucleophilic substitution?',
    options: [
      'Halogenation of alkanes',
      'Hydration of alkenes',
      'Reaction of alkyl halides with OH⁻',
      'Dehydration of alcohols'
    ],
    correct: 2,
    concept: 'Nucleophilic Substitution'
  }
]
```

### Periodic Table
```javascript
'periodic-table': [
  {
    id: 'per1',
    question: 'Which element has the highest electronegativity?',
    options: [
      'Oxygen',
      'Fluorine',
      'Nitrogen',
      'Chlorine'
    ],
    correct: 1,
    concept: 'Electronegativity Trends'
  }
]
```

---

## Mathematics Questions to Add

### Calculus
```javascript
'calculus': [
  {
    id: 'calc1',
    question: 'What is the derivative of sin(2x)?',
    options: [
      'cos(2x)',
      '2cos(2x)',
      '-sin(2x)',
      '-2sin(2x)'
    ],
    correct: 1,
    concept: 'Chain Rule'
  }
]
```

### Algebra
```javascript
'algebra': [
  {
    id: 'alg1',
    question: 'The roots of x² - 5x + 6 = 0 are:',
    options: [
      '1 and 6',
      '2 and 3',
      '-2 and -3',
      '5 and 1'
    ],
    correct: 1,
    concept: 'Quadratic Equations'
  }
]
```

---

## Adding a New Topic

### Step 1: Define the Topic

Add to `subjects` object:

```javascript
const subjects = {
  physics: {
    name: 'Physics',
    topics: [
      // ... existing topics ...
      {
        id: 'thermodynamics',                    // Unique topic ID
        name: 'Thermodynamics',                  // Display name
        concepts: [                              // List of concepts
          'First Law of Thermodynamics',
          'Second Law of Thermodynamics',
          'Carnot Cycle',
          'Adiabatic Process',
          'Isothermal Process'
        ]
      }
    ]
  }
}
```

### Step 2: Add Questions for the Topic

```javascript
const quizQuestions = {
  // ... existing topics ...
  'thermodynamics': [
    // Add 5-10 questions here
  ]
}
```

### Step 3: Test

1. Login as student
2. Navigate to Physics
3. Verify new topic appears
4. Click and take quiz
5. Check all features work

---

## Question Writing Guidelines

### Good Questions

✅ **Clear and Unambiguous**
```javascript
{
  question: 'A 5 kg block slides down a frictionless incline of 30°. What is the acceleration? (g = 10 m/s²)',
  // Clear values, clear question
}
```

✅ **Single Correct Answer**
```javascript
{
  options: [
    '5 m/s²',      // Clearly correct
    '10 m/s²',     // Clearly wrong
    '8.66 m/s²',   // Close but wrong
    '2.5 m/s²'     // Clearly wrong
  ],
  correct: 0
}
```

✅ **Tests Understanding, Not Memorization**
```javascript
{
  question: 'Why does a ball thrown upward eventually come down?',
  options: [
    'Air resistance slows it',
    'Gravitational force acts downward',
    'Initial velocity decreases',
    'Energy is converted to heat'
  ],
  correct: 1,
  concept: 'Newton\'s Law of Gravitation'
}
```

### Bad Questions to Avoid

❌ **Ambiguous Wording**
```javascript
{
  question: 'What happens to velocity?',
  // Happens when? In what context?
}
```

❌ **Multiple Correct Answers**
```javascript
{
  options: [
    'Increases energy',    // Could be correct
    'Does positive work',  // Also correct
    'Transfers momentum',  // Maybe correct?
    'Applies force'        // Also correct
  ]
}
```

❌ **Trick Questions**
```javascript
{
  question: 'A car moves at 60 km/h for 2 hours. Distance?',
  options: [
    '120 km',      // Seems obviously correct
    '120,000 m',   // Same answer, different unit (unfair)
    '30 km',
    '240 km'
  ]
}
```

---

## Concept Mapping

### Ensure Concepts Match

The `concept` field in questions MUST match exactly with concepts defined in the topic:

**Topic Definition:**
```javascript
{
  id: 'kinematics',
  name: 'Kinematics',
  concepts: [
    'Displacement & Velocity',    // ← Exact spelling
    'Acceleration',               // ← Exact spelling
    'Equations of Motion'         // ← Exact spelling
  ]
}
```

**Question:**
```javascript
{
  question: '...',
  concept: 'Acceleration'  // ← Must match EXACTLY
}
```

**Wrong:**
```javascript
{
  concept: 'acceleration'     // ❌ Wrong case
}
{
  concept: 'Accelerations'    // ❌ Plural
}
{
  concept: 'Accel'           // ❌ Abbreviated
}
```

---

## Difficulty Levels (For Future)

Currently, all questions are treated equally. For future versions, you can add difficulty:

```javascript
{
  id: 'k1',
  question: '...',
  options: [...],
  correct: 1,
  concept: 'Acceleration',
  difficulty: 'easy'  // or 'medium', 'hard'
}
```

This allows adaptive difficulty in quizzes.

---

## Question Categories

### Recommended Distribution Per Topic

- **Easy (40%)**: Direct formula application, definitions
- **Medium (40%)**: Multi-step problems, conceptual understanding
- **Hard (20%)**: Complex scenarios, combined concepts

### Example Distribution (10 questions per topic)

```javascript
'kinematics': [
  // Easy (4 questions)
  { id: 'k1', difficulty: 'easy', ... },
  { id: 'k2', difficulty: 'easy', ... },
  { id: 'k3', difficulty: 'easy', ... },
  { id: 'k4', difficulty: 'easy', ... },
  
  // Medium (4 questions)
  { id: 'k5', difficulty: 'medium', ... },
  { id: 'k6', difficulty: 'medium', ... },
  { id: 'k7', difficulty: 'medium', ... },
  { id: 'k8', difficulty: 'medium', ... },
  
  // Hard (2 questions)
  { id: 'k9', difficulty: 'hard', ... },
  { id: 'k10', difficulty: 'hard', ... }
]
```

---

## Content Goals for First Month

### Week 1
- ✅ 3 Physics topics (15 questions) - DONE
- [ ] Add 3 more Physics topics (15 questions)

### Week 2
- [ ] 5 Chemistry topics (25 questions)
- [ ] Polish existing questions

### Week 3
- [ ] 5 Mathematics topics (25 questions)
- [ ] Add difficulty levels

### Week 4
- [ ] Review all content
- [ ] Add 5 questions per topic (total 100+ questions)
- [ ] Test with real students

---

## Quality Checklist

Before adding questions, verify:

- [ ] Question is grammatically correct
- [ ] All options are plausible
- [ ] Only one correct answer
- [ ] Concept field matches topic definition exactly
- [ ] ID is unique (not used elsewhere)
- [ ] Tested in browser
- [ ] Verified answer is actually correct
- [ ] Difficulty is appropriate for target grade

---

## Bulk Adding Questions (Advanced)

If you have questions in Excel/CSV:

1. **Format CSV:**
```csv
id,question,option_a,option_b,option_c,option_d,correct,concept
k6,"Question text?","Option A","Option B","Option C","Option D",1,"Concept Name"
```

2. **Convert to JavaScript:**
- Use online CSV to JSON converter
- Manually format into the required structure
- Copy-paste into code

3. **Or Use Script:** (Coming in Phase 2)
- Upload CSV via admin panel
- Automatic parsing and addition
- Bulk preview before publishing

---

## Getting Help

If you need assistance:

1. **Review this template again**
2. **Check existing questions as examples**
3. **Test changes incrementally** (add 1-2 questions at a time)
4. **Use browser console** (F12) to check for errors
5. **Backup your file** before major changes

---

## Sample Questions for All Subjects

### Physics - Rotational Motion (10 Questions Needed)
```javascript
'rotational-motion': [
  {
    id: 'rot1',
    question: 'A wheel rotates with angular velocity 10 rad/s. A point at 0.5 m from center has linear velocity:',
    options: ['2 m/s', '5 m/s', '10 m/s', '20 m/s'],
    correct: 1,
    concept: 'Angular Velocity'
  }
  // Add 9 more...
]
```

### Chemistry - Chemical Bonding (10 Questions Needed)
```javascript
'chemical-bonding': [
  {
    id: 'bond1',
    question: 'Which molecule has maximum bond angle?',
    options: ['H₂O', 'NH₃', 'CH₄', 'CO₂'],
    correct: 3,
    concept: 'VSEPR Theory'
  }
  // Add 9 more...
]
```

### Mathematics - Probability (10 Questions Needed)
```javascript
'probability': [
  {
    id: 'prob1',
    question: 'A die is rolled. What is the probability of getting an even number?',
    options: ['1/6', '1/3', '1/2', '2/3'],
    correct: 2,
    concept: 'Basic Probability'
  }
  // Add 9 more...
]
```

---

**Ready to add content? Start with 2-3 questions and test before adding more!**
