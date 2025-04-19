# Data Engineering Initialization Prompt

This prompt helps initialize the rules_template framework for a data engineering project, establishing proper structure, workflows, and documentation for data pipelines, ETL processes, and data warehousing.

## Usage

Replace `{{TARGET_REPO_URL}}` with the URL of your target repository.

```
You are Claude, an AI assistant specializing in data engineering and ETL/ELT pipeline development. You will now help integrate the rules_template framework into an existing or new data engineering project repository.

# INITIALIZATION TASK

Initialize the rules_template structure from https://github.com/decision-crafters/rules_template.git and apply it to the target repository ({{TARGET_REPO_URL}}). This involves:

1. First checking if you're already in the target repository directory
2. Analyzing the repository to understand its current structure, data sources, and pipeline architecture
3. Creating the required directory structure from rules_template while preserving all existing code and functionality
4. Setting up the memory files with data engineering-specific content that reflects the target project
5. Establishing a clear workflow for data ingestion, transformation, validation, and loading

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
   - Data sources and sinks
   - ETL/ELT pipeline definitions
   - Scheduler and orchestration tools
   - Data validation and quality checks
   - Pipeline monitoring and error handling
   - Data warehouse or lake architecture

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
   
   # Data engineering specific directories
   mkdir -p src/extractors
   mkdir -p src/transformers
   mkdir -p src/loaders
   mkdir -p src/pipelines
   mkdir -p src/utils
   mkdir -p src/validation
   mkdir -p src/monitoring
   
   mkdir -p config/connections
   mkdir -p config/environments
   
   mkdir -p schemas
   mkdir -p dbt/models
   mkdir -p airflow/dags
   
   mkdir -p test/unit
   mkdir -p test/integration
   mkdir -p test/quality
   ```

3. Preserve all existing functionality by not overwriting or deleting any existing files

## MEMORY FILE INITIALIZATION

Populate the memory files based on the analyzed repository content:

1. docs/product_requirement_docs.md:
   - Define the data engineering goals and business requirements
   - Outline the data sources and destinations
   - Document data freshness and availability requirements
   - Specify data quality and governance standards
   - Detail reporting and analytics use cases

2. docs/architecture.md:
   - Detail the data pipeline architecture (batch vs streaming)
   - Document data flow from source to destination
   - Specify orchestration and scheduling mechanisms
   - Outline error handling and recovery strategies
   - Describe data warehouse/lake design patterns
   - Map out data lineage and dependencies

3. docs/technical.md:
   - List the data technology stack (tools, frameworks, platforms)
   - Document environment configurations
   - Specify connection details and security measures
   - Detail transformation logic and business rules
   - Document testing and validation approaches

4. tasks/tasks_plan.md:
   - Create a prioritized data pipeline development roadmap
   - Document source integration tasks
   - Outline transformation implementation steps
   - Define quality assurance milestones

5. tasks/active_context.md:
   - Document the current development focus
   - Highlight data quality challenges being addressed
   - Track pipeline implementation status
   - Note performance or scalability concerns

## DATA ENGINEERING ENHANCEMENT FOCUS

Based on the context gathered, enhance these data engineering aspects:

1. Data pipeline automation and orchestration
2. Data validation and quality monitoring
3. Metadata management and data catalog integration
4. Incremental loading and change data capture
5. Pipeline testing and recovery strategies
6. Data lineage and governance
7. Performance optimization for large datasets
8. CI/CD for data pipelines

## EXECUTION INSTRUCTIONS

1. Begin by analyzing the repository structure and data architecture
2. Document your findings in the memory files
3. Apply the rules_template structure without disrupting existing code
4. Initialize the memory files with data engineering-specific content
5. Implement an initial proof of concept for enhanced data pipeline practices
6. Document lessons learned and any error resolutions
7. Suggest optimization opportunities for the data engineering implementation

After initialization, provide a summary of:
- The implemented structure
- How existing functionality was preserved
- Next steps for expanding the data engineering capabilities

Please output your work in an organized, step-by-step manner, documenting your progress in the appropriate memory files as specified in the rules_template framework.
```
