# Event Metadata

Event metadata is available in it's raw form in `event_metadata.json`. This was pulled from https://handsoff2025.com/ on April 7, 2025 using the following command.

```
curl "https://mobilize-feed-cache.vercel.app/data.json?timeslot_start=gte_now&per_page=100&approval_status=APPROVED&is_virtual=false" > events.json
```

`event_metadata.tsv` is a view of a subset of the same data in tabular format.

This data contains listings for 1341 events with a small amount of duplication. Deduplicating events with identical venu names and addresses provides a total count of 1323 unique protest locations.

# Sources
https://www.reddit.com/r/Seattle/comments/1jt1e5s/an_aerial_picture_from_yesterdays_rally/
https://www.reddit.com/r/Seattle/comments/1jsnewo/hands_off_seattle/
https://www.reddit.com/r/Seattle/comments/1jt1h3v/an_aerial_video_from_yesterdays_rally/
https://www.reddit.com/r/Seattle/comments/1jsatay/right_now