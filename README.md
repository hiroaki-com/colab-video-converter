# Make Demo GIF / MP4 

[![Python](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Colab](https://img.shields.io/badge/platform-Google%20Colab-orange.svg)](https://colab.research.google.com/github/hiroaki-com/colab-video-converter/blob/main/make_demo_gif_mp4_ja.ipynb)
[![FFmpeg](https://img.shields.io/badge/FFmpeg-compatible-blueviolet.svg)](https://ffmpeg.org/)

[English](./README_EN.md) | 日本語

![demo_ja_full](https://github.com/user-attachments/assets/43463ffe-1d36-4ddb-9317-105da243d52f)

### 概要

Google Colab環境で画面録画などの動画ファイルを、GitHub / SNS 向けの GIF または MP4 に変換するツールです。複数ファイルの結合・品質調整・再生速度変更・特定箇所へのズームをすべてノートブック上の UI で完結できます。

対応入力形式: `.mov` `.mp4` `.avi` `.mkv` `.webm`

#### 主な機能

- 複数動画の結合（ドロップダウンで結合順を指定）
- GIF / MP4（H.264）の選択出力
- プリセット品質設定（GitHub README 向け・SNS 軽量・高品質）またはカスタム指定
- 再生速度変更（0.75x 〜 2.0x、カスタム指定も可）
- ズーム機能（画面録画デモ向けの特定箇所強調）
- ローカルダウンロードまたは Google Drive への保存

#### 対象ユーザー

- 画面録画をそのまま GitHub README や SNS に使いたい開発者
- デモ動画で重要な操作部分を強調したい開発者
- ffmpeg コマンドを書かずにデモ動画を手軽に仕上げたいエンジニア
- Zenn / Qiita 向けに軽量 GIF を作りたいテクニカルライター

---

### クイックスタート

#### 実行環境

```
https://colab.research.google.com/github/hiroaki-com/colab-video-converter/blob/main/make_demo_gif_mp4_ja.ipynb
```

> CPU ランタイムで動作します。GPU は不要です。

#### 基本的な実行手順

1. Google Colab でノートブックを開きます
2. セルを上から順に実行します
3. ② で動画ファイルをアップロードします（複数選択可）
4. ③ で結合順を指定します（1 本の場合はスキップ）
5. ④ で出力形式・品質・再生速度を設定します
6. ⑤ で変換を実行します
7. ⑥ でプレビューを確認します
8. ⑦ でズーム設定を行います（オプション）
9. ⑧ で最終出力を生成します
10. ⑨ で保存先を選択して保存します

---

### 出力形式の選び方

| 形式 | 特性 | 向いている用途 | 向かない用途 |
|---|---|---|---|
| GIF | 自動再生・ループ・あらゆる Markdown で動く。256色・ファイル大 | GitHub README（自動再生必須）・Zenn / Qiita | ファイルサイズが厳しい場面 |
| MP4 (H.264) | 高品質・小容量・フルカラー。再生にはプレイヤーが必要。音声なし | X / Slack / GitHub README（クリック再生で可） | 自動再生・ループが必須の場面 |

---

### 品質設定

#### GIF プリセット

| プリセット | 横幅 | FPS | 色数 | 用途 |
|:---|:---:|:---:|:---:|:---|
| GitHub README 用 | 960px | 15fps | 256色 | README への埋め込み（推奨） |
| SNS・軽量用 | 640px | 10fps | 128色 | ファイルサイズを抑えたい場合 |
| 高品質 | 1280px | 20fps | 256色 | クオリティ優先 |
| カスタム指定 | 任意 | 任意 | 任意 | 細かく調整したい場合 |

#### MP4 プリセット

| プリセット | CRF | 目安 |
|:---|:---:|:---|
| 高品質 | 18 | ファイル大きめ |
| 標準 | 23 | バランス重視（推奨） |
| 軽量 | 28 | ファイル小さめ |
| カスタム指定 | 0–51 | 細かく調整したい場合 |

#### 再生速度

| 選択肢 | 倍率 |
|:---|:---:|
| 等倍 | 1.0x |
| 1.5 倍速 | 1.5x |
| 2.0 倍速 | 2.0x |
| 0.75 倍速 | 0.75x |
| カスタム指定 | 0.1x 〜 10.0x |

---

### ズーム機能

画面録画デモで重要な操作部分を強調できます。

![zoom_update_ja](https://github.com/user-attachments/assets/d2994db3-ec6f-4b60-bcb3-2ea783090304)

#### 使い方

1. ⑦ のプレビュー動画を再生し、ズームしたいタイムスタンプを確認
2. 「ズームを追加する」をチェック（チェック時に最初のイベントが自動追加されます）
3. 「＋ Zoomイベント追加」で追加のズームイベントを追加
4. 各イベントで以下を設定:
   - ズーム領域（3x3 グリッドから選択）
   - 最大ズーム倍率（1.1x 〜 5.0x）
   - 開始時刻: 動画を任意の位置で停止し「📍 この開始位置を記録」ボタンで反映
   - ズームイン / ホールド / ズームアウトの各時間
5. ⑧ で最終出力を生成

> 複数のズームイベントを設定できますが、時間が重ならないように注意してください。重複がある場合はエラーで通知されます。

---

### サービス別サイズ制約（2026/02 時点）

| プラットフォーム | 対応形式 | サイズ上限 |
|---|---|---|
| GitHub README | GIF / MP4 / MOV | 100 MB（動画）/ 10 MB（GIF） |
| Zenn | GIF | 3 MB |
| Qiita | GIF / MP4 | 100 MB |
| X（標準） | MP4 / MOV | 512 MB |
| Slack | GIF / MP4 / MOV 他 | 1 GB |

> GIF が 15 MB を超えた場合、ノートブックが自動で警告を表示し、軽量化の手順を案内します。

---

### アップロード上限

| 条件 | 上限目安 |
|---|---|
| 1 ファイルあたり | 〜2 GB |
| 複数ファイル | 2 GB × ファイル数 |

---

### 保存オプション

| 保存先 | 説明 |
|---|---|
| ローカルにダウンロード | ブラウザのダウンロードダイアログで保存 |
| Google Drive に保存 | 指定パスへ自動コピー（マウント込み） |
| 両方 | 上記を同時に実行 |

---

### 技術スタック

- Runtime: Google Colab (Python 3.10+)
- 変換エンジン: FFmpeg
- UI: ipywidgets
- Storage: Google Drive API / ローカルダウンロード

---

### ライセンス

MIT License. 詳細は [LICENSE](LICENSE) を参照してください。

### クレジット

- [FFmpeg](https://ffmpeg.org/) - 動画変換エンジン
- [Google Colab](https://colab.research.google.com/) - 無料実行環境

### サポート

- バグ報告: [Issues](https://github.com/hiroaki-com/colab-video-converter/issues)
- 質問・議論: [Discussions](https://github.com/hiroaki-com/colab-video-converter/discussions)
