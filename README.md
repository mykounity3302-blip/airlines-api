# Airlines API

REST API for airline information including IATA/ICAO codes, fleet data, and home airports. Search 1,000+ airlines worldwide.

## Features

- Search by airline name, IATA code, or ICAO code
- Returns fleet breakdown by aircraft type
- Covers 1,000+ airlines globally
- 5,000 requests/month on free tier
- Example Response:
```json
{
  "name": "Southwest Airlines",
  "country": "United States",
  "founded_year": "1967",
  "home_airport": "Orlando International Airport",
  "iata_code": "WN",
  "icao_code": "SWA",
  "fleet": {
    "B737": 459,
    "B738": 207,
    "B38M": 94,
    "total_count": 770
  }
}
```

## Authentication

1. Create account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up)

![Sign Up](https://raw.githubusercontent.com/omkarcloud/assets/master/images/signup.png)

2. Get API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key)

![Copy API Key](https://raw.githubusercontent.com/omkarcloud/assets/master/images/enrichment-key-omkar.png)

3. Include `API-Key` header in requests

## Quick Start

```bash
curl -X GET "https://airlines-api.omkar.cloud/airlines?name=Southwest" \
  -H "API-Key: YOUR_API_KEY"
```

```json
{
  "name": "Southwest Airlines",
  "country": "United States",
  "founded_year": "1967",
  "home_airport": "Orlando International Airport",
  "iata_code": "WN",
  "icao_code": "SWA",
  "fleet": {
    "B737": 459,
    "B738": 207,
    "B38M": 94,
    "total_count": 770
  }
}
```

## Installation

### Python

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://airlines-api.omkar.cloud/airlines",
    params={"name": "Southwest"},
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()[0]
print(f"Airline: {data['name']}, Fleet Size: {data['fleet']['total_count']}")
```

### Node.js

```bash
npm install axios
```

```javascript
import axios from "axios";

const response = await axios.get("https://airlines-api.omkar.cloud/airlines", {
    params: { name: "Southwest" },
    headers: { "API-Key": "YOUR_API_KEY" }
});

console.log(`Airline: ${response.data[0].name}`);
```

## API Reference

### Endpoint

```
GET https://airlines-api.omkar.cloud/airlines
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `API-Key` | Yes | API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key) |

### Parameters

At least one parameter is required.

| Parameter | Required | Description |
|-----------|----------|-------------|
| `name` | No | Airline name (supports partial match, e.g., "Delta") |
| `iata` | No | 2-character IATA code (e.g., "WN") |
| `icao` | No | 3-character ICAO code (e.g., "SWA") |

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Airline name |
| `country` | string | Country of origin |
| `founded_year` | string | Year airline was founded |
| `home_airport` | string | Main hub airport |
| `iata_code` | string | 2-character IATA code |
| `icao_code` | string | 3-character ICAO code |
| `fleet` | object | Aircraft types with counts |

Fleet object contains aircraft codes (B737, A320, etc.) with counts and `total_count` for fleet size.

### Common Aircraft Codes

| Code | Aircraft |
|------|----------|
| B737 | Boeing 737 |
| B738 | Boeing 737-800 |
| B38M | Boeing 737 MAX 8 |
| A320 | Airbus A320 |
| A321 | Airbus A321 |
| B787 | Boeing 787 Dreamliner |

## Examples

### Search by airline name

```python
response = requests.get(
    "https://airlines-api.omkar.cloud/airlines",
    params={"name": "Delta"},
    headers={"API-Key": "YOUR_API_KEY"}
)

airline = response.json()[0]
print(f"{airline['name']} - Fleet: {airline['fleet']['total_count']} aircraft")
```

### Search by IATA code

```python
response = requests.get(
    "https://airlines-api.omkar.cloud/airlines",
    params={"iata": "UA"},
    headers={"API-Key": "YOUR_API_KEY"}
)

airline = response.json()[0]
print(f"{airline['name']} ({airline['icao_code']})")
```

### Search by ICAO code

```python
response = requests.get(
    "https://airlines-api.omkar.cloud/airlines",
    params={"icao": "AAL"},
    headers={"API-Key": "YOUR_API_KEY"}
)

airline = response.json()[0]
print(f"Home Airport: {airline['home_airport']}")
```

## Error Handling

```python
response = requests.get(
    "https://airlines-api.omkar.cloud/airlines",
    params={"name": "Southwest"},
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 5,000 |
| Starter | $25 | 100,000 |
| Grow | $75 | 1,000,000 |
| Scale | $150 | 10,000,000 |

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Airlines API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Airlines%20API.)

[![Contact Us on Email about Airlines API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Airlines%20API%20Question)
