# Debugging and TDD Workflow Initialization Prompt

This prompt helps initialize the rules_template framework with a robust debugging approach and Test-Driven Development workflow, integrating GitHub Actions for continuous testing.

## Usage

Replace `{{TARGET_REPO_URL}}` with the URL of your target repository.

```
You are Claude, an AI assistant specializing in software debugging, Test-Driven Development, and automated testing workflows. You will now help integrate the rules_template framework into a repository with a focus on establishing effective debugging practices and TDD workflows.

# INITIALIZATION TASK

Initialize the rules_template structure from https://github.com/decision-crafters/rules_template.git and apply it to the target repository ({{TARGET_REPO_URL}}), while establishing best practices for debugging and Test-Driven Development with GitHub Actions integration. This involves:

1. First checking if you're already in the target repository directory
2. Analyzing the repository to understand its current structure, testing approach, and debugging practices
3. Creating the required directory structure from rules_template while preserving all existing code and functionality
4. Setting up TDD workflows and implementing Agans' 9 Rules of Debugging
5. Configuring GitHub Actions for continuous testing and validation

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
   - Directory structure and code organization
   - Existing testing approaches and frameworks
   - Current debugging practices or tools
   - CI/CD configuration if present
   - Common bug patterns or issues

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
   
   # Testing and debugging specific directories
   mkdir -p test/unit
   mkdir -p test/integration
   mkdir -p test/e2e
   mkdir -p test/fixtures
   mkdir -p test/mocks
   
   mkdir -p .github/workflows
   mkdir -p scripts/debugging
   mkdir -p docs/debugging-guides
   ```

3. Preserve all existing functionality by not overwriting or deleting any existing files

## MEMORY FILE INITIALIZATION

Populate the memory files based on the analyzed repository content:

