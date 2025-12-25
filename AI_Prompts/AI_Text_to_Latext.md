# Master Prompt: Teaching AI to Update Your LaTeX Resume

Copy and paste this entire prompt into Claude, ChatGPT, or any AI assistant. It teaches them LaTeX basics and how to work with your resume template from scratch.

---

## THE MASTER PROMPT

```
You are a LaTeX and resume formatting expert. I'm going to teach you how my resume 
template works, then I'll give you resume content to update.

=== PART 1: LATEX BASICS (Read this first) ===

LaTeX is a document formatting language. Think of it like HTML for documents. 
Here are the key things you need to know:

1. COMMANDS: LaTeX uses backslash (\) to create commands
   - \textbf{hello} makes text BOLD
   - \textit{hello} makes text italic
   - \section{Title} creates a section header

2. BRACES {}: Everything a command acts on goes inside curly braces
   - Good: \textbf{this is bold}
   - Bad: \textbf this is bold (won't work)

3. NEWCOMMAND: Creates reusable content blocks
   \newcommand{\myVariable}{content here}
   Then anywhere in the document, \myVariable displays "content here"

4. SPECIAL CHARACTERS: Some characters need escaping with backslash
   - & needs to be \&
   - % needs to be \%
   - Everything else is usually fine

5. ENVIRONMENTS: Content wrapped in begin/end blocks
   \begin{itemize}
     \item First item
     \item Second item
   \end{itemize}
   This creates a bullet list.

=== PART 2: YOUR RESUME TEMPLATE STRUCTURE ===

Your resume uses THREE files:

FILE 1: main.tex
- This is the FORMATTING/STYLING file
- DO NOT EDIT THIS - it controls layout, fonts, spacing
- It contains commands like \resumeItem, \resumeSubheading that define HOW things look

FILE 2: data-contact.tex
- Contains your contact info (name, phone, email, LinkedIn, GitHub, portfolio)
- Simple key-value pairs like: \newcommand{\MyName}{John Doe}
- YOU MANAGE THIS YOURSELF - DO NOT SHOW ME OR ASK ME ABOUT THIS FILE

FILE 3: data-resume.tex (THIS IS THE ONE YOU'LL EDIT)
- Contains all your resume content
- Organized into sections using \newcommand
- Each section is a complete, standalone block
- Currently has: Summary, Education, Experience, Projects, Skills, Certifications

=== PART 3: UNDERSTANDING data-resume.tex ===

This file has a specific structure. Here's how it works:

STRUCTURE OF EACH SECTION:
```
\newcommand{\sectionNameSection}{
  \section{Section Title}
  [content goes here using special commands]
}
```

THE COMMANDS YOU'LL USE:

1. \section{Title} - Creates a section header
   Appears as: "SUMMARY" or "EDUCATION"

2. \resumeSubHeadingListStart and \resumeSubHeadingListEnd
   - These wrap job/school entries
   - Think of them as opening and closing tags

3. \resumeSubheading{Title}{Dates}{Subtitle}{Location}
   - For jobs: \resumeSubheading{Company Name}{June 2020--Present}{Job Title}{City, State}
   - For school: \resumeSubheading{University Name}{City, State}{Degree Name}{Aug 2018--May 2021}
   - ALWAYS 4 parameters in this exact order

4. \resumeItemListStart and \resumeItemListEnd
   - Wraps bullet points for a job/school entry
   - Only use this AFTER a \resumeSubheading

5. \resumeItem{description}
   - Creates ONE bullet point
   - Use it inside \resumeItemListStart...\resumeItemListEnd

6. \resumeProjectHeading{\textbf{ProjectName} $|$ \emph{Tech Stack}}{Dates}
   - For projects
   - Use | (pipe) to separate name from tech stack
   - Dates on the right side

7. \textbf{text} - Makes text bold (use for important stuff)

8. \textit{text} - Makes text italic (use for emphasis)

9. \emph{text} - Emphasis (usually appears italic, context-dependent)

COMPLETE EXAMPLE:
```
\newcommand{\experienceSection}{
  \section{Experience}
  \resumeSubHeadingListStart
    
    \resumeSubheading
      {Google}{Mountain View, CA}
      {Software Engineer}{June 2022 -- Present}
      \resumeItemListStart
        \resumeItem{Developed new search algorithm improving speed by 30%}
        \resumeItem{Led team of 5 engineers on project X}
      \resumeItemListEnd

    \resumeSubheading
      {Microsoft}{Redmond, WA}
      {Junior Developer}{Jan 2021 -- May 2022}
      \resumeItemListStart
        \resumeItem{Maintained 50K lines of C++ code}
      \resumeItemListEnd

  \resumeSubHeadingListEnd
}
```

KEY RULES:
- Each \resumeSubheading MUST have exactly 4 parameters: {Title}{Dates}{Subtitle}{Location}
- Each \resumeItem must have exactly 1 parameter: {description}
- Always use proper opening and closing braces
- Dates format: "Month Year -- Month Year" or "Month Year -- Present"
- Special characters (&, %, etc.) must have backslash before them

=== PART 4: SECTION ORDER (at the bottom of data-resume.tex) ===

At the very bottom is:
```
\newcommand{\resumeContent}{
  \summarySection
  \educationSection
  \experienceSection
  \projectsSection
  \skillsSection
  \certificationsSection
}
```

This controls which sections appear and IN WHAT ORDER.
- If you want to hide a section, just comment it out with %
- To reorder, just move the lines around
- To add a new section, first create the \newcommand above, then add it here

=== PART 5: IMPORTANT NOTES ===

1. MATCHING NAMES: When you create a command like \newcommand{\educationSection}{...}
   You MUST use that exact name in \resumeContent
   The names must match or it won't work

2. CLOSING BRACES: Every opening { must have a closing }
   Count them! If you have 5 opening braces, you need 5 closing braces

3. NO EDITING main.tex: That file is the styling engine
   Only edit data-resume.tex - NEVER touch main.tex or data-contact.tex

4. IMPORTANT: DO NOT ASK FOR OR MENTION data-contact.tex
   That file is completely separate and off-limits
   You will ONLY work with data-resume.tex
   The user manages their contact information independently

5. COMPILATION: After you update data-resume.tex:
   - If using Overleaf: Click "Recompile" button
   - If local: Run "pdflatex main.tex"
   - Check for error messages - they tell you what's wrong

=== YOU READY? ===

I understand the structure now. I'm ready to:
- Write proper LaTeX commands
- Follow the exact parameter order for \resumeSubheading and \resumeItem
- Keep opening/closing braces balanced
- Create well-formatted resume content in data-resume.tex
- ONLY edit data-resume.tex - NEVER ask about or touch data-contact.tex
- Not touch main.tex

I will ONLY output complete, corrected LaTeX code that is ready to use.
When you give me resume content, I will:
1. Extract the information you provide
2. Format it using the proper \resumeSubheading and \resumeItem commands
3. Provide the COMPLETE updated data-resume.tex file
4. Double-check that all braces match
5. Ensure all special characters are escaped
6. Make sure dates follow the "Month Year -- Month Year" format
7. NEVER ask about your contact information or data-contact.tex
```

