# TASVS-CODE: コード品質とエクスプロイト軽減 (Code Quality and Exploit Mitigation)

## 管理目標

アプリケーションのソースコードがセキュリティ脆弱性の導入を最小限に抑える方法で開発および保守されることを確保します。

## テストチェックリスト


| TASVS-ID        | 説明                                                                                                                                                                                                                                                                                           | L1 | L2 | L3 |
| ---- | ------------- | - | - | - |
| TASVS-CODE-1    | サーバーサイド (Server Side)                                                                                                                                                                                                                                                                   |    |    |    |
| TASVS-CODE-1.1  | シッククライアントがサーバーサイド API やサービスに依存している場合、そのテストは適切なアプリケーションセキュリティ検証標準 (ASVS) に委ねます。そのガイドを使用してテストを開始した場合は、この項目をレビュー済みとしてマークします。                                                          | X  | X  | X  |
| TASVS-CODE-2    | クライアントサイド - 署名と完全性 (Client Side - Signing and Integrity)                                                                                                                                                                                                                        |    |    |    |
| TASVS-CODE-2.1  | シッククライアントバイナリが適切に署名されていることを確認します。                                                                                                                                                                                                                             | X  | X  | X  |
| TASVS-CODE-2.2  | ファイル完全性チェックをテストします。                                                                                                                                                                                                                                                         | X  | X  | X  |
| TASVS-CODE-2.3  | ランタイム完全性チェックをテストします。                                                                                                                                                                                                                                                       | X  | X  | X  |
| TASVS-CODE-2.4  | クライアントはリリースビルドに適した設定で、リリースモードでビルドされています。                                                                                                                                                                                                               | X  | X  | X  |
| TASVS-CODE-2.5  | バイトコードの縮小化やスタック保護など、フレームワークに適切なセキュリティ機能を有効にします。                                                                                                                                                                                                 | X  | X  | X  |
| TASVS-CODE-3    | クライアントサイド - 静的コード解析 (Client Side - Static Code Analysis)                                                                                                                                                                                                                       |    |    |    |
| TASVS-CODE-3.1  | ライブラリやフレームワークなど、シッククライアントで使用されるすべてのサードパーティコンポーネントが特定され、既知の脆弱性がないかチェックされ、最新のものです。サポートされていないもの、非推奨のもの、レガシーなものであってはなりません。                                                   | X  | X  | X  |
| TASVS-CODE-3.2  | 例外がスローされ、適切に処理されていないケースについて、ソースコードを検索します。たとえば、C# では 'findstr /N /s /c:"throw;" \*.cs' を使用します。また、その例外が認証やその他の重要な操作のバイパスを許可していないかどうかにも注意します。                                                 | X  | X  | X  |
| TASVS-CODE-3.3  | バイナリ静的解析を実行します。 (バイナリが最新のコンパイラでコンパイルされていることを検証し、コンパイル設定を調べ、バイナリ署名を確認します)                                                                                                                                                  | X  | X  | X  |
| TASVS-CODE-3.4  | 使用している言語に応じて、適切な静的アプリケーションセキュリティテスト (SAST) ツールを選択し、ソースコードを解析して脆弱性を特定します。                                                                                                                                                       | X  | X  | X  |
| TASVS-CODE-3.5  | 該当する場合は、内部ツール、ポリシー、テストケースが正しく実装され、評価されていることを確認します。                                                                                                                                                                                           | X  | X  | X  |
| TASVS-CODE-3.6  | 未使用のコードを特定して消去します。後で必要になった場合、ソースコードリポジトリの履歴に残ることを覚えておいてください。README や changelog ファイルを使用して、価値の高い歴史的コンテキストや非推奨の詳細を保存します。使われなくなったプロジェクトリポジトリを保持せずに、リポジトリをアーカイブすることを検討してください。 | X  | X  | X  |
| TASVS-CODE-4    | クライアントサイド - バリデーション、サニタイゼーション、エンコーディング (Client Side - Validation, Sanitization and Encoding)                                                                                                                                                                |    |    |    |
| TASVS-CODE-4.1  | マクロやテンプレートなどの機能を介した信頼できないデータはコードインジェクション攻撃およびコマンドインジェクション攻撃から保護します。代替手段がない場合、含まれているあらゆるユーザー入力は実行前にサニタイズまたはサンドボックス化しなければなりません。                                                         | X  | X  | X  |
| TASVS-CODE-4.2  | アプリケーションが OS コマンドインジェクションを防ぐことを検証します。                                                                                                                                                                                                                         | X  | X  | X  |
| TASVS-CODE-4.3  | 非構造化データがサニタイズされ、許容される文字や長さなどの安全対策を施していることを検証します。                                                                                                                                                                                               | X  | X  | X  |
| TASVS-CODE-4.4  | アプリケーションは XML パーサーを適切に制限し、可能な限り最も制限的な構成のみを使用すること、および、外部エンティティの解決などの安全でない機能を無効にし、XML eXternal Entity (XXE) 攻撃を防ぐことを検証します。                                                                              | X  | X  | X  |
| TASVS-CODE-4.5  | アプリケーションはメモリセーフな文字列、より安全なメモリコピーおよびポインタ演算を使用して、スタック、バッファ、ヒープのオーバーフローを検出または防止することを検証します。                                                                                                                   | X  | X  | X  |
| TASVS-CODE-4.6  | フォーマット文字列は潜在的に敵対的な入力を受け入れず、不変であることを検証します。                                                                                                                                                                                                             | X  | X  | X  |
| TASVS-CODE-4.7  | 符号、範囲、入力バリデーション技法を使用して整数オーバーフローを防ぐことを検証します。                                                                                                                                                                                                         | X  | X  | X  |
| TASVS-CODE-4.8  | シリアライズされたオブジェクトは完全性チェックを使用するか暗号化して、敵対的なオブジェクトの作成やデータの改竄を防ぐことを検証します。                                                                                                                                                         | X  | X  | X  |
| TASVS-CODE-4.9  | 信頼できないデータのデシリアライズを回避するか、カスタムコードとサードパーティライブラリ (JSON, XML, YAML パーサーなど) の両方で防御することを検証します。                                                                                                                                     | X  | X  | X  |
| TASVS-CODE-4.10 | シッククライアントのプロセス生成は安全に行われます。 (プロセス引数のバリデーションとサニタイゼーション)                                                                                                                                                                                        | X  | X  | X  |
| TASVS-CODE-4.11 | ユーザーが送信したファイル名メタデータはシステムやフレームワークのファイルシステムに直接使用されず、パストラバーサルを防ぐことを検証します。一例として "ZipSlip" スタイルの攻撃があります。                                                                                                    | X  | X  | X  |
| TASVS-CODE-4.12 | アンマネージドコードでは、メモリが安全に割り当て、解放、使用されます。                                                                                                                                                                                                                         | X  | X  | X  |
| TASVS-CODE-5    | クライアントサイド - ビジネスロジック (Client Side - Business Logic)                                                                                                                                                                                                                           |    |    |    |
| TASVS-CODE-5.1  | パスワードや PIN などの機密データはユーザーインタフェースを通じて公開されることがありません。                                                                                                                                                                                                  | X  | X  | X  |
| TASVS-CODE-5.2  | ユーザーを騙したり操って、本来なら選ばないような選択をさせ、害を及ぼすようなデザイン慣行がないか確認します。別名「ダークパターン (deceptive patterns)」。例については https://www.deceptive.design/types を参照してください。                                                                  | X  | X  | X  |
| TASVS-CODE-5.3  | シッククライアントは一般的なセキュリティアドバイスに違反しないワークフローのみを使用している。                                                                                                                                                                                                 | X  | X  | X  |
| TASVS-CODE-5.4  | サードパーティライブラリをサンドボックス化やカプセル化して、必要な動作のみをアプリケーションに公開することにより、攻撃対象領域が減少していることを検証します。                                                                                                                                 | X  | X  | X  |
| TASVS-CODE-5.5  | インポートファイルが悪用できないことを確認します。                                                                                                                                                                                                                                             | X  | X  | X  |
| TASVS-CODE-5.6  | シッククライアントが URL ハンドラやプロトコルハンドラを登録する場合、危険なアクションを引き起こしたり一般的な脆弱性 (メモリ破損、コマンドや引数のインジェクションなど) を引き起こしたりしないことを検証します。                                                                                | X  | X  | X  |
| TASVS-CODE-6    | クライアントサイド - ファジング (Client Side - Fuzzing)                                                                                                                                                                                                                                        |    |    |    |
| TASVS-CODE-6.1  | ランダムな入力でアプリケーションの「ダムファジング (dumb fuzzing)」を実行し、クラッシュを引き起こそうとします。                                                                                                                                                                                | X  | X  | X  |
| TASVS-CODE-6.2  | 「スマートファジング (smart fuzzing)」を実行します。コードカバレッジを最大化するテストケースをインテリジェントに生成し、複雑なプログラムの状態を探索して、「ダムファジング (dumb fuzzing)」よりも脆弱性を発見する可能性を高めます。                                                            |    |    | X  |
| TASVS-CODE-7    | クライアントサイド - 権限と 2 のルール (Client Side - Privilege and Rule of two)                                                                                                                                                                                                               |    |    |    |
| TASVS-CODE-7.1  | ソフトウェアが最小権限の原則に従い、期待通りに動作するために最低レベルの権限で実行することを確保します。複数レベルの権限が必要となる場合、その IPC インタフェースが明確に定義され、必要以上の機能は公開していません。                                                                          | X  | X  | X  |
| TASVS-CODE-7.2  | シッククライアントは「2 のルール」に従っており、信頼できない入力で動作、メモリ安全でない言語で記載、高い権限で/サンドボックスなしで動作、の 2 つ以上を持つことはできません。                                                                                                                   | X  | X  | X  |

