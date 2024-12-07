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

### Showing a user:
```javascript
show users

### Deleting a user:
```javascript
db.dropUser("cooluser")





