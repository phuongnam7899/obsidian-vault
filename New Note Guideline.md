# New Note Guidelines

## Note Structure

### Frontmatter

- Date and time: `{{date}} {{time}}`
- Tags: Use appropriate tags from the "3 - Tags" directory (Create new tag if really neccessary)

### Content Layout

- Begin with a clear definition or primary concept
- Use bullet points for concise information
- Include code blocks with appropriate language syntax highlighting when needed
- Use nested bullet points for hierarchical information
- Add examples where relevant

### References Section

- Always include a "References" section at the bottom
- Link to related notes using double brackets syntax `[[Note Name]]`

## Folder Organization

### 1 - Rough Notes

- For initial, unrefined thoughts
- Quick capture of ideas before proper organization

### 2 - Source Material

- Notes from external sources
- Use the Source Material template
- Include source links and status (e.g., #source-eating)

### 3 - Tags

- Contains tag index files
- Each tag file may include links to related notes

### 4 - Indexes

- For organizing and linking related content
- Creates a table of contents for specific topics

### 5 - Templates

- Contains reusable templates:
  - Main Note template
  - Source Material template
  - Design Pattern template

### 6 - Main Notes

- No nested folder here, only notes files
- Refined, organized knowledge
- Use the Main Note template
- Includes concept definitions, examples, and technical information
- Should be properly tagged and referenced
- Follow Atomic Note technique

### 7 - Files

- For attachments and external resources

### 8 - Content Factory

- For notes in development/production phase

## Tagging System

- Use tags to categorize notes by topic
- Create new tag files in the "3 - Tags" directory when needed
- Tags should be specific enough to be useful but general enough to group related concepts
- Common tag categories include:
  - Technology (e.g., #Java, #ReactJS)
  - Domain (e.g., #Finance, #Business)
  - Concept type (e.g., #Design-Pattern, #Clean-Code)

## Note Creation Workflow

1. Start with a rough note if capturing quick thoughts
2. When refining, use the appropriate template
3. Place in the correct directory based on note type
4. Add proper tags and references
5. Link to related notes in the References section

## Formatting Guidelines

- Use Markdown syntax for formatting
- Create hierarchical structure with headers (# for main headers, ## for subheaders)
- Use bullet points for lists
- Use code blocks with syntax highlighting for code examples
- Use dividers (---) to separate sections
- Link related concepts using wiki-style links [[Note Name]]

## Best Practices

- Keep notes atomic (one main concept per note)
- Use descriptive titles that start with "what is" or clear actions
- Create meaningful connections between notes
- Regularly review and update existing notes
- Maintain consistency in formatting and organization
- For tags included in each note, using link to a file inside '3- Tags' folder (instead of using #) (For example `[[TagName]]` instead of `#TagName`)
