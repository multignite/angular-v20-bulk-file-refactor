# Angular v20 Bulk File Refactor

A CLI tool to automate file renaming and content refactoring for Angular 20 projects. This tool updates file names and TypeScript file contents to align with Angular 20 conventions, handling patterns like `.component`, `.service`, `.directive`, and `.model`.

---

## ⚠️ Important Note

> **The project path you provide must include `/src/app`**  
>  
> If you omit `/src/app`, the tool will **not work** and will throw an error.  
>  
> Example:  
> ✅ `npx angular-v20-bulk-file-refactor /path/to/angular/project/src/app`  
> ❌ `npx angular-v20-bulk-file-refactor /path/to/angular/project`

---

## Installation

### Global Installation
Install the tool globally to use it from any directory:

```bash
npm install -g angular-v20-bulk-file-refactor
```

Run the tool directly:

```bash
angular-v20-bulk-file-refactor /path/to/your/angular/project/src/app
```

### Local Installation
Install the tool locally within a project:

```bash
npm install angular-v20-bulk-file-refactor
```

Run the tool using `npx`:

```bash
npx angular-v20-bulk-file-refactor /path/to/your/angular/project/src/app
```

Alternatively, add a script to your `package.json`:

```json
{
  "scripts": {
    "refactor": "angular-v20-bulk-file-refactor"
  }
}
```

Then run:

```bash
npm run refactor -- /path/to/your/angular/project/src/app
```

## Usage

Run the tool on your Angular project by specifying the project folder path. Use the global command or `npx` depending on your installation method.

### Options

- `--skip-dirs <dirs>`: Comma-separated list of directories to skip during processing.  
  **Default**: `models,partials`  
  **Example**: `--skip-dirs models,tests` skips the `models` and `tests` directories.

- `--replace-file-name-segments <segments>`: Comma-separated list of file name segments to replace with a hyphenated version (e.g., `.service` becomes `-service` in the `services` folder).  
  **Default**: `services,directives`  
  **Example**: `--replace-file-name-segments services,pipes` replaces `.service` with `-service` in the `services` folder.

- `--remove-file-name-segments <segments>`: Comma-separated list of file name segments to remove (e.g., `.model` is removed from file names in the `models` folder).  
  **Default**: `models`  
  **Example**: `--remove-file-name-segments models,utils` removes `.model` from file names in the `models` folder.

- `--replace-import-segments <segments>`: Comma-separated list of import segments to replace (e.g., `.service` becomes `-service` in import statements).  
  **Default**: `.service`  
  **Example**: `--replace-import-segments .service` replaces `.service` with `-service` in imports.

- `--remove-import-segments <segments>`: Comma-separated list of import segments to remove from import statements.  
  **Default**: `.component,.directive,.model`  
  **Example**: `--remove-import-segments .component,.directive` removes these segments from imports.

### Example

Run the tool on a specific Angular project folder with custom options:

```bash
# Global installation
angular-v20-bulk-file-refactor D:\\Multignite\\Programming\\My-Projects\\angular-app\\src\\app --skip-dirs models,tests --replace-file-name-segments services,pipes --remove-file-name-segments models,utils

# Local installation with default options
npx angular-v20-bulk-file-refactor D:\\Multignite\\Programming\\My-Projects\\angular-app\\src\\app --skip-dirs models,partials --replace-file-name-segments services,directives --remove-file-name-segments models --replace-import-segments .service --remove-import-segments .component,.directive,.model

# Local installation with custom options
npx angular-v20-bulk-file-refactor D:\\Multignite\\Programming\\My-Projects\\angular-app\\src\\app --skip-dirs models,tests --replace-file-name-segments services,pipes --remove-file-name-segments models,utils

# Using package.json script
npm run refactor -- D:\\Multignite\\Programming\\My-Projects\\angular-app\\src\\app --skip-dirs models,tests --replace-file-name-segments services,pipes --remove-file-name-segments models,utils
```

## Compatibility

This tool has been tested on Windows and works reliably. A Linux binary is included but hasn’t been fully tested yet. I’d love to hear how it performs on Linux or macOS! Please share your experience or report issues at [github.com/multignite/angular-v20-bulk-file-refactor/issues](github.com/multignite/angular-v20-bulk-file-refactor/issues).

## License

MIT License. See [LICENSE](./LICENSE) for details.

## Author

Multignite [multignite](https://github.com/multignite)

## Repository

[github.com/multignite/angular-v20-bulk-file-refactor](https://github.com/multignite/angular-v20-bulk-file-refactor)

## Issues

Report bugs or suggest improvements at [github.com/multignite/angular-v20-bulk-file-refactor/issues](https://github.com/multignite/angular-v20-bulk-file-refactor/issues).

## Security Measures

This package includes several security features to protect users:
- **SHA-256 Verification**: Each binary comes with a `.sha256` file containing a unique fingerprint that verifies the file hasn't been tampered with during download.
- **GPG Signatures**: All binaries include `.asc` signature files that prove the software was created by the package author and not modified by third parties.
- **Automated Builds**: All binaries are built using GitHub Actions automated workflows, ensuring consistent and reproducible builds without manual intervention.

Read more at [keys/README.md](keys/README.md)

