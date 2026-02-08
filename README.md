# JEE Prep Platform - Adaptive Learning System

## 🎓 Project Overview

An intelligent web-based learning platform designed for students preparing for IIT-JEE exams. The platform features an **adaptive learning system** that identifies weak concepts and creates personalized follow-up tests to ensure mastery.

### Key Features

✅ **Adaptive Quiz System**: Automatically generates follow-up tests based on incorrectly answered questions
✅ **Concept Tracking**: Identifies and tracks weak concepts requiring additional study
✅ **Attention Alerts**: Flags concepts that students fail multiple times
✅ **Teacher Dashboard**: Real-time monitoring of student progress and performance
✅ **Multi-Subject Support**: Physics, Chemistry, and Mathematics content
✅ **Grade-Level Customization**: Content for 10th, 11th, 12th grade and long-term students
✅ **Free Hosting**: No server costs - runs entirely in the browser with localStorage

---

## 🚀 Quick Start

### Option 1: Open Directly in Browser (Easiest)

1. Download the `index.html` file
2. Double-click to open it in any modern web browser
3. Login with demo credentials (see below)

### Option 2: Deploy to Free Hosting

#### Deploy to GitHub Pages (Recommended)

1. Create a new GitHub repository
2. Upload `index.html` to the repository
3. Go to Settings → Pages
4. Select main branch as source
5. Your site will be live at `https://yourusername.github.io/repository-name`

#### Deploy to Netlify

