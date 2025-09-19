# 📝 Exercises (Pokémon API Edition)

Practice queries to build confidence with GraphQL using the

- Use **Pokémon GraphQL API** →
  [https://graphql-pokemon2.vercel.app/](https://graphql-pokemon2.vercel.app/)
  for **read-only practice**.
- Use the **GraphQL Zero API**
  ([https://graphqlzero.almansi.me/api](https://graphqlzero.almansi.me/api)) for
  **mutations and CRUD practice**.

You can run these queries in **Apollo Sandbox** or any GraphQL playground.

---

## 🟢 Beginner

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

### 5. Using Variables

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

### 6. Fragments

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

## ## 🔵 Challenge (Pokemon)

### 7. Multiple Pokémon Query

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

---

## ✍️ GraphQL Zero Exercises (CRUD Practice)

Now that you’re comfortable with queries, try mutations and CRUD operations
using GraphQL Zero: 👉 https://graphqlzero.almansi.me/api

## 🟢 Beginner (GraphQL Zero)

### 1. Fetch a User

Get a user’s id, name, and email.

```graphql
{
  user(id: 1) {
    id
    name
    email
  }
}
```

➡️ Modify it to also fetch the user’s username and phone.

### 2. Fetch Posts

Get the first 3 posts (id + title).

```graphql
{
  posts(options: { paginate: { page: 1, limit: 3 } }) {
    data {
      id
      title
    }
  }
}
```

➡️ Modify it to also include each post’s body.

## 🟡 Intermediate (GraphQL Zero)

### 3. Create a Post

Create a new post for user 1.

```graphql
mutation {
  createPost(
    input: {
      title: "Learning GraphQL"
      body: "This is my first post!"
      userId: 1
    }
  ) {
    id
    title
    body
    user {
      id
      name
    }
  }
}
```

➡️ Try changing the userId and see how it changes the result.

### 4. Update a Post

Update the title of post 1.

```graphql
mutation {
  updatePost(id: 1, input: { title: "Updated Title with GraphQL" }) {
    id
    title
    body
  }
}
```

➡️ Try updating both title and body.

### 5. Delete a Post

Delete post 1.

```graphql
mutation {
  deletePost(id: 1)
}
```

➡️ Confirm the deletion by querying post 1 again.

## 🔵 Challenges (GraphQL Zero)

### 6. Create and Update a User

Create a new user.

```graphql
mutation {
  createUser(input: { name: "Alice GraphQL", email: "alice@example.com" }) {
    id
    name
    email
  }
}
```

Update the same user’s email.

```graphql
mutation {
  updateUser(id: USER_ID, input: { email: "alice.updated@example.com" }) {
    id
    name
    email
  }
}
```

➡️ Replace USER_ID with the id returned from the createUser mutation.

### 7. Chaining Queries

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

- Use Pokémon API for exploring queries and fragments.
- Use GraphQL Zero for practicing mutations and CRUD operations.
- Combine both to understand how GraphQL works across different APIs.
