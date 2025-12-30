# AI Understanding Guide: LaTeX Resume Template Structure

## Overview

This is a modular LaTeX resume template system with three files:

- **main.tex** - Template formatting (DO NOT EDIT)
- **data-contact.tex** - Contact information
- **data-resume.tex** - Resume content (PRIMARY EDITING FILE)

---

## Key Rule

**Only edit `data-resume.tex` unless the user explicitly asks for changes to other files.**

---

## How the Template Works

### File Architecture

1. `main.tex` loads and compiles content from the other two files
2. It defines all LaTeX commands and formatting styles
3. It pulls data from `data-contact.tex` and `data-resume.tex` automatically
4. **Never modify main.tex** - it's the engine, not the content

### Data Flow

```
data-contact.tex (contact info)
        ↓
    main.tex (compiles & formats)
        ↓
    PDF Resume Output
        ↑
data-resume.tex (all sections)
```

---

## Understanding data-resume.tex Structure

Each section is a `\newcommand` that contains content. Think of them as containers you fill with text.

### Section Template Pattern

```latex
\newcommand{\sectionNameSection}{
  \section{Display Name}
  % Content goes here
  % Different sections use different LaTeX structures
}
```

### The Six Main Sections

#### 1. **Summary Section** - One paragraph overview

```latex
\newcommand{\summarySection}{
  \section{Summary}
  \begin{itemize}[leftmargin=0.15in, label={}]
    \small{\item{
      [EDIT THIS TEXT - Your professional summary]
    }}
  \end{itemize}
}
```

**Edit**: Replace the text inside `\item{...}`

**Best Practices:**

- **Keep it 1–3 sentences max** - Anything longer wastes resume space
- **Be specific** - Mention your core expertise and years of experience
- **Show impact** - Lead with results, not just job titles

**Example:**

- ❌ Wrong: "Experienced programmer with knowledge of web development"
- ✅ Right: "Full-stack developer with 4+ years building scalable web apps. Specialized in React and FastAPI, with a track record of delivering production-ready solutions."

---

#### 2. **Education Section** - Degree entries with dates

```latex
\newcommand{\educationSection}{
  \section{Education}
  \resumeSubHeadingListStart
    \resumeSubheading
      {School Name}{City, State}
      {Degree Title, Minor if applicable}{Start Date -- End Date}
    % Add more \resumeSubheading entries for additional degrees
  \resumeSubHeadingListEnd
}
```

**Edit**: Replace in each `\resumeSubheading`:

- `{School Name}` → Your school
- `{City, State}` → Location
- `{Degree Info}` → What you earned
- `{Dates}` → When you attended

**To add degrees**: Duplicate the entire `\resumeSubheading` block and fill in new info

---

#### 3. **Experience Section** - Jobs with bullet points

```latex
\newcommand{\experienceSection}{
  \section{Experience}
  \resumeSubHeadingListStart
    \resumeSubheading
      {Job Title}{Start Date -- End Date}
      {Company Name}{City, State}
      \resumeItemListStart
        \resumeItem{Achievement or responsibility}
        \resumeItem{Another achievement}
      \resumeItemListEnd
    % Add more \resumeSubheading blocks for more jobs
  \resumeSubHeadingListEnd
}
```

**Edit**: For each job:

- `{Job Title}` → Your position
- `{Dates}` → When you worked there
- `{Company}` → Employer name
- `{Location}` → City, State
- Each `\resumeItem{...}` → One bullet point (achievement/responsibility)

**To add jobs**: Duplicate the entire `\resumeSubheading` block with its bullet points

**Writing Bullet Points - Critical Rules:**

- **Impact over responsibilities**: Don't just list what you did. Show the real contribution with data and measurable improvements.
- **Use action verbs**: "Built," "Optimized," "Increased," "Reduced," "Implemented"
- **Include numbers when possible**: Percentages, counts, time saved, or revenue impacted

**Examples:**

- ❌ Wrong: "Responsible for maintaining server infrastructure"
- ✅ Right: "Optimized server infrastructure, reducing deployment time by 40% and cutting cloud costs by $12K annually"

- ❌ Wrong: "Fixed bugs in the codebase"
- ✅ Right: "Resolved 25+ critical bugs in production, improving app stability from 94% to 99.2% uptime"

- ❌ Wrong: "Worked on web application development"
- ✅ Right: "Built REST API using FastAPI that processed 100K+ requests daily, enabling real-time data sync across 500+ users"

---

#### 4. **Projects Section** - Project entries with details

```latex
\newcommand{\projectsSection}{
  \section{Projects}
  \resumeSubHeadingListStart
    \resumeProjectHeading
      {\textbf{Project Name} $|$ \emph{Technologies Used}}{Dates}
      \resumeItemListStart
        \resumeItem{What you built or accomplished}
        \resumeItem{Key feature or result}
      \resumeItemListEnd
    % Add more projects as needed
  \resumeSubHeadingListEnd
}
```

**Edit**: For each project:

