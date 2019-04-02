import speech_recognition as sr
from gtts import gTTS
import pyglet
import time,os



r=sr.Recognizer()
lang='en'


with sr.Microphone() as source:
    print("Speak anything")
    audio=r.listen(source)
    print("Done")
    
    try:
        text=r.recognize_google(audio)
        print("you said :{}".format(text))
        
    except:
        print("sorry could not recognize your voice")

def speak():
    with sr.Microphone() as source:
       print("Speak anything")
       audio=r.listen(source)
       print("Done")
        
       try:
            text=r.recognize_google(audio)
            print("you said :{}".format(text))
            return (text)
            
            
       except:
            print("sorry could not recognize your voice")




def tts(time,lang):
    file=gTTS(text=text,lang=lang)
    filename='final_temp.mp3'
    file.save(filename)
    
    music=pyglet.media.load(filename,streaming=False)
    music.play()
    time.sleep(music.duration)
    os.remove(filename)


tts(time,lang)

text="Do you want to continue"
print(text)
tts(time,lang)
text=speak()
if(text=='yes'):
    print("Say your new message :")
    speak()
elif(text=='no'):
    print("thank you")
    
    
