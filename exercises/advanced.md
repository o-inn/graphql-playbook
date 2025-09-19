# ⚡ Advanced GraphQL Exercises

These exercises cover **variables, fragments, multiple queries, and chaining
relationships**.  
They build on the basics from `queries.md` (Pokémon API) and `mutations.md`
(GraphQL Zero).

---

## 🟣 Pokémon API (Advanced Queries)

### 1. Using Variables

Write a query with variables instead of hardcoding the Pokémon name.

```graphql
query GetPokemon($name: String!) {
  pokemon(name: $name) {
    id
    number
    name
    types
  }
}
```

With variables JSON:

```json
{
  "name": "Bulbasaur"
}
```

➡️ Change the variable to fetch Squirtle.

### 2. Fragments

Create a reusable fragment for Pokémon fields.

```graphql
fragment BasicInfo on Pokemon {
  id
  number
  name
}

{
  pokemon(name: "Eevee") {
    ...BasicInfo
    types
  }
}
```

➡️ Extend the fragment to also include the classification.

### 3. Multiple Pokémon Query

Fetch two different Pokémon in the same query.

```graphql
{
  pikachu: pokemon(name: "Pikachu") {
    number
    name
  }
  bulbasaur: pokemon(name: "Bulbasaur") {
    number
    name
  }
}
```

➡️ Modify it to also fetch their attacks.

## 🟠 GraphQL Zero (Chaining Relationships)

### 4. Chaining Queries

Fetch the first 2 users and their posts (title + body).

```graphql
{
  users(options: { paginate: { page: 1, limit: 2 } }) {
    data {
      id
      name
      posts {
        data {
          title
          body
        }
      }
    }
  }
}
```

➡️ Modify it to fetch comments for each post.

### 🌱 Next Steps

- Mix variables + fragments to make queries more reusable.
- Combine queries across Pokémon API and GraphQL Zero in the same playground.
- Try larger pagination challenges with pokemons(first: N) or users/posts in
  GraphQL Zero.
