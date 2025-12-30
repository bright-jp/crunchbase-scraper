# Bright Data Crunchbase Scraper のセットアップ

本ガイドでは、Crunchbase 向けの Bright Data Web Scraper をセットアップして使用する方法を、手順に沿って説明します。Bright Data の強力なインフラストラクチャを活用して、API によるプログラム経由、またはユーザーフレンドリーなノーコードインターフェース経由で、Crunchbase プロフィールからデータを収集できます。

**前提条件:**

* 有効な Bright Data アカウント。

## 手順

1.  **Bright Data にログインします:**
    Bright Data ダッシュボードにアクセスします。
2.  **Web Scrapers Library に移動します:**
    * 左側メニューで **Web Scrapers** タブを選択します。
    * **Web Scrapers Library** サブタブを選択します。

    ![Bright Data Dashboard](https://github.com/user-attachments/assets/f680db57-a15a-4bd9-8dfc-f7cab5e3219b)

3.  **Crunchbase Scraper を見つけます:**
    * 検索バーを使用し、「crunchbase」と入力します。
    * 検索結果から **crunchbase.com** スクレイパーを選択します。

    ![Search for Crunchbase Scraper](https://github.com/user-attachments/assets/faf6ef56-859c-4cd9-baef-ace81d6cfe1d)

4.  **Scraper タイプを選択します:**
    Crunchbase 向けに複数のスクレイパーテンプレートが表示されます。本ガイドでは **Collect by URL** オプションに焦点を当てます。これを選択します。

    ![Select Collect by URL](https://github.com/user-attachments/assets/fc1cc4dc-b637-44db-b782-81a9be0cf92f)

5.  **操作方法を選択します:**
    Bright Data では、スクレイパーを使用する方法が 2 つあります:
    * **Scraper APIs:** アプリケーションへのプログラム統合向けです。
    * **No-code scraper:** コードを書かずに、ユーザーインターフェース主導で進める方法です。

    ニーズに最も合う方法を選択し、**Next** を選択します。

    ![Choose Scraper API or No-code](https://github.com/user-attachments/assets/3b9518a2-ce00-4e90-9f8b-44ff3be30d54)

### オプション A: Scraper API を使用する

**Scraper APIs** を選択した場合、API 設定ダッシュボードに移動します。

![Crunchbase Scraper API Dashboard](https://github.com/user-attachments/assets/63e80d6e-5c57-4f2e-8d3c-300baa5f43a1)

**設定と使用方法:**

1.  **API Request Builder:**
    * **Inputs:** スクレイピングしたい特定の Crunchbase URL を追加します。
    * **Output Format:** 目的のデータ形式（JSON、CSV）を選択します。
    * **Data Delivery:** データの受け取り方法を設定します:
        * [Deliver to External Storage](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-deliver-to-external-storage%3A)（例: Email、S3、Google Cloud Storage、SFTP）。
        * [Send to Webhook](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-webhook%3A)。
    * **Notifications:** ジョブの完了時または失敗時に通知を受け取るための URL を設定します。

2.  **スクレイパーの実行:**
    * 設定を調整すると、右側のリクエストビルダーが自動的に更新されます。
    * すぐに使える **cURL command**、または各種プログラミング言語（Python、Node.js、Java、C#、PHP など）のコードスニペットが提供されます。
    * 生成されたコードをコピーし、ターミナルから実行するか、アプリケーションに統合します。

3.  **追加機能:**
    * **Overview Tab:** API 使用状況に関する一般情報です。
    * **Management APIs Tab:** スクレイパーインスタンスをプログラムで管理するための API です。
    * **Logs Tab:** API リクエストおよびスクレイパー実行の詳細ログです。

すべての設定に関する包括的な概要については、[Web Scraper API Documentation](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview) を参照してください。

### オプション B: No-code Scraper を使用する

**No-code scraper** を選択した場合、設定用のユーザーフレンドリーなインターフェースが表示されます。

**設定と実行:**

1.  **入力 URL:**
    * 複数の Crunchbase URL を入力フィールドに直接貼り付けます（1 行につき 1 URL）。
    * 代わりに、URL リストを含む **CSV file をアップロード** することもできます。

2.  **Data Delivery 設定:**
    * データの配信方法と配信先（例: Email、クラウドストレージ）を設定します。
    * 配信設定のトグルを選択して設定します。詳細は [Data Delivery Settings](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-deliver-to-external-storage%3A) を参照してください。

3.  **開始とダウンロード:**
    * 入力と配信設定が完了したら、**Start collecting** ボタンを選択します。

      ![No-code Scraper Input Configuration](https://github.com/user-attachments/assets/ee2b3bc4-9d42-45c2-99f2-e9387548ff26)

    * 収集が完了したら、希望する形式（JSON、CSV、JSONL、または NDJSON）でデータをダウンロードします。
    
      ![Download Data Options](https://github.com/user-attachments/assets/f3fd94f3-c995-46a5-aaaa-3f5ad3361e4c)