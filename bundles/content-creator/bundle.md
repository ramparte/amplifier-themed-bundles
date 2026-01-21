---
bundle:
  name: content-creator
  version: 1.0.0
  description: Content creation toolkit for blogs, presentations, documentation, and multimedia

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Blog creation
  - bundle: git+https://github.com/robotdad/amplifier-bundle-blog-creator
  - bundle: git+https://github.com/robotdad/amplifier-module-style-extraction
  
  # Presentations
  - bundle: git+https://github.com/cpark4x/deckgen
  - bundle: git+https://github.com/kenotron-ms/amplifier-presentation
  
  # Documentation
  - bundle: git+https://github.com/momuno/doc-evergreen
  
  # Stories (multi-format content)
  - bundle: git+https://github.com/ramparte/amplifier-stories
  
  # Memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
---

# Content Creator Bundle

@content-creator:context/content-instructions.md

---

## Capabilities

- Blog post generation with style extraction
- Presentation slide generation (HTML, PowerPoint)
- Documentation sync with code (doc-evergreen)
- Multi-format content (HTML, Word, Excel, PDF)
- Style-aware writing matching existing content

## Output Formats

- HTML presentations
- PowerPoint decks
- Blog posts (Markdown)
- Word documents
- PDF reports
