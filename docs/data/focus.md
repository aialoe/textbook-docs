# Focus Time

Focus time (the duration where something is visible in a user's viewport) is tracked on a per-element basis, this usually means that every text paragraph, figure and video elements get its own records. The css selector used is

```
content.querySelectorAll("h1, h2, p, img, video")
```

Every element is then assigned an integer id starting from zero with the being order the same as their order on the page.

If a user leaves the page, by switching to another tab or close the browser, the timer automatically pauses.

## Sample data

```json
{
    "uid": "APgf5SYmkkXu1d13fw25K4BxyRI3",
    "startTime": "January 13, 2023 at 11:13:19 AM UTC-6",
    "endTime": "January 13, 2023 at 11:13:49 AM UTC-6",
    "location": {
        "module": 1,
        "chapter": 1,
        "section": 3
    },
    "elements": [
        {
            "id": 0,
            "lastViewStarted": 74143.5,
            "totalViewTime": 27000,
        },
        {
            "id": 1,
            "lastViewStarted": 107142.29999999702,
            "totalViewTime": 29286.59999999404
        },
        // other elements on the page
        ...
    ]
}
```