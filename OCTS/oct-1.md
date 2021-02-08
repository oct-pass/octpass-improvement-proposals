---
oct-v: 1
title: Oct-Pass v1 specification
author: Blockchain Contents Association
created: 2021-01-06
---

## What is Oct-Pass?

Oct-Pass  is open NFT(Non Fungible Token) common specification for free.									
By creating NFT metadata in accordance with this specification, interoperability of NFT among applications will be made possible									
We are  intended to help realize the NFT metaverse, where the world is connected by NFT across different applications such as games, SNS, and wallets.									

## Oct-Pass Rationale

NFT (Non-Fungible Token) is a non-replaceable token issued in compliance with the Ethereum technical standard ERC-721													
ERC-721 is a standard that defines "ownership, transfer, and delegation" and NFT content information is defined in metadata													
NFTs are expected to be displayed and used in different applications and blockchain environments without depending on a specific platform.													
There may be cases where the conventional NFT market meta data format is not enough to support licensing, permission for display and modification, and expression of the nature of each content.													
As each NFT had a different metadata format until now, it was difficult to handle the metadata in a unified manner, and it was necessary to develop systems and make adjustments to support each NFT creator and application individually.													
By defining a common specification for NFT metadata, the Oct-Pass metadata format, we aim to improve this situation and make it easier for NFT authors and applications to handle NFTs.													

## Oct-Pass Improvement Proposal
We'll accept improvement proposals as Oct-Pass Improvement Proposals (OIP) and update them in four stages

1.Idea						
Abstract,Moltivation.Specification						
Please follow the format above to create an issue to discuss it.						
Then, please submit pull request  follwing the new OIP template under OIPS.						
2.Draft						
It will be adapted as a draft after disucussion in our association.						
3.Review						
14 days as a review period for recruiting public comment.						
4.Final						
If there are no problems , OIP will be implemented

## Oct-Pass Types
This specification aim to be a format that is suitable for using content in the blockchain era by defining the metadata by basic(basic NFT info,name,category,image of thumbnail, issued amount ), contents(NFT contents information, License information to use or change etc), property(additional information of contents property) categories.

### Basic
| Item     | Required    | Contents                                 | Example                                                                                                                                                           | 
| ------------ | ------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | 
| name         | ◯      | NFT name        | Nobunaga Oda #50010006 Lv.100                                                                                                                                | 
| description  | ◯      | NFT description（ERC721/EIP1047）          | Heroes are unique characters, originated from My Crypto Heroes. Pick your hero and compete in the MCH universe! The hero type of this asset is Nobunaga Oda. | 
| image        | ◯      | URI（ERC721/EIP1047）      | https://www.mycryptoheroes.net/images/heroes/2000/5001.png                                                                                                   | 
| nft_id       | ◯      | NFT ID                               | 50010001                                                                                                                                                     | 
| nft_class    | ◯      | NFT class name         | MyCryptoHeroes:Hero                                                                                                                                          | 
| nft_type     |         | NFT Type name                          | Nobunaga Oda                                                                                                                                                 | 
| symbol       | ◯      | ERC-721 symbol        | MCHH                                                                                                                                                         | 

### Contents
| Item                 | Required       | Contents                                                                        | Example                                         |                                                            | 
| -------------------- | ---------- | --------------------------------------------------------------------------- | ------------------------------------------ | ---------------------------------------------------------- | 
| contents             | ○        |                                                                           | contents URI                              | https://www.mycryptoheroes.net/images/heroes/2000/5001.png | 
| （配列）             |            |                                                                             |                                            |                                                            | 
| mime                 | ◯         | contents MIME type                                                        | image/png                                  |                                                            | 
| license              |   | copyright                                                                            | copyright statement                           | © 2018 double jump.tokyo, inc                              | 
| uri                  |            | license agreement URL                                                           | https://www.mycryptoheroes.net/ja/terms    |                                                            | 
| contact              |            | for licensing inquiries                                             | info@doublejump.tokyo                      |                                                            | 
| type                 | ◯         | creative commons notation,redistribution prohibited https://creativecommons.jp/licenses/      | BY-NC                                      |                                                            | 
|                      |            | （RedistributionProhibited/ CC0/BY/BY-NC/BY-NC-ND/BY-NC-SA/BY-ND/BY-SA/PD） |                                            |                                                            | 
| usecase              | reference  | ◯                                                                          | refarence available?（allow/disallow）               | allow                                                      | 
| trade                | ◯         | tradable?（allow/disallow）                                                | allow                                      |                                                            | 
| lock                 | ◯         | lockable?（allow/disallow）                                              | disallow                                   |                                                            | 
| trade_shares（array） | percentage |                                                                             | trading fee allocation                            | 2.5                                                        | 
| account              |            | allocation                                                                     | 0x6738001581C6ac28f7B05bfca3348caFB05Ef289 |                                                            | 


### Property
| Item       | Required  | Contents                                                                  | Example                                                                                                                                                                                                                                                                          | 
| ---------- | ---- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | 
| attributes | ◯   | Key parameters of content (OpenSea compliant)                               | {"type_name":"Nobunaga Oda", "lv":100, "rarity":"Legendary", "hp":471, "phy":202, "int":79, "agi":114,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"active_skill":"Hot chili pepper", "passive_skill":"Rule the Empire by Force"},                                                         | 
| extras     |      | Quasi-parameters in content (parameters that do not need to be displayed on OpenSea, etc.) | {"active_skill_id":3130, "art_history":["略"], "ce":1110243,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"current_art":"Qmez4jc4S9y2mYyNDZpXaqXNHdcK636LfgPJqpvzcNwU8x",&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"current_stamina":40, "hero_type":5001, "max_stamina":288, "passive_skill_id":1001}} | 

* Attributes need to specify for main parameter to display on the NFT exchange. This specification use [OpenSea](https://docs.opensea.io/docs/metadata-standards) as a preference.										
* Extras is semi parameter that is not needed to display on NFT exchange. However , parameters to be reference is listed here as a related contents.										



## Question Guide
Please contact [Blockchain Contents Association](https://www.blockchaincontents.org/contact) for help and support etc.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