## コントロールグループ定義

### TASVS-CODE-1.1

TASVS と ASVS 間の不要なクロスオーバーを避けるために、このコントロールは、ASVS を使用してシッククライアントのサーバーサイドコンポーネントをテストするための単なる注意喚起です。

### TASVS-CODE-2.1

シッククライアントバイナリは改竄されていないことを確認するために署名する必要があります。これは、ソフトウェアの信頼性を検証する方法を提供するため、エンドユーザーに配布するシッククライアントにとって特に重要です。

### TASVS-CODE-2.2

ファイル完全性チェックを使用して、シッククライアントで使用するファイルが改竄されていないことを検証します。これは、マルウェアやその他の悪意のあるコードの導入など、ソフトウェアへの認可されていない変更を検出するのに役立ちます。

### TASVS-CODE-2.3

ランタイム完全性チェックを使用して、シッククライアントが *実行* 時に改竄されていないことを検証します。これは、使用中のソフトウェアの動作を変更しようとする攻撃を検出するのに役立ちます。

### TASVS-CODE-2.4

シッククライアントはリリースビルドに適した設定でのリリースモードでビルドする必要があります。これは、ソフトウェアのパフォーマンスとセキュリティを最適化し、デバッグ情報やその他の不要なコードを削除します。

### TASVS-CODE-2.5

