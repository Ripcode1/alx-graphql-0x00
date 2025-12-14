# ALX GraphQL - Level 0: Query Fundamentals

GraphQL queries for the Rick and Morty API - Learning to write precise queries for characters and episodes.

## 📚 Overview

This directory contains GraphQL query exercises demonstrating fundamental GraphQL concepts:
- Querying single items by ID
- Querying paginated lists
- Selecting specific fields
- Using query arguments

## 🎯 Learning Objectives

By completing these tasks, you will:
- ✅ Write GraphQL queries with proper syntax
- ✅ Use arguments to filter data (id, page)
- ✅ Structure queries to avoid over-fetching
- ✅ Understand pagination in GraphQL

## 📁 Directory Structure

```
alx-graphql-0x00/
├── character/
│   ├── README.md
│   ├── character-id-1.graphql          # Query Rick Sanchez
│   ├── character-id-1-output.json
│   ├── character-id-2.graphql          # Query Morty Smith
│   ├── character-id-2-output.json
│   ├── character-id-3.graphql          # Query Summer Smith
│   ├── character-id-3-output.json
│   ├── character-id-4.graphql          # Query Beth Smith
│   ├── character-id-4-output.json
│   ├── characters-page-1.graphql       # Paginated list - Page 1
│   ├── characters-page-1-output.json
│   ├── characters-page-2.graphql       # Paginated list - Page 2
│   ├── characters-page-2-output.json
│   ├── characters-page-3.graphql       # Paginated list - Page 3
│   ├── characters-page-3-output.json
│   ├── characters-page-4.graphql       # Paginated list - Page 4
│   └── characters-page-4-output.json
├── episode/
│   ├── README.md
│   ├── episode-page-1.graphql          # Query Episode 1
│   ├── characters-page-1-output.json
│   ├── characters-page-2.graphql       # Query Episode 2
│   ├── characters-page-2-output.json
│   ├── characters-page-3.graphql       # Query Episode 3
│   ├── characters-page-3-output.json
│   ├── characters-page-4.graphql       # Query Episode 4
│   └── characters-page-4-output.json
└── README.md (this file)
```

## 🚀 Getting Started

### API Endpoint
```
https://rickandmortyapi.com/graphql
```

### Testing Your Queries

