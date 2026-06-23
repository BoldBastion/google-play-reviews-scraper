[Google Play Reviews Scraper](https://apify.com/webdatalabs/google-play-reviews-scraper?fpr=data)

⚡ **1000 reviews in 30 seconds** | 💰 **Pay-per-event pricing** | 🔄 **Incremental scraping**

Scrape Google Play reviews at scale with features competitors don't offer. Perfect for sentiment analysis, competitor research, and automation workflows.

## 🌟 Key Features

### Advanced Capabilities

- ✅ **Incremental scraping** - Save 90% time for scheduled runs with `since` parameter
- ✅ **Developer reply tracking** - Analyze competitor engagement rates and community management
- ✅ **Webhook support** - Real-time integration with n8n, Zapier, Make.com
- ✅ **Pre-filtered views** - Negative reviews, unanswered reviews, developer engagement
- ✅ **Batch processing** - Scrape 100+ apps at once
- ✅ **Flexible filtering** - Star ratings, helpful votes, language, country, developer replies

### Differentiation vs Competitors

- 🔥 **Only actor with incremental scraping** - Avoid reprocessing reviews on scheduled runs
- 🔥 **Developer engagement analysis** - Track reply rates for competitor research
- 🔥 **Automation-first design** - Webhooks, error handling, continuous operation
- 🔥 **Multiple dataset views** - Instant insights without manual filtering

## 📊 Use Cases

### Game Publishers

Monitor player feedback across your portfolio. Schedule daily runs to catch new reviews and respond quickly to issues.

**Example Workflow:**

1. Configure actor with your game app IDs
2. Schedule daily runs at 9am
3. Actor scrapes only new reviews (incremental)
4. Webhook triggers Slack alert for 1-2 star reviews
5. Team responds within hours

### Product Managers

Track sentiment trends over time. Identify feature requests and pain points from user reviews.

**Example Workflow:**

1. Scrape competitor apps + your own app
2. Compare developer reply rates
3. Analyze negative reviews for common themes
4. Export to sentiment analysis tools

### Competitor Analysis

Compare developer engagement rates. See which competitors actively respond to reviews.

**Example Workflow:**

1. Batch scrape top 10 competitors
2. Use "Developer Engagement" view
3. Calculate reply rate for each competitor
4. Benchmark against your own engagement

### Automation Builders

Real-time alerts for negative reviews. Integrate with CRM, support systems, or analytics platforms.

**Example Workflow:**

1. Set `webhookUrl` to n8n/Zapier endpoint
2. Actor sends each review as it's scraped
3. Downstream system filters for 1-2 stars
4. Creates support ticket automatically

## 🚀 Quick Start

### Basic Usage

```
{
  "appIds": ["com.mojang.minecraftpe"],
  "maxReviewsPerApp": 100,
  "sortBy": "NEWEST"
}
```

### Advanced Example - Incremental Scraping

```
{
  "appIds": [
    "com.mojang.minecraftpe",
    "com.roblox.client",
    "com.supercell.clashofclans"
  ],
  "maxReviewsPerApp": 500,
  "sortBy": "NEWEST",
  "minRating": 1,
  "maxRating": 2,
  "hasReplyOnly": false,
  "language": "en",
  "country": "us",
  "since": "2025-01-01T00:00:00Z",
  "webhookUrl": "https://your-webhook.com/endpoint"
}
```

## 📥 Input Parameters

### Required

| Parameter | Type | Description | Example |
| --- | --- | --- | --- |
| `appIds` | array | Google Play app IDs or URLs | `["com.android.chrome"]` |

### Optional

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `maxReviewsPerApp` | integer | 50 | Max reviews per app (1-100,000). Free tier: 50 suggested. |
| `sortBy` | enum | `NEWEST` | Sort order: `NEWEST`, `RATING`, `HELPFULNESS` |
| `minRating` | integer | 1 | Minimum star rating (1-5) |
| `maxRating` | integer | 5 | Maximum star rating (1-5) |
| `language` | string | `en` | Two-letter language code (en, de, fr, etc.) |
| `country` | string | `us` | Two-letter country code (us, uk, de, etc.) |
| `hasReplyOnly` | boolean | false | Only reviews with developer replies |
| `minHelpfulCount` | integer | 0 | Minimum helpful votes |
| `since` | string | - | ISO datetime or reviewId for incremental scraping |
| `webhookUrl` | string | - | POST each review to this URL (n8n/Zapier/Make.com) |

### Filter Examples

**Negative reviews only:**

```
{
  "minRating": 1,
  "maxRating": 2
}
```

**Popular reviews with developer replies:**

```
{
  "minHelpfulCount": 10,
  "hasReplyOnly": true
}
```

**Incremental - only reviews after January 1, 2025:**

```
{
  "since": "2025-01-01T00:00:00Z"
}
```

## 📤 Output Schema

### Fields

| Field | Type | Description | Example |
| --- | --- | --- | --- |
| `reviewId` | string | Unique Google Play review ID | `gp:AOqpTOHPW7X...` |
| `appId` | string | App package ID | `com.mojang.minecraftpe` |
| `rating` | integer | Star rating (1-5) | `5` |
| `title` | string | Review title | `"Great game!"` |
| `text` | string | Review body | `"This app works perfectly..."` |
| `userName` | string | Author name | `"John Doe"` |
| `userImage` | string/null | Author avatar URL | `https://play-lh...` |
| `reviewDate` | string | ISO 8601 date | `2025-01-10T00:00:00.000Z` |
| `version` | string/null | App version reviewed | `1.20.51.01` |
| `thumbsUp` | integer | Helpful votes | `12` |
| `replyText` | string/null | Developer reply | `"Thank you for feedback!"` |
| `replyDate` | string/null | Reply date (ISO 8601) | `2025-01-11T00:00:00.000Z` |
| `url` | string | Direct review link | `https://play.google.com...` |
| `scrapedAt` | string | Scrape timestamp (ISO 8601) | `2025-10-19T14:30:00.000Z` |

### Dataset Views

The actor provides 4 pre-configured views in Apify Console:

1. **Overview** - Complete review data with key fields
2. **Negative Reviews (1-2 Stars)** - Low-rated reviews for issue detection
3. **Unanswered Reviews** - Reviews without developer replies
4. **Developer Engagement** - Reviews with developer replies

### Sample Output

```
{
  "reviewId": "gp:AOqpTOHPW7XqQGJvN...",
  "appId": "com.mojang.minecraftpe",
  "rating": 5,
  "title": "Best game ever!",
  "text": "This game is amazing and runs perfectly on my device. Highly recommended!",
  "userName": "John Doe",
  "userImage": "https://play-lh.googleusercontent.com/...",
  "reviewDate": "2025-01-10T00:00:00.000Z",
  "version": "1.20.51.01",
  "thumbsUp": 12,
  "replyText": "Thank you for your support! We're glad you're enjoying the game.",
  "replyDate": "2025-01-11T00:00:00.000Z",
  "url": "https://play.google.com/store/apps/details?id=com.mojang.minecraftpe&reviewId=gp:AOqpTOHPW7X...",
  "scrapedAt": "2025-10-19T14:30:00.000Z"
}
```

## 💰 Pricing

### Pricing Model

- **Free Tier**: 50 reviews per app (suggested, configurable) - perfect for testing
- **Pay-Per-Event**: Transparent pricing based on reviews successfully scraped

See current pricing in the Apify Console when starting a run.

### Cost Control

- Set `maxReviewsPerApp` to control costs per run
- Use incremental scraping to avoid reprocessing reviews
- Scheduled runs only scrape new reviews (massive cost savings)

## 🔧 Advanced Features

### Incremental Scraping (Scheduled Runs)

The `since` parameter allows you to scrape only new reviews since a specific date/time or reviewId.

**Benefits:**

- 10x faster for scheduled runs
- Avoid paying for duplicate reviews
- Perfect for daily/weekly monitoring

**How it works:**

1. First run: Scrape all reviews (e.g., 1000 reviews)
2. Actor saves state (last reviewId)
3. Second run: Use `since` parameter OR omit it (actor uses saved state)
4. Only new reviews are scraped (e.g., 50 reviews)

**Example - Manual incremental:**

```
{
  "appIds": ["com.android.chrome"],
  "since": "2025-01-15T00:00:00Z"
}
```

**Example - Automatic incremental:**

```
{
  "appIds": ["com.android.chrome"]
}
```

*(Actor automatically uses saved state from previous run)*

### Webhook Integration

Send each review to a webhook URL for real-time processing.

**Supported platforms:**

- n8n
- Zapier
- Make.com
- Custom endpoints

**Example workflow (n8n):**

1. Create n8n webhook endpoint
2. Configure actor with `webhookUrl`
3. Actor POSTs each review as JSON
4. n8n workflow:

- Filter for 1-2 star reviews
- Create Slack alert
- Create support ticket in Zendesk
- Update dashboard

**Example - Webhook configuration:**

```
{
  "appIds": ["com.example.app"],
  "webhookUrl": "https://your-n8n.com/webhook/xyz123"
}
```

### Batch Processing

Scrape multiple apps in a single run.

**Example - Portfolio monitoring:**

```
{
  "appIds": [
    "com.game1.app",
    "com.game2.app",
    "com.game3.app",
    "com.game4.app"
  ],
  "maxReviewsPerApp": 200
}
```

**Benefits:**

- Monitor entire app portfolio
- Compare reviews across apps
- Single scheduled task

### Developer Engagement Analysis

Track which apps have active developers responding to reviews.

**Use "Developer Engagement" view to:**

- Calculate reply rate (% of reviews with replies)
- Measure response time (review date vs reply date)
- Benchmark against competitors

**Example - Find engaged developers:**

```
{
  "appIds": ["competitor1", "competitor2", "competitor3"],
  "hasReplyOnly": true,
  "maxReviewsPerApp": 500
}
```

## 🔒 Privacy & Compliance

- Only scrapes publicly available review data
- No authentication required
- Respects Google Play's rate limits (5 requests/second)
- Datacenter proxies sufficient (included in Apify)

## 🛠️ Technical Details

### Rate Limiting

- Built-in throttling: 5 requests/second (conservative)
- Exponential backoff on errors (2s, 4s, 8s, 16s, 32s)
- Handles 503/429 rate limit errors gracefully

### Error Handling

- Individual app failures don't stop entire run
- Continues to next app on error
- Detailed error logging for debugging

### State Management

- Saves last reviewId per app for incremental scraping
- State persists between runs (automatic)
- Manual override with `since` parameter

## 📚 API Usage

### Run via Apify API

```
curl -X POST https://api.apify.com/v2/acts/YOUR_ACTOR_ID/runs \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{
    "appIds": ["com.android.chrome"],
    "maxReviewsPerApp": 100,
    "sortBy": "NEWEST"
  }'
```

### Run via Apify Client (Node.js)

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('YOUR_ACTOR_ID').call({
  appIds: ['com.android.chrome'],
  maxReviewsPerApp: 100,
  sortBy: 'NEWEST',
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

## 🔗 Integration Examples

### n8n Workflow

1. **Trigger:** Schedule (daily at 9am)
2. **Apify Node:** Run Google Play Reviews Scraper
3. **Filter Node:** rating <= 2
4. **Slack Node:** Send alert to #feedback channel
5. **Airtable Node:** Add to "Negative Reviews" table

### Zapier Workflow

1. **Trigger:** Apify Actor Run Finished
2. **Filter:** Only new reviews
3. **Google Sheets:** Append row
4. **Email:** Send summary to product manager

### Make.com Workflow

1. **Trigger:** Webhook (from actor)
2. **Router:**

- Path A (rating 1-2): Create Zendesk ticket
- Path B (rating 4-5): Add to testimonials database
3. **HTTP:** Update dashboard API

## ❓ FAQ

### How do I get app IDs?

**Option 1:** Use full URL from Google Play:

```
https://play.google.com/store/apps/details?id=com.android.chrome
```

**Option 2:** Extract app ID from URL (everything after `?id=`):

```
com.android.chrome
```

### How does incremental scraping work?

Actor saves the last reviewId for each app. On next run, it only scrapes reviews newer than that reviewId. This saves time and cost.

### What's the rate limit?

Actor uses conservative 5 requests/second limit to avoid hitting Google Play's rate limits. This is built-in and automatic.

### Can I scrape multiple countries?

Set the `country` parameter to change regions. Run multiple times with different countries for comprehensive coverage.

### How do I filter for negative reviews only?

Set `minRating: 1` and `maxRating: 2` in input.

### Can I get only reviews with developer replies?

Set `hasReplyOnly: true` in input.

### How do I export to CSV?

In Apify Console, go to dataset → Export → CSV.

## 🐛 Troubleshooting

### No reviews returned

**Possible causes:**

1. App ID is incorrect (check format: `com.example.app`)
2. Filters too strict (check minRating, maxRating, minHelpfulCount)
3. App has no reviews in selected language/country

**Solution:** Start with minimal filters and verify app ID.

### Rate limiting errors (503)

**Cause:** Google Play rate limiting (rare with built-in throttling)

**Solution:** Actor automatically retries with exponential backoff. If persistent, contact support.

### Webhook not working

**Possible causes:**

1. Webhook URL is incorrect
2. Webhook endpoint is down
3. Webhook expects different format

**Solution:** Check webhook logs. Actor continues even if webhook fails.

## 📞 Support

- **Email:** via Apify
- **Issues:** Report bugs or request features via email

## 📄 License

MIT License - Free to use, modify, and distribute.

---

## 🔗 Explore More of Our Actors

### 📰 Content & Publishing

| Actor | Description |
| --- | --- |
| [Notion Marketplace Scraper](https://apify.com/webdatalabs/notion-marketplace-scraper) | Scrape Notion templates and marketplace listings |
| [Ghost Newsletter Scraper](https://apify.com/webdatalabs/ghost-newsletter-scraper) | Extract Ghost newsletter content and subscriber data |
| [Farcaster Hub Scraper](https://apify.com/webdatalabs/farcaster-hub-scraper) | Scrape Farcaster decentralized social network data |

### 🛒 E-commerce

| Actor | Description |
| --- | --- |
| [Shopify Scraper Pro](https://apify.com/webdatalabs/shopify-scraper-pro) | Extract complete Shopify product data with variants and sales estimates |
| [eBay Scraper (PPR)](https://apify.com/webdatalabs/ebay-scraper-pro) | Extract eBay products with seller analytics and engagement metrics |
| [Etsy Scraper Pro](https://apify.com/webdatalabs/etsy-scraper-pro) | Fast Etsy product scraper with ratings, reviews, and shop data |
| [Amazon Reviews Scraper](https://apify.com/webdatalabs/amazon-reviews-scraper) | Extract Amazon customer reviews for sentiment analysis |
| [Amazon Bestsellers Tracker](https://apify.com/webdatalabs/amazon-bestsellers-tracker) | Monitor Amazon bestseller rankings and track trending products |

---

---

**Built with ❤️ by WebDataLabs** | [More Apify Actors](https://apify.com/webdatalabs)

---

## 📬 Custom Solutions & Enterprise

Need a custom data feed, modified output format, or enterprise integration?

**Contact:** [Furkanc58@gmail.com](mailto:Furkanc58@gmail.com)

I offer:

- Daily/weekly data feeds (Snowflake, S3, BigQuery, Google Sheets)
- Custom scrapers for platforms not yet covered
- White-label solutions for agencies
- Priority support and SLAs

*Response within 24-48 hours.*

## Legal Disclaimer

This actor is a general-purpose tool for analyzing publicly accessible web data. The user bears sole responsibility for ensuring their specific use complies with:

- Applicable laws (GDPR/DSGVO, copyright law)
- The target website's Terms of Service
- Apify's Terms of Service

The provider (webdatalabs) expressly disclaims liability for any unauthorized or unlawful use. By using this actor, the user agrees to indemnify the provider against any third-party claims arising from their use of the data.

---

*This tool is not affiliated with Google. All trademarks belong to their respective owners.*