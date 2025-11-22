# Academic CV Template

A professional LaTeX template for academic curriculum vitae, designed for researchers, academics, and scholars.

## Overview

This template provides a comprehensive structure for creating academic CVs with sections for:
- Research interests
- Education
- Research experience
- Teaching experience
- Industrial experience
- Honors and awards
- Teaching courses
- Student supervision
- Entrepreneurship
- Publications (with BibTeX support)
- Presentations
- Invited talks and interviews
- Research grants
- Research projects
- Open source contributions
- Scholarly and professional services
- Community service
- Skills
- Certifications
- Professional development
- References

## Requirements

- LaTeX distribution (TeX Live, MiKTeX, or MacTeX)
- Required packages (automatically loaded):
  - `curve` document class
  - `biblatex` for bibliography management
  - `fontawesome5` for icons
  - And other standard LaTeX packages

## Usage

### Using in Overleaf (Recommended)

1. **Download the template** as a ZIP file from the repository
2. **Create a new project** in Overleaf:
   - Click "New Project" → "Upload Project"
   - Select the ZIP file you downloaded
   - Click "Upload"
3. **Compile** the document:
   - Overleaf will automatically compile when you upload
   - If needed, manually compile by clicking "Recompile"
   - For bibliography, ensure the compiler is set to "pdfLaTeX" and run Biber if needed
4. **Edit your content** directly in Overleaf's editor

### Using Locally

1. **Clone or download** this template

2. **Replace placeholder content** in all `.tex` files with your own information:
   - `main-cv.tex` - Main document and header information
   - `research_interest.tex` - Research interests
   - `education.tex` - Education history
   - `employment.tex` - Research experience
   - `teaching_experience.tex` - Teaching positions
   - `industrial.tex` - Industry experience
   - `honours-and-awards.tex` - Awards and honors
   - `teaching.tex` - Courses taught
   - `supervision.tex` - Student supervision
   - `entrepreneur.tex` - Entrepreneurship activities
   - `publication.bib` - Your publications (BibTeX format)
   - `publications.tex` - Publications section formatting
   - `presentations.tex` - Conference presentations
   - `press.tex` - Invited talks and interviews
   - `grants.tex` - Research grants
   - `research_and_projects.tex` - Research projects
   - `opensource.tex` - Open source contributions
   - `scholar_services.tex` - Professional services
   - `volunteer.tex` - Community service
   - `skills.tex` - Technical skills
   - `certifications.tex` - Certifications
   - `professional_development.tex` - Professional development
   - `referee.tex` - References

3. **Update your name** in `main-cv.tex`:
   - Change `\myname{LastName}{First\bibnamedelima Name}` to match your name as it appears in your publications
   - Update the header with your contact information (name, email, website, etc.)

4. **Add your publications** to `publication.bib` in BibTeX format. The template supports:
   - Journal articles
   - Conference proceedings
   - Posters
   - Books and chapters
   - Manuscripts under review
   - Preprints
   - Books in progress
   - Drafts in progress

5. **Customize sections** in `main-cv.tex`:
   - Comment/uncomment sections you don't need using `% \makecvsection{section_name}`
   - Reorder sections by moving the `\makecvsection{}` commands

6. **Compile** the document:
   ```bash
   pdflatex main-cv.tex
   biber main-cv
   pdflatex main-cv.tex
   pdflatex main-cv.tex
   ```
   Or use your preferred LaTeX editor (TeXShop, TeXworks, etc.)

**Note:** For Overleaf users, simply upload the project as a ZIP file and compile directly in the browser. Overleaf handles the compilation process automatically.

## Template Structure

The template uses `cvsection` environments and commands (aliases for the underlying `rubric` commands from the curve class):

- `\begin{cvsection}{Section Title}...\end{cvsection}` - For section content
- `\makecvsection{filename}` - To include a section file
- `\makecvsectionhead{Title}` - For custom section headers
- `\subcvsection{Subsection Title}` - For subsections within a section

## Standardized Commands

The template provides standardized commands for consistent formatting across all sections. **You must use these commands instead of manually formatting entries.**

**Important Restrictions:**
- **Do NOT use raw `\entry*[]` commands directly** - The template prevents direct use of `\entry*[]` to ensure consistent formatting
- **Always use the provided template commands** (e.g., `\employment`, `\education`, `\presentation`, etc.)
- If you need a custom format, modify the command definitions in `settings.sty` rather than using raw `\entry*[]`

