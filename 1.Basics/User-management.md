### Creating a user:
```javascript
db.runCommand(
{
  createUser: "cooluser",
  pwd: "newpassword",
  roles: [
    { role: "readWrite", db: "fruit" }
  ]
})
