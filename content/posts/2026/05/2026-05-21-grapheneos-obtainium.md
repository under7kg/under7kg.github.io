---
title: "アプリ管理はObtainiumで一本化"
description: "GrapheneOSでObtainiumにF-DroidのURLを登録しアプリ管理を一本化する方法。Proton Pass・AntennaPodなどお気に入りアプリの設定例も紹介。"
slug: privacy/grapheneos-obtainium
date: 2026-05-21T09:00:00+09:00
categories: [ nomad ]
tags: [ GrapheneOS, appstore, foss ]
comments: false
---
![ObtainiumにF-Droid](/images/2026-06-07-proton.png)

GrapheneOSにはGoogle Playがない。アプリの導入はF-DroidかAPKの直接入手が基本になるが、管理先が複数に渡るとアップデートの見落としが起こる罠がある。

## 二刀流の限界

これまで[F-Droid](https://fdroid.org)をメインのアプリストアとし、F-Droidに登録されていないアプリは[Obtainium](https://github.com/ImranR98/Obtainium)でGitHubのリリースページから直接インストールする、「**二刀流**」で運用してきた。ところが、F-Droidには登録されているのにGitHubにはソースコードのみでリリース用APKが存在しないアプリがいくつかある。
  
![Proton Github](/images/2026-06-07-proton-github.png)

こうしたアプリは、F-Droidのページから手動でAPKをダウンロードしつつ、ObtainiumにはGitHubのURLを登録してアップデートの有無だけ確認する……ど〜〜もすっきりしない運用になる。

## ObtainiumにF-Droid App Page urlを登録できる！
![ObtainiumにF-Droid](/images/2026-06-07-proton-fdroid.png)

F-DroidのアプリページURLをそのままObtainiumに登録できる。いつから可能になったのかは分からぬが、
F-DroidのURLを直接登録できると分かったことで、アプリ管理の完全一本化がようやく現実的になる

## お気に入りアプリ
その他、同様の方法が使えるお気に入りアプリも確認。(スッキリ！)

- **Proton Pass** : `https://f-droid.org/packages/proton.android.pass.fdroid/`
- **AntennaPod** : `https://f-droid.org/packages/de.danoeh.antennapod/`
- **Etar** : `https://f-droid.org/packages/ws.xsoh.etar/`
- **Suntimes** : `https://f-droid.org/packages/com.forrestguice.suntimeswidget/`
- **Suntimes Calendars** : `https://f-droid.org/packages/com.forrestguice.suntimescalendars/`

GrapheneOS＋Obtainiumの組み合わせは、プライバシーとコントロールの両立という点でも理にかなった構成だと改めて感じる（お勧めします）。

---

**参照**
- **Breezy Weather**の[インストールガイド](https://github.com/breezy-weather/breezy-weather/blob/main/INSTALL.md)
- [中級者向けGrapheneOSガイド](/grapheneos-wise-manual)
