[English](README.md) | [日本語](README.ja.md)

# md2cv Examples

このリポジトリは [md2cv](https://www.npmjs.com/package/md2cv) のサンプル Markdown ファイルを保持し、コマンドを使用して PDF と HTML の履歴書・職務経歴書を生成する方法を説明するためのものです。

## 構成

```
cv-en/
  cv-en.md                    # 英語版 CV ソース（フロントマター使用）
rirekisho-cv-ja/
  cv-ja.md                    # 日本語版 履歴書/職務経歴書 ソース（フロントマター使用）
cv-en-env-variables/
  cv-en.md                    # 英語版 CV ソース（環境変数使用）
  .env.example                # 環境変数のサンプル
cv-ja-env-variables/
  cv-ja.md                    # 日本語版 CV ソース（環境変数使用）
  .env.example                # 環境変数のサンプル
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

### ワークフロー概要

ワークフロー（`.github/workflows/release.yml`）は以下を実行します：

1. フロントマターベースのソース（`cv-en/`, `rirekisho-cv-ja/`）から CV ファイルを生成
2. 環境変数ベースのソース（`cv-en-env-variables/`, `cv-ja-env-variables/`）から CV ファイルを生成
3. 生成されたすべての PDF と HTML ファイルを含む GitHub Release を作成

### GitHub Secrets の設定

環境変数ベースの CV 生成を使用するには、リポジトリに GitHub Secrets を設定する必要があります。

1. GitHub でリポジトリを開く
2. **Settings** > **Secrets and variables** > **Actions** に移動
3. **New repository secret** をクリックして以下のシークレットを追加：

#### 英語版 CV 用シークレット

| シークレット名 | 説明 | 例 |
|----------------|------|-----|
| `CV_EN_NAME` | 氏名 | `John Smith` |
| `CV_EN_EMAIL_ADDRESS` | メールアドレス | `john.smith@example.com` |
| `CV_EN_PHONE_NUMBER` | 電話番号 | `+1-555-123-4567` |
| `CV_EN_HOME_ADDRESS` | 住所 | `San Francisco, CA` |
| `CV_EN_LINKEDIN` | LinkedIn URL | `https://linkedin.com/in/johnsmith` |

#### 日本語版 CV 用シークレット

| シークレット名 | 説明 | 例 |
|----------------|------|-----|
| `CV_JA_NAME` | 氏名（ローマ字） | `Taro Yamada` |
| `CV_JA_NAME_JA` | 氏名（漢字） | `山田 太郎` |
| `CV_JA_NAME_FURIGANA` | 氏名（ふりがな） | `ヤマダ タロウ` |
| `CV_JA_EMAIL_ADDRESS` | メールアドレス | `taro.yamada@example.com` |
| `CV_JA_PHONE_NUMBER` | 電話番号 | `090-1234-5678` |
| `CV_JA_POST_CODE` | 郵便番号 | `150-0001` |
| `CV_JA_HOME_ADDRESS` | 住所 | `東京都渋谷区神宮前 1-2-3` |
| `CV_JA_HOME_ADDRESS_FURIGANA` | 住所（ふりがな） | `とうきょうと しぶやく じんぐうまえ` |
| `CV_JA_EMAIL_ADDRESS2` | 連絡先メールアドレス | `taro.yamada2@example.com` |
| `CV_JA_PHONE_NUMBER2` | 連絡先電話番号 | `03-1234-5678` |
| `CV_JA_POST_CODE2` | 連絡先郵便番号 | `100-0001` |
| `CV_JA_HOME_ADDRESS2` | 連絡先住所 | `東京都千代田区千代田 1-1` |
| `CV_JA_HOME_ADDRESS2_FURIGANA` | 連絡先住所（ふりがな） | `とうきょうと ちよだく ちよだ` |
| `CV_JA_DOB` | 生年月日 | `1995-04-15` |
| `CV_JA_GENDER` | 性別 | `男` |

### ローカル開発での環境変数使用

md2cv はマークダウンファイルと同じディレクトリにある `.env` ファイルを自動的に読み込みます。

```bash
cd cv-en-env-variables
cp .env.example .env
# .env を編集して情報を入力

# CV を生成（source .env は不要）
npx md2cv -i cv-en.md -o cv-en -f cv -t both -p a4
```

## ライセンス

詳細は [LICENSE](LICENSE) を参照してください。
