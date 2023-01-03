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
        "refreshToken": "AOkPPWQoyuLaTbNUfDxfGq5eShlCxRYPYdjbGQSLXR0OT3ZKRADjRb5J6QQnbiEQvskvSdBXqQWczMDFKznBjLH1-Jjmvf_hn_KihfPm7lL3gVn9sbzO9Y0ngtb5-B4oi66cA8zfjweIPqsvh-vozlWwjYrRAaZuA8tzopQmTpA3L5QfmBOTVozajLwSPzjnXfAiYr9UQuys5xQYQ75oEeZofb9DOYxcVghHH9OV_D4zgT8oeKymZZDRf_gU01ePLtbA9bTeFu29WOqhIjC2djc29-ctORpHia00j1rKmbgadBbwoBKdiCg5e--NQxil5aJ84vWtVS0DjGEP3gVTbXRkZWzK6gMl7kcmbHXr7esZ5Sen0vVSzsL-FVQBw40wJDvkWsSf9i53k6XjVe0KNC77-qeIAt4ms3IoxM3teIn8HLclpyVEAH4",
        "accessToken": "eyJhbGciOiJSUzI1NiIsImtpZCI6ImNlOWI4ODBmODE4MmRkYTU1N2Y3YzcwZTIwZTRlMzcwZTNkMTI3NDciLCJ0eXAiOiJKV1QifQ.eyJuYW1lIjoiU2NvdHQgQ3Jvc3NsZXkiLCJwaWN0dXJlIjoiaHR0cHM6Ly9saDMuZ29vZ2xldXNlcmNvbnRlbnQuY29tL2EvQUxtNXd1MlJyd3pQUVllMUlaWUtHdXd1ZzZCbXZCUk9mVjNrbXlBaUNiNzc9czk2LWMiLCJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vdGV4dGJvb2stZGVtbyIsImF1ZCI6InRleHRib29rLWRlbW8iLCJhdXRoX3RpbWUiOjE2NzI3MTYyMTksInVzZXJfaWQiOiJBUGdmNVNZbWtrWHUxZDEzZncyNUs0Qnh5UkkzIiwic3ViIjoiQVBnZjVTWW1ra1h1MWQxM2Z3MjVLNEJ4eVJJMyIsImlhdCI6MTY3MjcxNjIxOSwiZXhwIjoxNjcyNzE5ODE5LCJlbWFpbCI6ImxlYXIubGFiLnZ1QGdtYWlsLmNvbSIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7Imdvb2dsZS5jb20iOlsiMTEyMTY4NDAzNjE3MjY0MDczODEzIl0sImVtYWlsIjpbImxlYXIubGFiLnZ1QGdtYWlsLmNvbSJdfSwic2lnbl9pbl9wcm92aWRlciI6Imdvb2dsZS5jb20ifX0.OODTjOHFpJKBkaYoZIQ70xUqNjbzbM92dKTubKO92Q9nEaobi00UpmU83mGiCtudMIVcxHum8R8P0QOQ--Ku7sja0OGOJkWKCptdAe-oAeb1VHKzMgoY-AdxzJu1pfURje4EFWuZqorZom_5348iXm9nfMg9VjWDNkXsv5t1aRq-XjEu78sdbAQ6QP2Uf4-iNGcB8OGmeEy-kCtHv_rgwpWslygSgtpSAUbzys6c7UqyFonYfBMukGZg2mcxLCyYLY6ia9OTc087C9awSGOND4SiiduzMr-y6-c5OE8TVwDodgoq59jRsKemucVgG_BDLUVqytan2W_s65wSkPSqzw",
        "expirationTime": 1672719819067
    },
    "createdAt": "1666046663358",
    "lastLoginAt": "1672716219080",
    "apiKey": "AIzaSyCxm4tGe2XL1OKx0x4CL8fbAzjU8eUuCd4",
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