1. docs/product_requirement_docs.md:
   - Define the project's quality objectives and testing requirements
   - Outline the debugging philosophy (Agans' 9 Rules)
   - Document test coverage expectations and thresholds
   - Specify regression prevention strategies

2. docs/architecture.md:
   - Detail the testing architecture and test types
   - Document how debugging is integrated into the development workflow
   - Specify the TDD approach and lifecycle
   - Outline test environments and isolation strategies

3. docs/technical.md:
   - List the testing and debugging tools and frameworks
   - Document testing environment configurations
   - Specify mocking and fixture strategies
   - Detail GitHub Actions workflow configuration
   - Document debugging tools and techniques

4. tasks/tasks_plan.md:
   - Create a prioritized testing infrastructure development roadmap
   - Document initial TDD implementation tasks
   - Outline CI pipeline development steps
   - Define key debugging workflow improvements

5. tasks/active_context.md:
   - Document the current testing focus areas
   - Highlight critical bugs or issues being addressed
   - Track test coverage improvement initiatives
   - Note challenging debugging scenarios

6. .cursor/rules/error-documentation.mdc:
   - Document common bug patterns and their solutions
   - Create a debugging decision tree
   - Record lessons learned from past debugging sessions

## DEBUGGING AND TDD WORKFLOW SETUP

1. Create GitHub Actions workflow for continuous testing:
   ```bash
   cat > .github/workflows/test.yml << 'EOL'
   name: Continuous Testing

   on:
     push:
       branches: [ main, develop ]
     pull_request:
       branches: [ main, develop ]

   jobs:
     test:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         
         - name: Set up runtime environment
           # Setup language-specific runtime (Node.js, Python, etc.)
           # This will vary based on the project
           run: echo "Setup environment here"
           
         - name: Install dependencies
           run: echo "Install dependencies here"
           
         - name: Run unit tests
           run: echo "Run unit tests here"
           
         - name: Run integration tests
           run: echo "Run integration tests here"
           
         - name: Generate test coverage report
           run: echo "Generate coverage report here"
           
         - name: Upload test results
           uses: actions/upload-artifact@v3
           with:
             name: test-results
             path: |
               coverage/
               test-results/
   EOL
   ```

2. Create debugging guide based on Agans' 9 Rules:
   ```bash
   cat > docs/debugging-guides/agans-9-rules.md << 'EOL'
   # Agans' 9 Rules of Debugging

   This guide outlines the application of David J. Agans' debugging methodology to our project.

   ## 1. Understand the System

   **Application in our project:**
   - Review architecture documentation before debugging
   - Use system diagrams to visualize component relationships
   - Understand data flow through the system

   **Tools and resources:**
   - Architecture diagrams in docs/architecture.md
   - Component specifications
   - Data flow documentation

   ## 2. Make It Fail

   **Application in our project:**
   - Create reproducible test cases for all bugs
   - Document steps to consistently reproduce issues
   - Automate reproduction in test suites when possible

   **Tools and resources:**
   - test/fixtures directory for test data
   - Regression tests for known bugs
   - CI/CD pipeline for consistent environments

   ## 3. Quit Thinking and Look

   **Application in our project:**
   - Use logging strategically to observe behavior
   - Implement monitoring for production systems
   - Leverage debugging tools appropriate for our stack

   **Tools and resources:**
   - Logging configuration
   - Monitoring dashboards
   - Debugging tools guide

   ## 4. Divide and Conquer

   **Application in our project:**
   - Use binary search techniques to isolate issues
   - Test components in isolation 
   - Leverage mocks and stubs to isolate system parts

   **Tools and resources:**
   - Component-level tests
   - Mock libraries
   - Test harnesses for isolation

   ## 5. Change One Thing at a Time

   **Application in our project:**
   - Document each change during debugging
   - Revert to baseline after each test
   - Use version control for experimental branches

   **Tools and resources:**
   - Git for change tracking
   - Debugging journals
   - Isolated test environments

   ## 6. Keep an Audit Trail

   **Application in our project:**
   - Document debugging steps in issues/tickets
   - Update error-documentation.mdc with findings
   - Record solutions and patterns

   **Tools and resources:**
   - Issue tracking system
   - debugging session templates
   - lessons-learned.mdc file

   ## 7. Check the Plug

   **Application in our project:**
   - Verify environment configuration first
   - Check dependencies and versions
   - Validate inputs and pre-conditions

   **Tools and resources:**
   - Environment validation scripts
   - Dependency checking tools
   - Input validation tests

   ## 8. Get a Fresh View

   **Application in our project:**
   - Implement pair debugging
   - Rotate difficult bugs to fresh team members
   - Use rubber duck debugging techniques

   **Tools and resources:**
   - Code review process
   - Team debugging sessions
   - External consultation process

   ## 9. If You Didn't Fix It, It Ain't Fixed

   **Application in our project:**
   - Require tests proving the fix for all bugs
   - Validate fixes in multiple environments
   - Monitor for regression after deployment

   **Tools and resources:**
   - Regression test suite
   - Multi-environment validation
   - Monitoring alerts for known issues

   ## Integration with Our Workflow

   These debugging principles are integrated into our development workflow:

   1. **Issue Creation**: Document reproduction steps
   2. **Debugging**: Follow the 9 rules systematically
   3. **Fix Implementation**: Use TDD to validate the fix
   4. **Documentation**: Update error-documentation.mdc
   5. **Review**: Peer verification of the fix
   6. **Monitoring**: Post-deployment validation
   EOL
   ```

3. Create TDD workflow guide:
   ```bash
   cat > docs/debugging-guides/tdd-workflow.md << 'EOL'
   # Test-Driven Development Workflow

   This guide outlines our TDD approach for development and debugging.

   ## TDD Cycle

   Our development follows the Red-Green-Refactor cycle:

   1. **Red**: Write a failing test that defines the expected behavior
   2. **Green**: Write the minimum code needed to make the test pass
   3. **Refactor**: Improve the implementation while keeping tests passing

   ## TDD for Features

   When developing new features:

   1. Write acceptance tests describing the feature from a user perspective
   2. Break down the feature into smaller units of work
   3. For each unit:
      - Write a failing unit test
      - Implement just enough code to pass
      - Refactor for clean code
   4. Integrate the units and validate with acceptance tests

   ## TDD for Debugging

   When fixing bugs:

   1. Write a failing test that reproduces the bug
   2. Verify the test fails for the right reason
   3. Fix the code until the test passes
   4. Add regression tests for edge cases
   5. Refactor while maintaining passing tests

   ## Testing Levels

   Our TDD approach encompasses multiple testing levels:

   1. **Unit Tests**: Test individual functions and classes in isolation
   2. **Integration Tests**: Test interactions between components
   3. **End-to-End Tests**: Test complete features from a user perspective

   ## TDD and Agans' Debugging Rules

   TDD naturally complements Agans' debugging principles:
   
   - "Make It Fail" → Reproducible test case
   - "Divide and Conquer" → Isolate with unit tests
   - "Change One Thing at a Time" → Focused test-code cycles
   - "Keep an Audit Trail" → Tests document expectations
   - "If You Didn't Fix It, It Ain't Fixed" → Tests verify fixes

   ## GitHub Actions Integration

   Our GitHub Actions workflow automates the TDD cycle:

   1. Runs tests on every pull request
   2. Validates test coverage meets thresholds
   3. Executes integration tests in isolated environments
   4. Reports results with actionable feedback

   ## Getting Started with TDD

   To apply TDD to your work:

   1. Begin by writing a failing test
   2. Run the test to confirm it fails appropriately
   3. Implement the minimum code to pass
   4. Run the test to confirm it passes
   5. Refactor for clarity and maintainability
   6. Repeat for the next small increment
   EOL
   ```

## GITHUB ACTIONS SETUP

1. Create GitHub Actions workflow for test coverage:
   ```bash
   cat > .github/workflows/coverage.yml << 'EOL'
   name: Test Coverage

   on:
     push:
       branches: [ main, develop ]
     pull_request:
       branches: [ main, develop ]

   jobs:
     coverage:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         
         - name: Set up runtime environment
           # Setup language-specific runtime
           run: echo "Setup environment here"
           
         - name: Install dependencies
           run: echo "Install dependencies here"
           
         - name: Generate coverage report
           run: echo "Generate coverage report here"
           
         - name: Check coverage thresholds
           run: echo "Check if coverage meets thresholds"
           
         - name: Upload coverage report
           uses: actions/upload-artifact@v3
           with:
             name: coverage-report
             path: coverage/
   EOL
   ```

2. Create debugging utility scripts:
   ```bash
   cat > scripts/debugging/reproduce-environment.sh << 'EOL'
   #!/bin/bash
   # Script to reproduce a consistent debugging environment
   
   echo "Setting up debugging environment..."
   
   # Environment setup would go here
   
   echo "Environment ready for debugging"
   EOL
   
   chmod +x scripts/debugging/reproduce-environment.sh
   ```

## DEBUGGING AND TDD ENHANCEMENT FOCUS

Based on the context gathered, enhance these aspects:

1. Test-first development culture and practices
2. Automated testing infrastructure
3. Debugging tools and workflows
4. Systematic bug reproduction and documentation
5. GitHub Actions integration for continuous testing
6. Regression prevention strategies
7. Bug pattern identification and prevention

## EXECUTION INSTRUCTIONS

1. Begin by analyzing the repository structure and existing testing approaches
2. Document your findings in the memory files
3. Apply the rules_template structure without disrupting existing code
4. Initialize the memory files with debugging and TDD-specific content
5. Set up GitHub Actions workflows for testing
6. Create debugging guidelines based on Agans' 9 Rules
7. Establish TDD workflows and documentation

After initialization, provide a summary of:
- The implemented debugging and testing structure
- How to apply TDD practices in the project
- How to leverage GitHub Actions for continuous testing
- How to follow Agans' debugging principles

Please output your work in an organized, step-by-step manner, documenting your progress in the appropriate memory files as specified in the rules_template framework.
```
