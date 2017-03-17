# User

## Login

```shell
curl -X POST 
 -H "Content-Type: application/json"
 -H "Cache-Control: no-cache" 
 -H "Postman-Token: 445adf6ef-66f9-6e82-bbc8-9185216f9e47" 
 -d '{
        "email": "youremail@example.com",
        "password": "your password"
    }'
```

> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IJkLpXVCJ9.eyJ1c2VyIjp7ImNsaWVudElkIjoiNThhZDI3ZDYwNjc5NTBlN2I3MGVhMGQyIiwiZW1haWwiOiJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5NzM1MTA2fQ.AUN4ORsz_o7Gs3xjl4VDQZfeTCyicVbhurmp27wdefg_I"
  }
}
```

This endpoint allows user to login .

`GET http://localhost:5000/api/v1/login`

### Request Parameters

Parameter | Description
--------- | -----------
email | Your registered email id
password | Your password 

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
token | JWT token 

<aside class="success">
Remember — Enter your valid credentials!
</aside>


# Report

## Count Report
```shell
curl -X GET 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInqRS5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImNsaWVudzElkIjoiNThhZDI3ZDYwNjc5NTBlN2I3MGVhMGQyIiwiZW1haWwiOiJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5NTEyOTU0fQ.V5Pfz20Ep2EFClNJnqaU6tYIJKLbQQegGjEnAX8CJqnMA" 

```
> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "count": {
      "conversation": {
        "month": 33,
        "week": 1,
        "yesterday": 0,
        "today": 0,
        "total": 33
      },
      "successIntent": {
        "month": 0,
        "week": 0,
        "yesterday": 0,
        "today": 0,
        "total": 0
      },
      "failedIntent": {
        "month": 3,
        "week": 3,
        "yesterday": 0,
        "today": 0,
        "total": 3
      },
      "user": {
        "month": 0,
        "week": 0,
        "yesterday": 0,
        "today": 0,
        "total": 2
      }
    }
  }
}
```
`GET http://localhost:5000/api/v1/reports`

This endpoint retrieves a total count of conversation, success intent, failed intent and user access.

<aside class="warning">To access this API a valid JWT must be sent in the Authorization header</aside>

### Request Parameters

Parameter | Description
--------- | -----------
Authorization | Your JWT token

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
conversation |  To get the input and the output between the bot and the user.
successIntent | Success intent is determined by the confidence score that we recieve from each response of the Watson.The range of the confidence score is between 0 to 1.When the confidence score is above and not equal to 0.5 then it is determined as success intent.
failedIntent |   Failed intent is determined by the confidence score that we recieve from each response of the Watson.The range of the confidence score is between 0 to 1.When the confidence score is below or equal to 0.5 then it is determined as failed intent
user  |  The super admin will receive the total count of success and failed intents. 
month  | Total count of intent for month
week  | Total count of intent for week
yesterday  | Total count of intent for yesterday 
today  |  Total count of intent for today
total  |  Overall toal intent counts

## Conversation Report

```shell
curl -X GET 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpqrsXVCJ9.eyJ1c2VyIjp7ImNsaWVudElkIjoiNThhZDI3ZDYwNjc5fNTBlN2I3MGVhMGQyIiwiZW1haWwiOiJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5MjI1MzIyfQ.a7f6mgB2kp8KyyRk6SkvE1vbS43FVhBol5JWzbGGESBY" 

```
> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "conversationReport": [
      {
        "date": "Feb 28",
        "count": 13
      },
      {
        "date": "Mar 01",
        "count": 12
      },
      {
        "date": "Mar 02",
        "count": 7
      }
    ]
  }
}
```
`GET localhost:5000/api/v1/reports/conversation?endDate=:EndDate&startDate=:StartDate`

Conversation Reports API provides the count for total nummber of conversations occured for any given date.

<aside class="warning">To access this API a valid JWT must be sent in the Authorization header</aside>

### Request Parameters

Parameter | Description
--------- | -----------
Authorization | Your JWT token
startDate  |  Start date
endDate  |  End Date

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
date  | Conversation date
count  | Total count of conversations 

## Intent Report

```shell
curl -X GET 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImNsaWuVudElkIjoiNThhZDI3ZDYwNjc5NTBlN2I3MGVhMGQyIiwiZW1haWwiOixJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5MjI1MzIyfQ.a7f6mgB2kp8KyyRdk6SkvE1vbS43FVBcvol5JWzbGGESBY" 

```
> The above request returns JSON structured like this:

```json
{

}
```
`GET http://localhost:5000/api/v1/reports/intents?endDate=:EndDate&startDate=:StartDate`

