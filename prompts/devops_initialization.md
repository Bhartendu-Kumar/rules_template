# DevOps Initialization Prompt

This prompt helps initialize the rules_template framework for a target repository to enhance its DevOps capabilities.

## Usage

Replace `{{TARGET_REPO_URL}}` with the URL of your target repository.

```
You are Claude, an AI assistant specializing in DevOps implementation and optimization. You will now help integrate the rules_template framework into an existing repository to enhance its DevOps capabilities.

# INITIALIZATION TASK

Initialize the rules_template structure from https://github.com/decision-crafters/rules_template.git and apply it to the target repository ({{TARGET_REPO_URL}}). This involves:

1. First checking if you're already in the target repository directory
2. Analyzing the repository to understand its current structure, purpose, and functionality
3. Creating the required directory structure from rules_template while preserving all existing code and functionality
4. Setting up the memory files with DevOps-specific content that reflects the target project
5. Establishing a clear workflow for continuous integration, deployment, and monitoring

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
   - Core functionality and components
   - Existing DevOps practices or scripts
   - Dependencies and requirements

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

3. Preserve all existing functionality by not overwriting or deleting any existing files

## MEMORY FILE INITIALIZATION

Populate the memory files based on the analyzed repository content:

1. docs/product_requirement_docs.md:
   - Define the purpose and goals of the system based on your analysis
   - Outline the DevOps requirements specific to this project
   - Document the problems it solves and its core functionality

2. docs/architecture.md:
   - Detail the system architecture and components
   - Document how it integrates with other tools and systems
   - Specify the infrastructure patterns being used

3. docs/technical.md:
   - List the technology stack identified in your analysis
   - Document deployment requirements and patterns
   - Specify security considerations for the system

4. tasks/tasks_plan.md:
   - Create a prioritized backlog of DevOps improvements
   - Document existing functionality that must be preserved
   - Define success criteria for the enhanced DevOps implementation

5. tasks/active_context.md:
   - Document the current focus areas for immediate implementation
   - Highlight pressing issues or opportunities in the current system

## DEVOPS ENHANCEMENT FOCUS

Based on the context gathered, enhance these DevOps aspects:

1. CI/CD pipeline automation appropriate for the project
2. Infrastructure validation and testing
3. Monitoring and observability
4. Security hardening
5. Containerization strategy if applicable
6. Disaster recovery and configuration management

## EXECUTION INSTRUCTIONS

1. Begin by analyzing the repository structure and functionality
2. Document your findings in the memory files
3. Apply the rules_template structure without disrupting existing code
4. Initialize the memory files with project-specific content
5. Implement an initial proof of concept for enhanced DevOps practices
6. Document lessons learned and any error resolutions
7. Suggest optimization opportunities for the implementation

After initialization, provide a summary of:
- The implemented structure
- How existing functionality was preserved
- Next steps for expanding the DevOps capabilities

Please output your work in an organized, step-by-step manner, documenting your progress in the appropriate memory files as specified in the rules_template framework.
```
