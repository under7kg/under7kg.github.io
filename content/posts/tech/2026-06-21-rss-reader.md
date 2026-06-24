---
title: "RSS Readerのススメ：アルゴリズムの外側で生きる情報収集術"
slug: tech/rss-reader
date: 2026-06-21T00:00:00+04:00
categories: [ nomad ]
tags: [ privacy, foss, recommend ]
ShowToc: true
TocOpen: false
comments: false
---

広告収入が命のメディア企業から長年毛嫌いされ、Google Readerのサービス終了以降は「死んだ」と言われ続けてきたRSS（Really Simple Syndication）。それでも世界中の愛好家は今も使い続けています。理由はシンプルです——アルゴリズムが介在しないからです。

## なぜ今でもRSSが強いのか

Cory Doctorowが「エンシットフィケーション（**enshittification**）」と呼ぶプラットフォームの劣化——広告だらけのタイムライン、アルゴリズム優先のおすすめ、行動データの収集——これらすべてを、RSSは根本から回避します。

- **アルゴリズムに支配されない**：自分が選んだソースの記事だけが、時系列で届きます。「おすすめ」も広告も混入しません。
- **既読管理が完結する**：フィードを開いた時点で管理が終わります。SNSのような「見落とし」が起きにくいのが実用的な強みです。
- **購読リストは永続する資産**：プラットフォームが消えても、フィードURLは残ります。フォロワー数もアルゴリズムも関係ありません。
- **ニッチな情報源に強い**：個人ブログ、学術機関、政府の統計フィードなど、SNSでは辿り着けない発信者と直接繋がれます。
- **プライバシーが守られる**：GoogleやMetaに読書履歴を渡しません。多くのFOSSクライアントはトラッキングを一切行いません。
- **長期的に安定**：枯れた技術は安定しています。サイトがフィードを提供し続ける限り、同じ方法で購読できます。

2025〜2026年にかけて、Hacker NewsやMastodonコミュニティではRSS活用の話題が定期的に上位に来るようになりました。「**アルゴリズムに支配されない情報空間を自分で構築する**」という考え方が、独立系ウェブ（Indie Web）のムーブメントとともに静かに広がっています。

## おすすめFOSS RSSクライアント

オープン規格であるRSSには、FOSS（Free and Open Source Software）のクライアントが豊富に揃っています。費用は不要、データは売られない、ベンダーロックインもありません。

### iOS & macOS ── [NetNewsWire](https://github.com/Ranchero-Software/NetNewsWire)

![NetNewsWire](https://netnewswire.com/images/NNW7-Light.png)
Brent Simmons氏が個人で開発・維持する、完全無料・完全オープンソースのフィードリーダーです。macOSとiOSで同期でき、動作は軽く、余計な機能がありません。iCloud同期のほか、FeedlyやFreshRSSとの連携にも対応しています。広告もサブスク料金もトラッキングも一切なく、「Apple環境でRSSを始めるならまずこれ」という評価がRedditやMastodonで圧倒的です。

### Android ── [Feeder](https://github.com/spacecowboy/Feeder)

![Feeder](/images/2026-06-21-rssreader-feeder.png)
F-Droid（Google Playに依存しない完全FOSSのアプリストア）でも入手できる、Androidの定番アプリです。軽量でクリーンなUI、完全オフライン対応。サーバー不要でローカル管理したい方に向いています。Mastodonコミュニティでも「Androidに移ってからずっとFeeder」という声が多く見られます。

### セルフホスト型 ── [FreshRSS](https://github.com/FreshRSS/FreshRSS)

![FreshRSS](/images/2026-06-21-rssreader-freshrss.png)
自分のサーバーやNASに置いて運用する、ウェブベースのフィードアグリゲーターです。NetNewsWire（iOS/macOS）やFeedMe（Android）など外部クライアントからもアクセスできます。「クラウドには預けたくないが、複数デバイスで同期したい」という方に最適な選択肢です。PHP製で動作が軽く、Raspberry Pi程度のスペックでも問題なく動きます。

### セルフホスト型（ミニマリスト向け） ── [Miniflux](https://github.com/miniflux/v2)

![Miniflux](https://miniflux.app/images/overview.png)
Go製の超軽量セルフホスト型リーダーです。FreshRSSよりさらにシンプルで、余計なUIを削ぎ落とした設計になっています。AndroidではFeedMeやMinifluttから、PCはブラウザから使います。「フィードリーダーはコンテンツを読む道具であって、それ自体が注目を奪うべきではない」という哲学のもとで作られています。

### Linux デスクトップ ── [Newsflash]((https://github.com/patchedsoul/news-flash))

![Newsflash](/images/2026-06-21-rssreader-newsflash.png)
GNOMEデスクトップ環境に自然に馴染む、**Rust**で書かれたFOSSリーダーです。FreshRSSやMinifluxをバックエンドとして使えるほか、ローカルフィードの管理にも対応しています。見た目が洗練されており、LinuxでRSSを始める方の最初の選択肢として推奨されます。

### Windows ── [RSS Guard](https://github.com/martinrotter/rssguard)

![RSS Guard](https://raw.githubusercontent.com/martinrotter/rssguard/d1198081416301868b91cfb1e9159962f758b6c6/resources/graphics/official_pictures/main-window-linux.png)
Windows・Linux・macOSに対応するクロスプラットフォームのFOSSリーダーです。FreshRSSやMinifluxとの連携も可能です。UIは多機能ですが、慣れると非常に強力です。

## まとめ

古い技術であることは確かですが、枯れた技術は安定しています。オープンで、誰かの都合で突然消えることがなく、アルゴリズムと広告に侵食されない数少ない情報空間のひとつです。

iOS/macOSならまず **NetNewsWire** を入れてみてください。それだけで、広告に邪魔されず、アルゴリズムに踊らされず、自分のペースで情報と向き合える環境が手に入ります。（日本のRSSサイトはちょっと厳しい状況になってきてる。。）



## おまけ：このブログもRSSで購読できます

このブログ（under7kg.pages.dev）もRSSフィードを配信しています。

しかも、ブログ全体を購読するよりも便利な使い方があります。**カテゴリ単位、タグ単位でフィードを取得できます**。

- メインサイト：https://under7kg.pages.dev/
- Mumble　カテゴリ：https://under7kg.pages.dev/categories/mumble/
- CriticalThinking　タグ：https://under7kg.pages.dev/tags/critical-thinking/

「全部の記事は多すぎるけど、特定のカテゴリやタグの記事だけ読みたい」という場合も、そのカテゴリやタグのURLをNetNewsWireやFreshRSSに登録するだけでOKです。HugoやJekyllといった静的サイトジェネレーターの強みで、すべてのカテゴリ・タグページにRSSフィードが自動で付いてきます。