Intent reports API provides the list of most used intents.

You can set limits to get the list of most frequently used intents and can also date range to filter the data.
By default you will be provided with the top five intents if the limit was not set.

<aside class="warning">To access this API a valid JWT must be sent in the Authorization header</aside>

### Request Parameters

Parameter | Description
--------- | -----------
Authorization | Your JWT token
startDate  |  Start date
endDate  |  End Date

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
date  | Conversation date
count  | Total count of conversations 


# ChatBot

## Get ChatBot

```shell
curl -X GET 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCfJ9.eyJ1c2VyIjp7ImNsaWVudElkIjoiNThhZDI3ZDYhwNjc5NTBlN2I3MGVhMGQyIiwiZW1ihaWwiOiJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5MjI1MzIyfQ.a7f6mgB2kp8KyyRk6SkvEd1vbS43FVBol5JWzbGGESBY" 

```
> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "name": "ZEB",
    "appearance": {
      "secondaryColor": "white",
      "primaryColor": "#08eaa3",
      "position": "BL",
      "showBotPicture": false,
      "badgeStyle": "COMPACT",
    },
    "text": {
      "titleBar": "Gust Bot",
      "startButton": "Start Chat",
      "welcomeText": "Welcome to Gust Chatbot",
      "badge": "Ask Clever",
    },
    "watson": {
      "workspaceId": "752b1f9a-6425-49dd-a02c-957793752189",
      "username": "78546a01-3420-4625-9e9d-11f5a6464de9",
      "password": "27h17mcu2Cmp"
    },
    "hideRegistrationForm": false,
    "hideRatingForm": true,
    "removeChatbotBrand": true,
    "language": "en",
    "avatar": null,
    "timezone": "Asia/Kolkata"
  }
}
```
`GET http://localhost:5000/api/v1/chatbot`

Get information about the chat bot including the name of the chat bot, appearance, text contents, Watson credentials, language, data and timezone in JSON format.

<aside class="warning">To access this API a valid JWT must be sent in the Authorization header</aside>

### Request Parameters

Parameter | Description
--------- | -----------
Authorization | Your JWT token

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
name  | Chatbot name
appearence  | ChatBot appearance
secondaryColor  | Secondary color of chatbot
primaryColor  |  Primary color of chatbot
position  |  chatbot position in window
showBotPicture  | To show chatbot picture
badgeStyle  | Badge style of chatbot
titleBar  |  Title bar text of Chatbot
startButton  |  Start button text of chatbot
welcomeText  |  Welcome text of chatbot
badge  |  Badge text of chatbot
workspaceId  |  Your watson workspace id
username  | Your watson username
password  | Your watson password
hideRegistrationForm  | To hide registration form
hideRatingForm  |  To hide rting form
removeChatbotBrand  |  To remove chatbot brand 
language  |  Language Type
avatar  |  To show avatar
timezone  | Timezone of chatbot

## Update ChatBot

```shell
curl -X PUT 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7cfgImNsaWVudEmnlkIjoiNThhZDI3ZDYwNjc5NTBlN2I3MGVhMGQl5yIiwiZW1haWwiOiJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5MjI1MzIyfQ.a7f6mgB2kp8KyyRk6SkvE1vbS43FVBobGGESBY" 
-H "Content-Type: application/json" 
-d '{
        "name": "ZEB",
        "appearance": {
            "badgeStyle": "COMPACT",
            "showBotPicture": true,
            "position": "BR",
            "primaryColor": "",
            "secondaryColor": "",
        },
        "text": {
            "titleBar": "Live Chat",
            "startButton": "Start Chat",
            "welcomeText": "Welcome to Live Chatbot",
            "badge": "Chat with us!",
            "firstMessage": "Hi {{username}}, How can i help you?",
        },
        "watson": {
            "workspaceId": "752b1f9a-6425-49dd-a02c-957793752189",
            "username": "78544a01-3120-4625-9f9d-11f5a6432de9",
            "password": "25h17nqw2Cmp"
        },
        "hideRegistrationForm": false,
        "hideRatingForm": true,
        "removeChatbotBrand": false,
        "language": "en",
        "avatar": null,
        "timezone": "Asia/Kolkata"
  }'
```
> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "name": "ZEB",
    "appearance": {
      "secondaryColor": "white",
      "primaryColor": "#08eaa3",
      "position": "BL",
      "showBotPicture": false,
      "badgeStyle": "COMPACT",
    },
    "text": {
      "titleBar": "Gust Bot",
      "startButton": "Start Chat",
      "welcomeText": "Welcome to Gust Chatbot",
      "badge": "Ask Clever",
    },
    "watson": {
      "workspaceId": "752b1f9a-6425-49dd-a02c-957793752189",
      "username": "78546a01-3420-4625-9e9d-11f5a6464de9",
      "password": "27h17mcu2Cmp"
    },
    "hideRegistrationForm": false,
    "hideRatingForm": true,
    "removeChatbotBrand": true,
    "language": "en",
    "avatar": null,
    "timezone": "Asia/Kolkata"
  }
}
```
`PUT http://localhost:5000/api/v1/chatbot`

