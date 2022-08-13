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
![起動ボタン](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9201%E3%83%BC%E8%B5%B7%E5%8B%95.png)

キーペア（ログイン）-**新しいキーペア**を押下  
![新しいキーペア](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9202-%E6%96%B0%E3%81%97%E3%81%84%E3%82%AD%E3%83%BC%E3%83%9A%E3%82%A2.png)  
![キーペアを作成](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9203-%E6%96%B0%E3%81%97%E3%81%84%E3%82%AD%E3%83%BC%E3%83%9A%E3%82%A2.png)  

キーペア名を入力、**キーペアを作成**を押下  
![起動中](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9204-%E6%96%B0%E3%81%97%E3%81%84%E3%82%AD%E3%83%BC%E3%83%9A%E3%82%A2.png)  

鍵（LPIC1.pem）がローカルに保存される  
**インスタンスを起動**を押下し、インスタンスが起動するまで１分ほど待つ  
![松](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9205-%E8%B5%B7%E5%8B%95%E4%B8%AD.png)

一覧で**インスタンスの状態**が`running`であれば起動成功  
![running](https://github.com/norikata99/hello_git/blob/main/img/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202022-08-13%2021.55.59.png)

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
  
インスタンスの一覧を表示  
起動したインスタンスを選択し、**接続**を押下  
![インスタンスに接続](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9211-%E6%8E%A5%E7%B6%9A.png)  

EC2 Instance Connect（ブラウザベースのSSH接続）を選択、**接続**を押下  
![接続ボタン](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9212-%E6%8E%A5%E7%B6%9A%E3%83%9C%E3%82%BF%E3%83%B3.png)  

ログインプロンプトを確認
![a](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9213-%E6%8E%A5%E7%B6%9A%E3%83%9C%E3%82%BF%E3%83%B3.png)

確認したいコマンドを入力、`Enter`を押下し結果を確認  
![コマンド確認](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9214-%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E7%A2%BA%E8%AA%8D.png)  
![manページ](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9215-%E6%8E%A5%E7%B6%9A%E3%83%9C%E3%82%BF%E3%83%B3.png)  

***
■確認するポイント  
`man ls`のように入力することで調べたいコマンドの`man`ページを参照できます。  
実行できないコマンドは`yum`コマンドで適宜インストールしてください。  
***
&ensp;  

## <a id="jump-there4">EC2インスタンスを終了する</a>
  
一覧よりインスタンスを選択、`インスタンスの状態`→`インスタンスを終了`を押下  
終了ステータスを確認  
![インスタンス](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9221.png)
![ボリューム](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9222.png)
![20220813−23.png](https://github.com/norikata99/hello_git/blob/main/img/20220813%E2%88%9223.png)
***
■インスタンスの状態について  
**停止**をすると、後で再起動が可能です。  
**終了**はインスタンスの削除となり、二度と再起動できません。  
無料枠があるため課金されることは少ないですが、不安な方はインスタンスを終了することを勧めます。
***
