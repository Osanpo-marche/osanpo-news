# おさんぽマルシェ新聞

直売所や畑の背景を、月1回の小さな新聞として残すための作業フォルダです。

## 基本の流れ

1. `input/material.md` に今月の素材を書く
2. 写真を `input/images/` に入れる
3. 各コーナーの下書きを作る
4. `output/YYYY-MM/article.md` に完成原稿をまとめる
5. `newspaper.html` からLINE配信用画像を作る
6. `docs/issues/YYYY-MM.html` にバックナンバーを追加する

素材は `templates/material.md` の形を毎号の基本にします。
新しい号を作るときは、`templates/material.md` を `input/material.md` に写してから書き込みます。

## 文字量の目安

長文にしすぎず、スマホで読める短さを優先します。

- おさんぽ便り: 200〜350字
- 季節のお野菜: 250〜450字
- 第三枠（ジジババ・人情・裏話 / 温故知新）: 300〜600字
- 野食育: 400〜800字
- お知らせ: 100〜250字

## 第三枠の使い分け

第三枠は、号によって「ジジババ・人情・裏話」または「温故知新」を選びます。

「ジジババ・人情・裏話」は、会話、畑での出来事、直売所の裏話、お客さんとのやり取りなど、ネット不要の人情話を扱います。

「温故知新」は、オラが選んだ動画、記事、本、昔の言葉などを入口にして、今の畑、直売所、暮らしへつなげるキュレーション枠です。出典URLや題材を素材に残し、元ネタの要約だけで終わらせず、「昔からある知恵」と「いま目の前にある現実」がつながる読み物にします。

動画や記事を使うときは、素材に次のように書きます。

```md
## 第三枠：ジジババ・人情・裏話 または 温故知新

### 温故知新

- 今回の題材: 養老孟司先生の動画から、情報化社会と生きた現実について考える
- 出典URL: https://www.youtube.com/watch?v=2Y1g3-v3oVI
- 心に残った考え、言葉、場面: 情報は変わらないが、人間や自然は変わり続ける
- 昔の知恵や言葉とのつながり: 方丈記「ゆく河の流れは絶えずして、しかももとの水にあらず」
- 畑、直売所、暮らしにつなげたいこと: 画面の情報だけでなく、土や季節に触れる実感を大事にする
```

## 野食育の下書き

連載「開墾からはじまる野食育 〜荒れ地から直売所へ、紡ぐ生きた知恵の記憶〜」は、`reporter4` が担当します。

まず、毎月の `input/material.md` にある野食育の欄へ、思い出したことを素材として書きます。
文章にまとめなくても、箇条書き、話し言葉、写真についてのメモで大丈夫です。

書けたら Codex に次のように頼みます。

```text
input/material.md の野食育の素材を読んで、
reporter4 の profile.md に従って下書きを作って。
```

下書きを読んで、言い回しや事実関係を直したいときは、そのまま Codex に伝えます。
本人の言葉を残すことを優先し、勝手に話を膨らませない連載にします。
書き手の熱量は大切にしながら、価値観を押し付けず、読者が自分で感じられる余白を残します。
伝えたいことが多いときは、無理に1回へ詰め込まず次回以降へつなぎます。

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

新聞で使う写真は、基本の「今月のピックアップ写真」と、野食育の記録写真に分けます。

ピックアップ写真は毎号1枚だけにして、1枚目の上部に入れます。
本番号では、写真ファイル名をできるだけ次の名前にそろえます。

```text
input/images/pickup.jpg
```

野食育では、開墾当時の様子や人との出会いを伝えるために、過去の写真も使えます。
1回の記事につき1〜3枚を目安にして、できるだけ次の名前にそろえます。

```text
input/images/remember-01.jpg
input/images/remember-02.jpg
input/images/remember-03.jpg
```

写真が入りきらない場合は、小さく詰め込まず、野食育のページを増やします。
LINE配信用画像が2枚を超えても、読みやすさを優先します。

素材メモには、次のように書きます。

```md
## 写真メモ

- `input/images/pickup.jpg`: 今月のピックアップ写真。1枚目に使う。
- `input/images/remember-01.jpg`: 野食育で使う。開墾を始めた頃の畑。
- `input/images/remember-02.jpg`: 野食育で使う。写真にまつわる出来事や写っている人。
```

テスト号などで別名の写真を使う場合も、素材メモに用途を書きます。

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
各 profile.md に従って reporter1、reporter2、reporter3、reporter4 の下書きを
output/test-issue/draft/ に作ってください。
```

下書きは次の場所に作ります。

- `output/test-issue/draft/reporter1.md`
- `output/test-issue/draft/reporter2.md`
- `output/test-issue/draft/reporter3.md`
- `output/test-issue/draft/reporter4.md`

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

野食育を載せる号では、必要に応じて野食育のページを追加します。
野食育の記録写真は1〜3枚を目安にして、本文と一緒に配置します。

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