**Important Note on Empty Parameters:** Many commands have optional parameters. When a parameter is not applicable, use `{}` (empty braces) to indicate the field is empty. For example, if an award has no additional description, use `\award{Name}{}{YYYY}` where the second parameter is empty. All template files include comments explaining which parameters are optional.

### Employment/Research Experience
```latex
\employment{institution}{location}{dates}{role}{description}{achievements}
```
- `achievements` (6th parameter) should contain `\item` entries - use `{}` if no achievements to list

**Examples:**
```latex
\employment{MIT}{USA}{2020--2023}{Postdoctoral Associate}{Research on AI.}{%
\item Published 5 papers
\item Supervised 3 students
}
\employment{University Name}{Location}{2023--Present}{Researcher}{Brief description.}{}
```

### Teaching Experience
```latex
\teachingexp{institution}{location}{dates}{role}{description}{achievements}
```
- `achievements` (6th parameter) should contain `\item` entries - use `{}` if no achievements to list

**Example:**
```latex
\teachingexp{University Name}{Location}{2020--2023}{Instructor}{Taught courses.}{%
\item Mentored 50+ students
\item Improved course ratings
}
```

### Industrial Experience
```latex
\industrial{company}{location}{role}{dates}{description}
```

### Education
```latex
\education{degree}{university}{location}{dates}{additional}
```
- `additional` (5th parameter) is optional - use `{}` if no additional info (dissertation, specialization, etc.)

**Examples:**
```latex
\education{Ph.D. in Computer Science}{University Name}{Country}{2020--2023}{Dissertation: Title}
\education{B.Sc. in Computer Science}{University Name}{Country}{2015--2019}{}
```

### Additional Training
```latex
\training{name}{location}{dates}
```

### Awards and Honors
```latex
\award{name}{description}{dates}
```
- `description` (2nd parameter) is optional - use `{}` if no additional description needed

**Examples:**
```latex
\award{\textbf{Best Paper Award}, Conference Name}{}{2023}
\award{\textbf{Scholarship Name}}{Awarded for outstanding academic performance.}{2022}
```

### Presentations
```latex
\presentation{title}{venue}{location}{dates}
```

### Invited Talks
```latex
\invitedtalk{title}{event}{dates}
```

### Research Grants
```latex
\grant{title}{agency}{role}{status}{dates}
```
- `status` (4th parameter) is optional - use `{}` if no status info
- `dates` (5th parameter) is optional - use `{}` if no date range available

**Examples:**
```latex
\grant{Project Title}{NSF}{Principal Investigator}{Active}{2023--2026}
\grant{Project Title}{Funding Agency}{Co-Investigator}{Draft in progress}{}
```

### Research Projects
```latex
\researchproject{title}{status}
```
- `status` (2nd parameter) is optional - use `{}` if no status, or use "Active", "Completed", etc.

**Examples:**
```latex
\researchproject{Project Name -- Description}{Active}
\researchproject{Project Name}{}
```

### Student Supervision
```latex
\supervision{student}{project}{type}{level}{year}{status}
```
- `level` (4th parameter) is optional - use `{}` if not specifying degree level
- `status` (6th parameter) is optional - use `{}` if not needed
- All arguments are required - use placeholder text if a field is not applicable
- **Note:** Do NOT use within `\begin{itemize}...\end{itemize}` - the command handles formatting automatically

**Examples:**
```latex
\supervision{John Doe}{Machine Learning Project}{Research}{Master's}{2023}{Completed}
\supervision{Jane Smith}{Project Title}{Research}{}{2024}{}
\supervision{Student Name}{Thesis Title}{Thesis}{Bachelor's}{2023}{Completed}
```

### Entrepreneurship
```latex
\entrepreneurship{name}{description}{role}{focus}{website}
```
- `focus` (4th parameter) is optional - use `{}` if no focus areas
- `website` (5th parameter) is optional - use `{}` if no website

**Examples:**
```latex
\entrepreneurship{Company Name}{Description.}{Founder \& CEO}{AI Research}{https://example.com}
\entrepreneurship{Startup Name}{Brief description.}{Co-Founder}{}{}
```

### Certifications
```latex
\certification{name}{issuer}{dates}
```

### Professional Development
```latex
\professionaldev{activity}{location}{dates}
```
- `location` (2nd parameter) is optional - use `{}` if no location available

