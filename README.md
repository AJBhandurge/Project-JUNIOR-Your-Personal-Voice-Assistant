# Project-JUNIOR-Your-Personal-Voice-Assistant
The proposed system is a hybrid voice assistant capable of functioning with and without internet connectivity. It performs local tasks (like opening applications or speaking responses) offline and uses the Gemini API for intelligent responses to complex queries when online.

import speech_recognition as sr #For speech-to-text conversion
import pyaudio #To enable mic
import setuptools #To setup tools
import webbrowser #To open Browser
import pyttsx3 #For text-to-speech conversion
import wikipedia #to get information
from google import genai # To use googleai for information
music = {"jugraafiya":"https://youtu.be/gRRMSF0nB0c?si=7DYueCbN5pVNN6Vh", #Add your songs
         "laila":"https://youtu.be/5uL82FnMSeM?si=zdVO5NmAYqKSe6S6", 
         "bulleya":"https://youtu.be/a9Hxkc9YxGE?si=T60Ii_PG2Ch1GIjF",
        "shanti":"https://youtu.be/DAYszemgPxc?si=0iXrTNmWLzankVZI"}

def AI(command):  
    client = genai.Client(api_key="Google API")   #Google API
    response = client.models.generate_content(
    model="gemini-2.5-flash", contents=command)
    return (response.text)
    
recognizer = sr.Recognizer()
engine = pyttsx3.init()

def speak(text):
    engine.say(text)
    engine.runAndWait()
    
def ProcessCommand(c):
    if c.lower() == "open google":
        webbrowser.open("https://www.google.com")
    elif c.lower() == "open youtube":
        webbrowser.open("https://www.youtube.com")
    elif c.lower() == "open linkedin":
        webbrowser.open("https://www.linkdid.com")
    elif c.lower() == "open insta":
        webbrowser.open("https://www.instagram.com")
    elif c.lower().startswith("play"):
        song = c.lower().split(" ")[1]
        link = music[song]
        webbrowser.open(link)

    else:
        output = AI(c)
        speak(output)
if __name__ == "__main__":
    while True:
        rate = engine.getProperty('rate')
        engine.setProperty('rate',170)
        voices = engine.getProperty('voices')
        engine.setProperty('voice',voices[1].id)
        try:
            with sr.Microphone() as source:
                print("Speak:")
                recognizer.adjust_for_ambient_noise(source)
                audio = recognizer.listen(source)
                print("Recognizing")
                word = recognizer.recognize_google(audio)
            if word.lower() == "junior":
                speak("Yes..")
                with sr.Microphone() as source:
                    print("Listening")
                    recognizer.adjust_for_ambient_noise(source)
                    audio = recognizer.listen(source)
                    print("Recognizing")
                    command = recognizer.recognize_google(audio)
                    ProcessCommand(command)                   
        except sr.UnknownValueError :
                print("Unable to Recognize")
