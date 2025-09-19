## 🛠️ Mutation GraphQL Exercises

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
