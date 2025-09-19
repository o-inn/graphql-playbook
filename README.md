# 📘 GraphQL Cheat Sheet

A quick reference guide to help you (and your team) learn and use GraphQL
effectively.  
Includes concepts, examples, and common patterns.

---

## 🔑 Core Concepts

- **Schema** = the contract (defines types & operations).
- **Query** = read data (like `GET` in REST).
- **Mutation** = write/change data (like `POST/PUT/DELETE`).
- **Variables** = pass dynamic values into queries/mutations.
- **Relationships** = traverse fields naturally (e.g. `user.posts`).
- **Response shape = query shape** → you get exactly what you ask for.

---

## ⚖️ REST vs GraphQL

| Task                | REST                                                         | GraphQL                                    |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------ |
| Get user with posts | `GET /users/1` → user data <br> `GET /users/1/posts` → posts | `{ user(id: 1) { name posts { title } } }` |
| Over-fetching       | Returns _all_ fields, even if you only need one              | You choose which fields you want           |
| Endpoints           | Many endpoints (`/users`, `/posts`, etc.)                    | One endpoint (`/graphql`)                  |

---

## 🏗 Example Schema

```graphql
type User {
  id: ID!
  name: String!
  email: String!
  posts: [Post!]!
}

type Post {
  id: ID!
  title: String!
  published: Boolean!
  author: User!
}

type Query {
  user(id: ID!): User
  posts: [Post!]!
}

type Mutation {
  createUser(name: String!, email: String!): User
  createPost(title: String!, published: Boolean!, authorId: ID!): Post
}
```

---

## 📖 Query Example

```graphql
{
  user(id: 1) {
    name
    posts {
      title
      published
    }
  }
}
```

✅ Gets user 1’s name and their post titles with published status.

---

## ✍️ Mutation Example

```graphql
mutation {
  createUser(name: "Eoghan", email: "eoghan@example.com") {
    id
    name
  }
}
```

✅ Creates a user and returns their id and name.

---

## 🔄 Using Variables

```graphql
mutation CreatePost($title: String!, $published: Boolean!, $authorId: ID!) {
  createPost(title: $title, published: $published, authorId: $authorId) {
    id
    title
    author {
      name
    }
  }
}
```

#### With variables JSON:

```json
{
  "title": "Learning GraphQL",
  "published": true,
  "authorId": 1
}
```

## 📦 Common Patterns

#### Arguments

```graphql
{
  posts(published: true) {
    title
  }
}
```

## Pagination (Relay style)

```graphql
{
  posts(first: 5, after: "cursor123") {
    edges {
      node {
        id
        title
      }
    }
    pageInfo {
      hasNextPage
    }
  }
}
```

## Fragments (reusable field sets)

```graphql
fragment UserFields on User {
  id
  name
}

{
  user(id: 1) {
    ...UserFields
    email
  }
}
```

## 🧠 Quick Tips

- Use **parentheses `()`** for arguments/variables.
- Use **curly braces `{}`** for field selection.
- No commas inside field selections.
- Name operations (`query GetUser`, `mutation CreatePost`) for easier debugging.
- Always check the **schema** — you can only ask for what’s defined there.
