# 配布条件・第三者通知 — 0.3.0

## 自作コード

Copyright (c) 2026 Tetsu Suzuki. 自作コードは[MIT License](MIT.txt)です。原文の著作権・許諾通知を保持してください。無保証・責任制限は原文によります。利用者の制作目的に非商用限定の条件を追加しません。

## インストール時の同意

パッケージのMIT原文を本体が同意対象として表示します。通知は別に閲覧できます。拒否・取り消しではそのパッケージを適用しません。更新版では文書と同意を改めて確認します。これによってMITやLGPLで認められた権利を減らすものではありません。

## 外部ソフト

Qt 6.8.3のRelease共有ライブラリ・プラグインとMicrosoft Visual C++再頒布DLLはパッケージに含まれます。別のVST Runtime導入は不要です。使用するWindows x64・ステレオ対応VST3エフェクトと、その製品のライセンスを別途用意してください。

ATEM Software、NDI Runtime／Tools、Desktop Video、利用者のVST3プラグインはこのパッケージに含まれません。外部ソフトを導入するときはその提供元の契約を確認・承諾してください。アドオンの同意操作は外部インストーラーの同意を代行しません。SDKは生成する開発者だけが別途取得して契約を確認します。

## 生成元と境界

使用するSDKは VST 3 SDK 3.8.1（v3.8.1_build_84）とQt 6.8.3。配置は `audio-addons/vtr-pon-vst3-addon.exe`、実行契約は `vst-protocol-v2`です。DeckLinkの追加Output ABIはv1です。

SDK本体、生成ヘッダー、IDL、サンプル、テストDLL、デバッグ情報、ベンダーRuntime、他者のプラグインは配布しません。SDK由来の必要なコード・通知と、次項の同梱依存の条件を自作MITと区別します。

## 同梱する依存

- VST 3 SDK 3.8.1: Steinberg Media Technologies GmbH、MIT。[原文](third-party/VST3-SDK-LICENSE.txt)。SDKの必要コードを実行ファイルへリンクし、SDK全体と利用者のプラグインは同梱しません。
- Qt 6.8.3: Copyright (C) The Qt Company Ltd. and other contributors. Core・Gui・Widgets・Svgと必要なWindows／画像プラグインを共有ライブラリとして使用し、LGPL-3.0-onlyを選択します。[LGPL 3](third-party/qt/LGPL-3.0-only.txt)・[GPL 3](third-party/qt/GPL-3.0-only.txt)・[内包コードの通知](third-party/qt/ATTRIBUTIONS.md)を収録します。Qt EntryPointはBSD-3-Clause、FreeTypeはFTLを選択します。Parts of this software are copyright © The FreeType Project (www.freetype.org). All rights reserved. This software is based in part on the work of the Independent JPEG Group.
- Mesa 11.2.2／LLVM 3.6.2: `opengl32sw.dll` のソフトウェア描画。MIT／NCSAの通知を `third-party/mesa/` と `third-party/llvm/` に保持します。
- Microsoft Visual C++ Runtime 14.42.34438.0、D3Dcompiler 6.3.9600.16384、DXC 1.7.2308.16／DXIL 101.7.2308.24: Microsoft Corporation。未改変の再頒布DLLです。`third-party/microsoft/` に通知と使用した許諾条件のテキストを収録します。VC++インストーラーは含みません。

Qt DLLのビルド済みコードへの独自修正はありません。配布ツールによるQtCoreの配置パス調整は行います。[対応ソースと交換手順](THIRD-PARTY-SOURCES.md)を参照してください。LGPLライブラリの改変・交換と、そのデバッグのためのリバースエンジニアリングを妨げる独自の条件は設けません。

VST is a trademark of Steinberg Media Technologies GmbH. Qt is a trademark of The Qt Company Ltd.
