# AX modules for Ansible 活用ガイド  
アラクサラ会員様専用サイトであるビジネスパートナー様サイトおよびシステムインテグレーター会員様専用サイトに掲載している
AX modules for Ansible活用ガイドの playbookの作成における基本的なモジュール、ディレクティブ、プラグインのplaybook記述サンプルや
各ユースケースのplaybookの解説とサンプルplaybookを提供しています。  


## はじめに
このドキュメントは、アラクサラの AX modules for Ansible を活用したネットワークシステムの運用自動化に役立てるものとして AX modules for Ansibleの使用方法やplaybook記述例について記載しています。またplaybookのサンプルを提供します。

**本ドキュメントの対象読者**  

このドキュメントは、Ansibleを用いた構成管理についての基礎知識と、CLIによるアラクサラ機器の操作に関する知識を有する方を前提に記載しています。

**関連情報**
- [AX modules for Ansible運用ガイド](http://www.alaxala.com/jp/techinfo/archive/manual/ANSIBLE/PDF/1_3/OP-GUIDE-SOFT-AM-2303_R3.pdf)

- [Ansibleに関連するドキュメント](http://docs.ansible.com/ansible/latest/)

**AX modules for Ansibleの入手方法**  

AX modules for Ansibleは、[アラクサラ会員専用サイト](https://www.alaxala.com/jp/member/)から入手することができます。アラクサラの会員専用サイトのアカウントをお持ちでない場合は、会員専用サイトお申込みサイトからアカウント発行をお申込みください。

**本ドキュメント使用上の注意事項**
- 記載内容は、弊社が特定の環境において基本動作を確認したものであり、機能・性能・信頼性についてあらゆる環境条件すべてにおいて保証するものではありません。またマニュアルの補助資料としてご利用いただけますようお願いいたします。

- AX modules for Ansible Version 1.3を対象に記載しています。また改良のため予告なく変更する場合があります。


**輸出管理の注意**  

本ドキュメントをもとに新たなコンテンツを作成し配布する場合には、外国為替及び外国貿易法の規制並びに米国輸出管理規制など外国の輸出関連法規をご確認の上、必要な手続きをおとりください。


**商標一覧**
- アラクサラの名称およびロゴマークは、アラクサラネットワークス株式会社の商標および登録商標です。
- Ansibleは，Red Hat, Inc.およびその子会社の商標または登録商標です。
- Red Hat Enterprise Linuxは，Red Hat, Inc.の商標または登録商標です。
- CentOSは，Red Hat, Inc.の商標または登録商標です。
- Pythonは，Python Software Foundationの商標または登録商標です。
- Ethernet は、富士ゼロックス株式会社の登録商標です。
- イーサネットは、富士ゼロックス株式会社の登録商標です。
- そのほかの記載の会社名、製品名は、それぞれの会社の商標または登録商標です。


## AX modules for Ansible 活用ガイドの内容
第1章および第2章については以下に掲載されている「AX Modules for Ansible 活用ガイド」をご参照ください。  
[ALAXALAホームページ - 技術情報 - 設定例/システム構築ガイド - 運用管理](https://www.alaxala.com/jp/techinfo/guide/#management)

- ### 1. Ansibleとは

- ### 2. アラクサラのAXモジュール

- ### [3. playbookの作成](/N18R001_Ansible_Guide_Chapter3.md)

- ### [4. 各ユースケースでのサンプルplaybook](/N18R001_Ansible_Guide_Chapter4.1.md)
    - #### [4.1. 管理対象装置の構成とコンフィグレーション](N18R001_Ansible_Guide_Chapter4.1.md)
    - #### [4.2. フィルタエントリの追加](N18R001_Ansible_Guide_Chapter4.2.md)
    - #### [4.3. VLANおよびVXLANの追加](N18R001_Ansible_Guide_Chapter4.3.md)
    - #### [4.4. ネットワーク装置の障害情報採取](N18R001_Ansible_Guide_Chapter4.4.md)
    - #### [4.5. ネットワーク装置のソフトウェアアップデート](N18R001_Ansible_Guide_Chapter4.5.md)
    - #### [4.6. NTPサーバ追加，移設にともなうネットワーク装置の設定](N18R001_Ansible_Guide_Chapter4.6.md)

- ### [付録](/N18R001_Ansible_Guide_Chapter_app.md)
