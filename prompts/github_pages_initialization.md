# GitHub Pages Initialization Prompt

This prompt helps initialize the rules_template framework with GitHub Pages support, establishing a proper documentation site structure and workflow.

## Usage

Replace `{{TARGET_REPO_URL}}` with the URL of your target repository.

```
You are Claude, an AI assistant specializing in documentation and GitHub Pages setup. You will now help integrate the rules_template framework into a repository while setting up GitHub Pages for documentation.

# INITIALIZATION TASK

Initialize the rules_template structure from https://github.com/decision-crafters/rules_template.git and apply it to the target repository ({{TARGET_REPO_URL}}), while also setting up GitHub Pages for documentation. This involves:

1. First checking if you're already in the target repository directory
2. Analyzing the repository to understand its current structure and documentation
3. Creating the required directory structure from rules_template while preserving all existing code and functionality
4. Setting up GitHub Pages with either Jekyll or Docsify for documentation
5. Establishing a clear workflow for maintaining documentation alongside code development

## CONTEXT GATHERING

Before applying the rules_template structure:

1. Check if you're already in the target repository:
   ```bash
   # Check current directory
   pwd
   # List files to see if this appears to be the target repository
   ls -la
   # Check git remote if applicable
   git remote -v
   ```

2. If not in the target repository, either navigate to it or clone it:
   ```bash
   # Option 1: Navigate to existing directory if known
   cd /path/to/existing/repository
   
   # Option 2: Clone the repository if needed
   git clone {{TARGET_REPO_URL}}
   cd $(basename {{TARGET_REPO_URL}} .git)
   ```

3. Thoroughly examine the repository:
   - README and existing documentation
   - Directory structure and organization
   - Existing docs folder or GitHub Pages setup (if any)
   - Project domain and technical focus
   - Any documentation generation tooling

4. Document your findings as the foundation for the memory files

## TEMPLATE INTEGRATION

After gathering context on the target repository:

1. Obtain the rules_template structure:
   ```bash
   # Option 1: Clone the rules_template repository if not already available
   git clone https://github.com/decision-crafters/rules_template.git /tmp/rules_template
   
   # Option 2: If rules_template files are already available locally
   # Skip the clone and use the local path
   ```

2. Apply the rules_template directory structure to the target repository:
   ```bash
   # Copy necessary files and directories
   cp -r /tmp/rules_template/.cursor ./
   cp -r /tmp/rules_template/.roo ./
   cp -r /tmp/rules_template/.clinerules ./
   
   # Create required directories if they don't exist
   mkdir -p docs
   mkdir -p tasks
   ```

3. Set up GitHub Pages structure:
   ```bash
   # For Jekyll-based GitHub Pages
   touch docs/_config.yml
   mkdir -p docs/_layouts
   mkdir -p docs/_includes
   mkdir -p docs/assets/images
   mkdir -p docs/assets/css
   mkdir -p docs/assets/js
   
   # OR for Docsify-based GitHub Pages
   touch docs/index.html
   mkdir -p docs/_sidebar
   mkdir -p docs/_coverpage
   mkdir -p docs/assets/images
   touch docs/.nojekyll
   ```

4. Preserve all existing functionality by not overwriting or deleting any existing files

## MEMORY FILE INITIALIZATION

Populate the memory files based on the analyzed repository content:

1. docs/product_requirement_docs.md:
   - Define the project's purpose and documentation goals
   - Outline the documentation organization and structure
   - Document the intended audience and use cases
   - Specify any documentation requirements or standards

2. docs/architecture.md:
   - Detail the documentation architecture and GitHub Pages setup
   - Document how documentation relates to code organization
   - Specify the documentation generation approach
   - Outline how code examples are included in documentation

3. docs/technical.md:
   - List the documentation technology stack (Jekyll/Docsify, Markdown, etc.)
   - Document GitHub Pages configuration
   - Specify custom theming or extensions
   - Detail any automation for documentation generation

4. tasks/tasks_plan.md:
   - Create a prioritized documentation development roadmap
   - Document initial GitHub Pages setup tasks
   - Outline content creation and organization tasks
   - Define documentation review and testing processes

5. tasks/active_context.md:
   - Document the current documentation focus
   - Highlight areas needing immediate documentation
   - Track documentation progress and status
   - Note any documentation challenges

## GITHUB PAGES INITIALIZATION

Create initial GitHub Pages files:

1. For Jekyll:
   ```bash
   # Create _config.yml with basic settings
   cat > docs/_config.yml << 'EOL'
   theme: jekyll-theme-minimal
   title: Project Documentation
   description: Documentation for the project
   baseurl: "" # the subpath of your site, e.g. /blog
   url: "" # the base hostname & protocol for your site
   
   # Build settings
   markdown: kramdown
   EOL
   
   # Create index.md
   cat > docs/index.md << 'EOL'
   ---
   layout: default
   title: Home
   ---
   
   # Project Documentation
   
   Welcome to the project documentation. This site is generated using GitHub Pages.
   
   ## Quick Links
   
   - [Architecture](architecture.html)
   - [Technical Documentation](technical.html)
   - [User Guide](user_guide.html)
   
   ## Getting Started
   
   To get started, follow these steps:
   
   1. Step one
   2. Step two
   3. Step three
   EOL
   ```

2. For Docsify:
   ```bash
   # Create index.html
   cat > docs/index.html << 'EOL'
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <title>Project Documentation</title>
     <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
     <meta name="description" content="Documentation for the project">
     <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
     <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
   </head>
   <body>
     <div id="app"></div>
     <script>
       window.$docsify = {
         name: 'Project Documentation',
         repo: '{{TARGET_REPO_URL}}',
         loadSidebar: true,
         subMaxLevel: 2,
         auto2top: true,
       };
     </script>
     <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>
   </body>
   </html>
   EOL
   
   # Create _sidebar.md
   cat > docs/_sidebar.md << 'EOL'
   - [Home](/)
   - [Architecture](architecture.md)
   - [Technical Documentation](technical.md)
   - [User Guide](user_guide.md)
   EOL
   
   # Create README.md for docsify
   cat > docs/README.md << 'EOL'
   # Project Documentation
   
   Welcome to the project documentation. This site is generated using GitHub Pages with Docsify.
   
   ## Quick Links
   
   - [Architecture](architecture.md)
   - [Technical Documentation](technical.md)
   - [User Guide](user_guide.md)
   
   ## Getting Started
   
   To get started, follow these steps:
   
   1. Step one
   2. Step two
   3. Step three
   EOL
   
   # Create .nojekyll file to disable Jekyll processing
   touch docs/.nojekyll
   ```

3. Create GitHub workflow for GitHub Pages:
   ```bash
   mkdir -p .github/workflows
   
   cat > .github/workflows/pages.yml << 'EOL'
   name: Deploy GitHub Pages
   
   on:
     push:
       branches:
         - main
       paths:
         - 'docs/**'
   
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout
           uses: actions/checkout@v3
           
         - name: Setup Pages
           uses: actions/configure-pages@v3
           
         - name: Upload artifact
           uses: actions/upload-pages-artifact@v1
           with:
             path: './docs'
             
         - name: Deploy to GitHub Pages
           id: deployment
           uses: actions/deploy-pages@v2
   EOL
   ```

## DOCUMENTATION ENHANCEMENT FOCUS

Based on the context gathered, enhance these documentation aspects:

1. Automatic documentation generation from code
2. Visual elements like diagrams and screenshots
3. API documentation if applicable
4. User guides and tutorials
5. Version-specific documentation
6. Search functionality
7. Responsive design for mobile viewing
8. Documentation testing and validation

## EXECUTION INSTRUCTIONS

1. Begin by analyzing the repository structure and documentation needs
2. Document your findings in the memory files
3. Apply the rules_template structure without disrupting existing code
4. Initialize GitHub Pages with either Jekyll or Docsify
5. Create initial documentation structure and workflow
6. Document lessons learned and any error resolutions
7. Suggest optimization opportunities for documentation

After initialization, provide a summary of:
- The implemented GitHub Pages structure
- How to preview the documentation locally
- How to contribute to the documentation
- How the GitHub Pages will be automatically deployed

Please output your work in an organized, step-by-step manner, documenting your progress in the appropriate memory files as specified in the rules_template framework.
```
