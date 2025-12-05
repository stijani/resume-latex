# Resume LaTeX Compilation Guide

This folder contains LaTeX resume files that can be compiled to PDF format.

## Files
- `saheed-ml.tex` - **Main modular resume** (recommended for easy editing)
- `saheed-single-module-ml.tex` - Single-file backup version
- `src/` - **Modular components directory**
  - `preamble.tex` - Document setup, packages, and formatting
  - `summary.tex` - Professional summary
  - `experience-*.tex` - Individual job experience sections
  - `skills.tex` - Technical skills and tools
  - `certifications.tex` - Professional certifications
  - `education.tex` - Academic qualifications
  - `publications.tex` - Research publications

## Modular Structure Benefits
- ✅ **Easy maintenance** - Update individual sections without touching others
- ✅ **Version control friendly** - Track changes to specific sections
- ✅ **Customizable** - Include/exclude sections for different versions
- ✅ **Collaborative** - Multiple people can work on different sections
- ✅ **Reusable** - Use components in other documents

## Prerequisites
You need a LaTeX distribution installed on your system. We recommend:
- **Tectonic** (recommended for modern LaTeX compilation)
- **XeLaTeX** (part of most LaTeX distributions)
- **TeXLive** or **MacTeX** (full LaTeX distributions)

## Installation

### Option 1: Tectonic (Recommended)
```bash
# Install via Homebrew (macOS)
brew install tectonic

# Or install via Cargo (if you have Rust)
cargo install tectonic
```

### Option 2: MacTeX (macOS)
```bash
# Install via Homebrew
brew install --cask mactex
```

## Compilation Commands

### Using Tectonic (Recommended)
```bash
# Compile main modular resume
tectonic saheed-ml.tex

# Compile single-file version
tectonic saheed-single-module-ml.tex
```

### Using XeLaTeX
```bash
# Compile main modular resume
xelatex saheed-ml.tex

# Compile single-file version
xelatex saheed-single-module-ml.tex
```

## Output
The compilation will generate PDF files with the same name as the .tex files:
- `saheed-ml.pdf` - From the modular version
- `saheed-single-module-ml.pdf` - From the single-file version

Both versions produce identical output with the same content and formatting.

## Converting to Word Format

If you need a Word document version of your resume:

### Method 1: PDF to Word (Recommended)
```bash
# Activate environment
conda activate latex-thesis

# Compile main resume to PDF
tectonic saheed-ml.tex

# Install pdf2docx if not already installed
pip install pdf2docx

# Convert PDF to Word
python -c "
from pdf2docx import Converter
cv = Converter('saheed-ml.pdf')
cv.convert('saheed-ml.docx')
cv.close()
print('Conversion complete: saheed-ml.docx created')
"
```

This method preserves the two-column layout and formatting much better than direct LaTeX to Word conversion.

## Quick Start Guide
1. **Activate environment**: `conda activate latex-thesis`
2. **Edit content**: Modify files in `src/` directory
3. **Compile**: `tectonic saheed-ml.tex`  
4. **Output**: `saheed-ml.pdf` ready for use

## Version Control Best Practices
- Commit changes to individual `src/*.tex` files separately
- Use descriptive commit messages for each section update
- The modular structure makes diffs and reviews much cleaner
- Consider branching for major content restructuring

## Architecture Details

### Modular Design
The resume follows a modular architecture where:
- `saheed-ml.tex` serves as the main orchestrator
- `src/preamble.tex` contains all LaTeX setup and configuration
- Individual content sections are separated into logical files
- All components are assembled via `\input{}` commands

### Technical Specifications
- **Document class**: `moderncv` with banking theme
- **Layout**: Two-column using `paracol` package (62%/35% width ratio)
- **Fonts**: Avant (sans-serif family)
- **Typography**: Microtype for improved text rendering
- **Colors**: Custom color scheme (lightgrey, dategrey, companygrey)
- **Spacing**: Optimized with enumitem package (3pt item separation)

### Content Sections
- Professional summary highlighting ML/AI expertise
- Current role at Disco.ac with audio processing achievements
- Previous experience at Powercor, Summit Innovation, Elenium, NBN
- Comprehensive technical skills across ML frameworks
- AWS certifications and academic qualifications
- Research publications in federated learning

## Troubleshooting

### Common Issues
1. **Environment not activated**
   ```bash
   conda activate latex-thesis
   ```

2. **Missing packages**
   - Ensure you have a complete LaTeX distribution
   - Tectonic automatically downloads required packages

3. **Character encoding warnings**
   - Warnings about missing characters (📍, –) are normal
   - They don't affect PDF generation

4. **Compilation errors**
   - Check syntax in modified `.tex` files
   - Ensure all `\begin{}` have matching `\end{}`
   - Verify file paths in `\input{}` commands

5. **Modular version issues**
   - Ensure all files in `src/` directory exist
   - Check that `\input{src/filename}` paths are correct
   - Try compiling single-file version to isolate issues

### Debug Steps
```bash
# Test individual components
tectonic --print saheed-ml.tex

# Fall back to single-file version
tectonic saheed-single-module-ml.tex

# Check file structure
ls -la src/
```

## Customization

### Modular Version (Recommended)
Edit individual component files in the `src/` directory:
- **Personal info**: Edit `src/preamble.tex` (name, contact details)
- **Summary**: Edit `src/summary.tex`
- **Work experience**: Edit individual `src/experience-*.tex` files
- **Skills**: Edit `src/skills.tex`
- **Education**: Edit `src/education.tex`
- **Publications**: Edit `src/publications.tex`
- **Certifications**: Edit `src/certifications.tex`
- **Styling/colors**: Edit `src/preamble.tex`

### Single-File Version
Modify `saheed-single-module-ml.tex` directly for all changes.

## Adding New Experience
To add a new job experience to the modular version:
1. Create a new file: `src/experience-newcompany.tex`
2. Add the experience content following the existing format
3. Include it in `saheed-ml.tex` with: `\input{src/experience-newcompany}`

## Environment Setup
Ensure you have the `latex-thesis` conda environment activated:
```bash
conda activate latex-thesis
```