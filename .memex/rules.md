# Memextech App Registry - Adding New MCP Servers

## Project Overview

This is a fork of the official Memextech app registry where we maintain and add new MCP (Model Context Protocol) servers for AI assistant integration.

**Project Structure**: Working directory is the project root folder

## Process for Adding New MCP Servers

### 1. Research Phase

**Goal**: Find official MCP servers and gather all necessary information

#### Steps:
1. **Search for official MCP servers**:
   ```bash
   # Use search tool to find official repositories
   # Search terms: "[Company] MCP server model context protocol github"
   ```

2. **Key information to collect**:
   - Official GitHub repository URL
   - NPM package name (if available)
   - Package manager and installation command
   - Authentication requirements
   - Available features and capabilities
   - Setup documentation

3. **Verify authenticity**:
   - Check if the repository is under the official organization
   - Look for official documentation links
   - Verify package ownership on NPM

### 2. Icon Acquisition

**Goal**: Obtain appropriate light and dark SVG icons for the service

#### Options:
1. **Official brand assets** (preferred):
   - Search on https://brandfetch.com/ first for official brand assets
   - Check company's brand/press kit pages
   - Look for official SVG downloads
   - Use vector logo repositories like vectorlogo.zone

2. **Create from existing assets**:
   - Download official logos and convert to appropriate formats
   - Ensure proper light/dark variants

#### Icon Requirements:
- **Format**: SVG only
- **Variants**: Both light and dark versions needed
- **Naming**: `{service-name}-light.svg` and `{service-name}-dark.svg`
- **Colors**: 
  - Light version: Dark colors for light backgrounds
  - Dark version: Light colors for dark backgrounds
- **Size**: Scalable SVG (typically 64x64 viewBox or similar)

#### Icon Storage:
```bash
# Copy icons to assets folder
cp /path/to/icon-light.svg ./assets/{service}-light.svg
cp /path/to/icon-dark.svg ./assets/{service}-dark.svg
```

### 3. JSON Entry Creation

**Goal**: Add properly formatted entry to apps.json

#### Entry Structure:
```json
{
  "name": "Service Name",
  "description": "Clear description of what the MCP server enables Claude to do",
  "icon": {
    "type": "url",
    "url": {
      "light": "https://raw.githubusercontent.com/memextech/app-registry/refs/heads/main/assets/{service}-light.svg",
      "dark": "https://raw.githubusercontent.com/memextech/app-registry/refs/heads/main/assets/{service}-dark.svg"
    }
  },
  "category": "Appropriate Category",
  "price": "Free",
  "developer": "Official Developer Name",
  "sourceUrl": "https://github.com/official/repo",
  "config": {
    "mcpKey": "unique-key",
    "runtime": "npx|uvx",
    "args": [
      "-y",
      "package-name"
    ]
  },
  "features": [
    {
      "name": "Feature Name",
      "description": "What this feature does",
      "prompt": "Example prompt to demonstrate usage"
    }
  ],
  "setup": [
    {
      "label": "Setup Instruction",
      "value": "Description with links",
      "type": "text"
    },
    {
      "label": "API Key Label",
      "type": "input",
      "placeholder": "Enter your API key",
      "value": "Enter your API key",
      "key": "ENV_VAR_NAME"
    }
  ]
}
```

#### Categories:
- Development
- Utilities  
- Communication
- Productivity
- Finance
- Social
- Search
- Flashcards

#### Runtime Options:
- `npx`: For Node.js packages
- `uvx`: For Python packages

### 4. Integration Steps

1. **Find insertion point**:
   ```bash
   # Find where to insert (usually by category or alphabetically)
   grep -n "category.*Development" apps.json
   ```

2. **Add entry to apps.json**:
   - Insert before or after similar entries
   - Maintain proper JSON formatting
   - Ensure proper comma placement

3. **Validate JSON**:
   ```bash
   # Check JSON syntax
   python3 -m json.tool apps.json > /dev/null && echo "JSON is valid" || echo "JSON is invalid"
   ```

### 5. Quality Checklist

Before committing:

- [ ] JSON is valid syntax
- [ ] Icons exist in assets folder
- [ ] Icon URLs match the pattern
- [ ] All required fields are present
- [ ] Setup instructions are clear and include links
- [ ] Features have realistic example prompts
- [ ] Package installation command is correct
- [ ] Environment variables are properly named
- [ ] Category is appropriate
- [ ] Description is clear and actionable

### 6. Example: Netlify MCP Addition

**What we did**:
1. Researched official Netlify MCP at `https://github.com/netlify/netlify-mcp`
2. Found NPM package `@netlify/mcp`
3. Used official Netlify brand SVG icons (variants 0 and 3)
4. Created comprehensive entry with 4 key features
5. Added setup instructions for Personal Access Token
6. Placed in "Development" category
7. Validated JSON syntax

**Result**: Successfully added Netlify MCP with proper authentication setup and clear usage examples.

## Troubleshooting

### Common Issues:
1. **JSON syntax errors**: Use `python3 -m json.tool` to validate
2. **Missing icons**: Ensure both light and dark variants exist
3. **Incorrect URLs**: Double-check GitHub raw URLs for icons
4. **Wrong runtime**: Verify if package is Node.js (npx) or Python (uvx)
5. **Missing setup**: Always include authentication setup if required

### Best Practices:
- Research thoroughly before starting
- Use official sources only
- Test JSON validation after each change
- Write clear, actionable descriptions
- Include realistic example prompts
- Provide complete setup instructions

## File Locations

- **Main registry**: `apps.json`
- **Icons**: `assets/` folder
- **This documentation**: `.memex/rules.md`

## Git Workflow

When making changes:
1. Create feature branch for new additions
2. Commit early and often
3. Include clear commit messages
4. Include Memex co-authorship in commits