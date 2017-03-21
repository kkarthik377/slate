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
failedIntent |   Failed intent is determined by the confidence score that we recieve from each response of the Watson.The range of the confidence score is between 0 to 1.When the confidence score is below or equal to 0.5 then it is determined as failed intent.
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
  "status": "success",
  "data": {
    "intentsReport": [
      {
        "total": 14,
        "intent": "verkeerde_product_wrong_and_exchange"
      },
      {
        "total": 8,
        "intent": "capabilities"
      },
      {
        "total": 7,
        "intent": "greeting"
      },
      {
        "total": 7,
        "intent": "verkeerde_product_wrong"
      },
      {
        "total": 7,
        "intent": "null"
      }
    ]
  }
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
total  | Total count of particular intent 
intent  | Intent type 

## Success Intent Report

```shell
curl -X GET 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImNsaWuVudElkIjoiNThhZDI3ZDYwNjc5NTBlN2I3MGVhMGQyIiwiZW1haWwiOixJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5MjI1MzIyfQ.a7f6mgB2kp8KyyRdk6SkvE1vbS43FVBcvol5JWzbGGESBY" 
```
> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "successIntents": [
      {
        "intent": "yes",
        "confidence": 0.99,
        "output": "Ik weet het niet zeker. Je kunt dingen vragen als \"is de levering gratis\" of \"de beschikbaarheid van de winkel\", etc .... \"",
        "input": "ja"
      },
      {
        "intent": "No",
        "confidence": 0.9359049201011658,
        "output": "Ik weet het niet zeker. Je kunt dingen vragen als \"is de levering gratis\" of \"de beschikbaarheid van de winkel\", etc .... \"",
        "input": "Nee, ik ben niet tevreden"
      },
      {
        "intent": "yes",
        "confidence": 0.99,
        "output": "dank u voor het contacteren van ZEB",
        "input": "yes"
      }
    ]
  }
}
```
`GET http://localhost:5000/api/v1/reports/successintents?endDate=:EndDate&startDate=:StartDate`

Success intent reports API provides the list of used success intents.

You can set limits to get the list of most frequently used success intents and can also date range to filter the data.

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
intent  | Intent text
confidence  | Success intent confidence level
input  | Input text
output  | Output text

## Failure Intent Report

```shell
curl -X GET 
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImNsaWuVudElkIjoiNThhZDI3ZDYwNjc5NTBlN2I3MGVhMGQyIiwiZW1haWwiOixJtYWFydGVuQGNsZXZlci5iZSIsImF2YXRhciI6bnVsbCwiZ2VuZGVyIjoiTSIsInJvbGUiOiJTVVBFUkFETUlOIiwiZnVsbE5hbWUiOiJNYWFydGVuIFZlcnNjaHVlcmUiLCJ1c2VySWQiOiI1OGFkMjkzYjA2Nzk1MGU3YjcwZWEwZDMifSwiaWF0IjoxNDg5MjI1MzIyfQ.a7f6mgB2kp8KyyRdk6SkvE1vbS43FVBcvol5JWzbGGESBY" 
```
> The above request returns JSON structured like this:

```json
{
  "status": "success",
  "data": {
    "failureIntents": [
      {
        "intent": "goodbyes",
        "confidence": 0.20787838101387024,
        "output": "geen enkel probleem! Kan ik verder nog iets voor je doen?",
        "input": "welcome"
      },
      {
        "intent": "null",
        "confidence": 0.30756891,
        "output": "Ik weet het niet zeker. Je kunt dingen vragen als \"is de levering gratis\" of \"de beschikbaarheid van de winkel\", etc .... \"",
        "input": "ne"
      },
      {
        "intent": "null",
        "confidence": 0,
        "output": "Ik weet het niet zeker. Je kunt dingen vragen als \"is de levering gratis\" of \"de beschikbaarheid van de winkel\", etc .... \"",
        "input": "hi"
      }
    ]
  }
}
```
`GET http://localhost:5000/api/v1/reports/failureintents?endDate=:EndDate&startDate=:StartDate`

Failure intent reports API provides the list of used failure intents.

You can set limits to get the list of most frequently used failure intents and can also date range to filter the data.

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
intent  | Intent text
confidence  | Failure intent confidence level
input  | Input text
output  | Output text