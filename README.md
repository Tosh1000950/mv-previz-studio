# 2.5D MV Previz Studio

**動画生成AIに「カメラワーク」を伝えるための、下書き（プリビズ／アニメティクス）作成ツール。**

AI video generators are bad at following camera directions written in text.
So design the shot first: place your storyboard images in a 3D space, move a real
3D camera to your music's waveform timeline, then export the result as
first/last-frame PNGs and a guide video to feed into the generator.

ブラウザで開くだけで動きます（インストール不要）。楽曲の波形に合わせてカットを組み、
絵コンテ画像を3D空間に置いてカメラを回し、動画生成AIへの入力素材
（開始／終了フレームPNG・ガイド動画WebM）を書き出すための道具です。

> 個人制作のための簡易ツールです。プロ向けプリビズソフトの代替ではなく、
> 「生成前に、カメラとタイミングを目で確認する」ための最小構成になっています。

## 使い方 / How to use

1. `index.html` をブラウザで開く（ネット接続が必要：Three.js等をCDNから読みます）
2. デモが再生されるので、まず Space キーで再生・停止を試す
3. 上部から自分の楽曲（mp3/wav等）を読み込むと、波形がタイムラインに出ます
4. レイヤー（背景・中景・キャラ・前景）に手持ちの画像を読み込む
5. カットごとにカメラの開始・終了を数値で決める（自由カメラモードで探して「視点を記録」も可）
6. 書き出し：
   - **開始PNG／終了PNG** … 動画生成AIの First / Last Frame 指定用
   - **カット動画／全体録画（WebM）** … Video-to-Video やモーション参照用のガイド動画

作業データはJSONで保存・読み込みできます（`sample_project.json` が見本です）。

## できること / Features

- 楽曲波形タイムラインとカット管理（開始・終了秒の調整）
- 3Dカメラワーク（位置・注視点・FOV・ロール、開始→終了のイージング補間）
- 4レイヤーの奥行き配置（視差）、キャラの移動・回転・拡縮、歩行バウンス
- First/Last Frame PNG とガイド動画（WebM）の書き出し
- プロジェクトのJSON保存・読み込み

## できないこと / Limitations

- キャラのポーズ変化や関節アニメーション（歩く・座る等の身体の動きは再現しません）
- カメラは開始・終了の2点補間だけ（途中のキーフレームや曲線編集はなし）
- 書き出した数値をプロンプトにしても、動画生成AIに完全再現はできません。
  ガイド画像・ガイド動画として渡すのが前提の設計です

## 由来 / Background

AIにMV制作を任せて盛大に失敗した経験から生まれました。
失敗談はこちら：[AIでMVを個人制作しようとして、盛大に躓いた話](https://zenn.dev/tosh1000950/articles/521eb49923fb87)（Zenn）

## License

MIT License — see [LICENSE](LICENSE).
This tool itself was drafted with the help of Gemini (Hydrogen) and reviewed/hardened by hand.
Third-party libraries (Three.js, Tailwind CSS) are loaded from CDN under their own licenses.