1. Go to [netlify.com](https://www.netlify.com/)
2. Drag and drop the `index.html` file
3. Get instant free hosting with SSL

#### Deploy to Vercel

1. Go to [vercel.com](https://vercel.com/)
2. Import your repository or upload the file
3. Deploy with one click

---

## 👥 Demo Credentials

### Students (10 accounts available)
- **Username**: `student1` to `student10`
- **Password**: `pass123`
- **User Type**: Student

**Sample Student Accounts:**
- student1 - Rahul Sharma (11th Grade)
- student2 - Priya Patel (11th Grade)
- student3 - Amit Kumar (12th Grade)
- student4 - Sneha Reddy (11th Grade)
- student5 - Rohan Gupta (12th Grade)
- student6 - Anjali Singh (10th Grade)
- student7 - Vikram Joshi (11th Grade)
- student8 - Meera Iyer (12th Grade)
- student9 - Karan Malhotra (11th Grade)
- student10 - Divya Nair (10th Grade)

### Teacher
- **Username**: `teacher1`
- **Password**: `teach123`
- **User Type**: Teacher

---

## 📚 Platform Workflow

### For Students

1. **Login** → Select subject → Choose topic
2. **Take Quiz** → Answer MCQs (5 questions per topic)
3. **Get Results** → See score and concepts to review
4. **Review Concepts** → Study recommended materials
5. **Take Follow-up Test** → Mix of previously wrong + new questions
6. **Repeat Until Mastery** → System tracks progress automatically

### Adaptive Learning Logic

```
First Attempt → Student answers questions
    ↓
If any wrong → System identifies weak concepts
    ↓
Results show: Score + Concepts to Review (NO answers shown)
    ↓
Student reviews concepts
    ↓
Follow-up Test → 50% previously wrong + 50% new questions
    ↓
If still wrong → "Attention Required" flag raised
    ↓
Teacher notified → Can provide personalized help
```

### For Teachers

1. **Login** → View student overview table
2. **Monitor Progress** → See attempts, weak concepts, status
3. **View Details** → Click on any student for detailed breakdown
4. **Identify Struggling Students** → "Attention Required" alerts
5. **Provide Targeted Help** → Focus on flagged concepts

---

## 🏗️ Technical Architecture

### Technology Stack
- **Frontend**: Pure HTML, CSS, JavaScript (No frameworks)
- **Storage**: Browser localStorage (persistent data)
- **Hosting**: Static file hosting (GitHub Pages, Netlify, Vercel)
- **Cost**: 100% FREE - No backend, no database fees

### Data Structure

```javascript
// Student Progress stored in localStorage
{
  "student1": {
    "name": "Rahul Sharma",
    "grade": "11th",
    "subjects": {
      "physics": {
        "kinematics": {
          "attempts": 2,
          "scores": [60, 80],
          "wrongQuestions": ["k1", "k4"],
          "weakConcepts": {
            "Acceleration": { failures: 2, lastAttempt: timestamp }
          }
        }
      }
    },
    "attentionRequired": ["Acceleration", "Relative Motion"]
  }
}
```

### Key Algorithms

**Follow-up Test Generation:**
```javascript
if (previousWrongQuestions.length > 0) {
  followUpQuestions = 50% wrong questions + 50% new questions
  Mix and randomize
} else {
  Take all questions (first attempt)
}
```

**Attention Flagging:**
```javascript
if (questionWrong in followUpTest && questionWrong in previousTest) {
  Flag concept for "Attention Required"
  Notify teacher dashboard
}
```

---

## 📊 Sample Content Included

### Physics (3 Topics - 15 Questions)
1. **Kinematics** (5 MCQs)
   - Displacement & Velocity
   - Acceleration
   - Equations of Motion
   - Relative Motion

2. **Newton's Laws** (5 MCQs)
   - First Law - Inertia
   - Second Law - F=ma
   - Third Law - Action-Reaction
   - Free Body Diagrams

3. **Work, Energy & Power** (5 MCQs)
   - Work Done by Force
   - Kinetic Energy
   - Potential Energy
   - Conservation of Energy
   - Power

### Chemistry (1 Topic - Ready for Expansion)
- Atomic Structure

### Mathematics (1 Topic - Ready for Expansion)
- Trigonometry

---

## 🔧 Customization Guide

### Adding New Questions

Edit the `quizQuestions` object in the JavaScript section:

```javascript
const quizQuestions = {
  'your-topic-id': [
    {
      id: 'unique_id',
      question: 'Your question text?',
      options: ['Option A', 'Option B', 'Option C', 'Option D'],
      correct: 1, // Index of correct answer (0-3)
      concept: 'Specific Concept Name'
    }
  ]
};
```

### Adding New Topics

1. Add to `subjects` object:
```javascript
const subjects = {
  physics: {
    name: 'Physics',
    topics: [
      {
        id: 'new-topic',
        name: 'New Topic Name',
        concepts: ['Concept 1', 'Concept 2']
      }
    ]
  }
};
```

2. Add questions for the topic in `quizQuestions`

### Adding More Students/Teachers

Edit the `users` object:

```javascript
const users = {
  students: [
    { username: 'student11', password: 'pass123', name: 'New Student', grade: '11th' }
  ],
  teachers: [
    { username: 'teacher2', password: 'teach123', name: 'New Teacher' }
  ]
};
```

### Changing Quiz Parameters

```javascript
// In startQuiz() function
const numFollowUp = Math.ceil(followUpQuestions.length); // 100% of wrong questions
const numNew = Math.min(newQuestions.length, followUpQuestions.length); // Equal new questions

// Modify to change ratio, e.g., 70-30 split:
const numFollowUp = Math.ceil(followUpQuestions.length * 0.7);
const numNew = Math.ceil(followUpQuestions.length * 0.3);
```

### Customizing Performance Thresholds

```javascript
// In updateProgress() function
if (topicProgress.weakConcepts[concept].failures >= 3) {
  // Flag for attention after 3 failures (change this number)
  progress[username].attentionRequired.push(concept);
}
```

---

## 🎨 UI Customization

### Change Color Scheme

Find and replace these color codes in the CSS:

- Primary Purple: `#667eea` → Your color
- Secondary Purple: `#764ba2` → Your color
- Success Green: `#28a745` → Your color
- Warning Yellow: `#ffc107` → Your color
- Danger Red: `#dc3545` → Your color

### Responsive Design

The platform is fully responsive and works on:
- ✅ Desktop computers
- ✅ Tablets (iPad, Android tablets)
- ✅ Mobile phones (all screen sizes)

---

## 📈 Scaling & Future Enhancements

### Current Limitations (Prototype)
- ❌ No backend server
- ❌ Data stored locally (browser-specific)
- ❌ No data sync across devices
- ❌ Limited to 10 students + 1 teacher

### Production Recommendations

For scaling beyond prototype:

1. **Backend Database** (Month 2-3)
   - Use Firebase Firestore (Free tier: 50K reads/day)
   - Or MongoDB Atlas (Free tier: 512MB)
   - Enables data sync across devices

2. **Authentication** (Month 2-3)
   - Firebase Authentication
   - JWT tokens for security
   - Password reset functionality

3. **Content Management** (Month 3-4)
   - Admin panel to add questions via UI
   - Bulk upload via CSV/Excel
   - Question categorization by difficulty

4. **Analytics** (Month 4+)
   - Time spent per question
   - Concept mastery over time
   - Predictive performance modeling

5. **Additional Features** (Month 4+)
   - Video explanations for concepts
   - Doubt resolution chat
   - Practice problem generator
   - Mock test series
   - Performance comparison (class average)

---

## 🐛 Troubleshooting

### Progress Not Saving
- **Issue**: Data disappears after browser close
- **Solution**: Don't clear browser cache/cookies
- **Workaround**: Export progress (feature to be added)

### Login Not Working
- **Issue**: Invalid credentials error
- **Solution**: 
  - Check username is lowercase (student1, not Student1)
  - Password is case-sensitive (pass123)
  - Select correct user type

### Questions Not Loading
- **Issue**: "Questions are being prepared" message
- **Solution**: That topic hasn't been added yet - add questions following the customization guide

### Browser Compatibility
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ❌ IE 11 (not supported)

---

## 📝 Development Roadmap

### ✅ Phase 1 - Prototype (Current)
- Basic authentication
- Adaptive quiz logic
- Teacher dashboard
- Sample content for Physics

### 🔄 Phase 2 - Content Expansion (Weeks 2-4)
- Add all Physics topics (20+ topics)
- Add Chemistry topics (15+ topics)
- Add Mathematics topics (15+ topics)
- 500+ total questions

### 🔄 Phase 3 - Backend Integration (Month 2)
- Firebase setup
- User authentication
- Cloud data storage
- Multi-device sync

### 🔄 Phase 4 - Advanced Features (Month 3+)
- Video integration
- Performance analytics
- Spaced repetition algorithm
- Mobile app (React Native)

---

## 🤝 Contributing

To add content or features:

1. Download `index.html`
2. Make your changes
3. Test in browser
4. Share updated file

For major changes:
1. Fork the repository
2. Create feature branch
3. Submit pull request

---

## 📄 License

This is a prototype for educational purposes. Free to use and modify for non-commercial educational institutions.

---

## 📞 Support

For questions or issues:
- Review this README thoroughly
- Check the customization guide
- Test with demo credentials first
- Ensure browser localStorage is enabled

---

## 🎯 Success Metrics to Track

After 1 month of usage, evaluate:

1. **Student Engagement**
   - % of students taking follow-up tests
   - Average attempts per topic
   - Time spent on platform

2. **Learning Effectiveness**
   - Score improvement on follow-up tests
   - Reduction in "attention required" concepts
   - Concept mastery rate

3. **Teacher Usage**
   - Frequency of dashboard checks
   - Response time to attention flags
   - Correlation between intervention & improvement

---

## 🚀 Next Steps

1. **Deploy** the prototype using GitHub Pages
2. **Test** with 2-3 real students
3. **Gather feedback** on user experience
4. **Add content** for 2-3 more topics
5. **Iterate** based on actual usage data
6. **Plan** backend integration for Month 2

---

## 💡 Best Practices for Usage

### For Students
- Take quizzes seriously (no random clicking)
- Actually review concepts before follow-up tests
- Track your own progress over time

### For Teachers
- Check dashboard weekly minimum
- Intervene when "attention required" appears
- Use data to inform lesson planning

### For Admins
- Back up localStorage data monthly (export feature coming)
- Monitor browser compatibility issues
- Plan content addition schedule

---

**Built with ❤️ for JEE aspirants | Ready to deploy in under 5 minutes!**
