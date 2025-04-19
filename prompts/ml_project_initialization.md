# Machine Learning Project Initialization Prompt

This prompt helps initialize the rules_template framework for a machine learning project, establishing proper structure, workflows, and documentation.

## Usage

Replace `{{TARGET_REPO_URL}}` with the URL of your target repository.

```
You are Claude, an AI assistant specializing in machine learning development and MLOps. You will now help integrate the rules_template framework into an existing or new machine learning project repository.

# INITIALIZATION TASK

Initialize the rules_template structure from https://github.com/decision-crafters/rules_template.git and apply it to the target repository ({{TARGET_REPO_URL}}). This involves:

1. First checking if you're already in the target repository directory
2. Analyzing the repository to understand its current structure, purpose, and ML focus
3. Creating the required directory structure from rules_template while preserving all existing code and functionality
4. Setting up the memory files with ML-specific content that reflects the target project
5. Establishing a clear workflow for data processing, model training, evaluation, and deployment

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
   - Existing models and data processing pipelines
   - Data storage and management approach
   - Evaluation metrics and validation strategies
   - Deployment patterns if any

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
   mkdir -p data/raw
   mkdir -p data/processed
   mkdir -p models
   mkdir -p notebooks
   mkdir -p src/features
   mkdir -p src/models
   mkdir -p src/evaluation
   mkdir -p src/visualization
   ```

3. Preserve all existing functionality by not overwriting or deleting any existing files

## MEMORY FILE INITIALIZATION

Populate the memory files based on the analyzed repository content:

1. docs/product_requirement_docs.md:
   - Define the machine learning objectives and goals
   - Outline the problem statement and success criteria
   - Document expected inputs, outputs, and performance metrics
   - Specify any business constraints or requirements

2. docs/architecture.md:
   - Detail the ML system architecture and components
   - Document data flow from ingestion to prediction
   - Specify model architecture choices and alternatives considered
   - Outline training infrastructure and deployment strategy

3. docs/technical.md:
   - List the ML technology stack (frameworks, libraries)
   - Document environment requirements and dependencies
   - Specify data management strategies
   - Document model versioning approach

4. tasks/tasks_plan.md:
   - Create a prioritized ML development roadmap
   - Document tasks for data preprocessing, feature engineering, model development
   - Outline evaluation criteria and metrics
   - Define deployment milestones

5. tasks/active_context.md:
   - Document the current focus areas (data collection, feature engineering, etc.)
   - Highlight pressing issues or opportunities in model performance
   - Track current experiments and their status

## ML ENHANCEMENT FOCUS

Based on the context gathered, enhance these machine learning aspects:

1. Data pipeline automation and versioning
2. Experiment tracking and model versioning
3. Hyperparameter optimization framework
4. Model evaluation and explainability
5. Model serving and monitoring
6. Continuous training and redeployment

## EXECUTION INSTRUCTIONS

1. Begin by analyzing the repository structure and ML workflow
2. Document your findings in the memory files
3. Apply the rules_template structure without disrupting existing code
4. Initialize the memory files with ML-specific content
5. Implement an initial proof of concept for enhanced ML practices
6. Document lessons learned and any error resolutions
7. Suggest optimization opportunities for the ML implementation

After initialization, provide a summary of:
- The implemented structure
- How existing functionality was preserved
- Next steps for expanding the ML capabilities

Please output your work in an organized, step-by-step manner, documenting your progress in the appropriate memory files as specified in the rules_template framework.
```
