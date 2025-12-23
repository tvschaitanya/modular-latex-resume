# Modular LaTeX Resume Template

A simple resume template with AI help to tailor it to job descriptions.

---

## What Is This?

- A resume template that separates your info into simple text files
- You edit the files, it makes a PDF
- Includes AI prompts to help you write better resume content

## What You Get

```
data-contact.tex          → Your name, email, phone, LinkedIn, GitHub
data-resume.tex           → Your experience, skills, education, projects
main.tex                  → The template (don't touch this)
AI_JOB_FIT_ANALYZER.md    → AI tool to check if you're a good fit for a job
AI_RESUME_OPTIMIZER.md    → AI tool to improve your resume for a job
SampleResume.pdf                → Example of what it looks like
```

---

## How to Use It (3 Steps)

### Step 1: Set Up on Overleaf

1. Go to [Overleaf.com](https://www.overleaf.com) and sign up (free)
2. Click "New Project" → "Upload Project"
3. Upload all your files
4. Done! Overleaf is ready to go

### Step 2: Add Your Info

**Edit `data-contact.tex`:**

```
\newcommand{\MyName}{Your Name}
\newcommand{\MyEmail}{your.email@example.com}
\newcommand{\MyPhone}{+1-555-123-4567}
\newcommand{\MyLinkedIn}{linkedin.com/in/yourprofile}
\newcommand{\MyGitHub}{github.com/yourprofile}
\newcommand{\MyPortfolio}{yourwebsite.com}
```

Leave blank `{}` if you don't want to show it.

**Edit `data-resume.tex`:**
Replace the example content with:

- Your summary
- Education
- Work experience
- Projects
- Skills
- Certifications

Follow the same format as the examples.

### Step 3: Make Your PDF

Click "Recompile" in Overleaf. Download your resume.

---

## Using the AI Tools

### Before You Apply: Check Job Fit

**Use: `AI_JOB_FIT_ANALYZER.md`**

1. Copy the prompt into ChatGPT or Claude
2. Paste in:
   - The job description
   - Your current resume (from `data-resume.tex`)
3. AI tells you:
   - How good a fit you are (0-100%)
   - What you're good at
   - What's missing
   - Should you apply?

### Improve Your Resume: Tailor It to the Job

**Use: `AI_RESUME_OPTIMIZER.md`**

1. Copy the prompt into ChatGPT or Claude
2. Paste in:
   - Your current resume (from `data-resume.tex`)
   - The job fit analysis from Step 1
3. AI rewrites your resume to match the job better
4. Copy the new content and paste it into `data-resume.tex`
5. Recompile in Overleaf
6. Download your updated resume

---

## The Workflow

```
Job Description
     ↓
Use AI_JOB_FIT_ANALYZER → Get honest feedback about fit
     ↓
Use AI_RESUME_OPTIMIZER → Get improved resume content
     ↓
Paste into data-resume.tex
     ↓
Recompile in Overleaf
     ↓
Download PDF
```

---

## Simple Tips

- **Use the AI tools for every job.** Don't send the same resume everywhere.
- **Be honest with the AI.** It works best with real information.
- **Follow the format.** Look at the examples in `data-resume.tex`.
- **Check dates.** Use `June 2020 -- Present` (not `6/2020` or `Jun. 2020`).
- **Add numbers.** "Improved by 40%" is better than "improved."

---

## Common Issues

**Resume won't compile?**

- Check for missing `}` or `{` in your text
- Make sure your dates are formatted like: `June 2020 -- Present`
- Look at the red error message in Overleaf

**PDF looks bad?**

- Your resume might be too long (keep it to 1 page)
- Check that you're using the same format as the examples

**AI prompt not working?**

- Copy the whole file, don't paraphrase
- Paste in a complete job description
- Paste in your full resume

---

## Don't Do This

- ❌ Don't edit `main.tex`
- ❌ Don't make up skills you don't have
- ❌ Don't use the same resume for every job
- ❌ Don't ignore the AI's honest feedback

---

## Need Help?

- Overleaf tutorials: [overleaf.com/learn](https://www.overleaf.com/learn)
- Check examples in `data-resume.tex` for formatting
- Read the instructions in the AI prompt files themselves
