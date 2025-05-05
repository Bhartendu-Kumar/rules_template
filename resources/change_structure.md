in this file we will architect the change framework, when new changes are requested.

# RooCode
## Changes in System Prompt of Roo-Code
1. We have to change the files in `.roo/` directory

## Adding new mode
1. System prompts in `.roo/` directory in section `MODES` (every file in `.roo/` directory has a section `MODES`)
2. The Capabilities section of each system prompt, has mode specific information for switch modes.
