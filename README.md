# Project-JUNIOR-Your-Personal-Voice-Assistant
The proposed system is a hybrid voice assistant capable of functioning with and without internet connectivity. It performs local tasks (like opening applications or speaking responses) offline and uses the Gemini API for intelligent responses to complex queries when online.

# 🤖 JUNIOR – Your Personal Voice Assistant  

**JUNIOR** is a hybrid voice assistant built in Python that works both **online and offline**.  
It can perform **local system tasks** (like opening apps or speaking responses) without the internet and uses **Google Gemini API** for intelligent responses to complex queries when online.  

---

## 🧩 Features  

✅ **Offline Mode**
- Opens local or web applications (Google, YouTube, Instagram, LinkedIn, etc.)
- Plays predefined music tracks
- Provides speech feedback via text-to-speech (`pyttsx3`)

✅ **Online Mode**
- Uses **Gemini API** for smart, conversational responses
- Fetches real-time information through the internet

✅ **Voice Recognition**
- Uses your system’s microphone for real-time speech recognition
- Detects the activation word **“Junior”** before executing commands

---

## 🛠️ Technologies Used  

| Function | Library / API |
|-----------|----------------|
| Speech Recognition | `speech_recognition` |
| Text to Speech | `pyttsx3` |
| Microphone Input | `pyaudio` |
| Web Access | `webbrowser` |
| Knowledge Lookup | `wikipedia`, `google.genai` |
| AI Response Generation | **Gemini 2.5 Flash API** |

---

## 🧠 How It Works  

1. The assistant continuously listens for the keyword **“Junior”**.  
2. Once triggered, it listens for the next command.  
3. If the command matches a predefined task (like “open Google” or “play Song 1”), it executes locally.  
4. Otherwise, it sends the command to the **Gemini API** to get an intelligent response and speaks it aloud.  

---

## 💻 Installation  

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/Project-JUNIOR-Voice-Assistant.git
   cd Project-JUNIOR-Voice-Assistant
