# pdf-regex-to-table

A browser-based tool to extract text from PDF files using regular expressions
and export the results as a table.

## Features

- Drag & drop PDF files or folders
- Extract text using custom regex patterns with capture groups
- Preview matched data in a table
- Export to CSV or XLSX

## Usage

1. Visit the [live demo](https://cmiic.github.io/pdf-regex-to-table/)
2. Drop a PDF file onto the dropzone
3. Enter a regex pattern with capture groups (e.g., `(\d+)\s+(\w+)`)
4. View matched data in the table
5. Export as CSV or XLSX

## Development

```bash
npm install
npm run dev
```

### Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run lint` | Run ESLint and markdownlint |
| `npm run preview` | Preview production build |

## Browser Requirements

This application requires a modern browser with ES2024 support:

- Chrome / Chromium 134+
- Firefox 133+
- Safari 18+
- Edge 134+

## License

MIT
