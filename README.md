# VaaS API Documentation
Last updated: 3/14/2022  
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
---
| v1/requirements |
| --- |

Returns the visa requirements

**Requirement body parameters:**
| Body Parameter | Description |
| --- | ----------- |
|location| 2 letter country code i.e. US, MX |  
|destination| 2 letter country code i.e. US, MX | 
|type| tourist / business | 

**Example response:**
```
{
    "ISO_Code": "AF_Tourist",
    "Requirements": "Passport and a copy of passport biopage, a visa form, passport-style photo, ID card (resident card if not a US citizen), proof of employment, proof of address (bill or bank statement), letter of invitation or hotel reservation, cover-letter, and filing fees (www.afghanembassy.us/visa/).",
    "Procedures": "You can apply by mail or in person with an appointment. Mail-in applications must be notarized prior to submission. You can request expedited service for an additional $50. Fees are paid by Money Order, payable to the consulate where you are submitting the application. You must also include a prepaid envelope for the return of your passport. Processing time is approximately 7-10 business days.",
    "Contacts": "Embassy of Afghanistan in Washington, DC\nAddress: 2341 Wyoming Ave, NW\nWashington, DC 20008\nTél.: (+1) 202-483-6410\nFax: (+1) 202-483-6488\nEmail: info@embassyofafghanistan.org; Consular: consulate@embassyofafghanistan.org\nWeb: www.embassyofafghanistan.org\n\nConsulate General of Afghanistan in New York\nAddress: 241-02 Northern Blvd. 3rd Floor\nLittle Neck, NY 11362\nTél.: (+1) 212 972 2276\nFax: (+1) 718 279 9046\nEmail: visa.new york@mfa.af; info.newyork@mfa.af\nWeb: https://www.newyork.mfa.af/the-general-consulate/contact-us.html\n\nConsulate General of Afghanistan in Los Angeles\nAddress: 120 South Doheny Drive\nBeverly Hills, CA 90211\nTél.: (+1) 310-288-8334\nFax: (+1) 310-288-8355\nEmail: Question_la@afghanconsulategeneral.org\nWeb: www.afghanconsulategeneral.org",
    "Filing_Tips": "Best Practices for Submitting a Visa Application:\n\n1.        Passport:  Have a valid biometric passport, usually with at least six months of validity remaining, and with free space for visas, usually at least two blank visa pages. If you are not a citizen of the country from which you are applying, you should also submit proof of your residency in the country. This proof may be a work visa, a residence permit, or a long-stay visa. Normally short-term visas like tourist and business visas are not permitted as proof.\n\n2.        Application:  Fill out the electronic/paper visa application form completely, and it must be signed by the applicant.  However, if the applicant is a minor (younger than 18), the parents (or custodial parent) may sign the application on behalf of the minor child. If the child is traveling alone or with only one parent, a minor consent form is normally required by the consulate in order for a visa to be issued.  Some consulates may require an affidavit in lieu of the form, so check the consulate links or contact the consulate if you need a visa for a minor. \n\n3.        Photo: This is usually referred to as a passport-sized photo, even if the consulates provide varying dimensions for the photos. \n\n4.        Letter of support/letter of invitation: This is a letter you or your sponsor write to the consulate requesting the visa you seek, providing details about yourself, your sponsor (if applicable), the purpose of your visit, your time frame, and arrangements you have made. Some countries require that this letter be notarized with a copy of the ID of the sponsor\n\n5.        Proof of sufficient funds: This may include a letter of employment showing you are employed, a copy of your bank statement, an affidavit from your local sponsor guaranteeing your funds for your stay, proof of assets or any other sources of funding to show that you will be accounted for financially during your stay. \n\n6.        Police Reports: The requirements for a police report usually means an FBI report in the US.  FBI reports are obtained through one of the vendors accredited by the FBI to conduct the report: https://www.fbi.gov/services/cjis/compact-council/list-of-approved-channelers.  For other countries, please confirm report requirements with the embassy or consulate before your submission. \n\n7.        Other official documents: Birth certificates and marriage certificates are usually submitted if your spouse and children are seeking a visa based on your approved application, or if you are applying as a family.  Copies of the certificates must normally be certified. Additionally, if the documents are not in one of the official languages of the country to which you are traveling, they must also contain a certified translation into the country’s language. A document in English or translated into English is usually acceptable, unless specifically indicated in the filing procedures. \n\n8.        All required documents, other than identity documents or passports, such as letters of invitation, bank statements, police reports, medical examinations, and proof of medical insurance, must have an issue date not later than three months from the date of your visa application.  \n\n9.        For filing fees, and as good practice, please check the links provided for the embassy or consulate in your jurisdiction to review the detailed requirements and, if necessary, to contact the embassy or consulate. \n\n10.        During the pandemic, many embassies and consulates have reduced their work hours or adopted contactless submission methods. Be sure to contact the embassy or consulate about their preferred submission procedures prior to submitting your visa application. \n",
    "forms": [
        "https://drive.google.com/uc?id=1AExSwAPsTbCUpD4opNH9O9rb6jRbpCkf&export=download"
    ]
}
```
