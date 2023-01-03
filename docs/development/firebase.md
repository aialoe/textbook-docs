# Connecting to Firebase



## Python

Install the `firebase_admin` library and download the firebase credentials at <https://console.firebase.google.com/u/0/project/textbook-demo/settings/serviceaccounts/adminsdk>

```python
import firebase_admin
from firebase_admin import credentials

cred = credentials.Certificate("path/to/serviceAccountKey.json")
firebase_admin.initialize_app(cred)
```