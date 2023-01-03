# Focus Time

Focus time (the duration where something is visible in a user's viewport) is tracked on a per-element basis, this usually means that every text paragraph, figure and video elements get its own records.

If a user leaves the page, by switching to another tab or close the browser, the timer automatically pauses.

## Sample data

```json
{
    "uid": "APgf5SYmkkXu1d13fw25K4BxyRI3",
    "location": {
        "module": 1,
        "chapter": 1,
        "section": 3
    },
    // text content for the paragraph
    "text": "At times, such as when many people having trouble making ends meet, it is easy to tell how the economy is doing. This photograph shows people lined up during the Great Depression, waiting for relief checks. At other times, when some are doing well and others are not, it is more difficult to ascertain how the economy of a country is doing. ",
    // duration of visible time, in seconds
    "totalViewTime": 31,
    // last visible time, unix timestamp
    "lastVisibleTime": 1666125567096
}
```