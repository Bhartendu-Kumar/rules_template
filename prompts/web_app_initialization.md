# Web Application Initialization Prompt

This prompt helps initialize the rules_template framework for a web application project, establishing proper structure, workflows, and documentation for both frontend and backend components.

## Usage

Replace `{{TARGET_REPO_URL}}` with the URL of your target repository.

```
You are Claude, an AI assistant specializing in web application development. You will now help integrate the rules_template framework into an existing or new web application project repository.

# INITIALIZATION TASK

Initialize the rules_template structure from https://github.com/decision-crafters/rules_template.git and apply it to the target repository ({{TARGET_REPO_URL}}). This involves:

1. First checking if you're already in the target repository directory
2. Analyzing the repository to understand its current structure, architecture, and tech stack
3. Creating the required directory structure from rules_template while preserving all existing code and functionality
4. Setting up the memory files with web-specific content that reflects the target project
5. Establishing a clear workflow for frontend, backend, and full-stack development

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
   - README and documentation
   - Directory structure and organization
   - Frontend framework and components
   - Backend services and architecture
   - API design and integration patterns
   - State management and data flow
   - Testing and deployment strategies

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
   
   # Web application specific directories
   mkdir -p src/frontend/components
   mkdir -p src/frontend/pages
   mkdir -p src/frontend/assets
   mkdir -p src/frontend/styles
   mkdir -p src/frontend/utils
   
   mkdir -p src/backend/controllers
   mkdir -p src/backend/models
   mkdir -p src/backend/routes
   mkdir -p src/backend/services
   mkdir -p src/backend/middleware
   
   mkdir -p config/environments
   mkdir -p public
   mkdir -p test/frontend
   mkdir -p test/backend
   mkdir -p test/integration
   ```

3. Preserve all existing functionality by not overwriting or deleting any existing files

## MEMORY FILE INITIALIZATION

Populate the memory files based on the analyzed repository content:

1. docs/product_requirement_docs.md:
   - Define the web application's purpose and user goals
   - Outline the features and user stories
   - Document user flows and interaction patterns
   - Specify accessibility and performance requirements

2. docs/architecture.md:
   - Detail the application architecture (MVC, microservices, etc.)
   - Document component relationships and data flow
   - Specify the API design and communication patterns
   - Outline state management and persistence strategies
   - Describe the deployment architecture

3. docs/technical.md:
   - List the technology stack (frameworks, libraries, tools)
   - Document build and bundling configuration
   - Specify coding standards and patterns
   - Detail authentication and authorization mechanisms
   - Document responsive design approach

4. tasks/tasks_plan.md:
   - Create a prioritized development roadmap
   - Document frontend, backend, and integration tasks
   - Outline testing strategy and coverage goals
   - Define deployment pipeline milestones

5. tasks/active_context.md:
   - Document the current development focus
   - Highlight UI/UX challenges being addressed
   - Track API integration status
   - Note performance or security concerns

## WEB APPLICATION ENHANCEMENT FOCUS

Based on the context gathered, enhance these web development aspects:

1. Component architecture and reusability
2. API design and documentation
3. State management and data flow
4. Responsive and accessible design
5. Performance optimization
6. Testing coverage and automation
7. Security best practices
8. CI/CD pipeline for frontend and backend

## EXECUTION INSTRUCTIONS

1. Begin by analyzing the repository structure and web architecture
2. Document your findings in the memory files
3. Apply the rules_template structure without disrupting existing code
4. Initialize the memory files with web-specific content
5. Implement an initial proof of concept for enhanced web development practices
6. Document lessons learned and any error resolutions
7. Suggest optimization opportunities for the web application

After initialization, provide a summary of:
- The implemented structure
- How existing functionality was preserved
- Next steps for expanding the web application capabilities

Please output your work in an organized, step-by-step manner, documenting your progress in the appropriate memory files as specified in the rules_template framework.
```
