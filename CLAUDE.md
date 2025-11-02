# EditorConfig Expert Knowledge

This document provides specialized knowledge for working effectively with EditorConfig files and this repository.

## Core Understanding

### What is EditorConfig?

EditorConfig helps maintain consistent coding styles across different editors and IDEs. It uses `.editorconfig` files to define and maintain consistent formatting standards.

### EditorConfig File Structure

- **INI-like syntax**: Uses sections `[pattern]` followed by key-value pairs
- **Root directive**: `root = true` stops EditorConfig from searching parent directories
- **Glob patterns**: Use wildcards to match file paths
- **Properties**: Define formatting rules for matched files

## Key Behaviors and Skills

### 1. Glob Pattern Expertise

**Pattern matching syntax:**
- `*` - Matches any string except path separator `/`
- `**` - Matches any string (including path separators)
- `?` - Matches any single character
- `[seq]` - Matches any character in sequence
- `[!seq]` - Matches any character not in sequence
- `{s1,s2,s3}` - Matches any of the strings (comma-separated)
- `{num1..num2}` - Matches integers between num1 and num2

**Pattern ordering matters:**
- Later patterns override earlier ones for the same files
- More specific patterns should come after general patterns
- Order sections from general to specific

**Examples:**
```ini
# General default
[*]
indent_style = space
indent_size = 2

# More specific override
[*.py]
indent_size = 4
```

### 2. Standard Properties Knowledge

**Indentation:**
- `indent_style` - `tab` or `space`
- `indent_size` - Integer or `tab` (to use tab_width)
- `tab_width` - Integer (defaults to indent_size)

**Line endings:**
- `end_of_line` - `lf`, `cr`, or `crlf`
- Platform defaults: Unix/macOS = `lf`, Windows = `crlf`

**Character set:**
- `charset` - `latin1`, `utf-8`, `utf-8-bom`, `utf-16be`, `utf-16le`

**Whitespace:**
- `trim_trailing_whitespace` - `true` or `false`
- `insert_final_newline` - `true` or `false`

**Line length:**
- `max_line_length` - Integer or `off`

**Quote style:**
- `quote_type` - `single` or `double` (not universally supported)

### 3. Language-Specific Best Practices

**Programming languages with standard conventions:**
- Python: 4 spaces, max_line_length = 88 (Black) or 79 (PEP 8)
- Go: tabs (required by `go fmt`)
- JavaScript/TypeScript: 2 spaces (common) or 4 spaces
- Ruby: 2 spaces
- Java/C#/C/C++: 4 spaces or tabs
- Rust: 4 spaces, max_line_length = 100

**Configuration files:**
- YAML: 2 spaces (tabs break YAML)
- JSON: 2 spaces, often `insert_final_newline = false`
- TOML: 2 or 4 spaces
- INI/Config: 2 spaces

**Markup and documentation:**
- Markdown: 2 spaces, `trim_trailing_whitespace = false` (allows double-space line breaks)
- HTML/XML: 2 spaces
- LaTeX: 2 spaces

**Special cases:**
- Makefiles: MUST use tabs
- Batch/CMD files: CRLF line endings required
- PowerShell: CRLF line endings (Windows convention)
- Lock files: Often `insert_final_newline = false`
- Binary files: Use `unset` for all properties

### 4. Pattern Design Principles

**Use precise glob patterns:**
```ini
# Good - specific extensions
[*.{js,jsx,ts,tsx}]

# Less good - too broad
[*.js]
[*.jsx]
[*.ts]
[*.tsx]
```

**Handle special file names:**
```ini
# Specific named files
[{Makefile,Dockerfile,Jenkinsfile}]

# Files with specific prefixes
[Dockerfile.*]

# Multiple naming patterns
[{package.json,package-lock.json,yarn.lock}]
```

**Path-specific rules:**
```ini
# GitHub Actions
[.github/workflows/*.{yml,yaml}]

# All test files
[**/*test.{js,ts}]
```

### 5. Common Pitfalls to Avoid

**1. Wrong pattern syntax:**
```ini
# WRONG - missing braces
[*.js,*.ts]

# CORRECT
[*.{js,ts}]
```

**2. Conflicting properties:**
```ini
# WRONG - indent_size conflicts with tab usage
[*.go]
indent_style = tab
indent_size = 2  # Misleading - tabs don't have size

# CORRECT
[*.go]
indent_style = tab
tab_width = 4    # Or just omit
```

**3. Missing quotes in patterns:**
```ini
# WRONG - will not work correctly
[package.json]

# CORRECT - use braces for literal names
[{package.json}]

# ALSO CORRECT - simpler for single files
[package.json]  # Actually works but braces are clearer
```

**4. Incorrect line ending choices:**
```ini
# WRONG - Windows batch needs CRLF
[*.bat]
end_of_line = lf

# CORRECT
[*.bat]
end_of_line = crlf
```

