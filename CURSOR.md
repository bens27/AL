# Developing with Cursor

This repository is configured for [Cursor](https://cursor.com), an AI-powered editor built on VS Code. You get the same AL Language tooling as VS Code, plus AI assistance tuned for AL development.

## Quick Start

1. **Open in Cursor** — Open this folder or a sample subfolder (e.g., `samples/HelloWorld`).
2. **Install the AL Language extension** — See [Install the AL extension](#install-the-al-extension) below.
3. **Accept extension recommendations** — Cursor prompts to install recommended extensions from `.vscode/extensions.json`.
4. **Configure your BC server** — Copy and edit a sample `launch.json` for publish/debug (see any sample under `samples/*/.vscode/launch.json`).

## Install the AL Extension

Cursor uses the Open VSX registry, which may lag behind the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dynamics-smb.al). If the AL Language extension is missing or outdated:

1. Download the latest VSIX from the [Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dynamics-smb.al) (click **Download Extension** on the right side, or use a VSIX downloader).
2. In Cursor, open the Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`).
3. Run **Extensions: Install from VSIX...** and select the downloaded file.

Extension ID: `ms-dynamics-smb.al`

## AI Rules

Cursor rules in `.cursor/rules/` are adapted from Microsoft's [Vibe Coding Rules for AL](https://github.com/microsoft/alguidelines/tree/main/content/docs/agentic-coding/vibe-coding-rules). They guide the AI when editing `.al` files and working in this repository.

For the full rule set, see [alguidelines.dev](https://alguidelines.dev/docs/agentic-coding/vibe-coding-rules/).

## Workspace Settings

Shared settings in `.vscode/settings.json` include:

- AL file associations and 2-space indentation
- Code analyzers (AppSourceCop, CodeCop, UICop)
- Exclusion of `.alpackages/` and `*.app` from search

## Sample Projects

| Sample | Description |
|--------|-------------|
| `samples/HelloWorld` | Minimal extension with page extension and codeunit |
| `samples/GetAddressService` | Web service integration with translations |
| `samples/ControlAddIn` | Control add-in with JavaScript |
| `samples/DotNetReplace` | Modern AL types replacing .NET interop |
| `samples/TowersOfHanoi` | Algorithm demo |
| `samples/UploadViewPictures` | Media upload example |

Open a sample folder as the workspace root when developing or testing with the AL compiler.

## Resources

- [Cursor Agent guide for AL](https://alguidelines.dev/docs/agentic-coding/communityresources/agents/cursor-agent/)
- [Effective prompting for AL](https://alguidelines.dev/docs/agentic-coding/gettingstarted/effective-prompting/)
- [AL Language extension issues](https://github.com/microsoft/AL/issues)
- [Business Central developer docs](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-get-started)

## Troubleshooting

**Extension not found in marketplace** — Install manually from VSIX (see above).

**Outdated AL extension version** — Cursor's marketplace may show an older version. VSIX install gets the latest from Microsoft.

**Symbols not downloading** — Ensure `launch.json` points to a running BC instance and credentials are correct.

**AI generates incorrect AL** — Reference `@app.json` and existing sample code; rules in `.cursor/rules/` improve consistency.
