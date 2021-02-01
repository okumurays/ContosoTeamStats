# ContosoTeamStats
Microsoft社の公式ドキュメントに記載のある"チュートリアル:ASP.NET でキャッシュ アサイド スコアボードを作成する"を実装したサンプルアプリです  
- [チュートリアル:ASP.NET でキャッシュ アサイド スコアボード](https://docs.microsoft.com/ja-jp/azure/azure-cache-for-redis/cache-web-app-cache-aside-leaderboard "チュートリアル:ASP.NET でキャッシュ アサイド スコアボード")

# 概要
- Visual Studioでのローカル作業が負担になると思い、GitHubに動作するコードとして用意しました
- DatabaseとしてSQL Database、CacheとしてAzure Cache for Redisを利用したサンプルアプリです

# 使い方
## 前提
- 上記ページの下記ステップまで完了していること
  - [アプリのデータベースをプロビジョニングする](https://docs.microsoft.com/ja-jp/azure/azure-cache-for-redis/cache-web-app-cache-aside-leaderboard#provision-a-database-for-the-app "アプリのデータベースをプロビジョニングする")
  - プライベートエンドポイントを利用しない場合は、SQL Database側のファイアウォールでApp Serviceの送信IPアドレスを追加する必要がある
    - App Serviceの送信IPアドレスは、[設定] - [プロパティ]から確認可能
---
1. 本リポジトリをご自身のリポジトリにforkする
1. 下記条件でAzure App Serviceの作成を行う

|項目名|値|
|:--|:--|
|**名前**|任意の文字|
|**公開**|コード|
|**ランタイムスタック**|ASP.NET V4.8|
|**オペレーティングシステム**|Windows|
|**地域**|任意のリージョン|
|**Windowsプラン**|新規作成|
|**SKUとサイズ**|**S1**以上|

3. デプロイメント - デプロイセンターを選択
4. 下記設定でデプロイ設定の保存

|項目名|値|
|:--|:--|
|**ソース**|GitHub|
|**プロバイダー**|**App Service のビルド サービス**に変更|
|**組織**|ご自身のGitHubアカウント|
|**リポジトリ**|ContosoTeamStats|
|**ブランチ**|master|

5. ログ タブに移動し、デプロイが成功したことを確認する
6. 下記手順に従い、Cacheの接続文字列を設定する
- [アプリの設定を追加するには](https://docs.microsoft.com/ja-jp/azure/azure-cache-for-redis/cache-web-app-howto#to-add-the-app-setting "アプリの設定を追加するには")
- ただし末尾に,allowAdmin=trueを追加すること
  - (例) xxxx.redis.cache.windows.net:6380,password=xxxxx,ssl=True,abortConnect=False,allowAdmin=true

# License

[MIT](https://github.com/okumurays/ContosoTeamStats/blob/master/LICENSE)

# Author

[okumurays](https://github.com/okumurays)


