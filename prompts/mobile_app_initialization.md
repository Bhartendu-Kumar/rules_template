# Mobile App Development Initialization Prompt

This prompt helps initialize the rules_template framework for a mobile application project, establishing proper structure, workflows, and documentation for both native and cross-platform mobile development.

## Usage

Replace `{{TARGET_REPO_URL}}` with the URL of your target repository.

```
You are Claude, an AI assistant specializing in mobile application development. You will now help integrate the rules_template framework into an existing or new mobile app project repository.

# INITIALIZATION TASK

Initialize the rules_template structure from https://github.com/decision-crafters/rules_template.git and apply it to the target repository ({{TARGET_REPO_URL}}). This involves:

1. First checking if you're already in the target repository directory
2. Analyzing the repository to understand its current structure, platform focus, and tech stack
3. Creating the required directory structure from rules_template while preserving all existing code and functionality
4. Setting up the memory files with mobile-specific content that reflects the target project
5. Establishing a clear workflow for native or cross-platform mobile development

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
   - Platform focus (iOS, Android, or cross-platform)
   - UI components and navigation patterns
   - State management and data persistence
   - Native module integrations
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
   
   # For cross-platform apps (React Native, Flutter)
   mkdir -p src/components
   mkdir -p src/screens
   mkdir -p src/navigation
   mkdir -p src/services
   mkdir -p src/hooks
   mkdir -p src/utils
   mkdir -p src/assets
   mkdir -p src/styles
   
   # For native iOS apps
   mkdir -p ios/Classes/ViewControllers
   mkdir -p ios/Classes/Views
   mkdir -p ios/Classes/Models
   mkdir -p ios/Resources
   
   # For native Android apps
   mkdir -p android/app/src/main/java
   mkdir -p android/app/src/main/res
   
   # Testing directories
   mkdir -p test/unit
   mkdir -p test/integration
   mkdir -p test/e2e
   ```

3. Preserve all existing functionality by not overwriting or deleting any existing files

## MEMORY FILE INITIALIZATION

Populate the memory files based on the analyzed repository content:

1. docs/product_requirement_docs.md:
   - Define the mobile app's purpose, target platforms, and user goals
   - Outline the core features and user stories
   - Document user flows and interaction patterns
   - Specify UI/UX requirements and platform-specific constraints
   - Detail offline capability requirements and data sync strategies

2. docs/architecture.md:
   - Detail the mobile app architecture patterns (MVC, MVVM, Redux, etc.)
   - Document navigation flow and screen relationships
   - Specify data flow and state management
   - Outline native and third-party integrations
   - Describe offline behavior and data persistence strategies

3. docs/technical.md:
   - List the technology stack (frameworks, libraries, SDKs)
   - Document build and deployment configurations
   - Specify platform-specific considerations
   - Detail authentication and authorization mechanisms
   - Document responsive design and accessibility approaches

4. tasks/tasks_plan.md:
   - Create a prioritized development roadmap
   - Document platform-specific implementation tasks
   - Outline testing strategy across platforms
   - Define app store submission and release processes

5. tasks/active_context.md:
   - Document the current development focus
   - Highlight UI/UX challenges being addressed
   - Track API integration status
   - Note performance or platform-specific concerns

## MOBILE APP ENHANCEMENT FOCUS

Based on the context gathered, enhance these mobile development aspects:

1. Component architecture and reusability
2. Native module integration and performance
3. State management and data persistence
4. Responsive UI across device sizes
5. Platform-specific feature implementation
6. Offline capabilities and data synchronization
7. Testing on multiple devices and OS versions
8. CI/CD pipeline for mobile releases

## EXECUTION INSTRUCTIONS

1. Begin by analyzing the repository structure and mobile architecture
2. Document your findings in the memory files
3. Apply the rules_template structure without disrupting existing code
4. Initialize the memory files with mobile-specific content
5. Implement an initial proof of concept for enhanced mobile development practices
6. Document lessons learned and any error resolutions
7. Suggest optimization opportunities for the mobile application

After initialization, provide a summary of:
- The implemented structure
- How existing functionality was preserved
- Next steps for expanding the mobile application capabilities

Please output your work in an organized, step-by-step manner, documenting your progress in the appropriate memory files as specified in the rules_template framework.
```
