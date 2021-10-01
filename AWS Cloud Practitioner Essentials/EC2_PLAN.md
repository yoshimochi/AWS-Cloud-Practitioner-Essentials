# EC2の料金
## EC2は利用したコンピューティング時間に対してのみ料金が発生する（従量課金制）。

## オンデマンドインスタンス
### 初期費用や最低料金は発生せず、使用したコンピューティング時間に対して料金を支払う。中断できない不規則で短期的なワークロードに最適。ユーザーがインスタンスを停止するまで、インスタンスは継続的に実行される。
### 例）①アプリケーションの開発とテスト、②使用パターンが予測不可能なアプリケーションの実行
### 1年以上実行し続ける場合は推奨されない。そのような場合には、リザーブドインスタンスを使用することで大幅なコスト削減ができる

## Amazon EC2 Savings Plans
### 一定のコンピューティング使用料を１年または３年の期間で契約することで、コンピューティング料金をオンデマンドに比べて約７２％節約できる節約できる。契約した使用料に達するまで、割引が適用された料金で課金される。契約料を超過するとオンデマンド料金で課金される。

## リザーブドインスタンス
### オンデマンドインスタンスの利用に適用される割引。スタンダードリザーブドインスタンスとコンバーティブルリザーブドインスタンスは 1 年または 3 年の契約で購入でき、スケジュールされたリザーブドインスタンスは 1 年契約で購入できます。3 年のオプションの場合、コストを大幅に削減できます。

## スポットインスタンス
### 開始時刻と終了時刻が定まっていないワークロードや、中断可能なワークロードに最適。スポットインスタンスは、未使用のキャパシティーを利用することで、オンデマンドと比較して最大９０％コストを削減できる。
### スポットインスタンスは、スポットリクエストを行い、キャパシティーに空きがあればスポットインスタンスが作成され、空きがない場合は、空きができるまでリクエストは成功しない。スポットインスタンスを作成した後も、キャパシティーが使用できなくなったり、スポットインスタンスの需要が増えたりすると、インスタンスが中断される可能性がある。

## Dedicated Hosts
### 顧客専用のインスタンスキャパシティーを備えた物理サーバー。EC2の全料金オプションのうち最も高価なオプション。