# EditorConfig

Comprehensive, production-ready [EditorConfig](https://editorconfig.org/) file for maintaining consistent coding styles across different editors and IDEs.

## Installation

### Option 1: Direct Download

Download the [`.editorconfig`](.editorconfig) file and place it in your project root:

```bash
curl -o .editorconfig https://raw.githubusercontent.com/gfmio/editorconfig/main/.editorconfig
```

### Option 2: Git Clone

```bash
# Clone the repository
git clone https://github.com/gfmio/editorconfig.git

# Copy to your project
cp editorconfig/.editorconfig /path/to/your/project/
```

### Option 3: Git Submodule

```bash
# Add as a submodule
git submodule add https://github.com/gfmio/editorconfig.git .editorconfig-source

# Create a symlink (Unix/macOS/Linux)
ln -s .editorconfig-source/.editorconfig .editorconfig

# Or on Windows (requires admin)
mklink .editorconfig .editorconfig-source\.editorconfig
```

## What is EditorConfig?

EditorConfig helps maintain consistent coding styles across different editors and IDEs. When you open a file, your editor automatically applies the formatting rules defined in `.editorconfig` - no per-developer configuration needed.

**Supports:**

- Indentation style (spaces vs tabs)
- Indentation size
- Line endings (LF, CRLF)
- Character encoding
- Trailing whitespace
- Final newlines
- Maximum line length

## What's Included

This configuration covers **75+ languages and file types** with conventions based on official style guides and community best practices.

### Programming Languages

**Web Development:**

- JavaScript (`.js`, `.jsx`, `.mjs`, `.cjs`) - 2 spaces
- TypeScript (`.ts`, `.tsx`, `.mts`, `.cts`) - 2 spaces, single quotes
- HTML, XML, SVG, Vue - 2 spaces
- CSS, SCSS, Sass, Less, Stylus - 2 spaces

**Backend Languages:**

- Python (`.py`, `.pyw`, `.pyx`) - 4 spaces, 88 char max (Black compatible)
- Go (`.go`) - tabs (required by `go fmt`)
- Ruby (`.rb`, `.rake`, Gemfile) - 2 spaces
- PHP (`.php`, `.phtml`) - 4 spaces
- Java (`.java`) - 4 spaces
- C# (`.cs`) - 4 spaces
- Rust (`.rs`) - 4 spaces, 100 char max
- C/C++ (`.c`, `.cpp`, `.h`, `.hpp`) - 4 spaces

**Functional & Modern:**

- Haskell, Elm, Scala, Clojure
- Elixir, Erlang, OCaml, F#
- Dart, Kotlin, Swift
- Crystal, Nim, Zig

**Scientific & Data:**

- R, Julia, MATLAB
- SAS, SPSS, Stata
- Jupyter Notebooks

**Systems & Specialized:**

- Assembly, WebAssembly
- CUDA, OpenCL, GLSL/HLSL
- Solidity, Vyper
- Fortran, COBOL, Pascal
- Lua, Perl, Groovy

### Configuration Files

**Package Managers:**

- `package.json`, `package-lock.json` - no final newline
- `yarn.lock`, `pnpm-lock.yaml` - proper handling
- `Gemfile`, `Gemfile.lock`
- `bunfig.toml`

**Data Formats:**

- JSON, JSONC, JSON5 - 2 spaces, no final newline
- YAML - 2 spaces (tabs would break YAML)
- TOML - 2 spaces
- XML - 2 spaces
- INI, Properties, Config files - 2 spaces
- CSV, TSV - preserves trailing whitespace

**Documentation:**

- Markdown (`.md`) - 2 spaces, 80 char max, preserves trailing whitespace (for double-space line breaks)
- reStructuredText (`.rst`) - 3 spaces (RST convention)
- AsciiDoc (`.adoc`) - 2 spaces
- LaTeX (`.tex`) - 2 spaces

### DevOps & Infrastructure

**Containers & Orchestration:**

- Docker (`Dockerfile`, `Dockerfile.*`) - 2 spaces
- Docker Compose (`docker-compose.yml`) - 2 spaces
- Kubernetes (`*.k8s.yml`) - 2 spaces

**Infrastructure as Code:**

- Terraform (`.tf`, `.tfvars`, `.hcl`) - 2 spaces
- Vagrant (`Vagrantfile`) - 2 spaces

**CI/CD:**

- GitHub Actions (`.github/workflows/*.yml`) - 2 spaces
- CircleCI (`.circleci/config.yml`) - 2 spaces
- Travis CI (`.travis.yml`) - 2 spaces
- GitLab CI (`.gitlab-ci.yml`) - 2 spaces
- Jenkins (`Jenkinsfile`) - 4 spaces

### Build Tools & Tooling

**JavaScript/TypeScript Ecosystem:**

- Prettier config (`.prettierrc`, etc.) - 2 spaces
- ESLint config (`.eslintrc`, etc.) - 2 spaces
- Biome config (`biome.json`) - 2 spaces
- TSConfig (`tsconfig.json`) - 2 spaces
- Babel config (`.babelrc`, etc.) - 2 spaces

**Bundlers & Test Runners:**

- webpack, Vite, Rollup configs - 2 spaces
- Jest, Vitest configs - 2 spaces

**Linters:**

- Stylelint config (`.stylelintrc`) - 2 spaces

**Dependency Management:**

- Renovate config (`renovate.json`) - 2 spaces
- Dependabot (`.github/dependabot.yml`) - 2 spaces

**Build Systems:**

- CMake (`CMakeLists.txt`, `*.cmake`) - 2 spaces
- Bazel (`BUILD`, `WORKSPACE`) - 2 spaces
- Gradle (`.gradle`, `.gradle.kts`) - 4 spaces
- Taskfile (`Taskfile.yml`) - 2 spaces

**Other:**

- GraphQL, Prisma - 2 spaces
- Protocol Buffers - 2 spaces

### Special Files

**Git:**

- `.gitignore`, `.gitattributes`, `.gitconfig` - 2 spaces

**Project Documentation:**

- `README`, `LICENSE`, `CHANGELOG` - trimmed whitespace, 80 char max
- `CONTRIBUTING`, `CODE_OF_CONDUCT` - 80 char max

**Scripts:**

- Shell scripts (`.sh`, `.bash`, `.zsh`, `.fish`) - 2 spaces
- Batch files (`.bat`, `.cmd`) - 2 spaces, CRLF line endings
- PowerShell (`.ps1`, `.psd1`, `.psm1`) - 4 spaces, CRLF line endings

**Build Requirements:**

- Makefiles - tabs (required by Make)

**Server Configs:**

- Apache (`.htaccess`) - 2 spaces
- Nginx (`nginx.conf`) - 4 spaces
- Caddy (`Caddyfile`) - 2 spaces

**Environment:**

- `.env`, `.env.*` - 2 spaces, no final newline

**Binary Files:**

- Images, fonts, archives - all formatting disabled to prevent corruption

## Language-Specific Conventions

This configuration follows official style guides and community standards:

| Language/Type | Indent | Size | Max Length | Notes |
|---------------|--------|------|------------|-------|
| JavaScript/TypeScript | spaces | 2 | 120 | Single quotes, standard in React/Vue/Node |
| JSON/YAML | spaces | 2 | 120 | YAML requires spaces |
| Python | spaces | 4 | 88 | Black formatter default |
| Go | tabs | - | 120 | Required by `go fmt` |
| Rust | spaces | 4 | 100 | Rustfmt default |
| Ruby | spaces | 2 | 120 | Community standard |
| Java/C#/C/C++ | spaces | 4 | 120 | Industry standard |
| PHP | spaces | 4 | 120 | PSR-2/PSR-12 standard |
| HTML/CSS | spaces | 2 | 120 | Web development standard |
| Markdown | spaces | 2 | 80 | Readability, preserves trailing spaces |
| Makefiles | tabs | 4 | - | Make requires tabs |
| Shell scripts | spaces | 2 | 120 | Common practice |
| Windows scripts | spaces | 2/4 | 120 | CRLF line endings required |

## Usage

### Basic Usage

Simply place the `.editorconfig` file in your project root and commit it:

```bash
git add .editorconfig
git commit -m "chore: add EditorConfig for consistent formatting"
```

Your editor will automatically apply the rules when you open files.

### Customization

#### Override Specific Rules

Create sections for project-specific overrides. More specific patterns override general ones:

```ini
# Your custom override (add to the end of .editorconfig)
[src/legacy/*.js]
indent_size = 4  # Override 2-space default for legacy code
```

#### Add Custom Language Support

```ini
# MyLang support
[*.mylang]
indent_style = space
indent_size = 2
max_line_length = 100
```

#### Per-Directory Settings

Create additional `.editorconfig` files in subdirectories (without `root = true`):

```ini
# In src/generated/.editorconfig
[*]
insert_final_newline = false
max_line_length = off
```

## Editor Support

EditorConfig is natively supported or has plugins for all major editors:

**Built-in Support:**

- VS Code
- JetBrains IDEs (IntelliJ IDEA, WebStorm, PyCharm, RubyMine, etc.)
- Visual Studio 2017+
- GitHub (respects EditorConfig in web editor)

**Plugin Available:**

- Sublime Text (EditorConfig package)
- Atom (editorconfig package)
- Vim/Neovim (editorconfig-vim)
- Emacs (editorconfig-emacs)
- Notepad++ (EditorConfig plugin)

See the [official download page](https://editorconfig.org/#download) for complete list and installation instructions.

### Verifying Editor Support

Most editors will show they're using EditorConfig:

- VS Code: Look for "EditorConfig" in status bar
- JetBrains: File → Settings → Editor → Code Style → enable "Enable EditorConfig support"

## Integration with Other Tools

### Prettier

Prettier respects EditorConfig automatically. EditorConfig settings take precedence for:

- `indent_style` → Prettier's `useTabs`
- `indent_size` → Prettier's `tabWidth`
- `max_line_length` → Prettier's `printWidth`
- `end_of_line` → Prettier's `endOfLine`

You can override in `.prettierrc`:

```json
{
  "printWidth": 100
}
```

### ESLint

Configure ESLint to respect EditorConfig with the plugin:

```bash
npm install --save-dev eslint-plugin-editorconfig
```

```json
{
  "extends": ["plugin:editorconfig/all"]
}
```

Or use specific rules:

```json
{
  "rules": {
    "indent": ["error", "tab"]  // Syncs with EditorConfig
  }
}
```

### Black (Python)

Black respects `max_line_length` from EditorConfig automatically. This config uses 88 characters to match Black's default.

Override in `pyproject.toml` if needed:

```toml
[tool.black]
line-length = 100
```

### rustfmt (Rust)

Configure rustfmt to read from EditorConfig in `rustfmt.toml`:

```toml
edition = "2021"
# max_width is read from EditorConfig max_line_length
```

### Git

EditorConfig handles formatting; use `.gitattributes` for line ending conversion during checkout:

```gitattributes
# .gitattributes
* text=auto
*.sh text eol=lf
*.bat text eol=crlf
```

## Common Patterns

### Monorepo Structure

```text
.editorconfig              # Root config (this file)
packages/
  frontend/
    .editorconfig          # Frontend-specific overrides (no root = true)
  backend/
    .editorconfig          # Backend-specific overrides (no root = true)
```

### Mixed Technology Stack

The comprehensive nature of this config means it works well for polyglot projects:

```text
project/
  frontend/               # JavaScript/TypeScript (2 spaces)
  backend/                # Python (4 spaces, 88 chars)
  infrastructure/         # Terraform (2 spaces)
  .editorconfig           # Handles all of them
```

### Legacy Code

Exclude legacy directories from strict formatting:

```ini
# Add to your .editorconfig
[legacy/**/*]
indent_size = unset
max_line_length = unset
```

## Philosophy

This configuration follows these principles:

1. **Standards-first**: Use official style guides and community conventions
2. **Comprehensive**: Cover the most common languages and tools developers encounter
3. **Sensible defaults**: Choose widely-accepted settings that work for most projects
4. **Easy to customize**: Well-commented and logically structured for easy modification
5. **Production-ready**: Tested across multiple projects and teams
6. **Tool-friendly**: Works alongside formatters like Prettier, Black, and rustfmt
7. **Clear organization**: Grouped by category with explanatory comments

## Why Use EditorConfig?

### Without EditorConfig

- Developers use different editor settings
- Mixed tabs and spaces in the same file
- Inconsistent line endings cause Git conflicts
- Windows developers create files with CRLF, breaking Unix scripts
- No clear project standards
- Code review noise from formatting differences
- New team members don't know the formatting conventions

### With This EditorConfig

- Instant consistency across the entire team
- Works automatically with any editor
- No per-developer configuration needed
- Follows industry best practices for each language
- Reduces "formatting wars" discussions
- New team members get correct formatting immediately
- Integrates seamlessly with formatters and linters
- Single source of truth for basic formatting rules

## FAQ

**Q: Why use spaces instead of tabs for most languages?**

A: Most modern style guides prefer spaces for consistency across different editor tab-width settings. Tabs are used only where required (Makefiles) or strongly preferred by the language tooling (Go).

**Q: Can I use this with Prettier/ESLint/Black?**

A: Yes! Most modern formatters respect EditorConfig. EditorConfig provides baseline formatting (indentation, line endings), while formatters handle more complex rules (semicolons, quotes, etc.).

**Q: Why 2 spaces for JavaScript instead of 4?**

A: 2 spaces is the most common convention in modern JavaScript/TypeScript (Airbnb, Google, StandardJS). It's standard in React, Vue, Angular, and Node.js projects.

**Q: Do I need to install anything?**

A: Most modern editors have built-in EditorConfig support. Older editors may need a plugin. Check [editorconfig.org/#download](https://editorconfig.org/#download).

**Q: Should I commit this file?**

A: Yes! Always commit `.editorconfig` so all team members and CI/CD systems use the same formatting rules.

**Q: What if my team uses different conventions?**

A: Fork this repository and modify to match your team's standards. Or simply edit your copy to override specific sections.

**Q: Why is max_line_length 120 instead of 80?**

A: Modern screens are wider, and 120 is a good balance between readability and screen real estate. Specific languages use their community standards (Python: 88, Rust: 100, Markdown: 80).

**Q: Will this slow down my editor?**

A: No. EditorConfig processing is extremely fast and happens only when opening files.

**Q: Can I use multiple .editorconfig files?**

A: Yes! EditorConfig searches from the current directory up to the project root. You can have directory-specific configs (just don't include `root = true` in them).

**Q: What about binary files?**

A: All formatting rules are disabled for binary files (images, fonts, archives) to prevent corruption.

## Troubleshooting

### Rules Not Applying

1. **Check editor support**: Verify your editor has EditorConfig enabled
   - VS Code: Built-in, check status bar
   - JetBrains: Enable in Settings → Editor → Code Style
   - Other editors: Install plugin from [editorconfig.org](https://editorconfig.org/#download)

2. **Check file pattern**: Ensure the glob pattern matches your file

   ```bash
   # Test if .editorconfig would match your file
   # (no built-in tool, but check patterns manually)
   ```

3. **Check pattern order**: Later patterns override earlier ones
   - More specific patterns should come after general ones

4. **Check root directive**: Multiple `root = true` can cause issues
   - Only the top-most `.editorconfig` should have `root = true`

### Mixed Indentation in Existing Files

EditorConfig only affects new edits, not existing content. To reformat:

**VS Code:**

```text
Shift+Alt+F (Windows/Linux)
Shift+Option+F (macOS)
```

**JetBrains:**

```text
Ctrl+Alt+L (Windows/Linux)
Cmd+Option+L (macOS)
```

**Command line with Prettier:**

```bash
npx prettier --write "**/*"
```

### Line Ending Issues

If you see `^M` characters or Git shows every line changed:

1. Configure Git to normalize line endings:

   ```bash
   git config --global core.autocrlf input  # Unix/Mac
   git config --global core.autocrlf true   # Windows
   ```

2. Create `.gitattributes`:

   ```gitattributes
   * text=auto
   ```

3. Re-normalize the repository:

   ```bash
   git add --renormalize .
   git commit -m "chore: normalize line endings"
   ```

## Contributing

Issues and pull requests are welcome!

### Reporting Issues

Found a problem or have a suggestion? [Open an issue](https://github.com/gfmio/editorconfig/issues/new).

### Pull Requests

1. Fork the repository
2. Create a feature branch (`git checkout -b feat/add-amazing-language`)
3. Make your changes to [`.editorconfig`](.editorconfig)
4. Ensure conventions follow the language's official style guide
5. Add comments explaining non-obvious choices
6. Commit your changes (`git commit -m 'feat: add support for AmazingLang'`)
7. Push to the branch (`git push origin feat/add-amazing-language`)
8. Open a Pull Request

### Adding Language Support

When adding a new language:

1. **Research**: Check the language's official style guide and community conventions
2. **Glob patterns**: Include all relevant file extensions
3. **Indentation**: Set correct style (spaces/tabs) and size
4. **Line length**: Set `max_line_length` if the language has a convention
5. **Comments**: Explain non-obvious choices
6. **Organization**: Group with similar languages
7. **Ordering**: Maintain logical ordering within categories

Example:

```ini
# AwesomeLang - follows AwesomeLang official style guide v2.0
[*.{awsl,awesome}]
indent_style = space
indent_size = 3
max_line_length = 100
```

## Resources

- [EditorConfig Official Site](https://editorconfig.org/)
- [EditorConfig Specification](https://spec.editorconfig.org/)
- [Editor Plugins](https://editorconfig.org/#download)
- [EditorConfig on GitHub](https://github.com/editorconfig)
- [Glob Pattern Reference](https://editorconfig.org/#file-format-details)

## License

[MIT](LICENSE)

## Author

Frédérique Mittelstaedt

- GitHub: [@gfmio](https://github.com/gfmio)

## Acknowledgments

- The EditorConfig team for creating this essential tool
- Language communities for establishing and documenting style conventions
- Contributors who help improve this configuration
