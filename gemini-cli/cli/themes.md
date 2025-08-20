[Skip to content](https://gemini-cli.xyz/docs/en/cli/themes#VPContent)

On this page

# Themes [​](https://gemini-cli.xyz/docs/en/cli/themes\#themes)

Gemini CLI supports a variety of themes to customize its color scheme and appearance. You can change the theme to suit your preferences via the `/theme` command or `"theme":` configuration setting.

## Available Themes [​](https://gemini-cli.xyz/docs/en/cli/themes\#available-themes)

Gemini CLI comes with a selection of pre-defined themes, which you can list using the `/theme` command within Gemini CLI:

- **Dark Themes:**
  - `ANSI`
  - `Atom One`
  - `Ayu`
  - `Default`
  - `Dracula`
  - `GitHub`
- **Light Themes:**
  - `ANSI Light`
  - `Ayu Light`
  - `Default Light`
  - `GitHub Light`
  - `Google Code`
  - `Xcode`

### Changing Themes [​](https://gemini-cli.xyz/docs/en/cli/themes\#changing-themes)

1. Enter `/theme` into Gemini CLI.
2. A dialog or selection prompt appears, listing the available themes.
3. Using the arrow keys, select a theme. Some interfaces might offer a live preview or highlight as you select.
4. Confirm your selection to apply the theme.

### Theme Persistence [​](https://gemini-cli.xyz/docs/en/cli/themes\#theme-persistence)

Selected themes are saved in Gemini CLI's [configuration](https://gemini-cli.xyz/docs/en/cli/configuration) so your preference is remembered across sessions.

* * *

## Custom Color Themes [​](https://gemini-cli.xyz/docs/en/cli/themes\#custom-color-themes)

Gemini CLI allows you to create your own custom color themes by specifying them in your `settings.json` file. This gives you full control over the color palette used in the CLI.

### How to Define a Custom Theme [​](https://gemini-cli.xyz/docs/en/cli/themes\#how-to-define-a-custom-theme)

Add a `customThemes` block to your user, project, or system `settings.json` file. Each custom theme is defined as an object with a unique name and a set of color keys. For example:

json

```
{
  "customThemes": {
    "MyCustomTheme": {
      "name": "MyCustomTheme",
      "type": "custom",
      "Background": "#181818",
      "Foreground": "#F8F8F2",
      "LightBlue": "#82AAFF",
      "AccentBlue": "#61AFEF",
      "AccentPurple": "#C678DD",
      "AccentCyan": "#56B6C2",
      "AccentGreen": "#98C379",
      "AccentYellow": "#E5C07B",
      "AccentRed": "#E06C75",
      "Comment": "#5C6370",
      "Gray": "#ABB2BF",
      "DiffAdded": "#A6E3A1",
      "DiffRemoved": "#F38BA8",
      "DiffModified": "#89B4FA",
      "GradientColors": ["#4796E4", "#847ACE", "#C3677F"]
    }
  }
}
```

**Color keys:**

- `Background`
- `Foreground`
- `LightBlue`
- `AccentBlue`
- `AccentPurple`
- `AccentCyan`
- `AccentGreen`
- `AccentYellow`
- `AccentRed`
- `Comment`
- `Gray`
- `DiffAdded` (optional, for added lines in diffs)
- `DiffRemoved` (optional, for removed lines in diffs)
- `DiffModified` (optional, for modified lines in diffs)

**Required Properties:**

- `name` (must match the key in the `customThemes` object and be a string)
- `type` (must be the string `"custom"`)
- `Background`
- `Foreground`
- `LightBlue`
- `AccentBlue`
- `AccentPurple`
- `AccentCyan`
- `AccentGreen`
- `AccentYellow`
- `AccentRed`
- `Comment`
- `Gray`

You can use either hex codes (e.g., `#FF0000`) **or** standard CSS color names (e.g., `coral`, `teal`, `blue`) for any color value. See [CSS color names](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value#color_keywords) for a full list of supported names.

You can define multiple custom themes by adding more entries to the `customThemes` object.

### Example Custom Theme [​](https://gemini-cli.xyz/docs/en/cli/themes\#example-custom-theme)

![Custom theme example](https://gemini-cli.xyz/docs/assets/theme-custom.8rbAfpr6.png)

### Using Your Custom Theme [​](https://gemini-cli.xyz/docs/en/cli/themes\#using-your-custom-theme)

- Select your custom theme using the `/theme` command in Gemini CLI. Your custom theme will appear in the theme selection dialog.
- Or, set it as the default by adding `"theme": "MyCustomTheme"` to your `settings.json`.
- Custom themes can be set at the user, project, or system level, and follow the same [configuration precedence](https://gemini-cli.xyz/docs/en/cli/configuration) as other settings.

* * *

## Dark Themes [​](https://gemini-cli.xyz/docs/en/cli/themes\#dark-themes)

### ANSI [​](https://gemini-cli.xyz/docs/en/cli/themes\#ansi)

![ANSI theme](https://gemini-cli.xyz/docs/assets/theme-ansi.pCBSEPdC.png)

### Atom OneDark [​](https://gemini-cli.xyz/docs/en/cli/themes\#atom-onedark)

![Atom One theme](https://gemini-cli.xyz/docs/assets/theme-atom-one.PNX31oDm.png)

### Ayu [​](https://gemini-cli.xyz/docs/en/cli/themes\#ayu)

![Ayu theme](https://gemini-cli.xyz/docs/assets/theme-ayu.CF47LzuE.png)

### Default [​](https://gemini-cli.xyz/docs/en/cli/themes\#default)

![Default theme](https://gemini-cli.xyz/docs/assets/theme-default.B6dwzAzm.png)

### Dracula [​](https://gemini-cli.xyz/docs/en/cli/themes\#dracula)

![Dracula theme](https://gemini-cli.xyz/docs/assets/theme-dracula.cpPSsK_a.png)

### GitHub [​](https://gemini-cli.xyz/docs/en/cli/themes\#github)

![GitHub theme](https://gemini-cli.xyz/docs/assets/theme-github.BpWi5Qop.png)

## Light Themes [​](https://gemini-cli.xyz/docs/en/cli/themes\#light-themes)

### ANSI Light [​](https://gemini-cli.xyz/docs/en/cli/themes\#ansi-light)

![ANSI Light theme](https://gemini-cli.xyz/docs/assets/theme-ansi-light.Cnac_xgp.png)

### Ayu Light [​](https://gemini-cli.xyz/docs/en/cli/themes\#ayu-light)

![Ayu Light theme](https://gemini-cli.xyz/docs/assets/theme-ayu-light.CA4JUp9p.png)

### Default Light [​](https://gemini-cli.xyz/docs/en/cli/themes\#default-light)

![Default Light theme](https://gemini-cli.xyz/docs/assets/theme-default-light.BAWb3fen.png)

### GitHub Light [​](https://gemini-cli.xyz/docs/en/cli/themes\#github-light)

![GitHub Light theme](https://gemini-cli.xyz/docs/assets/theme-github-light.Yq7OLHGL.png)

### Google Code [​](https://gemini-cli.xyz/docs/en/cli/themes\#google-code)

![Google Code theme](https://gemini-cli.xyz/docs/assets/theme-google-light.Bo1oTaQ8.png)

### Xcode [​](https://gemini-cli.xyz/docs/en/cli/themes\#xcode)

![Xcode Light theme](https://gemini-cli.xyz/docs/assets/theme-xcode-light.CuI5pPvp.png)