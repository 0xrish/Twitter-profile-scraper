# Twitter X Profile Scraper — Scrape X (Twitter) Profiles, Tweets & Media Without an API Key

> **Extract public X (Twitter) data at scale** — profiles, tweets, replies, media, and search results — with no API key, no authentication, and no rate-limit headaches. Built by [MikoLabs](https://mikolabs.xyz/) and available on [Apify](https://apify.com/).

[![Apify Actor](https://img.shields.io/badge/Apify-Actor-orange)](https://apify.com/) [![No API Key Required](https://img.shields.io/badge/API%20Key-Not%20Required-brightgreen)]() [![MikoLabs](https://img.shields.io/badge/Built%20by-MikoLabs-red)](https://mikolabs.xyz/)

---

## What Is the Twitter X Profile Scraper?

**Twitter X Profile Scraper** is an automation tool that lets you pull structured data from [X (Twitter)](https://x.com/) — profiles, tweets, replies, media, and keyword search results — without touching the official X API, its authentication flow, or its restrictive rate limits.

Just hand it a username, a profile URL, or a search term, and it auto-detects what you're after and returns clean, ready-to-use JSON in minutes.

### Key data points you can scrape

- **Profile information** — bio, follower/following counts, location, website, join date, avatar, and banner
- **Tweets and posts** — full text, timestamps, hashtags, mentions, links, and engagement metrics
- **Replies and threads** — full conversational context
- **Media content** — tweets containing images, videos, and GIFs
- **Retweets and quote tweets** — including original author metadata
- **Search results** — keyword search within a profile or across all of X

---

## Why Scrape X (Twitter) Data?

X has over 500 million monthly active users and remains one of the internet's richest real-time data sources. Common use cases include:

| Use Case | What It Helps You Do |
|---|---|
| **Brand monitoring** | Track mentions and sentiment in real time |
| **Competitive intelligence** | Analyze competitor tweets, engagement, and audience growth |
| **Influencer research** | Find influencers by engagement rate, followers, or niche |
| **Lead generation** | Spot prospects based on public activity |
| **Academic research** | Build datasets for social studies or NLP training |
| **Content strategy** | See what tweet formats drive the most engagement |
| **News & trend tracking** | Catch breaking news and viral content early |
| **Market sentiment** | Monitor crypto, stocks, and financial chatter |

---

## How to Scrape X (Twitter) — Step by Step

1. **Open the Actor** on Apify and click **Try for free**.
2. **Enter Twitter handles** (e.g. `elonmusk`, `apify`) or paste profile URLs.
3. **Configure your options** — replies, media-only, or profile info.
4. **Apply filters** (optional) — date range, engagement thresholds, content type, or search keywords.
5. **Click Run.**
6. **Download your data** from the Dataset tab once the run finishes.

The Actor automatically routes each request to the right scraping mode — no manual configuration required.

---

## Input Parameters

| Field | Type | Description |
|---|---|---|
| `twitterHandles` | `string[]` | Usernames to scrape (with or without `@`) |
| `twitterUrls` | `string[]` | Direct profile URLs (e.g. `https://x.com/elonmusk`) |
| `includeReplies` | `boolean` | Include reply tweets in results |
| `mediaOnly` | `boolean` | Scrape only tweets containing images or videos |
| `maxItems` | `integer` | Max tweets to collect (`0` = unlimited) |
| `searchTerms` | `string[]` | Keywords to search for within tweets |
| `startDate` | `string` | Filter tweets from this date (`YYYY-MM-DD`) |
| `endDate` | `string` | Filter tweets up to this date (`YYYY-MM-DD`) |
| `minLikes` | `integer` | Minimum likes threshold |
| `minReplies` | `integer` | Minimum replies threshold |
| `minRetweets` | `integer` | Minimum retweets threshold |
| `nsfwContent` | `boolean` | Enable NSFW/sensitive media (auto-routes through US/CA residential proxy) |
| `proxyConfiguration` | `object` | Proxy settings (auto-configured for NSFW mode) |

### Example input

```json
{
  "twitterHandles": ["elonmusk", "apify"],
  "includeReplies": false,
  "mediaOnly": false,
  "maxItems": 100,
  "searchTerms": ["AI research"],
  "startDate": "2024-01-01",
  "endDate": "2024-12-31",
  "minLikes": 50
}
```

---

## Output Format

Data is delivered as clean, structured JSON and can be exported as **JSON, CSV, Excel, XML, RSS, or an HTML table**.

### Profile output

```json
{
  "type": "profile",
  "username": "apify",
  "fullname": "Apify",
  "bio": "Web scraping and automation platform for data extraction",
  "followers": 12500,
  "following": 567,
  "tweets": 1234,
  "likes": 890,
  "avatar": "https://pbs.twimg.com/profile_images/...",
  "banner": "https://pbs.twimg.com/profile_banners/...",
  "website": "https://apify.com",
  "location": "San Francisco, CA",
  "joined": "January 2024",
  "scrape_date": "2024-10-24T12:00:00.000Z"
}
```

### Tweet output

```json
{
  "type": "tweet",
  "username": "@apify",
  "fullname": "Apify",
  "text": "Excited to announce our new scraping features!",
  "tweet_url": "https://x.com/apify/status/123456",
  "tweet_id": "123456",
  "date": "Oct 24, 2024 · 12:00 PM UTC",
  "hashtags": ["#webscraping", "#automation"],
  "mentions": ["@user1", "@user2"],
  "urls": ["https://example.com"],
  "stats": {
    "comments": 12,
    "retweets": 34,
    "quotes": 5,
    "likes": 156
  },
  "media": [
    {
      "type": "image",
      "url": "https://pbs.twimg.com/media/...",
      "thumbnail": "https://pbs.twimg.com/media/..."
    }
  ],
  "is_retweet": false,
  "is_reply": false,
  "is_quoted": false,
  "author": {
    "username": "@apify",
    "fullname": "Apify",
    "avatar": "https://pbs.twimg.com/...",
    "verified": true
  },
  "scrape_date": "2024-10-24T12:00:00.000Z"
}
```

---

## Data Field Reference

### Profile data

| Field | Type | Description |
|---|---|---|
| `type` | `string` | Always `"profile"` |
| `username` | `string` | Twitter handle |
| `fullname` | `string` | Display name |
| `bio` | `string` | Profile biography |
| `followers` | `integer` | Follower count |
| `following` | `integer` | Following count |
| `tweets` | `integer` | Total tweet count |
| `likes` | `integer` | Total likes given |
| `avatar` | `string` | Profile image URL |
| `banner` | `string` | Banner image URL |
| `website` | `string` | Profile website link |
| `location` | `string` | Profile location |
| `joined` | `string` | Account join date |
| `scrape_date` | `string` | ISO timestamp of when data was scraped |

### Tweet data

| Field | Type | Description |
|---|---|---|
| `type` | `string` | `"tweet"`, `"profile_search_tweet"`, etc. |
| `username` | `string` | Tweet author handle |
| `text` | `string` | Full tweet text |
| `tweet_url` | `string` | Direct link to tweet |
| `date` | `string` | Publication date |
| `hashtags` | `string[]` | Hashtags used |
| `mentions` | `string[]` | Users mentioned |
| `stats.likes` | `integer` | Like count |
| `stats.retweets` | `integer` | Retweet count |
| `stats.comments` | `integer` | Reply count |
| `stats.quotes` | `integer` | Quote tweet count |
| `media` | `object[]` | Attached images/videos |
| `is_retweet` | `boolean` | Whether it's a retweet |
| `is_reply` | `boolean` | Whether it's a reply |

---

## Free vs. Paid Plan Limits

| Feature | Free Tier | Paid Plan / Subscribed |
|---|---|---|
| Runs per Day | 5 free runs / day | Unlimited runs |
| Items per Target | 10 items / target | Unlimited (or custom limit) |
| Parallel Scraping | Standard | High Concurrency |
| Proxy Routing | Direct / Fallback | Residential Proxy (US / CA) |

> **Note:** Free users get up to 5 free runs per day and 10 items per target. For unlimited runs, high concurrency, and full-volume historical scraping, upgrade to an [Apify paid subscription](https://apify.com/pricing).

---

## How Much Does It Cost to Scrape X (Twitter)?

Apify gives you **$5 in free usage credits every month** on the [Apify Free plan](https://apify.com/pricing) — enough to scrape hundreds of tweets and profiles for testing or small projects.

For regular data needs, the **[$49/month Starter plan](https://apify.com/pricing)** is ideal for ongoing monitoring, competitive research, and medium-scale collection.

For enterprise-scale needs — thousands of profiles, millions of tweets — the **[Scale plan at $499/month](https://apify.com/pricing)** delivers the throughput required.

---

## Tips for Scraping X (Twitter) Effectively

- **Start small** — set `maxItems` to 20–50 on your first run to validate configuration before scaling.
- **Use engagement filters** — filter by `minLikes` or `minRetweets` to surface high-quality, viral content.
- **Combine include/exclude filters** — e.g., include media while excluding replies, for precise targeting.
- **Set date ranges** — always specify `startDate` and `endDate` for large collections to avoid over-scraping.
- **Enable residential proxies** — for the most reliable results at scale.
- **Let it run in parallel** — the Actor processes multiple handles simultaneously for faster results.
- **Rely on built-in retries** — failed requests are automatically retried with exponential backoff.

---

## Frequently Asked Questions

**Can I scrape private Twitter profiles?**
No. Twitter X Profile Scraper only works with public profiles — private or protected accounts cannot be scraped.

**Do I need a Twitter API key or account?**
No. This Actor requires no Twitter API credentials, cookies, or authentication, and works independently of the official Twitter API.

**What export formats are available?**
JSON, CSV, Excel (XLSX), XML, RSS, or an HTML table — all exportable directly from the Apify Console Dataset tab.

**How many tweets can I scrape?**
On paid plans, there's no hard cap — set `maxItems` to `0` for unlimited scraping. Free-tier users get up to 3 runs per day with up to 10 items per target.

**Can I search for specific keywords within a profile?**
Yes — use the `searchTerms` field to search within a profile's tweets, with support for AND/OR operators.

**Is it legal to scrape X (Twitter)?**
Personal data is protected under GDPR and similar regulations worldwide. Don't scrape personal data without a legitimate reason, and review [X's Terms of Service](https://twitter.com/en/tos) before scraping. Always scrape responsibly and avoid collecting sensitive personal information. For more, see [Is Web Scraping Legal?](https://blog.apify.com/is-web-scraping-legal/)

---

## Python Quick Start

```python
from apify_client import ApifyClient

# Initialize the ApifyClient with your Apify API token
client = ApifyClient("<YOUR_API_TOKEN>")

# Prepare the Actor input
run_input = {
    "twitterHandles": ["figma"],
    "maxItems": 20,
    "proxyConfiguration": {
        "useApifyProxy": True,
        "apifyProxyGroups": ["RESIDENTIAL"],
    },
}

# Run the Actor and wait for it to finish
run = client.actor("mikolabs/Twitter-X-Profile-Scraper").call(run_input=run_input)

# Fetch and print results
print(f"💾 Check your data here: https://console.apify.com/storage/datasets/{run.default_dataset_id}")
for item in client.dataset(run.default_dataset_id).iterate_items():
    print(item)

# Learn more: https://docs.apify.com/api/client/python/docs/quick-start
```

---

## Integrations

Twitter X Profile Scraper integrates seamlessly with **Make (Integromat), Zapier, Google Sheets, Slack**, and more via the Apify platform. Schedule recurring runs, configure webhooks, or pull results directly via the REST API.

- [Apify Documentation](https://docs.apify.com/)
- [Python SDK Documentation](https://docs.apify.com/sdk/python/)
- [Apify API Reference](https://docs.apify.com/api)
- [Integrations with Make, Zapier, and more](https://apify.com/integrations)

---

## Support & Feedback

Found a bug or have a feature request? Open an issue in the **Issues** tab on the Actor's page.

For custom scraping solutions or enterprise support, visit **[MikoLabs](https://mikolabs.xyz/)**.

---

*Built and maintained by [MikoLabs](https://mikolabs.xyz/) — automation and scraping tools for developers, marketers, and businesses.*
