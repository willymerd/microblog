# Belajar API Bettermode

Source GPT : https://chatgpt.com/share/2601c979-3e60-4e0a-b414-59831ac84b7a

langkah

1. Generate `Authorization` dengan Encode `clientId` dan `clientSecret` menjadi format Base64. menggunakan terminal

```graphql
echo -n "YOUR_CLIENT_ID:YOUR_CLIENT_SECRET" | base64
```

1. Tambahkan Header Autentikasi
Tambahkan header `Authorization` dengan nilai `Basic <encoded_credentials>`:

```graphql
{
  "Authorization": "Basic NjY1OWYxODUtYWM0Y2UyZDA5NWJkOjI0NzVmNGM1MGEzMjQzMjY4NjFkY2ExN2U4ZjJjNzg5"
}
```

1. Masukkan Query GraphQL
Masukkan query GraphQL untuk menghasilkan token akses

```graphql
query {
  limitedToken(
    context: NETWORK, 
    networkId: "0pvfvYjmJh", 
    entityId: "0pvfvYjmJh", 
    impersonateMemberId: "2oGvhsS4EF"
  ) {
    accessToken
  }
}
```

```json
{
  "data": {
    "limitedToken": {
      "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjJvR3Zoc1M0RUYiLCJleHRlcm5hbEFjdG9ySWQiOiJBUFA6OnlLOE5Rc2pVWk9VcSIsIm5ldHdvcmtJZCI6IjBwdmZ2WWptSmgiLCJ0b2tlblR5cGUiOiJMSU1JVEVEIiwiZW50aXR5SWQiOiIyb0d2aHNTNEVGIiwicGVybWlzc2lvbkNvbnRleHQiOiJNRU1CRVIiLCJwZXJtaXNzaW9ucyI6WyIqIl0sImlhdCI6MTcxNzYzMDMxMSwiZXhwIjoxNzIwMjIyMzExfQ.ovCMm-X1xfFXf-Ij6HV1oMg2gUZfLZ9xgz2ANLSfWw4"
    }
  },
  "extensions": {
    "complexity": 1
  }
}
```

1. Gunakan Token Akses yang Dihasilkan
    
    Salin `accessToken` dari respons. Hapus header sebelumnya di tab `HTTP HEADERS` dan tambahkan header baru:
    

```json
{
  "Authorization": "Bearer <accessToken>"
}
```