# Keystroke Logging

Keystroke logging is recorded at every key-press and key-release event when the user focuses on the summary text field. Each key-press and key-release forms a pair that is one row in a keystroke record, and all the keystrokes will be submitted in batch once a summary has been made, regardless of whether it has passed the test.

We also keep track of who (`uid`) and where (`module`, `chapter`, `section`) the keystrokes are submitted.

## Sample data

```json
{
    "uid": "hu8NH9M1aNRfWr5PJjOAA87qJF82",
    "location": {
        "module" : 1,
        "chapter": 1,
        "section": 1,
    },
    "keystrokes": [
        {
            "downKey": "v",
            "downTime": "15297.40000000596",
            "duration": 131.7000000178814,
            "eventId": 1,
            "upKey": "v",
            "upTime" 15429.100000023842
        }
    ]
}
```