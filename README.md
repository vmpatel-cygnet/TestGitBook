---
subtitle: |
  Version 1.0
title: iVvy API
---

# Initial page

## Contents

## Document Control

| Document No. | 1.0 |
| --- | --- |
| Effective Date | 23 July 2015 |
| Document Classification | Public |

### Revision History

| **Date** | **Change** | **Reference Section\(s\)** |
| --- | --- | --- |
| 01/May/2015 | Initial document created |  |
| 04/May/2015 | Added the inviteContacts api call to the event namespace | [inviteContacts](./#_jggqll6qze1v) |
| 05/May/2015 | Added the contact namespace | [contact](./#contact-namespace-contact) |
| 06/May/2015 | Added more options to the add/update contact | [addOrUpdateContact](./#_fy3x7ub206sd) |
| 07/May/2015 | Added the getSponsorshipList api call | [getSponsorshipList](./#_bqpu6t8zpppt) |
| 08/May/2015 | Added the createLoginToken api call | [createLoginToken](./#_w8ib4011b5sv) |
| 11/May/2015 | Added the getSpeakerList api call | [getSpeakerList](./#_f45eeivfiryz) |
| 15/May/2015 | Added the getCustomFieldDefinition api call | [getCustomFieldDefinition](./#_34le503wi213) |
| 18/May/2015 | Update the format required for dates and times | [IVVY-Date header](./#ivvy-date-optional) [Date Responses](./#dates) [ping](./#ping) [Timestamp Format](./#timestamp-format) |
| 20/May/2015 | Added the progress, repost, restart and results api calls | [progress](./#_itfy49x6c21n) [repost](./#repost) [restart](./#restart) [results](./#_4u4dtsj954o9) |
| 20/May/2015 | Added the venue namespace api calls | [Venue Namespace \(venue\)](./#venue-namespace-venue) |
| 26/May/2015 | Removed the X-Api-Version header. The version is now part of the url. |  |
| 28/May/2015 | Added the “marketplaceEventTypes” description to the sample venue api response. |  |
| 29/May/2015 | Added the marketplace namespace api calls | [Marketplace Namespace \(marketplace\)](./#marketplace-namespace-marketplace) |
| 5/June/2015 | Changed the integer values of “marketplaceEventTypes”. |  |
| 10/June/2015 | Added params, returns and throws to a lot of api calls |  |
| 18/Jun/2015 | Updates to the getContact api call | [getContact](./#getcontact) |
| 19/Jun/2015 | Added details in eventInvitations section of getContact API | [getContact](./#getcontact) |
| 24/Jun/2015 | Added more information in the getEventList api call. | [getEventList](./#geteventlist) |
| 29/Jun/2015 | Updated documentation for the getContact api call and added the invoices, currentStatus and confirmedDate properties to the eventRegistrations property | [getContact](./#getcontact) |
| 23/Jul/2015 | Updated getContact api call to return the eventStartDateTime and added a parameter to introduce sorting of the eventRegistrations and eventInvitations properties | [getContact](./#getcontact) |
| 14/Aug/2015 | Update getContact api call to return links to pdf version of invoices and tickets | [getContact](./#getcontact) |
| 30/Aug/2016 | Updated description of the ivvy headers and the string to sign to be more clear. Updated C\# example for calculating the MD5 sum. | [Signing the request](./#signing-the-request), [Calulating MD5](./#c) |
| 8/Nov/2016 | Added the enum values in the currentStatus of the event | [getEventList](./#geteventlist) |
| 06/Jun/2017 | Allow filter by [Filter](./#filtering) properties \(afterDate, beforeDate, Status\) Allow ordering results by date | [getEventList](./#geteventlist) |
| 09/Jun/2017 | Added invoice namespace. Methods available | [Invoice](./#invoice-namespace-invoice) |
| 30/Jun/2017 | Allow filter by [Filter](./#filtering) property | [getInvoiceList](./#getinvoicelist) |
|  | \(fromModifiedDate, toModifiedDate\) |  |
| 23/Aug/2017 | Added following methods to contact namespace | [getCompanyList](./#getcompanylist) |
| 24/Aug/2017 | Updated host description. | [HOST \(Required\)](./#host-required) |
| 11/Sep/2017 | Allow filter by [Filter](./#filtering) property | [getContactList](./#getcontactlist) [getCompanyList](./#getcompanylist) |
|  | \(fromModifiedDate, toModifiedDate\) |  |
| 12/Sep/2017 | Added venueId to filter of getInvoiceList action | [getInvoiceList](./#getinvoicelist) |
| 19/Sep/2017 | Updated the response data \(“include” and “display” properties\) of getEvent action | [getEvent](./#getevent) |
| 21/Sep/2017 | Added refType to filter of getInvoiceList | [getInvoiceList](./#getinvoicelist) |
|  | action |  |
| 17/Oct/2017 | - Added companies to addOrUpdateContact to update the companies while adding/updating a contact. - Updated response data of methods getContact and getContactList to return - companies \(array of ids of companies\) - externalId of the contact | [addOrUpdateContact](./#addorupdatecontact) [getContactList](./#getcontactlist) [getContact](./#getcontact) |
| 22/Nov/2017 | - Added booking reference code in getinvoiceList API | [getInvoiceList](./#getinvoicelist) |
| 16/Jan/2018 | - Added modifiedDateBefore, modifiedDateAfter filter in booking listing actions - Added eventType\(string\) in booking data | [getBookingList](./#getbookinglist) [getBookingListForAccount](./#getbookinglistforaccount) [getBooking](./#getvenueroomlist) |
| 23/Jan/2018 | - Added method to venue namespace - getVenueRoomList | [getVenueRoomList](./#getvenueroomlist) |
| 1/Feb/2018 | - Added below mentioned API’s details | [addItemsToBooking](./#additemstobooking) [addPaymentToBooking](./#addpaymenttobooking) [addRefundToBooking](./#addrefundtobooking) [addOrUpdateCostCenter](./#addorupdatecostcenter) [getCostCenterList](./#getcostcenterlist) [getTaxList](./#_88p9gk1py4a4) |
|  | 1\) addItemsToBooking 2\) addPaymentToBooking 3\) addRefundToBooking 4\) addOrUpdateCostCenter 5\) getCostCenterList - Remove getTaxList APi from invoice namespace and added the same to the Venue namespace |  |
| 5/Feb/2018 | - Added method to venue namespace - getVenueRatePlanList | [getVenueRatePlanList](./#_hgnp643z0woj) |
| 5/Mar/2018 | Removed “rev no” column from revision history. |  |
| 5/Mar/2018 | - Added action addOrUpdateEvent - Added section Timezone List | [addOrUpdateEvent](./#addorupdateevent) [Timezone List](./#timezone-list) |
| 26/Apr/2018 | - Added modifiedDate in getEventList API, | _getEventList_ |
| 9/May/2018 | - Removed “salesPriceTax” property from addItemsToBooking request - Updated descriptions for addItemsToBooking request | [addItemsToBooking](./#additemstobooking) |
| 01/June/2018 | - Added daily revenue data to getBooking - Added the fee details to “payments” section of getInvoice - Added actions “getRegistration”, “getRegistrationList”, “getAttendee”, and “getAttendeeList” to event namespace | [getBooking](./#getvenueroomlist) [getInvoice](./#getinvoice) [getRegistration](./#getregistration) [getRegistrationList](./#getregistrationlist) [getAttendee](./#getattendee) [getAttendeeList](./#getattendeelist) |
| 01/June/2018 | - Add following endpoints to event namespace getPollList | _getPollList getPoll addResponse getDiscussionList addDiscussion addQuestion_ |
|  | getPoll |  |
|  | addResponse |  |
|  | getDiscussionList |  |
|  | addDiscussion |  |
|  | addQuestion |  |
| 05/June/2018 | Add following endpoints: addOrUpdateLead addOrUpdateOpportunity convertLeadToOpportunity | _addOrUpdateLead addOrUpdateOpportunity convertLeadToOpportunity_ |

* Now returns the inviceLinkYes, inviteLinkNo and response in the eventInvitations object
* Now returns the eventCode, printTicketUrl, attendeeCount, invoiceUrl and guestDetails in the eventRegistrations object
* added eventCode parameter
* added Value and its meaning for Response Field
* Added the eventType
* Added the events timezone
* Added venue
* Added tickets
* Added information
* Added the homepageContent
* getInvoice
* getInvoiceList
* getOptions
* getCompanyList
* getCompany
* addOrUpdateCompany

## Introduction

The iVvy system is built with flexibility in mind, and this API forms a large part of that promise.

The API described in this document follows an RPC \(Remote Procedure Call\) paradigm. Each RPC method is grouped into a few higher level namespaces to help organise this document in a more logical manner.

iVvy takes security very seriously and the API described in this document has been designed to be as secure as possible.

* All transport has been secured by utilising industry standard TLS
* Key generation can be done first authenticating with the iVvy backend system
* All requests must be signed using the key/secret pair to prove the request was made by a valid key
* All requests have a time limit to avoid future replay attacks

## Obtaining Keys

Keys are defined as a pair of strings, the ‘key’ and the ‘secret’. Each request must be signed using a ‘secret’ key. There are generated from within the accounts ‘settings’ section of the website.

## Creating the request

Requests to the API are over the standard HTTP \(HyperText Transfer Protocol\). The protocol defines three parts to every request

1. the method/uri header
2. a number of request headers
3. optional body of the request

Note also that the HTTP request also needs to be secured by a TLS/SSL connection, often referred to as HTTPS \(or HTTP over SSL\). iVvy uses industry standard TLS \(Transport Layer Security, the successor to SSL, Secure Sockets Layer\) to secure the HTTP transport to the API to ensure eavesdropping on the connection by third parties is protected.

### Method/URI Header

This is a line consisting of the method of the request, followed by the request URI, followed by the HTTP version. i.e.

> POST /api/1.0/event?action=getEventList HTTP/1.0

This example is for a request, to iVvy’s api ‘event’ namespace, calling the ‘getEventList’ API call, using HTTP version 1.0. Note the HTTP method for calls to the iVvy API are all POST requests. The api version being called is 1.0. Currently supported versions are:

* 1.0

The URI in the request must always start with /api/{version} \(where {version} is the specific api version, e.g. 1.0\) followed by the namespace of the eventual api call to make. All requests must also provide the action parameter indicating the API call to invoke.

### Request Headers

Request headers are defined by the header name, followed by a colon \(:\) followed by a space, followed by the value of the header. A number of headers are used with the iVvy API

#### Standard Headers

**HOST \(Required\)**

This determines the host that is used for the request. This value is required and should be set to one of the following:

* api.ap-southeast-2.ivvy.com
* api.us-west-2.ivvy.com
* api.eu-west-2.ivvy.com

Contact [support@ivvy.com](mailto:support@ivvy.com) if you are unsure which value to use.

> HOST: api.ap-southeast-2.ivvy.com

**Date \(Required unless using IVVY-Date header\)**

The date header determines the date the request was made. The iVvy API uses this date, compared to the date of the server to determine if the request is within the time to live setting. \(Currently requests over 5 minutes old are deemed invalid, this value may change in the future.\)

> Date: Thu, 12 Apr 2012 07:17:06 UTC

**Content-MD5 \(Required\)**

This is the md5 sum of the body of the request. This header is used to verify the contents of the body of the request have not been altered during transport. Note that if there is no content in the body, the MD5 for the request must still be calculated. See [Calculating MD5](./#calculating-md5) for more details on how to calculate the value for this field.

**Content-Type**

The content type of the request body. Valid request types for the api are...

* application/json

**Content-Length**

The length of the request body, in bytes.

#### Custom Headers

A number of custom headers can be used with the request to the API.

**IVVY-Date \(Optional\)**

If your HTTP client does not allow the date header to be accessed or set, you can optionally use this header to use for the date string. Note if this header is used, the ‘date’ part of the [signed string](./#signing-the-request) will need to be empty. The format of the value of this header will be the [iVvy Timestamp Format](./#timestamp-format), NOT the string format of the standard Date header.

**X-Api-Authorization \(Required\)**

This is the same format at the standard HTTP Authorization header. For iVvy requests, the format is...

> X-Api-Authorization: IWS key:signature

… where IWS is the authentication system used by iVvy, key is the key used to sign the request, and the signature is the HMAC-SHA1 signature of the request. See [Signing the request](./#signing-the-request) for details on how to sign a request.

The iVvy API server will lookup the secret key associated with the key used in this header, then use the details in the request in association with the secret key, then reconstruct the [HMAC-SHA1](./#hmac-sha1) hash. Only when the calculated hash, and the signature sent through this header match will the request be authenticated.

### Signing the request

Every request to the API must be signed with the accounts or users API key. Signing the request is obtained by the following pseudo-code:

```php
method := POST
contentMd5 := md5(\)
contentType := the value of the Content-Type header
contentSign := {contentMd5}{contentType}
date := the date header of the request (i.e. Tue, 03 Apr, 2012 22:23:24 utc)
NOTE: if using the 
IVVY-Date
 header, this field will be empty
requestString := the entire request string used in the request
apiVersion := the api version to use
ivvyHeaders := Concatenated string of all headers starting with IVVY, removing all the
Dashes (-) and underscore (_) characters in the header, in alphabetical order, joined together with the
ampersand (&) character
initialStringToSign := {method}{contentSign}{date}{requestString}{apiVersion}{ivvyHeaders}
stringToSign := lowercase version of the initialStringToSign
```

For example, the following request...

> `POST /api/1.0/test?action=ping HTTP/1.0`
>
> `Host: api.ap-southeast-2.ivvy.com`
>
> `Date: Tue, 03 Apr 2012 22:23:24 UTC`
>
> `Content-MD5: a09f600c77a6dbd947db24c61e8935ca`
>
> `Content-Type: application/json`
>
> `Content-Length: 18`
>
> `X-Api-Version: 1.0`
>
> `X-Api-Authorization: IWS {key:signature here}`
>
> `IVVY-Date: 2012-04-03 22:23:24`
>
> `{"example":"body"}`

… will require the following string to be signed …

> `posta09f600c77a6dbd947db24c61e8935caapplication/json/api/1.0/test?action=ping1.0ivvydate=2012-04-03 22:23:24`

Note the entire string is set to lowercase before signing.

Signing is achieved using the HMAC algorithm, using SHA1 encryption. See [HMAC-SHA1](./#hmac-sha1) for further details

### Query Parameters

The api exposes a RPC interface. As such there is a required query parameter, the ‘action’ parameter. This will identify the RPC call to invoke.

## Interpreting the response

The response will be given back will be the response in [JSON](./#json-encoding) format.

#### Collections

Some results return collections of objects. E.g. event?action=getEventList. The resulting [JSON](./#json-encoding) response for these collections will be an object with the following properties.

* meta: An object providing information about the result set. The following keys may exist
  * totalResults: The number of results in the complete collection
  * start: The starting index of the collection this result represents
  * perPage: The number of items per page of results
  * count: The number of objects included in this result.
* results: An array of objects

#### Pagination

Some requests \(mostly the requests that return [collections](./#collections)\) may also accept some pagination options.

* perPage: The number of items to return per page. Note that most requests have a cap on this number and providing a perPage option greater than that cap will not have any effect.
* start: The record to start paging from. Note this number is zero based, i.e. to return results from the very first result, the start will need to equal 0 \(which is the default\). Note also this is not the page to start at. For example to get the second page from a list of results that have 20 results per page, the start property will need to equal 20 \(i.e. starting at the 21st result\)

#### Filtering

Some requests \(mostly requests that return [collections](./#collections) and/or take [pagination](./#pagination) requests\) may also accept a filter argument. The structure of this filter will be an object with the key’s being what needs to be filtered, and the value will be the content of the filter.

There are a number of options that may modify the filter behaviour. These are appended to the end of the key to filter. The accepted modifiers are:

* **\_\_CONTAINS**: Return the results that contain the value.
* **\_\_NOTCONTAINS**: Return the results that do not contain the value.
* **\_\_BEGINS**: Return the results that start with the value.
* **\_\_ENDS**: Return the results that end with the value.
* **\_\_LESSTHAN**: Return the results that are less than or equal to the value.
* **\_\_GREATERTHAN**: Return the results that are greater than or equal to the value.
* **\_\_NOT**: Return the results that are not equal to the value.
* **\_\_EMPTY**: Returns results that are empty

If you want to search for ‘Null’ values, you can use the special value ‘**\_**_**ISNULL**_**\_**’ for the filter value.

**Example: Filter all the results where the firstName = Bob**

> {"filter":{"firstName":"Bob"}}

**Example: Filter all results where the firstName starts with ‘M’**

> {"filter":{"firstName\_\_BEGINS":"M"}}

**Example: Filter all results where the birthDay has not been set**

> {"filter":{"firstName":"**ISNULL**"}}

#### Exceptions

If an error occurred the response will be a [JSON](./#json-encoding) representation of what went wrong. This will provide the error code, a brief message as well as a specific code. The specific code is a useful piece of information to be provided in any bug reports.

Current exception codes and meanings are:

400: Bad Request

401: Unauthorized

403: Forbidden

404: Not Found

405: Method Not Allowed

406: Not Acceptable

429: Too Many Requests

460: Unknown

461: Failed Request

462: Session Expired

463: Key Revoked

500: Internal Server Error

501: Not Implemented

Some exceptions will have an additional piece of information associated with the exception, which will contain more specific message about the exception.

**Exception: Specific Code 23016**

A parameter provided in the request did not validate correctly. For example, the API might have been expecting a number, but a string was provided instead. This exception gets thrown when the first invalid parameter is found.

The additional messages will contain the messages from the validator as to why the value was not validated.

**Example: Key does not validate error**

**Request \(contact?action=getContact\):**

```javascript
{"id":"wrong"}
```

**Response:**

```javascript
{
"errorCode":400,
"message":"'id' does not validate",
"specificCode":23016,
"additionalMessages":["Value must be a whole number"]
}
```

**Exception: Specific Code 23017**

A required parameter was missing from the request.

**Example: Key is required error**

**Request \(contact?action=getContact\):**

> {}

**Response:**

```javascript
{"errorCode":400,"message":"'id' is required","specificCode":23017}
```

#### Response Headers

**Content-Type**

This header will identify the content type of the response. At this time only one content type is supported, the application/json type.

#### Dates

Responses from the iVvy API may contain dates. In all cases \(unless otherwise stated in documentation for the specific action\) the dates are in Universal Coordinated Time \(UTC\). Care must be taken when using or displaying these dates to ensure they: a\) maintain their UTC time zone for communication with the API, and; b\) represented in the appropriate time zone for users utilizing the date.

Dates may be represented as a string which must be parsed appropriately if it is to be used. Where possible any dates will be converted to the [iVvy Timestamp Format](./#timestamp-format), which is a simple to understand text format to represent a specific point in time to the second.

## API

There are a few things to note as per the structure of the API.

### Namespaces

The API is segmented into various namespaces. The support namespaces for the API are…

* batch
* event
* Test
* invoice

### Actions

Within each namespace will be a set of actions that can be performed via API calls. These behave like RPC calls. Each action is unique within the namespace. When calling the API both the namespace and the action must be provided in the following URI format…

/api/{version}/{namespace}?action={action}

i.e.

/api/1.0/batch?action=run

Each action may require some extra parameters as part of the call. These are provided in the BODY of the request as a JSON encoded object. The specifics for each call are outlined in this document.

Batch Namespace (batch)
-----------------------

As a way of providing asynchronous access to iVvy’s API, there is a namespace
added for batch requests. This also provides a way to run multiple api calls in
a batch and provide the result of all the api calls via a URL callback.

### run

**Parameters**

| jobs        | Array of api jobs to be run on the api. Each job needs to have the following keys:                   | Required |
|-------------|------------------------------------------------------------------------------------------------------|----------|
| callbackUrl | The URL to hit with a POST request after the batch has been run, with a JSON object of the responses | Required |

-   namespace

-   action

-   params

**Returns**

| asyncId | Identifier for the batch request |
|---------|----------------------------------|


**Throws**

| Specific Code: 24092 | Incorrect Job Format          |
|----------------------|-------------------------------|
| Specific Code: 24093 | Empty job parameter found     |
| Specific Code: 24091 | The information was not saved |

The run action takes an array of api calls and returns an identifier that can be
used to identify the batch. Keep this identifier as it can be used to identify
the response of the batch request, as well as being used to fetch the progress
and results of the request.

To run a batch job, an JSON object must be provided with the following keys:

-   jobs: An array of jobs, each element being an object with the following keys

    -   namespace: The namespace of the api call

    -   action: The api call to make

    -   params: Any parameters required for the api call

-   callbackUrl: A URL that will be called after the batch has completed.

    -   The request will be a POST request

    -   The response will be a JSON object with the following keys

        -   asyncId: The async identifier provided when the batch was created

        -   results: An array of objects for each result of the batch, with the
            following keys

            -   namespace: The namespace of the call for the response

            -   action: The action of of the call for the response

            -   request: The original request parameters used

            -   response: The response of the api call

#### Example: Run a batch job inviting some contacts to different events

**Request:**

>   {"jobs":[{"namespace":"event",”action:"inviteContacts","params":{"event":1,"contacts":[1,2,3]}},{"namespace":"event",”action:"inviteContacts","params":{"event":2,"contacts":[1,2,4]}},],"callbackUrl":"<http://example.callback.url.com>"}

**Response:**

>   {"asyncId":"e35e06ee592d17a42dc9e6252a058617"}

### progress

**Parameters**

| async | The asyncId for the batch job to check progress for | Required |
|-------|-----------------------------------------------------|----------|


**Returns**

| progress | The progress of the batch job, as a percentage of work completed. |
|----------|-------------------------------------------------------------------|


**Throws**

| Specific Code: 24105 | Could not find batch |
|----------------------|----------------------|


The progress action takes the asyncId as a parameter and returns back the
progress of the batch job as a percentage

#### Example: Fetch the progress of a batch job

**Request:**

>   {"async":"a7ec88af7d710bf51b188004bb532d77"}

**Response:**

>   {"progress":33}
