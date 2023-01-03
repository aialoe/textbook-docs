# Identity Management

When a user first logs in he/she is required to input some identity data. Currently we only support logins via one's google account. Other methods will be added later, e.g., email-password, phone number or via other social providers.

## Sample data

User data is stored in two places, firebase's built-in user pool and firestore.

The user pool stores what is returned from the identity provider. For example, a user created via google login has

```json
{
    "uid": "APgf5SYmkkXu1d13fw25K4BxyRI3",
    "email": "lear.lab.vu@gmail.com",
    "emailVerified": true,
    "displayName": "Scott Crossley",
    "isAnonymous": false,
    "photoURL": "https://lh3.googleusercontent.com/a/ALm5wu2RrwzPQYe1IZYKGuwug6BmvBROfV3kmyAiCb77=s96-c",
    "providerData": [
        {
            "providerId": "google.com",
            "uid": "112168403617264073813",
            "displayName": "Scott Crossley",
            "email": "lear.lab.vu@gmail.com",
            "phoneNumber": null,
            "photoURL": "https://lh3.googleusercontent.com/a/AEdFTp7GuDRSryTEoiSFSw45MUubMB-3a87030KOfSxi=s96-c"
        }
    ],
    "stsTokenManager": {
        "refreshToken": "some token",
        "accessToken": "some token",
        "expirationTime": 1672719819067
    },
    "createdAt": "1666046663358",
    "lastLoginAt": "1672716219080",
    "apiKey": "some api key",
    "appName": "[DEFAULT]"
}
```

Firestore stores business-relevant user data.

```json
{
    "displayName": "jane doe",
    "email":  "jane@gmail.com",
    // the user's current progress submitting summaries, incremented everytime when the user submits a new successful
    "location": {
        "module": 1,
        "chapter": 1,
        "section": 4,
    },
    "photoURL": "https://lh3.googleusercontent.com/a/ALm5wu08JCkPL9PCJEEfQhuIfOr1kV4fS534NAc74jBC7Q=s96-c",
    // an array of sucessful summaries
    "summaries": []
}

```