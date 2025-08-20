[Skip to content](https://gemini-cli.xyz/docs/en/sandbox#VPContent)

On this page

# Sandboxing in the Gemini CLI [​](https://gemini-cli.xyz/docs/en/sandbox\#sandboxing-in-the-gemini-cli)

This document provides a guide to sandboxing in the Gemini CLI, including prerequisites, quickstart, and configuration.

## Prerequisites [​](https://gemini-cli.xyz/docs/en/sandbox\#prerequisites)

Before using sandboxing, you need to install and set up the Gemini CLI:

bash

```
npm install -g @google/gemini-cli
```

To verify the installation

bash

```
gemini --version
```

## Overview of sandboxing [​](https://gemini-cli.xyz/docs/en/sandbox\#overview-of-sandboxing)

Sandboxing isolates potentially dangerous operations (such as shell commands or file modifications) from your host system, providing a security barrier between AI operations and your environment.

The benefits of sandboxing include:

- **Security**: Prevent accidental system damage or data loss.
- **Isolation**: Limit file system access to project directory.
- **Consistency**: Ensure reproducible environments across different systems.
- **Safety**: Reduce risk when working with untrusted code or experimental commands.

## Sandboxing methods [​](https://gemini-cli.xyz/docs/en/sandbox\#sandboxing-methods)

Your ideal method of sandboxing may differ depending on your platform and your preferred container solution.

### 1\. macOS Seatbelt (macOS only) [​](https://gemini-cli.xyz/docs/en/sandbox\#_1-macos-seatbelt-macos-only)

Lightweight, built-in sandboxing using `sandbox-exec`.

**Default profile**: `permissive-open` \- restricts writes outside project directory but allows most other operations.

### 2\. Container-based (Docker/Podman) [​](https://gemini-cli.xyz/docs/en/sandbox\#_2-container-based-docker-podman)

Cross-platform sandboxing with complete process isolation.

**Note**: Requires building the sandbox image locally or using a published image from your organization's registry.

## Quickstart [​](https://gemini-cli.xyz/docs/en/sandbox\#quickstart)

bash

```
# Enable sandboxing with command flag
gemini -s -p "analyze the code structure"

# Use environment variable
export GEMINI_SANDBOX=true
gemini -p "run the test suite"

# Configure in settings.json
{
  "sandbox": "docker"
}
```

## Configuration [​](https://gemini-cli.xyz/docs/en/sandbox\#configuration)

### Enable sandboxing (in order of precedence) [​](https://gemini-cli.xyz/docs/en/sandbox\#enable-sandboxing-in-order-of-precedence)

1. **Command flag**: `-s` or `--sandbox`
2. **Environment variable**: `GEMINI_SANDBOX=true|docker|podman|sandbox-exec`
3. **Settings file**: `"sandbox": true` in `settings.json`

### macOS Seatbelt profiles [​](https://gemini-cli.xyz/docs/en/sandbox\#macos-seatbelt-profiles)

Built-in profiles (set via `SEATBELT_PROFILE` env var):

- `permissive-open` (default): Write restrictions, network allowed
- `permissive-closed`: Write restrictions, no network
- `permissive-proxied`: Write restrictions, network via proxy
- `restrictive-open`: Strict restrictions, network allowed
- `restrictive-closed`: Maximum restrictions

### Custom Sandbox Flags [​](https://gemini-cli.xyz/docs/en/sandbox\#custom-sandbox-flags)

For container-based sandboxing, you can inject custom flags into the `docker` or `podman` command using the `SANDBOX_FLAGS` environment variable. This is useful for advanced configurations, such as disabling security features for specific use cases.

**Example (Podman)**:

To disable SELinux labeling for volume mounts, you can set the following:

bash

```
export SANDBOX_FLAGS="--security-opt label=disable"
```

Multiple flags can be provided as a space-separated string:

bash

```
export SANDBOX_FLAGS="--flag1 --flag2=value"
```

## Linux UID/GID handling [​](https://gemini-cli.xyz/docs/en/sandbox\#linux-uid-gid-handling)

The sandbox automatically handles user permissions on Linux. Override these permissions with:

bash

```
export SANDBOX_SET_UID_GID=true   # Force host UID/GID
export SANDBOX_SET_UID_GID=false  # Disable UID/GID mapping
```

## Troubleshooting [​](https://gemini-cli.xyz/docs/en/sandbox\#troubleshooting)

### Common issues [​](https://gemini-cli.xyz/docs/en/sandbox\#common-issues)

**"Operation not permitted"**

- Operation requires access outside sandbox.
- Try more permissive profile or add mount points.

**Missing commands**

- Add to custom Dockerfile.
- Install via `sandbox.bashrc`.

**Network issues**

- Check sandbox profile allows network.
- Verify proxy configuration.

### Debug mode [​](https://gemini-cli.xyz/docs/en/sandbox\#debug-mode)

bash

```
DEBUG=1 gemini -s -p "debug command"
```

**Note:** If you have `DEBUG=true` in a project's `.env` file, it won't affect gemini-cli due to automatic exclusion. Use `.gemini/.env` files for gemini-cli specific debug settings.

### Inspect sandbox [​](https://gemini-cli.xyz/docs/en/sandbox\#inspect-sandbox)

bash

```
# Check environment
gemini -s -p "run shell command: env | grep SANDBOX"

# List mounts
gemini -s -p "run shell command: mount | grep workspace"
```

## Security notes [​](https://gemini-cli.xyz/docs/en/sandbox\#security-notes)

- Sandboxing reduces but doesn't eliminate all risks.
- Use the most restrictive profile that allows your work.
- Container overhead is minimal after first build.
- GUI applications may not work in sandboxes.

## Related documentation [​](https://gemini-cli.xyz/docs/en/sandbox\#related-documentation)

- [Configuration](https://gemini-cli.xyz/docs/en/cli/configuration): Full configuration options.
- [Commands](https://gemini-cli.xyz/docs/en/cli/commands): Available commands.
- [Troubleshooting](https://gemini-cli.xyz/docs/en/troubleshooting): General troubleshooting.