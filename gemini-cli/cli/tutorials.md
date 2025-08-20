[Skip to content](https://gemini-cli.xyz/docs/en/cli/tutorials#VPContent)

On this page

# Tutorials [​](https://gemini-cli.xyz/docs/en/cli/tutorials\#tutorials)

This page contains tutorials for interacting with Gemini CLI.

## Setting up a Model Context Protocol (MCP) server [​](https://gemini-cli.xyz/docs/en/cli/tutorials\#setting-up-a-model-context-protocol-mcp-server)

CAUTION

Before using a third-party MCP server, ensure you trust its source and understand the tools it provides. Your use of third-party servers is at your own risk.

This tutorial demonstrates how to set up a MCP server, using the [GitHub MCP server](https://github.com/github/github-mcp-server) as an example. The GitHub MCP server provides tools for interacting with GitHub repositories, such as creating issues and commenting on pull requests.

### Prerequisites [​](https://gemini-cli.xyz/docs/en/cli/tutorials\#prerequisites)

Before you begin, ensure you have the following installed and configured:

- **Docker:** Install and run [Docker](https://www.docker.com/).
- **GitHub Personal Access Token (PAT):** Create a new [classic](https://github.com/settings/tokens/new) or [fine-grained](https://github.com/settings/personal-access-tokens/new) PAT with the necessary scopes.

### Guide [​](https://gemini-cli.xyz/docs/en/cli/tutorials\#guide)

#### Configure the MCP server in `settings.json` [​](https://gemini-cli.xyz/docs/en/cli/tutorials\#configure-the-mcp-server-in-settings-json)

In your project's root directory, create or open the [`.gemini/settings.json` file](https://gemini-cli.xyz/docs/en/cli/configuration). Within the file, add the `mcpServers` configuration block, which provides instructions for how to launch the GitHub MCP server.

json

```
{
  "mcpServers": {
    "github": {
      "command": "docker",
      "args": [\
        "run",\
        "-i",\
        "--rm",\
        "-e",\
        "GITHUB_PERSONAL_ACCESS_TOKEN",\
        "ghcr.io/github/github-mcp-server"\
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_PERSONAL_ACCESS_TOKEN}"
      }
    }
  }
}
```

#### Set your GitHub token [​](https://gemini-cli.xyz/docs/en/cli/tutorials\#set-your-github-token)

CAUTION

Using a broadly scoped personal access token that has access to personal and private repositories can lead to information from the private repository being leaked into the public repository. We recommend using a fine-grained access token that doesn't share access to both public and private repositories.

Use an environment variable to store your GitHub PAT:

bash

```
GITHUB_PERSONAL_ACCESS_TOKEN="pat_YourActualGitHubTokenHere"
```

Gemini CLI uses this value in the `mcpServers` configuration that you defined in the `settings.json` file.

#### Launch Gemini CLI and verify the connection [​](https://gemini-cli.xyz/docs/en/cli/tutorials\#launch-gemini-cli-and-verify-the-connection)

When you launch Gemini CLI, it automatically reads your configuration and launches the GitHub MCP server in the background. You can then use natural language prompts to ask Gemini CLI to perform GitHub actions. For example:

bash

```
"get all open issues assigned to me in the 'foo/bar' repo and prioritize them"
```