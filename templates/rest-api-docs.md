# REST API Documentation Template (My Little Pony Characters API)

Welcome to the My Little Pony Characters API template! 

My sample REST API template shows developers how to access information about characters from the My Little Pony universe, including details such as character names, special abilities, and more.

## Base URL
All API requests should be made to the following base URL:
```
https://api.mylittlepony.com/v1
```

---

## Authentication
To access the My Little Pony API, include your API key in the `Authorization` header for all requests. 

```
Authorization: Bearer YOUR_API_KEY
```

> Get your API key by signing up on our [developer portal](https://mylittlepony.com/dev-portal).

---

## Endpoints Overview

| Method | Endpoint                    | Description                         |
|--------|-----------------------------|-------------------------------------|
| GET    | /ponies                     | Get a list of all pony characters   |
| GET    | /ponies/{id}                | Get detailed information about a pony by ID |
| POST   | /ponies                     | Create a new pony character         |
| PUT    | /ponies/{id}                | Update an existing pony character by ID |
| DELETE | /ponies/{id}                | Delete a pony character by ID       |

---

## Endpoints

### 1. **Get All Ponies**

Retrieve a list of all My Little Pony characters.

- **Endpoint**: `/ponies`
- **Method**: `GET`
- **Headers**:
  - `Authorization: Bearer YOUR_API_KEY`
  
#### Request Parameters
| Parameter  | Type   | Required | Description                                   |
|------------|--------|----------|-----------------------------------------------|
| name       | string | No       | Filter ponies by name                         |
| species    | string | No       | Filter ponies by species (e.g., unicorn, pegasus) |
| sort       | string | No       | Sort by a field (e.g., `name`, `age`)         |
| limit      | integer| No       | Limit the number of ponies returned           |

**Example Request**
```
GET https://api.mylittlepony.com/v1/ponies?species=unicorn&limit=5
```

**Example Response**
```json
{
  "ponies": [
    {
      "id": "123",
      "name": "Twilight Sparkle",
      "species": "Unicorn",
      "color": "Purple",
      "abilities": ["Magic", "Flying"],
      "age": 18
    },
    {
      "id": "456",
      "name": "Rainbow Dash",
      "species": "Pegasus",
      "color": "Blue",
      "abilities": ["Flying", "Speed"],
      "age": 19
    }
  ]
}
```

#### Response Codes
| Code | Description                                   |
|------|-----------------------------------------------|
| 200  | OK. The list of ponies was successfully retrieved. |
| 401  | Unauthorized. Your API key is invalid or missing. |
| 500  | Internal Server Error. Something went wrong on the server. |

---

### 2. **Get a Pony by ID**

Retrieve detailed information about a specific pony character.

- **Endpoint**: `/ponies/{id}`
- **Method**: `GET`
- **Headers**:
  - `Authorization: Bearer YOUR_API_KEY`

#### Request Parameters
| Parameter | Type   | Required | Description                |
|-----------|--------|----------|----------------------------|
| id        | string | Yes      | unique pony ID    |

**Example Request**
```
GET https://api.mylittlepony.com/v1/ponies/123
```

**Example Response**
```json
{
  "id": "123",
  "name": "Twilight Sparkle",
  "species": "Unicorn",
  "color": "Purple",
  "abilities": ["Magic", "Flying"],
  "friends": [
    {
      "name": "Applejack",
      "species": "Earth Pony"
    },
    {
      "name": "Rainbow Dash",
      "species": "Pegasus"
    }
  ],
  "age": 18
}
```

#### Response Codes
| Code | Description                                |
|------|--------------------------------------------|
| 200  | OK. The pony details were successfully retrieved. |
| 404  | Not Found. The specified pony ID does not exist.  |

---

### 3. **Create a New Pony**

Add a new pony character to the database.

- **Endpoint**: `/ponies`
- **Method**: `POST`
- **Headers**:
  - `Authorization: Bearer YOUR_API_KEY`
  - `Content-Type: application/json`

#### Request Body
| Field      | Type    | Required | Description                            |
|------------|---------|----------|----------------------------------------|
| name       | string  | Yes      | The name of the pony                   |
| species    | string  | Yes      | The species of the pony (e.g., unicorn, pegasus, earth pony) |
| color      | string  | No       | The pony's color                       |
| abilities  | array   | No       | List of abilities (e.g., "Dark Magic", "Flying") |
| age        | integer | No       | Age of the pony                        |

**Example Request**
```json
POST https://api.mylittlepony.com/v1/ponies
{
  "name": "Fluttershy",
  "species": "Pegasus",
  "color": "Yellow",
  "abilities": ["Animal Communication", "Flying"],
  "age": 17
}
```

**Example Response**
```json
{
  "id": "789",
  "name": "Fluttershy",
  "species": "Pegasus",
  "color": "Yellow",
  "abilities": ["Animal Communication", "Flying"],
  "age": 17
}
```

#### Response Codes
| Code | Description                                   |
|------|-----------------------------------------------|
| 201  | Created. The pony was successfully added.     |
| 400  | Bad Request. The input data is invalid.       |

---

### 4. **Update a Pony**

Update information about an existing pony character.

- **Endpoint**: `/ponies/{id}`
- **Method**: `PUT`
- **Headers**:
  - `Authorization: Bearer YOUR_API_KEY`
  - `Content-Type: application/json`

#### Request Body
| Field      | Type    | Required | Description                            |
|------------|---------|----------|----------------------------------------|
| name       | string  | No       | The name of the pony                   |
| species    | string  | No       | The species of the pony                |
| color      | string  | No       | The pony's color                       |
| abilities  | array   | No       | List of abilities (e.g., "Dark Magic", "Flying") |
| age        | integer | No       | Age of the pony                        |

**Example Request**
```json
PUT https://api.mylittlepony.com/v1/ponies/123
{
  "name": "Twilight Sparkle",
  "species": "Alicorn",
  "color": "Purple",
  "abilities": ["Magic", "Flying", "Teleportation"],
  "age": 19
}
```

**Example Response**
```json
{
  "id": "123",
  "name": "Twilight Sparkle",
  "species": "Alicorn",
  "color": "Purple",
  "abilities": ["Magic", "Flying", "Teleportation"],
  "age": 19
}
```

#### Response Codes
| Code | Description                                |
|------|--------------------------------------------|
| 200  | OK. The pony details were successfully updated. |
| 400  | Bad Request. The input data is invalid.     |
| 404  | Not Found. The pony ID does not exist.      |

---

### 5. **Delete a Pony**

Delete a pony character from the database.

- **Endpoint**: `/ponies/{id}`
- **Method**: `DELETE`
- **Headers**:
  - `Authorization: Bearer YOUR_API_KEY`

**Example Request**
```
DELETE https://api.mylittlepony.com/v1/ponies/123
```

**Example Response**
```json
{
  "message": "Pony with ID 123 was successfully deleted."
}
```

#### Response Codes
| Code | Description                                |
|------|--------------------------------------------|
| 200  | OK. The pony was successfully deleted.     |
| 404  | Not Found. The pony ID does not exist.      |

---

## Rate Limiting

The API uses rate limiting to ensure fair usage. 

Each API key is limited to **100 requests per minute**.

---

## Error Codes

| Code | Message                  | Description                                |
|------|--------------------------|--------------------------------------------|
| 400  | Bad Request               | The request was invalid or malformed.      |
| 401  | Unauthorized              | The API key is missing or invalid.         |
| 404  | Not Found                 | The requested resource was not found.      |
| 500  | Internal Server Error     | Something went wrong on the server.        |

---

## Support
If you encounter any issues or have questions, reach out to your pony friends at [support@mylittleponyapi.com](mailto:support@mylittleponyapi.com)

---



> FYI, the '80s 'My Little Pony' cartoon is waaay weirder than you remember. 

![MLP_Movie_VHS_80s](https://github.com/user-attachments/assets/86e2c977-3222-4ad4-a80a-9dc4e7bc65fb)
