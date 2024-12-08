### User Management Commands

```javascript
// Creating a user
db.runCommand(
{
  createUser: "cooluser",
  pwd: "newpassword",
  roles: [
    { role: "readWrite", db: "fruit" }
  ]
})

// Showing users
show users

// Deleting a user
db.dropUser("cooluser"))