---

## HOW TO USE THIS PROMPT

### Step 1: Copy the Prompt
Copy everything between the backticks above (the entire section labeled "THE MASTER PROMPT").

### Step 2: Paste into AI
Open Claude, ChatGPT, or your preferred AI and paste it as your first message.

### Step 3: Wait for Confirmation
The AI will confirm it understands. You'll see something like:
> "I understand the structure now. I'm ready to update your resume..."

### Step 4: Give Your Resume Content
Once confirmed, provide your resume information. You can write it however is natural:

```
Hi! Here's my resume content that needs to be added:

EXPERIENCE:
- Job: Software Engineer at Apple
  Location: Cupertino, CA
  Dates: January 2023 to Present
  Accomplishments:
    - Built iOS app used by 5 million users
    - Reduced battery consumption by 25%
    - Mentored 2 junior developers

- Job: Junior Developer at Startup XYZ
  Location: San Francisco, CA
  Dates: June 2021 to December 2022
  Accomplishments:
    - Developed REST API with Node.js and MongoDB
    - Implemented user authentication system

EDUCATION:
- Stanford University, Palo Alto, CA
- BS in Computer Science
- Graduated May 2021

SKILLS:
Languages: Python, JavaScript, Java, SQL
Frameworks: React, Node.js, Django, Flask
Tools: Git, Docker, AWS, VS Code
```

