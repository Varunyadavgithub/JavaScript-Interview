## 🌐 What is CORS?

**CORS** is a **browser security feature** that **restricts cross-origin HTTP requests** initiated from scripts running in the browser.

> CORS allows a web server to tell the browser:
> “Yes, it's okay for this site (origin) to access my resources.”

---

## 🧠 Why do we need CORS?

Let’s say:

- Your frontend runs on: `http://localhost:3000`
- Your backend/API runs on: `http://localhost:5000`

This is considered a **cross-origin** request. Browsers block such requests **by default** for security reasons.

CORS is a way to say: “Allow it safely.”

---

## 🔧 How does CORS work?

When the frontend (JavaScript in the browser) tries to access a resource on a different origin, the browser sends a **CORS request**.

### There are two types of CORS requests:

---

### 1. 🟢 **Simple Requests**

Sent automatically if:

- Method is `GET`, `POST`, or `HEAD`
- No custom headers
- Content-Type is `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain`

#### ✅ Browser flow:

1. Browser sends the actual request
2. Server responds with CORS headers like:
   ```http
   Access-Control-Allow-Origin: http://localhost:3000
   ```

3. If valid → browser lets the JS access the response.

---

### 2. 🟡 **Preflight Requests**

Sent **before the actual request** to ask permission for:

- Methods like `PUT`, `DELETE`, `PATCH`
- Custom headers
- Other content-types

#### ✅ Browser flow:

1. Browser sends an **OPTIONS** request (preflight)
2. Server responds with:
   ```http
   Access-Control-Allow-Origin: http://localhost:3000
   Access-Control-Allow-Methods: GET, POST, PUT
   Access-Control-Allow-Headers: Content-Type, Authorization
   ```

3. If valid → browser sends the actual request next.

---

## 🛠️ Server-side CORS Example (Node.js + Express)

```js
const express = require('express');
const cors = require('cors');
const app = express();

// Allow all origins (not recommended for production)
app.use(cors());

// Or allow specific origin
// app.use(cors({ origin: 'http://localhost:3000' }));

app.get('/data', (req, res) => {
  res.json({ message: 'CORS allowed' });
});

app.listen(5000, () => console.log('Server running on port 5000'));
```

---

## ⚠️ Common CORS Errors

- **CORS Policy Blocked:** Means the frontend tried to access an endpoint without permission.
- **Missing Access-Control-Allow-Origin:** The backend didn’t allow the origin.
- **Preflight request failed:** Usually due to missing method/header permission on the server.

---

## 📌 Summary Table

| Term                    | Meaning                                                             |
|-------------------------|---------------------------------------------------------------------|
| CORS                    | Cross-Origin Resource Sharing                                       |
| Origin                  | Protocol + Host + Port (e.g., `http://localhost:3000`)              |
| Preflight Request       | An `OPTIONS` request sent before the actual one                     |
| Access-Control-Allow-Origin | Server header to allow specific frontend origin              |
| Browser's Role          | Blocks unauthorized cross-origin requests by default                |

---

## ✅ Real Use Case Example

A React app (`localhost:3000`) makes an API call to a Node server (`localhost:5000`). To make this work:

1. The server must include:
   ```http
   Access-Control-Allow-Origin: http://localhost:3000
   ```

2. Or configure CORS properly using middleware (like `cors` package in Express)
