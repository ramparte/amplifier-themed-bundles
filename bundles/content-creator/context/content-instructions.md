# Content Creation Instructions

## Style Extraction Workflow

When creating content that should match an existing style:

1. **Analyze Source Material**: Use the style extraction module to analyze existing blog posts, documentation, or marketing content
2. **Extract Style Profile**: Identify tone, vocabulary level, sentence structure, and formatting patterns
3. **Apply Consistently**: Generate new content that maintains the extracted style characteristics

### Style Elements to Consider

- **Voice**: First person, third person, formal, conversational
- **Tone**: Technical, friendly, authoritative, casual
- **Structure**: Paragraph length, use of headers, bullet points vs prose
- **Vocabulary**: Technical depth, jargon usage, acronym handling

## Content Workflows

### Blog Post Creation

1. Define the target audience and key message
2. Extract style from existing blog posts if available
3. Generate outline with clear sections
4. Draft content with appropriate tone
5. Add code examples, images, or diagrams as needed
6. Review for SEO considerations (headers, keywords)

### Presentation Generation

1. Determine presentation format (HTML reveal.js or PowerPoint)
2. Define key takeaways (3-5 main points)
3. Structure with clear narrative arc
4. Keep slides focused: one idea per slide
5. Include speaker notes for context

### Documentation Sync (doc-evergreen)

1. Link documentation to source code
2. Detect when code changes invalidate docs
3. Generate update suggestions
4. Maintain consistency between code and documentation

### Multi-Format Stories

1. Create content once, output to multiple formats
2. Supported outputs: HTML, Word, Excel, PDF
3. Use semantic markup for format flexibility
4. Test rendering in each target format

## Format-Specific Tips

### Markdown (Blog Posts)

- Use descriptive headers (H2, H3) for scannability
- Include code blocks with language hints
- Add alt text for images
- Keep paragraphs short (3-4 sentences)

### PowerPoint Presentations

- Limit text per slide (6x6 rule: 6 bullets, 6 words each)
- Use consistent slide layouts
- Include visual hierarchy
- Add presenter notes for additional context

### HTML Presentations (reveal.js)

- Leverage vertical slides for drill-down content
- Use fragments for progressive disclosure
- Include speaker notes with `<aside class="notes">`
- Test transitions and animations

### Word Documents

- Use heading styles for automatic TOC generation
- Include proper figure/table captions
- Maintain consistent formatting
- Use styles rather than direct formatting

### PDF Reports

- Design for print dimensions
- Include page numbers and headers/footers
- Ensure fonts are embedded
- Test accessibility (screen reader compatibility)

## Memory Integration

The tool-memory module helps maintain context across sessions:

- Store style profiles for reuse
- Track content creation history
- Remember audience preferences
- Maintain terminology consistency

## Best Practices

1. **Know Your Audience**: Adjust technical depth and tone accordingly
2. **Start with Structure**: Outline before drafting
3. **Iterate**: First draft is never final
4. **Consistency**: Maintain voice across all content pieces
5. **Accessibility**: Consider all readers and viewers
6. **Reusability**: Create modular content that works across formats