To update the name of the chat bot, appearance, text contents, Watson credentials, language, data and timezone.

<aside class="warning">To access this API a valid JWT must be sent in the Authorization header</aside>

### Request Parameters

Parameter | Description
--------- | -----------
Authorization | Your JWT token
name  | Chatbot name
appearence  | ChatBot appearance
secondaryColor  | Secondary color of chatbot
primaryColor  |  Primary color of chatbot
position  |  chatbot position in window
showBotPicture  | To show chatbot picture
badgeStyle  | Badge style of chatbot
titleBar  |  Title bar text of Chatbot
startButton  |  Start button text of chatbot
welcomeText  |  Welcome text of chatbot
badge  |  Badge text of chatbot
workspaceId  |  Your watson workspace id
username  | Your watson username
password  | Your watson password
hideRegistrationForm  | To hide registration form
hideRatingForm  |  To hide rting form
removeChatbotBrand  |  To remove chatbot brand 
language  |  Language Type
avatar  |  To show avatar
timezone  | Timezone of chatbot

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
name  | Chatbot name
appearence  | ChatBot appearance
secondaryColor  | Secondary color of chatbot
primaryColor  |  Primary color of chatbot
position  |  chatbot position in window
showBotPicture  | To show chatbot picture
badgeStyle  | Badge style of chatbot
titleBar  |  Title bar text of Chatbot
startButton  |  Start button text of chatbot
welcomeText  |  Welcome text of chatbot
badge  |  Badge text of chatbot
workspaceId  |  Your watson workspace id
username  | Your watson username
password  | Your watson password
hideRegistrationForm  | To hide registration form
hideRatingForm  |  To hide rting form
removeChatbotBrand  |  To remove chatbot brand 
language  |  Language Type
avatar  |  To show avatar
timezone  | Timezone of chatbot

# Conversation

## Get Conversation History

```shell
curl -X GET 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cTI6IfpXVCJ9.eyJ1c2VyIjp7ImNsaWVudElkIjoiNThhZDI3ZDYwNjc5jkqlN2I3MGVhMGQyIiwiZW1haWwiOiJtYWFydGVuQGmsaXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5MjI1MzIyfQ.a7f6mgB2kp8KyyRk6fkvE2vbS43FVBol5JWzbGGESBY" 

```
> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "conversations": [
      {
        "chatbotId": "58b4182867680cf51b83b4a8",
        "general": {
          "ip": null,
          "browser": null,
          "os": null
        },
        "geo": {
          "region": null,
          "country": null,
          "city": null
        },
        "updatedAt": "2017-02-28T12:41:35.143Z",
        "createdAt": "2017-02-28T12:41:35.143Z",
        "conversations": [
          {
            "textType": "BOT",
            "text": "Hi. It looks like a nice drive today. What would you like me to do? ",
            "date": "2017-02-28T12:41:35.141Z",
          }
        ],
        "feedback": null,
        "rating": 0,
        "pageUrl": "",
        "endDate": "2017-02-28T12:41:35.142Z",
        "startDate": "2017-02-28T12:41:35.142Z",
        "name": "",
        "email": "",
        "watsonConversationId": "84957ffb-2ac5-4y11-8fed-ce0e68430f14"
     }
    ]
  }
}  
      
```
`GET http://localhost:5000/api/v1/conversation/history`

To provide the conversation history of the chat bot.

<aside class="warning">To access this API a valid JWT must be sent in the Authorization header</aside>

### Request Parameters

Parameter | Description
--------- | -----------
Authorization | Your JWT token

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
chatbotId  | Chatbot embeded code
ip  | End user ip details
browser  | End User browser details 
os  | End User os details
region  | End User region details
country  | End User country details
city  | End User city details
updatedAt  | Conversation updated date in database
createdAt  | Conversation created date in database
textType  | Conversation type [USER / BOT] 
text  | Conversation default text
date  | Coversation request date
feedback  | Feedback
rating  | 
pageUrl  |
endDate  | Coversation start date
startDate  | Coversation end date
name  | User name
email  | User email 
watsonConversationId  | Watson conversation id