バイトコードの縮小やスタック保護などのフレームワークセキュリティ機能を有効にして、シッククライアントを一般的なセキュリティ脆弱性から保護する必要があります。これらの機能はバッファオーバーフローとスタックスマッシングなどの攻撃を防ぐのに役立ちます。

### TASVS-CODE-3.1

ライブラリやフレームワークなど、シッククライアントで使用されるサードパーティコンポーネントを特定し、既知の脆弱性がないかチェックする必要があります。これらのコンポーネントは、シッククライアントにセキュリティ脆弱性をもたらす可能性があるため、サポートされていないもの、非推奨のもの、レガシーなものではなく、最新のものであることを確保することが重要です。

### TASVS-CODE-3.2

例外がスローされて適切に処理されないと、シッククライアントのセキュリティ脆弱性につながる可能性があります。悪意のあるアクションが実行される可能性があるため、例外がスローされて適切に処理されないケースについて、ソースコードを検索することが重要です。

### TASVS-CODE-3.3

# バイナリ静的解析とは？

バイナリ静的解析を使用して、シッククライアントバイナリが最新のコンパイラでコンパイルされていること、およびコンパイル設定がセキュリティについて適切であることを検証します。これは、コンパイルプロセスの中で発生する可能性のあるシッククライアントのセキュリティ脆弱性を特定するのに役立ちます。

