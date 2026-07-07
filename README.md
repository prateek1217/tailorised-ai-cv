# CVbyAI - ATS-Optimized Resume Generator

A LangGraph-based AI agent that generates tailored, ATS-optimized resumes by analyzing your CV and job descriptions using the NVIDIA Nemotron LLM.

**New Approach (Option 3):** Generates Word documents (.docx) with your exact resume design, then converts to PDF.

## Features

- 📄 **Smart CV Analysis**: Reads your CV and extracts relevant information
- 🎯 **ATS Optimization**: Tailors your resume to match job descriptions
- 🤖 **NVIDIA Nemotron LLM**: Uses state-of-the-art language model for resume generation
- 📊 **DOCX + PDF Output**: Generates both Word document and PDF
- 🔄 **LangGraph Workflow**: Robust, scalable workflow management
- ✨ **Exact Design Preservation**: Keeps your original resume design perfectly

## Workflow

```
Load CV & JD → Extract & Tailor → Create DOCX → Convert PDF → Save
     ↓              ↓              ↓             ↓           ↓
  cv.md +       Structured      Beautiful   Professional  generated_resumes/
  jd.txt        Resume Data     Word Doc    PDF Format
```

## Setup

### Prerequisites
- Python 3.12+
- `uv` package manager
- NVIDIA API key (from https://build.nvidia.com/)
- LibreOffice (optional, for automatic PDF conversion)

### Installation

1. **Navigate to project**
```bash
cd CVbyAI
```

2. **Create `.env` file** with your API key:
```bash
echo "NVIDIA_API_KEY=your-actual-api-key-here" > .env
```

3. **Install dependencies** using `uv`
```bash
uv sync
```

Get your NVIDIA API key from: https://build.nvidia.com/

## Usage

### 1. Prepare your files

Your files are already set up:
- **`cv.md`** - Your CV (already populated)
- **`jd.txt`** - Job description (update with target job)

### 2. Run the agent

```bash
uv run main.py
```

### 3. Output files

The agent generates in `generated_resumes/`:
- `tailored_resume.docx` - Word document (editable)
- `tailored_resume.pdf` - PDF (ready to submit)

## How It Works

### The LLM-Powered Workflow

1. **Load Files** - Reads your CV and target job description
2. **AI Tailoring** - NVIDIA Nemotron LLM analyzes both and generates resume data:
   - Extracts experience matching job requirements
   - Highlights quantified achievements (e.g., "32x faster", "25% reduction")
   - Prioritizes relevant skills from the job description
   - Creates ATS-optimized bullet points
3. **DOCX Generation** - Builds a professional Word document with:
   - Centered name and contact links
   - Section dividers (black lines)
   - Proper formatting and spacing
   - Dark gray text with blue hyperlinks
4. **PDF Export** - Converts to PDF for easy submission (requires LibreOffice)

### Why This Approach Works

✅ **AI-Powered Customization**: Each resume is tailored specifically for the job  
✅ **Professional Design**: Clean, modern template that's ATS-friendly  
✅ **Quantified Metrics**: LLM includes concrete numbers and results  
✅ **Editable Format**: DOCX is editable if you need to make changes  
✅ **Multiple Formats**: Get both DOCX and PDF ready to use

## Resume Template Structure

The generated resume follows this professional format:

```
CENTERED NAME (18pt, Bold, Dark Gray)
Centered Contact Info (Phone | Email | GitHub | LinkedIn | LeetCode)
─────────────────────────────────────────────────────────────────
PROFESSIONAL SUMMARY
Brief overview tailored to job description
─────────────────────────────────────────────────────────────────
EXPERIENCE
Company Name | Dates
Job Title
• Achievement 1 with metrics
• Achievement 2 with metrics
─────────────────────────────────────────────────────────────────
PROJECTS
Project Name
• Description with technologies
• Key achievement with metrics
─────────────────────────────────────────────────────────────────
SKILLS
Programming Languages: Go, Python, ...
Cloud & Infrastructure: Kubernetes, ...
─────────────────────────────────────────────────────────────────
ACHIEVEMENTS & CERTIFICATIONS
• Achievement 1
• Achievement 2
```

**Design Features:**
- Dark gray text (#1F1F1F) for professional appearance
- Blue hyperlinks (#0066CC) for contact information
- Black divider lines separating each section
- Professional spacing and font sizing (11pt body, 18pt name)
- ATS-friendly structure

## LangGraph Nodes

1. **load_files**: Reads `cv.md` and `jd.txt` from project root
2. **generate_data**: LLM extracts structured resume data tailored to job description, returns JSON
3. **create_docx**: Creates Word document (.docx) with professional formatting and your template structure
4. **convert_pdf**: Converts DOCX to PDF using LibreOffice (or skips if unavailable)

## Configuration

The API is configured in `main.py` using the OpenAI SDK with NVIDIA endpoint:

```python
client = OpenAI(
    base_url="https://integrate.api.nvidia.com/v1",
    api_key=os.getenv("NVIDIA_API_KEY")
)
```

LLM Parameters:
- **Model**: `nvidia/llama-3.3-nemotron-super-49b-v1`
- **Temperature**: 0.6 (balanced creativity)
- **Top P**: 0.95 (nucleus sampling)
- **Max Tokens**: 4096 (detailed responses)

Make sure to set `NVIDIA_API_KEY` in `.env` before running.

## File Descriptions

- **`main.py`** - Main LangGraph agent orchestrating the workflow
- **`cv.md`** - Your CV content in Markdown format
- **`jd.txt`** - Job description to tailor resume for
- **`generated_resumes/`** - Output folder containing generated DOCX and PDF
- **`.env`** - API configuration (keep secret!)

## PDF Conversion

### Automatic (with LibreOffice)
If LibreOffice is installed, the script automatically converts DOCX to PDF.

### Manual (without LibreOffice)
1. Open the DOCX file in Word or LibreOffice
2. File → Export as PDF
3. Save to `generated_resumes/tailored_resume.pdf`

## Troubleshooting

### "CV file not found" or "JD file not found"
- Make sure `cv.md` and `jd.txt` exist in the project root
- Check file spelling and case sensitivity

### API Key Error
- Verify your NVIDIA API key is correct in `.env`
- Check your API quota/credits at build.nvidia.com

### DOCX file looks incorrect
- The DOCX is generated from your extracted data
- Check that the LLM extracted the right information
- You can always edit the DOCX manually

## Next Steps / Enhancements

- [ ] Add multiple JD support (generate multiple tailored resumes)
- [ ] Add resume templates for different industries
- [ ] Implement ATS keyword scoring
- [ ] Add cover letter generation
- [ ] Create web UI for easy file uploads
- [ ] Support for different file formats (DOCX, PDF input)

## License

MIT

## Author

**Prateek Khandelwal** 