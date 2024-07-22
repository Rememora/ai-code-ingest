# ai-code-ingest

A CLI tool to aggregate your codebase into a single Markdown file for use with Claude Projects or custom ChatGPTs.

## Features

- Aggregates all files in the specified directory and subdirectories
- Ignores common build artifacts and configuration files
- Outputs a single Markdown file containing the whole codebase
- Provides options for whitespace removal and custom ignore patterns

## How to Use

Start by running the CLI tool in your project directory:

```bash
npx ai-code-ingest
```

This will generate a `codebase.md` file with your codebase.

Once you've generated the Markdown file containing your codebase, you can use it with AI models like ChatGPT and Claude for code analysis and assistance.

### With ChatGPT:
1. Create a Custom GPT
2. Upload the generated Markdown file to the GPT's knowledge base

### With Claude:
1. Create a new Project
2. Add the Markdown file to the Project's knowledge

For best results, re-upload the Markdown file before starting a new chat session to ensure the AI has the most up-to-date version of your codebase.

## Options

- `-i, --input <directory>`: Specify input directory (default: current directory)
- `-o, --output <file>`: Specify output file (default: codebase.md)
- `--no-default-ignores`: Disable default ignore patterns
- `--whitespace-removal`: Enable whitespace removal
- `--show-output-files`: Display a list of files included in the output
- `--help`: Show help

## Local testing

To test the tool locally, you can run the following command:

   ```bash
   npm build
   # make sure you're in the repo folder when you run this
   npx ai-code-ingest -i /path/to/your/project -o /path/to/your/project/project_summary.md
   ```


## Examples

1. Basic usage:

   ```bash
   npx ai-code-ingest
   ```

2. Specify input and output:

   ```bash
   npx ai-code-ingest -i /path/to/your/project -o project_summary.md
   ```

3. Enable whitespace removal:

   ```bash
   npx ai-code-ingest --whitespace-removal
   ```

4. Show list of included files:

   ```bash
   npx ai-code-ingest --show-output-files
   ```

5. Combine multiple options:

   ```bash
   npx ai-code-ingest -i /path/to/your/project -o project_summary.md --whitespace-removal --show-output-files
   ```

## Custom Ignore Patterns

ai-code-ingest supports custom ignore patterns using a `.aiignore` file in the root directory of your project. This file works similarly to `.gitignore`, allowing you to specify files and directories that should be excluded from the aggregation.

Use the `--show-output-files` flag to see which files are being included, making it easier to identify candidates for exclusion.


## Whitespace Removal

When using the `--whitespace-removal` flag, ai-code-ingest removes excess whitespace from files to reduce the token count when used with AI models. This feature is disabled for whitespace-dependent languages like Python and YAML.

## Binary and SVG File Handling

Binary files and SVGs are included in the output with a note about their file type. This allows AI models to be aware of these files without including their full content.

## Local Development

Run `npm run start` to run the CLI tool on the local project. (Very meta!)

Run `npm test` to run the tests.

## Deploy New Version

```
npm publish
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License.