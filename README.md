# 🎙️ GYANI - Voice-Activated AI Assistant

An intelligent voice assistant with speech recognition, text-to-speech, weather updates, YouTube integration, and schedule management.

## ✨ Features

- **Voice Recognition**: Real-time speech-to-text conversion
- **Text-to-Speech**: Natural voice responses
- **Weather Updates**: Real-time weather information via OpenWeatherMap API
- **YouTube Integration**: Voice-controlled YouTube search and playback
- **Schedule Management**: JSON-based task scheduling
- **AI Roadmap**: Integrated AI learning roadmap tracker
- **Multi-functional**: Web browsing, time queries, and more

## 🛠️ Tech Stack

- **Python 3.x**
- **SpeechRecognition** - Voice input processing
- **pyttsx3** - Text-to-speech engine
- **sounddevice** - Audio recording
- **yt-dlp** - YouTube integration
- **OpenWeatherMap API** - Weather data
- **NumPy & SciPy** - Audio processing

## 📦 Installation

```bash
git clone https://github.com/vageeshgos/machin-learning.git
cd machin-learning
pip install speechrecognition sounddevice pyttsx3 yt-dlp requests numpy scipy
```

## 🚀 Usage

```bash
python GYANI.py
```

Speak commands like:
- "What's the weather?"
- "Play [song name] on YouTube"
- "What time is it?"
- "Open [website]"

## 🔑 API Setup

Get your OpenWeatherMap API key:
1. Visit [OpenWeatherMap](https://openweathermap.org/api)
2. Sign up and get API key
3. Replace `API_KEY` in `GYANI.py`

## 📊 Features Breakdown

### Voice Commands
- Weather queries
- YouTube search
- Web browsing
- Time/date queries
- Schedule management

### Schedule System
- JSON-based task storage
- Date parsing with natural language
- Reminder system
- AI learning roadmap integration

### Audio Processing
- 5-second recording buffer
- 16kHz sample rate
- Noise handling
- Retry mechanism (3 attempts)

## 🎯 Use Cases

- Hands-free computer control
- Personal productivity assistant
- Learning schedule tracker
- Weather monitoring
- Entertainment control

## 🔧 Customization

Modify schedule paths:
```python
schedule_path = "your_schedule.json"
roadmap_path = "your_roadmap.json"
```

## 🤝 Contributing

Enhance voice commands or add new features!

## 👤 Author

**Vageesh Goswami**
- GitHub: [@vageeshgos](https://github.com/vageeshgos)
- LinkedIn: [vageesh-goswami](https://www.linkedin.com/in/vageesh-goswami/)
- Portfolio: [vageesh-goswami-portfolio.base44.app](https://vageesh-goswami-portfolio.base44.app/)
