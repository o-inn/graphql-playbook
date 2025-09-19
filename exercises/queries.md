---
title: Queries
parent: Exercises
nav_order: 1
---

# 🔍 Queries GraphQL Exercises

### 1. Simple Query

Fetch a Pokémon’s **number** and **name**.

```graphql
{
  pokemon(name: "Pikachu") {
    number
    name
  }
}
```

➡️ Modify it to also return the Pokémon’s classification.

### 2. Nested Query

Fetch a Pokémon’s name and its attacks.

```graphql
{
  pokemon(name: "Pikachu") {
    name
    attacks {
      special {
        name
        damage
      }
    }
  }
}
```

➡️ Modify it to also include the fast attacks.

### 3. List Query

Fetch the first 5 Pokémon with their number and name.

```graphql
{
  pokemons(first: 5) {
    number
    name
  }
}
```

➡️ Modify it to fetch the first 10 Pokémon instead.

## 🟡 Intermediate

### 4. Nested Data with Evolutions

Fetch a Pokémon’s name and its evolutions.

```graphql
{
  pokemon(name: "Charmander") {
    name
    evolutions {
      number
      name
    }
  }
}
```

➡️ Modify it to also include the types of each evolution.
