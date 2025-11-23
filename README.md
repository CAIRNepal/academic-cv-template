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
   - **Important**: The `\myname` command automatically bolds your name in all publication entries. See the "Author Name Bolding" section below for details.

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
\industrial{company}{location}{dates}{role}{description}{achievements}
```
- Format: First row - **Company**, Location + Date (right-aligned)
- Second row - Position Title (italics)
- Third row - Description
- Fourth - Achievements (optional, use \item entries)
- `achievements` (6th parameter) should contain `\item` entries - use `{}` if no achievements to list

**Examples:**
```latex
\industrial{Company Name}{Location}{2020--2023}{Software Engineer}{Developed applications.}{%
\item Led team of 5 developers
\item Improved performance by 40%
}
\industrial{Company Name}{Location}{2023--Present}{Senior Developer}{Brief description.}{}
```

### Education
```latex
\education{degree}{university}{location}{dates}{additional}
```
- Format: First row - **Degree** + Date (right-aligned)
- Second row - University, Country
- Third row - Additional info (optional)
- `additional` (5th parameter) is optional - use `{}` if no additional info (dissertation, specialization, etc.)

**Examples:**
```latex
\education{Ph.D. in Computer Science}{University Name}{Country}{2020--2023}{Dissertation: Title}
\education{B.Sc. in Computer Science}{University Name}{Country}{2015--2019}{}
```

### Additional Training
```latex
\training{name}{location}{dates}{additional}
```
- Format: First row - **Training Name** + Date (right-aligned)
- Second row - Location
- Third row - Additional info (optional)
- `additional` (4th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\training{Summer School: Machine Learning}{Location}{2023}{}
\training{Course Name, 3 Credits}{Institution Name, Location}{2022}{Additional details or credits information.}
```

### Awards and Honors
```latex
\award{name}{organization}{dates}{description}
```
- Format: First row - **Award Name** + Date (right-aligned)
- Second row - Organization/Location (optional)
- Third row - Description/Additional info (optional)
- `organization` (2nd parameter) is optional - use `{}` if no organization
- `description` (4th parameter) is optional - use `{}` if no additional description

**Examples:**
```latex
\award{Best Paper Award}{Conference Name}{2023}{}
\award{Scholarship Name}{Organization Name}{2022}{Awarded for outstanding academic performance.}
\award{Award Name}{Organization Name, Location}{2024}{Additional details about the award.}
```

