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

#### Q:Explain what `saltRounds` signifies and how it affects the security of the hashed password.

**Answer**:`saltRounds` indicates the computational cost of hashing the password. More salt rounds mean the hashing process takes longer, which increases security by making it harder for attackers to perform brute-force attacks or rainbow table attacks. However, there is a trade-off, as higher salt rounds may slow down legitimate login processes.

#### Q:What potential issues could arise from using a low number of salt rounds, and how can you determine the appropriate number of salt rounds for your application?

**Answer**:Using a low number of salt rounds can lead to weaker password hashes, making them easier to crack through brute-force or rainbow table attacks.

To determine the appropriate number of salt rounds, consider:

1. **Security Needs:** Higher salt rounds improve security but increase computation time.
2. **Performance Impact:** Balance security with acceptable performance for user login times.

A common practice is to start with 10 salt rounds and adjust based on performance testing and security requirements.

#### Q:Why is it important to use an asynchronous function for password hashing in a Node.js application?

**Answer**:Using an asynchronous function for password hashing is important because:

1. **Non-blocking:** It prevents blocking the event loop, allowing other requests to be processed while the hashing operation is performed. This improves the application's responsiveness.
2. **Performance:** Password hashing can be resource-intensive. Using `async` allows the server to handle multiple requests efficiently without waiting for the hashing to complete.

#### Q:What are the potential risks of directly using values from `req.body` and how can they be mitigated?

**Answer**:Directly using values from `req.body` can lead to security risks, such as injection attacks (SQL, NoSQL, etc.) and validation issues. To mitigate these risks, you should validate and sanitize inputs, use libraries like `express-validator`, and implement proper error handling.

#### Q:How would you validate the month provided in the request body to ensure it is in a correct format before querying the database?

**Answer**:Use a validation library (like `Joi`)

#### Q:What security measures should be considered when handling JWTs in a real-world application?

**Answer**:Helmet is a good measure for securing HTTP headers, additional security measures for handling JWTs include using HTTPS to encrypt data in transit, setting short expiration times for tokens, implementing refresh tokens for long-lived sessions, and properly validating the token on each request to ensure it hasn't been tampered with.
