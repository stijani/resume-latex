# Resume LaTeX Compilation Guide

This folder contains LaTeX resume files that can be compiled to PDF format.

## Files
- `saheed-ml.tex` - Main two-column resume template

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
# Compile main resume
tectonic saheed-ml.tex

### Using XeLaTeX
```bash
# Compile main resume
xelatex saheed-ml.tex

# Compile alternative version
cd latex
xelatex saheed-ml.tex
```

## Output
The compilation will generate a PDF file with the same name as the .tex file:
- `saheed-ml.pdf`

## Notes
- The resume uses the `moderncv` class with custom styling
- Fonts used: Avant (sans-serif family)
- The template includes custom colors and two-column layout
- Make sure all required packages are installed (usually handled automatically by modern LaTeX distributions)

## Troubleshooting
If compilation fails:
1. Ensure you have a complete LaTeX distribution installed
2. Check that all required packages are available
3. Try using Tectonic instead of traditional LaTeX engines
4. Check for syntax errors in the .tex file

## Customization
You can modify the .tex files directly to update:
- Personal information
- Work experience
- Skills and certifications
- Colors and formatting