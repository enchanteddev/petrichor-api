# The API Guidelines
This is made by me (Kaushik). Contact me if doubts.

**DON'T PROCEED FURTHER IF YOU ARE NOT SURE WHAT AN API IS. GOOGLE IT FIRST**

## API #1 User-Auth
### User Registration
- A **POST** API, that gets email and password, and registers the user.
- API Usage: ```base.url/api/register```
- Return Value:
  ```JSON
  {
    "registered": "true or false",
    "message": "'Success' or 'Already registered with this email' or 'Misc'"
  }
  ```
- Google Login Integration
### User Login
- A **POST** API, that gets email and password, and logs the user in.
- API Usage: ```base.url/api/login```
- Return Value:
  ```JSON
  {
    "loggedin": "true or false",
    "message": "'Success' or 'Not registered with this email' or 'Misc'",
    "user": {
        "name": "Kaushik Rawat",
        "email": "example@example.com",
        "phone": 1234567890,
        "CA": ""
      }
  }
  ```
### User data
- A **GET** API, returns user data
- API Usage: ```base.url/api/user?email=email@email.com```
- Response Value:
  ```JS
  {
    "name": "Kaushik Rawat",
    "email": "example@example.com",
    "phone": 1234567890,
    "CA": "" // leave blank for no CA code,
    ...
  }
  ```
## API #2 Data representation
- A **GET** API, diplays data for each event.
- Each event can have its own unique id, eg: T002 for "Tesseract" (**T**echinical **0**(pre-fest, 1 for on-fest) **02**nd event chronologically).
- The above nomenclature is not decided yet, I just came up with it, it can be anything else, but it will a string.
- API Usage: ```base.url/api/event_data?id=T002```
- API Response:
  ```JSON
  {
    "name": "Tesseract",
    "participants": [
      {
        "name": "Kaushik Rawat",
        "email": "example@example.com",
        "phone": 1234567890,
        "CA": ""
      },
      {
        "name": "Some Other Person",
        "email": "example2@example.com",
        "phone": 1234567890,
        "CA": ""
      }
    ]
  }
  ```
- **Note:** This API is just capable for things with a single participant, and not teams. Further spec will be released in future. For now assume there are only individual competitions
## API #3 Merchandise
- A **GET** API to show merch data.
- API Usage: ```base.url/api/merch?id=all```
- Response:
  ```JSON
  {
    "merch": [
      {
        "name" : "some weird-ass name from the creative team",
        "type" : "tshirt or cap or something",
        "price": "overpriced garbage, but iit ka logo so you will buy",
        "image": "base.url/static/merch-images/shirt.png"
      },
      {
        "name" : "some weird-ass name from the creative team",
        "type" : "tshirt or cap or something",
        "price": "overpriced garbage, but iit ka logo so you will buy",
        "image": "base.url/static/merch-images/shirt.png"
      },
      {
        "name" : "some weird-ass name from the creative team",
        "type" : "tshirt or cap or something",
        "price": "overpriced garbage, but iit ka logo so you will buy",
        "image": "base.url/static/merch-images/shirt.png"
      },
  ]
  }
  ```
