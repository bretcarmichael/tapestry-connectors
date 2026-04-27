# tapestry-connectors
Includes two connectors for IconFactory's excellent Tapestry app:
* **Nitter:** Nitter lets you follow Twitter accounts inside of Tapestry. Visit a user's profile on Nitter, copy their RSS feed URL, and add it to Tapestry. When you want to visit the the actual post, you'll be navigated to the original post on Twitter. 
* **Trump's Truth:** Follow posts made by POTUS on Truth Social. No textra work necessary. Install the connector, and add the feed.

## Nitter Release Notes
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
## Version 1.1
* Initial release.