### Presentations
```latex
\presentation{title}{venue}{location}{dates}{additional}
```
- Format: First row - **Title** + Date (right-aligned)
- Second row - Venue, Location
- Third row - Additional info (optional)
- `additional` (5th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\presentation{Presentation Title}{Conference Name}{Location}{2023}{}
\presentation{Research Talk}{Workshop Name}{Location (online)}{2024}{Additional details.}
```

### Invited Talks
```latex
\invitedtalk{title}{event}{dates}{additional}
```
- Format: First row - **Title** + Date (right-aligned)
- Second row - Event Name
- Third row - Additional info (optional)
- `additional` (4th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\invitedtalk{Talk Title}{Event Name}{2023}{}
\invitedtalk{Panel Discussion}{Conference Name}{2024}{Additional details.}
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
- Format: First row - **Student Name** + Year (right-aligned)
- Second row - Project/Thesis Title
- Third row - Type | Level | Status (only shows non-empty fields)
- `type` (3rd parameter) is optional - use `{}` if not needed
- `level` (4th parameter) is optional - use `{}` if not specifying degree level
- `status` (6th parameter) is optional - use `{}` if not needed

**Examples:**
```latex
\supervision{John Doe}{Machine Learning Project}{Research}{Master's}{2023}{Completed}
\supervision{Jane Smith}{Project Title}{Research}{}{2024}{In Progress}
\supervision{Student Name}{Thesis Title}{Thesis}{Bachelor's}{2023}{Completed}
\supervision{Student Name}{Research Project}{}{PhD}{2024}{}
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
\certification{name}{issuer}{dates}{additional}
```
- Format: First row - **Certification Name** + Date (right-aligned)
- Second row - Issuing Organization/Platform
- Third row - Additional info (optional)
- `additional` (4th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\certification{Certification Name}{Issuing Organization}{2023}{}
\certification{Certification Name}{Platform}{2024}{Additional details or credential ID.}
```

### Professional Development
```latex
\professionaldev{activity}{location}{dates}{additional}
```
- Format: First row - **Activity Name** + Date (right-aligned)
- Second row - Location/Institution
- Third row - Additional info (optional)
- `location` (2nd parameter) is optional - use `{}` if no location available
- `additional` (4th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\professionaldev{Training Name}{Institution Name}{2023}{}
\professionaldev{Online Course}{}{2022}{Additional details or completion certificate.}
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

#### Individual Service Entry
```latex
\service{role}{venue}{dates}{additional}
```
- Format: First row - **Role** + Date (right-aligned)
- Second row - Venue/Journal/Conference Name
- Third row - Additional info (optional)
- `additional` (4th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\service{Reviewer}{Journal Name}{2023}{}
\service{Program Committee Member}{Conference Name}{2024}{Additional details.}
```

#### Grouped Services by Role
For grouping multiple venues under the same role (e.g., multiple journal reviews):
```latex
\servicerole{role}
\servicevenue{venue}{date}
\servicevenue{venue}{date}
...
```
- `\servicerole{role}` - Starts a role group, displays role name (indented)
- `\servicevenue{venue}{date}` - Adds a venue entry with bullet, dots, and date (right-aligned)
- Format: Role name on first line, then bulleted list of venues with dates

**Example:**
```latex
\subcvsection{Journal Reviews}
\servicerole{Reviewer}
\servicevenue{eBioMedicine}{2025}
\servicevenue{Computer Communications}{2024}
\servicevenue{Semantic Web}{2024}

\servicerole{Program Committee Member}
\servicevenue{ISWC}{2025}
\servicevenue{KGSWC}{2023}
```

### Editorial Services
```latex
\editorial{role}{venue}{url}{year}{additional}
```
- Format: First row - **Role** + Date (right-aligned)
- Second row - Venue/Journal/Conference Name
- Third row - URL (if provided) and additional info (optional)
- `url` (3rd parameter) is optional - use `{}` if no URL available
- `additional` (5th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\editorial{General Chair}{Conference Name (Year)}{https://example.com}{2024}{}
\editorial{Guest Editor}{Journal Name}{}{2023}{Additional details.}
```

### Workshop Organization
```latex
\workshoporg{title}{location}{dates}{organization}{host}{registrations}{participants}{additional}
```
- Format: First row - **Title** + Date (right-aligned)
- Second row - Location/Venue
- Third row - Organization, Host, Registrations, Participants, and additional info
- Most parameters are optional - use `{}` for any field that is not applicable
- `title` (1st), `location` (2nd), and `dates` (3rd) are typically required

**Example:**
```latex
\workshoporg{Workshop Title}{Location}{2024}{Organization}{Host Org}{210}{70}{Additional details.}
```

### Community Service/Volunteer
```latex
\volunteer{role}{organization}{dates}{additional}
```
- Format: First row - **Role** + Date (right-aligned)
- Second row - Organization Name
- Third row - Additional info (optional)
- `additional` (4th parameter) is optional - use `{}` if no additional info

**Examples:**
```latex
\volunteer{Volunteer}{Organization Name}{2023}{}
\volunteer{Board Member}{Non-profit Organization}{2022--2024}{Additional details.}
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
\course{code}{name}{semesters}{additional}
```
- Format: First row - **Course Code Course Name** + Semesters (right-aligned, if provided)
- Second row - Additional info (optional)
- `semesters` (3rd parameter) is optional - use `{}` if no semester information available
- `additional` (4th parameter) is optional - use `{}` if no additional info
- **Note:** Institution and location should be specified in `\subcvsection{}` to avoid repetition

**Examples:**
```latex
\subcvsection{University Name, Location}
\course{CS101}{Introduction to Programming}{Fall 2023, Spring 2024}{}
\course{CS201}{Data Structures}{}{Additional details (optional).}
```

## Author Name Bolding

The template automatically bolds your name in all publication entries. This feature is implemented using biblatex's name formatting hooks.

### How to Use

1. **Set your name** in `main-cv.tex` using the `\myname` command:
   ```latex
   \myname{LastName}{First\bibnamedelima Name}
   ```

2. **Name Format Guidelines**:
   - **Last Name**: Your family name (e.g., `Smith`, `Chhetri`)
   - **First Name**: Your given name(s)
   - **Spaces in First Name**: Use `\bibnamedelima` for spaces (e.g., `First\bibnamedelima Middle\bibnamedelima Name`)
   - **Multiple First Names**: Separate with `\bibnamedelima` (e.g., `John\bibnamedelima Michael`)

3. **Examples**:
   ```latex
   % Simple name
   \myname{Smith}{John}
   
   % Name with middle name
   \myname{Chhetri}{Tek\bibnamedelima Raj}
   
   % Name with multiple given names
   \myname{Johnson}{Mary\bibnamedelima Elizabeth\bibnamedelima Anne}
   ```

4. **Important Notes**:
   - The name must **exactly match** how it appears in your `publication.bib` file
   - Matching is **case-sensitive** - ensure capitalization matches
   - The name format in your `.bib` file should use standard BibTeX name format: `Last, First` or `First Last`
   - Your name will be automatically bolded in all publication types (articles, proceedings, books, etc.)

5. **Troubleshooting**:
   - If your name is not being bolded, check that:
     - The name in `\myname` exactly matches the name in `publication.bib`
     - The capitalization is correct
     - You've compiled the document with Biber (run `biber main-cv` after the first `pdflatex` run)
     - The bibliography has been properly processed

## Automatic Features

### Last Updated Date

The template **automatically** displays a "Last Updated" date in the footer of your CV, showing when the document was last compiled. **No commands are needed** - it appears automatically on every page.

- **Location**: Appears in the footer, centered at the bottom of each page
- **Format**: "Last Updated: [Date]" in a subtle color
- **Automatic**: The date updates automatically each time you compile the document - no manual intervention required
- **Customization**: 
  - To remove it, comment out or modify the `\fancyfoot[C]` section in `settings.sty` (around line 441)
  - To customize the format or position, modify the footer setup in `settings.sty`
  - The template optionally uses the `datetime2` package for better date formatting if available

## Customization

- **Colors**: Modify color scheme in `settings.sty` (lines 41-43)
  - `SwishLineColour` - Section header line color
  - `MarkerColour` - Icon and link colors
- **Fonts**: Font packages are loaded in `main-cv.tex` (lines 20-31)
  - Uses Cochineal (serif), Cabin (sans-serif), and Inconsolata (monospace)
- **Sections**: Comment/uncomment sections in `main-cv.tex` as needed
- **Photo**: Uncomment photo lines in `main-cv.tex` (lines 73-74) if you want to include a photo
- **Layout**: Adjust margins in `main-cv.tex` (line 43) if needed
- **Last Updated Date**: Comment out `\lastupdated` in `main-cv.tex` if you don't want the date displayed

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

This template is licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0). See [LICENSE](LICENSE) file for details.

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

For more information, visit: https://creativecommons.org/licenses/by/4.0/

## Contact

For questions or support, please contact:
- Email: info@cair-nepal.org
- Organization: CAIR-Nepal

## Acknowledgments

This template is maintained by CAIR-Nepal for the academic community.