**Examples:**
```latex
\professionaldev{Training Name}{Institution Name}{2023}
\professionaldev{Online Course}{}{2022}
```

### Skills
```latex
\skillcategory{category}{skills}
```
- `skills` should be comma-separated

**Example:**
```latex
\skillcategory{Programming Languages}{Python, Java, C++}
```

### Professional Services
```latex
\service{role}{venue}{dates}
```

**Example:**
```latex
\service{Reviewer}{Journal Name}{2023}
```

### Editorial Services
```latex
\editorial{role}{venue}{url}{year}
```
- `url` (3rd parameter) is optional - use `{}` if no URL available

**Examples:**
```latex
\editorial{General Chair}{Conference Name (Year)}{https://example.com}{2024}
\editorial{Guest Editor}{Journal Name}{}{2023}
```

### Workshop Organization
```latex
\workshoporg{eventtype}{daterange}{title}{organization}{host}{registrations}{participants}{year}
```
- Most parameters are optional - use `{}` for any field that is not applicable
- Only `eventtype` (1st) and `year` (8th) are typically required

**Example:**
```latex
\workshoporg{Workshop}{Feb 1--2}{Workshop Title}{Organization}{Host Org}{210}{70}{2024}
```

### Community Service/Volunteer
```latex
\volunteer{role}{organization}{dates}
```

### Open Source Projects
```latex
\opensource{name}{project}{url}
```
- `project` (2nd parameter) is optional - use `{}` if no project link
- `url` (3rd parameter) is optional - use `{}` if no repository URL

**Examples:**
```latex
\opensource{Project Name}{https://example.com}{https://github.com/user/repo}
\opensource{Project Name}{}{https://github.com/user/repo}
```

### References
```latex
\reference{name}{title}{institution}{email}
```

### Courses Taught
```latex
\course{code}{name}{institution}{location}{semesters}
```
- `semesters` (5th parameter) is optional - use `{}` if no semester information available

**Examples:**
```latex
\course{CS101}{Introduction to Programming}{University Name}{Location}{Fall 2023, Spring 2024}
\course{CS201}{Data Structures}{University Name}{Location}{}
```

## Customization

- **Colors**: Modify color scheme in `settings.sty` (lines 41-43)
  - `SwishLineColour` - Section header line color
  - `MarkerColour` - Icon and link colors
- **Fonts**: Font packages are loaded in `main-cv.tex` (lines 20-31)
  - Uses Cochineal (serif), Cabin (sans-serif), and Inconsolata (monospace)
- **Sections**: Comment/uncomment sections in `main-cv.tex` as needed
- **Photo**: Uncomment photo lines in `main-cv.tex` (lines 73-74) if you want to include a photo
- **Layout**: Adjust margins in `main-cv.tex` (line 43) if needed

## File Structure

```
template_academic_cv/
├── main-cv.tex              # Main document file
├── settings.sty             # Style definitions and customizations
├── publication.bib          # Bibliography file (BibTeX format)
├── research_interest.tex    # Research interests section
├── education.tex           # Education section
├── employment.tex           # Research experience section
├── teaching_experience.tex  # Teaching experience section
├── industrial.tex           # Industrial experience section
├── honours-and-awards.tex   # Honors and awards section
├── teaching.tex             # Courses taught section
├── supervision.tex          # Student supervision section
├── entrepreneur.tex         # Entrepreneurship section
├── publications.tex        # Publications section (uses BibTeX)
├── presentations.tex        # Presentations section
├── press.tex                # Invited talks and interviews section
├── grants.tex               # Research grants section
├── research_and_projects.tex # Research projects section
├── opensource.tex           # Open source contributions section
├── scholar_services.tex     # Professional services section
├── volunteer.tex            # Community service section
├── skills.tex               # Technical skills section
├── certifications.tex       # Certifications section
├── professional_development.tex # Professional development section
├── referee.tex              # References section
├── referee-full.tex         # Alternative reference format (optional)
├── README.md                # This file
└── LICENSE                  # MIT License
```

## License

This template is licensed under the MIT License. See [LICENSE](LICENSE) file for details.

## Contact

For questions or support, please contact:
- Email: info@cair-nepal.org
- Organization: CAIR-Nepal

## Acknowledgments

This template is maintained by CAIR-Nepal for the academic community.

