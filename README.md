# 📚 Bibliothèque — セットアップガイド

## ディレクトリ構成

```
your-server/
├── index.html          ← サイト本体（このファイル1つ）
├── books/              ← 電子書籍ファイルをここに入れる
│   ├── wagahai.epub
│   ├── botchan.pdf
│   └── ...（100冊でもOK）
└── covers/             ← カバー画像（省略可）
    └── sample.jpg
```

---

## 🔑 Step 1: パスワードを変更する

`index.html` を開き、以下を探して変更：

```javascript
const PASSWORD = "library2024";  // ← 自分のパスワードに変更
```

---

## 📖 Step 2: 書籍を追加する

`BOOKS` 配列にオブジェクトを追加します：

```javascript
{
  id: 11,                        // 重複しない番号
  title: "書名",
  author: "著者名",
  year: 2023,                    // 刊行年（任意）
  genre: "小説",                 // ジャンル（フィルター用）
  format: "epub",                // "epub" または "pdf"
  file: "books/filename.epub",   // ファイルパス
  cover: "covers/cover.jpg",     // カバー画像（省略可）
},
```

---

## 🌐 Step 3: サーバーにアップロード

### 無料ホスティング（おすすめ）

| サービス | 方法 | 備考 |
|---|---|---|
| **Netlify** | フォルダをD&Dするだけ | 最も簡単 |
| **GitHub Pages** | GitHubにpush | バージョン管理もできる |
| **Vercel** | GitHubと連携 | 高速CDN |

### レンタルサーバー（Xserver / さくら等）
FTPソフト（FileZilla等）で `index.html` と `books/` フォルダをアップロード。

---

## 📖 EPUB表示について

- EPUBは **epub.js** を使ってブラウザ内でインライン表示されます
- ページ送りは「‹ ›」ボタン、またはキーボードの ← → 矢印キー
- ファイルをサーバーに置いた状態でのみ動作します（ローカルファイルは制限あり）
- PDFはブラウザ標準のビューアで表示されます

---

## 🔒 セキュリティについて

このパスワード認証は**フロントエンドのみ**です。
URLを知っていればファイルに直接アクセスできます。

より強固な保護が必要な場合：
- **Netlify** → Netlify Identity または Basic Auth
- **Apache** → `.htaccess` でBasic認証
- **Nginx** → `auth_basic` 設定

---

## ✏️ カスタマイズ

| 変えたいもの | 場所 |
|---|---|
| パスワード | `const PASSWORD = "..."` |
| サイトタイトル | `<title>` タグ・ヘッダー部分 |
| ジャンル別カバー色 | `const GC = {...}` |
| 書籍の追加 | `const BOOKS = [...]` |
