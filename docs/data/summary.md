# Summary

A summary record contains its text content alongside its score. Summary is sent to firestore once a summary has been made and passes the requirement for the minimum number of words and language detection, regardless of whether it passes the quality check.

Physically the summaries are stored as an array of the `users` collection.

```json
{
    // other user attributes
    ...,
    "summaries": [
        {
            "location": {
                "module": 1,
                "chapter": 1,
                "section": 1
            },
            "text": "sample text that is English and more than 50 words",
            // unix timestamp
            "timestamp": 1666125567096
        }
    ]
}
```