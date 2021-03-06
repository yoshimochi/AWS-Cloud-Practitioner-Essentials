# サブネットとアクセスコントロールリスト

## サブネット
 - サブネットは、セキュリティまたは運用のニーズに基づいてリソースをグループ化できるVPC内のセクション。
 - パブリックに設定することも、プライベートに設定することもできる。  
<br/>
<br/>
1. パブリックサブネット
 - オンラインストアのウェブサイトなど、一般に公開されているリソースが含まれる。

2. プライベートサブネット
 - 顧客の個人情報や注文履歴を含むデータベースなど、プライベートネットワークを介してのみアクセス可能なリソースが含まれる。

## VPCでは、サブネットは交互に通信できる。
 - 例）パブリックサブネットにある Amazon EC2 インスタンスを含むアプリケーションからプライベートサブネットにあるデータベースに通信できる。

## VPC内のネットワークトラフィック
 - 顧客がAWSクライドにあるアプリケーションからデータをリクエストすると、このリクエストはパケットとして送信される。

- **パケット** 
 - インターネットまたはネットワークを介して送信されるデータの単位。
 - パケットは、インターネットゲートウェイを介してVPCに送信される。
 - パケットは、サブネットに出入りする前に、アクセス許可がチェックされる。
 - **パケットからサブネットへのアクセス許可をチェックする VPC コンポーネントは、ネットワークアクセスコントロールリスト (ACL)**


## ネットワークアクセスコントロールリスト (ACL)
 - ネットワークアクセスコントロールリスト (ACL) は、サブネットレベルでインバウンドトラフィックとアウトバウンドトラフィックを制御する仮想ファイアウォール。

 - 入国審査官を例にすると
  - 旅行者はパケット、入国審査官はネットワーク ACL と同じように考えることができる。
  -入国審査官は、旅行者の出入国時にその旅行者の履歴情報を確認し、旅行者が承認リストに載っている場合、旅行者は入国できる。
  - ただし、旅行者が承認リストに載っていない場合、または入国禁止者のリストに明示的に載っている場合は、入国できない。


  - AWSアカウントには、デフォルトのネットワークACLがある。
  - VPCを設定する際は、デフォルトのものを使うか、カスタムネットワークACLを作成する。
  - デフォルトのACLは、全てのトラフィックが許可される。
  - 一方で、カスタムACLは、許可するトラフィックを指定するルールを追加するまで、全てのトラフィックを拒否する。

### ステートレスパケットフィルタリング
 - ネットワークACLでは、**ステートレス**パケットフィルタリングが実行される。
 - これは、処理情報が保存されないため、パケットがサブネットの境界を出入りする度にチェックを受けるため。
 - パケットがサブネットを通過すると、次はサブネット内のリソース（EC2インスタンスなど）へのアクセス許可が必要となる。
 - このアクセス許可をチェックするVPCコンポーネントが、**セキュリティグループ**である。


## セキュリティグループ
 - セキュリティグループは、Amazon EC2 インスタンスのインバウンドトラフィックとアウトバウンドトラフィックを制御する仮想ファイアウォール。
 - デフォルトでは、全てのインバウンドトラフィックを拒否し、全てのアウトバウンドトラフィックを許可する。
 - ユーザーは、カスタムルールを追加して、許可や拒否するトラフィックを設定する。
 - サブネット内に Amazon EC2 インスタンスが複数ある場合は、インスタンスを同じセキュリティグループに関連付けることも、インスタンスごとに異なるセキュリティグループを使用することもできる。

### ステートフルパケットフィルタリング
 - セキュリティグループでは、ステートフルパケットフィルタリングが実行され、受信したパケットに対して行われた処理情報は保存される。