# MongoDB User Management Examples

This file contains practical examples for managing MongoDB users.

## Example 1: Create a New User

To create a new user with `readWrite` access to the `fruit` database:

```javascript
db.runCommand(
  {
    createUser: "cooluser",
    pwd: "newpassword",
    roles: [
      { role: "readWrite", db: "fruit" }
    ]
  }
)
