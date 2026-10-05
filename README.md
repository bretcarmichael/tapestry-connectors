# Tapestry Connectors
Includes four connectors for IconFactory's excellent Tapestry app:
* **FxTwitter:** Follow X accounts without an API key. Leverage FxTwitter's edge-hosted service to display X posts as a social media feed in Tapestry.
* **Narro.info:** Follow X accounts in Narro, and add the Narro-provided RSS feed to the Tapestry connector.
* **Nitter:** Nitter lets you follow Twitter accounts inside of Tapestry. Visit a user's profile on Nitter, copy their RSS feed URL, and add it to Tapestry. When you want to visit the the actual post, you'll be navigated to the original post on Twitter. 
* **Trump's Truth:** Follow posts made by POTUS on Truth Social. No textra work necessary. Install the connector, and add the feed.

## FxTwitter for Tapestry — v1.0

Follow public X (Twitter) accounts in [Tapestry](https://usetapestry.com) without an X login or API key. Posts are loaded through the free [FxTwitter API](https://docs.fxembed.com/api/introduction).

### Features

- **Follow any public account by handle.** Enter `NASA`, `@NASA`, or paste an `x.com` profile link. Pasting a profile link or handle into Tapestry's Feed Finder also suggests this connector.
- **Native post layout.** Posts look like Tapestry's Bluesky and Mastodon feeds, with profile photos, display names and handles.
- **Rich content.** Photos (with alt text), videos, GIFs, link previews, polls, quote posts, X Articles, and Community Notes.
- **Linked text.** @mentions, #hashtags, $cashtags, and URLs are tappable, with t.co links expanded.
- **Thread view.** Swipe a post to see its thread and replies.
- **Feed options:**
  - Include Reposts (on by default)
  - Include Quotes (on by default)
  - Include Threads, i.e. replies to self (on by default)
  - Include Replies to Others (off by default)
- **Survives handle changes.** Feeds track the account's permanent ID, so they keep working if the account renames itself.
- **Automatic retries.** FxTwitter occasionally returns a false "not found" error; the connector retries before reporting a problem.

### Installation

1. Download `fxtwitter.tapestry` from the assets below.
2. Save it to Files or iCloud Drive on your iPhone or iPad.
3. In Tapestry, go to **Settings → Connectors → Add a Connector** and select the file.
4. Create a feed with **X (Twitter) – Follow Account** and enter a handle.

To follow several accounts, create one feed per account and group them in a timeline.

### Known limitations

- **Public accounts only.** Protected and suspended accounts can't be followed.
- **Repost dates.** X doesn't report when something was reposted, so reposts are dated by the original post and may appear further down your timeline.
- **No X Lists.** The FxTwitter API doesn't expose list timelines.
- **Third-party dependency.** This connector relies on FxTwitter, a community service. If it goes offline or changes, the connector will stop loading until it's updated. The API address is a single `site` value in `plugin-config.json`, so it can be pointed at a self-hosted [FxEmbed](https://github.com/FxEmbed/FxEmbed) instance.

### Credits

- [FxEmbed](https://github.com/FxEmbed/FxEmbed) for the FxTwitter API
- [The Iconfactory](https://github.com/TheIconfactory/Tapestry) for Tapestry and its connector documentation

## Narro for Tapestry v1.0.0

The first public release of a [Tapestry](https://usetapestry.com) connector for [Narro](https://narro.info) RSS feeds. Add your Narro feed URL and your curated list of X accounts shows up in your Tapestry timeline looking like a Bluesky or Mastodon feed instead of a plain RSS list.

### Highlights

- **Social-style posts.** Each post shows the author's display name, their @handle and their profile picture. Line breaks are kept, and links, @mentions and #hashtags can be tapped.
- **Reposts.** A retweet shows the original author's post, with a "Reposted by …" label above it naming the account from your list.
- **Quote posts.** The quoted post appears as an embedded card under the post, with its author, avatar, text and media, much like Bluesky and Mastodon. Tapping the card opens the quoted post.
- **Photos and videos.** Every photo in a post is shown, not just the first, and videos and GIFs play inline. This applies to reposts and quote cards too.
- **Link cards only where they help.** Posts linking to an outside article or video (a news site, YouTube) get a preview card. Links that only point back to X's own photo or video pages don't.
- **Cleaner timeline.** Replies to other people are hidden. Threads, where an account replies to its own posts, are kept and labeled "Reply to …", showing only the new text rather than repeating the parent post.

### Requirements

- Tapestry 2.0 or later. The connector uses Tapestry's 2.0 connector API.
- A Narro feed URL, in the form `https://rss.narro.info/<your-feed-id>`.

### Installation

1. Download **Narro.tapestry** from the assets below.
2. Open it in Tapestry.
3. Paste your Narro RSS feed URL when prompted. Tapestry checks the feed and fills in its name.

### How it works

Narro's RSS feed supplies the list of posts, but it leaves out videos and many photos, and it only gives an @handle for reposted and quoted authors. To fill those gaps, the connector looks up each post on [FxTwitter](https://github.com/FxEmbed/FxEmbed) (`api.fxtwitter.com`), a free, open-source public service. FxTwitter returns the full media, real display names, profile pictures and quoted posts.

- **Caching.** Lookups are cached, so each post is fetched once. The first refresh after adding the feed is slower than later ones.
- **Storage.** The cache only holds posts still in the feed and stays under Tapestry's 100,000-character storage limit.
- **Fallback.** If FxTwitter can't be reached, the feed still loads from Narro's own data. In that case, videos and some photos won't appear, reposted and quoted authors show as @handles, and avatars come from [unavatar.io](https://unavatar.io).
- **Debug logging.** With debugging turned on for the feed in Tapestry, the log shows how many lookups succeeded and the first few errors.

## Nitter Release Notes
### Version 1.2
* **NEW:** Added support for XCancel and other Nitter instances.
### Version 1.1.1
* **NEW:** In addition to reposts, replies are also indicated as such.
### Version 1.1
* 🐞 **FIXED:** When an X post contains only text, the X post's Twitter Card is not longer embedded, duplicating the content and showing a closeup of the poster's X avatar.
* ✅ **IMPROVED:** Video embeds display more consistently.
* ✅ **NEW:** Reposts show "Reposted by @username" annotation.
* ✅ **NEW:** Reposts show the original author's name, handle and avatar (cached).
### Version 1.0
* Initial release.

## Trump's Truth Release Notes
## Version 1.1
* Inline video playback with thumbnail preview
* Image attachments (single and multi-image posts)
* Link preview cards with Open Graph data
* Re-Truth detection for both quote-inline and h-card RT formats
* Profile avatar embedded as base64 (bypasses CDN hotlink restrictions)
* Media URL caching for fast subsequent loads
* Empty media shard items correctly suppressed
* Purple default feed color
## Version 1.0
* Initial release.
