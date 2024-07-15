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
| TASVS-CODE-4.1  | マクロやテンプレートなどの機能を介した信頼できないデータはコードおよびコマンドインジェクション攻撃から保護します。代替手段がない場合、含まれているあらゆるユーザー入力は実行前にサニタイズまたはサンドボックス化しなければなりません。                                                         | X  | X  | X  |
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

Depending on the language(s) in use, appropriate static application security testing (SAST) tooling should be used to analyze the source code of the thick client. This can help to identify vulnerabilities in the code that may be missed during manual code review.

Tools such as [SonarQube](https://www.sonarqube.org/), [Checkmarx](https://www.checkmarx.com/), and [Veracode](https://www.veracode.com/) can be used to perform static code analysis on the thick client codebase. Plus framework specific tools like [Brakeman](https://brakemanscanner.org/) for Ruby on Rails, [Bandit](https://bandit.readthedocs.io/en/latest/) for Python, and [FindBugs](http://findbugs.sourceforge.net/) for Java.

### TASVS-CODE-3.5

Internal tooling, policies, and test cases should be implemented and evaluated to ensure that they are working correctly. This can help to ensure that the thick client is developed and maintained in a manner that minimizes the introduction of security vulnerabilities.

These might include code review processes, automated testing tools, and security training for developers. It is important to regularly review and update these tools and processes to ensure that they are effective in identifying and mitigating security vulnerabilities.

### TASVS-CODE-3.6

Unused code should be identified and removed from the thick client codebase. This can help to reduce the attack surface of the thick client and minimize the risk of security vulnerabilities. It is important to use README and changelog files to preserve high-value historical context or deprecated details. Obsolote project repositories should be archived because they risk being used as a source of vulnerabilities in future projects.

### TASVS-CODE-4.1

Untrusted data should be protected from code and command injection attacks. This can be done by sanitizing or sandboxing user input before it is executed. If there is no alternative to including user input in the thick client, it should be sanitized or sandboxed to prevent code and command injection attacks.


### TASVS-CODE-4.2

The thick client should protect against OS command injection attacks. This can be done by validating and sanitizing user input before it is executed, and by using secure coding practices to prevent command injection vulnerabilities.

### TASVS-CODE-4.3

Unstructured data should be sanitized to enforce safety measures such as allowed characters and length. This can help to prevent security vulnerabilities that may be introduced by unstructured data, such as buffer overflows or injection attacks.

### TASVS-CODE-4.4

The thick client should restrict XML parsers to use the most restrictive configuration possible to prevent XML eXternal Entity (XXE) attacks. This can help to prevent attackers from exploiting XML parsers to read sensitive data or execute arbitrary code on the thick client.

### TASVS-CODE-4.5

The thick client should use memory-safe string, safer memory copy, and pointer arithmetic to detect or prevent stack, buffer, or heap overflows. This can help to prevent attackers from exploiting memory vulnerabilities to execute arbitrary code on the thick client.

Safe alternatives to common string functions like `strcpy` and `strcat` should be used to prevent buffer overflows. Memory-safe string functions like `strlcpy` and `strlcat` are available in many programming languages and can help to prevent buffer overflows.

### TASVS-CODE-4.6

Format strings should not take potentially hostile input, and should be constant. This can help to prevent attackers from exploiting format string vulnerabilities to read sensitive data or execute arbitrary code on the thick client.

An attack might look like this:

```c
char buffer[100];
snprintf(buffer, sizeof(buffer), user_input);
```

If `user_input` contains a format string specifier like `%s`, an attacker could use it to read sensitive data or execute arbitrary code on the thick client.

For example if `user_input` is `"%s"`, the `snprintf` function will try to read a string from memory and write it to the buffer. This can lead to a buffer overflow or other memory corruption vulnerability.

If user_input is `"%x %x %x %x"`, `snprintf` will interpret this as reading four hexadecimal values from the stack, potentially leaking stack contents.

To mitigate this, the format string should be constant, like this:

```c
snprintf(buffer, sizeof(buffer), "%s", user_input);
```

Notice that the format string is constant i.e. `"%s"` and not `user_input`.



### TASVS-CODE-4.7

Sign, range, and input validation techniques should be used to prevent integer overflows. This can help to prevent attackers from exploiting integer overflows to execute arbitrary code on the thick client.

For exmaple in C/C++:

```c
int a = 100;
int b = 200;
int c = a + b;
```

If `a` and `b` are user-controlled, an attacker could set them to values that cause an integer overflow, resulting in `c` being a negative value. This can lead to unexpected behavior or security vulnerabilities in the thick client.

To mitigate this, input validation should be used to ensure that `a` and `b` are within a valid range before performing the addition:

```c
if (a > INT_MAX - b) {
    // handle error
}
int c = a + b;
```


### TASVS-CODE-4.8

Serialized objects should use integrity checks or be encrypted to prevent hostile object creation or data tampering. This can help to prevent attackers from exploiting serialization vulnerabilities to execute arbitrary code on the thick client.

For example, if an attacker can modify a serialized object before it is deserialized, they could introduce malicious code or data into the thick client. By using integrity checks or encryption, the thick client can verify that the serialized object has not been tampered with before deserializing it.

In C# a bad example might look like this:

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

In this example, an attacker could modify the `serialized` object before it is deserialized, potentially introducing malicious code or data into the thick client. To mitigate this, integrity checks or encryption should be used to verify that the serialized object has not been tampered with before deserializing it.

A good implementation might look like this:

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

In this example, a hash of the serialized object is calculated before it is deserialized, and the hash is verified after deserialization to ensure that the object has not been tampered with. This can help to prevent attackers from exploiting serialization vulnerabilities to execute arbitrary code on the thick client.


### TASVS-CODE-4.9

Deserialization of untrusted data should be avoided or protected in both custom code and third-party libraries. This can help to prevent attackers from exploiting deserialization vulnerabilities to execute arbitrary code on the thick client.

For example, if an attacker can control the data that is deserialized by the thick client, they could introduce malicious code or data into the application. By avoiding deserialization of untrusted data or protecting it with integrity checks or encryption, the thick client can verify that the data has not been tampered with before deserializing it.

It is recommended to use safer libraries where possible and to validate the data before deserializing it. For example, in C# the `DataContractSerializer` class can be used to deserialize JSON data in a safer way than the `BinaryFormatter` class.

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

In this example, the `DataContractJsonSerializer` class is used to deserialize JSON data in a safer way than the `BinaryFormatter` class. This can help to prevent attackers from exploiting deserialization vulnerabilities to execute arbitrary code on the thick client.


### TASVS-CODE-4.10

The thick client's handling of spawning processes should be done securely. This can help to prevent attackers from exploiting process spawning vulnerabilities to execute arbitrary code on the thick client.

For example, if the thick client spawns a process with user-controlled arguments, an attacker could use this to execute arbitrary code on the thick client. By validating and sanitizing process arguments before spawning a process, the thick client can prevent attackers from exploiting process spawning vulnerabilities.

In C# a bad example might look like this:

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

In this example, the `user_input` variable is used to construct the arguments for the `cmd.exe` process, potentially allowing an attacker to execute arbitrary code on the thick client. A malicious user could set `user_input` to something like `"; calc.exe;` to execute the Windows Calculator application. To mitigate this, process arguments should be validated and sanitized before spawning a process:

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

In this example, the `IsValid` function is used to validate and sanitize the `user_input` variable before it is used to construct the arguments for the `cmd.exe` process. This can help to prevent attackers from exploiting process spawning vulnerabilities to execute arbitrary code on the thick client.

### TASVS-CODE-4.11

User-submitted filename metadata should not be used directly by system or framework filesystems to prevent path traversal attacks. This can help to prevent attackers from exploiting path traversal vulnerabilities to read sensitive data or execute arbitrary code on the thick client.

For example, if the thick client uses user-submitted filenames to access files on the filesystem, an attacker could use this to read sensitive data or execute arbitrary code on the thick client. By validating and sanitizing user-submitted filenames before using them to access files, the thick client can prevent attackers from exploiting path traversal vulnerabilities.

In C# a bad example might look like this:

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

In this example, the `user_input` variable is used to construct the path to a file on the filesystem, potentially allowing an attacker to read sensitive data or execute arbitrary code on the thick client. A malicious user could set `user_input` to something like `..\..\..\Windows\System32\cmd.exe` to execute the Windows Command Prompt application. To mitigate this, user-submitted filenames should be validated and sanitized before using them to access files, in C# Path.GetFullPath can be used to resolve the path and more generally a known good list of paths can be used to validate the input.

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

Memory should be allocated, freed, and used securely in unmanaged code. This can help to prevent attackers from exploiting memory vulnerabilities to execute arbitrary code on the thick client.

For example, if memory is not allocated, freed, and used securely in unmanaged code, an attacker could exploit memory vulnerabilities to execute arbitrary code on the thick client. By using secure memory allocation, freeing, and usage practices, the thick client can prevent attackers from exploiting memory vulnerabilities.

In C/C++ a bad example might look like this:

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

In this example, the `buffer` variable is allocated, used, and freed in an insecure way, potentially allowing an attacker to exploit memory vulnerabilities to execute arbitrary code on the thick client. To mitigate this, memory should be allocated, used, and freed securely:

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

In this example, the `buffer` variable is allocated, used, and freed securely, with checks for allocation failure and bounds checking to prevent memory vulnerabilities. This can help to prevent attackers from exploiting memory vulnerabilities to execute arbitrary code on the thick client.

### TASVS-CODE-5.1

If passwords or pins are displayed in clear text on the user interface of the thick client, an attacker could easily steal them and use them to access sensitive information. By ensuring that sensitive data is not exposed through the user interface, the thick client can protect sensitive information from unauthorized access.


### TASVS-CODE-5.2

In thick client implementations, users face significant risks due to deceptive design patterns. These include tactics like fake scarcity, forced actions, hidden costs, and trick wording, which manipulate users into making unintended decisions. For instance, users might encounter fake urgency to rush purchases or hidden subscriptions they didn't consent to. Such practices undermine user autonomy, increase the likelihood of inadvertent commitments, and obscure critical information, leading to potential financial and security implications. Ensuring transparency and user control is crucial to mitigate these risks.

For more details, visit [Deceptive Patterns.](https://www.deceptive.design/types)

### TASVS-CODE-5.3

The thick client should only use workflows that do not violate common security advice. This can help to prevent attackers from exploiting security vulnerabilities in the thick client. For example, if the thick client uses insecure authentication methods or insecure data storage practices. This control is a reminder to the tester to allow intuition and experience to guide the testing process.

### TASVS-CODE-5.4

The attack surface of the thick client should be reduced to be as small as possible. Sandboxing or encapsulation can help to prevent attackers from exploiting vulnerabilities in third-party libraries. For example, if a third-party library has a vulnerability that allows an attacker to execute arbitrary code, sandboxing or encapsulating the library can prevent the attacker from exploiting the vulnerability to compromise the thick client. We can limit the risk by using encapsulation or sandboxing to expose only the required behavior of the third-party library to the thick client. This allows us to better test and understand the functionality consumed by the application.

An example of sandboxing a third-party library might look like this:

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

In this example, the `Sandbox` class is used to encapsulate the `ThirdPartyLibrary` and prevent it from accessing code outside of the sandbox.


### TASVS-CODE-5.5

To prevent attackers from exploiting vulnerabilities in import files to compromise the thick client, it is important to ensure that import files cannot be abused. This can be done by validating and sanitizing import files before using them. For example, if the thick client imports data from a CSV file, the file should be validated and sanitized.

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
