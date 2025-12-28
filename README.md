[English](README.md) | [日本語](README.ja.md)

# md2cv Examples

This repository contains sample Markdown files for [md2cv](https://www.npmjs.com/package/md2cv) and demonstrates how to use the command to generate PDF and HTML resumes.

## Structure

```
cv-en/
  cv-en.md                    # English CV source (with frontmatter)
rirekisho-cv-ja/
  cv-ja.md                    # Japanese CV/履歴書 source (with frontmatter)
cv-en-env-variables/
  cv-en.md                    # English CV source (using environment variables)
  .env.example                # Example environment variables
cv-ja-env-variables/
  cv-ja.md                    # Japanese CV source (using environment variables)
  .env.example                # Example environment variables
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

### Workflow Overview

The workflow (`.github/workflows/release.yml`) performs the following:

1. Generates CV files from frontmatter-based sources (`cv-en/`, `rirekisho-cv-ja/`)
2. Generates CV files from environment variable-based sources (`cv-en-env-variables/`, `cv-ja-env-variables/`)
3. Creates a GitHub Release with all generated PDF and HTML files

### Setting Up GitHub Secrets

To use the environment variable-based CV generation, you need to configure GitHub Secrets in your repository.

1. Go to your repository on GitHub
2. Navigate to **Settings** > **Secrets and variables** > **Actions**
3. Click **New repository secret** and add the following secrets:

#### English CV Secrets

| Secret Name | Description | Example |
|-------------|-------------|---------|
| `CV_EN_NAME` | Full name | `John Smith` |
| `CV_EN_EMAIL_ADDRESS` | Email address | `john.smith@example.com` |
| `CV_EN_PHONE_NUMBER` | Phone number | `+1-555-123-4567` |
| `CV_EN_HOME_ADDRESS` | Address | `San Francisco, CA` |
| `CV_EN_LINKEDIN` | LinkedIn URL | `https://linkedin.com/in/johnsmith` |

#### Japanese CV Secrets

| Secret Name | Description | Example |
|-------------|-------------|---------|
| `CV_JA_NAME` | Name (romaji) | `Taro Yamada` |
| `CV_JA_NAME_JA` | Name (kanji) | `山田 太郎` |
| `CV_JA_NAME_FURIGANA` | Name (furigana) | `ヤマダ タロウ` |
| `CV_JA_EMAIL_ADDRESS` | Email address | `taro.yamada@example.com` |
| `CV_JA_PHONE_NUMBER` | Phone number | `090-1234-5678` |
| `CV_JA_POST_CODE` | Postal code | `150-0001` |
| `CV_JA_HOME_ADDRESS` | Address | `東京都渋谷区神宮前 1-2-3` |
| `CV_JA_HOME_ADDRESS_FURIGANA` | Address (furigana) | `とうきょうと しぶやく じんぐうまえ` |
| `CV_JA_EMAIL_ADDRESS2` | Secondary email | `taro.yamada2@example.com` |
| `CV_JA_PHONE_NUMBER2` | Secondary phone | `03-1234-5678` |
| `CV_JA_POST_CODE2` | Secondary postal code | `100-0001` |
| `CV_JA_HOME_ADDRESS2` | Secondary address | `東京都千代田区千代田 1-1` |
| `CV_JA_HOME_ADDRESS2_FURIGANA` | Secondary address (furigana) | `とうきょうと ちよだく ちよだ` |
| `CV_JA_DOB` | Date of birth | `1995-04-15` |
| `CV_JA_GENDER` | Gender | `男` |

### Local Development with Environment Variables

md2cv automatically loads `.env` file from the same directory as the markdown file.

```bash
cd cv-en-env-variables
cp .env.example .env
# Edit .env with your information

# Generate CV (no need to source .env)
npx md2cv -i cv-en.md -o cv-en -f cv -t both -p a4
```

## License

See [LICENSE](LICENSE) for details.
