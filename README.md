#  Wroxen

Wroxen is an advanced **Telegram Movie / File Indexing & Search Bot** built using **Pyrogram**, **MongoDB**, and **Redis**.  
It allows you to index files from a source channel/group and provide a fast, searchable experience in a target group.

---

## ✨ Features

- 🔗 Link a **Source Channel** to a **Target Group**
- 📥 Index thousands of video/document files
- 🧠 Smart parsing of:
  - Title  
  - Year  
  - Quality  
  - Language  
  - Season / Episode  
  - Codec  
- ⚡ Ultra-fast search using **MongoDB + Redis cache**
- ♻️ Duplicate detection using `file_unique_id`


---

## 🧩 Architecture

- **Bot** – Handles user interaction & search in groups  
- **Userbot** – Reads messages from source channels  
- **MongoDB** – Stores indexed movie data  
- **Redis** – Caches search results for speed  
- **Single Lifecycle** – Bot & Userbot start/stop together  

---

## ⚠️ Notes

- Works **only in authorized & linked chats**.  
- Userbot must be at least a **member** in the source channel. 
## 🚀 Commands
---

### User Commands

- **/index `<target_chat_id>` `<source_chat_id>`**  
  Link your group with a source channel for indexing.

- **/delete `<target_chat_id>` `<source_chat_id>`**  
  Unlink a group and source channel and delete all indexed data.

- **Search Movies or Series**  
  Just send a movie name in your linked group.  
  The bot fetches results instantly with pagination buttons.

---

### Utility Commands

- **/resetdb** – Clean MongoDB database  
- **/reindex** – Reindex chat messages  
- **/clearcache** – Clear Redis cache (specific chat)  
- **/restart** – Pull latest commits & restart bot  
- **/flushredis** – Clear entire Redis database  
- **/checkbot** – Verify MongoDB & Redis health  
---

## 🛠 Environment Variables
| Variable     | Where to get it |
|-------------|----------------|
| `BOT_TOKEN` | Create a bot via [@BotFather](https://t.me/BotFather) on Telegram. He will give you the token. |
| `APP_ID` & `API_HASH` | Sign up at [my.telegram.org](https://my.telegram.org) → API development tools → Create a new app. |
| `USER_SESSION` | Generate a Pyrogram string session using Pyrogram. Login with your personal account number. |
| `AUTHORIZED_USERS` | Telegram user IDs of admins allowed to run `/index` and `/delete`. |
| `MONGO_URL`      | Connection string from **MongoDB Atlas** (cloud) or local MongoDB. Example: `mongodb+srv://username:password@cluster0.mongodb.net/dbname` |
| `DB_NAME`        | Database name, e.g., `wroxen-moviesbotdb` |
| `COLLECTION_NAME`| Collection name, e.g., `wroxen-movies` |
| `REDIS_HOST`    | Redis server host. You can use a local Redis server or a cloud Redis provider like [RedisLabs](https://redis.com/) / Upstash. |
| `REDIS_PORT`    | Usually `6379` (default) |
| `REDIS_USERNAME`| Optional, only if your Redis requires a username |
| `REDIS_PASSWORD`| Optional, only if your Redis requires a password |

---

###  Example `config.env`

```env
BOT_TOKEN=123456789:ABCdefGhIJKlmNoPQRsTUVwxyZ
APP_ID=1234567
API_HASH=abcdef1234567890abcdef1234567890
USER_SESSION=your_generated_user_session

AUTHORIZED_USERS=123456789,987654321

MONGO_URL=mongodb+srv://username:password@cluster0.mongodb.net/wroxen-moviesbotdb
DB_NAME=wroxen-moviesbotdb
COLLECTION_NAME=wroxen-movies

REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_USERNAME=
REDIS_PASSWORD=
```

---
## 🚀 Quick Setup

1️⃣ **Clone Repo**  
```bash
git clone https://github.com/lx0980/TG-Media-Search
```

2️⃣ **Setup Config**
Rename sample_config.env → config.env and fill in your credentials (Bot, Userbot, MongoDB, Redis).

**3️⃣ Install Dependencies**
```
pip install -r requirements.txt
```

**4️⃣ Run Bot**
```
python3 main.py
```

### [Lx 0980](https://github.com/lx0980) 