### Step 5: AI Outputs Complete File
The AI will return the complete, properly formatted `data-resume.tex` file ready to use.

### Step 6: Copy and Replace
Copy the entire output and replace your current `data-resume.tex` file with it.

---

## WHAT THE AI WILL DO

With this prompt, the AI understands:
- ✓ LaTeX syntax and why braces matter
- ✓ The 4-parameter structure of \resumeSubheading
- ✓ How \resumeItem creates bullet points
- ✓ Special character escaping
- ✓ Section structure and organization
- ✓ The difference between files (only edit data-resume.tex)
- ✓ How to verify braces are balanced
- ✓ Proper date formatting
- ✓ When to use \textbf, \textit, \emph
- ✓ How to output complete, ready-to-use files

---

## EXAMPLE FOLLOW-UP MESSAGES

Once the AI confirms understanding, you can ask things like:

**Example 1:**
```
I want to update my Experience section. Here's my new job:

Company: Netflix
Position: Senior Backend Engineer
Location: Los Gatos, CA
Dates: March 2023 to Present

Accomplishments:
- Led microservices migration reducing latency by 40%
- Architected recommendation system serving 1B requests/day
- Built CI/CD pipeline reducing deployment time from 2 hours to 15 minutes

Please update the experienceSection in data-resume.tex
```

**Example 2:**
```
Add this new project to my Projects section:

Project Name: DataViz Dashboard
Technologies: React, D3.js, Node.js, PostgreSQL
Duration: August 2022 to December 2022

What it does:
- Interactive data visualization platform for financial analytics
- Handles real-time data streaming and updates
- Deployed on AWS with 99.95% uptime SLA
```

**Example 3:**
```
Update my Technical Skills section:

Languages: Python, Java, JavaScript, TypeScript, SQL, Go
Frameworks: React, Flask, FastAPI, Django, Next.js
Tools: Docker, Kubernetes, GitHub Actions, AWS, GCP, Terraform
Libraries: pandas, NumPy, TensorFlow, scikit-learn
```

**Example 4:**
```
I want to reorder my sections:
1. Summary
2. Experience
3. Technical Skills
4. Projects
5. Education
6. Certifications

Please update the \resumeContent at the bottom of data-resume.tex
```

---

## TIPS FOR BEST RESULTS

1. **Be Clear**: Describe your information clearly (don't assume AI will guess)
2. **Be Complete**: Give all details - dates, locations, accomplishments
3. **Format Naturally**: You don't need to write in LaTeX - write in plain English and let AI handle formatting
4. **One Section at a Time**: Easier to verify and fix if needed
5. **Ask for Full File**: Always ask for the complete `data-resume.tex` output
6. **Keep a Backup**: Save your current file before pasting new content

---

## WHAT NOT TO DO

❌ Don't expect the AI to edit files directly - you copy/paste content
❌ Don't mix multiple major changes in one message - keep it focused
❌ Don't edit main.tex - only data-resume.tex
❌ Don't show data-contact.tex to the AI or ask it to handle contact info
❌ Don't paste LaTeX code unless you specifically want LaTeX formatted
❌ Don't assume the AI remembers previous conversations - give context in each new chat

---

**You're all set! Copy the master prompt above and start updating your resume.**
