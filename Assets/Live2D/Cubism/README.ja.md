[English](README.md) / [日本語](README.ja.md)

---

# CubismUnityComponents

Unity用のCubismSDKのオープンコンポーネントです。

SDKパッケージのダウンロードページをお探しの場合は、[ダウンロードページ](https://www.live2d.com/download/cubism-sdk/download-unity/)にアクセスしてください。

## ライセンス

ご使用前に[ライセンス](LICENSE.md)をお読みください。

## お知らせ

ご使用前に[お知らせ](NOTICE.ja.md)をお読みください。

## 構造

### コンポーネント

コンポーネントは役割ごとにグループ化されており、このグループ化はフォルダー構造と名前空間の両方に反映されます。

#### Coreラッパー

このグループのコンポーネントとクラスは、CubismコアライブラリをC#とUnityにラップするためのレイヤーであり、`./Assets/Live2D/Cubism/Core`にあります。

#### フレームワーク

このグループのコンポーネントとクラスは、リップシンクやCubismの組み込み用ファイルとUnityの統合などの追加機能を提供します。CubismファイルをプレハブとAnimationClipに変換するのはここで行われます。すべてのフレームワークコードは`./Assets/Live2D/Cubism/Framework`にあります。

#### レンダリング

このグループのコンポーネントとクラスは、Unityの機能を使用してCubismモデルをレンダリングする機能を提供します。コードは、`./Assets/Live2D/Cubism/Rendering`にあります。

### エディター拡張機能

Unity Editor拡張機能は、`./Assets/Live2D/Cubism/Editor`にあります。

### リソース

シェーダー等のアセットのリソースは、`./Assets/Live2D/Cubism/Rendering/Resources`にあります。

## 開発環境

| Unity | バージョン |
| --- | --- |
| Tech Stream | 2022.2.2f1 |
| LTS | 2021.3.16f1 |
| LTS | 2020.3.43f1 |

| ライブラリ / ツール | バージョン |
| --- | --- |
| Android SDK / NDK | *1 |
| Visual Studio 2022 | 17.4.4 |
| Windows SDK | 10.0.22621.0 |
| Xcode | 14.2 |

*1 Unityに組み込まれたライブラリまたは推奨ライブラリを使用してください。

### C#コンパイラ

Unity2018.4以降でサポートされているRoslynまたはmcsコンパイラを使用してビルドします。

注：mcsコンパイラは非推奨であり、ビルドのみをチェックします。

使用できるC#のバージョンについては、次の公式ドキュメントを参照してください。

https://docs.unity3d.com/ja/2018.4/Manual/CSharpCompiler.html

## テスト済みの環境

| プラットフォーム | バージョン |
| --- | --- |
| Android | 13 |
| iOS | 16.2 |
| iPadOS | 16.2 |
| Ubuntu | 20.04.5 |
| macOS | 12.6.2 |
| Windows 10 | 22H2 |
| Google Chrome | 109.0.5414.75 |
| Chrome OS 64bit (x86_64) | 108.0.5359.172 |
| Chrome OS 32bit (ARMv8) (*2) | 108.0.5359.172 |

*2 Android向けAPKファイルでの動作確認です。

## ブランチ

最新の機能や修正をお探しの場合、`develop`ブランチをご確認ください。

`master`ブランチは、公式のSDKリリースごとに`develop`ブランチと同期されます。

## 使用法

`./Assets`の下にあるすべてのファイルを、Unityプロジェクト内のLive2DCubismSDKがあるフォルダーにコピーしてください。

### unsafeブロック

Coreラッパーでは、unsafeコードのブロックを許可する必要があり、Unityが作成するC#プロジェクトにはそれに応じてパッチが適用されます。unsafeコードを選択できない場合、現在のところ最善の方法は、コンポーネントをコンパイルして、そのdllをUnityプロジェクトに適用することです。

## プロジェクトへの貢献

プロジェクトに貢献する方法はたくさんあります。バグのログの記録、このGitHubでのプルリクエストの送信、Live2Dコミュニティでの問題の報告と提案の作成です。

### フォークとプルリクエスト

修正、改善、さらには新機能をもたらすかどうかにかかわらず、プルリクエストに感謝します。ただし、ラッパーは可能な限り軽量で浅くなるように設計されているため、バグ修正とメモリ/パフォーマンスの改善のみを行う必要があることに注意してください。メインリポジトリを可能な限りクリーンに保つために、必要に応じて個人用フォークと機能ブランチを作成してください。

### バグ

Live2Dコミュニティでは、問題のレポートと機能リクエストを定期的にチェックしています。バグレポートを提出する前に、Live2Dコミュニティで検索して、問題のレポートまたは機能リクエストがすでに投稿されているかどうかを確認してください。問題がすでに存在する場合は、関連するコメントを追記してください。

### 提案

SDKの将来についてのフィードバックにも関心があります。Live2Dコミュニティで提案や機能のリクエストを送信できます。このプロセスをより効果的にするために、それらをより明確に定義するのに役立つより多くの情報を含めるようお願いしています。

## コーディングガイドライン

### ネーミング

可能な限り、[Microsoftガイドライン](https://msdn.microsoft.com/en-us/library/ms229002(v=vs.110).aspx)に準拠するようにしてください。プライベートフィールドには、アンダースコアで始まる小文字の名前を付けます。

### スタイル

- Unity Editor拡張機能では、LINQやその他すべての凝ったものを使って表現力豊かなコードを書いてみてください。
- それ以外の場所ではLINQを使用せず、`foreach`よりも`for`を優先してください。
- アクセス修飾子を明示的にするようにしてください。`void Update()`ではなく `private void Update()`を使いましょう。

## コミュニティ

ご不明な点がございましたら、公式のLive2Dコミュニティに参加して、他のユーザーと話し合ってください。

- [Live2D 公式コミュニティ](https://creatorsforum.live2d.com/)
- [Live2D community (English)](https://community.live2d.com/)
