[Skip to content](https://gemini-cli.xyz/docs/en/cli/#VPContent)

On this page

# Gemini CLI [​](https://gemini-cli.xyz/docs/en/cli/\#gemini-cli)

Within Gemini CLI, `packages/cli` is the frontend for users to send and receive prompts with the Gemini AI model and its associated tools. For a general overview of Gemini CLI, see the [main documentation page](https://gemini-cli.xyz/docs/en/).

## Navigating this section [​](https://gemini-cli.xyz/docs/en/cli/\#navigating-this-section)

- **[Authentication](https://gemini-cli.xyz/docs/en/cli/authentication):** A guide to setting up authentication with Google's AI services.
- **[Commands](https://gemini-cli.xyz/docs/en/cli/commands):** A reference for Gemini CLI commands (e.g., `/help`, `/tools`, `/theme`).
- **[Configuration](https://gemini-cli.xyz/docs/en/cli/configuration):** A guide to tailoring Gemini CLI behavior using configuration files.
- **[Token Caching](https://gemini-cli.xyz/docs/en/cli/token-caching):** Optimize API costs through token caching.
- **[Themes](https://gemini-cli.xyz/docs/en/cli/themes)**: A guide to customizing the CLI's appearance with different themes.
- **[Tutorials](https://gemini-cli.xyz/docs/en/cli/tutorials)**: A tutorial showing how to use Gemini CLI to automate a development task.

## Non-interactive mode [​](https://gemini-cli.xyz/docs/en/cli/\#non-interactive-mode)

Gemini CLI can be run in a non-interactive mode, which is useful for scripting and automation. In this mode, you pipe input to the CLI, it executes the command, and then it exits.

The following example pipes a command to Gemini CLI from your terminal:

bash

```
echo "What is fine tuning?" | gemini
```

Gemini CLI executes the command and prints the output to your terminal. Note that you can achieve the same behavior by using the `--prompt` or `-p` flag. For example:

bash

```
gemini -p "What is fine tuning?"
```