# The Intern Academy

## Team : PyDev 
## Team Members : Govind Jaiswal ,Pallavi Panday, Candes Perreira
## The 20° C MONSOON INTERNSHIP PROGRAM in Python Projects .
### Automatic_Mailing_System
     A user can automate the his mailing functioning by using this program. User have to Speak the Reciver Name , Subject and Conntent ,
     this program will automatic send the mail to that person. 
     
## Approch that we have used:

- Import the libraries :
     - smtplib
     - speech_recognition
     - pyttsx3
     - EmailMessage
- Making functions:
     - Listening the users msg
     - Giving Responsing 
     - Mail sending
 - Calling the funtions


### Importing the Libraries
```
     import smtplib
     import speech_recognition as sr
     import pyttsx3
     from email.message import EmailMessage
```

### Initializing the methods of Library

```
    listener = sr.Recognizer()
    engine = pyttsx3.init()
```
### Declaring the listening function()
```
    def talk(text):
    engine.say(text)
    engine.runAndWait()
```

### Declaring the Response funtion()
```
    def get_info():
    try:
        with sr.Microphone() as source:
            print('listening...')
            voice = listener.listen(source)
            info = listener.recognize_google(voice)
            print(info)
            return info.lower()
    except:
        pass
```

### Declaring the Sending Mail funtion()
```
    def send_email(receiver, subject, message):
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    # Make sure to give app access in your Google account
    server.login('*********@gmail.com', '**********')
    email = EmailMessage()
    email['From'] = 'Sender_Email'
    email['To'] = receiver
    email['Subject'] = subject
    email.set_content(message)
    server.send_message(email)
```

### Creating the perons list
```
    email_list = {
    'dude': 'cscience696@gmail.com',
    'bts': 'diamond@bts.com',
    'pink': 'jennie@blackpink.com',
    'lisa': 'lisa@blackpink.com',
    'irene': 'irene@redvelvet.com'
    }
```

### Getting the mail information
```
    def get_email_info():
    talk('To Whom you want to send email')
    name = get_info()
    receiver = email_list[name]
    print(receiver)
    talk('What is the subject of your email?')
    subject = get_info()
    talk('Tell me the text in your email')
    message = get_info()
    send_email(receiver, subject, message)
    talk('Hey lazy ass. Your email is sent')
    talk('Do you want to send more email?')
    send_more = get_info()
    if 'yes' in send_more:
        get_email_info()
```

### Calling the funtions
```
    get_email_info()
```
