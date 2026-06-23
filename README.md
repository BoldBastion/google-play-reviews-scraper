[Google Play Reviews Scraper](https://apify.com/benthepythondev/google-play-reviews-scraper?fpr=data)

# Google Play Store Reviews Scraper

Scrape customer reviews from **any Android app** on the Google Play Store. Extract ratings, review text, author information, developer replies, thumbs up counts, and more.

## Features

- **Multi-App Support**: Scrape reviews from multiple apps in one run
- **Multi-Country**: Get reviews from 50+ country Play Stores
- **Rich Data**: Ratings, full review text, author info, developer replies
- **Thumbs Up Counts**: See which reviews are most helpful
- **Filter by Rating**: Get only 1-star, 5-star, or any specific rating
- **Developer Replies**: Capture official app developer responses
- **Fast & Reliable**: Uses optimized scraping - no browser needed

## Use Cases

### App Store Optimization (ASO)

- Analyze review sentiment for your Android apps
- Track competitor review trends
- Identify common user complaints and feature requests

### Sentiment Analysis

- Build datasets for ML/NLP training
- Monitor brand perception over time
- Detect emerging issues early

### Competitor Research

- Compare review volume and ratings across competitors
- Analyze competitor weaknesses from negative reviews
- Track feature reception and user feedback

### Market Research

- Analyze app categories and niches
- Identify market gaps from user complaints
- Track industry trends

## Input Options

| Parameter | Type | Description |
| --- | --- | --- |
| `appIds` | array | Google Play package IDs (e.g., "com.twitter.android") |
| `appUrls` | array | Full Google Play Store URLs |
| `countries` | array | Country codes (e.g., "us", "gb", "de") |
| `language` | string | Review language (e.g., "en", "es", "de") |
| `maxReviews` | number | Max reviews per app/country (default: 500) |
| `sortBy` | string | "newest" or "most_relevant" |
| `filterRating` | number | Filter by star rating (1-5) |
| `delaySeconds` | number | Delay between requests (default: 0.5) |

### Finding App Package IDs

Package IDs can be found in Google Play URLs:

- `https://play.google.com/store/apps/details?id=com.twitter.android` - ID is `com.twitter.android`
- `https://play.google.com/store/apps/details?id=com.instagram.android` - ID is `com.instagram.android`

## Example Inputs

### Scrape Reviews for One App

```
{
  "appIds": ["com.twitter.android"],
  "countries": ["us"],
  "maxReviews": 500
}
```

### Scrape Multiple Apps

```
{
  "appIds": [
    "com.twitter.android",
    "com.instagram.android",
    "com.facebook.katana"
  ],
  "countries": ["us"],
  "maxReviews": 200
}
```

### Scrape from Multiple Countries

```
{
  "appIds": ["com.twitter.android"],
  "countries": ["us", "gb", "ca", "au", "de"],
  "maxReviews": 100
}
```

### Filter Only 1-Star Reviews

```
{
  "appIds": ["com.twitter.android"],
  "countries": ["us"],
  "filterRating": 1,
  "maxReviews": 500
}
```

### Using Google Play URLs

```
{
  "appUrls": [
    "https://play.google.com/store/apps/details?id=com.twitter.android",
    "https://play.google.com/store/apps/details?id=com.instagram.android"
  ],
  "countries": ["us"],
  "maxReviews": 300
}
```

## Output Format

Each review includes:

```
{
  "review_id": "gp:AOqpTOHxyz123...",
  "app_id": "com.twitter.android",
  "app_name": "X",
  "author_name": "John Smith",
  "author_image": "https://play-lh.googleusercontent.com/...",
  "rating": 4,
  "content": "Great app but the latest update has some bugs. The timeline doesn't load properly sometimes...",
  "thumbs_up_count": 142,
  "review_date": "2024-01-15T10:30:00",
  "reply_content": "Thanks for your feedback! We're working on fixing this issue.",
  "reply_date": "2024-01-16T14:22:00",
  "app_version": "10.15.2",
  "country": "US",
  "app_url": "https://play.google.com/store/apps/details?id=com.twitter.android"
}
```

## Supported Countries

50+ countries including: US, GB, CA, AU, DE, FR, ES, IT, JP, KR, BR, MX, IN, RU, NL, SE, and many more.

## Comparison: Google Play vs App Store

| Feature | Google Play Scraper | App Store Scraper |
| --- | --- | --- |
| Max Reviews | Unlimited (paginated) | ~500 per app |
| Developer Replies | Yes | No |
| Thumbs Up Count | Yes | Vote Count |
| Filter by Rating | Yes | No |
| Review Speed | ~200/request | ~50/page |

Use both scrapers together for complete cross-platform app intelligence!

## Limitations

- **Rate Limits**: Google may temporarily block requests if too fast. Use `delaySeconds` parameter.
- **Recent Reviews**: Very old reviews may not be available
- **Private Apps**: Enterprise/private apps are not accessible

## How It Works

This scraper uses the `google-play-scraper` library which interfaces with Google Play's internal APIs to fetch review data efficiently without browser automation.

## Pricing

$2.00 per 1,000 reviews scraped

## Tips

1. **Start Small**: Test with `maxReviews: 10` first
2. **Use Filters**: Filter by rating to focus on specific sentiment
3. **Multiple Countries**: Reviews vary significantly by region
4. **Combine Platforms**: Use with App Store Scraper for complete analysis

## Support

For issues or feature requests, contact the developer.