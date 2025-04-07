# VS Code Extensions for Python Development

This document describes the configured extensions to optimize the VS Code development environment for Python projects.

## 1. Python (Microsoft)
- **Purpose**: The official Python extension for VS Code that provides full support: IntelliSense, linting, debugging, navigation, and more.
- **Features**:
  - Autocompletion (IntelliSense)
  - Error detection and linting
  - Code navigation and refactoring
  - Jupyter notebook support
  - Python environment selection
- **How to Use**:
  - Install the extension from the VS Code Marketplace.
  - Select your Python interpreter using the command palette (`Ctrl+Shift+P` → `Python: Select Interpreter`).

## 2. Black Formatter
- **Purpose**: Automatically formats Python code following the Black style guide to maintain consistent code.
- **Features**:
  - Consistent formatting throughout the project.
  - Integration with VS Code for manual formatting (`Shift+Alt+F`) or automatic formatting on save.
- **How to Use**:
  - Install the Black Formatter extension or alternatively install Black in your environment using `pip install black`.
  - Configure in `settings.json`: `"python.formatting.provider": "black"`.

## 3. Pylint
- **Purpose**: Provides static analysis and linting to ensure adherence to Python coding standards (PEP8).
- **Features**:
  - Highlights potential errors and style issues.
  - Integrates with the VS Code Problems panel.
- **How to Use**:
  - Install Pylint in your environment with `pip install pylint`.
  - The Python extension in VS Code detects it automatically. You can adjust additional rules in the settings.

## 4. Pylance
- **Purpose**: A fast and robust IntelliSense and type checking provider for Python based on the Pyright static type checker.
- **Features**:
  - Real-time type checking.
  - Fast navigation through your code.
  - Automatic import suggestions.
- **How to Use**:
  - Install Pylance from the VS Code Marketplace.
  - (Optional) Ensure that `"python.languageServer": "Pylance"` is set in your `settings.json`.

## 5. Python Indent
- **Purpose**: Automatically corrects indentation in Python files, ensuring that the code is properly aligned.
- **Features**:
  - Fixes indentation errors when pasting code.
  - Automatically aligns code blocks.
- **How to Use**:
  - Install and enable the extension—it works automatically.

## 6. Python Docstring Generator
- **Purpose**: Automatically generates docstrings for functions, methods, and classes based on their signature.
- **Features**:
  - Supports multiple docstring formats (Google, NumPy, etc.).
  - Speeds up and simplifies code documentation.
- **How to Use**:
  - Place the cursor inside a function or class and trigger the command from the palette (`Ctrl+Shift+P` → `Generate Docstring`).

## 7. GitLens
- **Purpose**: Enhances VS Code's built-in Git capabilities by allowing you to view code history, see blame annotations, and more.
- **Features**:
  - Displays inline code authorship (Git blame).
  - Enables exploration of repository history and branches.
  - Provides detailed diff views and advanced change analysis.
- **How to Use**:
  - Install GitLens from the Marketplace.
  - Hover over a line of code to see author details or explore the history via the sidebar.

## 8. GitHub Pull Requests and Issues
- **Purpose**: Manage GitHub pull requests and issues directly within VS Code, making collaboration smoother.
- **Features**:
  - View and manage pull requests.
  - Browse and resolve issues.
  - Review and comment on PRs without leaving the editor.
- **How to Use**:
  - Install the extension and connect your GitHub account.
  - Use the source control panel to manage PRs and issues.

## 9. Beared Icons
- **Purpose**: Provides a set of sleek, distinctive icons (Beared Icons) to personalize the file and folder view in VS Code.
- **Features**:
  - Sharp, customized icons for better visual distinction.
  - Adds character and originality to your development environment.
- **How to Use**:
  - Install the [Beared Icons](https://marketplace.visualstudio.com/items?itemName=BeardedBear.beardedicons) extension from the Marketplace.
  - Go to `File → Preferences → File Icon Theme` and select "Beared Icons" as your icon theme.

## 10. Jupyter
- **Purpose**: Adds support for Jupyter Notebooks, allowing you to run and edit notebooks directly within VS Code.
- **Features**:
  - Open and edit `.ipynb` files natively.
  - Supports interactive plots and seamless integration with Python.
- **How to Use**:
  - Install the Jupyter extension.
  - Open a `.ipynb` file or create a new notebook using the command palette (`Ctrl+Shift+P` → `Jupyter: Create New Blank Notebook`).

---

This README details the extensions configured to optimize the VS Code environment for Python development. You can further customize your setup in the `settings.json` file to adjust formatting, linting, and other preferences as needed.

Hope this helps improve your workflow in VS Code!
