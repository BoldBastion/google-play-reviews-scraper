[Google Play Reviews Scraper](https://apify.com/thewolves/google-play-reviews-scraper?fpr=data)

![](https://images.apifyusercontent.com/WvdegL_MfYkx_heA_ikPiZNOwdsD3JILkgX8qMTj0X4/w:1800/cb:1/aHR0cHM6Ly93d3cuZHJvcGJveC5jb20vc2NsL2ZpLzE5amVhZmdsMmI1dnZtczE5Y3ozbC9nb29nbGVwbGF5LXJldmlld3MuanBlZz9ybGtleT1xbXloNXMwbjhoamJna2d6Mngyb2N3djR0JmRsPTE.webp)

# 🥃 Google Play Reviews Scraper API: Extract Android App Reviews, Developer Replies & Feature Ratings at Scale

The **Google Play Reviews Scraper** by [The Wolves](https://apify.com/thewolves?fpr=yhdrb) is an Apify Actor that extracts user reviews, star ratings, developer replies, feature-specific quality ratings, app version data, reviewer profiles, and multi-language feedback from any Google Play Store listing. This **google play review scraper api** delivers 17 structured fields per review at speeds of **100-200 reviews per second** — with no proxy configuration required on your end.

**$0.10 per 1,000 reviews.** Extract Android app reviews from Google Play at scale. Target specific apps by package ID or URL, filter by country and language, sort by relevance or date, and collect reviews with developer replies and feature-specific criteria ratings that reveal exactly what users think about individual game mechanics or app features.

Built by **The Wolves** — a pack of data scientists with over a decade of experience in web scraping and API development. We build scrapers the way data teams actually need them: rich output, precise filtering, and pricing that scales.

> **Important:** Google Play allows users to rate apps with or without a comment. This scraper extracts **only reviews with comments** — ratings without text are not included. If the extracted count doesn't match the total rating count on Google Play, this is the reason.

**Pricing:** $0.10 per 1,000 reviews | **100-200 reviews/second** | **No proxy setup required**

---

## Table of Contents

1. What Does the Google Play Reviews Scraper Do?
2. Features and Capabilities
3. Pricing
4. Input Parameters
5. Output Format and Data Fields
6. Custom Map Function
7. AI Agent Integration via MCP
8. The Wolves Scraper Pack
9. Demo Mode and Free Testing
10. Automated Scheduling and Monitoring
11. Quick Start Guide
12. Use Cases and Industries
13. Troubleshooting
14. Frequently Asked Questions
15. Contact

---

## What Does the Google Play Reviews Scraper Do?

**Google Play review extraction** is the automated process of collecting user reviews, ratings, developer responses, and metadata from Android app listings on the Google Play Store. Google Play hosts over 3.5 million apps with billions of user reviews — making it the largest source of structured user feedback for Android applications and games.

The **Wolves Google Play Reviews Scraper** extracts structured review data that goes significantly deeper than basic text and ratings. Each review includes **developer replies** (when present), **feature-specific criteria ratings** (game genre, multiplayer quality, subject-specific scores), **thumbs-up counts**, and **multi-language support** — data points that are critical for Android app intelligence, game analytics, and cross-market analysis.

Unlike App Store reviews, Google Play reviews have **no hard per-country limit** on the number of reviews you can extract. Combined with language and sorting parameters, this gives you maximum flexibility in building comprehensive review datasets.

### What You Get From Every Review

**Review Content and Rating**

- Full review text and title
- Star rating (1-5) and score text
- Publication date (ISO 8601)
- Direct review URL on Google Play
- Thumbs-up count (community engagement)

**Developer Response**

- Developer reply text (when present)
- Developer reply date

**App and Version Context**

- App ID (package name, e.g., `com.instagram.android`)
- App version at time of review
- Country code
- Language code

**Feature-Specific Criteria Ratings**

- Array of criteria with individual ratings (e.g., game genre, multiplayer quality, subject-specific scores)

**Reviewer Profile**

- Reviewer name
- Reviewer avatar image URL

---

## Features and Capabilities

### Input Flexibility

| Input Type | Example | Best For |
| --- | --- | --- |
| **App ID + Country + Language** | `appIds: ["com.instagram.android"]`, `country: "us"`, `language: "en"` | Targeting specific apps in specific markets and languages |
| **Direct URL** | `https://play.google.com/store/apps/details?id=com.instagram.android` | Scraping from a Google Play listing URL |

### Core Capabilities

- **High-Speed Extraction** — 100-200 reviews per second
- **Triple Input Parameters** — App IDs with country and language codes, or paste direct Google Play URLs
- **Developer Replies** — Capture both the developer response text and reply date
- **Feature-Specific Criteria** — Extract quality ratings for specific game/app features (shooting, multiplayer, etc.)
- **Multi-Language Support** — Extract reviews in any language available on Google Play
- **Sort Options** — Sort by NEWEST, relevance, or other criteria
- **Global Coverage** — Extract reviews from any Google Play country locale
- **Thumbs-Up Count** — Community engagement metric per review
- **Reviewer Avatars** — User profile images included
- **No Proxy Required** — The scraper handles proxy rotation internally
- **Custom Map Function** — Transform output with custom JavaScript before saving
- **Multiple Export Formats** — JSON, CSV, Excel direct download
- **API Integration** — RESTful API for Python, Node.js, or any HTTP client

### Key Differences From App Store

- **No per-country review limit** — Unlike App Store's 500-review cap, Google Play has no hard limit
- **Developer replies included** — Full response text and date
- **Feature criteria ratings** — Granular quality scores for specific app/game features
- **Language parameter** — Separate from country, allowing precise linguistic targeting

---

## Pricing

### Pay-Per-Review Pricing

No subscriptions, no rentals, no minimum commitments. You pay only for the reviews you extract:

| Metric | Price |
| --- | --- |
| **Per 1,000 reviews** | $0.10 |
| **Per review** | $0.0001 |
| **Per 100,000 reviews** | $10.00 |

> **Example:** Extracting 5,000 reviews from a popular Android game costs **$0.50**. Monitoring reviews from your top 20 competitor apps monthly keeps costs well under **$5.00**.

---

## Input Parameters

| Field | Type | Description | Default |
| --- | --- | --- | --- |
| `appIds` | array | Google Play package IDs (e.g., `com.instagram.android`). Required if using `country` or `language` | `[]` |
| `country` | string | Google Play country code. Required if using `appIds` or `language` | `us` |
| `language` | string | Google Play language code. Required if using `appIds` or `country` | `en` |
| `sort` | string | Sort reviews by criteria | `NEWEST` |
| `startUrls` | array | Direct Google Play URLs — scraping begins immediately from these endpoints | `[]` |
| `maxItems` | number | Maximum number of reviews to output | `Infinity` |
| `customMapFunction` | string | JavaScript function to transform each review object (transformation only, not filtering) | `null` |

### Input Examples

**Single App — US English Reviews (Newest First):**

```
{
    "appIds": ["com.instagram.android"],
    "country": "us",
    "language": "en",
    "sort": "NEWEST",
    "maxItems": 1000
}
```

**Multiple Apps — Competitive Comparison:**

```
{
    "appIds": ["com.instagram.android", "com.twitter.android", "com.facebook.katana"],
    "country": "us",
    "language": "en",
    "maxItems": 1000
}
```

**Direct URL — No Package ID Needed:**

```
{
    "startUrls": [
        "https://play.google.com/store/apps/details?id=com.instagram.android&hl=en&gl=US"
    ],
    "maxItems": 1000
}
```

**Multi-Language — Same App, Different Languages:**
Run separate extractions for each language to build a multilingual dataset. For example, extract English reviews first, then French, then German — each run targets a different language code while keeping the same country.

---

## Output Format and Data Fields

Each extracted review is a structured JSON object containing 17 fields. Here is a sample:

```
{
    "id": "fcfcdecc-6270-4abe-9879-1e619549c8c8",
    "userName": "John Doe",
    "userImage": "https://play-lh.googleusercontent.com/a/ACg8ocJ5x-8yRBHpTKH4aEnumyflOawkGOI4vPrlLEp7FvWu=mo",
    "date": "2024-02-20T20:29:58.216Z",
    "score": 5,
    "scoreText": "5",
    "url": "https://play.google.com/store/apps/details?id=com.instagram.android&reviewId=fcfcdecc-6270-4abe-9879-1e619549c8c8",
    "title": "Amazing App and I love it",
    "text": "Perfect App",
    "replyDate": "2024-02-20T20:29:58.216Z",
    "replyText": "Thank you very much",
    "version": "318.0.0.30.110",
    "thumbsUp": 0,
    "criterias": [
        { "criteria": "vaf_games_genre_shooting", "rating": 1 },
        { "criteria": "vaf_games_massively_multi_player", "rating": 2 },
        { "criteria": "vaf_games_subject_bmx", "rating": 3 }
    ],
    "country": "FR",
    "appId": "com.instagram.android",
    "language": "tr"
}
```

### Complete Field Reference

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | Unique Google Play review identifier (UUID) |
| `userName` | string | Reviewer's display name |
| `userImage` | string | Reviewer's avatar image URL |
| `date` | string | ISO 8601 review publication date |
| `score` | number | Star rating (1-5) |
| `scoreText` | string | Rating as text string |
| `url` | string | Direct link to the review on Google Play |
| `title` | string | Review title (when provided) |
| `text` | string | Full review body text |
| `replyDate` | string | ISO 8601 date of developer reply (if exists) |
| `replyText` | string | Developer's response text (if exists) |
| `version` | string | App version the reviewer was using |
| `thumbsUp` | number | Number of thumbs-up votes from other users |
| `criterias` | array | Feature-specific quality ratings with criteria names and scores |
| `country` | string | Google Play country code |
| `appId` | string | Google Play package name (e.g., `com.instagram.android`) |
| `language` | string | Language code of the review |

### Data Fields by Use Case

| Use Case | Key Fields |
| --- | --- |
| **Android App Sentiment Analysis** | `text`, `title`, `score`, `date`, `language` |
| **Developer Response Tracking** | `replyText`, `replyDate`, `score`, `text`, `date` |
| **Game Feature Quality Analysis** | `criterias`, `score`, `text`, `version`, `appId` |
| **Release Impact Tracking** | `version`, `score`, `text`, `date`, `replyText` |
| **Competitive Benchmarking** | `appId`, `score`, `text`, `date`, `thumbsUp` |
| **Cross-Market Analysis** | `country`, `language`, `score`, `text`, `date` |
| **NLP Training Data** | `text`, `title`, `score` (as label), `language` |

### Developer Replies: Why They Matter

Developer replies are one of the most underutilized data points in app review analysis. The `replyText` and `replyDate` fields enable:

- **Support response rate calculation** — What percentage of negative reviews receive a developer response?
- **Response time analysis** — How quickly does the development team respond to user complaints?
- **Resolution tracking** — Do reviews that receive developer replies get updated to higher ratings?
- **Competitive support benchmarking** — Compare developer engagement across competing apps

---

## Custom Map Function

Transform each review before it's saved to the dataset. The `customMapFunction` parameter accepts a JavaScript function that reshapes every review object. Use this to flatten nested structures, extract specific criteria, or compute derived values.

**Important:** The custom map function is for **transformation only**, not filtering. Do not use it for filtering purposes.

### Example: Flatten for Sentiment Analysis

```
(review) => ({
    app: review.appId,
    rating: review.score,
    title: review.title,
    body: review.text,
    date: review.date,
    version: review.version,
    country: review.country,
    language: review.language,
    reviewer: review.userName,
    thumbsUp: review.thumbsUp,
    hasDevReply: !!review.replyText,
    devReply: review.replyText,
    devReplyDate: review.replyDate
})
```

### Example: Extract for Cross-Platform Comparison

```
(review) => ({
    platform: "Google Play",
    appId: review.appId,
    rating: review.score,
    text: review.text,
    title: review.title,
    date: review.date,
    country: review.country,
    reviewer: review.userName
})
```

### Example: Game Feature Analysis

```
(review) => ({
    game: review.appId,
    rating: review.score,
    text: review.text,
    version: review.version,
    featureRatings: review.criterias?.reduce((acc, c) => {
        acc[c.criteria] = c.rating;
        return acc;
    }, {})
})
```

---

## AI Agent Integration via MCP

Apify provides a hosted **Model Context Protocol (MCP) server** at `mcp.apify.com` that allows AI agents and LLM-based applications to discover and run Apify Actors as tools — including this Google Play Reviews Scraper.

### What This Means

If you're building AI agents using Claude Desktop, VS Code with MCP support, or any framework that implements the MCP specification, you can give your agent the ability to extract Google Play reviews autonomously. The agent can call this scraper as a tool, receive structured JSON results with developer replies and feature ratings, and use them in downstream analysis.

### How to Connect

Add this scraper to your MCP client configuration:

```
https://mcp.apify.com?tools=thewolves/google-play-reviews-scraper
```

Or use the CLI for local development:

```
$npx @apify/actors-mcp-server --tools thewolves/google-play-reviews-scraper
```

### Use Cases for AI Agent Integration

- **Automated app monitoring** — An AI agent extracts new reviews after each app update, summarizes sentiment trends by version, and flags critical bugs reported by users.
- **Cross-platform analysis** — Combine Google Play reviews with App Store reviews using the [App Store Reviews Scraper](https://apify.com/thewolves/appstore-reviews-scraper?fpr=yhdrb) in a single agent workflow for unified iOS + Android reporting.
- **Developer engagement analysis** — Extract reviews with developer replies, compute response rates and response times, and generate support quality reports automatically.

For full setup instructions, see the [Apify MCP documentation](https://docs.apify.com/platform/integrations/mcp).

---

## The Wolves Scraper Pack

All tools below are built and maintained by [The Wolves](https://apify.com/thewolves?fpr=yhdrb) — a pack of data scientists with over a decade of experience building high-performance scrapers and APIs. Powerful, easy to use, and priced for scale.

| Tool | Platform | Price | Best For |
| --- | --- | --- | --- |
| **Google Play Reviews Scraper** | Google Play | $0.10/1K reviews | Android app intelligence **(You are here)** |
| **[App Store Reviews Scraper](https://apify.com/thewolves/appstore-reviews-scraper?fpr=yhdrb)** | Apple App Store | $0.10/1K reviews | iOS app intelligence |
| **[TripAdvisor Reviews Scraper](https://apify.com/thewolves/tripadvisor-reviews-scraper?fpr=yhdrb)** | TripAdvisor | $0.50/1K reviews | Hospitality intelligence |
| **[Trustpilot Reviews Scraper](https://apify.com/thewolves/trustpilot-reviews-scraper?fpr=yhdrb)** | Trustpilot | $0.50/1K reviews | B2B/SaaS reputation analysis |

### Google Play Reviews vs. App Store Reviews

| Feature | Google Play (This Tool) | App Store |
| --- | --- | --- |
| **Platform** | Android | iOS / macOS |
| **Developer replies** | Yes (`replyText` + `replyDate`) | No |
| **Feature criteria ratings** | Yes (`criterias` array) | No |
| **Language parameter** | Separate from country | Not available |
| **Sort options** | NEWEST and others | Not available |
| **Review limit per country** | No hard limit | 500 (Apple limitation) |
| **Thumbs-up count** | Yes | No |
| **Reviewer avatar** | Yes (`userImage`) | No |
| **Speed** | 100-200 reviews/second | 100-200 reviews/second |

---

## Demo Mode and Free Testing

Free plan users can test this **Google Play reviews scraper** in Demo Mode with a maximum of **10 items** per run. Demo Mode is designed to validate the output format, data quality, and field coverage before committing to larger runs.

**Demo Mode Limitations:**

- Maximum 10 reviews per run
- API access not available on Free plan
- Full functionality requires a [paid Apify plan](https://apify.com/pricing?fpr=yhdrb)

**How to Test:**

- Run the scraper with `maxItems: 10` to preview the output structure
- Verify that developer replies, criteria ratings, and language codes are present
- Test with both `appIds` + `country` + `language` and `startUrls` input methods
- Confirm the `customMapFunction` works with your transformation logic

---

## Automated Scheduling and Monitoring

App reviews on Google Play appear continuously. For **app publishers**, **game studios**, and **product managers**, automated recurring runs ensure you capture new user feedback as it's posted.

### Why Schedule Review Extraction?

- **Release monitoring** — Track user sentiment after each app update by comparing reviews before and after version changes
- **Developer response tracking** — Monitor whether your team is responding to negative reviews and measure response times
- **Competitor tracking** — Monitor competitor Android app reviews weekly for feature gaps and user complaints
- **Rating trend analysis** — Detect rating drops before they impact Google Play ranking
- **Multi-language monitoring** — Track reviews in different languages to catch localization issues

### How to Set Up Scheduled Runs

1. Open the Actor in Apify Console
2. Configure your input parameters (appIds, country, language, sort, maxItems)
3. Click **Schedule** and set frequency (daily, weekly, after each release)
4. Optionally add a **webhook** to push new data to your pipeline

### Webhook Integration

Combine scheduled runs with webhooks to build fully automated review monitoring:

```
Scheduled Run -> New Reviews Extracted -> Webhook fires -> Your system receives data
```

Use webhooks to trigger:

- Slack alerts for 1-star reviews mentioning crashes or bugs
- Database updates with new review and developer reply data
- Dashboard refreshes with latest sentiment and criteria metrics
- Jira ticket creation for critical user-reported issues

---

## Quick Start Guide

### For Non-Technical Users (Apify Console)

1. Go to **[Google Play Reviews Scraper](https://apify.com/thewolves/google-play-reviews-scraper?fpr=yhdrb)** on Apify
2. Click **Try for free**
3. Enter an App ID (e.g., `com.instagram.android`) in the `appIds` field
4. Set `country`, `language`, and `maxItems`
5. Click **Start** and wait for results
6. **Export Google Play reviews to CSV** from the Storage tab

### For Developers (Python API)

```
from apify_client import ApifyClient
client = ApifyClient("YOUR_TOKEN")
run = client.actor("thewolves/google-play-reviews-scraper").call(run_input={
    "appIds": ["com.instagram.android"],
    "country": "us",
    "language": "en",
    "sort": "NEWEST",
    "maxItems": 1000
})
items = client.dataset(run["defaultDatasetId"]).list_items().items
```

### For Game Studios (Competitor + Feature Analysis)

```
{
    "appIds": ["YOUR_GAME_ID", "COMPETITOR_1_ID", "COMPETITOR_2_ID"],
    "country": "us",
    "language": "en",
    "maxItems": 2000
}
```

> Extract thousands of reviews from each game in a single run. The `criterias` array in the output provides feature-specific quality ratings — ideal for understanding which game mechanics players love or hate across your title and competitors.

### For Cross-Platform Analysis (Android + iOS)

Run this scraper for Google Play reviews, then run the [App Store Reviews Scraper](https://apify.com/thewolves/appstore-reviews-scraper?fpr=yhdrb) for the same app on iOS. Use matching `customMapFunction` outputs to normalize fields across platforms:

```
(review) => ({
    platform: "Google Play",
    rating: review.score,
    text: review.text || review.title,
    date: review.date,
    country: review.country,
    appId: review.appId,
    hasDevReply: !!review.replyText
})
```

---

## Use Cases and Industries

### Android App Sentiment Analysis and NLP

Extract thousands of Google Play reviews with full text, titles, star ratings, and language codes for training sentiment classifiers, topic modeling, or aspect-based sentiment analysis. The `language` field enables language-specific model training, while the `criterias` array provides feature-level sentiment data that goes beyond overall ratings.

**Key fields:** `text`, `title`, `score`, `date`, `language`, `criterias`

### Developer Response and Support Quality Analysis

The `replyText` and `replyDate` fields are unique to Google Play — App Store reviews don't include developer replies. Track your team's response rate to negative reviews, measure average response time, and analyze whether developer engagement correlates with improved ratings over time. Compare developer responsiveness across competitors.

**Key fields:** `replyText`, `replyDate`, `score`, `text`, `date`, `appId`

### Game Publishing and Feature Quality Tracking

The `criterias` array contains feature-specific quality ratings that are unique to Google Play game reviews. These granular scores (shooting quality, multiplayer experience, subject-specific ratings) provide actionable data for game designers and producers — revealing which mechanics players value and which need improvement, version by version.

**Key fields:** `criterias`, `score`, `text`, `version`, `date`, `appId`

### Product Management and Release Impact

Feed review data into product analytics to identify the most-requested features and most-reported bugs. The `version` field enables release-by-release tracking — measure whether a bug fix actually reduced 1-star reviews, or whether a new feature generated positive sentiment. Developer replies show how your team is responding to feedback.

**Key fields:** `text`, `score`, `version`, `date`, `replyText`, `thumbsUp`

### Cross-Platform App Intelligence

Compare user sentiment between Android (Google Play) and iOS (App Store) for the same app. Identify platform-specific issues, feature gaps, and satisfaction differences. Google Play's additional data — developer replies, criteria ratings, and language codes — provides richer analysis on the Android side.

**Key fields:** `appId`, `score`, `text`, `date`, `country`, `language`

### Multi-Language and Multi-Market Research

Google Play's separate `country` and `language` parameters enable precise linguistic targeting. Extract French-language reviews from the French market, then compare with French-language reviews from the Canadian market — or analyze how sentiment differs between English and Spanish reviews for the same app in the US.

**Key fields:** `country`, `language`, `score`, `text`, `date`, `appId`

---

## Troubleshooting

### Common Issues and Solutions

| Issue | Cause | Solution |
| --- | --- | --- |
| **Fewer reviews than expected** | Google Play only shows reviews with comments | Ratings without text are excluded — this is expected behavior |
| **Getting more results than requested** | High-speed extraction overshoots slightly | You are billed only for the number you requested, not the extra results delivered |
| **Missing data in output** | Results stored in Apify dataset | Navigate to the "Storage" tab and select "Download the results" or "Open in a New Tab" |
| **Empty results** | Invalid package ID format | Ensure you're using the package name (e.g., `com.instagram.android`), not the app name |
| **No developer replies** | Not all reviews receive developer responses | The `replyText` field is `null` when no developer reply exists — this is accurate data |
| **Empty criterias array** | Not all apps have feature criteria | The `criterias` array is populated mainly for games with feature-specific quality ratings |

### Performance Tips

- **Start small:** Test with `maxItems: 10` (Demo Mode) to validate your setup before scaling
- **Use all three input parameters:** `appIds` + `country` + `language` for the most targeted extraction
- **Sort strategically:** Use `NEWEST` for monitoring, or other sort options for relevance-based analysis
- **Multiple apps in one run:** Provide multiple package IDs in the `appIds` array for competitive analysis
- **Monitor billing:** You are billed per review extracted — if fewer reviews with comments exist, you pay only for what's delivered

---

## Frequently Asked Questions

### What Google Play review data can I extract?

Extract **review text**, **titles**, **star ratings (1-5)**, **review dates**, **reviewer names**, **reviewer avatars**, **developer reply text and dates**, **app version at review time**, **thumbs-up counts**, **feature-specific criteria ratings**, **country codes**, **language codes**, **package IDs**, and **direct review URLs** — all in structured JSON or CSV format.

### Can I export Google Play reviews to CSV?

Yes. **Download Google Play reviews** directly from Apify Console in JSON, CSV, or Excel format. Use the `customMapFunction` to flatten nested objects (like `criterias` and developer replies) into a single-row-per-review format ideal for spreadsheets.

### Why are fewer reviews extracted than the total shown on Google Play?

Google Play allows users to leave **ratings without comments**. This scraper extracts only **reviews with text comments**. The total rating count on a Google Play listing includes both ratings-only and text reviews — so the extracted count will be lower than the displayed total.

### Does this extract developer replies?

Yes. The `replyText` field contains the full developer response, and `replyDate` contains when the developer replied. These fields are `null` when no developer reply exists. This is one of the key advantages over App Store review extraction.

### What are the criteria ratings?

The `criterias` array contains feature-specific quality ratings that Google Play collects for certain apps (primarily games). Each entry has a `criteria` name (e.g., `vaf_games_genre_shooting`, `vaf_games_massively_multi_player`) and a `rating` value. Not all apps have criteria — the array may be empty for non-game apps.

### Can I scrape reviews from multiple apps at once?

Yes. Provide multiple package IDs in the `appIds` array (e.g., `["com.instagram.android", "com.twitter.android"]`). Each app's reviews are extracted within a single Actor run, with the `appId` field identifying which app each review belongs to.

### Is there a per-country review limit like App Store?

No. Unlike the App Store's 500-review-per-country limitation, Google Play has **no hard per-country limit** on the number of reviews you can extract. You can collect thousands of reviews per app depending on availability.

### Can I use Python to scrape Google Play reviews?

Yes. Full Python support via the Apify Client library. See the Quick Start Guide for Python integration with `client.actor("thewolves/google-play-reviews-scraper")`.

### Can AI agents use this scraper?

Yes. Through Apify's **Model Context Protocol (MCP) server**, AI agents built with Claude Desktop, VS Code, or any MCP-compatible framework can call this scraper as a tool. This enables automated app monitoring, cross-platform analysis, and multi-step research pipelines. See AI Agent Integration via MCP for setup details.

### How fast is the extraction?

**100-200 reviews per second**, depending on the app listing and Google Play's response times. This scraper is optimized for maximum throughput with internal proxy management.

### Do I need to set up proxies?

No. This scraper handles all proxy rotation internally. You don't need to configure, purchase, or manage any proxy infrastructure.

### How is this different from the App Store Reviews Scraper?

The **Google Play Reviews Scraper** extracts Android reviews with **developer replies**, **feature-specific criteria ratings**, **thumbs-up counts**, **reviewer avatars**, **language codes**, and **sort options** — none of which are available from the App Store. Google Play also has **no per-country review limit**. The [App Store Reviews Scraper](https://apify.com/thewolves/appstore-reviews-scraper?fpr=yhdrb) extracts iOS reviews with review titles and parent review IDs. Use both for cross-platform app intelligence.

---

## Contact

**Built by [The Wolves](https://apify.com/thewolves?fpr=yhdrb)** — a pack of data scientists with over a decade of experience building scrapers and APIs. We build them powerful, we build them fast, and we price them fair.

For questions, feature requests, or support:

- **Discord:** Reach out to [Tommy the Wolf](https://discordapp.com/users/tommy_the_wolf) — always available

---

**Ready to extract Google Play review data at scale?** At $0.10 per 1,000 reviews with 100-200 reviews/second, developer reply tracking, feature-specific criteria ratings, multi-language support, and no per-country limits, this **Google Play Reviews Scraper API** by [The Wolves](https://apify.com/thewolves?fpr=yhdrb) delivers the deepest Android app review data on the market. Start scraping today.