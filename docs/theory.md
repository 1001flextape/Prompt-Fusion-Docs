
# Prompt Fusion Documentation

## Overview
**Prompt Fusion** is a powerful tool designed to automate project generation through a structured, folder-based prompting system. It leverages the capabilities of Large Language Models (LLMs) to efficiently create files, manage changes, and debug potential issues, all while minimizing redundant generation.

### Two Phases of Operation:
1. **Planning Phase**: 
    - Users define the project structure and create prompts that guide the file generation process.
    
2. **Code Generation Phase**: 
    - Executes the defined prompts to generate code and documentation based on the specifications provided.

### Key Concepts:
- **Root Directory**: 
    - The main folder where the project is managed and organized. The engine operates only when the configuration file `config.prompt-fusion.json` is identified in this directory.
  
- **_prompts Folder**: 
    - A folder within each directory that triggers the engine to generate files based on defined prompts. Placing a `_prompts` folder in a directory begins the blueprinting process for file generation.
  
- **Redundant File Management**: 
    - Uses versioning or hashing to prevent unnecessary file generation, applying updates only when changes are detected.
  
- **Batch Processing**: 
    - Handles file generation in parallel to manage large-scale projects efficiently.

- **Debugging Robot**: 
    - The only AI with a complete view of the project. It verifies that all generated files align with documentation and resolves any issues detected during the generation process.

---

## Features

### Root Directory
- The root directory is the central location for project organization.
- The engine operates only when the `config.prompt-fusion.json` file is correctly identified in this directory.

### _prompts Folder
- To generate files within a folder, add a `_prompts` subfolder in that directory to blueprint the file generation.
  - **Purpose**: Contains instructions and context for generating files.
  - **Contents**: Includes prompt files and context documentation to aid in the generation process.

#### Example Structure:

```bash
project-root
│
├── config.prompt-fusion.json        # Configuration file for project settings
├── folder1                          # Random folder for the project
│   ├── _prompts                     # Folder containing prompts and related files (triggers the engine to create files in this directory)
│   │   ├── files                    # Directory containing prompt files
│   │   │   └── filename.prompt.md   # A markdown file that generates one file in folder1
│   │   └── context                  # Directory for context-related documentation
│   │       └── random_file_for_context.md  # Loads the context before generating files
```

---

### Configuration Options:

- **cascadeParentFolderContext**: 
    - A boolean option (defaults to `true`) that determines if context is loaded from parent `_prompts/context` directories. The context is loaded in the following order:
  
        1. `folder1/_prompts/context`
        2. `folder1/folder2/_prompts/context`
        3. `folder1/folder2/folder3/_prompts/context`

<!-- - **stackNewProjectOutput**: 
    - A boolean option (defaults to `false`) that specifies how projects are structured:
        - When set to `true`, the project is stored as a stack of folders.
        - When set to `false`, all files are merged into a single folder. -->

---

### File Generation Phases

1. **Plan Phase**: 
    - Users blueprint the project by creating directories and adding `_prompts` folders to locations where file generation is needed.

2. **Execute Phase**:
    - The engine processes each directory containing a `_prompts` folder, generating files according to the instructions.
    - Directories without a `_prompts` folder are skipped.
    - The system scans directories with `_prompts` folders and pushes tasks to a queue for processing.
    - Robots answer requests on the queue to scale up the speed of the build.
    - If files are modified, the engine ensures documentation is updated to keep everything in sync.
    - After processing, a debug robot reviews the project to resolve issues, using its full project view to ensure generated files meet the requirements.

## Workflow

1. **Initial Setup**: Define the root directory, create `_prompts` folders, and add prompt instructions.
2. **Generation**:
    - The engine runs through all `_prompts` folders and generates files.
    - Skips files that have not changed.
3. **Debugging**:
    - Auto-fixes any simple issues, prompts the user for complex errors, and logs the status.
4. **Final Output**: Once all files are generated and errors are resolved, the project is ready for use.

---

## Example Structure

Here’s a sample project folder structure using the Prompt Engine:

```
/my-project
  ├── /config.prompt-fusion.json
  ├── /src
  │    ├── app.ts
  │    └── /_prompts
  │        └── files
  │           └── app.ts.prompt.md
```

---

## Conclusion
The Prompt Engine streamlines the project generation process using a scalable, batch-oriented approach. With automated debugging, efficient file management, and user prompts, it ensures projects can be generated quickly and accurately.
