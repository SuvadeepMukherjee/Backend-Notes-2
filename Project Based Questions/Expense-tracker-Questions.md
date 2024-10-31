## Expense Tracker Questions

#### Q: How require function works in Node ? 

**Answer**: require *imports modules* and *returns there exported functions and objects for use in the current file* 

#### Q: What is the purpose of the path module in node.js ? 

**Answer**:The path module provides *utilities to work with file and directory paths ensuring cross-platform compatability* 

#### Q:Why is relative path better than absolute path ? 

**Answer**: relative paths improve *portability* by depending on the current file location 

#### Q: Why is it important to separate concerns by placing DB Logic in Models like Expense and User ?

**Answer**: makes the code *cleaner* and more *maintainable*

#### Q:What is *sequelize* ? 

**Answer**: Sequelize is an *Object-relational Mapping (ORM) library for node that allows us to interact with the DB using javascript* 

#### Q:How would you handle errors when requiring modules that may not exist ? 

**Answer**: using *try--catch*

```js
exports.getHomePage = (req, res, next) => {

  res.sendFile(path.join(rootDir, "views", "homePage.html"));

};
```

#### Q: What does `path.join(rootDir, "views", "homePage.html")`  do ?

**Answer**:It joins the rootDir(root directory ) , views folder and homePage.html file in views folder and joins them and sendFile sends the file when the client asks for it 

#### Q:What is the role of `sequelize.transaction` ? 

**Answer**: It ensures atomicity by rolling back all changes if any query fails preventing partial updates

#### Q:What does jsonwebtoken do ? 

**Answer**: Create and verify JSON Web Tokens (JWTs) for authentication 

#### Q:What does `jwt.sign()` do ? 

**Answer**:The `jwt.sign()` function takes two main parameters:     - Payload:  object with the data you want to encode in the token     - Secret: A secret key used to sign the token.   -The resulting JWT is a string  - we send this as a token during succesfull login (login function backend)

#### Q:Why is it important to use a secret key in the `jwt.sign()` function?

**Answer**:The secret key is used to sign the token, ensuring that the token cannot be forged. It secures the token and verifies its authenticity when it's sent back to the server.

#### Q:What happens if an invalid or tampered token is provided during authentication?

**Answer**:If an invalid or tampered token is provided during authentication, the server will reject the token, and authentication will fail, usually resulting in an error response to the client.

#### Q:Why are you using `path.join(rootDir,"views","login.html") instead of directly concatenating paths ? 

**Answer**: `path.join(rootDir,"views","sign-up.html")` constructs a platform independent file path , ensuring that the correct path seperator (eg / for Unix amd \ for Windows) is used

#### Q:What is the purpose of using `bcrypt` to hash the password, and what are the implications of not hashing it before storing it in the database?

**Answer**:The purpose of using `bcrypt` to hash the password is to securely store user credentials, protecting them from exposure. Storing plain-text passwords increases the risk of unauthorized access if the database is compromised.

#### Q:when should you avoid using transactions?

**Answer**:**Read-Only Operations:** When only reading data without modifying it, transactions may be unnecessary.

#### Q:What is the purpose of the `uuidv4` function in this code snippet, and when would you typically use it?

**Answer**:When the user sends a POST request to "/password/sendMail" EndPoint , we are generating a unique request id with `uuidv4()` , The email we sent to the user with a password reset link includes the unique request id as a parameter 
