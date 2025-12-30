# Crunchbase Scraper

[![Bright Data Promo](https://github.com/luminati-io/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.jp/products/web-scraper/crunchbase)

このリポジトリでは、Crunchbase からビジネスインテリジェンスデータを抽出するための 2 つのアプローチを提供しています。

1. **基本スクレイパースクリプト:** 軽量でブラウザ自動化型のスクレイパーで、限定的なデータ収集向けです。
2. **Bright Data Crunchbase Scraper API:** 大量かつ信頼性の高いデータ抽出のための、堅牢でスケーラブル、かつメンテナンス不要のソリューションです。

## Table of Contents
- [Basic Crunchbase Scraper](#1-basic-crunchbase-scraper)
    - [Features](#features)
    - [Prerequisites](#prerequisites)
    - [Implementation](#implementation)
    - [Sample Output](#sample-output)
    - [Limitations & Challenges](#significant-limitations--challenges)
- [Bright Data Crunchbase Scraper API](#2-bright-data-crunchbase-scraper-api)
    - [Key Benefits](#key-benefits)
    - [Getting Started](#getting-started)
    - [API Methods](#api-methods)
      - [A. Collect Crunchbase Data by URL](#a-collect-crunchbase-data-by-url)
      - [B. Discover Crunchbase Data by Keyword](#b-discover-crunchbase-data-by-keyword)
- [API Configuration & Delivery Options](#api-configuration--delivery-options)
- [No-Code Scraper Interface](#no-code-scraper-interface)
- [Alternative: Pre-Collected Crunchbase Datasets](#alternative-pre-collected-crunchbase-datasets)
- [Resources & Support](#resources--support)


## 1. Basic Crunchbase Scraper

Crunchbase のプロフィールから基本的な企業データを抽出する方法を示す Python 実装です。

<img width="800" alt="Bright Data Platform Interface" src="https://github.com/luminati-io/crunchbase-scraper/blob/main/images/440236063-03b5a4c6-ba43-4595-bab8-96161740e197.png" />

### Features

このスクリプトは、以下を含む公開データポイントを収集します。

- 企業の基本情報（説明、Web サイト、設立日）
- 連絡先情報（メール、電話）
- 運用指標（ステータス、従業員数、所在地）
- リーダーシップ情報（創業者）
- 業界分類

### Prerequisites

* Python 3.x のインストール
* SeleniumBase ライブラリ: `pip install seleniumbase`

### Implementation

1. **コードの取得:** スクリプトファイルはこちらから参照できます: [free-crunchbase-scraper/crunchbase-scraper.py](https://github.com/luminati-io/crunchbase-scraper/blob/main/free-crunchbase-scraper/crunchbase-scraper.py)
2. **対象 URL の設定:** スクリプトを開き、`target_url` 変数をスクレイピングしたい Crunchbase 企業プロフィールの URL に変更します。
    
    ```python
    target_url = "https://www.crunchbase.com/organization/your-target-company"
    ```
    
3. **スクリプトの実行:** ターミナルからスクリプトを実行します: `python crunchbase-scraper.py`


💡 **Note:** このスクリプトは [SeleniumBase](https://seleniumbase.io/) を使用しています。これは Selenium の高度なラッパーで、CAPTCHA やその他のブラウザ上の課題に対応するためのツールが組み込まれています。詳細はこちらをご覧ください: [Web Scraping with SeleniumBase](https://brightdata.jp/blog/web-data/web-scraping-with-seleniumbase) および [SeleniumBase with Proxies](https://brightdata.jp/blog/proxy-101/seleniumbase-with-proxies)。


### Sample Output

スクリプトは以下の形式で構造化データを抽出します。

```jsonc
{
  "description": "Bright Data offers a platform for ethical web data collection and analysis.",
  "website_url": "[https://brightdata.jp](https://brightdata.jp/)",
  "founding_date": "2018-07-01",
  "email": "[sales@brightdata.com](mailto:sales@brightdata.com)",
  "phone": "(888) 538-9204",
  "company_overview": "Bright Data is a data collection platform that helps businesses gather publicly available web data...",
  "headquarters_location": "New York, United States, North America",
  "operating_status": "active",
  "employee_count": "251-500",
  "founder_names": [
    "Derry Shribman",
    "Ofer Vilenski"
  ],
  "industry_categories": [
    "Business Intelligence",
    "Cloud Data Services", "/* ... */"
  ]
}
```

### Significant Limitations & Challenges

このアプローチは、重大な [Webスクレイピングの課題](https://brightdata.jp/blog/web-data/web-scraping-challenges) に直面し、本番規模のデータ収集には不向きです。

- **IP ブロッキングとレート制限:** Crunchbase は個別 IPアドレス からのリクエストを積極的に監視し、制限しています。スクレイピングを数回試みるだけで、IP がすぐにブロックされる可能性が高いです。
- **高度なアンチボット対策:** Crunchbase は、CAPTCHA（[Cloudflare Turnstile](https://brightdata.jp/products/web-unlocker/captcha-solver/cloudflare-turnstile) など）や行動分析を含む高度なセキュリティを採用しており、自動化スクリプトの検知とブロックを目的として設計されています。

  <img width="800" alt="Crunchbase CAPTCHA Challenge" src="https://github.com/luminati-io/crunchbase-scraper/blob/main/images/440239044-44cb5a79-e943-454b-9354-28b78ef67b57.png" />

- **動的な Web サイト構造:** Crunchbase は Web サイトのレイアウトやコードを頻繁に更新します。変更が入るたびにスクリプトが動かなくなる可能性があり、継続的で時間のかかるメンテナンスが必要になります。
- **スケーラビリティの問題:** この方法では、複数 URL を効率的に処理したり、大量データを扱ったりする規模へ拡張できません。
- **メンテナンス負荷:** インフラ管理、ブロック対応、スクリプト更新、コンプライアンス確保はすべてお客様側の責任となります。


## 2. Bright Data Crunchbase Scraper API
[Bright Data Crunchbase Scraper API](https://brightdata.jp/products/web-scraper/crunchbase) は、スクレイピングの複雑さに対処することなく、Crunchbase から包括的なデータを抽出できる、堅牢でスケーラブル、かつ手間のかからない方法を提供します。

### Key Benefits

- **技術的課題を回避:** 高度なプロキシローテーションと Web unlocking 技術により、IP ブロック、CAPTCHA、レート制限を自動的に処理します。
- **エンタープライズ級のスケーラビリティ:** 大量データ収集向けに設計されています。
- **高い信頼性:** エンタープライズ級の稼働率で安定したデータ配信を保証します。
- **開発者フレンドリー:** シンプルな API 統合により、複雑なスクレイパー開発とメンテナンスが不要になります。
- **構造化データ形式:** 分析にすぐ使える、クリーンで正規化されたデータを提供します。
- **規制遵守:** GDPR や CCPA を含むデータプライバシー規制に準拠します。
- **柔軟な料金体系:** データ配信成功に基づく従量課金モデルです。
- **専任サポート:** 24/7 の専門技術サポートを利用できます。
- **実装オプション:** API をプログラムから利用するか、[No-Code Scraper](https://brightdata.jp/products/web-scraper/no-code) インターフェースから利用できます。

### Getting Started

1. **アカウント作成:** [Bright Data アカウント](https://brightdata.jp/) にサインアップします *(新規ユーザーは支払い方法を追加すると $5 クレジットを受け取れます)*。
2. **API トークン生成:** ダッシュボードから固有の [API key](https://docs.brightdata.com/general/account/api-token) を取得します。
3. **実装ガイド:** 2 つの API メソッドと No-Code インターフェースの両方について、詳細な設定手順はこちらをご覧ください:
[setup-bright-data-crunchbase-scraper.md](https://github.com/luminati-io/crunchbase-scraper/blob/main/setup-bright-data-crunchbase-scraper.md)


### API Methods

この API は、主に 2 つのデータ収集アプローチを提供します。

### A. Collect Crunchbase Data by URL

特定の Crunchbase 企業 URL に対して包括的なプロフィール情報を取得します。

**Input Parameters:**

| Parameter | Required | Description |
| --- | --- | --- |
| `url` | Yes | Crunchbase の企業 URL 全体です。 |

**Example Request (Python):**

```python
config = {
    "api_token": "YOUR_API_TOKEN",  # Replace with actual token
    "organizations": [
        {"url": "https://www.crunchbase.com/organization/apple"},
        {"url": "https://www.crunchbase.com/organization/brightdata"},
    ],
    "output_file": "crunchbase-company-profiles.json", # Optional custom filename
}
# ... rest of the script uses this config
```

- `"YOUR_API_TOKEN"` を実際の Bright Data API トークンに置き換えてください。
- `organizations` リストを対象の Crunchbase URL に変更してください。
- 実行可能な完全なスクリプトはこちら: [crunchbase-scraper-api/crunchbase-profile-fetcher.py](https://github.com/luminati-io/crunchbase-scraper/blob/main/crunchbase-scraper-api/crunchbase-profile-fetcher.py)

**Example Request (cURL):**

```bash
curl -X POST \
  "https://api.brightdata.com/datasets/v3/trigger?dataset_id=gd_l1vijqt9jfj7olije&include_errors=true" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '[{"url":"https://www.crunchbase.com/organization/apple"},{"url":"https://www.crunchbase.com/organization/brightdata"}]'
```


**Sample Output Snippet:**

API は包括的で構造化されたデータを返します。以下は、単一企業に対して利用可能なフィールドのごく一部です。

```jsonc
{
  "companyName": "Bright Data",
  "legalName": "Bright Data",
  "website": "https://brightdata.jp",
  "description": "Offers a platform for ethical web data collection and analysis...",
  "foundedDate": "2014-01-01",
  "location": {"city": "New York", "state": "New York", "country": "United States"},
  "companyType": "For-Profit",
  "operatingStatus": "Active",
  "ipoStatus": "Private (Acquired)",
  "employeeSizeRange": "251-500",
  "industries": ["Business Intelligence", "Cloud Data Services", "..."],
  "keyPersonnel": {
    "ceo": {"name": "Or Lenchner", "...": "..."},
    "founders": [{"name": "Derry Shribman", "...": "..."}, {"name": "Ofer Vilenski", "...": "..."}]
  },
  "webTraffic": {"monthlyVisits": 865525, "source": "Semrush", "...": "..."},
  "technology": {"activeTechCount": 19, "exampleTechUsed": ["Cloudflare Hosting", "..."]},
  "products": {"totalActive": 23, "exampleProductNames": ["Residential Proxies", "..."]},
  "acquisitionDetails": {"acquiredBy": "EMK Capital", "priceUSD": 200000000, "...": "..."},
  "intellectualProperty": {"patentsGranted": 199, "trademarksRegistered": 18}
  // Additional data fields available
}
```

完全なサンプルレスポンスはこちら: [crunchbase-data/crunchbase-company-profiles.json](https://github.com/luminati-io/crunchbase-scraper/blob/main/crunchbase-data/crunchbase-company-profiles.json)

### B. Discover Crunchbase Data by Keyword

特定のキーワードまたは業界（例: "AI"、"Venture Capital"、"SaaS"）に関連する企業を特定します。

<img width="800" alt="Discover by Keyword Interface Example" src="https://github.com/luminati-io/crunchbase-scraper/blob/main/images/440271152-56e59e94-19fa-4977-84a0-4b70c794cb20.png" />

**Input Parameter:**

| Parameter | Required | Description |
| --- | --- | --- |
| `keyword` | Yes | 関連企業を検索するためのキーワードです。 |

**Example Request (Python):**

```python
config = {
    "api_token": "YOUR_API_TOKEN",  # Replace with actual token
    "keywords": [
        {"keyword": "AI"},
        {"keyword": "Venture Capital"},
        {"keyword": "SaaS"}
        # Add more keywords as needed
    ],
    "output_file": "crunchbase-keyword-results.json", # Optional: Customize output filename
}
# ... (script uses this config to make the API call)
```

- `"YOUR_API_TOKEN"` を置き換えてください。
- `keywords` リストを変更してください。
- 実行可能な完全なスクリプトはこちら: [`crunchbase-scraper-api/crunchbase-keyword-search.py`](https://github.com/luminati-io/crunchbase-scraper/blob/main/crunchbase-scraper-api/crunchbase-keyword-search.py)

**Example Request (cURL):**

```bash
curl -X POST \
  "https://api.brightdata.com/datasets/v3/trigger?dataset_id=gd_l1vijqt9jfj7olije&include_errors=true&type=discover_new&discover_by=keyword" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '[{"keyword":"AI"},{"keyword":"Venture Capital"}]'

```

**Sample Output Snippet:**

レスポンスには、キーワード検索に一致した *複数* 企業のデータが含まれます。以下は 1 件の結果における構造例です。

```jsonc
{
  "companyName": "Airbus", // Example result for "AI" keyword
  "legalName": "Airbus Defense and Space Holdings, Inc.",
  "website": "https://us.airbus.com",
  "description": "Airbus designs, manufactures, and delivers aerospace products...",
  "foundedDate": "2014-01-01",
  "location": {
    "city": "Herndon",
    "state": "Virginia",
    "country": "United States"
  },
  "companyType": "For-Profit",
  "operatingStatus": "Active",
  "ipoStatus": "Private",
  "employeeSizeRange": "10001+",
  "industries": [
    "Aerospace",
    "Commercial",
    "Manufacturing"
  ],
  // ... includes similar detailed fields as the 'Collect by URL' method
}
```

完全なサンプルレスポンスはこちら: [crunchbase-data/crunchbase-keyword-results.json](https://github.com/luminati-io/crunchbase-scraper/blob/main/crunchbase-data/crunchbase-keyword-results.json)

### API Configuration & Delivery Options

API リクエスト内の追加パラメータを使用して、データ収集ジョブをカスタマイズできます。

| Parameter | Type | Description | Example |
| --- | --- | --- | --- |
| `limit` | `integer` | 入力（URL または keyword）あたりの最大結果数を設定します。 | `limit=50` |
| `include_errors` | `boolean` | 問題が発生した場合、レスポンスに詳細なエラー情報を含めます。 | `include_errors=true` |
| `format` | `enum` | 希望する出力形式（`json`, `csv`, `ndjson`）を指定します。 | `format=csv` |
| `notify` | `url` | ジョブ完了時の通知を受け取るための webhook URL を指定します。 | `notify=https://...` |

データは、希望する [external storage](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-deliver-to-external-storage%3A) へ直接配信するか、[webhook](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-webhook%3A) 経由で配信できます。

Web Scraper API と収集トリガーに関する包括的なドキュメントは、以下をご覧ください。

- [Bright Data Web Scraper API Documentation](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview)
- [Trigger Collection API Reference](https://docs.brightdata.com/api-reference/web-scraper-api/trigger-a-collection)



### No-Code Scraper Interface

視覚的なポイント＆クリック操作を好むユーザー向けに、Bright Data は [No-Code Scraper](https://brightdata.jp/products/web-scraper/no-code) も提供しています。このインターフェースでは、同じ強力な基盤インフラを使用して、コードを書かずに Crunchbase のデータ収集タスクを設定し、起動できます。ガイダンスについては [Setup Guide](https://github.com/luminati-io/crunchbase-scraper/blob/main/setup-bright-data-crunchbase-scraper.md) を参照してください。

## Alternative: Pre-Collected Crunchbase Datasets

スクレイピングジョブを自分で実行せずに、構造化された Crunchbase データを大量にすぐ利用したい場合は、Bright Data の事前収集済み [Crunchbase Datasets](https://brightdata.jp/products/datasets/crunchbase) をご検討ください。

- **すぐに利用可能:** 検証済みで構造化された Crunchbase データに即時アクセスできます。
- **包括的なカバレッジ:** データセットには企業プロフィールあたり 100 以上のデータポイントが含まれます。
- **定期更新:** データ鮮度のオプション（毎日、毎週、毎月、またはカスタム）を選択できます。
- **柔軟な購入オプション:** データセット全体、またはニーズと予算に合わせた特定サブセットを取得できます。
- **容易な統合:** API 連携または直接ダウンロードで、データセットをシームレスに統合できます。
- **サンプルデータ提供:** データ品質と適合性を評価するためのサンプルをリクエストできます。


## Resources & Support

- **Bright Data Documentation:**
    - [Crunchbase Scraper API Product Page](https://brightdata.jp/products/web-scraper/crunchbase)
    - [Web Scraper API Documentation](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview)
    - [API Reference: Trigger Collection](https://docs.brightdata.com/api-reference/web-scraper-api/trigger-a-collection)
    - [Datasets Product Page](https://brightdata.jp/products/datasets)
    - [Getting Your API Token](https://docs.brightdata.com/general/account/api-token)
- **Guides & Blog Posts:**
    - [How to Scrape Crunchbase (Comprehensive Guide)](https://brightdata.jp/blog/web-data/how-to-scrape-crunchbase)
    - [Web Scraping Without Getting Blocked](https://brightdata.jp/blog/web-data/web-scraping-without-getting-blocked)
    - [Setup Guide for Bright Data Crunchbase Scraper (in this repo)](https://github.com/luminati-io/crunchbase-scraper/blob/main/setup-bright-data-crunchbase-scraper.md)
- **Technical Support:** Bright Data のサポートチームへは、アカウントダッシュボードまたはメール [support@brightdata.com](mailto:support@brightdata.com) から 24/7 でお問い合わせいただけます。