# VaaS API Documentation

## Prerequisites
1. In order to communicate with the VaaS API, you should reach out to your account manager and request your own unique API key that is required in the header of all requests. 
2. Additionally, provide your account manager with the domain in which you will be calling the API from.

## HTTP Status Codes
| Status Code | Description |
| --- | ----------- |
| 200 | Indicates that request has succeeded. |
| 400 | You have attempted to call an endpoint with invalid data. |
| 401 | You are not authorized to execute the given endpoint. |
| 500 | The server encountered an unexpected condition which prevented it from fulfilling the request. |

## Making Requests
### Headers
Every request to the VaaS API has two require header parameters:  

| Parameter | Description |
| --- | ----------- |
|apikey| string api key |  
|environment| staging / production |

## Endpoints
Base URL: https://vaas-production.herokuapp.com/

| v1/vaccinations |
| --- |

Returns the recommneded and required vaccinations for a given country.

**Requirement parameters:**
| Parameter | Description |
| --- | ----------- |
|country| 2 letter country code i.e. US, MX |  

**Example response:**
```
{
    "country": "Mexico",
    "Vaccinations": "Recommended all: Routine vaccines, Covid-19, Hepatitis A, Hepatitis B, Measles (for infants). Most: Typhoid. Malaria is a risk in some areas.",
    "Country_ISO_Code": "MX",
    "Last_Updated": "01_03_2022"
}
```
---
| v1/travel-advisory |
| --- |

Returns the travel advisory and border information for a given country.

**Requirement parameters:**
| Parameter | Description |
| --- | ----------- |
|country| 2 letter country code i.e. US, MX |  

**Example response:**
```
{
    "country": "Mexico",
    "Travel_Advisory": "Air border open without restriction. Land borders remain closed. ",
    "Covid_Health_Form": "",
    "Country_ISO_Code": "MX"
}
```
---
| v1/visa-exemption |
| --- |

Returns the visa details for a traveller for specific country

**Requirement body parameters:**
| Body Parameter | Description |
| --- | ----------- |
|nationality| 2 letter country code i.e. US, MX |  
|destination| 2 letter country code i.e. US, MX | 

**Example response:**
```
{
    "passport_requirement_for_entry": "Your passport must be valid at least six months from the date of arrival.",
    "Visa_Required": true,
    "Visa_On_Arrival": false,
    "Visa_Online": false,
    "Travel_Authorization": "none",
    "Exemptions": "none"
}
```
---
| v1/requests|
| --- |

Returns the list of requests against the VaaS API. 

**Example response:**
```
  {
    "_id": "61e6e284423a3c0016cc195b",
    "ipAddress": "::ffff:10.1.59.123",
    "status": "success",
    "endpoint": "vaccinations",
    "apiKey": "dmnlskwenjdkjnendjnk3",
    "environment": "production",
    "duration": "0.438 seconds",
    "date": "2022-01-18T15:53:40.642Z",
    "__v": 0
  }
```
