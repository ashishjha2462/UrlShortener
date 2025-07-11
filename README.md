# 🔗 URL Shortener Api

A simple api that shortens long URLs, tracks clicks, supports expiration.

---

## 🚀 Features

- 🔐 Shorten any long URL

  ***Screenshot:***
  <img width="1713" height="875" alt="Screenshot 2025-07-11 110221" src="https://github.com/user-attachments/assets/ea3ecbe0-3d12-4e96-a304-41f437fdcf44" />

- 🔁 Redirect using short codes

  ***Screenshot:***
  <img width="1722" height="922" alt="Screenshot 2025-07-11 110332" src="https://github.com/user-attachments/assets/f3216373-cef2-4eb1-844d-bbab3f6a2e8f" />

- ⏰ Set optional expiration dates

  ***Screenshot:***
  <img width="1714" height="765" alt="Screenshot 2025-07-11 111345" src="https://github.com/user-attachments/assets/9a74ef17-0347-4e9f-82f5-57b8389b6408" />

- 📊 Click tracking

  ***Screenshot:***
  <img width="1460" height="259" alt="Screenshot 2025-07-11 111138" src="https://github.com/user-attachments/assets/aa99f52c-0bfd-4f63-adf8-21c08ad0e548" />

- ⚠️ Rate limiting (10 req/min per IP)

  ***Screenshot:***
  <img width="1727" height="679" alt="Screenshot 2025-07-11 110744" src="https://github.com/user-attachments/assets/91ef08cf-f424-4bd2-b10e-1832f95f8187" />

---

## 🛠️ Tech Stack

| Layer     | Technology         |
|-----------|--------------------|
| Backend   | Node.js, Express.js|
| Database  | MongoDB (Mongoose) |
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

  ***Screenshot:***
  <img width="1460" height="259" alt="Screenshot 2025-07-11 111138" src="https://github.com/user-attachments/assets/d1c7180e-f274-4fc0-9c89-1351f14062d0" />

---

## 💻 Local Setup Instructions

### 1. Clone the repo

    git clone https://github.com/your-username/url-shortener.git
    cd url-shortener

### 2. Delete node_modules folder

### 3. Install dependencies

    npm install

### 4. Configure `.env`

    PORT=5000
    MONGO_URI=mongodb://localhost:27017/urlshortener
    BASE_URL=https://short.ly

### 5. Run the server

    npm start

---

## 📄 License

MIT
