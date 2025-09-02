# POrigins Sprites Repository

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

The POrigins Sprites Repository is a comprehensive collection of PNG sprites for the Poketibia server "Porigins". This is a media/asset repository containing over 22,000 sprites organized in categories for game items and Pokemon.

## Working Effectively

### Repository Navigation
- Navigate to the repository root: `cd /home/runner/work/porigins-sprites/porigins-sprites`
- View current directory contents: `ls -la`
- Check repository status: `git status`
- View repository structure:
  - `/items/` - Game item sprites organized by type (pokeballs, foods, tools, etc.)
  - `/pokemons/` - Pokemon sprites with variants (normal, shiny, portraits, corpses)
  - Root level PNG files for miscellaneous items
  - `stats.json` - Auto-generated sprite and category counts

### Essential Commands
- Search for specific sprites: `find . -name "*charizard*" -type f`
- List sprite categories: `ls items/` or `ls pokemons/`
- View sprite details: `file path/to/sprite.png`
- Count total sprites: `find . -type f -iname "*.png" ! -path "./.git/*" ! -path "./.github/*" | wc -l`
- Count categories: `find . -type d ! -path "./.git*" ! -path "./.github*" ! -path "*/.*" ! -name "." | wc -l`

### GitHub Workflow Operations
- Stats generation runs automatically on pushes to `develop` branch
- Workflow file: `.github/workflows/stats.yml`
- Stats generation takes ~0.2 seconds - NEVER CANCEL (set timeout to 60+ seconds)
- Updates `stats.json` with current sprite and category counts
- Triggered by changes to image files (png, jpg, jpeg, bmp, gif) or workflow file
- Test command: `IMAGE_EXTENSIONS="png jpg jpeg bmp gif" && TOTAL_IMAGES=0 && for ext in $IMAGE_EXTENSIONS; do count=$(find . -type f -iname "*.${ext}" ! -path "./.git/*" ! -path "./.github/*" | wc -l); TOTAL_IMAGES=$((TOTAL_IMAGES + count)); done && echo "Total: $TOTAL_IMAGES"`

## Validation

### Manual Validation for Sprite Changes
- ALWAYS verify sprite files are valid PNG images: `file path/to/sprite.png`
- Check sprite is properly organized in appropriate category directory
- Ensure file naming follows existing patterns in the category
- Verify no duplicate sprites exist in multiple locations
- Test search functionality: `find . -name "*sprite-name*" -type f`

### Common Validation Scenarios
- Adding new Pokemon sprites: Place in `/pokemons/[pokemon-number]-[name]/` directory
- Adding item sprites: Place in appropriate `/items/[category]/` subdirectory
- Always check existing directory structure before adding new categories
- Verify sprites follow naming conventions used in similar categories

### No Traditional Build/Test Process
- This repository contains only asset files - no compilation required
- No unit tests or test suite exists
- No linting or code formatting tools are used
- Only validation is ensuring PNG files are valid images and properly organized

## Common Tasks

### Adding New Sprites
- Identify appropriate category directory in `/items/` or `/pokemons/`
- Place sprite files with descriptive names following existing patterns
- Use Git to add and commit: `git add .` then `git commit -m "Add [description]"`
- Push changes to trigger stats update workflow

### Searching and Organizing
- Search by Pokemon name: `find . -name "*pokemon-name*" -type f`
- Search by item type: `ls items/[category]/`
- Find all sprites in a category: `find ./items/pokeballs -name "*.png" -type f`
- List all Pokemon directories: `ls pokemons/`

### Working with Git
- Check current branch: `git branch`
- View recent changes: `git log --oneline -10`
- See file differences: `git diff`
- Add new sprites: `git add path/to/sprite.png`
- Commit changes: `git commit -m "Descriptive message"`

## Repository Statistics (Current Validated Counts)
- Total sprites: 22,036 PNG files (verified with find command)
- Categories: 309 directories (verified with find command)
- Main categories: items (75+ subcategories), pokemons (45+ Pokemon)
- File types: Primarily PNG images, some directories contain variants (shiny, portrait, corpse)
- Stats generation timing: ~0.2 seconds for full repository scan

## File Organization Guidelines
- Pokemon sprites go in `/pokemons/[number]-[name]/` format
- Item sprites go in `/items/[category]/[subcategory]/` hierarchy
- Use descriptive filenames that indicate sprite purpose
- Follow existing naming patterns within each category
- Maintain consistent directory structure for similar sprite types

## Key Project Locations
- **Item Categories**: `/items/pokeballs/`, `/items/foods/`, `/items/tools/`, etc.
- **Pokemon Sprites**: `/pokemons/0006-charizard/`, `/pokemons/0150-mewtwo/`, etc.
- **Statistics**: `stats.json` (auto-updated by GitHub workflow)
- **Workflow Configuration**: `.github/workflows/stats.yml`

## Important Notes
- This is an asset repository, not a software project
- No build process, compilation, or testing infrastructure exists
- Primary workflow is adding, organizing, and managing sprite files
- GitHub workflow automatically maintains sprite statistics
- Changes should focus on sprite organization and file management