# Prompts Guide for rules_template

This directory contains specialized prompts that can be used with AI assistants to extend and enhance the rules_template framework for different use cases.

## Available Prompts

1. [DevOps Initialization](./devops_initialization.md) - Initializes the rules_template framework for DevOps-focused projects
2. [Machine Learning Project Initialization](./ml_project_initialization.md) - Sets up rules_template for ML and data science projects
3. [Web Application Initialization](./web_app_initialization.md) - Configures rules_template for web app development (frontend and backend)
4. [Mobile App Development Initialization](./mobile_app_initialization.md) - Adapts rules_template for mobile app projects (native and cross-platform)
5. [Data Engineering Initialization](./data_engineering_initialization.md) - Applies rules_template to data pipeline and ETL/ELT projects
6. [GitHub Pages Initialization](./github_pages_initialization.md) - Configures rules_template with GitHub Pages for documentation
7. [Debugging and TDD Workflow](./debugging_tdd_workflow.md) - Establishes systematic debugging practices and Test-Driven Development with GitHub Actions

## How to Add a New Prompt

To add a new specialized prompt to the collection, follow these steps:

1. **Identify the Use Case**: Determine a specific use case where rules_template could be applied (e.g., web development, data science, mobile app development).

2. **Create a New File**: Create a new Markdown file in the `/prompts` directory with a descriptive name (e.g., `data_science_initialization.md`).

3. **Structure Your Prompt**: Follow this recommended structure:
   - Title and brief description
   - Usage instructions with any variables clearly marked
   - The complete prompt with well-defined sections
   - Examples of usage (optional)

4. **Parameterize When Possible**: Use variables like `{{TARGET_REPO_URL}}` for elements that will change with each use.

5. **Test Your Prompt**: Test the prompt with an AI assistant to ensure it produces the expected results.

6. **Update This README**: Add your new prompt to the "Available Prompts" section above.

## Prompt Development Guidelines

For effective prompts that work well with rules_template:

1. **Understand the Framework**: Familiarize yourself with the rules_template structure and memory files before creating a prompt.

2. **Focus on Initialization**: Prompts should primarily focus on initializing the repository with the right structure and initial content.

3. **Preserve Existing Content**: All prompts should emphasize preserving existing functionality when applying to established repositories.

4. **Be Domain-Specific**: Target your prompt to the specific domain or use case, including domain-specific terminology and workflows.

5. **Include Analysis Phase**: Always include a phase for analyzing existing repository content before applying changes.

6. **Document Memory Files**: Provide clear guidance on what information should go into each memory file for your use case.

## Example Prompt Template

```
# [Title] Initialization Prompt

This prompt helps initialize the rules_template framework for [specific use case].

## Usage

Replace `{{VARIABLE}}` with [explanation].

```
[Complete prompt goes here]
```
```

## Contributing

When contributing new prompts:

1. Follow the structure and guidelines above
2. Make sure your prompt is thoroughly tested
3. Focus on specific, practical use cases
4. Submit a pull request with a clear description of the prompt's purpose and usage
