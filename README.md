# Assembly Syntax for Zed

Tree-sitter based syntax highlighting for assembly source files in the [Zed](https://zed.dev) editor.

## Features

- Syntax highlighting for comments, directives, labels, mnemonics, registers, numbers, and strings
- Automatic language detection for `.s`, `.S`, and `.asm` files
- Line comment toggling (`#` and `;`)

## Installation

### From the Zed extensions page

1. Open the command palette (`ctrl-shift-p`) and run `zed: extensions`
2. Search for **Assembly Syntax**
3. Click **Install**

### As a dev extension (local)

1. Install Rust via [rustup](https://rustup.rs) (required by Zed to build extensions)
2. Clone this repository:
   ```bash
   git clone https://github.com/NasriAnis/asm-syntax.git
   ```
3. In Zed, run `zed: install dev extension` and select the cloned folder

## Supported files

| Extension | Description                 |
| --------- | --------------------------- |
| `.s`      | Assembly source             |
| `.S`      | Assembly with preprocessor  |
| `.asm`    | Assembly source             |

If a file is not detected automatically, click the language name in the bottom-right status bar and pick **Assembly**.

## Customizing

To associate other file extensions with this language, add them to your Zed `settings.json`:

```json
{
  "file_types": {
    "Assembly": ["inc", "mac"]
  }
}
```

## Limitations

- Highlighting comes from a generic assembly grammar, so it is not tailored to a single architecture or assembler dialect. Some architecture-specific instructions, registers, or directives may not be highlighted perfectly.
- There is no language server support (completion, diagnostics, hover). This extension only provides syntax highlighting.

## Troubleshooting

- **Language shows as "Plain Text":** check that the file extension is listed above, or select Assembly manually from the status bar.
- **No colors or wrong colors:** run `dev: open syntax tree view` to inspect the parse tree. Errors there point to a grammar issue; a correct tree with no colors points to the highlight queries.
- **Extension fails to build:** run `zed --foreground` from a terminal to see build errors, and confirm Rust was installed with rustup.

## Credits

- Grammar: [RubixDev/tree-sitter-asm](https://github.com/RubixDev/tree-sitter-asm)
- The highlight queries are based on the ones from that repository and adapted for Zed.

## Contributing

Issues and pull requests are welcome. If you find code that is highlighted incorrectly, please include a small sample file in your report.

## License

MIT. See [LICENSE](LICENSE).