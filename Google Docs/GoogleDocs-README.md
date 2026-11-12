# Google Docs Technical Collaboration — Reference & Workflow Guide

A reference manual covering real-time collaboration, structural formatting, version management, and team documentation workflows in **Google Docs**.

---

## 1. Introduction to Google Docs

**Google Docs** is a cloud-based, multi-user word processor within Google Workspace designed for synchronous document creation, technical proposal drafting, and team reporting. It complements developer tools like LaTeX and Doxygen by offering visual editing, integrated reviewing mechanisms, and continuous cloud backup.

---

## 2. Core Technical Writing Features

### 2.1 Paragraph Styles & Automated Table of Contents
Structuring documents using formal paragraph styles (Title, Subtitle, Heading 1, Heading 2, Heading 3) enforces consistent typography and automatically generates an interactive outline and Table of Contents (TOC).

- **Heading Hierarchy**:
  - `Title`: Project Name / Document Title
  - `Heading 1`: Major Sections (e.g., Introduction, Requirements)
  - `Heading 2`: Subsections (e.g., System Architecture, API Specs)
  - `Heading 3`: Sub-components
- **Insert Table of Contents**: `Insert` $\rightarrow$ `Table of contents` (Choose with page numbers or hyperlink markers).

### 2.2 Equations & Math Formulas
Google Docs includes a graphical equation editor supporting basic LaTeX-style math operators:
- **Insert Equation**: `Insert` $\rightarrow$ `Equation`
- **Supported Math Syntax**: Supports inline fractions (`\frac`), superscripts (`^`), subscripts (`_`), Greek letters (`\alpha`, `\beta`, `\pi`), and integrals (`\int`).

### 2.3 Built-in Citations and Bibliography
- **Tool Access**: `Tools` $\rightarrow$ `Citations`
- **Supported Citation Styles**: APA (7th ed.), MLA (8th ed.), Chicago (17th ed. Author-Date).
- **Workflow**: Add reference source details (book, journal, website) manually or via ISBN/DOI lookups, insert inline citations, and click **Insert Bibliography** to generate formatted references.

---

## 3. Real-Time Collaboration & Reviewing Workflows

Google Docs supports three distinct interaction modes that facilitate structured editorial reviews:

```
                  ┌─────────────────────────────────────┐
                  │          Document Access            │
                  └──────────────────┬──────────────────┘
                                     │
         ┌───────────────────────────┼───────────────────────────┐
         ▼                           ▼                           ▼
┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
│   Editing Mode  │         │ Suggesting Mode │         │   Viewing Mode  │
│ Direct changes  │         │ Tracked edits & │         │ Read-only view  │
│ to text/layout  │         │ proposal markup │         │ & export access │
└─────────────────┘         └─────────────────┘         └─────────────────┘
```

### 3.1 Editing Modes
1. **Editing Mode**: Direct modifications alter the active document text immediately.
2. **Suggesting Mode**: Edits appear as color-coded markup proposals. Owners and editors can **Accept** ($\checkmark$) or **Reject** ($\boldsymbol{\times}$) each proposed change.
3. **Viewing Mode**: Read-only mode designed for final document presentation or distribution without risk of accidental modification.

### 3.2 Comments, Assignments, and Threads
- **Add Comment**: Highlight target text $\rightarrow$ Click `+` or press `Ctrl + Alt + M` (`Cmd + Option + M` on macOS).
- **Assign Task**: Type `@username` or `@email` in a comment and check **Assign to [User]** to delegate action items.
- **Resolve Thread**: Click **Resolve** once feedback has been incorporated to archive the comment thread.

---

## 4. Version History & Revision Control

Google Docs continuously saves changes to the cloud, providing an immutable audit trail of document revisions.

### 4.1 Inspecting & Naming Versions
- **Access Revision Log**: `File` $\rightarrow$ `Version history` $\rightarrow$ `See version history` (`Ctrl + Alt + Shift + H`).
- **Milestone Naming**: To preserve key project stages (e.g., *First Draft*, *Faculty Review*, *Final Submission*):
  1. Open Version History.
  2. Click the three dots ($\vdots$) next to a timestamp.
  3. Select **Name this version** and enter a descriptive tag.

### 4.2 Restoring Previous Revisions
Users with edit access can revert the entire document to any historical snapshot without losing subsequent history.

---

## 5. Exporting, Publishing, and Security Controls

### 5.1 Export Options
Export documents into standard offline formats via `File` $\rightarrow$ `Download`:
- **PDF Document (`.pdf`)**: Print-ready, immutable distribution.
- **Microsoft Word (`.docx`)**: Compatibility with desktop office suites.
- **OpenDocument Format (`.odt`)**: Open-standard document exchange.
- **Plain Text (`.txt`) & HTML (`.html`)**: Web and code pipeline conversions.

### 5.2 Permissions & Access Management
- **Share Settings**: Restrict access to specific email addresses, domain users, or anyone with the link.
- **Granular Rights**: Assign *Viewer*, *Commenter*, or *Editor* roles.
- **Link Expiration & Restrictions**: Prevent viewers/commenters from downloading, printing, or copying files under advanced sharing settings.

---

## 6. Matrix Comparison: Google Docs vs. Doxygen vs. LaTeX

| Evaluation Dimension | Google Docs | Doxygen | LaTeX |
| :--- | :--- | :--- | :--- |
| **Primary Output** | Proposals, Specs, Reports | Software API Manuals | Formal Papers, Books, Slides |
| **Creation Paradigm** | Visual WYSIWYG Editor | Code Comment Parsing | Programmatic Text Markup |
| **Collaboration** | Live multi-user cursors | Asynchronous Git PRs | Git / Overleaf integration |
| **Math Support** | Basic graphical editor | LaTeX formulas in tags | Industry-standard native math |
| **Version Control** | Automatic cloud history | Git repository commits | Git repository commits |
| **Ease of Learning** | Immediate (No syntax needed)| Low (Tag learning) | Moderate to High |

---
*Google Docs Technical Collaboration Guide (MNIT Jaipur Technical Writing Course).*
