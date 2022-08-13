# LPIC1学習用のサーバー構築手順【AWS EC2】
## サーバー構築の目的  
- CLIによる基本のLinuxコマンドの確認を行う  
## 動作環境
- macOS Monterey バージョン12.4
- Chrome バージョン: 104.0.5112.79（Official Build）（arm64）

&ensp;  

# 手順  
- [AWSアカウントを開設する（省略）](#jump-there1)  
- [EC2インスタンスを起動する](#jump-there2)
- [Linuxコマンドを確認する](#jump-there3)
- [EC2インスタンスを終了する](#jump-there4)  
***  
&ensp;  
## <a id="jump-there1">AWSアカウントを開設する（省略）　　</a>  
まず[こちら](https://aws.amazon.com/jp/register-flow/)を参照しAWSアカウントを作成  
途中、[住所の英語への変換](http://judress.tsukuenoue.com/)が必要  

&ensp;  

## <a id="jump-there2">EC2インスタンスを起動する</a>  
  

コンソールにサインイン後、EC2サービスにアクセス  
インスタンスを起動を押下  
![起動ボタン]()

キーペア（ログイン）-**新しいキーペア**を押下  
![新しいキーペア]()  

キーペア名を入力、**キーペアを作成**を押下  
![キーペアを作成]()  

鍵（LPIC1.pem）がローカルに保存される  
**インスタンスを起動**を押下し、インスタンスが起動するまで１分ほど待つ  
![起動中]()  

一覧で**インスタンスの状態**が`running`であれば起動成功  

***
■パタメータまとめ  
なお今回は**キーペア**以外の設定は必要なくデフォルトのままで大丈夫です  
- **名前とタグ**：サーバの名前を設定します  
- **アプリケーションおよび OS イメージ (Amazon マシンイメージ)**  
  -  **Amazonマシンイメージ（AMI)**：OSを選択します
  -  **アーキテクチャ**：アーキテクチャを選択します
- **インスタンスタイプ**：CPU・メモリのスペックを選択します
- **キーペア（ログイン）**：接続に必要なキーペアを作成します。今回は作成のみ、使用しません。  
- **ネットワーク設定**：VPC,サブネット他の設定を行います
- **ストレージを設定**：ストレージのサイズ・種類を選択します
***  

&ensp;  

## <a id="jump-there3">Linuxコマンドを確認する</a>
  
起動したインスタンスを選択し、**接続**を押下  
![インスタンスに接続]()  

EC2 Instance Connect（ブラウザベースのSSH接続）を選択、**接続**を押下  
![接続ボタン]()  

ログインプロンプトを確認
![接続ボタン]()  

確認したいコマンドを入力、`Enter`を押下し結果を確認  
![コマンド確認]()  
![manページ]()  

***
■確認するポイント  
`man cat`のように入力することで調べたいコマンドの`man`ページを参照できます。  
実行できないコマンドは`yum`コマンドで適宜インストールしてください。  
***
&ensp;  

## <a id="jump-there4">EC2インスタンスを終了する</a>
  
一覧よりインスタンスを選択、`アクション`→`インスタンスの状態`→`終了`を押下  
インスタンス、ボリュームがなくなっていることを確認  
![インスタンス]()  
![ボリューム]()  

***
■インスタンスの状態について  
**停止**をすると、後で再起動が可能です。  
**終了**はインスタンスの削除となり、二度と再起動できません。  
無料枠があるため課金されることは少ないですが、不安な方はインスタンスを終了することを勧めます。
***