# Apple AppStore

## Introduction

**Apple AppStore API** provides apps information, reviews, developers info, and much more from Apple Store.

## Authentication

The URL you need to use is the following: `https://apple-appstore.p.rapidapi.com/`
The API requires the headers listed below:

- **`x-rapidapi-host`**: `apple-appstore.p.rapidapi.com`
- **`x-rapidapi-key`**: `YOUR_API_KEY`

Make sure to replace `YOUR_API_KEY` with your API key. You can register one [here](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/apple-appstore/pricing).
Some frameworks automatically add extra headers, you have to make sure to remove them in order to get a response from the API.

## Endpoints

The API is configured to accept only **GET** requests. Below are the available endpoints with their descriptions and required parameters.

### 1. **`GET /developer`**

- **Description**: Retrieves a list of applications by the given developer id.

| Parameter | Type   | Default     | Description                                               | Required |
|-----------|--------|-------------|-----------------------------------------------------------|----------|
| `devId`   | string | -           | The AppStore dev Id of the developer                      | Yes      |
| `lang`    | string | `undefined` | Language code for the result text                         | No       |
| `country` | string | -           | The two letter country code to get the app details from * | No       |

*: This also affects the language of the data.

Example request:

```javascript
fetch('https://apple-appstore.p.rapidapi.com/developer?devId=284882218', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'apple-appstore.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
[
  {
    "id": 454638411,
    "appId": "com.facebook.Messenger",
    "title": "Messenger",
    "url": "https://apps.apple.com/us/app/messenger/id454638411?uo=4",
    "description": "Messenger is a free messaging app that helps you connect with anyone, anywhere. Stay in touch with your friends and family, explore your interests with ...",
    "icon": "https://is1-ssl.mzstatic.com/image/thumb/Purple211/v4/f7/30/6b/f7306b04-4919-d74a-f178-af9d9a09c39f/AppIcon-0-0-1x_U007epad-0-1-0-sRGB-85-220.png/512x512bb.jpg",
    "genres": [
      "Social Networking",
      "Productivity"
    ],
    "genreIds": [
      "6005",
      "6007"
    ],
    "primaryGenre": "Social Networking",
    "primaryGenreId": 6005,
    "contentRating": "12+",
    "languages": [
      "HR",
      "CS",
      "DA",
      "NL",
      "EN",
      "FI",
      "FR",
      "DE",
      "EL",
      "HU",
      ...
```

### 2. **`GET /search`**

- **Description**: Retrieves a list of apps that results of searching by the given term.

| Parameter | Type    | Default | Description                                                                     | Required |
|-----------|---------|---------|---------------------------------------------------------------------------------|----------|
| `term`    | string  | -       | The term to search for                                                          | Yes      |
| `idsOnly` | boolean | `false` | Skip extra lookup request. Search results will contain array of application ids | No       |
| `lang`    | string  | `en-us` | Language code for the result text                                               | No       |
| `country` | string  | -       | The two letter country code to get the similar apps from                        | No       |
| `num`     | string  | `50`    | The amount of elements to retrieve                                              | No       |
| `page`    | string  | `1`     | The page of results to retrieve apps from                                       | No       |

Example request:

```javascript
fetch('https://apple-appstore.p.rapidapi.com/search?term=panda&num=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'apple-appstore.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
[
  {
    "id": 903990394,
    "appId": "com.pandarg.pxmobileapp",
    "title": "Panda Express",
    "url": "https://apps.apple.com/us/app/panda-express/id903990394?uo=4",
    "description": "Good Fortune Awaits with Panda Rewards and the Panda Express® App. Order your Panda favorites on the fly for dine-in, take out, or delivery. And you can ...",
    "genres": [
      "Food & Drink"
    ],
    "genreIds": [
      "6023"
    ],
    "primaryGenre": "Food & Drink",
    "primaryGenreId": 6023,
    "contentRating": "4+",
    "languages": [
      "EN"
    ],
    "size": "146292736",
    "requiredOsVersion": "12",
    "released": "2014-08-20T21:39:53Z",
    "updated": "2024-10-21T13:11:28Z",
    "releaseNotes": "More exclusive Panda Rewards updates including user experience improvements and minor bug fixes.\nAre you hungry? Order your Panda favorites through the ...",
    "version": "6.2.8",
    "price": 0,
    "currency": "USD",
    "free": true,
    "developerId": 903990397,
    ...
```

### 3. **`GET /suggest`**

- **Description**: Retrieves up to 50 suggestions to complete the provided term.

| Parameter | Type    | Default | Description                                                                     | Required |
|-----------|---------|---------|---------------------------------------------------------------------------------|----------|
| `term`    | string  | -       | The term to search for                                                          | Yes      |

Example request:

```javascript
fetch('https://apple-appstore.p.rapidapi.com/suggest?term=panda', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'apple-appstore.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "data": [
    {
      "term": "panda express"
    },
    {
      "term": "panda pop"
    },
    {
      "term": "panda"
    },
    {
      "term": "pandabuy"
    },
    {
      "term": "panda vpn"
    },
    {
      "term": "pandadoc"
    },
    {
      "term": "panda games"
    },
    {
      "term": "pandar"
    },
    {
      "term": "pandalive"
    },
    {
      ...
```

### 4. **`GET /privacy`**

- **Description**: Retrieves the ratings for the app. Currently only for US App Store.

