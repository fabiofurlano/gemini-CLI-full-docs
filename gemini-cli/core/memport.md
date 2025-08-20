[Skip to content](https://gemini-cli.xyz/docs/en/core/memport#VPContent)

On this page

# Memory Import Processor [​](https://gemini-cli.xyz/docs/en/core/memport\#memory-import-processor)

The Memory Import Processor is a feature that allows you to modularize your GEMINI.md files by importing content from other files using the `@file.md` syntax.

## Overview [​](https://gemini-cli.xyz/docs/en/core/memport\#overview)

This feature enables you to break down large GEMINI.md files into smaller, more manageable components that can be reused across different contexts. The import processor supports both relative and absolute paths, with built-in safety features to prevent circular imports and ensure file access security.

## Syntax [​](https://gemini-cli.xyz/docs/en/core/memport\#syntax)

Use the `@` symbol followed by the path to the file you want to import:

markdown

```
# Main GEMINI.md file

This is the main content.

@./components/instructions.md

More content here.

@./shared/configuration.md
```

## Supported Path Formats [​](https://gemini-cli.xyz/docs/en/core/memport\#supported-path-formats)

### Relative Paths [​](https://gemini-cli.xyz/docs/en/core/memport\#relative-paths)

- `@./file.md` \- Import from the same directory
- `@../file.md` \- Import from parent directory
- `@./components/file.md` \- Import from subdirectory

### Absolute Paths [​](https://gemini-cli.xyz/docs/en/core/memport\#absolute-paths)

- `@/absolute/path/to/file.md` \- Import using absolute path

## Examples [​](https://gemini-cli.xyz/docs/en/core/memport\#examples)

### Basic Import [​](https://gemini-cli.xyz/docs/en/core/memport\#basic-import)

markdown

```
# My GEMINI.md

Welcome to my project!

@./getting-started.md

## Features

@./features/overview.md
```

### Nested Imports [​](https://gemini-cli.xyz/docs/en/core/memport\#nested-imports)

The imported files can themselves contain imports, creating a nested structure:

markdown

```
# main.md

@./header.md
@./content.md
@./footer.md
```

markdown

```
# header.md

# Project Header

@./shared/title.md
```

## Safety Features [​](https://gemini-cli.xyz/docs/en/core/memport\#safety-features)

### Circular Import Detection [​](https://gemini-cli.xyz/docs/en/core/memport\#circular-import-detection)

The processor automatically detects and prevents circular imports:

markdown

```
# file-a.md

@./file-b.md

# file-b.md

@./file-a.md <!-- This will be detected and prevented -->
```

### File Access Security [​](https://gemini-cli.xyz/docs/en/core/memport\#file-access-security)

The `validateImportPath` function ensures that imports are only allowed from specified directories, preventing access to sensitive files outside the allowed scope.

### Maximum Import Depth [​](https://gemini-cli.xyz/docs/en/core/memport\#maximum-import-depth)

To prevent infinite recursion, there's a configurable maximum import depth (default: 5 levels).

## Error Handling [​](https://gemini-cli.xyz/docs/en/core/memport\#error-handling)

### Missing Files [​](https://gemini-cli.xyz/docs/en/core/memport\#missing-files)

If a referenced file doesn't exist, the import will fail gracefully with an error comment in the output.

### File Access Errors [​](https://gemini-cli.xyz/docs/en/core/memport\#file-access-errors)

Permission issues or other file system errors are handled gracefully with appropriate error messages.

## Code Region Detection [​](https://gemini-cli.xyz/docs/en/core/memport\#code-region-detection)

The import processor uses the `marked` library to detect code blocks and inline code spans, ensuring that `@` imports inside these regions are properly ignored. This provides robust handling of nested code blocks and complex Markdown structures.

## Import Tree Structure [​](https://gemini-cli.xyz/docs/en/core/memport\#import-tree-structure)

The processor returns an import tree that shows the hierarchy of imported files, similar to Claude's `/memory` feature. This helps users debug problems with their GEMINI.md files by showing which files were read and their import relationships.

Example tree structure:

```
Memory Files
 L project: GEMINI.md
            L a.md
              L b.md
                L c.md
              L d.md
                L e.md
                  L f.md
            L included.md
```

The tree preserves the order that files were imported and shows the complete import chain for debugging purposes.

## Comparison to Claude Code's `/memory` ( `claude.md`) Approach [​](https://gemini-cli.xyz/docs/en/core/memport\#comparison-to-claude-code-s-memory-claude-md-approach)

Claude Code's `/memory` feature (as seen in `claude.md`) produces a flat, linear document by concatenating all included files, always marking file boundaries with clear comments and path names. It does not explicitly present the import hierarchy, but the LLM receives all file contents and paths, which is sufficient for reconstructing the hierarchy if needed.

Note: The import tree is mainly for clarity during development and has limited relevance to LLM consumption.

## API Reference [​](https://gemini-cli.xyz/docs/en/core/memport\#api-reference)

### `processImports(content, basePath, debugMode?, importState?)` [​](https://gemini-cli.xyz/docs/en/core/memport\#processimports-content-basepath-debugmode-importstate)

Processes import statements in GEMINI.md content.

**Parameters:**

- `content` (string): The content to process for imports
- `basePath` (string): The directory path where the current file is located
- `debugMode` (boolean, optional): Whether to enable debug logging (default: false)
- `importState` (ImportState, optional): State tracking for circular import prevention

**Returns:** Promise<ProcessImportsResult> - Object containing processed content and import tree

### `ProcessImportsResult` [​](https://gemini-cli.xyz/docs/en/core/memport\#processimportsresult)

typescript

```
interface ProcessImportsResult {
  content: string; // The processed content with imports resolved
  importTree: MemoryFile; // Tree structure showing the import hierarchy
}
```

### `MemoryFile` [​](https://gemini-cli.xyz/docs/en/core/memport\#memoryfile)

typescript

```
interface MemoryFile {
  path: string; // The file path
  imports?: MemoryFile[]; // Direct imports, in the order they were imported
}
```

### `validateImportPath(importPath, basePath, allowedDirectories)` [​](https://gemini-cli.xyz/docs/en/core/memport\#validateimportpath-importpath-basepath-alloweddirectories)

Validates import paths to ensure they are safe and within allowed directories.

**Parameters:**

- `importPath` (string): The import path to validate
- `basePath` (string): The base directory for resolving relative paths
- `allowedDirectories` (string\[\]): Array of allowed directory paths

**Returns:** boolean - Whether the import path is valid

### `findProjectRoot(startDir)` [​](https://gemini-cli.xyz/docs/en/core/memport\#findprojectroot-startdir)

Finds the project root by searching for a `.git` directory upwards from the given start directory. Implemented as an **async** function using non-blocking file system APIs to avoid blocking the Node.js event loop.

**Parameters:**

- `startDir` (string): The directory to start searching from

**Returns:** Promise<string> - The project root directory (or the start directory if no `.git` is found)

## Best Practices [​](https://gemini-cli.xyz/docs/en/core/memport\#best-practices)

1. **Use descriptive file names** for imported components
2. **Keep imports shallow** \- avoid deeply nested import chains
3. **Document your structure** \- maintain a clear hierarchy of imported files
4. **Test your imports** \- ensure all referenced files exist and are accessible
5. **Use relative paths** when possible for better portability

## Troubleshooting [​](https://gemini-cli.xyz/docs/en/core/memport\#troubleshooting)

### Common Issues [​](https://gemini-cli.xyz/docs/en/core/memport\#common-issues)

1. **Import not working**: Check that the file exists and the path is correct
2. **Circular import warnings**: Review your import structure for circular references
3. **Permission errors**: Ensure the files are readable and within allowed directories
4. **Path resolution issues**: Use absolute paths if relative paths aren't resolving correctly

### Debug Mode [​](https://gemini-cli.xyz/docs/en/core/memport\#debug-mode)

Enable debug mode to see detailed logging of the import process:

typescript

```
const result = await processImports(content, basePath, true);
```