# Focus Time

Focus time (the duration where something is visible in a user's viewport) is tracked on a per-section-element basis. When the user enters a section, the visible time of every text paragraph, figure and video elements get is recorded. The css selector used is

```javascript
content.querySelectorAll("h1, h2, p, img, video, iframe")
```

Every element is then assigned an integer id starting from zero with the being order the same as their order on the page.

The entire collection of all the visibility times of all elements in the section is sent to firebase at a 60s interval. The visibility data of an element looks like

```json
{
    // a combination of the element's type and the first 10 characters of its content nodeType--first10characters
    "id": "H1--Overview",
    // which subsection the element belongs to, e.g. the nearest previous h1 heading
    "subSection": "Overview",
    // timestamp of when the element becomes visible for the last time
    "lastViewStarted": 74143.5,
    // total view time during the 60s interval
    "totalViewTime": 27000,
    // if the element is visible at the time of sending
    "visible": false
},
```

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
            "id": "H1--Overview",
            "lastViewStarted": 2405.2999999523163,
            "subSection": "Overview",
            "totalViewTime": 0,
            "visible": false,
        },
        {
            "id": "P--Data is very importa",
            "lastViewStarted": 57660.5,
            "subSection": "Introduction to FRED",
            "totalViewTime": 1092.3999999761581,
            "visible": false
        },
        {
            "id": "video--",
            "lastViewStarted": 58910.799999952316,
            "subSection": "Why Study Economics?",
            "totalViewTime": 5719.100000023842
            "visible": false
        }
        // other elements on the page
        ...
    ]
}
```