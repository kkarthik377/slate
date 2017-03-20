# ChatBot Widget

## Post Conversation

```shell
curl -X POST 
-H "Content-Type: application/json" 
-d '{
        "input": {},
        "context": {},
        "chatbot": {
            "name": "your name",
            "email": "yourmailid@sample.com",
            "pageUrl": ""
        },
        "browserDetails": {
            "screenResolution": "1440 x 900",
            "browser": "Chrome",
            "browserVersion": "56.0.2924.87",
            "browserMajorVersion": 56,
            "mobile": false,
            "os": "Mac OS X",
            "osVersion": "10_12_3",
            "cookies": true,
            "flashVersion": "no check",
            "timeZone": "+05:30",
            "ipAddress": "183.288.102.215"
        }
    }'
```

> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "intents": [],
    "entities": [],
    "input": {},
    "output": {
      "log_messages": [],
      "text": [
        "hallo, wat kan ik voor u doen?"
      ],
      "nodes_visited": [
        "welcome"
      ]
    },
    "context": {
      "conversation_id": "2a7f6a1a-de36-4308-ae06-c2f96f4f9efc",
      "system": {
        "dialog_stack": [
          {
            "dialog_node": "welcome"
          }
        ],
        "dialog_turn_counter": 1,
        "dialog_request_counter": 1,
        "_node_output_map": {
          "welcome": [
            0,
            2,
            6,
            1,
            5,
            0,
            3,
            4
          ]
        }
      }
    }
  }
}
```

Get a response to a user's input.

`POST http://localhost:5000/api/v1/conversation/:chatbotembedcode`

### Request Parameters

Parameter | Description
--------- | -----------
input | The user input from the request
context | The context for the dialog node
name  | End user name
email  | End user email
pageUrl  | End user pageUrl
browserDetails  | End user browser deatails
screenResolution  | Screen resolution of end user browser
browser  | End user browser name
browserVersion  | End user browser version
browserMajorVersion  | Browser major version
mobile  | End user mobile number
os  | End user os type
osVersion  | End user os version
flashVersion  | End user flash version
timeZone  | Timezone
ipAddress  | End user ip address

### Response Parameters

Parameter | Description
--------- | -----------
status | Status message
intents  | An array of intents objects defining the intents for the workspace.
entities  | An array of entities objects defining the entities for the workspace.
input  | The user input from the request
output  | The output from the dialog node
log_messages  | Up to 50 messages logged with the request. Returns an empty array if no messages are returned.
text  | An array of responses to the user. Returns an empty array if no responses are returned
nodes_visited | An array of the nodes that were triggered to create the response. This information is useful for debugging and for visualizing the path taken through the node tree.
conversation_id | The unique identifier of the conversation.
dialog_stack | An array of DialogStack objects identifying the dialog nodes that are in focus in the conversation.
dialog_node | The ID of a dialog node.
dialog_turn_counter | The number of cycles of user input and response in this conversation.
dialog_request_counter | The number of inputs in this conversation. This counter might be higher than the dialog_turn_counter counter when multiple inputs are needed before a response can be returned.


<aside class="success">
Remember — Enter your authorized credentials!
</aside>

## Get ChatBot Config

```shell
localhost:5000/api/v1/chatbot/f0a3dc1f865a4b349a11b78282c2ab0f
```

> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "name": "ZEB",
    "appearance": {
      "secondaryColor": "",
      "primaryColor": "",
      "position": "BR",
      "showBotPicture": true,
      "badgeStyle": "COMPACT",
    },
    "text": {
      "titleBar": "Live Chat",
      "startButton": "Start Chat",
      "welcomeText": "Welcome to Live Chatbot",
      "badge": "Chat with us!",
      "firstMessage": "Hi {{username}}, How can i help you?",
    },
    "hideRegistrationForm": false,
    "hideRatingForm": true,
    "removeChatbotBrand": false,
    "language": "en",
    "avatar": null,
    "timezone": "Asia/Kolkata"
  }
}
```

Get information about the chat bot including the name of the chat bot, appearance, text contents,language, data and timezone in JSON format.

`GET http://localhost:5000/api/v1/chatbot/:chatbotembedcode`

### Request Parameters

Parameter | Description
--------- | -----------
chatbotembedcode  | chatbot embed code

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
hideRegistrationForm  | To hide registration form
hideRatingForm  |  To hide rting form
removeChatbotBrand  |  To remove chatbot brand 
language  |  Language Type
avatar  |  To show avatar
timezone  | Timezone of chatbot

