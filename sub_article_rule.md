## サブ記事（`2026shinki/〜/main.tex` など）のルール

- **クラス宣言・前文は書かない**
  - `\documentclass{...}` や `\usepackage{...}`、`\begin{document}` / `\end{document}` は **禁止**
  - 冊子全体の `main.tex` 側で一括管理する

- **記事ファイルの先頭構成**
  - 1行目に記事タイトルを `\section{タイトル}` として書く  
    - 例: `\section{ニート向け時間の潰し方Tier}`
  - その直後に文責を右寄せで書く  
    - 例: `\rightline{（文責:かりね）}`

- **本文の扱い**
  - 原稿テキストは **一文字も削らず** LaTeX に起こす
  - 自動校正・言い換え・省略は行わない  
    - 誤変換の修正など、著者の意図を変えうる修正は必ず人間側で判断する
  
- **段落について**
  - `\section`は`\subsection`に変換する
  - あくまでも記事一つがsectionとしての立ち位置である。
  - 段落は`\subsection`で表現する。
  - `\subsection`は`\subsubsection`に変換する

- **画像の扱い**
  - 画像ファイルは、原則として  
    - `2026shinki/<記事フォルダ名>/images/` に配置する
  - `\includegraphics` のパスは、**冊子全体の `main.tex` から見た相対パス** で書く  
    - 例: `\includegraphics{2026shinki/neet_kill_time/images/Tier.png}`
  - 図の基本書式  
    - 例:
      ```tex
      \begin{figure}[h]
        \centering
        \includegraphics[width=0.8\linewidth]{2026shinki/neet_kill_time/images/XXXX.png}
        \caption{キャプション}
      \end{figure}
      ```

- **`main.tex`（冊子全体）側の指定**
  - サブ記事は `\input{2026shinki/<記事フォルダ名>/main}` で読み込む
  - サブ記事側でクラス宣言やパッケージ読み込みをしない前提で設計する

