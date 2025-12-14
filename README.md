# Voice-BridgeHere's a comprehensive README for Voice-Bridge:

```markdown
# 🌍 Voice-Bridge

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Django](https://img.shields.io/badge/Django-5.2.6-green.svg)](https://www.djangoproject.com/)
[![React](https://img.shields.io/badge/React-19.1.1-blue.svg)](https://reactjs.org/)

**Voice-Bridge** is an AI-powered multilingual announcement system that breaks down language barriers by automatically translating and generating voice announcements.

Perfect for government agencies, transportation hubs, educational institutions, healthcare facilities, and any organization that needs to communicate effectively across Nigeria's diverse linguistic landscape.

## ✨ Features

### 🎯 Core Functionality
- **Text-to-Multilingual Audio**: Convert English text into natural-sounding audio in Yoruba, Igbo, and Hausa
- **Voice-to-Multilingual Announcements**: Record audio and automatically transcribe, translate, and generate announcements in multiple languages
- **Announcement History**: Access and manage previously created announcements
- **Cloud Storage**: All audio files are securely stored on Cloudinary for easy access and playback

### 🚀 Technology Highlights
- AI-powered translation using Spitch API
- High-quality text-to-speech generation
- Automatic speech recognition and transcription
- Real-time audio processing and conversion
- Responsive web interface

## 🏗️ Tech Stack

### Backend
- **Framework**: Django 5.2.6 + Django REST Framework
- **Database**: PostgreSQL (production) / SQLite (development)
- **AI Services**: Spitch API (translation, TTS, transcription)
- **Storage**: Cloudinary
- **Audio Processing**: FFmpeg
- **Server**: Gunicorn

### Frontend
- **Framework**: React 19.1.1
- **Build Tool**: Vite 7.1.7
- **Styling**: Tailwind CSS 3.4.17
- **HTTP Client**: Axios
- **Routing**: React Router DOM

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- Python 3.10+
- Node.js 18+ and npm
- FFmpeg (for audio conversion)
- Git

### API Keys Required
- [Spitch API Key](https://spitch.ai) - For translation and text-to-speech
- [Cloudinary Account](https://cloudinary.com) - For audio file storage

## 🚀 Installation & Setup

### 1. Clone the Repository
```
git clone https://github.com/harshmriduhash/Voice-Bridge.git
cd Voice-Bridge
```

### 2. Backend Setup

#### Create Virtual Environment
```
cd backend
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

#### Install Dependencies
```
pip install -r requirements.txt
```

#### Configure Environment Variables
Create a `.env` file in the `backend` directory:

```
# Spitch AI API
SPITCH_API_KEY=your_spitch_api_key_here

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# Database (Optional - for production)
DATABASE_URL=postgresql://user:password@localhost:5432/voicebridge

# Django Settings
SECRET_KEY=your-secret-key-here
DEBUG=True
```

#### Run Migrations
```
python manage.py makemigrations
python manage.py migrate
```

#### Start Backend Server
```
python manage.py runserver
```

Backend will be available at `http://127.0.0.1:8000`

### 3. Frontend Setup

#### Navigate to Frontend Directory
```
cd ../frontend
```

#### Install Dependencies
```
npm install
```

#### Configure Environment Variables
Create a `.env` file in the `frontend` directory:

```
VITE_API_URL=http://127.0.0.1:8000
```

#### Start Development Server
```
npm run dev
```

Frontend will be available at `http://localhost:5173`

## 📖 Usage

### Creating Text-Based Announcements

1. Navigate to the **Create Announcement** page
2. Enter your announcement text in English
3. Select target languages (Yoruba, Igbo, Hausa)
4. Optionally select a tone (neutral, formal, friendly)
5. Click **Generate** to create multilingual audio announcements
6. Listen to or download the generated audio files

### Creating Voice-Based Announcements

1. Navigate to the **Voice Recording** page
2. Click the microphone icon to start recording
3. Speak your announcement in English
4. Stop recording and select target languages
5. The system will transcribe, translate, and generate audio in selected languages

### Viewing Announcement History

1. Navigate to the **History** page
2. Browse through previously created announcements
3. Play audio files directly from the browser
4. View translations and metadata

## 🌐 API Endpoints

### Announcements
```
POST   /api/create/          - Create text-based announcement
POST   /api/transcribe/      - Create voice-based announcement
GET    /api/history/         - Get announcement history
```

### Request Examples

#### Create Text Announcement
```
curl -X POST http://localhost:8000/api/create/ \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Welcome to our facility",
    "languages": ["yo", "ig", "ha"],
    "tone": "formal"
  }'
```

#### Create Voice Announcement
```
curl -X POST http://localhost:8000/api/transcribe/ \
  -F "audio=@recording.webm" \
  -F "languages=[\"yo\",\"ig\",\"ha\"]" \
  -F "tone=neutral"
```

## 🎨 Project Structure

```
Voice-Bridge/
├── backend/
│   ├── backend/           # Django settings
│   │   ├── settings.py
│   │   ├── urls.py
│   │   └── wsgi.py
│   ├── core/              # Main app
│   │   ├── models.py      # Database models
│   │   ├── views.py       # API views
│   │   ├── serializers.py # DRF serializers
│   │   └── urls.py        # App URLs
│   ├── requirements.txt
│   └── manage.py
│
└── frontend/
    ├── src/
    │   ├── pages/         # React pages
    │   ├── services/      # API services
    │   ├── context/       # State management
    │   └── App.jsx
    ├── package.json
    └── vite.config.js
```

## 🛠️ Development

### Running Tests
```
# Backend tests
cd backend
python manage.py test

# Frontend tests
cd frontend
npm run test
```

### Building for Production

#### Backend
```
cd backend
python manage.py collectstatic
gunicorn backend.wsgi:application
```

#### Frontend
```
cd frontend
npm run build
```

## 🌍 Supported Languages

| Language | Code | Voice Name |
|----------|------|------------|
| English  | en   | John       |
| Yoruba   | yo   | Femi       |
| Igbo     | ig   | Obinna     |
| Hausa    | ha   | Aliyu      |

## 🐛 Troubleshooting

### FFmpeg Not Found
Install FFmpeg:
```
# Ubuntu/Debian
sudo apt-get install ffmpeg

# macOS
brew install ffmpeg

# Windows
# Download from https://ffmpeg.org/download.html
```

### Cloudinary Upload Issues
Ensure your Cloudinary credentials are correct and your account has sufficient storage quota.

### Audio Recording Not Working
Make sure your browser has microphone permissions enabled for the application.

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👨‍💻 Author

**Harsh Mriduhash**
- GitHub: [@harshmriduhash](https://github.com/harshmriduhash)

## 🙏 Acknowledgments

- [Spitch AI](https://spitch.ai) for translation and text-to-speech services
- [Cloudinary](https://cloudinary.com) for audio file storage
- Nigerian language communities for inspiration

## 📧 Support

For support, email [your-email@example.com] or open an issue in the repository.

---

**Made with ❤️ for bridging language barriers in Nigeria**
```

This README provides:
- Clear project description and use cases
- Comprehensive installation instructions
- API documentation
- Usage examples
- Troubleshooting guide
- Contribution guidelines
- Professional formatting with badges and emojis

You can customize the email, license details, and any other specific information based on your requirements!