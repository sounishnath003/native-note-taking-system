# Native Text-Based Note Taking System

A powerful, lightweight note-taking system that generates PDF and HTML documents natively from plain text files using Pandoc and LaTeX.

## Overview

This project provides a streamlined workflow for creating professional-looking notes and presentations from simple text files. It automatically compiles individual note files into comprehensive PDF documents and HTML presentations, making it perfect for students, researchers, and professionals who prefer text-based note-taking.

## Features

- **Native Text Input**: Write notes in simple markdown/text format
- **Automatic Compilation**: Generate PDF and HTML outputs with a single command
- **Structure Discovery**: Auto-detects `MS*` and `mod*` folders, or processes any folder of `.md`/`.txt`
- **Modular Organization**: Organize notes by year and module
- **Professional Output**: Clean, readable PDFs with table of contents
- **HTML Presentations**: Generate HTML slides for web viewing
- **Batch Processing**: Compile all notes or specific modules at once
- **Custom Styling**: LaTeX and HTML templates live next to the script

## Project Structure

```
notes-exp/
├── README.md              # This file
├── notes                  # Main compilation script (run this)
├── about.md               # Intro content automatically included in PDFs
├── fonts.tex              # LaTeX font configuration (used by script)
├── slidy.html             # HTML presentation template (used by script)
└── MS1/                   # Year 1 notes
    ├── MS1.pdf            # Compiled year PDF
    └── mod1/              # Module 1 (folder name is arbitrary)
        ├── Any Name.txt   # Any .txt/.md filenames are supported
        ├── Another.md
        ├── mod1.pdf       # Compiled module PDF
        └── mod1.html      # Compiled module HTML
```

## Dependencies & Software Requirements

### Core Dependencies

1. **Pandoc** (Required)
   - Universal document converter
   - Installation:
     ```bash
     # macOS
     brew install pandoc
     
     # Ubuntu/Debian
     sudo apt-get install pandoc
     
     # Windows
     choco install pandoc
     ```

2. **LuaLaTeX** (Required for PDF generation)
   - LaTeX engine with Unicode support
   - Installation:
     ```bash
     # macOS
     brew install --cask mactex
     
     # Ubuntu/Debian
     sudo apt-get install texlive-luatex texlive-latex-extra
     
     # Windows
     choco install mactex
     ```

3. **Ghostscript** (Optional, for PDF merging)
   - Used to merge multiple PDFs into single documents
   - Installation:
     ```bash
     # macOS
     brew install ghostscript
     
     # Ubuntu/Debian
     sudo apt-get install ghostscript
     
     # Windows
     choco install ghostscript
     ```

### Additional Tools

4. **Bash** (Required)
   - Shell environment (usually pre-installed on Unix systems)

### LaTeX Packages (Auto-installed with LuaLaTeX)

The following packages are used and will be automatically installed:
- `fontspec` - Font selection for XeLaTeX and LuaLaTeX
- `geometry` - Page layout control
- `hyperref` - Hyperlinks in PDF
- `tocloft` - Table of contents formatting

## Installation

1. **Clone or download this repository**
   ```bash
   git clone <repository-url>
   cd notes-exp
   ```

2. **Install dependencies** (see above)

3. **Make the script executable**
   ```bash
   chmod +x notes
   ```

4. (Optional) Add the script to your PATH or create an alias

## Usage

### Usage

The script takes a work directory and an optional subfolder. It auto-discovers `MS*` and `mod*` directories and compiles all `.md`/`.txt` files it finds (no naming convention required).

```bash
# Compile everything under a work directory
./notes /path/to/notes

# Compile a specific MS folder (e.g., MS1)
./notes /path/to/notes MS1

# Compile a specific module folder (e.g., MS1/mod1)
./notes /path/to/notes MS1/mod1
```

Outputs:
- For each module directory: `<module>/<module>.pdf` and `<module>/<module>.html`
- For each MS directory: `MSX.pdf` (merged of all module PDFs in that MS)

### Note File Format

No special front-matter is required. Any `.md` or `.txt` file will be included.

Example (optional structure only):

```markdown
# Title

## Main Points
- Point 1
- Point 2

## Details
Your notes here...
```

### Output Files

- **PDF**: Professional documents with table of contents
- **HTML**: Web-ready presentations with slide formatting
- **Merged PDFs**: Combined module PDFs into year-level documents

## Customization

### Fonts
Edit `fonts.tex` to change LaTeX fonts:
```latex
\setromanfont{Latin Modern Roman}
```

### HTML Styling
Modify `slidy.html` to customize HTML presentation appearance.

### Script Behavior & Configuration
- Templates are taken from the script directory: `about.md`, `fonts.tex`, `slidy.html`
- You do NOT need to copy templates into your workdir
- File discovery: all `.md` and `.txt` files in each module directory (non-recursive per module)
- PDF merging uses Ghostscript when available

## Troubleshooting

### Common Issues

1. **LuaLaTeX not found**
   - Ensure TeXLive or MacTeX is properly installed
   - Check PATH includes LaTeX binaries

2. **Pandoc errors**
   - Verify Pandoc installation: `pandoc --version`
   - Check input file format

3. **Font issues**
   - Ensure fonts are available on your system
   - Modify `fonts.tex` for different fonts

4. **Permission denied**
   - Make script executable: `chmod +x notes`

### Getting Help

- Check Pandoc documentation: https://pandoc.org/
- LaTeX documentation: https://www.latex-project.org/
- LuaLaTeX guide: https://www.luatex.org/


## Acknowledgments

- 12 Years Ago [Vim notetaking tips - YouTube Video](https://www.youtube.com/watch?v=wh_WGWii7UE)
- [@github/Connermcd/notes](https://github.com/connermcd/notes)
- Built with [Pandoc](https://pandoc.org/)
- Powered by [LuaLaTeX](https://www.luatex.org/)
- HTML styling based on [Slidy](https://www.w3.org/Talks/Tools/Slidy2/)
