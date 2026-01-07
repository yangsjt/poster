# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MovePath Design Engine - A single-file web application for creating print-ready visual content. Users upload images, inject AI-generated SVG designs, and export to print-quality PDF.

## Development

No build system. Open `poster.html` directly in a browser to run.

```bash
# Quick local server (optional)
python3 -m http.server 8000
```

## Architecture

**Single file:** `poster.html` (~330 lines)

**External dependencies (CDN):**
- Tailwind CSS - UI framework
- jsPDF v2.5.1 - PDF generation
- svg2pdf.js v2.2.3 - SVG to PDF conversion

**Core workflow:**
1. Image upload → FileReader converts to base64 data URL
2. SVG code injection → Raw SVG inserted into `#canvasContainer`
3. Image binding → Uploaded image injected into SVG's `<image>` element (both `href` and `xlink:href`)
4. PDF export → svg2pdf.js renders vector content, second page contains print specs

**Key DOM elements:**
- `#canvasContainer` - Preview area, holds rendered SVG
- `#svgInput` - Textarea for SVG code
- `#imageUploader` - File input for images
- `#loadingOverlay` - Export progress indicator

**Brand constants:**
- MovePath Orange: `#F05F22`
- Suggested CMYK: C0 M76 Y88 K0
