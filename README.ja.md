[English](README.md) | [日本語](README.ja.md)

# md2cv Examples

このリポジトリは [md2cv](https://www.npmjs.com/package/md2cv) のサンプル Markdown ファイルを保持し、コマンドを使用して PDF と HTML の履歴書・職務経歴書を生成する方法を説明するためのものです。

## 構成

```
cv-en/
  cv-en.md          # 英語版 CV ソース
rirekisho-cv-ja/
  cv-ja.md          # 日本語版 履歴書/職務経歴書 ソース
```

## 前提条件

- Node.js 18+
- npm または npx

## CV/履歴書の生成

### 英語版 CV (A4)

```bash
# PDF のみ
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t pdf -p a4

# HTML のみ
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t html -p a4

# PDF と HTML 両方
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t both -p a4
```

### 日本語版 職務経歴書 (A4)

```bash
# PDF のみ
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t pdf -p a4

# HTML のみ
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t html -p a4

# PDF と HTML 両方
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t both -p a4
```

### 日本語版 履歴書 (A3)

```bash
# PDF のみ
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t pdf -p a3

# HTML のみ
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t html -p a3

# PDF と HTML 両方
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t both -p a3
```

### 一括生成

```bash
# 英語版 CV (A4)
npx md2cv -i cv-en/cv-en.md -o cv-en/cv-en -f cv -t both -p a4

# 日本語版 職務経歴書 (A4)
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f cv -t both -p a4

# 日本語版 履歴書 (A3)
npx md2cv -i rirekisho-cv-ja/cv-ja.md -o rirekisho-cv-ja/cv-ja -f rirekisho -t both -p a3
```

## 出力ファイル

| ソース | フォーマット | 用紙サイズ | 出力 |
|--------|--------------|------------|------|
| cv-en/cv-en.md | CV | A4 | cv-en/cv-en_cv.pdf, cv-en/cv-en_cv.html |
| rirekisho-cv-ja/cv-ja.md | CV (職務経歴書) | A4 | rirekisho-cv-ja/cv-ja_cv.pdf, rirekisho-cv-ja/cv-ja_cv.html |
| rirekisho-cv-ja/cv-ja.md | 履歴書 | A3 | rirekisho-cv-ja/cv-ja_rirekisho.pdf, rirekisho-cv-ja/cv-ja_rirekisho.html |

## GitHub Actions

このリポジトリには、`main` ブランチにプッシュすると自動的に PDF と HTML ファイルを生成し、日付タグ（例: `2025-12-27`）でリリースを作成する GitHub Actions ワークフローが含まれています。

## ライセンス

詳細は [LICENSE](LICENSE) を参照してください。
