# 🔗 URL Shortener Api

A simple api that shortens long URLs, tracks clicks, supports expiration.

---

## 🚀 Features

- 🔐 Shorten any long URL  
- 🔁 Redirect using short codes  
- ⏰ Set optional expiration dates  
- 📊 Click tracking  
- ⚠️ Rate limiting (10 req/min per IP)  

---

## 🛠️ Tech Stack

| Layer     | Technology         |
|-----------|--------------------|
| Backend   | Node.js, Express.js|
| Database  | MongoDB (Mongoose) |
| Frontend  | HTML, CSS, JS      |
| Extras    | MongoDB TTL Index, QRServer API |

---

## 📦 API Endpoints

### `POST /shorten`

**Body:**

    {
      "url": "https://example.com/very/long/path",
      "expiresAt": "2025-07-15T12:00:00Z" // optional
    }

**Response:**

    {
      "shortUrl": "https://short.ly/abc123"
    }

---

### `GET /:code`

- Redirects to the original URL
- If expired: returns HTTP `410 Gone`

---


## 🧱 MongoDB Schema

    {
      originalUrl: String,
      shortCode: String,
      createdAt: Date,
      expiresAt: Date,
      clickCount: Number
    }
---

## 💻 Local Setup Instructions

### 1. Clone the repo

    git clone https://github.com/your-username/url-shortener.git
    cd url-shortener

### 2. Install dependencies

    npm install

### 3. Configure `.env`

    PORT=5000
    MONGO_URI=mongodb://localhost:27017/urlshortener
    BASE_URL=https://short.ly

### 4. Run the server

    npm start

---

## 📄 License

MIT