- `{\textbf{Project Name}` → Your project title (keep `\textbf{}`)
- `\emph{Technologies}` → Tools/languages used (keep `\emph{}`)
- `{Dates}` → When you worked on it
- Each `\resumeItem{...}` → One achievement or feature

**To add projects**: Duplicate the entire `\resumeProjectHeading` block with its bullet points

---

#### 5. **Skills Section** - Technical skills organized by category

```latex
\newcommand{\skillsSection}{
  \section{Technical Skills}
  \begin{itemize}[leftmargin=0.15in, label={}]
    \small{\item{
     \textbf{Languages}{: Java, Python, C/C++, SQL} \\
     \textbf{Frameworks}{: React, Flask, Node.js} \\
     \textbf{Tools}{: Git, Docker, VS Code} \\
     \textbf{Libraries}{: pandas, NumPy}
    }}
  \end{itemize}
}
```

**Edit**:

- Each `\textbf{Category}` stays as-is (the label)
- Replace the comma-separated list after the colon with your skills
- Use `\\` to create line breaks between categories

---

#### 6. **Certifications Section** - Credentials with dates

```latex
\newcommand{\certificationsSection}{
  \section{Certifications}
  \resumeSubHeadingListStart
    \resumeCertItem{\textbf{Certification Name}}{Date}
    \resumeCertItem{\textbf{Another Certification}}{Month Year}
  \resumeSubHeadingListEnd
}
```

**Edit**:

- `{\textbf{Certification Name}` → Your credential (keep `\textbf{}`)
- `{Date}` → When you earned it

**To add certifications**: Add more `\resumeCertItem{}{}` lines

---

## Section Order Control

At the bottom of `data-resume.tex`:

```latex
\newcommand{\resumeContent}{
  \summarySection
  \skillsSection
  \experienceSection
  \educationSection
  \projectsSection
  \certificationsSection
}
```

**You can reorder sections** by rearranging these lines. Example:

```latex
\newcommand{\resumeContent}{
  \summarySection
  \experienceSection      % Moved up
  \projectsSection        % Moved up
  \skillsSection
  \educationSection
  \certificationsSection
}
```

---

## How to Hide Sections

To hide a section without deleting it:

1. Add a `%` at the start of the line
2. Example: `% \summarySection` (now it won't appear)

To show it again, remove the `%`

---

## Important Formatting Rules

### LaTeX Special Characters to Escape

If you need these characters in your text, add a backslash:

- `&` → `\&`
- `%` → `\%`
- `_` → `\_`
- `#` → `\#`

### Text Styling (Optional, already built-in)

- `\textbf{...}` = **Bold** (used for titles)
- `\textit{...}` = _Italic_ (used for subtitles)
- `\emph{...}` = _Emphasis_ (like italic)

### Line Structure

- Each line in `\resumeItem{}` is ONE bullet point
- Add multiple `\resumeItem{}` for multiple bullets
- Don't manually break text within `\resumeItem{}` - it wraps automatically

---

## Common Edits Checklist

- [ ] Update all company/school names
- [ ] Fix all dates (format: `Month Year -- Month Year`)
- [ ] Replace all achievements with your actual work
- [ ] Update technical skills list
- [ ] Add/remove certifications
- [ ] Reorder sections if needed
- [ ] Hide sections you don't want (comment with `%`)

---

## What NOT to Edit

**Never touch these files unless asked:**

- `main.tex` - Contains all LaTeX formatting magic
- The structure of commands in `data-resume.tex` - Only change the content inside `{...}`

**Never change:**

- `\newcommand{\sectionName}{...}` - The command definition
- `\resumeSubheading`, `\resumeItem`, etc. - The command names
- `\section{...}` - The section title formatting

---

## Content Quality Guidelines

### Summary Section Rule

- **1–3 sentences maximum** - Recruiters spend 6 seconds on a resume. Long summaries get skipped.
- Show your best skills, years of experience, and what you deliver
- Avoid generic phrases like "detail-oriented" or "team player"

### Impact Over Responsibilities

- **Never list duties** - That's what job descriptions do
- **Show results with data** - Increased, reduced, optimized, improved
- **Include measurable outcomes** - Percentages, savings, volume handled, time saved
- **Answer: "So what?"** - Each bullet should explain why this work mattered

### Language Mirroring

- **Study the job posting** - Find the specific terms they use (keywords, technologies, skills)
- **Use their language** - If they say "REST API," use "REST API" (not "HTTP interface")
- **Match their focus** - If they emphasize "scalability," highlight your work with large-scale systems
- **Example**: Job posting says "stakeholder communication" → Use that phrase if it applies to your work

---

✅ **DO THIS:**

- Edit text inside curly braces `{...}`
- Add or remove `\resumeItem{...}` lines for bullets
- Duplicate entire entry blocks to add more jobs/projects/degrees
- Reorder sections in `\resumeContent`
- Comment out lines with `%` to hide sections

❌ **DON'T DO THIS:**

- Edit `main.tex` (unless user explicitly asks)
- Change LaTeX command structure or names
- Modify how sections are formatted in `data-contact.tex`
- Remove or rename `\newcommand` definitions
- Change spacing commands like `\vspace`, `\hspace`
