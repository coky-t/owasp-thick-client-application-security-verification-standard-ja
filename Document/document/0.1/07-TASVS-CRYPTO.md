# TASVS-CRYPTO: 暗号 (Cryptography)

## 管理目標



## テストチェックリスト

| TASVS-ID         | 説明                                                                                                                                              | L1 | L2 | L3 |
| ---- | ------------- | - | - | - |
| TASVS-CRYPTO-1   | 通信 (Communication)                                                                                                                              |    |    |    |
| TASVS-CRYPTO-1.1 | TLS 設定は現在のベストプラクティスに従います。                                                                                                    | X  | X  | X  |
| TASVS-CRYPTO-2   | ストレージ (Storage)                                                                                                                              |    |    |    |
| TASVS-CRYPTO-2.1 | シッククライアントは同じ暗号鍵を複数の目的で再使用しません。                                                                                      | X  | X  | X  |
| TASVS-CRYPTO-2.2 | すべての乱数値は十分に安全な乱数生成器を使用して生成します。                                                                                      | X  | X  | X  |
| TASVS-CRYPTO-2.3 | シッククライアントは、セキュリティ上、広く非推奨とされている暗号プロトコルやアルゴリズムを使用しません。                                          | X  | X  | X  |
| TASVS-CRYPTO-2.4 | シッククライアントは、暗号化の唯一の方法としてハードコードされた鍵での対称暗号化に依存しません。                                                  | X  | X  | X  |
| TASVS-CRYPTO-3   | 全般 (General)                                                                                                                                    |    |    |    |
| TASVS-CRYPTO-3.1 | すべての暗号モジュールは安全に失敗し、パディングオラクル (Padding Oracle) 攻撃を有効にしない方法でエラーを処理することを検証します。              | X  | X  | X  |
| TASVS-CRYPTO-3.2 | カスタムコードによる暗号ではなく、業界で実証済みまたは政府が承認済みの暗号アルゴリズム、モード、ライブラリが使用されることを検証します。          | X  | X  | X  |

\newpage{}
