# TASVS-ARCH: アーキテクチャと脅威モデリング (Architecture & Threat Modelling)

## 管理目標

アーキテクチャと脅威モデリングは密接に関連しています。脅威モデリングはアーキテクチャの決定に情報を提供し、アーキテクチャは脅威を体系的に特定して対処するためのコンテキストを提供します。この共生関係は意図した設計目標を満たす安全なソフトウェアとシステムを提供するために不可欠です。


## テストチェックリスト

| TASVS-ID       | 説明                                                                                                                                        | L1 | L2 | L3 |
| ---- | ------------- | - | - | - |
| TASVS-ARCH-1   | 脅威モデリング (Threat Modeling)                                                                                                            |    |    |    |
| TASVS-ARCH-1.1 | シッククライアントのための忠実度の低い脅威モデルを完成します。                                                                              | X  | X  | X  |
| TASVS-ARCH-1.2 | 現在稼働中のシッククライアントのための忠実度の高い脅威モデルを完成します。                                                                  |    | X  | X  |
| TASVS-ARCH-1.3 | 脅威モデルにはサーバーサイドコンポーネントと依存関係 (クラウド API、OIDC プロバイダ、ファイルストレージなど) を含みます。                   |    | X  | X  |
| TASVS-ARCH-1.4 | 脅威モデリングプロセスにはすべてのフェーズ (システムモデリング、自動脅威識別、手動脅威識別、脅威緩和) を含みます。                          |    | X  | X  |
| TASVS-ARCH-1.5 | 脅威モデルはソースコードリポジトリにチェックインします。                                                                                    | X  | X  | X  |
| TASVS-ARCH-1.6 | 脅威モデルは開発チームの SSDLC 内で文書化されたプロセスの一環として定期的に更新します。                                                     |    | X  | X  |

## コントロールグループ定義

### TASVS-ARCH-1.1

#### 「忠実度の低い」モデリングの定義とは？

「忠実度の低い」モデリングにより、初期の脅威モデルを作成する労力を大幅に削減します。「忠実度の低い」システムモデルは資産、リンク、信頼境界を含みますが、属性が制限されます。

推奨される「忠実度の低い」ベースライン:
- データ資産を CIA (機密性/完全性/可用性) で定義します。
- 技術資産をテクノロジで定義します。
- 通信リンクをプロトコルで定義します。
- 技術資産を信頼境界内に配置します。

これで終わりです。その後、モデルをさらに精緻化し、忠実度スコアを上げていきます。システムモデルは、脅威を特定するという目的を達成するための手段であることを忘れないでください。

### TASVS-ARCH-1.2

"high fidelity" threat modeling is a more detailed and comprehensive approach to threat modeling. It includes all the elements of a low-fidelity model but adds more detail and context to the model. This includes:

- Detailed data flow diagrams
- Detailed trust boundaries
- Detailed threat identification

### TASVS-ARCH-1.3

Server-side components and dependencies should be included in the threat modeling process to ensure that all potential threats are identified and addressed. This includes cloud APIs, OIDC providers, file storage, and any other external services that the thick client interacts with. By including these components in the threat model, you can identify potential vulnerabilities and design security controls to mitigate them.

### TASVS-ARCH-1.4

Phases of threat modeling include system modeling, auto-threat identification, manual threat identification, and threat mitigation. Each phase is essential to the overall threat modeling process and should be completed thoroughly to ensure that all potential threats are identified and addressed.

### TASVS-ARCH-1.5

The threat model should be checked into the source code repository to ensure that it is accessible to all members of the development team. This allows team members to review the threat model and provide feedback, as well as track changes to the model over time.


### TASVS-ARCH-1.6

The threat model should be updated regularly as part of a documented process within the development team's SSDLC. This ensures that the threat model remains current and relevant as the thick client evolves and new threats emerge. Regular updates to the threat model help to ensure that the thick client remains secure and resilient to potential threats.


\newpage{}
