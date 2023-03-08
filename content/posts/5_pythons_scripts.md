


## URL Shortener


```Python
import pyshorteners

s = pyshorteners.Shortener(api_key="YOUR_KEY")

long_url = input("Enter the URL to shorten: ")

short_url = s.bitly.short(long_url)

print("The shortened URL is: " + short_url)
```



## Fake infos generator 


```Python
import pandas as pd
from faker import Faker

# Create object
fake = Faker()

# Generate data
fake.name()
fake.text()
fake.address()
fake.email()
fake.date()
fake.country()
fake.phone_number()
fake.random_number(digits=5)

# Dataframe creation
fakeDataframe = pd.DataFrame({‘date’:[fake.date() for i in range(5)],
 ‘name’:[fake.name() for i in range(5)],
 ‘email’:[fake.email() for i in range(5)],
 ‘text’:[fake.text() for i in range(5)]})
print(fakeDataframe)
```


## YouTube Video Downloader


```Python
from pytube import YouTube

link = input("Enter a youtube video's URL") # i.e. https://youtu.be/dQw4w9WgXcQ

yt = Youtube(link)
yt.streams.first().download()

print("downloaded", link)

```


## NATO Phonetic Alphabet Encryptor


```Python
def encrypt_message(message):
   nato_alphabet = {
   ‘A’: ‘Alfa’, ‘B’: ‘Bravo’, ‘C’: ‘Charlie’, ‘D’: ‘Delta’,
   ‘E’: ‘Echo’, ‘F’: ‘Foxtrot’, ‘G’: ‘Golf’, ‘H’: ‘Hotel’,
   ‘I’: ‘India’, ‘J’: ‘Juliet’, ‘K’: ‘Kilo’, ‘L’: ‘Lima’,
   ‘M’: ‘Mike’, ’N’: ‘November’, ‘O’: ‘Oscar’, ‘P’: ‘Papa’,
   ‘Q’: ‘Quebec’, ‘R’: ‘Romeo’, ‘S’: ‘Sierra’, ‘T’: ‘Tango’,
   ‘U’: ‘Uniform’, ‘V’: ‘Victor’, ‘W’: ‘Whiskey’, ‘X’: ‘Xray’,
   ‘Y’: ‘Yankee’, ‘Z’: ‘Zulu’
   }

   encrypted_message = “”
  
# Iterate through each letter in the message
   for letter in message:
   
  # If the letter is in the dictionary, add the corresponding codeword to the encrypted message
     if letter.upper() in nato_alphabet:
     encrypted_message += nato_alphabet[letter.upper()] + “ “
   
  # If the letter is not in the dictionary, add the original letter to the encrypted message
     else:
     encrypted_message += letter

  return encrypted_message


message = "Hello World"
encrypted_message = encrypt_message(message)
print("Encrypted message: ", encrypted_message)

```


## Social Media Login Automation


```Python
from selenium import webdriver

driver = webdriver.Firefox()
driver.get(“https://www.facebook.com/")

# Find the email or phone field and enter the email or phone number
email_field = driver.find_element_by_id(“email”)
email_field.send_keys(“your_email_or_phone”)

# Find the password field and enter the password
password_field = driver.find_element_by_id(“pass”)
password_field.send_keys(“your_password”)

# Find the login button and click it
login_button = driver.find_element_by_id(“loginbutton”)
login_button.click()
```


## The Gray Area

* Omy awesome : 
  * https://thegrayarea.tech/
  * https://thegrayarea.tech/tryhackme-writeup-vulnversity-c6d497f5eac5 : how to get root access thanks to the systemctl binary
  * https://tryhackme.com/room/vulnversity



