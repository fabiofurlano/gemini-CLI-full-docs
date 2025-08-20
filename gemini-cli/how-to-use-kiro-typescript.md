[Skip to content](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript#VPContent)

On this page

# How to Use Kiro (TypeScript/JavaScript) [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#how-to-use-kiro-typescript-javascript)

Kiro provides powerful AI-assisted development capabilities for TypeScript and JavaScript projects, helping you write, debug, and maintain code more efficiently. ![How to Use Kiro (TypeScript/JavaScript)](https://gemini-cli.xyz/docs/assets/kiro-typescript-cover.DFfF3FZX.svg)

## Prerequisites [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#prerequisites)

Before diving into TypeScript and JavaScript development with Kiro, ensure you have:

- **Node.js**: Install the latest version for your platform
- **TypeScript**: Install globally or locally in your project
- **Package Manager**: npm (comes with Node.js) or your preferred package manager
- **Git**: For version control and collaboration

## Suggested Extensions [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#suggested-extensions)

To enhance your TypeScript and JavaScript development experience with Kiro, consider installing these helpful extensions:

- **ESLint** \- Real-time code quality feedback and linting for JavaScript/TypeScript
- **Prettier - Code Formatter** \- Automatic code formatting for consistent style across your project
- **Auto Rename Tag** \- Automatically renames paired HTML/JSX tags when editing
- **JavaScript (ES6) code snippets** \- Provides useful code snippets for modern JavaScript and TypeScript development

## Working With Your Environment [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#working-with-your-environment)

### Project Configuration and Structure [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#project-configuration-and-structure)

Kiro can help you set up and maintain configuration files for your TypeScript and JavaScript projects, as well as organize your project following Kiro's best practices.

For example, you can ask Kiro:

- "Create a tsconfig.json for a React TypeScript project using ES6 modules"
- "Update my ESLint config to enforce React best practices"
- "Set up a monorepo structure for my frontend and backend TypeScript code"

### Code Analysis and Refactoring [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#code-analysis-and-refactoring)

Kiro can analyze your TypeScript and JavaScript code to identify issues and suggest improvements:

- **Code Quality Analysis**: Ask Kiro to review your code for potential bugs, performance issues, or style issues.
- **Refactoring Assistance**: Get help extracting functions, renaming variables, or restructuring code.
- **Type Inference**: Kiro can suggest TypeScript types based on your JavaScript code.

Example prompts:

- "Analyze this function for potential bugs"
- "Refactor this code to use async/await instead of promises"
- "Convert this JavaScript file to TypeScript with proper types"

### Debugging Assistance [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#debugging-assistance)

When you encounter errors in your TypeScript or JavaScript code:

- **Error Explanation**: Kiro can explain cryptic error messages in plain language
- **Solution Suggestions**: Kiro can suggest actionable fixes for common errors
- **Runtime Debugging**: Kiro can help set up debugging configurations

Examples:

- "Explain this TypeScript error: TS2339: Property 'value' does not exist on type 'never'"
- "Help me debug this React useEffect infinite loop"

## Steering [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#steering)

Steering allows you to provide Kiro with project specific context and guidelines. Kiro can generate steering files which you can refine:

- **Product brief** ( `product.md`) \- Contains information about the product, its purpose, and key features
- **Technical Stack** ( `tech.md`) \- Details the technologies, frameworks, and development guidelines
- **Project Structure** ( `structure.md`) \- Provides information about how the project is organized

For TypeScript and JavaScript projects, you can create additional custom steering files to provide more specific guidance.

### Creating Custom Steering Files [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#creating-custom-steering-files)

Use the following instructions to add new steering documents to your project.

**To add new steering documents:**

1. Navigate to the **Kiro** view in the sidebar.
2. In the **Agent Steering** section, choose the `+` button to create a new steering file.
3. Enter a name for your file with a descriptive title.
4. Add your custom steering content following markdown conventions.

Custom steering files are stored in the `.kiro/steering/` directory and are automatically recognized by Kiro during interactions.

### Code Style and Conventions [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#code-style-and-conventions)

You can define custom naming conventions, file structure, or practices for your project.

You can create a `js-conventions.md` steering file to define your team's coding standards:

markdown

```
# TypeScript/JavaScript Conventions

## Naming Conventions
- Use camelCase for variables and functions
- Use PascalCase for classes and React components
- Use UPPER_SNAKE_CASE for constants

## File Structure
- One component per file
- Group related components in folders
- Use index.ts files for exports

## TypeScript Practices
- Prefer interfaces over types for public APIs
- Use explicit return types for exported functions
- Avoid using 'any' type
```

### Framework Specific Guidelines [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#framework-specific-guidelines)

For React projects, you can create a `react-patterns.md` steering file:

markdown

```
# React Development Guidelines

## Component Structure
- Use functional components with hooks
- Separate business logic from UI components
- Follow the container/presentational pattern

## State Management
- Use React Context for global state
- Prefer useState for local component state
- Use useReducer for complex state logic

## Performance Optimization
- Memoize expensive calculations with useMemo
- Prevent unnecessary re-renders with React.memo
- Use useCallback for event handlers passed to child components
```

These steering files help Kiro generate code that follows your team's specific conventions and best practices.

## Agent Hooks [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#agent-hooks)

Kiro's Agent Hooks can automate common TypeScript and JavaScript development tasks:

1. Navigate to the **Agent Hooks** section in the Kiro panel
2. Click the `+` button to create a new hook
3. Define the hook workflow in natural language

Here are some hook examples:

### Test Generation Hook [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#test-generation-hook)

You can automatically generate tests when you save a TypeScript or JavaScript file:

"Create a hook that generates Jest tests when I save a new component"

### Type Checking Hook [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#type-checking-hook)

You can run TypeScript type checking in the background:

"Set up a hook to run TypeScript type checking when I save files"

### Dependency Update Hook [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#dependency-update-hook)

You can keep your dependencies up to date:

"Create a hook that checks for outdated npm packages"

### ESLint Auto-Fix Hook [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#eslint-auto-fix-hook)

When a JavaScript or TypeScript file is saved:

1. Run ESLint with auto-fix on the file
2. Report any remaining issues that couldn't be fixed automatically
3. Suggest fixes for complex issues

### Component Documentation Hook [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#component-documentation-hook)

When a React component file is saved:

1. Extract the component's props interface
2. Update or create a documentation comment above the component
3. Generate usage examples based on the props
4. Update the component's README.md if it exists

## MCP Servers [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#mcp-servers)

Kiro's support for Model Context Protocol (MCP) servers enhance your TypeScript and JavaScript development experience by providing specialized tools and capabilities. For a complete guide on setting up and using MCP, see the MCP documentation.

### Frontend MCP Server [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#frontend-mcp-server)

The AWS Labs Frontend MCP Server provides specialized tools for modern web application development, offering comprehensive documentation and guidance for React applications:

json

```
{
  "mcpServers": {
    "frontend": {
      "command": "uvx",
      "args": ["awslabs.frontend-mcp-server@latest"],
      "env": {
        "FASTMCP_LOG_LEVEL": "ERROR"
      }
    }
  }
}
```

Example usage:

- "Get essential knowledge for React development"
- "Help me troubleshoot this React component issue"
- "Show me best practices for modern React applications"

Explore more MCP servers in the AWS MCP Servers and Awesome MCP Servers collection.

## Documentation Access with \#docs [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#documentation-access-with-docs)

Kiro provides built-in access to documentation for JavaScript, TypeScript, and popular frameworks through the `#docs` reference system. This allows you to quickly bring relevant documentation into your conversations with Kiro. Simply type `#docs` in the chat and select from the available documentation sources, such as:

- **#Node.js** \- Node.js runtime documentation
- **#TypeScript** \- TypeScript language documentation
- **#React** \- React library documentation
- **#Svelte** \- Svelte framework documentation
- **#Express** \- Express.js framework documentation
- **#Vue.js** \- Vue.js framework documentation
- **#Alpine.js** \- Alpine.js framework documentation

Example usage:

- "#TypeScript How do I create a generic function?"
- "#React What's the best way to handle form state?"

You can also reference specific documentation URLs using `#URL`:

"#URL [https://react.dev/reference/react/useState](https://react.dev/reference/react/useState)"

## Debugging Issues [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#debugging-issues)

When you encounter issues, Kiro can help diagnose and fix them:

1. **Inline Chat**:

   - Type `Cmd/Ctrl + I` to open the inline chat.
   - Ask Kiro to help debug your code with natural language.
2. **Add to Chat**:

   - Type `Cmd/Ctrl + L` to add the current file to the chat.
   - Ask Kiro to help debug your code with natural language.
3. **Quick Fix**:

   - Hover on an error or warning, then select `Quick fix` and `Ask Kiro`.
   - Kiro will automatically add the code to the chat and start debugging.

## Resources [​](https://gemini-cli.xyz/docs/en/how-to-use-kiro-typescript\#resources)

- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [JavaScript MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Node.js Documentation](https://nodejs.org/en/docs/)