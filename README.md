# Homeschool Quiz Trainer

A simple, mobile-friendly static website for practicing mental math, geography, and other educational facts. Perfect for homeschooling!

## Features

- 📱 **Mobile-friendly** - Works great on phones and tablets
- 📝 **Two question types** - Short answer and multiple choice
- 🎲 **Random questions** - 10 random questions per quiz session
- 🧮 **LaTeX support** - Display mathematical equations beautifully
- 🖼️ **Image support** - Show maps, diagrams, or any images
- ✅ **Immediate feedback** - See the correct answer right away
- 📁 **Easy organization** - Quizzes organized by folders/sections
- 🚫 **No backend needed** - Pure static site, host on GitHub Pages
- 🔧 **Simple maintenance** - All quizzes in easy-to-edit markdown files

## Quick Start

### Using the App

1. Open `index.html` in your browser (or visit the GitHub Pages URL)
2. Select a quiz from the available sections
3. Answer 10 random questions one at a time
4. Get immediate feedback on each answer
5. See your final score at the end

### Adding a New Quiz

1. Create a new markdown file in the appropriate `quizzes/` subfolder
2. Use the quiz template below
3. Add the quiz to `quizzes.json`
4. Commit and push (or save if editing locally)

## Quiz Template

### Short Answer Quiz

```markdown
---
title: "Your Quiz Title"
type: "short-answer"
shuffle: true
---

# Question
What is 2 × 3?

## Answer
6

---

# Question
What is 5 + 7?

## Answer
12

---
```

### Multiple Choice Quiz

```markdown
---
title: "Your Quiz Title"
type: "multiple-choice"
shuffle: true
---

# Question
What is the capital of France?

## Options
- Paris *
- London
- Berlin
- Rome

---

# Question
What is 2 + 2?

## Options
- 3
- 4 *
- 5
- 6

---
```

**Note:** The asterisk `*` marks the correct answer in multiple choice questions.

### Quiz with Images

```markdown
---
title: "Country Shapes"
type: "multiple-choice"
shuffle: true
---

# Question
![Country outline](./images/france-outline.svg)

Which country is this?

## Options
- France *
- Germany
- Spain
- Italy

---
```

### Quiz with LaTeX Math

```markdown
---
title: "Fractions"
type: "short-answer"
shuffle: true
---

# Question
What is $\frac{1}{2} + \frac{1}{4}$?

## Answer
3/4

---

# Question
What is $\frac{2}{3} \times 3$?

## Answer
2

---
```

## Folder Structure

```
homeschool-facts-trainer/
├── index.html              # Main app file
├── quizzes.json           # Quiz list and metadata
├── quizzes/
│   ├── times-tables/
│   │   ├── 2-times-table.md
│   │   └── 5-times-table.md
│   ├── mental-math/
│   │   ├── addition-under-20.md
│   │   └── fractions.md
│   └── geography/
│       ├── european-countries.md
│       ├── country-shapes.md
│       └── images/
│           ├── italy-outline.svg
│           └── france-outline.svg
└── README.md
```

## Adding Images

1. Create an `images/` folder in your quiz section (e.g., `quizzes/geography/images/`)
2. Add your image files (PNG, JPG, SVG, etc.)
3. Reference them in your quiz with relative paths:
   ```markdown
   ![Description](./images/your-image.png)
   ```

## Updating quizzes.json

When you add a new quiz file, add an entry to `quizzes.json`:

```json
{
  "quizzes": [
    {
      "section": "Times Tables",
      "title": "3 Times Table",
      "file": "quizzes/times-tables/3-times-table.md"
    }
  ]
}
```

- **section**: The category name (creates headers in the quiz list)
- **title**: The quiz name shown to users
- **file**: Path to the markdown file

## Answer Flexibility

The app accepts multiple answer formats:

- **Whitespace**: "6", " 6 ", "  6" all accepted
- **Case insensitive**: "Paris", "paris", "PARIS" all accepted
- **Numeric formats**: "6", "6.0", "6.00" all accepted
- **Fractions**: "1/2", "0.5" both accepted for the same answer

## Hosting on GitHub Pages

1. Go to your repository settings
2. Navigate to "Pages" section
3. Select the branch (e.g., `main` or `claude/mobile-quiz-app-dVChh`)
4. Select root folder as source
5. Save and wait a few minutes
6. Your site will be available at `https://yourusername.github.io/homeschool-facts-trainer/`

## Local Development

Simply open `index.html` in your browser. No build step or local server required!

If you want to test with a local server (to avoid CORS issues when fetching files):

```bash
# Python 3
python -m http.server 8000

# Then visit http://localhost:8000
```

## Technical Details

- **No dependencies** - Pure HTML, CSS, and JavaScript
- **KaTeX** - For LaTeX rendering (loaded from CDN)
- **Static only** - No backend, database, or authentication
- **Browser storage** - No data is stored; scores are only shown per session
- **Markdown parsing** - Custom lightweight parser for quiz files

## Tips for Creating Quizzes

1. **Pool size**: Create at least 10 questions per quiz (app selects 10 random ones)
2. **More is better**: Add 15-20 questions for more variety
3. **Clear answers**: Make answers unambiguous for short answer questions
4. **Image size**: Keep images under 500KB for fast loading
5. **LaTeX syntax**: Use `$...$` for inline math and `$$...$$` for display math

## Sample Quizzes Included

- **Times Tables**: 2× and 5× multiplication
- **Mental Math**: Addition under 20, simple fractions
- **Geography**: European capitals, country shapes (with placeholder images)

## Customization

### Change Colors

Edit the CSS in `index.html` (around line 20-30):

```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Change Quiz Behavior

Edit the JavaScript in `index.html`:

- Number of questions: Line ~220 (`const numQuestions = Math.min(10, ...)`)
- Answer matching: Lines ~470-510 (`checkAnswer` function)

## Browser Support

Works on all modern browsers:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Contributing

This is a simple static site - feel free to:
- Add more quiz files
- Improve the styling
- Add new question types
- Enhance the markdown parser

## License

Free to use for educational purposes!