#### Option 1: GraphQL Playground (Recommended)
1. Visit [https://rickandmortyapi.com/graphql](https://rickandmortyapi.com/graphql)
2. Copy a query from any `.graphql` file
3. Paste into the playground
4. Click the play button ▶️

#### Option 2: cURL
```bash
curl 'https://rickandmortyapi.com/graphql' \
  -H 'Content-Type: application/json' \
  -d '{"query":"{ character(id: 1) { id name status species type gender } }"}'
```

#### Option 3: Postman
1. Create POST request to `https://rickandmortyapi.com/graphql`
2. Set header: `Content-Type: application/json`
3. Select GraphQL tab
4. Paste your query

## 📝 Tasks

### Task 0: Get Specific Character by ID

Query individual characters using their unique ID.

**Files**: `character/character-id-{1-4}.graphql`

**Example Query**:
```graphql
query GetCharacter {
  character(id: 1) {
    id
    name
    status
    species
    type
    gender
  }
}
```

**What You'll Learn**:
- Using query arguments (`id: 1`)
- Selecting specific fields
- Working with scalar types

### Task 1: Get List of All Characters

Query paginated lists of characters.

**Files**: `character/characters-page-{1-4}.graphql`

**Example Query**:
```graphql
query GetCharacters {
  characters(page: 1) {
    results {
      id
      name
      status
      image
    }
  }
}
```

**What You'll Learn**:
- Pagination with `page` argument
- Nested selection (results array)
- Efficient data fetching

### Task 2: Get Specific Episode by ID

Query individual episodes.

**Files**: `episode/characters-page-{1-4}.graphql`

**Example Query**:
```graphql
query GetEpisode {
  episode(id: 1) {
    id
    name
    air_date
    episode
  }
}
```

**What You'll Learn**:
- Querying different entity types
- Episode-specific fields
- Date formatting in GraphQL

## 🔑 Key Concepts

### GraphQL vs REST

| Feature | REST | GraphQL |
|---------|------|---------|
| Endpoints | Multiple (`/api/characters`, `/api/episodes`) | Single (`/graphql`) |
| Data Fetching | Fixed response structure | Client specifies fields |
| Over-fetching | Common | Eliminated |
| Under-fetching | Requires multiple requests | Single request with nested data |

### Query Structure

```graphql
query QueryName {           # Operation type and name
  fieldName(arg: value) {   # Field with argument
    subfield1               # Selected fields
    subfield2
  }
}
```

### Arguments

Arguments allow you to filter and customize queries:

```graphql
character(id: 1)           # Get specific character
characters(page: 2)        # Get page 2 of characters
episodes(filter: {...})    # Filter episodes
```

### Pagination

The API uses cursor-based pagination:

```graphql
{
  characters(page: 1) {
    info {
      pages    # Total pages
      next     # Next page number
      prev     # Previous page number
      count    # Total count
    }
    results {
      # Character data
    }
  }
}
```

## 📊 Output Files

Each `.graphql` query has a corresponding `-output.json` file showing:
- Expected response structure
- Sample data from the API
- Field types and values

These outputs help you:
- ✅ Verify your queries work correctly
- ✅ Understand response structure
- ✅ Learn GraphQL response format

## 🎓 Learning Path

1. **Start with character-id-1.graphql**
   - Learn basic query syntax
   - Understand field selection
   - See simple response structure

2. **Progress to characters-page-1.graphql**
   - Learn about pagination
   - Work with nested data
   - Handle result arrays

3. **Explore episode queries**
   - Apply learned concepts
   - Work with different types
   - Practice query construction

## 💡 Tips

1. **Start Small**: Begin with simple queries, add complexity gradually
2. **Check Output**: Compare your results with provided output files
3. **Experiment**: Try adding/removing fields to see what changes
4. **Read Errors**: GraphQL provides helpful error messages
5. **Use Introspection**: The playground shows available fields

## 🔍 Common Patterns

### Single Item Query
```graphql
query {
  character(id: 1) {
    id
    name
  }
}
```

### List Query with Pagination
```graphql
query {
  characters(page: 1) {
    info {
      count
      pages
    }
    results {
      id
      name
    }
  }
}
```

### Selecting Minimal Fields
```graphql
query {
  character(id: 1) {
    id        # Only get what you need
    name      # Avoid over-fetching
  }
}
```

## 🐛 Troubleshooting

**Query doesn't work?**
- Check syntax (missing brackets, commas)
- Verify field names match API schema
- Ensure arguments are correct type

**Empty results?**
- Check if ID exists
- Verify page number is valid
- Review error messages in response

**Wrong data structure?**
- Compare with output files
- Check nesting levels
- Verify field names

## 📚 Resources

- [GraphQL Official Documentation](https://graphql.org/learn/)
- [Rick and Morty API Docs](https://rickandmortyapi.com/documentation)
- [GraphQL Query Language](https://graphql.org/learn/queries/)
- [Apollo GraphQL Tutorial](https://www.apollographql.com/tutorials/)

## ✅ Checklist

Before moving to next level, ensure you can:
- [ ] Write a query for a single character by ID
- [ ] Write a query for a paginated list
- [ ] Select only needed fields
- [ ] Use query arguments correctly
- [ ] Understand response structure
- [ ] Identify when to paginate vs. single query

## 🎯 Next Steps

After mastering these fundamentals, proceed to:
- **alx-graphql-0x01**: Integrate GraphQL into a React app
- **alx-graphql-0x02**: Build a full application with UI components

---

**Repository**: `alx-graphql-0x00`  
**Directories**: `character/`, `episode/`

Happy querying! 🚀
