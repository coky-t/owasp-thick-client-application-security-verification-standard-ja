 # OWASP Thick Client Application Security Verification Standard (TASVS)
[![Downloads](https://img.shields.io/github/downloads/owasp/www-project-thick-client-application-security-verification-standard/total?logo=github&logoColor=white&style=flat-square)](https://github.com/owasp/www-project-thick-client-application-security-verification-standard/releases)
[![GitHub contributors](https://img.shields.io/github/contributors/owasp/www-project-thick-client-application-security-verification-standard)](https://github.com/owasp/www-project-thick-client-application-security-verification-standard/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/owasp/www-project-thick-client-application-security-verification-standard)](https://github.com/owasp/www-project-thick-client-application-security-verification-standard/issues)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/owasp/www-project-thick-client-application-security-verification-standard)](https://github.com/owasp/www-project-thick-client-application-security-verification-standard/pulls)
[![GitHub license](https://img.shields.io/github/license/owasp/www-project-thick-client-application-security-verification-standard)](https://github.com/owasp/www-project-thick-client-application-security-verification-standard/blob/main/LICENSE)


 
## はじめに
OWASP Thick Client Application Security Verification Standard (TASVS) プロジェクトはシッククライアントアプリケーションを安全にするためのオープンスタンダードを確立することを目的としています。このプロジェクトは、技術的なアプリケーションセキュリティコントロールを設計、構築、テストするための包括的な枠組みを提供します。

TASVS プロジェクトはウェブアプリケーションのための [OWASP Application Security Verification Standard (ASVS)](https://github.com/OWASP/ASVS) と [Mobile Application Security Verification Standard (MASVS)](https://github.com/OWASP/owasp-masvs) の間のギャップを埋めます。MASVS はシッククライアントのテストに適用できますが、理想的な適合ではありません。TASVS プロジェクトはこれらのシナリオに適した標準を作成することを目指しています。

## プロジェクトリーダーとワーキンググループ

このプロジェクトは主に一人のプロジェクトリーダー [Dave Hanson](https://github.com/JeffreyShran) によって管理されています。なお、彼は Bentley Systems のアクティブな AppSec チームである [Samuel Aubert](https://github.com/matreurai)、[Einaras Bartkus](https://github.com/eb-bsi)、[Thomas Chauchefoin](https://www.linkedin.com/in/thomaschauchefoin)、[John Cotter](https://www.linkedin.com/in/john-cotter-40338612/) などから多大な支援を受けています。

このプロジェクトは OWASP コミュニティと OWASP 財団からも支援を受けています。特に、プロジェクトのディレクターとしてサポートしてくれた [Starr Brown](https://github.com/mamicidal) に感謝します。

## ロードマップ

使用に適した最初の公開バージョンは 2024 年 9 月にリリースされました。このプロジェクトは標準を改良し、コンテンツをさらに追加している最中です。

私たちが成熟していくにつれて、ロードマップをより構造化したものにしたいと考えています。ほとんどの活動と同様に、[ASVS プロジェクト](https://github.com/OWASP/ASVS/wiki/Roadmap-to-version-5.0) が完了させた作業によって、その構造を見つけることができるでしょう。

`utils\Convert-TASVS-Excel` ディレクトリには、Excel テンプレートに TASVS チェックリストを入力するために使用できるスクリプトがあります。これは実用的な方法で標準を適用するための便利なツールです。まだ完全にリリースできる状態ではありませんが、いざというときに使用できます。時間をかけて更新するように努めますが、今のところは `TASVS_v1.6.xlsx` のような名前の Excel ファイルを入手してください。

## 貢献

このプロジェクトでは以下の作業を手伝ってくれる貢献者を募集しています。

- このプロジェクトについて広く知らせること。他に何もすることがなければ、このプロジェクトをあなたのネットワークで共有してください。
- 現在の標準をレビューし、フィードバックを提供します。
- 新しい管理目標を作成します。
- 既存のコントロールグループの定義を更新します。特に以下のものを更新します。
  - コード例から恩恵を受ける可能性があるもの
  - この分野の若手やセキュリティ経験の浅い開発者がより理解しやすいように、より簡単な言葉でさらに詳しく説明できるもの

> 貢献に興味がある場合は、[貢献ガイドライン](https://github.com/OWASP/www-project-thick-client-application-security-verification-standard/blob/main/CONTRIBUTING.md) と [行動規範](https://github.com/OWASP/www-project-thick-client-application-security-verification-standard/blob/main/CODE_OF_CONDUCT.md) をご確認ください。

## 標準の目的

要件は以下の目的を念頭に置いて作成されています。これらはウェブ ASVS プロジェクト https://github.com/OWASP/ASVS/blob/master/README.md#standard-objectives から引用されています。

* 組織が高品質のセキュアコーディング標準を採用または適応することを支援します。
* アーキテクトと開発者がセキュリティを設計および構築し、テストを実装する単体テストと統合テストを使用してセキュリティが適切で効果的であることを検証することで、安全なソフトウェアを構築することを支援します。
* セキュリティレビュー担当者がハイブリッドコードレビュー、セキュアコードレビュー、ピアコードレビュー、レトロスペクティブに包括的で一貫性のある高品質の標準を使用し、開発者と協力してセキュリティ単体テストと統合テストを構築することを支援します。この標準をレベル 1 のペネトレーションテストに使用することも可能です。

## 貢献者への謝辞

OWASP Thick Client Application Security Verification Standard (TASVS) プロジェクトは、プロジェクトへの支援と献身について以下の貢献者の方々に感謝の意を表します。

<a href="https://github.com/OWASP/www-project-thick-client-application-security-verification-standard/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=OWASP/www-project-thick-client-application-security-verification-standard" />
</a>

## スポンサー

<a href="https://www.bentley.com/company/about-us/">
  <div>
    <img src="https://raw.githubusercontent.com/OWASP/www-project-thick-client-application-security-verification-standard/refs/heads/main/assets/images/BentleyLOGO_BLK_type.jpg" width="230" alt="Bentley Systems" />
  </div>
  <b>
    Bentley は、生活の質と持続可能性を向上させるためのインフラストラクチャを推進する、インフラストラクチャエンジニアリングソフトウェアの大手プロバイダです。
  </b>
  <div>
    <sup>詳細については <u>bentley.com</u> をご覧ください。</sup>
  </div>
</a>

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=OWASP/www-project-thick-client-application-security-verification-standard&type=Date)](https://star-history.com/#OWASP/www-project-thick-client-application-security-verification-standard&Date)

## ライセンス

プロジェクトコンテンツ全体は [Creative Commons Attribution-ShareAlike 4.0 International License][cc-by-sa] の下にあります。

## 関連

いくつかの関連プロジェクトを紹介します。
> 自分のプロジェクトをここに掲載したい場合には、issue を開いてください。

- [OWASP Application Security Verification Standard (ASVS)](https://github.com/OWASP/ASVS)
- [OWASP Mobile Application Security Verification Standard (MASVS)](https://github.com/OWASP/owasp-masvs)
