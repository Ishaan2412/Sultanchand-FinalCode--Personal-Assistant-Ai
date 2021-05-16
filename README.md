# Sultanchand-FinalCode--Personal-Assistant-Ai

Code:-

import speech_recognition as sr
import pyttsx3
import pywhatkit
import datetime
import wikipedia
import pyjokes
import pyaudio

listener = sr.Recognizer()
model = pyttsx3.init()
model.say('Hello I am Champ, How can I help you?')


def talk(text):
    model.say(text)
    model.runAndWait()


def take_command():
    print("Getting command")
    command = ''
    with sr.Microphone() as source:
        print('listening...')
        voice = listener.listen(source)
        try:
            command = listener.recognize_google(voice)
            print("command is",command)
            command = command.lower()
            if 'champ' in command:
                command = command.replace('champ', '')
                print(command)
        except:
            print("Sorry couldnt guess")
    return command


def run_champ():
    print("take_command is called")
    command = take_command()
    print(command)

    if 'play' in command:
        song = command.replace('play', '')
        talk('playing ' + song)
        pywhatkit.playonyt(song)

    elif 'time' in command:
        time = datetime.datetime.now().strftime('%I:%M %p')
        talk('Current time is ' + time)

    elif 'who the heck is' in command:
        person = command.replace('who the heck is', '')
        info = wikipedia.summary(person, 1)
        print(info)
        talk(info)

    elif 'date' in command:
        talk('sorry, I have a headache')

    elif 'are you single' in command:
        talk('I am in a relationship with wifi')

    elif 'what is' in command:
        person = command.replace('what is','')
        info = wikipedia.summary(person,1)
        print(info)
        talk(info)

    elif 'who was' in command:
        person = command.replace('who was','')
        info = wikipedia.summary(person,1)
        print(info)
        talk(info)

    elif 'who was the' in command:
        person = command.replace('who was the','')
        info = wikipedia.summary(person,1)
        print(info)
        talk(info)

    elif 'wikipedia' in command:
        person = command.replace('wikipedia','')
        info = wikipedia.summary(person,1)
        print(info)
        talk(info)

    elif 'what is the full form of' in command:
        person = command.replace('what is the full form of','')
        info = wikipedia.summary(person,1)
        print(info)
        talk(info)

    elif 'joke' in command:
        talk(pyjokes.get_joke())

    else:
        talk('Please say the command again.')


while True:
    run_champ()
    
    
    
   
  
Import commands:

pip install SpeechRecognition
pip install pyttsx3
pip install pipwin
pipwin install pyaudio
pip install pywhatkit
pip install wikipedia
pip install pyjokes
pip install pythoncom
install pywintypes
