---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - php

toc_footers:
  - <a href='https://customer.roamler.com/#/settings'>Sign Up for an API Key</a>

includes:

search: true
---

# Introduction

Intro stuff

Get your key at [Roamler Customer Portal](https://github.com/lord/slate).

# Authentication

Roamler uses API keys to allow access to the API. You can register a new API key at our [customer portal](https://customer.roamler.com/#/settings). There are two ways to authenticate your API calls.

## Authenticate via URL
> To authorize a call via the url, use this code:

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/Jobs?apiKey=MY_API_KEY",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "X-Roamler-Api-Key: MY_API_KEY",
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```

You can add `apiKey` to the url parameters to authenticate API calls.

Example: 
<code>https://api-customer.roamler.com/v1/Jobs?apiKey=MY_API_KEY</code>

## Authenticate via header

> To authorize a call via a header, use this code:

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/Jobs",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```

You can add `X-Roamler-Api-Key` to your request headers to authenticate API calls.

Example:
<code>X-Roamler-Api-Key: MY_API_KEY</code>

# Webhook

> The webhook returns JSON structured like this:

```json
{
  "Id": "3354h3n436879257n2463",
  "Attempt": 1,
  "Properties": {},
  "Notifications": [
    ...
    {
      "Action": "submission-completed",
      "title": "string",
      "date": "datetime",
      "url": "url",
      "jobUrl": "url"
    }
    ...
  ]
}
```

Webhook description

Configure a webhook via our [customer portal](https://customer.roamler.com/#/settings).

# Jobs

## Get all jobs

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/Jobs",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "X-Roamler-Api-Key: MY_API_KEY",
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```


> The above command returns JSON structured like this:

```json
[
 ...
  {
    "hRef": "string",
    "id": 0,
    "title": "string",
    "description": "string",
    "liveDate": "datetime",
    "closeDate": "datettime",
    "isActive": true,
    "questions": [
      {
        "hRef": "string",
        "id": 0,
        "code": "string",
        "questionType": "None",
        "text": "string",
        "isOptional": true,
        "answerOptions": [
          {
            "id": 0,
            "text": "string",
            "code": "string"
          }
        ],
        "imageHash": "string"
      }
    ],
    "attributeDefinitions": [
      {
        "name": "string",
        "id": 0,
        "type": "Unknown",
        "options": [
          {
            "id": 0,
            "value": "string"
          }
        ]
      }
    ]
  }
 ...
]
```

This endpoint retrieves all jobs.

### HTTP Request

`GET /v1/Jobs/`

### URL Parameters

Parameter | Default value | Required | Description| Parameter Type| Data Type
--------- | ------- | ------- | ------- | ------- | -----------
page | 0 | No | I really don't know [TODO] | Query | Integer

## Get a specific job

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/Jobs/{JobId}",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "X-Roamler-Api-Key: MY_API_KEY",
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```


> The above command returns JSON structured like this:

```json
{
  "hRef": "string",
  "id": 0,
  "title": "string",
  "description": "string",
  "liveDate": "datetime",
  "closeDate": "datetime",
  "isActive": true,
  "questions": [
    {
      "hRef": "string",
      "id": 0,
      "code": "string",
      "questionType": "None",
      "text": "string",
      "isOptional": true,
      "answerOptions": [
        {
          "id": 0,
          "text": "string",
          "code": "string"
        }
      ],
      "imageHash": "string"
    }
  ],
  "attributeDefinitions": [
    {
      "name": "string",
      "id": 0,
      "type": "Unknown",
      "options": [
        {
          "id": 0,
          "value": "string"
        }
      ]
    }
  ]
}
```

This endpoint retrieves a specific job.

### HTTP Request

`GET /v1/Jobs/{JobId}`

### URL Parameters

Parameter | Default value | Required | Description| Parameter Type| Data Type
--------- | ------- | ------- | ------- | ------- | -----------
JobId | null | Yes | Id of the job | Path | Integer

## Get locations of a job

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/Jobs/{JobId}/Locations",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "X-Roamler-Api-Key: MY_API_KEY",
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```

> The above command returns JSON structured like this:

```json
[
 ...
  {
    "id": 0,
    "address": "string",
    "longitude": 0,
    "latitude": 0,
    "attributes": [
      {
        "name": "string",
        "attributeDefinitionId": 0,
        "type": "Unknown",
        "value": 0,
        "text": "string"
      }
    ]
  }
 ...
]
```

This endpoint retrieves locations for a specific job. You'll get all locations that are specified by Roamler for this job.

### HTTP Request

`GET /v1/Jobs/{JobId}/Locations`

### URL Parameters

Parameter | Default value | Required | Description| Parameter Type| Data Type
--------- | ------- | ------- | ------- | ------- | -----------
JobId | null | Yes | Id of the job | Path | Integer
showCustomerAvailableAttributes | false | No | Indicates if you want to see available location attributes | Query | Boolean

## Get submissions of a job

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/Jobs/{JobId}/Submissions?fromDate=2017-12-01&toDate=2017-12-31",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "X-Roamler-Api-Key: MY_API_KEY",
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```

> The above command returns JSON structured like this:

```json
[
 ...
  {
    "hRef": "string",
    "submitDate": "2017-12-18T09:44:49.342Z"
  }
 ...
]
```

This endpoint retrieves submission urls for a specific job.

### HTTP Request

`GET /v1/Jobs/{JobId}/Submissions`

### URL Parameters

Parameter | Default value | Required | Description| Parameter Type| Data Type
--------- | ------- | ------- | ------- | ------- | -----------
JobId | null | Yes | Id of the job | Path | Integer
fromDate | null | Yes | The start datetime of the timeframe you want to query for submissions | Query | Datetime
fromDate | null | Yes | The end datetime of the timeframe you want to query for submissions | Query | Datetime
page | 1 | No | The page of results you need | Query | Integer
take | 50 | No | The amount of submissions per page (max 1000) | Query | Integer

# Submissions

## Get a submission

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/submissions/{submissionId}",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "X-Roamler-Api-Key: MY_API_KEY",
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```


> The above command returns JSON structured like this:

```json
{
  "hRef": "string",
  "jobHRef": "string",
  "id": 0,
  "jobTitle": "string",
  "location": {
    "id": 0,
    "address": "string",
    "longitude": 0,
    "latitude": 0,
    "attributes": [
      {
        "name": "string",
        "attributeDefinitionId": 0,
        "type": "Unknown",
        "value": 0,
        "text": "string"
      }
    ]
  },
  "submissionDate": "datetime",
  "questions": [
    {
      "hRef": "string",
      "id": 0,
      "code": "string",
      "questionType": "None",
      "text": "string",
      "isOptional": true,
      "answerOptions": [
        {
          "id": 0,
          "text": "string",
          "code": "string"
        }
      ],
      "imageHash": "string"
    }
  ],
  "answers": [
    {
      "questionId": 0,
      "value": 0,
      "answerOptions": [
        {
          "id": 0,
          "text": "string",
          "code": "string"
        }
      ],
      "text": "string",
      "latitude": 0,
      "longitude": 0,
      "accuracy": 0,
      "userAnswerId": 0,
      "photoUrl": "string",
      "answerDate": "datetime"
    }
  ],
  "submissionSharing": {
    "isShared": true,
    "publicLink": "string"
  },
  "data": {
    "location": {}
  }
}
```

This endpoint retrieves a single submission. Most of the times you don't have to generate this url yourself. The webhook and the `/v1/Jobs/{JobId}/Submissions` will return the preformatted url to you in the `href` field. However, you may want to add some url parameters to get specific information in the response.

### HTTP Request

`GET /v1/submissions/{submissionId}`

### URL Parameters

Parameter | Default value | Required | Description| Parameter Type| Data Type
--------- | ------- | ------- | ------- | ------- | -----------
submissionId | null | Yes | The id of the submission | Path | Integer
includeAnswers | true | No | Indicating if you want to get the answers | Query | Integer
showCustomerAvailableAttributes | true | No | Indicates if you want to get task attributes | Query | Integer
includeQuestions | false | No | Indicates if you want to get the questions of the job | Query | Integer

## Get a photo

```php
<?php
	$curl = curl_init();

	curl_setopt_array($curl, array(
	  CURLOPT_URL => "https://api-customer.roamler.com/v1/submissions/{submissionId}/image/{photoId}",
	  CURLOPT_RETURNTRANSFER => true,
	  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	  CURLOPT_CUSTOMREQUEST => "GET",
	  CURLOPT_HTTPHEADER => array(
	    "X-Roamler-Api-Key: MY_API_KEY",
	    "content-type: application/json"
	  )
	));
		
	$response = curl_exec($curl);
	$error = curl_error($curl);
	
	curl_close($curl);
?>
```

This endpoint retrieves a photo.

### HTTP Request

`GET /v1/submissions/{submissionId}/image/{photoId}`

### URL Parameters

Parameter | Default value | Required | Description| Parameter Type| Data Type
--------- | ------- | ------- | ------- | ------- | -----------
submissionId | null | Yes | The id of the submission | Path | Integer
photoId | null | Yes | The id of the submission | Path | Integer