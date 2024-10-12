
## Command Line Documentation for Prompt Fusion

### Commands Overview

Prompt Fusion operates in two primary phases: **Plan Phase** and **Code Generation Phase**. Each phase is triggered by specific commands designed to maximize project creation efficiency.

---

### General Command

```bash
prompt-fusion
```
- **Purpose**: This is the smallest command that runs the **Plan Phase**. It initiates the browser-based planning tool, allowing users to define project structures and create `_prompts` folders with contents.
- **Details**: It launches the browser interface for folder and file configuration.

---

### Code Generation Command

```bash
prompt-fusion run
```
- **Purpose**: This command executes the **Code Generation Phase**. It processes the prompts defined in the `_prompts` folders, generates the necessary files, and updates the project structure based on these blueprints.
- **Details**:
  - Executes file generation only within folders containing `_prompts`.
  - Efficiently skips files that haven’t changed, preventing redundant generation.
  - Ensures that generated files adhere to the defined structure and documentation.

---

### Subfolder-Specific Code Generation

```bash
prompt-fusion run --path <subfolder>
```
- **Purpose**: Allows you to run the **Code Generation Phase** in a specific subfolder.
- **Details**:
  - The engine will only generate files within the specified folder and its child directories.
  - Useful for generating files in a portion of the project without triggering the entire root directory.

---

## Example Workflow

1. **Plan Phase**: 
   - Run `prompt-fusion` to open the planning GUI.
   - Define your project’s structure, create `_prompts` folders, and configure file generation logic.

2. **Code Generation Phase**:
   - Run `prompt-fusion run` to trigger the code generation for your entire project.
   - Use `prompt-fusion run --path <subfolder>` to generate files only within a specific subfolder.

   a. **Parallel Processing**:
      - Files are processed in parallel for efficient generation.
      
   b. **Debugging**:
      - After the Code Generation Phase, any issues found by the debug robot are either auto-fixed or flagged for user intervention.

---

### Conclusion

Prompt Fusion’s command structure is designed for simplicity and efficiency, with the ability to scale project generation seamlessly, using concepts like parallel processing, cascading contexts, and auto-debugging inspired by successful patterns from Jest.
