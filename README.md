[Google Play Reviews Scraper](https://apify.com/ahmed_jasarevic/google-play-reviews-scraper?fpr=data)

# 📱 Google Play Reviews Scraper & App Intelligence Tool

A powerful Apify Actor for scraping **Google Play Store apps and user reviews at scale**.

Extract structured **app data, reviews, ratings, and metadata** for:

- 📊 sentiment analysis
- 🤖 AI / LLM training datasets
- 🧠 market & competitor research
- 🐞 user feedback mining

---

## 🚀 Features

- 🔍 Search apps by keyword (e.g. `vpn`, `chatgpt`, `finance`)
- ⭐ Extract user reviews with full metadata
- 🎯 Filter by rating (1–5 stars)
- 🌍 Language & country targeting
- 🔁 Deduplicate reviews (optional)
- 📅 Filter by recency (last N days)
- 🧠 AI-ready structured output
- ⚡ Scalable multi-app scraping

---

## 📦 Input Parameters

| Field | Type | Description |
| --- | --- | --- |
| `term` | string | Search keyword for Google Play apps |
| `maxItems` | integer | Maximum number of reviews to collect |
| `appsLimit` | integer | Number of apps to scan from search results |
| `reviewsPerApp` | integer | Max reviews per app |
| `sort` | string | Sorting: `newest`, `rating`, `helpfulness` |
| `country` | string | Country code (e.g. `us`, `gb`, `de`) |
| `language` | string | Language code (e.g. `en`, `hr`) |
| `uniqueOnly` | boolean | Remove duplicate reviews |
| `ratingFilter` | integer | Exact rating filter (1–5, `0 = all`) |
| `keywords` | array | Only include reviews containing keywords |
| `recentDays` | integer | Only reviews from last N days (`0 = off`) |

---

## 🧪 Example Inputs

### 🔹 Basic scraping

```
{
  "term": "vpn",
  "maxItems": 50,
  "appsLimit": 5,
  "reviewsPerApp": 100,
  "sort": "newest",
  "country": "us",
  "language": "en",
  "uniqueOnly": true,
  "ratingFilter": 0,
  "keywords": [],
  "recentDays": 0
}
```

---

### 🔹 1-star complaint mining (bug & negative feedback)

```
{
  "term": "vpn",
  "maxItems": 100,
  "appsLimit": 10,
  "reviewsPerApp": 200,
  "sort": "newest",
  "country": "us",
  "language": "en",
  "uniqueOnly": true,
  "ratingFilter": 1,
  "keywords": [],
  "recentDays": 0
}
```

---

### 🔹 Keyword-based sentiment dataset

```
{
  "term": "chatgpt",
  "maxItems": 200,
  "appsLimit": 10,
  "reviewsPerApp": 200,
  "sort": "helpfulness",
  "country": "us",
  "language": "en",
  "uniqueOnly": true,
  "ratingFilter": 0,
  "keywords": ["bug", "crash", "slow", "amazing"],
  "recentDays": 30
}
```

---

## 📤 Output Format

Each dataset item returns **structured app + review intelligence data**:

```
{
  "type": "review",
  "appTitle": "VPN - Super Unlimited Proxy",
  "appId": "com.free.vpn.super.hotspot.open",
  "appUrl": "https://play.google.com/store/apps/details?id=com.free.vpn.super.hotspot.open",
  "developer": "VPN Super Inc",
  "summary": "Fast secure VPN service",
  "appScore": 4.7,
  "installs": "100,000,000+",

  "reviewId": "abc123",
  "user": "John Doe",
  "rating": 1,
  "text": "App keeps crashing",
  "date": "2026-05-01T00:00:00Z",
  "thumbsUp": 3,
  "version": "2.1.0",

  "language": "en",
  "country": "us",
  "source": "google-play-scraper"
}
```

---

## 🎯 Use Cases

- 📊 Sentiment analysis datasets
- 🤖 AI training (LLM fine-tuning)
- 🧠 App market intelligence
- 🏆 Competitor analysis
- 🐞 Bug & complaint mining
- 📈 Product research

---

## ⚙️ How it works

1. Search Google Play apps by keyword (`term`)
2. Select top apps (`appsLimit`)
3. Extract reviews per app (`reviewsPerApp`)
4. Apply filters:

- rating
- keywords
- date range
- duplicates
5. Return structured dataset

---

## 🧠 Optimization Tips

For best results:

- Use `reviewsPerApp >= 100`
- Combine multiple `appsLimit`
- Use `recentDays = 30` for fresh data
- Use `keywords` for niche insights
- Use `ratingFilter = 1` for complaint mining

---

## ⚠️ Notes

- Google Play does not expose full review history
- Pagination improves coverage but is still limited
- Some reviews vary by region/language