**5. Forgetting to unset binary files:**
```ini
# GOOD - prevent modifications to binaries
[*.{png,jpg,pdf,zip}]
indent_style = unset
end_of_line = unset
# ... unset all properties
```

### 6. Multi-Language Project Strategy

**Layer configurations from general to specific:**

1. Start with universal defaults for all files
2. Add language family rules (e.g., all web files)
3. Add specific language overrides
4. Add framework/tool-specific rules
5. Add special file exceptions

**Example structure:**
```ini
root = true

# Universal defaults
[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true

# Most languages use 2 spaces
[*.{js,ts,yaml,json,css}]
indent_style = space
indent_size = 2

# Languages requiring 4 spaces
[*.{py,java,cpp}]
indent_size = 4

# Languages requiring tabs
[*.go]
indent_style = tab

# Special exceptions
[{Makefile,*.mk}]
indent_style = tab

# Lock files - no modifications
[*.lock]
insert_final_newline = false

# Binary files
[*.{png,jpg,pdf}]
indent_style = unset
```

### 7. Testing and Validation

**Verify EditorConfig works:**
1. Check your editor has EditorConfig support (plugin or built-in)
2. Open files and verify formatting matches rules
3. Create test files to verify patterns match correctly
4. Test that `root = true` prevents parent directory traversal

**Common debugging:**
- Patterns not matching: Check glob syntax, especially braces
- Rules not applying: Check pattern order (later overrides earlier)
- Wrong indentation: Verify `indent_style` and `indent_size` consistency

### 8. Integration with Other Tools

**EditorConfig interacts with:**
- **Prettier**: Prettier respects EditorConfig settings
- **ESLint**: Can be configured to respect EditorConfig
- **Code formatters**: Most modern formatters check EditorConfig first

**Precedence (typical):**
1. Project-specific formatter config (e.g., `.prettierrc`)
2. EditorConfig settings
3. Editor defaults

**Best practice**: Use EditorConfig for basic whitespace/indentation, use tool-specific configs for complex formatting rules.

### 9. Maintenance Best Practices

**Keep it organized:**
- Group related file types together
- Add comments for clarity
- Use consistent property ordering
- Keep sections alphabetically sorted when logical

**Documentation:**
- Comment non-obvious patterns
- Explain why specific rules exist
- Note any project-specific conventions

**Version control:**
- Always commit `.editorconfig` to version control
- Review changes carefully (affects entire team)
- Test with multiple editors before committing

### 10. Platform-Specific Considerations

**Line endings strategy:**
- Default to `lf` for cross-platform projects
- Use `crlf` only when required (Windows batch/PowerShell)
- Let Git handle line ending conversion via `.gitattributes`

**Path separators:**
- Always use `/` in patterns (even on Windows)
- EditorConfig normalizes paths automatically

**Character encoding:**
- `utf-8` is the safest default
- Avoid `utf-8-bom` unless required by Windows tools
- Only use other encodings for legacy compatibility

## Working with This Repository

### Repository Purpose

This repository provides a comprehensive, production-ready `.editorconfig` file covering:
- 50+ programming languages
- 30+ configuration file types
- Framework-specific files
- CI/CD configurations
- Binary file handling

### When Making Changes

**Adding new language support:**
1. Research the language's standard conventions
2. Check official style guides
3. Consider community practices
4. Add appropriate glob patterns
5. Set correct indentation (spaces vs tabs, size)
6. Set max_line_length if applicable

**Updating existing rules:**
1. Verify change matches language standards
2. Check it doesn't conflict with other sections
3. Test the pattern matches intended files
4. Consider backward compatibility

**Pattern complexity:**
- Prefer comprehensive glob lists `[*.{ext1,ext2,ext3}]`
- Include common file variations
- Handle both explicit extensions and tool-specific naming

### Code Review Focus

When reviewing EditorConfig changes:
1. **Pattern correctness**: Does the glob match the right files?
2. **Convention accuracy**: Do rules match language standards?
3. **Consistency**: Are similar languages treated similarly?
4. **Completeness**: Are all relevant file extensions included?
5. **Order**: Are patterns ordered correctly (general → specific)?
6. **Documentation**: Are non-obvious choices explained?

## Quick Reference

### Creating a New Section

```ini
# [Language name] - Comment for clarity
[*.{ext1,ext2,ext3}]
indent_style = space|tab
indent_size = 2|4
max_line_length = 80|100|120
# Additional properties as needed
```

### Common Property Sets

**Standard text file:**
```ini
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
```

**Lock/generated file:**
```ini
insert_final_newline = false
# Usually inherit other settings
```

**Binary file:**
```ini
indent_style = unset
indent_size = unset
end_of_line = unset
insert_final_newline = unset
trim_trailing_whitespace = unset
charset = unset
```

## Resources

- Official spec: https://editorconfig.org/
- Editor support: https://editorconfig.org/#download
- Glob pattern tester: Test patterns in your editor
- Language style guides: Consult official docs for each language
