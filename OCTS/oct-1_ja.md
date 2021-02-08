---
oct-v: 1
title: Oct-Pass v1 specification
author: Blockchain Contents Association
created: 2021-01-06
---

## What is Oct-Pass?

「Oct-Pass」は誰でも無償で自由に利用することができるオープンなNFT共通仕様です。本仕様に準拠してNFTメタデータを作成することで、アプリケーション間におけるNFTの相互利用が容易にできるようになります。 これにより、ゲーム、SNS、マーケット、ウォレットなど異なるアプリケーションや、異なるブロックチェーンを跨いで、NFTで世界が繋がる「NFTメタバース」を実現する一助となることを目指しています。

## Oct-Pass Rationale

NFT（Non-Fungible Token）は、イーサリアムの技術規格ERC-721に準拠して発行された非代替性トークンです。ERC-721は「所有、譲渡、譲渡の委任」を定義する規格であり、NFTのコンテンツ情報はメタデータで定義されています。
NFTは、特定のプラットフォームに依存することなく、異なるアプリケーションやブロックチェーン環境で表示や利用されていくことが想定されます。 この場合、従来のNFTマーケットに対応するためのメタデータだけでは、ライセンスや表示・改変などの許諾、コンテンツごとの性質の表現に対応できないケースが考えられます。
これまでは、NFTごとにメタデータフォーマットが異なるため統一した取り扱いが難しく、NFT作成者やアプリケーションごとに個別に対応するためのシステム開発や調整が必要でした。
NFTメタデータの共通仕様「Oct-Pass metadata format」を定めることで、こういった状況を改善し、NFT作成者やアプリケーションでNFTの取り扱いを簡便にすることを目指します。

## Oct-Pass Improvement Proposal
Oct-Pass Improvemen Proposal(OIP)として改善案を受付、4段階にわけ更新を行います。
1. Idea
Github上で1.Abstract:概要、2.Motivation:なぜ必要なのか、3.Specification:詳細のフォーマットに従ってIssueをたて議論を行ってください。
その後、新規OIPフォーマットに沿ってPull Requestを出してください。
2. Draft
当協会内で協議の上、ドラフトとして採用(Pull requestがmerge)されます。
3. Review
14日間レビュー期間を設けてパブリックコメント募集を行います。
4. Final
レビュー期間に集まった意見を反映したり、問題なければそのまま最終化されます。

## Oct-Pass Types
本仕様では、basic（NFTの基本的情報。名前、種類、サムネイル画像、発行数など）、contents（NFTのコンテンツ情報と利用や改変に対するライセンス情報）、property（コンテンツの性質などの付随情報）のカテゴリ別にメタデータの共通仕様を定義することで、ブロックチェーン時代のコンテンツ利用に適したフォーマットを目指します。

### Basic
| 項目項目     | 必須    | 内容                                 | 例                                                                                                                                                           | 
| ------------ | ------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | 
| name         | ◯      | NFT名称（ERC721/EIP1047）            | Nobunaga Oda #50010006 Lv.100                                                                                                                                | 
| description  | ◯      | NFT説明文（ERC721/EIP1047）          | Heroes are unique characters, originated from My Crypto Heroes. Pick your hero and compete in the MCH universe! The hero type of this asset is Nobunaga Oda. | 
| image        | ◯      | サムネイルURI（ERC721/EIP1047）      | https://www.mycryptoheroes.net/images/heroes/2000/5001.png                                                                                                   | 
| nft_id       | ◯      | NFT ID                               | 50010001                                                                                                                                                     | 
| nft_class    | ◯      | NFTクラス名（ERC-721のname）         | MyCryptoHeroes:Hero                                                                                                                                          | 
| nft_type     |         | NFTタイプ名                          | Nobunaga Oda                                                                                                                                                 | 
| symbol       | ◯      | シンボル名（ERC-721のsymbol）        | MCHH                                                                                                                                                         | 

### Contents
| 項目                 | 必須       | 内容                                                                        | 例                                         |                                                            | 
| -------------------- | ---------- | --------------------------------------------------------------------------- | ------------------------------------------ | ---------------------------------------------------------- | 
| contents             | ◯        |                                                                           | コンテンツURI                              | https://www.mycryptoheroes.net/images/heroes/2000/5001.png | 
| （配列）             |            |                                                                             |                                            |                                                            | 
| mime                 | ◯         | コンテンツMIMEタイプ                                                        | image/png                                  |                                                            | 
| license              |   | copyright                                                                            | コピーライト文言                           | © 2018 double jump.tokyo, inc                              | 
| uri                  |            | ライセンス規約URL                                                           | https://www.mycryptoheroes.net/ja/terms    |                                                            | 
| contact              |            | ライセンスに関する問い合わせ先                                              | info@doublejump.tokyo                      |                                                            | 
| type                 | ◯         | Creative Commons表記 + 再配布禁止https://creativecommons.jp/licenses/       | BY-NC                                      |                                                            | 
|                      |            | （RedistributionProhibited/ CC0/BY/BY-NC/BY-NC-ND/BY-NC-SA/BY-ND/BY-SA/PD） |                                            |                                                            | 
| usecase              | reference  | ◯                                                                          | 参照可能か（allow/disallow）               | allow                                                      | 
| trade                | ◯         | 取引可能か（allow/disallow）                                                | allow                                      |                                                            | 
| lock                 | ◯         | ロック可能か（allow/disallow）                                              | disallow                                   |                                                            | 
| trade_shares（配列） | percentage |                                                                             | 取引手数料配分%                            | 2.5                                                        | 
| account              |            | 配分先                                                                      | 0x6738001581C6ac28f7B05bfca3348caFB05Ef289 |                                                            | 


### Property
| 項目       | 必須 | 内容                                                                  | 例                                                                                                                                                                                                                                                                          | 
| ---------- | ---- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | 
| attributes | ◯   | コンテンツの主要パラメタ（OpenSea対応）                               | {"type_name":"Nobunaga Oda", "lv":100, "rarity":"Legendary", "hp":471, "phy":202, "int":79, "agi":114,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"active_skill":"Hot chili pepper", "passive_skill":"Rule the Empire by Force"},                                                         | 
| extras     |      | コンテンツにおける準パラメタ（OpenSea等に表示するまでもないパラメタ） | {"active_skill_id":3130, "art_history":["略"], "ce":1110243,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"current_art":"Qmez4jc4S9y2mYyNDZpXaqXNHdcK636LfgPJqpvzcNwU8x",&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"current_stamina":40, "hero_type":5001, "max_stamina":288, "passive_skill_id":1001}} | 

* attributesは、NFT取引所に表示するための主なパラメタとして指定が必要。この仕様については[OpenSea](https://docs.opensea.io/docs/metadata-standards)を参照とする
* extrasは、NFT取引所に表示するまでもない準パラメタ。とはいえ、周辺コンテンツとしては参照したいパラメタをこちらに記載。



## Question Guide
ヘルプとサポートについては、[ブロックチェーンコンテンツ協会](https://www.blockchaincontents.org/contact)へご連絡ください。

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
