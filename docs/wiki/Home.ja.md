# Nexus Compression & Recovery Studio

**Version 2.7.1**

対応する言語モデルを低ビットの因子表現に圧縮し、回復学習によって言語品質をどこまで取り戻せるか評価します。

**[ブラウザーで試す](https://rdunbar01.github.io/Nexus-Little-Bit-Compression-Recovery-/Nexus_Compression_Recovery_Studio_v2_7_Browser.html)** · [デスクトップ用コンポーネントをダウンロード](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/tree/main/releases/2.7.1) · [README](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/README.md)

試用ページを開いてインターフェースを確認し、**Check WebGPU adapter** を選択してください。Python のインストールは不要です。短時間で概要を確認するための入口です。モデルの読み込みや処理の完了時間は、入力と端末によって異なります。

ネイティブパッケージ 2.7.1、ブラウザー版 2.7.1。

## 主な機能

- ローカルのモデルとコーパスを使った低ビット因子圧縮。
- 教師モデルに基づく回復学習の制御と、対応モデルの評価。
- ブラウザー WebGPU とインストール型 PyTorch の独立したワークフロー。
- 回復実験を比較するための進捗、時間、診断記録。

## 技術的な貢献

圧縮と回復の実験をローカルの GUI で扱えるようにした独立実装です。Nexus の回復学習カリキュラムはこのワークフローを拡張するものであり、Samsung の公式製品を再現したものではありません。

## 単一 HTML ファイルを使う理由

ブラウザー版は、インターフェース、JavaScript、CSS、WGSL カーネルを単一の HTML ファイルにまとめています。ビルド手順や実行時の CDN を必要とせず、オンラインで開き、リンクを共有し、内容を確認しやすくするための構成です。ファイルに含まれるのはブラウザー用エンジンであり、モデルの重みやネイティブ PyTorch バックエンドではありません。

HTTPS 上で WebGPU 対応ブラウザーを使用してください。実行時のネットワーク要求、ネイティブのハードウェア監視、ローカルサーバーとのブリッジは無効です。実際の学習や評価には対応する入力が必要です。ネイティブ PyTorch バックエンドには完全版のダウンロードが必要です。

[English](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ko)

## Python とネイティブ実行環境の要件

- **推奨インタープリターは標準の64ビット CPython 3.12 です。** インストーラーの案内範囲は **Python 3.11–3.14** ですが、起動用スクリプト自体はこの範囲を強制しません。他のバージョンで開けても、ネイティブバックエンドの互換性を証明したことにはなりません。
- **新しい AMD 実行環境のインストールには、Windows 11 25H2 上の標準64ビット CPython 3.11–3.14 が必要です。free-threaded 版は対象外です。** 既存環境はこのインストール条件の確認前にテストされ、実行テストに成功した場合のみ再利用されます。Python とインストール済み PyTorch wheel の対応が必要です。それ以上の Python バージョン互換性は認定していません。
- 同梱のネイティブテストは **PyTorch 2.14.0+rocm10.1.0**、HIP、設定された RX 7900 XT/XTX を要求し、FP32 の順伝播・逆伝播の値が有限であることを確認します。このパッケージは Python、AMD ドライバー、コンパイラーの前提条件をインストール・変更しません。[AMD 公式互換性表](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html)を確認してください。

これらはインストーラーと実行環境の条件であり、実機 Windows・WebView2・Radeon やフルモデルの検証完了を意味しません。テスト成功はすべての精度・コンパイル方式・処理負荷を保証しません。 Recovery は Windows 11 **26H2（ビルド26300以降）**も暫定的に許可します。このコード上の許可は、プラットフォームの検証完了や AMD 公式対応範囲の拡張を意味しません。


## 目的

低ビットの因子圧縮と教師モデルを使った回復学習を試すツールです。圧縮、推論の成功、品質の回復はそれぞれ別の段階です。対応するローカルモデルとコーパスを選択してください。元のコーパス ZIP は HTML に含まれず、ローカルで選択した後にチェックサムが検証されます。

## エディションの選択

### ブラウザー版

[HTML](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/Nexus_Compression_Recovery_Studio_v2_7_Browser.html) · [README](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/README.md)

HTTPS または対応する安全な localhost オリジンで、WebGPU 対応ブラウザーを使用してください。単一 HTML に独自の JavaScript/WGSL エンジンが含まれます。対応するローカルファイルを読み込んでください。Python、PyTorch、ネイティブサービス、オンラインデータセットの取得、ネイティブ GPU テレメトリーは利用できず、実行時のネットワーク要求は遮断されます。GitHub のソース表示画面ではアプリは実行されません。

### インストール版

[2.7.1 パッケージ](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/tree/main/releases/2.7.1)のすべてのファイルを、配布時の構成を保って一緒にダウンロードしてください。番号付きのすべての `.nxd` データパーツを [Start_Nexus.py](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/releases/2.7.1/Start_Nexus.py) と同じ場所に置き、対応する Python で `python Start_Nexus.py` を実行します。同意前に[対応するガイド](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/releases/2.7.1/README.md)とインストール内容の概要を確認してください。各 `.nxd` パーツは **10,000,000 バイト以下**、インストール前の配布ファイルは1個あたり **20,000,000 バイト未満**です。アーカイブ全体、復元後のアプリ、インストール済みファイル、ダウンロードするモデルはこれを超える場合があります。異なるリリースを混在させないでください。ネイティブ PyTorch の設定・テストはインストール版の機能であり、HTML 単体の試用版の機能ではありません。

## 測定結果と制限

CPU 回帰テストや静的解析・DOM テストは、実機の Windows/Radeon/WebGPU 検証ではありません。モデル、コーパス、コンテキスト、バッチ、精度、バックエンドが等しい条件で比較してください。学習・回復、プロンプト処理、トークン生成の速度は別々の指標です。すべての環境での互換性や最高速度を保証しません。

開発者が報告した回復学習の記録値は **毎秒 2,500 トークン**です。ここで独立に再現した数値ではなく、チャット生成速度でもありません。Samsung Research の LittleBit に着想を得た独立した Nexus の取り組みであり、Samsung 公式リリースではありません。1 ビット未満の保存形式は、学習メモリーも同じビット数になることや L3 キャッシュへの常駐を証明しません。SamsungLabs LittleBit コードの CC BY-NC 4.0 を含め、適用されるライセンスを保持してください。

## 利用条件とクレジット

Rich Dunbar / Nexus Emerging Technology. Nexus が権利を持つものについては、個人利用および社内での商用テスト・評価が許可されます。配布、改変、本番環境への導入、その他の商用利用には、明示的な書面による同意が必要です。第三者のライセンスと既に付与された権利は変更されません。 [ライセンス](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/LICENSE) · [評価用の追加許諾（英語）](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/COMMERCIAL_EVALUATION_PERMISSION.md).