| Parameter | Type    | Default | Description                                              | Required |
|-----------|---------|---------|----------------------------------------------------------|----------|
| `id`      | string  | -       | The AppStore "trackId" of the app                        | Yes      |

Example request:

```javascript
fetch('https://apple-appstore.p.rapidapi.com/privacy?id=324684580', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'apple-appstore.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "managePrivacyChoicesUrl": null,
  "privacyTypes": [
    {
      "privacyType": "Data Used to Track You",
      "identifier": "DATA_USED_TO_TRACK_YOU",
      "description": "The following data may be used to track you across apps and websites owned by other companies:",
      "dataCategories": [
        {
          "dataCategory": "Contact Info",
          "identifier": "CONTACT_INFO",
          "dataTypes": [
            "Email Address",
            "Phone Number"
          ]
        },
        {
          "dataCategory": "Identifiers",
          "identifier": "IDENTIFIERS",
          "dataTypes": [
            "User ID",
            "Device ID"
          ]
        },
        {
          "dataCategory": "Usage Data",
          "identifier": "USAGE_DATA",
          "dataTypes": [
            "Product Interaction",
            "Advertising Data"
            ...
```

### 5. **`GET /appinfo`**

- **Description**: Retrieves the full detail of an application.

| Parameter | Type    | Default     | Description                                                           | Required |
|-----------|---------|-------------|-----------------------------------------------------------------------|----------|
| `id`      | string  | -           | The AppStore "trackId" of the app                                     | Yes      |
| `lang`    | string  | `undefined` | Language code for the result text                                     | No       |
| `country` | string  | `us`        | The two letter country code to get the app details from *             | No       |
| `ratings` | string  | -           | Load additional ratings information like ratings number and histogram | No       |

*: This also affects the language of the data.

Example request:

```javascript
fetch('https://apple-appstore.p.rapidapi.com/appinfo?id=553834731', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'apple-appstore.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "id": 553834731,
  "appId": "com.midasplayer.apps.candycrushsaga",
  "title": "Candy Crush Saga",
  "url": "https://apps.apple.com/us/app/candy-crush-saga/id553834731?uo=4",
  "description": "Start playing Candy Crush Saga today – a legendary puzzle game loved by millions of players around the world.\n\nWith over a trillion levels played ...",
  "genres": [
    "Games",
    "Entertainment",
    "Puzzle",
    "Casual"
  ],
  "genreIds": [
    "6014",
    "6016",
    "7012",
    "7003"
  ],
  "primaryGenre": "Games",
  "primaryGenreId": 6014,
  "contentRating": "4+",
  "languages": [
    "AR",
    "CA",
    "HR",
    "CS",
    "DA",
    "NL",
    "EN",
    ...
```

### 6. **`GET /product/similar`**

- **Description**: Retrieves similar products to the one provided.

| Parameter   | Type    | Default     | Description                      | Required |
|-------------|---------|-------------|----------------------------------|----------|
| `productId` | string  | -           | The ID of the product            | Yes      |

Example request:

```javascript
fetch('https://macys4.p.rapidapi.com/api/product/similar?productId=14496474', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'apple-appstore.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "status": "sucess",
  "products": [
    [
      {
        "id": 17870999,
        "identifier": {
          "productUrl": "/shop/product/premier-comfort-cozy-plush-printed-wrap-50-x-70-exclusively-at-macys-a-30-value?ID=17870999",
          "productId": 17870999,
          "topLevelCategoryID": "7495",
          "topLevelCategoryName": "Bed & Bath"
        },
        "department": {
          "departmentId": 61,
          "departmentName": "MARKET DECORATIVE ACCESSORIES"
        },
        "messages": {
          "info": [
            {}
          ]
        },
        "detail": {
          "name": "Cozy Plush Printed Wrap, 50\" x 70\", Exclusively at Macy’s (A $30 value)",
          "description": "Snuggle in with the cozy feel of this Premier Comfort wrap, in ultra-soft plush with a fun print that makes warmth stylish.",
          "secondaryDescription": "",
          "seoKeywords": "Premier Comfort, Premier Comfort Cozy Plush Printed Wrap, 50\" x 70\", Exclusively at Macy’s (A $30 value)",
          "flags": {
            "chanel": false,
            "hermes": false,
            "coach": false,
            ...
```

## Error Handling

The  API returns standard HTTP status codes to indicate the success or failure of API requests. Below are common errors and suggestions for handling them.

|Status Code|Message|Description|Suggested Handling|
|--|--|--|--|
| **400** | Bad Request | The request was malformed or missing required parameters (e.g., `domain` parameter not provided). | Verify that all required parameters are included and correctly formatted. |
| **401** | Unauthorized | Invalid or missing API key in the request headers. | Check that a valid API key is included in `x-rapidapi-key`. |
| **403** | Forbidden | Access to the requested resource is denied, possibly due to rate limits or restricted access. | Review rate limits and ensure API permissions. Retry after a delay if rate limit exceeded. |
| **404** | Not Found | The requested domain information could not be found (e.g., domain does not exist). | Check the spelling or availability of the domain. |
| **429** | Too Many Requests | The API rate limit has been exceeded. | Implement rate-limiting logic and retry after the specified rate limit reset time. |
| **500** | Internal Server Error | A server error occurred while processing the request. | Retry the request after a few seconds. If the error persists, contact API support. |
| **503** | Service Unavailable | The API service is temporarily unavailable (e.g., due to maintenance). | Retry the request later or check the API status page for maintenance alerts. |
