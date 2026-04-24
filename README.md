# 🎵 SaavnBox

<img width="1313" height="589" alt="image" src="https://github.com/user-attachments/assets/eac368ce-82c1-40f8-8e6e-f814a4c40b6d" />


> **Free, unlimited music downloads from JioSaavn — no account, no limits.**

SaavnBox is a Flask-based web application that wraps the JioSaavn API to let you search and download songs, albums, and playlists in high quality. It features a clean, dark-mode UI with audio preview and one-click downloads.

---

## ✨ Features

- 🔍 **Search** songs, albums, and playlists by name or artist
- 🔗 **Paste JioSaavn URLs** to fetch songs, albums, or playlists directly
- 🎧 **Audio preview** — listen before you download
- ⬇️ **One-click download** with high-quality (320kbps where available)
- 📃 **Lyrics support** — optionally fetch song lyrics
- 🔒 **Audio proxy** — bypasses CDN rate-limiting and CORS restrictions
- 📱 **Responsive design** — works on desktop and mobile

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- pip

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/aaakash-01/saavnbox.git
cd saavnbox

# 2. Create and activate a virtual environment
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt
```

### Running Locally

```bash
python app.py
```

The app will start at **http://localhost:5100**

For production use with Gunicorn:

```bash
gunicorn -w 4 -b 0.0.0.0:5100 app:app
```

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Main web UI |
| `GET` | `/song/?query=<name>` | Search for songs by name |
| `GET` | `/song/get/?id=<id>` | Get a song by its JioSaavn ID |
| `GET` | `/album/?query=<url\|name>` | Fetch an album |
| `GET` | `/playlist/?query=<url\|name>` | Fetch a playlist |
| `GET` | `/lyrics/?query=<id\|url>` | Fetch lyrics for a song |
| `GET` | `/result/?query=<url\|name>` | Smart search — auto-detects song/album/playlist from URL |
| `GET` | `/proxy/?url=<cdn_url>` | Proxy audio streams from JioSaavn CDN |

### Optional Query Parameters

| Parameter | Values | Description |
|-----------|--------|-------------|
| `lyrics` | `true` / `false` | Include lyrics in the response (default: `false`) |
| `songdata` | `true` / `false` | Include full song metadata (default: `true`) |

### Example Requests

```bash
# Search for a song
GET /song/?query=Tum Hi Ho

# Get song by ID
GET /song/get/?id=5WXAlMNt

# Fetch an album via URL
GET /album/?query=https://www.jiosaavn.com/album/aashiqui-2/4h1duHFeqrI_

# Get lyrics
GET /lyrics/?query=5WXAlMNt
```

---

## 🗂️ Project Structure

```
saavnbox/
├── app.py            # Flask app — routes and proxy logic
├── jiosaavn.py       # JioSaavn API wrapper (search, songs, albums, playlists)
├── helper.py         # Data formatting and URL decryption utilities
├── endpoints.py      # API endpoint constants
├── requirements.txt  # Python dependencies
├── templates/
│   └── index.html    # Frontend UI (single-page app)
└── assests/
    └── images/
        └── logo.png  # App logo
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python · Flask · Flask-CORS |
| API | JioSaavn internal API |
| Decryption | pyDes (DES cipher for audio URLs) |
| HTTP | requests |
| Frontend | Vanilla HTML · CSS · JavaScript |
| Fonts | Google Fonts — Outfit |
| Production | Gunicorn |

---

## ⚙️ Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `SECRET` | `thankyoutonystark#weloveyou3000` | Flask secret key |

Set it before running:

```bash
# Windows PowerShell
$env:SECRET = "your-secret-key"

# Linux / macOS
export SECRET="your-secret-key"
```

---

## 📦 Dependencies

```
Flask
gunicorn
requests
pyDes
flask-cors
```

Install all at once:

```bash
pip install -r requirements.txt
```

---

## ⚠️ Disclaimer

SaavnBox is built for **educational purposes only**. It uses JioSaavn's internal API to fetch publicly available music metadata and stream URLs. Please respect copyright law and JioSaavn's [Terms of Service](https://www.jiosaavn.com/s/termsofuse). Do not use this tool for commercial redistribution of copyrighted content.

 
