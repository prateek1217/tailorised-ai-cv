# No Template File Needed!

## How the System Works (No Setup Required)

The CVbyAI system generates resumes **from scratch** without needing a template file. Here's the workflow:

### Files You Need (Already Provided)

```
CVbyAI/
├── cv.md                        ← Your CV data (required)
├── jd.txt                       ← Job description (required)
├── main.py                      ← The agent workflow
└── .env                         ← Your NVIDIA API key
```

**That's it! No template file needed.** ✨

### How It Works

1. **Load your data**
   - Reads `cv.md` (your experience, skills, projects)
   - Reads `jd.txt` (target job description)

2. **AI Extraction & Tailoring**
   - NVIDIA Nemotron LLM analyzes both documents
   - Extracts relevant experience for the job
   - Prioritizes matching skills
   - Generates quantified achievements
   - Creates ATS-optimized bullet points

3. **Generate Professional Resume**
   - Creates a DOCX with professional formatting:
     - Centered name (18pt, bold, dark gray)
     - Centered contact info with blue links
     - Black divider lines between sections
     - Professional spacing and layout
     - Dark gray text (#1F1F1F) for body
     - Blue hyperlinks (#0066CC)

4. **Convert to PDF**
   - Automatically converts to PDF (if LibreOffice installed)
   - Or save manually from DOCX

### Resume Template Structure

The generated resume always follows this professional format:

```
    PRATEEK KHANDELWAL (centered, 18pt, bold)
    +91 XXXXXXXXX | email@domain.com | GitHub | LinkedIn | LeetCode (centered, blue links)
    ─────────────────────────────────────────────────────────────
    PROFESSIONAL SUMMARY
    Tailored summary for the job...
    ─────────────────────────────────────────────────────────────
    EXPERIENCE
    Company Name | Date Range
    Job Title
    • Achievement with metrics
    • Achievement with metrics
    ─────────────────────────────────────────────────────────────
    PROJECTS
    Project Name
    • Description
    • Key achievement
    ─────────────────────────────────────────────────────────────
    SKILLS
    Programming Languages: Go, Python, ...
    Cloud & Infrastructure: Kubernetes, ...
    ─────────────────────────────────────────────────────────────
    ACHIEVEMENTS & CERTIFICATIONS
    • Achievement 1
    • Achievement 2
```

### Getting Started

1. **Prepare your data**
   - `cv.md` - Your experience, skills, projects (already populated)
   - `jd.txt` - Target job description (already populated with example)

2. **Set up API**
   - Create `.env` file with:
     ```
     NVIDIA_API_KEY=your-api-key
     ```
   - Get key from: https://build.nvidia.com/

3. **Install dependencies**
   ```bash
   uv sync
   ```

4. **Run the generator**
   ```bash
   uv run main.py
   ```

5. **Find your resume**
   - Output: `generated_resumes/tailored_resume.docx`
   - Output: `generated_resumes/tailored_resume.pdf` (if LibreOffice available)

### Customizing Your Resume Data

To generate a resume for a different job:

1. **Update `jd.txt`**
   - Replace with the new job description
   - Save the file

2. **Update `cv.md`** (optional)
   - Add or modify your experience
   - Add new projects or skills
   - Save the file

3. **Run again**
   ```bash
   uv run main.py
   ```

4. **New resume generated!**
   - Previous version is overwritten
   - Check `generated_resumes/tailored_resume.docx`

### Why This Approach?

✅ **No setup needed** - No template files to manage  
✅ **Consistent design** - Every resume has the same professional format  
✅ **Full customization** - LLM tailors content to each job  
✅ **ATS optimized** - Clean structure works with ATS systems  
✅ **Quantified metrics** - Includes actual numbers and results  
✅ **Fast iteration** - Generate new versions in seconds

That's all! Start generating tailored resumes now. 🚀
