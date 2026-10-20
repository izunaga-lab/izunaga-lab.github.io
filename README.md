# 〇〇研究室 ウェブサイト

Hugo で作成した研究室ウェブサイトです．main ブランチに push すると GitHub Actions で自動的に公開されます．

## 手元で確認する

Hugo（extended 版，v0.156 以降）をインストールしてから，このフォルダで次を実行します．

```bash
hugo server
```

ブラウザで http://localhost:1313 を開くと確認できます．ファイルを保存すると自動で再読み込みされます．

## よくある更新作業

| やりたいこと | 編集するファイル |
| --- | --- |
| お知らせを追加する | `hugo new content news/2026-11-01-xxx.md` で作成して本文を書く |
| メンバーを追加・更新する | `data/members.yaml` |
| 論文・発表・受賞を追加する | `data/publications.yaml` |
| 進路を追加する | `data/careers.yaml` |
| 研究内容・ゼミ情報を書き換える | `content/about/research.md`，`content/about/seminar.md` |
| トップページの紹介文 | `content/_index.md` |
| 研究室名・住所・メール | `hugo.toml` の `[params]` |
| 色やフォント | `assets/css/style.css` の先頭（`:root`） |

YAML はインデント（字下げ）がずれるとビルドが失敗します．既存の行をコピーして書き換えるのが安全です．

### 年度替わりのチェックリスト

1. `data/members.yaml` の学年を更新する
2. 卒業・修了したメンバーを `alumni` に移す
3. `data/careers.yaml` に新しい年度の進路を追加する
4. 新メンバーを追加する

## ファイル構成

```
.
├── hugo.toml                  サイト全体の設定・メニュー
├── content/                   各ページの本文（Markdown）
│   ├── _index.md              トップページの紹介文
│   ├── about/                 研究室紹介（研究内容・進路状況・ゼミ情報）
│   ├── members/               メンバーページ（表示内容は data/members.yaml）
│   ├── publications/          研究成果ページ（表示内容は data/publications.yaml）
│   └── news/                  お知らせ
├── data/                      メンバー・研究成果・進路のデータ
├── layouts/                   HTML テンプレート
├── assets/css/style.css       デザイン
├── static/                    画像などそのまま置くファイル
└── .github/workflows/         自動公開の設定
```

## 公開の設定（最初の1回だけ）

1. GitHub のリポジトリの Settings → Pages を開く
2. Source を「GitHub Actions」にする
3. main に push すると，Actions タブでビルドが始まり，数分で公開されます

Hugo のバージョンを上げるときは，`.github/workflows/hugo.yaml` の `hugo-version` も手元と同じ値に変更してください．
