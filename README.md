# おさんぽマルシェ新聞

直売所や畑の背景を、月1回の小さな新聞として残すための作業フォルダです。

## 基本の流れ

1. `input/material.md` に今月の素材を書く
2. 写真を `input/images/` に入れる
3. 各コーナーの下書きを作る
4. `output/YYYY-MM/article.md` に完成原稿をまとめる
5. `newspaper.html` からLINE配信用画像を作る
6. `docs/issues/YYYY-MM.html` にバックナンバーを追加する

## 文字量の目安

長文にしすぎず、スマホで読める短さを優先します。

- おさんぽ便り: 200〜350字
- 季節のお野菜: 250〜450字
- ジジババ・人情・裏話: 300〜600字
- お知らせ: 100〜250字

## フォルダ

- `input/`: 今月の素材と写真
- `output/`: 号ごとの完成原稿、画像、PDF
- `docs/`: GitHub Pagesで公開するバックナンバー
- `templates/`: HTMLや原稿の型
- `organization/`: エージェント役割や作業管理

## GitHub Pages バックナンバーの増やし方

GitHub Pages は `main` ブランチの `docs/` フォルダを公開元にします。
本番配信前のテスト号も、バックナンバー確認用として `docs/issues/` に置けます。

号を増やすときは、次の形にそろえます。

1. `output/YYYY-MM/YYYY-MM.html` をもとに `docs/issues/YYYY-MM.html` を作る
2. その号で使う画像を `docs/assets/images/YYYY-MM/` に置く
3. HTML内の画像パスを `../assets/images/YYYY-MM/画像ファイル名` に直す
4. `docs/index.html` のバックナンバー一覧に `issues/YYYY-MM.html` へのリンクを追加する
5. 変更後、ローカルで `docs/index.html` と各号のHTMLを開いて、リンクと画像表示を確認する

例:

```html
<a class="issue-link" href="issues/2026-06.html">2026年6月号：号のタイトル</a>
```

テスト号は `docs/issues/test-issue.html`、画像は `docs/assets/images/test-issue/` に置きます。

## 写真のルール

新聞で使う写真は、毎号1枚だけにします。

写真は「今月のピックアップ写真」として、1枚目の上部に入れます。
写真を1枚に決めておくと、紙面が崩れにくく、LINE配信用画像にも書き出しやすくなります。

本番号では、写真ファイル名をできるだけ次の名前にそろえます。

```text
input/images/pickup.jpg
```

素材メモには、次のように書きます。

```md
## 写真メモ

- `input/images/pickup.jpg`: 今月のピックアップ写真。1枚目に使う。
```

テスト号などで別名の写真を使う場合も、HTMLに入れる写真は1枚だけにします。

## テスト号の作り方

配信前に流れを試すときは、`output/test-issue/` を使います。
テスト号は練習用なので、公式LINEには配信しません。

### 1. 素材を書く

`input/test-material.md` に、テーマ、各コーナーの素材、お知らせ、写真メモを書きます。

写真を使う場合は `input/images/` に入れて、素材内のファイル名と実際のファイル名をそろえます。
本番号では `input/images/pickup.jpg` にそろえるのがおすすめです。
テスト号では例として `input/images/torii.jpg` を使いました。

### 2. リポーター下書きを作る

Codex に次のように頼みます。

```text
input/test-material.md を読んで、
各 profile.md に従って reporter1、reporter2、reporter3 の下書きを
output/test-issue/draft/ に作ってください。
```

下書きは次の場所に作ります。

- `output/test-issue/draft/reporter1.md`
- `output/test-issue/draft/reporter2.md`
- `output/test-issue/draft/reporter3.md`

### 3. 編集長が最終原稿をまとめる

下書きをもとに、`chief_editor` として `output/test-issue/article.md` にまとめます。

```text
chief_editor として、
output/test-issue/article.md にテスト号の最終原稿をまとめてください。
今回は配信しないテスト号なので、文章量は短めでお願いします。
```

### 4. 人間が article.md を直す

文章を少し直したくなったら、まず `output/test-issue/article.md` を直します。

`article.md` を文章の正本にしておくと、あとで迷いにくくなります。

### 5. HTML に反映する

`article.md` を直したら、Codex にこう頼みます。

```text
article.md に合わせて HTML も更新して
```

HTML は `output/test-issue/test-issue.html` に作ります。
LINE配信用画像にしやすいように、縦長の紙面として作ります。

テスト号では、たとえば次のように2枚に分けます。

- 1枚目: タイトル、今回の目的、テーマ、ピックアップ写真、おさんぽ便り
- 2枚目: 季節のお野菜、ジジババ・人情・裏話、お知らせ

ピックアップ写真は1枚だけ使います。
写真を増やしたくなっても、まずは1枚に絞ると紙面が安定します。

### 6. ブラウザで確認する

HTML をブラウザで開いて、文字のはみ出し、写真の表示、2枚の分かれ方を確認します。

必要ならスクリーンショットを作ります。

- `output/test-issue/test-issue-sheet-1.png`
- `output/test-issue/test-issue-sheet-2.png`
- `output/test-issue/test-issue-full-screenshot.png`

### 7. また直す

見てから直したいところが出たら、基本は `article.md` を直します。
見た目だけの調整なら `test-issue.html` を直します。

おすすめの流れは次の通りです。

```text
素材を書く
下書きを作る
article.md にまとめる
article.md を人間が少し直す
HTML に反映する
ブラウザとスクリーンショットで確認する
また少し直す
```
