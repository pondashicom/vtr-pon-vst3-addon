# 同梱する第三者ライブラリの対応ソース

Qtの共有ライブラリはQt 6.8.3公式配布版です。独自のコード修正はありません。配布ツールによるQtCoreの配置パス調整は行います。Qt内部の第三者コードはQtソースに含まれます。Mesa／LLVMはQt配布のソフトウェア描画DLLに対応します。

バイナリを受領した方へ、同梱するライブラリの対応ソースと適用した修正を請求に応じて提供します。この申し出はこの版の最終配布日から少なくとも3年間有効です。製品名・版・ライブラリ名を添えて [info@pondashi.com](mailto:info@pondashi.com) へご連絡ください。電子的な提供は無償、物理媒体も提供実費を超える料金は請求しません。上流の取得先が使えない場合もこの窓口から請求できます。

Qtの改変版への交換: 本体とアドオンを終了し、アドオンの `audio-addons/` 内のDLLと対応するプラグインを互換の改変版に交換します。LGPLの権利に従う改変・交換と、そのデバッグに必要なリバースエンジニアリングを妨げる条件はありません。EXEは自作MITソースとVST SDKから生成できます。生成手順はリポジトリのBUILDING.mdです。

## 版固定の取得先

- llvm 3.6.2: [llvm-3.6.2.src.tar.xz](https://releases.llvm.org/3.6.2/llvm-3.6.2.src.tar.xz)
  SHA-256: `f60dc158bfda6822de167e87275848969f0558b3134892ff54fced87e4667b94`

- mesa 11.2.2: [mesa-11.2.2.tar.xz](https://archive.mesa3d.org/older-versions/11.x/11.2.2/mesa-11.2.2.tar.xz)
  SHA-256: `40e148812388ec7c6d7b6657d5a16e2e8dabba8b97ddfceea5197947647bdfb4`

- qtbase 6.8.3: [qtbase-everywhere-src-6.8.3.tar.xz](https://download.qt.io/archive/qt/6.8/6.8.3/submodules/qtbase-everywhere-src-6.8.3.tar.xz)
  SHA-256: `56001b905601bb9023d399f3ba780d7fa940f3e4861e496a7c490331f49e0b80`

- qtsvg 6.8.3: [qtsvg-everywhere-src-6.8.3.tar.xz](https://download.qt.io/archive/qt/6.8/6.8.3/submodules/qtsvg-everywhere-src-6.8.3.tar.xz)
  SHA-256: `35eb516460f00f264eb504baa253432384351cf23fb9980a5857190e8deef438`
