Server-side languages are programming languages that run on the **web server**, not on the user’s browser. They are used to handle the backend of a website or application. Unlike client-side code (HTML, CSS, JavaScript), which runs on the user’s device, server-side code runs on a server and sends the result to the client.

**They are required for:**
1. Storing and retrieving data:
    - Using databases (MySQL, PostgreSQL, MongoDB) to save user information, posts, or transactions.
        
2. Creating dynamic pages:
    - Pages that change depending on the user or situation (e.g., showing a personalized dashboard).
    
3. Managing accounts and authentication:
    - Logging in/out, password handling, sessions, and user roles.
        
4. Running backend logic:
    - Performing calculations, sending emails, generating reports, or processing payments.
        
5. Communication with APIs:
    - Fetching external data (e.g., weather, payment gateway) securely.

---
## Common Server-Side Languages & Their Uses
|Language|Common Uses|Notes|
|---|---|---|
|**PHP**|Web applications, CMS (WordPress, Joomla)|Easy integration with HTML, widely supported|
|**Python**|Web development (Django, Flask), AI, Machine Learning|Clean syntax, great for rapid development|
|**NodeJS (JavaScript runtime)**|Real-time apps (chat apps, streaming, games)|Non-blocking I/O, event-driven, single language across frontend & backend|
|**Java**|Enterprise applications, large-scale web apps|Strongly typed, platform-independent, widely used in corporate software|
|**C#**|Windows apps, web apps with .NET|Great for enterprise apps, Microsoft ecosystem|

---

## Examples:
### PHP Example:
```bash
<?php
echo "Hello, world!";
?>
```

### Python Flask Example:
```bash
from flask import Flask
app = Flask(__name__)

@app.route("/")
def home():
    return "Hello, World!"

if __name__ == "__main__":
    app.run()
```


### NodeJS Example:
```bash
const http = require('http');
http.createServer((req, res) => {
    res.write("Hello World");
    res.end();
}).listen(3000);
```

----
## Client-Side vs Server-Side
|Factor|Client-Side|Server-Side|
|---|---|---|
|**Execution**|Runs in the user’s **browser**|Runs on the **web server**|
|**Speed**|Faster (direct execution on device)|Slower (server processes request first)|
|**Security**|Less secure, code is **visible** to users|More secure, code is **hidden** from users|
|**Access to Database**|Cannot directly access databases|Can access databases and perform CRUD operations|
|**Code Visibility**|Visible in browser developer tools|Hidden on server, only output sent to client|
|**Interactivity**|Handles UI updates, animations, form validations|Handles logic, authentication, database operations|
|**Resource Usage**|Uses user’s device resources|Uses server resources|
|**Examples**|HTML, CSS, JavaScript (front-end)|PHP, Python, NodeJS, Java, C#|
|**Dependency**|Independent of server for basic actions|Depends on server availability and processing|
|**Dynamic Content**|Limited – can manipulate DOM and local data|Unlimited – can generate pages based on user, database, or business logic|
|**Error Handling**|Limited to browser environment|Full control, can log and handle errors server-side|
|**Use Case**|Form validation, animations, interactive UI|User login, data storage, generating dynamic web pages|