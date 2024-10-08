# GraphQL API Documentation Template (She-Ra Characters API)

Welcome to the **She-Ra Characters GraphQL API**! 

My fun API allows you to query information about your favorite characters from the She-Ra universe, including their names, species, abilities, allies, and more. 

My template outlines how to structure the documentation for a **GraphQL API** using examples from the She-Ra universe. It documents example queries, mutations, types, and common errors. 

Let me know if you'd like to adjust or expand it!

## API Endpoint
All queries to the API should be made to the following GraphQL endpoint:

```
https://api.shera-universe.com/graphql
```

---

## Authentication

To access the API, include your API key in the request headers:

**Example:**
```json
{
  "Authorization": "Bearer YOUR_API_KEY"
}
```

---

## Querying the API

In GraphQL, you specify exactly what data you need, and the API will return only the requested fields. 

Below are some examples of queries and mutations you can make.

**Example Query: Retrieve Basic Character Information**

The following query fetches a character's name, species, and abilities by their ID.

#### Request:
```graphql
query {
  character(id: "1") {
    name
    species
    abilities
  }
}
```

#### Response:
```json
{
  "data": {
    "character": {
      "name": "Adora",
      "species": "Human",
      "abilities": ["Sword of Protection", "Super Strength"]
    }
  }
}
```

---

**Example Query: Retrieve a List of Allies for a Character**

You can also query for a list of allies related to a specific character.

#### Request:
```graphql
query {
  character(id: "2") {
    name
    allies {
      name
      species
    }
  }
}
```

#### Response:
```json
{
  "data": {
    "character": {
      "name": "She-Ra",
      "allies": [
        {
          "name": "Glimmer",
          "species": "Magicat"
        },
        {
          "name": "Bow",
          "species": "Human"
        }
      ]
    }
  }
}
```

---

**Example Query: Fetch Characters by Species**

Want to find all characters of a certain species? 

#### Request:
```graphql
query {
  characters(species: "Human") {
    name
    abilities
  }
}
```

#### Response:
```json
{
  "data": {
    "characters": [
      {
        "name": "Adora",
        "abilities": ["Sword of Protection", "Super Strength"]
      },
      {
        "name": "Bow",
        "abilities": ["Expert Archer", "Tech Master"]
      }
    ]
  }
}
```

---

**Example Mutation: Create a New Character**

In GraphQL, you can also modify the data. 

Here’s how to add a new character to the She-Ra universe.

#### Request:
```graphql
mutation {
  createCharacter(input: {
    name: "Catra",
    species: "Magicat",
    abilities: ["Agility", "Claws"]
  }) {
    character {
      id
      name
      species
      abilities
    }
  }
}
```

#### Response:
```json
{
  "data": {
    "createCharacter": {
      "character": {
        "id": "3",
        "name": "Catra",
        "species": "Magicat",
        "abilities": ["Agility", "Claws"]
      }
    }
  }
}
```

---

**Example Mutation: Update a Character’s Abilities**

You can also update the abilities of an existing character.

#### Request:
```graphql
mutation {
  updateCharacter(id: "3", input: {
    abilities: ["Agility", "Claws", "Enhanced Speed"]
  }) {
    character {
      id
      name
      abilities
    }
  }
}
```

#### Response:
```json
{
  "data": {
    "updateCharacter": {
      "character": {
        "id": "3",
        "name": "Catra",
        "abilities": ["Agility", "Claws", "Enhanced Speed"]
      }
    }
  }
}
```

---

## Available Types

### **Character**
- **id** (ID): The unique identifier of the character.
- **name** (String): The name of the character.
- **species** (String): The species of the character (e.g., Human, Magicat).
- **abilities** (Array of Strings): The abilities or powers of the character.
- **allies** (Array of Characters): A list of other characters who are allies of this character.

### **Queries**

#### `character(id: ID!)`: Fetch a character by ID
- **Parameters**:
  - `id` (ID!): The unique identifier of the character you want to retrieve.

#### `characters(species: String)`: Fetch all characters, with optional filtering by species
- **Parameters**:
  - `species` (String): Filter characters by species (e.g., Human, Magicat).

### **Mutations**

#### `createCharacter(input: CreateCharacterInput!)`: Create a new character
- **Parameters**:
  - `input` (CreateCharacterInput!): The input data to create a new character (name, species, abilities).

#### `updateCharacter(id: ID!, input: UpdateCharacterInput!)`: Update an existing character's data
- **Parameters**:
  - `id` (ID!): The ID of the character to update.
  - `input` (UpdateCharacterInput!): The data to update (abilities, allies, etc.).

---

## Error Handling

When things go wrong, the API will return an error message. 

Below are some common errors:

- **400 Bad Request**: The request is malformed.
- **401 Unauthorized**: Invalid API key or no API key provided.
- **404 Not Found**: The requested character or resource doesn’t exist.
- **500 Internal Server Error**: Something went wrong on the server.

**Example error response:**
```json
{
  "errors": [
    {
      "message": "Character not found",
      "locations": [{ "line": 2, "column": 3 }],
      "path": ["character"]
    }
  ]
}
```

---

## Rate Limiting

Each API key is limited to **200 requests per minute**. 

Be careful with your request rates to avoid being throttled.

---

## Try it Out!

If you prefer to use a graphical user interface to send a test query, you can use clients such as [GraphiQL](https://graphiql-online.com/), [Insomnia](https://insomnia.rest/), or [Postman](https://www.postman.com/).

---

> 🌈 Did you know? In the original 80s series, She-Ra talks to animals, sometimes telepathically. 

![Screenshot 2024-10-07 195615](https://github.com/user-attachments/assets/7626342e-f1d8-482e-a8b2-863ebc0d1e7d)






