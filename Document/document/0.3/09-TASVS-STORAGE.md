# TASVS-STORAGE: データストレージ (Data Storage)

## 管理目標


## テストチェックリスト

| TASVS-ID          | 説明                                                                                                                                                                                                                              | L1 | L2 | L3 |
| ---- | ------------- | - | - | - |
| TASVS-STORAGE-1   | 機密情報レビュー (Sensitive Information Review)                                                                                                                                                                                   |    |    |    |
| TASVS-STORAGE-1.1 | バイナリや設定ファイルにユーザー名、パスワード、接続文字列、API キーなどを含みます。                                                                                                                                              | X  | X  | X  |
| TASVS-STORAGE-1.2 | レジストリエントリにユーザー名、パスワード、接続文字列、API キーなどを含みます。                                                                                                                                                  | X  | X  | X  |
| TASVS-STORAGE-1.3 | PII や、外部リソースあるいはアプリケーションが実行されているマシン上の他のリソースに接続するために使用されるあらゆる種類のクレデンシャルなどの機密データをログにキャプチャや保存していないことを検証します。                      | X  | X  | X  |
| TASVS-STORAGE-1.4 | シッククライアントは機密データを必要以上にメモリに保持せず、使用後にはメモリを明示的にクリアします。                                                                                                                              | X  | X  | X  |
| TASVS-STORAGE-1.5 | 簡単な静的解析では重要なコードやデータは明らかになりません。                                                                                                                                                                      | X  | X  | X  |
| TASVS-STORAGE-1.6 | 個人を識別できる情報 (Personally Identifiable Information, PII)、機密性の高い個人情報、EU の GDPR の対象となる可能性が高いと評価されたデータなど、規制対象の個人データ、健康データ、金銭データを保管時に暗号化して保存することを検証します。 | X  | X  | X  |
| TASVS-STORAGE-1.7 | 認証トークンやセッショントークンは簡単には取得できません。                                                                                                                                                                        | X  | X  | X  |
| TASVS-STORAGE-2   | DLL ハイジャッキング (信頼できるアプリケーションの操作による悪意のある DLL のロード) (DLL Hijacking (Trusted application manipulation into loading a malicious DLL))                                                              |    |    |    |
| TASVS-STORAGE-2.1 | DLL 置き換え (DLL Replacement): 正規の DLL を悪意のあるものと入れ換えます。オプションで DLL プロキシを使用して、元の DLL の機能を保持します。                                                                                     | X  | X  | X  |
| TASVS-STORAGE-2.2 | DLL 検索順序ハイジャック (DLL Search Order Hijacking): 正規の DLL よりも前の検索パスに悪意のあるものを配置し、アプリケーションの検索パターンを悪用します。                                                                        | X  | X  | X  |

## コントロールグループ定義

### TASVS-STORAGE-1.1

TBC

### TASVS-STORAGE-1.2

TBC

### TASVS-STORAGE-1.3

TBC

### TASVS-STORAGE-1.4

TBC

### TASVS-STORAGE-1.5

TBC

### TASVS-STORAGE-1.6

TBC

### TASVS-STORAGE-1.7

TBC

### TASVS-STORAGE-2.1

TBC

### TASVS-STORAGE-2.2

TBC



\newpage{}
