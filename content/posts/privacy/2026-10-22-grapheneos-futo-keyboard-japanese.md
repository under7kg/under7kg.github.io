---
title: "GrapheneOS: FUTO Keyboardで日本語入力"
description: "GrapheneOSでFUTO Keyboardを導入し、完全オフラインの日本語音声入力を構築する手順を解説。MozcやFcitx5との比較からプライバシー重視の最適解を見抜く"
slug: privacy/grapheneos-futo-keyboard-japanese
date: 2026-10-22T10:00:00+09:00
categories: [ nomad ]
tags: [ GrapheneOS, privacy, foss ]
---

GrapheneOSを使っていて、じわじわストレスになってくるのが日本語入力だ。

![Futo Keyboard](/images/2026-07-12-futo.png)

定番だったMozcはいつの間にかF-Droidから消えていた。Fcitx5もAndroid版が最近出てきたので試してみたのだが、変換がもたつく感じで、あまり印象が良くない。かといってGboardではプライバシー重視でGrapheneOSを選んだ理由を自分で否定することになってしまう。

そんな状況で**FUTO Keyboard**に行き着いた。なぜ今まで引っかからなかったのか不思議なくらいで、GitHubのリリース履歴を見るとv0.1.20（2024年6月）から公開されている。音声入力にも対応（ここが大きい）している。

インストールは３段階：
1. アプリ: FDroid ([Repo](https://app.futo.org/fdroid/repo/))かObtanium ([Github Release](https://github.com/futo-org/android-keyboard/releases)）
2. 辞書ファイル: https://keyboard.futo.org/dictionaries?locale=ja
3. 音声入力モデル: https://keyboard.futo.org/voice-input-models

インストール後、アプリの設定から日本語キーボードを選択し、ダウンロードした辞書と音声モデルをそれぞれ読み込ませる。それだけだ。

肝心の音声認識だが、あまり滑舌の良くない自分の日本語でも、思いのほかちゃんと拾ってくれる。完全オフラインでこの精度なら十分実用に耐える。LineageOSやGrapheneOSを人に勧めるときに「日本語入力は？」と必ず聞かれるのだが、これでひとつ答えが用意できた気がした。

![Futo Keyboard](/images/2026-07-12-futo-dic.png)
![Futo Keyboard](/images/2026-07-12-futo-voice.png)

---

## おまけ：日本語入力アプリ

AndroidのFOSS系だと日本語入力関連が開発者が少ないのか、何ともな感じ。昔は京大の研究所とかSonyの技術者？の方々が割といて活発だった感じも・・・（こんなところにも国力の低下を感じる。大袈裟か。。）

他にも選択肢がないわけではないので、整理しておく。

AndroidのFOSS界隈は日本語IMEの開発者が少ないように思える。昔は京大の研究所やSonyのエンジニアあたりが活発に関わっていた記憶があるのだが、最近はめっきり静か。。少し寂しいわな。

## 選択肢の全体像

| IME                                         | 変換精度               | プライバシー         | 入手方法                                                                                           | 状態                       |
| ------------------------------------------- | ------------------ | -------------- | ---------------------------------------------------------------------------------------------- | ------------------------ |
| [FUTO Keyboard](https://keyboard.futo.org/) | 発展途上               | 最高（完全オフライン）    | 公式サイト/GitHub/Play Store                                                                        | 積極開発中                    |
| Mozc                                        | 最高峰                | 良好（オフライン動作）    | [GitHubソース](https://github.com/google/mozc/blob/master/docs/build_mozc_for_android.md)から自分でビルド | F-Droidから削除              |
| Fcitx5(Android版)                            | Anthy採用 | 良好（オフライン動作）    | F-Droid/GitHub                                                                                 | メンテナンス頻度は低め              |
| Gboard                                      | 最も賢い | 懸念あり（Google送信） | Play Store                                                                                     | GrapheneOSはmicroGなしで制限あり |

## FUTO Keyboardの特徴

- 100%オフライン動作、通信一切なし
- **オフライン音声入力**が最大の売り（Whisperベースのローカル音声認識）
- 独自のスワイプ入力エンジン搭載
- 買い切りライセンス（ソースファーストライセンス、OSI承認のオープンソースではない）
- **無料版の制限**：基本のタイピング・変換・スワイプ入力は無期限無料、音声入力機能のみトライアル期間後に購入が必要
- GrapheneOSの「ネットに繋がらないキーボード」という哲学と合致

## Mozc（訂正・確定事項）

- 変換精度は日本語IMEの中で最高峰（Google日本語入力の系譜）
- **F-Droidからは既に削除されている**（BazelベースのビルドシステムがF-Droidの自動ビルドパイプラインと相性が悪いことが一因と推測）
- 現在の入手方法は**GitHubのソースコードから自分でビルドする**しかない状況
- ビルド後は署名検証など自己責任での運用が前提

## Fcitx5(Android版) の訂正

- 当初「Mozcエンジンを使うことが多い」と説明したが、これは誤り
- 正しくは**Anthy**（またはその派生）ベースの実装が主流
- AnthyはMozcより変換精度・学習機能で劣る古典的なエンジン
- Fcitx5-Linuxでは`fcitx5-mozc`パッケージでMozc統合が可能だが、Android版では同様の統合は主流ではない

## 変換精度の序列（確定版）

**Mozc（自前ビルド）> Anthy(Fcitx5) ≈ FUTO(発展途上)**

## 結論・現実的な運用方針

1. **プライバシー最優先＋音声入力を使いたい** → FUTO Keyboard
2. **変換精度最優先** → MozcをGitHubから自分でビルド（手間はかかるが最高精度）
3. **妥協案** → Fcitx5(Anthy)、ただし精度はMozcに劣る
