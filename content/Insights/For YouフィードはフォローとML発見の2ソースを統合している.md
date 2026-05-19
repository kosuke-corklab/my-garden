---
publish: true
type: insight
source: "[[Sources/X-Algorithm]]"
domain: AI, technology
tags:
  - type/insight
  - domain/AI
  - domain/technology
---

# For You フィードはフォローと ML 発見の 2 ソースを統合している

X の For You フィードは、まったく異なる性質の 2 つの候補ソースを組み合わせている。

| ソース | 仕組み | 役割 |
|--------|--------|------|
| **Thunder（In-Network）** | フォロー済みアカウントの投稿をKafkaからリアルタイム取得 | 既存の関係性を反映 |
| **Phoenix（Out-of-Network）** | Two-Tower モデルによる類似度検索でMLが発見 | 未知の価値ある投稿を発掘 |

## なぜ2ソースか

フォローのみでは「すでに知っている世界」しか届かない。
ML 発見のみでは「関係性の文脈」が失われる。

2つを統合し、スコアリング（Weighted + OON Scorer）で最終順位を決めることで、**馴染みと発見のバランス**を実現している。

## OON Scorer の役割

Out-of-Network 投稿には `OON_WEIGHT_FACTOR` を乗算して調整する。
これにより In-Network 投稿の相対的な優先度を維持しつつ、ML 発見投稿も適切な割合で混入される。

## 「届ける」との接続

アルゴリズムはフォロワーがいない人にも価値ある投稿を届ける設計になっている。
Phoenix（ML 発見）が存在するため、**フォロワー数ゼロからでも高品質な投稿は拡散される可能性がある**。

## 接続

- [[Insights/XアルゴリズムはMLが手動ルールを完全に置き換えた]]
- [[Insights/スコアはエンゲージメント確率の加重和でありネガティブ反応が押し下げる]]
- [[Sources/X-Algorithm]]