[dnSpy]() や [ILSpy]() などのフレームワーク固有のツールを使用して、.NET バイナリを逆コンパイルして解析します。また、[Ghidra](https://ghidra-sre.org/) や [IDA Pro](https://www.hex-rays.com/products/ida/) などのツールを使用して、他の言語のバイナリを解析できます。


### TASVS-CODE-3.4

使用する言語に応じて、適切な静的アプリケーションセキュリティテスト (SAST) ツールを使用して、シッククライアントのソースコードを解析します。これは、手作業によるコードレビューで見落とされる可能性があるコード内の脆弱性を特定するのに役立ちます。

[SonarQube](https://www.sonarqube.org/), [Checkmarx](https://www.checkmarx.com/), [Veracode](https://www.veracode.com/) などのツールを使用すると、シッククライアントコードベースの静的コード解析を実行できます。さらに、Ruby on Rails 用の [Brakeman](https://brakemanscanner.org/)、Python 用の [Bandit](https://bandit.readthedocs.io/en/latest/)、Java 用の [FindBugs](http://findbugs.sourceforge.net/) などのフレームワーク固有のツールもあります。

### TASVS-CODE-3.5

内部ツール、ポリシー、テストケースを実装して評価し、それらが正しく機能していることを確認します。これにより、セキュリティ脆弱性の導入を最小限に抑える方法でシッククライアントを開発して保守できます。

これらには、コードレビュープロセス、自動テストツール、開発者向けのセキュリティトレーニングなどを含みます。これらのツールやプロセスを定期的にレビューして更新し、セキュリティ脆弱性を特定して緩和することに有効であることを確認することが重要です。

### TASVS-CODE-3.6

未使用のコードを特定し、シッククライアントコードベースから削除する必要があります。これにより、シッククライアントの攻撃対象領域を減らし、セキュリティ脆弱性のリスクを最小限に抑えることができます。README ファイルと changelog ファイルを使用して、価値の高い履歴コンテキストや廃止された詳細を保存することが重要です。廃止されたプロジェクトリポジトリは、将来のプロジェクトで脆弱性の原因として使用されるリスクがあるため、アーカイブ化する必要があります。

### TASVS-CODE-4.1

信頼できないデータはコードインジェクション攻撃やコマンドインジェクション攻撃から保護する必要があります。これは、ユーザー入力を実行前にサニタイズまたはサンドボックス化することで実現できます。ユーザー入力をシッククライアントに含める以外に方法がない場合は、サニタイズまたはサンドボックス化して、コードインジェクション攻撃やコマンドインジェクション攻撃を防ぐ必要があります。


### TASVS-CODE-4.2

シッククライアントは OS コマンドインジェクション攻撃から保護する必要があります。ユーザー入力が実行される前に検証してサニタイズすること、およびセキュアコーディングプラクティスを使用することで、コマンドインジェクション脆弱性を防ぎます。

### TASVS-CODE-4.3

非構造化データをサニタイズして、許容される文字や長さなどの安全対策を実施する必要があります。これは、バッファオーバーフローやインジェクション攻撃など、非構造化データによってもたらされる可能性のあるセキュリティ脆弱性を防ぐのに役立ちます。

### TASVS-CODE-4.4

シッククライアントは XML パーサーが最も制限の厳しい構成を使用するように制限して、XML eXternal Entity (XXE) 攻撃を防ぐ必要があります。これにより、攻撃者が XML パーサーを悪用して機密データを読み取ったり、シッククライアントで任意のコードを実行することを防ぐのに役立ちます。

### TASVS-CODE-4.5

シッククライアントはメモリセーフな文字列、より安全なメモリコピーおよびポインタ演算子を使用して、スタック、バッファ、ヒープのオーバーフローを検出または防止する必要があります。これにより、攻撃者がメモリの脆弱性を悪用して、シッククライアントで任意のコードを実行することを防ぐのに役立ちます。

`strcpy` や `strcat` などの一般的な文字列関数の安全な代替手段を使用して、バッファオーバーフローを防ぐ必要があります。`strlcpy` や `strlcat` などのメモリセーフな文字列関数は多くのプログラミング言語で利用可能であり、バッファオーバーフローを防ぐのに役立ちます。

### TASVS-CODE-4.6

フォーマット文字列は潜在的に悪意のある入力を受け取らず、不変である必要があります。これにより、攻撃者がフォーマット文字列の脆弱性を悪用して機密データを読み取ったり、シッククライアントで任意のコードを実行することを防ぐのに役立ちます。

攻撃は以下のようになるかもしれません。

```c
char buffer[100];
snprintf(buffer, sizeof(buffer), user_input);
```

`user_input` に `%s` のようなフォーマット文字列指定子が含まれると、攻撃者はそれを使用して機密データを読み取ったり、シッククライアントで任意のコードを実行する可能性があります。

たとえば `user_input` が `"%s"` の場合、`snprintf` 関数はメモリから文字列を読み取ってバッファに書き込もうとします。これによりバッファオーバーフローやその他のメモリ破損の脆弱性につながる可能性があります。

user_input が `"%x %x %x %x"` の場合、`snprintf` はこれをスタックから四つの十六進数値を読み取るものと解釈し、スタックの内容を漏洩する可能性があります。

これを避けるには、以下のようにフォーマット文字列を不変にする必要があります。

```c
snprintf(buffer, sizeof(buffer), "%s", user_input);
```

フォーマット文字列は不変、すなわち `"%s"` であり `user_input` ではないことに注意してください。



### TASVS-CODE-4.7

符号、範囲、入力バリデーションを使用して、整数オーバーフローを防ぐ必要があります。これにより、攻撃者が整数オーバーフローを悪用してシッククライアント上で任意のコードを実行することを防ぐことができる。

たとえば C/C++ の場合:

```c
int a = 100;
int b = 200;
int c = a + b;
```

`a` と `b` がユーザーによって制御される場合、攻撃者はそれらに整数オーバーフローを引き起こす値を設定し、結果として `c` は負の値になる可能性があります。これにより、シッククライアントで予期しない動作やセキュリティ脆弱性につながる可能性があります。

これを緩和するには、加算を実行する前に入力バリデーションを使用して、`a` と `b` が有効な範囲内であることを確認する必要があります。

```c
if (a > INT_MAX - b) {
    // handle error
}
int c = a + b;
```


### TASVS-CODE-4.8

シリアライズされたオブジェクトは完全性チェックを使用するか暗号化して、敵対的なオブジェクトの生成やデータの改竄を防ぐ必要があります。これにより、攻撃者がシリアライゼーション脆弱性を悪用してシッククライアント上で任意のコードを実行することを防ぐのに役立ちます。

たとえば、攻撃者がシリアライズされたオブジェクトをデシリアライズする前に改変できれば、悪意のあるコードやデータをシッククライアントに持ち込む可能性があります。完全性チェックや暗号化を使用することで、シッククライアントはシリアライズされたオブジェクトをデシリアライズする前に改竄されていないことを検証できます。

C# では、悪い例として以下のようになるかもしれません。

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class Program
{
    public static void Main()
    {
        // Serialize an object
        var obj = new MyClass();
        var formatter = new BinaryFormatter();
        var stream = new MemoryStream();
        formatter.Serialize(stream, obj);
        var serialized = stream.ToArray();

        // Deserialize the object
        var deserialized = (MyClass)formatter.Deserialize(new MemoryStream(serialized));
    }
}

[Serializable]
public class MyClass
{
    public string Name { get; set; }
}
```

この例では、攻撃者は `serialized` オブジェクトをデシリアライズする前に改変し、悪意のあるコードやデータをシッククライアントに持ち込む可能性があります。これを軽減するには、完全性チェックや暗号化を使用して、シリアライズされたオブジェクトをデシリアライズする前に改竄されていないことを検証する必要があります。

良い実装としては以下のようになるかもしれません。

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;
using System.Security.Cryptography;

public class Program
{
    public static void Main()
    {
        // Serialize an object
        var obj = new MyClass();
        var formatter = new BinaryFormatter();
        var stream = new MemoryStream();
        formatter.Serialize(stream, obj);
        var serialized = stream.ToArray();

        // Calculate a hash of the serialized object
        var hash = CalculateHash(serialized);

        // Deserialize the object
        var deserialized = (MyClass)formatter.Deserialize(new MemoryStream(serialized));

        // Verify the integrity of the deserialized object
        if (!VerifyHash(serialized, hash))
        {
            // handle error
        }
    }

    public static byte[] CalculateHash(byte[] data)
    {
        using (var sha256 = SHA256.Create())
        {
            return sha256.ComputeHash(data);
        }
    }

    public static bool VerifyHash(byte[] data, byte[] hash)
    {
        using (var sha256 = SHA256.Create())
        {
            var computedHash = sha256.ComputeHash(data);
            return StructuralComparisons.StructuralEqualityComparer.Equals(computedHash, hash);
        }
    }
}

[Serializable]
public class MyClass
{
    public string Name { get; set; }
}
```

この例では、シリアライズされたオブジェクトのハッシュをデシリアライズする前に計算し、デシリアライズ後にハッシュを検証して、オブジェクトが改竄されていないことを確認します。これにより、攻撃者がシリアライゼーション脆弱性を悪用して、シッククライアント上で任意のコードを実行することを防ぐのに役立ちます。


### TASVS-CODE-4.9

信頼できないデータのデシリアライズを回避するか、カスタムコードとサードパーティライブラリの両方で防御する必要があります。これにより、攻撃者がデシリアライゼーション脆弱性を悪用してシッククライアント上で任意のコードを実行することを防ぐのに役立ちます。

たとえば、攻撃者がシッククライアントでデシリアライズされるデータを制御できる場合、悪意のあるコードやデータをアプリケーションに持ち込む可能性がありません。信頼できないデータのデシリアライゼーションを回避したり、完全性チェックや暗号化で保護することで、シッククライアントはデシリアライズする前にデータが改竄されていないことを検証できます。

可能な限り安全なライブラリを使用し、データをデシリアライズする前に検証することをお勧めします。たとえば、C# では `DataContractSerializer` クラスを使用すると、`BinaryFormatter` クラスよりも安全な方法で JSON データをデシリアライズできます。

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Json;

public class Program
{
    public static void Main()
    {
        // Deserialize JSON data
        var json = "{\"Name\":\"Alice\"}";
        var serializer = new DataContractJsonSerializer(typeof(MyClass));
        var stream = new MemoryStream(System.Text.Encoding.UTF8.GetBytes(json));
        var deserialized = (MyClass)serializer.ReadObject(stream);
    }
}

[DataContract]
public class MyClass
{
    [DataMember]
    public string Name { get; set; }
}
```

この例では、`DataContractJsonSerializer` クラスを使用して、`BinaryFormatter` クラスより安全な方法で JSON データをデシリアライズします。これにより、攻撃者がデシリアライゼーション脆弱性を悪用してシッククライアント上で任意のコードを実行することを防ぐのに役立ちます。


### TASVS-CODE-4.10

シッククライアントのプロセス生成の処理は安全に行う必要があります。これにより、攻撃者がプロセス生成の脆弱性を悪用してシッククライアント上で任意のコードを実行することを防ぐのに役立ちます。

たとえば、シッククライアントがユーザー制御の引数でプロセスを生成する場合、攻撃者はこれを使用してシッククライアント上で任意のコードを実行できます。プロセスを生成する前にプロセス引数を検証してサニタイズすることで、シッククライアントは攻撃者がプロセス生成の脆弱性の悪用を防止できます。

C# では、悪い例として以下のようになるかもしれません。

```csharp
using System;
using System.Diagnostics;

public class Program
{
    public static void Main()
    {
        // Spawn a process with user-controlled arguments
        var process = new Process();
        process.StartInfo.FileName = "cmd.exe";
        process.StartInfo.Arguments = "/c " + user_input;
        process.Start();
    }
}
```

この例では、`user_input` 変数を使用して、`cmd.exe` プロセスの引数を作成し、攻撃者がシッククライアント上で任意のコードを実行できる可能性があります。悪意のあるユーザーは `user_input` に `"; calc.exe;` のようなものを設定して、Windows Calculator アプリケーションを実行できます。これを軽減するには、プロセスを生成する前にプロセス引数を検証してサニタイズする必要があります。

```csharp
using System;
using System.Diagnostics;

public class Program
{
    public static void Main()
    {
        // Validate and sanitize process arguments
        if (!IsValid(user_input))
        {
            // handle error
        }

        // Spawn a process with validated and sanitized arguments
        var process = new Process();
        process.StartInfo.FileName = "cmd.exe";
        process.StartInfo.Arguments = "/c " + user_input;
        process.Start();
    }

    public static bool IsValid(string input)
    {
        // Validate and sanitize input
        // For example, check for allowed characters and length
        allowed = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";

        if (input.Length > 10 || input.Any(c => !allowed.Contains(c)))
        {
            return false;
        }
    
        return true;
    }
}
```

この例では、`IsValid` 関数を使用して、`user_input` 変数を使用する前に検証しサニタイズしてから、`cmd.exe` プロセスの引数を構築します。これにより、攻撃者はプロセス生成の脆弱性を悪用してシッククライアント上で任意のコードを実行するのを防ぐのに役立ちます。

### TASVS-CODE-4.11

パストラバーサル攻撃を防ぐために、ユーザーが送信したファイル名メタデータをシステムやフレームワークのファイルシステムで直接使用すべきではありません。これにより、攻撃者がパストラバーサル脆弱性を悪用して機密データを読み取ったり、シッククライアント上で任意のコードを実行することを防ぐのに役立ちます。

たとえば、シッククライアントがファイルシステム上のファイルにアクセスするためにユーザーが送信したファイル名を使用する場合、攻撃者がこれを使用して機密データを読み取ったり、シッククライアント上で任意のコードを実行する可能性があります。ユーザーが送信したファイル名をファイルへのアクセスに使用する前に検証してサニタイズすることで、シッククライアントは攻撃者がパストラバーサル脆弱性を悪用するのを防ぐことができます。

C# では、悪い例として以下のようになるかもしれません。

```csharp
using System;
using System.IO;

public class Program
{
    public static void Main()
    {
        // Use user-submitted filename to access a file
        var filename = user_input;
        var path = Path.Combine("C:\\files", filename);
        var contents = File.ReadAllText(path);
    }
}
```

この例では、`user_input` 変数を使用してファイルシステム上のファイルへのパスを構築するため、攻撃者が機密データを読み取ったり、シッククライアント上で任意のコードを実行する可能性があります。悪意のあるユーザーは `user_input` に `..\..\..\Windows\System32\cmd.exe` のようなものを設定して、Windows Command Prompt アプリケーションを実行する可能性があります。これを軽減するには、ユーザーが送信したファイル名をファイルへのアクセスに使用する前に検証してサニタイズする必要があります。C# では、Path.GetFullPath を使用してパスを解決でき、より一般的には、既知の適切なパスのリストを使用して入力を検証できます。

```csharp
using System;
using System.IO;

public class Program
{
    public static void Main()
    {
        // Validate and sanitize user-submitted filename
        if (!IsValid(user_input))
        {
            // handle error
        }

        // Use validated and sanitized filename to access a file
        var filename = user_input;
        var path = Path.Combine("C:\\files", filename);
        var contents = File.ReadAllText(path);
    }

    public static bool IsValid(string input)
    {
        // Validate and sanitize input
        // For example, check for deny listed characters and defined list of allowed directories

        good-directories = new string[] {"C:\\files", "D:\\data"};
        deny-list = new string[] {"..", "/", "\\"};

        if (input.Any(c => deny-list.Contains(c)) || !good-directories.Contains(Path.GetDirectoryName(input)))
        {
            return false;
        }

        return true;
    }
}
```

### TASVS-CODE-4.12

メモリはアンマネージドコード内で安全に割り当てて、解放し、使用する必要があります。これにより、攻撃者がメモリ脆弱性を悪用してシッククライアント上で任意のコードを実行することを防ぐのに役立ちます。

たとえば、メモリがアンマネージドコード内で安全に割り当て、解放、使用されない場合、攻撃者はメモリ脆弱性を悪用してシッククライアント上で任意のコードを実行する可能性があります。安全なメモリ割り当て、解放、使用のプラクティスを使用することで、シッククライアントは攻撃者がメモリ脆弱性を悪用するのを防ぐことができます。

C/C++ では、悪い例として以下のようになるかもしれません。

```c
#include <stdlib.h>

void foo()
{
    // Allocate memory
    char* buffer = (char*)malloc(100);

    // Use memory
    strcpy(buffer, "Hello, world!");

    // Free memory
    free(buffer);
}
```

この例では、`buffer` 変数が安全でない方法で割り当てて、使用し、解放されるため、攻撃者がメモリ脆弱性を悪用してシッククライアント上で任意のコードを実行できる可能性があります。これを軽減するために、メモリは安全に割り当てて、使用し、解放される必要があります。

```c
#include <stdlib.h>

void foo()
{
    // Allocate memory
    char* buffer = (char*)malloc(100);

    // Check for allocation failure
    if (buffer == NULL)
    {
        // handle error
    }

    // Use memory
    strncpy(buffer, "Hello, world!", 100);

    // Free memory
    free(buffer);
}
```

この例では、`buffer` 変数が安全に割り当てて、使用し、解放され、割り当て失敗のチェックと境界チェックでメモリ脆弱性を防ぎます。これにより、攻撃者がメモリ脆弱性を悪用してシッククライアント上で任意のコードを実行するのを防ぐのに役立ちます。

### TASVS-CODE-5.1

パスワードや PIN などがシッククライアントのユーザーインタフェース上に平文で表示されると、攻撃者は簡単にそれらを盗み出して使用し、機密情報にアクセスできます。機密データがユーザーインタフェースを通じて公開されないようにすることで、シッククライアントは機密情報を認可されていないアクセスから保護できます。


### TASVS-CODE-5.2

シッククライアントの実装では、ユーザーは欺瞞的なデザインパターンによる重大なリスクに直面する。これには、偽の希少性、強制的なアクション、隠れたコスト、トリックワードなどの戦術があり、ユーザーを操作して意図しない意思決定をします。たとえば、ユーザーは購入を急がせる偽の緊急性や、同意していない隠されたサブスクリプションに遭遇するかもしれません。このような慣行は、ユーザーの自主性を損ない、不用意な約束の可能性を高め、重要な情報を不明瞭にし、金銭的およびセキュリティへの影響に及ぼす可能性があります。透明性とユーザーコントロールを確保し、これらのリスクを軽減するために不可欠です。

詳細については [Deceptive Patterns](https://www.deceptive.design/types) をご覧ください。

### TASVS-CODE-5.3

シッククライアントは、一般的なセキュリティアドバイスに違反しないワークフローのみを使用する必要である。これにより、攻撃者がシッククライアントのセキュリティ脆弱性を悪用するのを防ぐのに役立ちます。たとえば、シッククライアントが安全でない認証方法や安全でないデータストレージ方法を使用している場合などです。このコントロールはテスト担当者が直感と経験に基づいてテストプロセスを導くためのリマインダーです。

### TASVS-CODE-5.4

シッククライアントの攻撃対象領域は可能な限り小さくする必要があります。サンドボックス化やカプセル化は攻撃者がサードパーティライブラリの脆弱性を悪用するのを防ぐのに役立ちます。たとえば、サードパーティライブラリに攻撃者が任意のコードを実行できる脆弱性がある場合、ライブラリをサンドボックス化またはカプセル化することで、攻撃者が脆弱性を悪用してシッククライアントを侵害するのを防ぐことができます。リスクを抑えるには、カプセル化やサンドボックス化を使用して、サードパーティライブラリの必要な動作のみをシッククライアントに公開します。これにより、アプリケーションによって消費される機能をより適切にテストして理解できます。

サードパーティライブラリをサンドボックス化する例は以下のようになるかもしれません。

```csharp
using System;
using ThirdPartyLibrary;

public class Program
{
    public static void Main()
    {
        // Sandbox the third-party library
        using (var sandbox = new Sandbox())
        {
            // Use the third-party library in the sandbox
            sandbox.DoSomething();
        }
    }
}
```

この例では、`Sandbox` クラスを使用して、`ThirdPartyLibrary` をカプセル化し、サンドボックス外のコードにアクセスできないようにします。


### TASVS-CODE-5.5

攻撃者がインポートファイルの脆弱性を悪用してシッククライアントを侵害するのを防ぐには、インポートファイルを悪用できないようにすることが重要です。これはインポートファイルを使用する前に検証してサニタイズすることで実現できます。たとえば、シッククライアントが CSV ファイルからデータをインポートする場合、そのファイルを検証してサニタイズする必要があります。

### TASVS-CODE-5.6

If the thick client registers a URL handler or protocol handler, it is important to verify that it cannot trigger dangerous actions or introduce common vulnerabilities. For example, if the thick client registers a URL handler that allows it to open a file or execute a command, an attacker could use this to exploit memory corruption, command and argument injection, or other vulnerabilities. To mitigiate this, the thick client should validate and sanitize the URL handler or protocol handler before registering it or alternatively use an allow list of known good URLs or handlers.

### TASVS-CODE-6.1

Performing "dumb fuzzing" of the thick client with randomized input can help to identify security vulnerabilities that may be missed during manual code review. By generating random input and testing the thick client with it, the tester can identify potential security vulnerabilities that may be exploitable by an attacker.

One way to do this quickly is to use a fuzzer like [AFL]() or [libFuzzer](). These tools can automatically generate test cases and run them against the thick client to identify security vulnerabilities.

### TASVS-CODE-6.2

Performing "smart fuzzing" of the thick client can help to identify security vulnerabilities that may be missed during manual code review. By intelligently generating test cases that maximize code coverage and explore complex program states, the tester can increase the likelihood of finding vulnerabilities over "dumb fuzzing".

One way to do this is to use a fuzzer like [AFL]() or [libFuzzer]() with custom test case generation strategies, such as harnesses or mutators. These tools can automatically generate test cases and run them against the thick client to identify security vulnerabilities.

### TASVS-CODE-7.1

The thick client should follow the principle of least privileges and run with the lowest level of privileges required for it to work as expected. If several levels of privileges are required, their IPC interfaces should be well-defined and not expose more features than required. This can help to prevent attackers from exploiting privilege escalation vulnerabilities to compromise the thick client.

For example, if the thick client runs with elevated privileges, an attacker could exploit a vulnerability in the thick client to gain access to sensitive information or execute arbitrary code. By running the thick client with the lowest level of privileges required for it to work as expected, the attack surface is reduced and the risk of privilege escalation vulnerabilities is minimized.


### TASVS-CODE-7.2

The thick client should follow the "Rule of 2", where it cannot have more than 2 of the following characteristics:

- Works with untrustworthy inputs
- Is written in a memory-unsafe language
- Runs with high privileges or without a sandbox

This can help to prevent attackers from exploiting security vulnerabilities in the thick client. For example, if the thick client works with untrustworthy inputs and is written in a memory-unsafe language, an attacker could exploit memory vulnerabilities to execute arbitrary code. By following the "Rule of 2", the thick client can reduce the risk of security vulnerabilities and protect sensitive information from unauthorized access.

\newpage{}
