# Getting a free YouTube Data API v3 key

Needed for Phase 1 (search) and, separately, Phase 5 will need OAuth2
credentials for uploading — that's a different setup, covered when we get
there. This key is just for searching/reading public video data. Free,
no credit card, ~5 minutes.

1. Go to [console.cloud.google.com](https://console.cloud.google.com) and
   sign in with your Google account. Create a new project (or reuse one) —
   top-left project dropdown → "New Project".
2. Go to **APIs & Services → Library**, search for **"YouTube Data API v3"**,
   open it, click **Enable**.
3. Go to **APIs & Services → Credentials → Create Credentials → API key**.
4. Copy the key that's generated.
5. Click **Edit API key** on the key you just made, and under
   **API restrictions** choose **Restrict key** → select **YouTube Data API
   v3** only. This means the key is useless for anything else if it ever
   leaks. Save.
6. Paste it into `config/.env` (copy from `config/.env.example` first if
   you haven't already):
   ```
   YOUTUBE_API_KEY=your_key_here
   ```

## Quota, for context

Free tier is 10,000 units/day. Search costs 100 units/call, `videos.list`
costs 1 unit/call — Phase 1's daily discovery run costs well under 1,000
units. The expensive operation is uploading (1,600 units each, Phase 5) —
that's the ~6 uploads/day ceiling referenced in the project brief, not
something Phase 1 will bump into.

## When you have the key

Tell me and I'll run a real (small) Phase 1 search + download against it to
close out CHECKPOINT 1 — separate from the mocked unit tests already
passing on the discovery/filtering logic itself.

Source: [YouTube Data API — Getting Started](https://developers.google.com/youtube/v3/getting-started)
