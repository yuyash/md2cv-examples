[English](README.md) | [日本語](README.ja.md)

# md2cv Examples

This repository contains sample Markdown files for [md2cv](https://www.npmjs.com/package/md2cv) and demonstrates how to use the command to generate PDF and HTML resumes.

## Structure

```
cv-en/
  cv-en.md          # English CV source
rirekisho-cv-ja/
  cv-ja.md          # Japanese CV/履歴書 source
```

## Prerequisites

- Node.js 18+
- npm or npx

## Generate CV/Resume

### English CV (A4)

```bash
# PDF only
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t pdf -p a4

# HTML only
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t html -p a4

# Both PDF and HTML
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t both -p a4
```

### Japanese CV (職務経歴書) - A4

```bash
# PDF only
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t pdf -p a4

# HTML only
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t html -p a4

# Both PDF and HTML
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t both -p a4
```

### Japanese Rirekisho (履歴書) - A3

```bash
# PDF only
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t pdf -p a3

# HTML only
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t html -p a3

# Both PDF and HTML
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t both -p a3
```

### Generate All at Once

```bash
# English CV (A4)
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t both -p a4

# Japanese CV (A4)
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t both -p a4

# Japanese Rirekisho (A3)
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t both -p a3
```

## Output Files

| Source | Format | Paper Size | Output |
|--------|--------|------------|--------|
| cv-en/cv-en.md | CV | A4 | cv-en/cv-en_cv.pdf, cv-en/cv-en_cv.html |
| rirekisho-cv-ja/cv-ja.md | CV | A4 | rirekisho-cv-ja/cv-ja_cv.pdf, rirekisho-cv-ja/cv-ja_cv.html |
| rirekisho-cv-ja/cv-ja.md | Rirekisho | A3 | rirekisho-cv-ja/cv-ja_rirekisho.pdf, rirekisho-cv-ja/cv-ja_rirekisho.html |

## GitHub Actions

This repository includes a GitHub Actions workflow that automatically generates PDF and HTML files and creates a release with a date tag (e.g., `2025-12-27`) when you push to the `main` branch.

## License

See [LICENSE](LICENSE) for details.
