[Skip to content](https://gemini-cli.xyz/docs/en/tools/memory#VPContent)

On this page

# Memory Tool ( `save_memory`) [​](https://gemini-cli.xyz/docs/en/tools/memory\#memory-tool-save-memory)

This document describes the `save_memory` tool for the Gemini CLI.

## Description [​](https://gemini-cli.xyz/docs/en/tools/memory\#description)

Use `save_memory` to save and recall information across your Gemini CLI sessions. With `save_memory`, you can direct the CLI to remember key details across sessions, providing personalized and directed assistance.

### Arguments [​](https://gemini-cli.xyz/docs/en/tools/memory\#arguments)

`save_memory` takes one argument:

- `fact` (string, required): The specific fact or piece of information to remember. This should be a clear, self-contained statement written in natural language.

## How to use `save_memory` with the Gemini CLI [​](https://gemini-cli.xyz/docs/en/tools/memory\#how-to-use-save-memory-with-the-gemini-cli)

The tool appends the provided `fact` to a special `GEMINI.md` file located in the user's home directory ( `~/.gemini/GEMINI.md`). This file can be configured to have a different name.

Once added, the facts are stored under a `## Gemini Added Memories` section. This file is loaded as context in subsequent sessions, allowing the CLI to recall the saved information.

Usage:

```
save_memory(fact="Your fact here.")
```

### `save_memory` examples [​](https://gemini-cli.xyz/docs/en/tools/memory\#save-memory-examples)

Remember a user preference:

```
save_memory(fact="My preferred programming language is Python.")
```

Store a project-specific detail:

```
save_memory(fact="The project I'm currently working on is called 'gemini-cli'.")
```

## Important notes [​](https://gemini-cli.xyz/docs/en/tools/memory\#important-notes)

- **General usage:** This tool should be used for concise, important facts. It is not intended for storing large amounts of data or conversational history.
- **Memory file:** The memory file is a plain text Markdown file, so you can view and edit it manually if needed.