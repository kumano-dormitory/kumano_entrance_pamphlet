## 座談会記事（例: `2025shinki/nuigurumi_zadankai/nuigurumi.tex`）の書き方ルール

- **ファイルの位置と命名**
  - 各座談会記事は、年度別ディレクトリ配下にサブフォルダを作り、その中に `main.tex`（または固有名）として置く  
    - 例: `2025shinki/nuigurumi_zadankai/nuigurumi.tex`

- **前文・クラス宣言**
  - 冊子に組み込むときは、`sub_article_rule.md` と同様に **クラス宣言・前文を書かない**  
    - `\documentclass`, `\usepackage`, `\begin{document}`, `\end{document}` は禁止  
    - 必要なパッケージ・レイアウトは冊子全体の `preamble.tex` で管理する
  - 既存の単体用原稿から流用する場合は、これらを削除してから `2026shinki/〜` 形式に合わせる

- **先頭の体裁**
  - 1行目に座談会タイトルを `\section{タイトル}` で書く  
    - 例: `\section{ぬいぐるみ座談会}`
  - その直後に文責を右寄せで書く  
    - 例: `\rightline{（文責：アメリカムシクイ）}`

- **座談会用マクロ**
  - 発言者ラベル用に `\talkernui` のようなマクロを使う（名前は記事ごとに自由だが、意味は明確に）  
    - 例（`nuigurumi.tex`）:
      ```tex
      \newcommand{\talkernui}[1]{\noindent{\gtfamily \bfseries#1}:}
      ```
  - 以降の本文では必ずこのマクロを使って話者を示す  
    - 例: `\talkernui{カムイ}` のようにしてから本文を書く

- **レイアウト（段組・見出し・ブロック）**
  - 座談会本文は必要に応じて `multicols` で2段組にする  
    - 例:
      ```tex
      \begin{multicols}{2}
      ...
      \end{multicols}
      ```
  - セクション区切り用の太字見出しは、`uuline`＋`Large`＋`textbf` を組み合わせて使う  
    - 例:
      ```tex
      \noindent{\uuline{\Large\textbf{自己紹介\\}}}
      ```
  - 参加者一覧などは `itembox` で囲う  
    - 例:
      ```tex
      \begin{itembox}[m]{\LARGE 参加者}
      ...
      \end{itembox}
      ```

- **脚注・注釈の使い方**
  - 会話中の補足や内輪ネタの説明は `\footnote{...}` で本文中に付す  
  - 脚注は、会話のテンポを壊さない範囲で簡潔に書くが、**内容は原稿から一文字も省略しない**（補足を削る場合は人間側の判断で）

- **本文テキストの扱い**
  - 音声起こし等から作る場合も、原稿として確定したテキストは **一文字も変えない／削らない**  
  - 句読点や改行位置の調整はレイアウト都合で行ってよいが、言い換え・意味の変更はしない

- **画像の扱い（必要な場合）**
  - 画像は記事フォルダ直下に `figures/` などを作って置く  
    - 例: `2025shinki/nuigurumi_zadankai/figures/...`
  - 冊子 `main.tex` から見た相対パスで `\includegraphics` を書く  
    - 例: `\includegraphics{2025shinki/nuigurumi_zadankai/figures/XXX.jpg}`
  - 図の基本形は `sub_article_rule.md` と同様の `figure` / `figure*`＋`minipage` を使う

- **冊子側 `main.tex` での読み込み**
  - 他のサブ記事と同様に、冊子全体の `main.tex` からは  
    - 例: `\input{2025shinki/nuigurumi_zadankai/nuigurumi}`
  - 座談会側ではクラス宣言・パッケージ指定をしない前提で設計する

