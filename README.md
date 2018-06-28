>   **iVvy API**

>   *Version 1.0*

>   1

>   **Contents**

>   [Contents](#page2)

>   [Document Control](#page6)

>   [Revision History](#page6)

>   [Introduction](#page10)

>   [Obtaining Keys](#page11)

>   [Creating the request](#page11)

>   [Method/URI Header](#page11)

>   [Request Headers](#page11)

>   [Standard Headers](#page12)

>   [HOST (Required)](#page12)

>   [Date (Required unless using IVVY-Date header)](#page12)

>   [Content-MD5 (Required)](#page12)

>   [Content-Type](#page12)

>   [Content-Length](#page12)

>   [Custom Headers](#page12)

>   [IVVY-Date (Optional)](#page12)

>   [X-Api-Authorization (Required)](#page13)

>   [Signing the request](#page13)

>   [Query Parameters](#page14)

>   [Interpreting the response](#page14)

>   [Collections](#page14)

>   [Pagination](#page14)

>   [Filtering](#page15)

>   [Example: Filter all the results where the firstName = Bob](#page15)

>   [Example: Filter all results where the firstName starts with ‘M’](#page15)

>   [Example: Filter all results where the birthDay has not been set](#page15)
>   [Exceptions](#page15)

>   [Exception: Specific Code 23016](#page16)

>   [Example: Key does not validate error](#page16)

>   [Exception: Specific Code 23017](#page16)

>   [Example: Key is required error](#page16)

>   [Response Headers](#page16)

>   [Content-Type](#page16)

>   2

>   [Dates](#page17)

>   [API](#page18)

>   [Namespaces](#page18)

>   [Actions](#page18)

>   [Batch Namespace (batch)](#page18)

>   [run](#page18)

>   [Example: Run a batch job inviting some contacts to different
>   events](#page19) [progress](#page20)

>   [Example: Fetch the progress of a batch job](#page20)

>   [restart](#page20)

>   [Example: Restart a batch job](#page20)

>   [repost](#page20)

>   [Example: Restart a batch job](#page20)

>   [results](#page21)

>   [Example: Get the result of a batch job](#page21)

>   [Contact Namespace (contact)](#page21)

>   [getContactList](#page21)

>   [getContact](#page22)

>   [Example: Get a specific contact](#page26)

>   [addOrUpdateContact](#page26)

>   [Example: Adding a contact](#page27)

>   [Example: Updating a contact](#page28)

>   [getCustomFieldDefinition](#page28)

>   [getSubscriptionGroupList](#page29)

>   [addContactsToSubscriptionGroup](#page29)

>   [Example: Add 4 contacts to subscription group 2481](#page30)

>   [removeContactsFromSubscriptionGroup](#page30)

>   [getCompanyList](#page30)

>   [getCompany](#page31)

>   [Example: Get a specific company](#page33)

>   [addOrUpdateCompany](#page33)

>   [Example: Adding a company](#page34)

>   [Example: Updating a company](#page34)

>   [Event Namespace (event)](#page35)

>   [addOrUpdateEvent](#page35)

>   [getEventList](#page37)

>   [getEvent](#page40)

>   [getRegistration](#page42)

>   3

>   [getRegistrationList](#page42)

>   [getAttendee](#page43)

>   [getAttendeeList](#page45)

>   [inviteContacts](#page46)

>   [Example: Invite contacts with identifiers 1, 2 and 3 to event with
>   the](#page47) [identifier 4](#page47)

>   [getSponsorshipList](#page47)

>   [Example: Fetch the list of sponsors on an event](#page48)
>   [getSpeakerList](#page48)

>   [Example: Fetch the list of speakers at an event](#page49)
>   [createLoginToken](#page49)

>   [Example: Request a login token for a contact on an event](#page50) [Test
>   Namespace (test)](#page50)

>   [ping](#page50)

>   [Venue Namespace (venue)](#page50)

>   [getVenueList](#page50)

>   [getVenue](#page50)

>   [Example: Get a specific venue](#page51)

>   [getBookingList](#page57)

>   [Example: Get a specific venue’s Booking List](#page57)
>   [getBookingListForAccount](#page58)

>   [Example: Get Account’s Booking List](#page58)

>   [getBooking](#page59)

>   [Example: Get a specific Booking](#page59)

>   [getVenueRoomList](#page61)

>   [Example: Get a specific Venue’s Room List](#page61)

>   [getVenueRatePlanList](#page61)

>   [Example: Get a specific Venue’s Rate Plan List](#page62)
>   [addItemsToBooking](#page62)

>   [Example: Add items to booking](#page64)

>   [addPaymentToBooking](#page65)

>   [Example: Add payment to booking](#page66)

>   [addRefundToBooking](#page67)

>   [Example: Add refund to booking](#page68)

>   [getTaxList](#page68)

>   [Example: Get Venues Tax List](#page68)

>   [Marketplace Namespace (marketplace)](#page69)

>   [getVenueList](#page69)

>   [getVenue](#page71)

>   4

>   [Invoice Namespace (invoice)](#page77)

>   [getInvoiceList](#page77)

>   [getInvoice](#page80)

>   [getOptions](#page83)

>   [Account Namespace (account)](#page83)

>   [addOrUpdateCostCenter](#page83)

>   [Example: Add a cost center to an account](#page84)

>   [getCostCenterList](#page84)

>   [Example: get cost center list of the account](#page85)

>   *Example: Get a specific account’s Email Logs List*

>   [Appendix A: Algorithms/Code](#page88)

>   [Calculating MD5](#page88)

>   [Bash (Linux Command Line)](#page88)

>   [C\#](#page89)

>   [Java](#page89)

>   [Javascript](#page89)

>   [Nodejs](#page89)

>   [Objective-C](#page90)

>   [PHP](#page90)

>   [HMAC-SHA1](#page90)

>   [Bash](#page90)

>   [C\#](#page90)

>   [Javascript](#page91)

>   [NodeJS](#page91)

>   [Objective-C](#page91)

>   [PHP](#page92)

>   [Ruby](#page92)

>   [JSON Encoding](#page92)

>   [Timestamp Format](#page92)

>   [Date Format](#page93)

>   [URLEncoding](#page93)

>   [Timezone List](#page93)

>   5

>   **Document Control**

| Document No.            | 1.0          |
|-------------------------|--------------|
|                         |              |
| Effective Date          | 23 July 2015 |
|                         |              |
| Document Classification | Public       |
|                         |              |

>   **Revision History**

| **Date**     | **Change**                                      |                                    | **Reference Section(s)**           |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|--------------|-------------------------------------------------|------------------------------------|------------------------------------|--------------------------|---------------------------|---|---|---|---|---|---|---|---|---|---|---|---|---|
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 01/May/2015  | Initial document created                        |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 04/May/2015  | Added the inviteContacts api call to the        |                                    | inviteContacts                     |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | event namespace                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 05/May/2015  | Added the contact namespace                     |                                    | [contact](#page21)                 |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 06/May/2015  | Added more options to the add/update            |                                    | addOrUpdateContact                 |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | contact                                         |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 07/May/2015  | Added the getSponsorshipList api call           |                                    | getSponsorshipList                 |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 08/May/2015  | Added the createLoginToken api call             |                                    | createLoginToken                   |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 11/May/2015  | Added the getSpeakerList api call               |                                    | getSpeakerList                     |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 15/May/2015  | Added the getCustomFieldDefinition api          |                                    | getCustomFieldDefinition           |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | call                                            |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 18/May/2015  | Update the format required for dates and        |                                    | [IVVY-Date header](#page12)        |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | times                                           |                                    | [Date Responses](#page17)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | [ping](#page50)                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | [Timestamp Format](#page92)        |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 20/May/2015  | Added the progress, repost, restart and         |                                    | progress                           |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | results api calls                               |                                    | [repost](#page20)                  |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | [restart](#page20)                 |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | results                            |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | 6                                               |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 20/May/2015  | Added the venue namespace api calls             |                                    | [Venue Namespace](#page50)         |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    | [(venue)](#page50)       |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 26/May/2015  | Removed the X-Api-Version header. The           |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | version is now part of the url.                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 28/May/2015  | Added the “marketplaceEventTypes”               |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | description to the sample venue api             |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | response.                                       |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 29/May/2015  | Added the marketplace namespace api             |                                    | [Marketplace Namespace](#page69)   |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | calls                                           |                                    |                                    | [(marketplace)](#page69) |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 5/June/2015  | Changed the integer values of                   |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | “marketplaceEventTypes”.                        |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 10/June/2015 | Added params, returns and throws to a           |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | lot of api calls                                |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 18/Jun/2015  | Updates to the getContact api call              |                                    | [getContact](#page22)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | Now returns the inviceLinkYes,     |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | inviteLinkNo and response in the   |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | eventInvitations object            |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | Now returns the eventCode,         |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | printTicketUrl, attendeeCount,     |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | invoiceUrl and guestDetails in the |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | eventRegistrations object          |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 19/Jun/2015  | Added details in eventInvitations section       |                                    | [getContact](#page22)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | of getContact API                               |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | added eventCode parameter          |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | added Value and its meaning for    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | Response Field                     |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 24/Jun/2015  | Added more information in the                   |                                    | [getEventList](#page37)            |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | getEventList api call.                          |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | Added the eventType                |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | Added the events timezone          |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | Added venue                        |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | Added tickets                      |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | Added information                  |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | ●                                               | Added the homepageContent          |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 29/Jun/2015  | Updated documentation for the                   |                                    | [getContact](#page22)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | 7                                  |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | getContact api call and added the               |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | invoices, currentStatus and                     |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | confirmedDate properties to the                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | eventRegistrations property                     |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 23/Jul/2015  | Updated getContact api call to return the       |                                    | [getContact](#page22)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | eventStartDateTime and added a                  |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | parameter to introduce sorting of the           |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | eventRegistrations and eventInvitations         |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | properties                                      |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 14/Aug/2015  | Update getContact api call to return links      |                                    | [getContact](#page22)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | to pdf version of invoices and tickets          |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 30/Aug/2016  | Updated description of the ivvy headers         |                                    | [Signing the request](#page13)​,    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | and the string to sign to be more clear.        |                                    | [Calulating MD5](#page89)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | Updated C\# example for calculating the         |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | MD5 sum.                                        |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 8/Nov/2016   | Added the enum values in the                    |                                    | [getEventList](#page37)            |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | currentStatus of the event                      |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 06/Jun/2017  | Allow filter by ​[Filter](#page15)**​**properties |                                    | [getEventList](#page37)            |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | (afterDate, beforeDate, Status)                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | Allow ordering results by date                  |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 09/Jun/2017  | Added invoice namespace. Methods                |                                    | [Invoice](#page77)                 |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | available                                       |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | getInvoice                         |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | getInvoiceList                     |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | getOptions                         |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 30/Jun/2017  | Allow filter by ​[Filter](#page15)**​**property   |                                    | [getInvoiceList](#page77)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | (fromModifiedDate, toModifiedDate)              |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 23/Aug/2017  | Added following methods to contact              |                                    | [getCompanyList](#page30)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | namespace                                       |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | getCompanyList                     |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | getCompany                         |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \-                                              | addOrUpdateCompany                 |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 24/Aug/2017  | Updated host description.                       |                                    | [HOST (Required)](#page12)         |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 11/Sep/2017  | Allow filter by                                 | [​Filter](#page15)                  | **​**property                       |                          | [getContactList](#page21) |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 | 8                                  |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | (fromModifiedDate, toModifiedDate)              |                                    | [getCompanyList](#page30)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 12/Sep/2017  | Added venueId to filter of getInvoiceList       |                                    | [getInvoiceList](#page77)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | action                                          |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 19/Sep/2017  | Updated the response data (“include”            |                                    | [getEvent](#page40)                |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | and “display” properties) of getEvent           |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | action                                          |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 21/Sep/2017  | Added refType to filter of getInvoiceList       |                                    | [getInvoiceList](#page77)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | action                                          |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 17/Oct/2017  | \- Added companies to                           |                                    | [addOrUpdateContact](#page26)      |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | addOrUpdateContact to update the                |                                    | [getContactList](#page21)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | companies while adding/updating a               |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | [getContact](#page22)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | contact.                                        |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- Updated response data of methods             |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | getContact and getContactList to return         |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- companies (array of ids of                   |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | companies)                                      |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- externalId of the contact                    |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 22/Nov/2017  | \- Added booking reference code in              |                                    | [getInvoiceList](#page77)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | getinvoiceList API                              |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 16/Jan/2018  | \- Added modifiedDateBefore,                    |                                    | [getBookingList](#page57)          |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | modifiedDateAfter filter in booking listing     |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | [getBookingListForAccoun](#page58) |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | actions                                         |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | [t](#page58)                       |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- Added eventType(string) in booking           |                                    | [getBooking](#page61)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | data                                            |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 23/Jan/2018  | \- Added method to venue namespace              |                                    | [getVenueRoomList](#page61)        |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- getVenueRoomList                             |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 1/Feb/2018   | \- Added below mentioned API’s details          |                                    | [addItemsToBooking](#page62)       |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | 1) addItemsToBooking                            |                                    | [addPaymentToBooking](#page65)     |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | 2) addPaymentToBooking                          |                                    | [addRefundToBooking](#page67)      |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | 3) addRefundToBooking                           |                                    | [addOrUpdateCostCenter](#page83)   |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | [getCostCenterList](#page84)       |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | 4) addOrUpdateCostCenter                        |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    | getTaxList                         |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | 5) getCostCenterList                            |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- Remove getTaxList APi from invoice           |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | namespace and added the same to the             |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | Venue namespace                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | 9                                               |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 5/Feb/2018   | \- Added method to venue namespace              |                                    | [getVenueRatePlanList](#page61)    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- getVenueRatePlanList                         |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 5/Mar/2018   | Removed “rev no” column from revision           |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | history.                                        |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 5/Mar/2018   | \- Added action addOrUpdateEvent                |                                    | [addOrUpdateEvent](#page35)        |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- Added section Timezone List                  |                                    | [Timezone List](#page93)           |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 26/Apr/2018  | \- Added modifiedDate in getEventList           |                                    | getEventList                       |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | API,                                            |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 9/May/2018   | \- Removed “salesPriceTax” property             |                                    | [addItemsToBooking](#page62)       |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | from addItemsToBooking request                  |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- Updated descriptions for                     |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | addItemsToBooking request                       |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
| 01/June/2018 | \- Added daily revenue data to                  |                                    | [getBooking](#page61)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | getBooking                                      |                                    | [getInvoice](#page80)              |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- Added the fee details to “payments”          |                                    | [getRegistration](#page42)         |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | section of getInvoice                           |                                    | [getRegistrationList](#page42)     |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | \- Added actions “getRegistration”,             |                                    | [getAttendee](#page43)             |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | “getRegistrationList”, “getAttendee”, and       |                                    | [getAttendeeList](#page45)         |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              | “getAttendeeList” to event namespace            |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |
|              |                                                 |                                    |                                    |                          |                           |   |   |   |   |   |   |   |   |   |   |   |   |   |

>   **Introduction**

>   The iVvy system is built with flexibility in mind, and this API forms a
>   large part of that promise.

>   The API described in this document follows an RPC (Remote Procedure Call)
>   paradigm. Each RPC method is grouped into a few higher level namespaces to
>   help organise this document in a more logical manner.

>   iVvy takes security very seriously and the API described in this document
>   has been designed to be as secure as possible.

-   All transport has been secured by utilising industry standard TLS

-   Key generation can be done first authenticating with the iVvy backend system

-   All requests must be signed using the key/secret pair to prove the request
    was made by a valid key

-   All requests have a time limit to avoid future replay attacks

>   10

>   **Obtaining Keys**

>   Keys are defined as a pair of strings, the ‘key’ and the ‘secret’. Each
>   request must be signed using a ‘secret’ key. There are generated from within
>   the accounts ‘settings’ section of the website.

>   **Creating the request**

>   Requests to the API are over the standard HTTP (HyperText Transfer
>   Protocol). The protocol defines three parts to every request

1.  the method/uri header

2.  a number of request headers

3.  optional body of the request

>   Note also that the HTTP request also needs to be secured by a TLS/SSL
>   connection, often referred to as HTTPS (or HTTP over SSL). iVvy uses
>   industry standard TLS (Transport Layer Security, the successor to SSL,
>   Secure Sockets Layer) to secure the HTTP transport to the API to ensure
>   eavesdropping on the connection by third parties is protected.

>   **Method/URI Header**

>   This is a line consisting of the method of the request, followed by the
>   request URI, followed by the HTTP version. i.e.

>   POST /api/1.0/event?action=getEventList HTTP/1.0

>   This example is for a request, to iVvy’s api ‘event’ namespace, calling the
>   ‘getEventList’ API call, using HTTP version 1.0. Note the HTTP method for
>   calls to the iVvy API are all POST requests. The api version being called is
>   1.0. Currently supported versions are:

-   1.0

>   The URI in the request must always start with /api/{version} (where
>   {version} is the specific api version, e.g. 1.0) followed by the namespace
>   of the eventual api call to make. All requests must also provide the action
>   parameter indicating the API call to invoke.

>   **Request Headers**

>   Request headers are defined by the header name, followed by a colon (:)
>   followed

>   11

>   by a space, followed by the value of the header. A number of headers are
>   used with the iVvy API

>   **Standard Headers**

>   *HOST (Required)*

>   This determines the host that is used for the request. This value is
>   required and should be set to one of the following:

-   api.ap-southeast-2.ivvy.com

-   api.us-west-2.ivvy.com

-   api.eu-west-2.ivvy.com

>   Contact ​<support@ivvy.com>​if you are unsure which value to use.

>   HOST: api.ap-southeast-2.ivvy.com

>   *Date (Required unless using* [IVVY-Date header](#page12)*)*

>   The date header determines the date the request was made. The iVvy API uses
>   this date, compared to the date of the server to determine if the request is
>   within the time to live setting. (Currently requests over 5 minutes old are
>   deemed invalid, this value may change in the future.)

>   Date: ​Thu, 12 Apr 2012 07:17:06 UTC

>   *Content-MD5 (Required)*

>   This is the md5 sum of the body of the request. This header is used to
>   verify the contents of the body of the request have not been altered during
>   transport. Note that if there is no content in the body, the MD5 for the
>   request must still be calculated. See ​[Calculating MD5](#page88)​for more
>   details on how to calculate the value for this field.

>   *Content-Type*

>   The content type of the request body. Valid request types for the api are...

-   application/json

>   *Content-Length*

>   The length of the request body, in bytes.

>   **Custom Headers**

>   A number of custom headers can be used with the request to the API.

>   *IVVY-Date (Optional)*

>   If your HTTP client does not allow the date header to be accessed or set,
>   you can optionally use this header to use for the date string. Note if this
>   header is used, the ‘date’ part of the ​[signed string](#page13)​will need to
>   be empty. The format of the value of this header will be the ​[iVvy Timestamp
>   Format](#page92)​, NOT the string format of the standard

>   12

>   Date header.

>   *X-Api-Authorization (Required)*

>   This is the same format at the standard HTTP Authorization header. For iVvy
>   requests, the format is...

>   X-Api-Authorization: IWS key:signature

-   where IWS is the authentication system used by iVvy, key is the key used to
    sign the request, and the signature is the HMAC-SHA1 signature of the
    request. See [Signing the request](#page13)​for details on how to sign a
    request.

>   The iVvy API server will lookup the secret key associated with the key used
>   in this header, then use the details in the request in association with the
>   secret key, then reconstruct the ​[HMAC-SHA1](#page90)​hash. Only when the
>   calculated hash, and the signature sent through this header match will the
>   request be authenticated.

>   **Signing the request**

>   Every request to the API must be signed with the accounts or users API key.

>   Signing the request is obtained by the following pseudo-code:

>   method := POST

>   contentMd5 := md5(\<body of the request\>)

>   contentType := the value of the Content-Type header

>   contentSign := {contentMd5}{contentType}

>   date := the date header of the request (i.e. Tue, 03 Apr, 2012 22:23:24 utc)

>   NOTE: if using the [IVVY​-Date](#page12)​header, this field will be empty

>   requestString := the entire request string used in the request apiVersion :=
>   the api version to use

>   ivvyHeaders := Concatenated string of all headers starting with IVVY,
>   removing all the

>   Dashes (-) and underscore (_) characters in the header, in alphabetical
>   order, joined together with the

>   ampersand (&) character

>   initialStringToSign :=

>   {method}{contentSign}{date}{requestString}{apiVersion}{ivvyHeaders}

>   stringToSign := lowercase version of the initialStringToSign

>   For example, the following request...

>   POST /api/1.0/test?action=ping HTTP/1.0

>   Host: api.ap-southeast-2.ivvy.com

>   Date: Tue, 03 Apr 2012 22:23:24 UTC

>   Content-MD5: a09f600c77a6dbd947db24c61e8935ca

>   Content-Type: application/json

>   Content-Length: 18

>   X-Api-Version: 1.0

>   X-Api-Authorization: IWS {key:signature here}

>   IVVY-Date: 2012-04-03 22:23:24

>   {"example":"body"}

>   13

>   … will require the following string to be signed …

>   posta09f600c77a6dbd947db24c61e8935caapplication/json/api/1.0/test?action=ping1.0ivvy
>   date=2012-04-03 22:23:24

>   Note the entire string is set to lowercase before signing.

>   Signing is achieved using the HMAC algorithm, using SHA1 encryption. See
>   [HMAC-SHA1](#page90)​for further details

>   **Query Parameters**

>   The api exposes a RPC interface. As such there is a required query
>   parameter, the ‘action’ parameter. This will identify the RPC call to
>   invoke.

>   **Interpreting the response**

>   The response will be given back will be the response in
>   ​[JSON](#page92)​format.

>   **Collections**

>   Some results return collections of objects. E.g. event?action=getEventList.
>   The resulting ​[JSON](#page92)​response for these collections will be an
>   object with the following properties.

-   meta: An object providing information about the result set. The following
    keys may exist

    -   totalResults: The number of results in the complete collection

    -   start: The starting index of the collection this result represents

    -   perPage: The number of items per page of results

    -   count: The number of objects included in this result.

-   results: An array of objects

>   **Pagination**

>   Some requests (mostly the requests that return ​[collections](#page14)​) may
>   also accept some pagination options.

-   perPage: The number of items to return per page. Note that most requests
    have a cap on this number and providing a perPage option greater than that
    cap will not have any effect.

-   start: The record to start paging from. Note this number is zero based, i.e.
    to return results from the very first result, the start will need to equal 0
    (which is the default). Note also this is not the page to start at. For
    example to get the second page from a list of results that have 20 results
    per page, the start property will need to equal 20 (i.e. starting at the
    21st result)

>   14

>   **Filtering**

>   Some requests (mostly requests that return ​[collections](#page14)​and/or take
>   ​[pagination](#page14) requests) may also accept a filter argument. The
>   structure of this filter will be an object with the key’s being what needs
>   to be filtered, and the value will be the content of the filter.

>   There are a number of options that may modify the filter behaviour. These
>   are appended to the end of the key to filter. The accepted modifiers are:

-   **\__CONTAINS​**: Return the results that contain the value.

-   **\__NOTCONTAINS​**: Return the results that do not contain the value.

-   **\__BEGINS​**: Return the results that start with the value.

-   **\__ENDS​**: Return the results that end with the value.

-   **\__LESSTHAN​**: Return the results that are less than or equal to the
    value.

-   **\__GREATERTHAN​**: Return the results that are greater than or equal to the
    value.

-   **\__NOT​**: Return the results that are not equal to the value.

-   **\__EMPTY​**: Returns results that are empty

>   If you want to search for ‘Null’ values, you can use the special value ‘​
>   **ISNULL__​**’ for the filter value.

>   *Example: Filter all the results where the firstName = Bob*

>   {"filter":{"firstName":"Bob"}}

>   *Example: Filter all results where the firstName starts with ‘M’*

>   {"filter":{"firstName__BEGINS":"M"}}

>   *Example: Filter all results where the birthDay has not been set*

>   {"filter":{"firstName":"__ISNULL__"}}

>   **Exceptions**

>   If an error occurred the response will be a ​[JSON](#page92)​representation of
>   what went wrong. This will provide the error code, a brief message as well
>   as a specific code. The specific code is a useful piece of information to be
>   provided in any bug reports.

>   Current exception codes and meanings are:

1.  Bad Request

2.  Unauthorized

3.  Forbidden

4.  Not Found

5.  Method Not Allowed

>   15

1.  Not Acceptable

2.  Too Many Requests

3.  Unknown

4.  Failed Request

5.  Session Expired

6.  Key Revoked

7.  Internal Server Error

8.  Not Implemented

>   Some exceptions will have an additional piece of information associated with
>   the exception, which will contain more specific message about the exception.

>   *Exception: Specific Code 23016*

>   A parameter provided in the request did not validate correctly. For example,
>   the API might have been expecting a number, but a string was provided
>   instead. This exception gets thrown when the first invalid parameter is
>   found.

>   The additional messages will contain the messages from the validator as to
>   why the value was not validated.

>   **Example: Key does not validate error**

>   **Request (contact?action=getContact):**

>   {"id":"wrong"}

>   **Response:**

>   {

>   "errorCode":400,

>   "message":"'id' does not validate",

>   "specificCode":23016,

>   "additionalMessages":["Value must be a whole number"]

>   }

>   *Exception: Specific Code 23017*

>   A required parameter was missing from the request.

>   **Example: Key is required error**

>   **Request (contact?action=getContact):**

>   {}

>   **Response:**

>   {"errorCode":400,"message":"'id' is required","specificCode":23017}

>   **Response Headers**

>   *Content-Type*

>   16

>   This header will identify the content type of the response. At this time
>   only one content type is supported, the application/json type.

>   **Dates**

>   Responses from the iVvy API may contain dates. In all cases (unless
>   otherwise stated in documentation for the specific action) the dates are in
>   Universal Coordinated Time (UTC). Care must be taken when using or
>   displaying these dates to ensure they: a) maintain their UTC time zone for
>   communication with the API, and; b) represented in the appropriate time zone
>   for users utilizing the date.

>   Dates may be represented as a string which must be parsed appropriately if
>   it is to be used. Where possible any dates will be converted to the ​[iVvy
>   Timestamp Format](#page92)​, which is a simple to understand text format to
>   represent a specific point in time to the second.

>   17

>   **API**

>   There are a few things to note as per the structure of the API.

>   **Namespaces**

>   The API is segmented into various namespaces. The support namespaces for the
>   API are…

-   batch

-   event

-   Test

-   invoice

>   **Actions**

>   Within each namespace will be a set of actions that can be performed via API
>   calls. These behave like RPC calls. Each action is unique within the
>   namespace. When calling the API both the namespace and the action must be
>   provided in the following URI format…

>   /api/{version}/{namespace}?action={action}

>   i.e.

>   /api/1.0/batch?action=run

>   Each action may require some extra parameters as part of the call. These are
>   provided in the BODY of the request as a JSON encoded object. The specifics
>   for each call are outlined in this document.

>   **Batch Namespace (batch)**

>   As a way of providing asynchronous access to iVvy’s API, there is a
>   namespace added for batch requests. This also provides a way to run multiple
>   api calls in a batch and provide the result of all the api calls via a URL
>   callback.

>   **run**

>   **Parameters**

| jobs                 | Array of api jobs to be run on the api. Each job needs to have the | Required                         |        |   |   |
|----------------------|--------------------------------------------------------------------|----------------------------------|--------|---|---|
|                      | following keys:                                                    |                                  |        |   |   |
|                      | ●                                                                  | namespace                        |        |   |   |
|                      | ●                                                                  | action                           |        |   |   |
|                      |                                                                    |                                  |        |   |   |
|                      |                                                                    | 18                               |        |   |   |
|                      |                                                                    | ●                                | params |   |   |
|                      |                                                                    |                                  |        |   |   |
| callbackUrl          | The URL to hit with a POST request after the batch has been run,   | Required                         |        |   |   |
|                      | with a JSON object of the responses                                |                                  |        |   |   |
|                      |                                                                    |                                  |        |   |   |
| **Returns**          |                                                                    |                                  |        |   |   |
| asyncId              |                                                                    | Identifier for the batch request |        |   |   |
|                      |                                                                    |                                  |        |   |   |
| **Throws**           |                                                                    |                                  |        |   |   |
| Specific Code: 24092 |                                                                    | Incorrect Job Format             |        |   |   |
|                      |                                                                    |                                  |        |   |   |
| Specific Code: 24093 |                                                                    | Empty job parameter found        |        |   |   |
|                      |                                                                    |                                  |        |   |   |
| Specific Code: 24091 |                                                                    | The information was not saved    |        |   |   |
|                      |                                                                    |                                  |        |   |   |

>   The run action takes an array of api calls and returns an identifier that
>   can be used to identify the batch. Keep this identifier as it can be used to
>   identify the response of the batch request, as well as being used to fetch
>   the progress and results of the request.

>   To run a batch job, an JSON object must be provided with the following keys:

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

>   *Example: Run a batch job inviting some contacts to different events*

>   **Request:**

>   {"jobs":[{"namespace":"event",”action:"inviteContacts","params":{"event":1,"contacts

>   19

>   ":[1,2,3]}},{"namespace":"event",”action:"inviteContacts","params":{"event":2,"conta
>   cts":[1,2,4]}},],"callbackUrl":"[​http://example.callback.url.com](http://example.callback.url.com/)​"}

>   **Response:**

>   {"asyncId":"e35e06ee592d17a42dc9e6252a058617"}

>   **progress**

>   **Parameters**

| async | The asyncId for the batch job to check progress for | Required |
|-------|-----------------------------------------------------|----------|
|       |                                                     |          |

>   **Returns**

| progress | The progress of the batch job, as a percentage of work completed. |
|----------|-------------------------------------------------------------------|
|          |                                                                   |

>   **Throws**

| Specific Code: 24105 | Could not find batch |
|----------------------|----------------------|
|                      |                      |

>   The progress action takes the asyncId as a parameter and returns back the
>   progress of the batch job as a percentage

>   *Example: Fetch the progress of a batch job*

>   **Request:**

>   {"async":"a7ec88af7d710bf51b188004bb532d77"}

>   **Response:**

>   {"progress":33}

>   **restart**

>   The restart action takes the asyncId as a parameter and returns the success
>   of the call. Note a success of true does not mean the job will restart
>   immediately.

>   *Example: Restart a batch job*

>   **Request:**

>   {"async":"a7ec88af7d710bf51b188004bb532d77"}

>   **Response:**

>   {"restarted":true}

>   **repost**

>   The repost action takes the asyncId as a parameter and returns the success
>   of the call. Note a success of true does not mean the callback will be hit
>   immediately.

>   *Example: Restart a batch job*

>   **Request:**

>   {"async":"a7ec88af7d710bf51b188004bb532d77"}

>   20

>   **Response:**

>   {"reposted":true}

>   **results**

>   **Parameters**

| async                | The asyncId for the batch job to show the results of                               | Required  |   |   |
|----------------------|------------------------------------------------------------------------------------|-----------|---|---|
|                      |                                                                                    |           |   |   |
| **Returns**          |                                                                                    |           |   |   |
| results              | The results of the batch. This will be an array of objects with the following keys |           |   |   |
|                      | ●                                                                                  | namespace |   |   |
|                      | ●                                                                                  | action    |   |   |
|                      | ●                                                                                  | request   |   |   |
|                      | ●                                                                                  | response  |   |   |
|                      |                                                                                    |           |   |   |
| **Throws**           |                                                                                    |           |   |   |
| Specific Code: 24114 | Batch job not completed                                                            |           |   |   |
|                      |                                                                                    |           |   |   |
| Specific Code: 24115 | Could not find batch                                                               |           |   |   |
|                      |                                                                                    |           |   |   |

>   The result action takes the asyncId as a parameter and returns an array of
>   results from the batch job.

>   *Example: Get the result of a batch job*

>   **Request:**

>   {"async":"a7ec88af7d710bf51b188004bb532d77"}

>   **Response:**

>   {"results":[{"namespace":"contact","action":"addOrUpdateContact","request":{"id":776
>   6,"firstName":"Bob"},"response":{"success":true,"id":7766}]}

>   **Contact Namespace (contact)**

>   **getContactList**

>   **Parameters**

| perPage | The number of events to get in a single api call   | Must be an      |
|---------|----------------------------------------------------|-----------------|
|         |                                                    | integer greater |
|         |                                                    | than 0          |
|         |                                                    |                 |
| start   | The starting result of the page. Note this is zero | Must be an      |
|         | based (i.e. sending start=0 will start from the    | integer 0 or    |
|         | first result.)                                     | greater         |
|         |                                                    |                 |
|         | 21                                                 |                 |

>   **Additional** [​Filter](#page15)**​Properties**

| fromModifiedDate |                                                                                | Filter by Modified Date |                         | [iVvy Timestamp Format](#page92) |                                  |   |   |
|------------------|--------------------------------------------------------------------------------|-------------------------|-------------------------|----------------------------------|----------------------------------|---|---|
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| toModifiedDate   |                                                                                |                         | Filter by Modified Date |                                  | [iVvy Timestamp Format](#page92) |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| **Returns**      |                                                                                |                         |                         |                                  |                                  |   |   |
| id               | The unique identifier for the contact                                          |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| firstName        | The contact’s first name                                                       |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| lastName         | The contact’s last name                                                        |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| email            | The contact’s email address                                                    |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| phone            | The contact’s phone number                                                     |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| customFields     | The custom field information for the contact. This is an array of fields, each |                         |                         |                                  |                                  |   |   |
|                  | an object with the following keys:                                             |                         |                         |                                  |                                  |   |   |
|                  | ●                                                                              | fieldId                 |                         |                                  |                                  |   |   |
|                  | ●                                                                              | displayName             |                         |                                  |                                  |   |   |
|                  | ●                                                                              | value                   |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| groups           | The subscription group information for the contact.                            |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| companies        | This will an array company ids to which the contact belongs.                   |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| externalId       | This will be external id of the contact                                        |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |
| modifiedDate     | The modified date of the contact                                               |                         |                         |                                  |                                  |   |   |
|                  |                                                                                |                         |                         |                                  |                                  |   |   |

>   The result from this call will be a ​[collection](#page14)​of all the contacts
>   the user has access to. This call also accepts the ​[pagination](#page14)​and
>   ​[filter](#page15)​properties.

>   **getContact**

>   **Parameters**

| id                 | The contacts identifier                              | Required                                                                  |                                               |                                                     |                                  |                        |   |
|--------------------|------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------|-----------------------------------------------------|----------------------------------|------------------------|---|
|                    |                                                      | Must be an Integer                                                        |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| useEventSortOrder  | If true, the eventInvitations and eventRegistrations | Must be a Boolean                                                         |                                               |                                                     |                                  |                        |   |
|                    | will be returned ordered by the Event Start Date     |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| **Returns**        |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    | 22                                                   |                                                                           |                                               |                                                     |                                  |                        |   |
| id                 |                                                      | The unique identifier for the contact                                     |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| firstName          |                                                      | The contact’s first name                                                  |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| lastName           |                                                      | The contact’s last name                                                   |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| email              |                                                      | The contact’s email address                                               |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| phone              |                                                      | The contact’s phone number                                                |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| status             |                                                      | The contact's email status                                                |                                               |                                                     |                                  |                        |   |
|                    | 1                                                    | = 'Subscribed'                                                            |                                               |                                                     |                                  |                        |   |
|                    | 2                                                    | = 'Unsubscribed'                                                          |                                               |                                                     |                                  |                        |   |
|                    | 3                                                    | = 'Bounced'                                                               |                                               |                                                     |                                  |                        |   |
|                    | 4                                                    | = 'Registering'                                                           |                                               |                                                     |                                  |                        |   |
|                    | 5                                                    | = 'No Marketing'                                                          |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| smsStatus          |                                                      | The contact’s sms status                                                  |                                               |                                                     |                                  |                        |   |
|                    | 1                                                    | = 'Subscribed'                                                            |                                               |                                                     |                                  |                        |   |
|                    | 2                                                    | = 'Unsubscribed'                                                          |                                               |                                                     |                                  |                        |   |
|                    | 3                                                    | = 'Failed'                                                                |                                               |                                                     |                                  |                        |   |
|                    | 4                                                    | = 'No Marketing'                                                          |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| customFields       |                                                      | The custom field information for the contact. This is an array of fields, |                                               |                                                     |                                  |                        |   |
|                    |                                                      | each an object with the following keys:                                   |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           | ●                                             | fieldId                                             |                                  |                        |   |
|                    |                                                      |                                                                           | ●                                             | displayName                                         |                                  |                        |   |
|                    |                                                      |                                                                           | ●                                             | value                                               |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| groups             |                                                      | The subscription group information for the contact.                       |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| companies          |                                                      | This will an array company ids to which the contact belongs.              |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| externalId         |                                                      | This will be an external id of the contact                                |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| modifiedDate       |                                                      | The modified date of the contact                                          |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| eventInvitations   |                                                      | An array of events the contact has been invited to. Each element of the   |                                               |                                                     |                                  |                        |   |
|                    |                                                      | array is an object with the following fields                              |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | eventId                                                                   | The event identifier of the invitation        |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | eventCode                                                                 | The code of the event of the invitation       |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | eventStartDateTime                                                        | The timestamp the event is starting           |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | inviteLinkYes                                                             | Invitation link for the Yes response for this |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           | 23                                            |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | contact to the event                                |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | inviteLinkNo                                                              |                                               | Invitation link for No response for this contact to |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | the event                                           |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | response                                                                  |                                               | The contacts response to the invitation.            |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | Possible values are                                 |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | ●                                                   | U = Undecided                    |                        |   |
|                    |                                                      |                                                                           |                                               | ●                                                   | Y = Yes                          |                        |   |
|                    |                                                      |                                                                           |                                               | ●                                                   | N = No                           |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| eventRegistrations |                                                      | An array of events the contact has registered for. Each element of the    |                                               |                                                     |                                  |                        |   |
|                    |                                                      | array is an object with the following fields                              |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | eventId                                                                   |                                               | The event identifier of the registration            |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | eventCode                                                                 |                                               | The code of the event of the registration           |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | eventStartDateTime                                                        |                                               | The timestamp the event is starting                 |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | registrationId                                                            |                                               | The unique identifier of the registration           |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | currentStatus                                                             |                                               | The status of the registration                      |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | ●                                                   | 2 = Completed                    |                        |   |
|                    |                                                      |                                                                           |                                               | ●                                                   | 3 = Cancelled                    |                        |   |
|                    |                                                      |                                                                           |                                               | ● 4 = Payment Required                              |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | confirmedDate                                                             |                                               | Timestamp of the date the registration was          |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | confirmed                                           |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | isPaymentWaiting                                                          |                                               | If the registration is payment waiting or not       |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | printTicketUrl                                                            |                                               | The URL the registrations tickets                   |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | printTicketUrlPdf                                                         |                                               | Link to the PDF for the registrations tickets       |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | attendeeCount                                                             |                                               | Total number of attendees for this registration     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | invoiceUrl                                                                |                                               | The URL for the registration primary invoice        |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | invoiceUrlPdf                                                             |                                               | Link to the PDF for the registration primary        |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | invoice                                             |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | guestDetails                                                              |                                               | An array of objects with the following              |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | properties…                                         |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| 24                 |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | contactId                                           |                                  | The identifier for the |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  | contact if known       |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | fullName                                            |                                  | Name of guest          |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | email                                               |                                  | Email address of guest |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | attended                                            |                                  | If the contact has     |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  | attended the event     |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | attendedDateTime                                    | When the contact                 |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  | attended the event     |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      | invoices                                                                  |                                               | The list of invoices associated with the            |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | registration. Each element of the array is an       |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | object with the following fields                    |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | id                                                  | The unique identifier for the    |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | invoice                          |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | reference                                           | The reference number of the      |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | invoice                          |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | title                                               | The title of the invoice         |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | currentStatus                                       | The current status of the        |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | invoice. The value of this field |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | will be one of the following…    |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | 0 = Not Paid                     |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | 1 = Unconfirmed Paid             |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | 2 = Paid                         |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | 3 = Written Off                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | 4 = Cancelled                    |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | 5 = Refunded                     |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | description                                         | The description of the invoice   |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | currency                                            | The currency of the values of    |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | this invoice                     |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | totalCost                                           | The total amount of the invoice  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | totalPaid                                           | How much has been paid off       |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     | the invoice                      |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
| 25                 |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | invoiceUrl                                          | The URL for the invoice          |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               | invoiceUrlPdf                                       | The URL for the invoice pdf      |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |
|                    |                                                      |                                                                           |                                               |                                                     |                                  |                        |   |

>   **Throws**

![](media/b30d42b2780fda5515c388028782d31f.jpg)

>   Specific Code: 24096 Unable to find contact

>   The contact identifier must be provided to fetch a specific contact from the
>   system.

>   *Example: Get a specific contact*

>   **Request:**

>   {"id":6}

>   **Response:**

>   {

>   "id":"25146",

>   "firstName":"Test",

>   "lastName":"User",

>   "email":"user\@test.com",

>   "phone":"0455550000",

>   "customFields":[

>   {"fieldId":"102","displayName":"Dietary Requirements","value":[""]},
>   {"fieldId":"103","displayName":"Shirt Size","value":["Medium"]}

>   ],

>   "groups":[

>   {"contactId":"25146","groupId":"2481","joinDate":"2012-04-16 21:07:04"},

>   {"contactId":"25146","groupId":"2485","joinDate":"2014-05-6 12:32:12"}

>   ],

>   "companies":[

>   4,5,6

>   ],

>   "externalId":"59fc43b6726be"

>   }

>   **addOrUpdateContact**

>   **Parameters**

| id           | The contact’s identifier.                        | Must be an integer                                   |
|--------------|--------------------------------------------------|------------------------------------------------------|
|              | (Leave empty to add the                          |                                                      |
|              | contact to the system.)                          |                                                      |
|              |                                                  |                                                      |
| firstName    | The contact’s first name                         | Required when the id parameter is missing            |
|              |                                                  |                                                      |
| lastName     | The contact’s last name                          | Required when the id parameter is missing            |
|              |                                                  |                                                      |
| email        | The contact’s email address                      | Must be a valid email.                               |
|              |                                                  |                                                      |
|              | 26                                               |                                                      |
| phone        | The contact’s phone number                       | Must be a valid phone number.                        |
|              |                                                  |                                                      |
| groups       | The array of subscription                        | Note this list will override any groups currently    |
|              | groups to set for the contact                    | set for the contact                                  |
|              |                                                  |                                                      |
| customFields | The array of custom fields to                    | Each field will be validated depending on the        |
|              | set on the contact                               | type of field that is being set.                     |
|              |                                                  |                                                      |
| companies    | The array of companies to                        | Each values will be validated depending on           |
|              | set the contact.                                 | the type of field as well as it will verify that the |
|              |                                                  | given company is exist or not.                       |
|              |                                                  |                                                      |
| **Returns**  |                                                  |                                                      |
| success      | If the contact was successfully added or updated |                                                      |
|              |                                                  |                                                      |
| id           | The unique identifier for the contact            |                                                      |
|              |                                                  |                                                      |
| message      | Message of the failure (if success was false)    |                                                      |
|              |                                                  |                                                      |

>   This call takes values for a contact, and either

1.  Updates the values for that contact (after you have provided an id in the
    parameters), or

2.  Adds the contact to the system (if the id parameter is missing)

>   The result of this call will contain the status of the result (either true
>   or false) and the contact identifier of the updated or newly created
>   contact.

>   The properties of the contact currently supported are:

-   firstName

-   lastName

-   email

-   phone

-   groups

    -   This is an array of group objects with the ‘groupId’ key.

-   customFields

    -   This is an array of custom field objects with ‘fieldId’ and ‘value’ keys

-   Companies

    -   This is an array of companies Ids

>   *Example: Adding a contact*

>   **Request:**

>   {"firstName":"Bob","lastName":"Smith","email":"[​bob\@smith.com](mailto:bob@smith.com)​","groups":[{"groupId":2
>   2},{"groupId":3}],"customFields":[{"fieldId":33443,"value":"Yes"}],
>   "companies":[4,5]}

>   **Response:**

>   {"id":33884}

>   27

>   *Example: Updating a contact*

>   NOTE: the groups will be set to only group 10, destroying the existing value

>   **Request:**

>   {"id":33884,firstName":"Bobby","groups":[{"groupId":10}],"customFields":[{"fieldId":

>   33443,"value":"No"}],"companies":[4,5]}

>   **Response:**

>   {"id":33884}

>   **getCustomFieldDefinition**

>   **Returns (an array of objects with the following properties)**

| fieldId      | The unique identifier for this custom field                    |                                                        |
|--------------|----------------------------------------------------------------|--------------------------------------------------------|
|              |                                                                |                                                        |
| fieldType    | The type of this field                                         |                                                        |
|              | ● 0 = Small Text                                               |                                                        |
|              | ● 1 = Large Text                                               |                                                        |
|              | ● 2 = Single Select                                            |                                                        |
|              |                                                                | ○ Valid options are provided in the ‘selectValues’ key |
|              | ● 3 = Multiple Select                                          |                                                        |
|              |                                                                | ○ Valid options are provided in the ‘selectValues’ key |
|              | ●                                                              | 4 = Address                                            |
|              | ●                                                              | 5 = Date                                               |
|              | ●                                                              | 6 = File                                               |
|              |                                                                | ○ Valid file types are provided in the ‘fileTypes’ key |
|              | ● 7 = Static Text                                              |                                                        |
|              |                                                                | ○ Values cannot be set for this type                   |
|              | ● 8 = Whole Number                                             |                                                        |
|              |                                                                |                                                        |
| displayName  | The name of this field                                         |                                                        |
|              |                                                                |                                                        |
| isRequired   | If this field is required or not                               |                                                        |
|              |                                                                |                                                        |
| sortOrder    | Order to display this field                                    |                                                        |
|              |                                                                |                                                        |
| selectValues | Values that can be selected with select fields                 |                                                        |
|              |                                                                |                                                        |
| fileTypes    | Types of files that can be uploaded with the file custom field |                                                        |
|              |                                                                |                                                        |

>   This call will return an array of custom fields available on the account.
>   The result will have the fieldId which is the unique field identifier for
>   the specific field, as well as the display name and any options required for
>   each field.

>   As part of the field definition there is a ‘fieldType’ property which can be
>   resolved to the following types

>   28

-   0 = Small Text

-   1 = Large Text

-   2 = Single Select

    -   Valid options are provided in the ‘selectValues’ key

-   3 = Multiple Select

    -   Valid options are provided in the ‘selectValues’ key

-   4 = Address

-   5 = Date

-   6 = File

    -   Valid file types are provided in the ‘fileTypes’ key

-   7 = Static Text

    -   Values cannot be set for this type

-   8 = Whole Number

>   **getSubscriptionGroupList**

>   **Returns**

>   An array with the following properties

| id          | The subscription group identifier   |
|-------------|-------------------------------------|
|             |                                     |
| groupName   | The name for the group              |
|             |                                     |
| memberCount | The number of contacts in the group |
|             |                                     |
| tagColour   | The designated colour for the group |
|             |                                     |

>   Returns an array of subscription groups available on the account.

>   **addContactsToSubscriptionGroup**

>   **Parameters**

| contacts | The contact identifiers to | Required.                                               |
|----------|----------------------------|---------------------------------------------------------|
|          | subscribe to the group     | This is an array of contact identifiers (each must be a |
|          |                            |                                                         |
|          |                            | valid integer)                                          |
|          |                            |                                                         |
| group    | The subscription group     | Required.                                               |
|          | identifier to add the      |                                                         |
|          | contacts to                | Must be a valid integer.                                |
|          |                            |                                                         |

>   **Returns**

>   An array of objects with the following properties

| contactId | The contact this result is for               |
|-----------|----------------------------------------------|
|           |                                              |
|           | 29                                           |
| status    | If the contact was added to the group or not |
|           |                                              |

>   Adds a number of contacts to a subscription group.

>   *Example: Add 4 contacts to subscription group 2481*

>   **Request:**

>   {"contacts":[4,6,55,33],"group":2481}

>   **Response:**

>   [{"contactId":4,"status":true},{"contactId":6,"status":true},{"contactId":55,"status
>   ":true},{"contactId":33,"status":false}]

>   **removeContactsFromSubscriptionGroup**

>   **Parameters**

| contacts | The contact identifiers to | Required.                                               |
|----------|----------------------------|---------------------------------------------------------|
|          | unsubscribe from the       |                                                         |
|          | group                      | This is an array of contact identifiers (each must be a |
|          |                            | valid integer)                                          |
|          |                            |                                                         |
| group    | The subscription group     | Required.                                               |
|          | identifier to remove the   |                                                         |
|          | contacts from              | Must be a valid integer.                                |
|          |                            |                                                         |

>   **Returns**

>   An array of objects with the following properties

| contactId | The contact this result is for                   |
|-----------|--------------------------------------------------|
|           |                                                  |
| status    | If the contact was removed from the group or not |
|           |                                                  |

>   Removes a number of contacts from a subscription group. This call is very
>   similar to the ​*addContactsToSubscriptionGroup*​call. It takes the same
>   parameters and returns the same result.

>   **getCompanyList**

>   **Parameters**

| perPage                                        | The number of companies to get in a single api                       | Must be an      |                         |                      |                                  |         |   |   |   |   |
|------------------------------------------------|----------------------------------------------------------------------|-----------------|-------------------------|----------------------|----------------------------------|---------|---|---|---|---|
|                                                | call                                                                 | integer greater |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      | than 0          |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| start                                          | The starting result of the page. Note this is zero                   | Must be an      |                         |                      |                                  |         |   |   |   |   |
|                                                | based (i.e. sending start=0 will start from the                      | integer 0 or    |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
|                                                | 30                                                                   |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      | first result.)  |                         |                      |                                  | greater |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| **Additional ​**[Filter](#page15)**​Properties** |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| fromModifiedDate                               |                                                                      |                 | Filter by Modified Date |                      | [iVvy Timestamp Format](#page92) |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| toModifiedDate                                 |                                                                      |                 | Filter by Modified Date |                      | [iVvy Timestamp Format](#page92) |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| **Returns**                                    |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| id                                             | The unique identifier for the company                                |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| externalId                                     | Optionally a unique identifier of the company that is managed by an  |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         | external application |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| businessName                                   | The company's business name                                          |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| tradingName                                    | The company's trading name                                           |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| businessNumber                                 | The company's registration number                                    |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| phone                                          | The company's phone number                                           |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| fax                                            | The company's fax number                                             |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| website                                        | The company's website                                                |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| email                                          | The company's email address                                          |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| address                                        | The company’s address. This is an an object with the following keys: |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | line1                            |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | line2                            |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | line3                            |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | line4                            |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | city                             |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | stateCode (e.g: QLD)             |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | countryCode (e.g: AU)            |         |   |   |   |   |
|                                                |                                                                      |                 |                         | ●                    | postalCode                       |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |
| modifiedDate                                   | The modified date of the company                                     |                 |                         |                      |                                  |         |   |   |   |   |
|                                                |                                                                      |                 |                         |                      |                                  |         |   |   |   |   |

>   The result from this call will be a
>   ​[collection](https://docs.google.com/document/d/19K4AL6VP4OknfzPud2PUKY1zlbj2_sgVefTOANdeAFc/edit#heading=h.30l4t7cku5e4)​of
>   all the companies the user has access to. This call also accepts the
>   ​[pagination](https://docs.google.com/document/d/19K4AL6VP4OknfzPud2PUKY1zlbj2_sgVefTOANdeAFc/edit#heading=h.82axcekcr8k4)​and
>   ​[filter](https://docs.google.com/document/d/19K4AL6VP4OknfzPud2PUKY1zlbj2_sgVefTOANdeAFc/edit#heading=h.h94gxeaaelp6)​properties.

>   **getCompany**

>   **Parameters**

>   31

| The company’s identifier | Required           |
|--------------------------|--------------------|
|                          | Must be an Integer |
|                          |                    |

>   **Returns**

| id             | The unique identifier for the company                                |                       |
|----------------|----------------------------------------------------------------------|-----------------------|
|                |                                                                      |                       |
| externalId     | Optionally a unique identifier of the company that is managed by an  |                       |
|                | external application                                                 |                       |
|                |                                                                      |                       |
| businessName   | The company's business name                                          |                       |
|                |                                                                      |                       |
| tradingName    | The company's trading name                                           |                       |
|                |                                                                      |                       |
| businessNumber | The company's registration number                                    |                       |
|                |                                                                      |                       |
| phone          | The company's phone number                                           |                       |
|                |                                                                      |                       |
| fax            | The company's fax number                                             |                       |
|                |                                                                      |                       |
| website        | The company's website                                                |                       |
|                |                                                                      |                       |
| email          | The company's email address                                          |                       |
|                |                                                                      |                       |
| address        | The company’s address. This is an an object with the following keys: |                       |
|                | ●                                                                    | line1                 |
|                | ●                                                                    | line2                 |
|                | ●                                                                    | line3                 |
|                | ●                                                                    | line4                 |
|                | ●                                                                    | city                  |
|                | ●                                                                    | stateCode (e.g: QLD)  |
|                | ●                                                                    | countryCode (e.g: AU) |
|                | ●                                                                    | postalCode            |
|                |                                                                      |                       |
| modifiedDate   | The modified date of the company                                     |                       |
|                |                                                                      |                       |

>   **Throws**

![](media/b30d42b2780fda5515c388028782d31f.jpg)

>   Specific Code: 24153 Unable to find company

>   The company identifier must be provided to fetch a specific company from the
>   system.

>   32

>   *Example: Get a specific company*

>   **Request:**

>   {"id":6}

>   **Response:**

>   {

>   "id":"25146",

>   "businessName":"Test",

>   "tradingName":"Test Trading",

>   "businessNumber":"1234586",

>   "email":"company\@test.com",

>   "phone":"0455550000",

>   "fax":"0455550125",

>   "website":"[www.test.com​](http://www.test.com/)",​

>   "address": {"line1": "Street Number", "line2": "Street Name", "line3": "",

>   "line4": "", "city": "Gold Coast", "stateCode": "QLD",

>   "countryCode": "AU", "postalCode": "4227"}

>   }

>   **addOrUpdateCompany**

>   **Parameters**

| id             | The company’s identifier. (Leave empty to add the     | Must be an   |              |
|----------------|-------------------------------------------------------|--------------|--------------|
|                | company to the system.)                               | integer      |              |
|                |                                                       |              |              |
| externalId     | Optionally a unique identifier of the company that is |              |              |
|                | managed by an external application                    |              |              |
|                |                                                       |              |              |
| businessName   | The company's business name                           | Mandatory if |              |
|                |                                                       |              | adding a new |
|                |                                                       |              | company      |
|                |                                                       |              |              |
| tradingName    | The company's trading name                            |              |              |
|                |                                                       |              |              |
| businessNumber | The company's registration number                     |              |              |
|                |                                                       |              |              |
| phone          | The company's phone number                            |              |              |
|                |                                                       |              |              |
| fax            | The company's fax number                              |              |              |
|                |                                                       |              |              |
| website        | The company's website                                 |              |              |
|                |                                                       |              |              |
| email          | The company's email address                           |              |              |
|                |                                                       |              |              |
| address        | The company’s address. This is an an object with the  |              |              |
|                | following keys:                                       |              |              |
|                | ●                                                     | line1        |              |
|                | ●                                                     | line2        |              |
|                | ●                                                     | line3        |              |
|                |                                                       |              |              |
|                |                                                       | 33           |              |

![](media/0d6525adf8701fbf575c1320a4b6d952.jpg)

>   ● line4

>   ● city

>   ● stateCode (e.g: QLD)

>   ● countryCode (e.g: AU)

>   ● postalCode

>   **Returns**

| success | If the company was successfully added or updated |
|---------|--------------------------------------------------|
|         |                                                  |
| id      | The unique identifier for the company            |
|         |                                                  |
| message | Message of the failure (if success was false)    |
|         |                                                  |

>   This call takes values for a company, and either

1.  Updates the values for that company (after you have provided an id in the
    parameters), or

2.  Adds the company to the system (if the id parameter is missing)

>   The result of this call will contain the status of the result (either true
>   or false) and the company identifier of the updated or newly created
>   company.

>   The properties of the company currently supported are:

-   businessName

-   externalId

-   tradingName

-   businessNumber

-   phone

-   fax

-   website

-   email

-   address

    -   This is an object

>   *Example: Adding a company*

>   **Request:**

>   {"businessName":"New

>   Company","tradingName":"ABC","email":"[​company\@test.com](mailto:company@test.com)​","address":{"line1":"address
>   line 1", "line2":"address line 2", "stateCode": "QLD", "postalCode":"4227",
>   "countryCode": "AU" }}

>   **Response:**

>   {"success":true, "id":1618}

>   *Example: Updating a company*

>   **Request:**

>   {"id":1618, businessName":"Updated Company name",
>   "address":{"line1":"address line 11", "line2":"address line 22",
>   "stateCode": "QLD", "postalCode":"4227",

>   34

>   "countryCode": "AU" }}

>   **Response:**

>   {"id":1618}

>   **Event Namespace (event)**

>   **addOrUpdateEvent**

>   **Parameters**

| id                     |                                                        | The event’s unique identifier.                 | Integer           |
|------------------------|--------------------------------------------------------|------------------------------------------------|-------------------|
|                        |                                                        | Exclude to add an event.                       | \> 0              |
|                        |                                                        | Include to update an existing event.           |                   |
|                        |                                                        |                                                |                   |
| eventType              |                                                        | Required: always.                              | Integer           |
|                        |                                                        | The type of event.                             | \>= 0             |
|                        |                                                        | Value must be 12 (Record Event Details).       |                   |
|                        |                                                        | The value cannot be changed for an             |                   |
|                        |                                                        | existing event.                                |                   |
|                        |                                                        |                                                |                   |
| code                   |                                                        | The event’s unique code.                       | String            |
|                        |                                                        | Can be excluded when adding an event           | Max length: 12    |
|                        |                                                        | (system will assign a unique code).            |                   |
|                        |                                                        | The value cannot be changed for an             |                   |
|                        |                                                        | existing event.                                |                   |
|                        |                                                        |                                                |                   |
| title                  |                                                        | Required: when adding an event.                | String            |
|                        |                                                        | The title of the event.                        | Max length: 140   |
|                        |                                                        |                                                |                   |
| timezone               |                                                        | Required: when adding an event.                | Timezone          |
|                        |                                                        | The timezone of the event.                     |                   |
|                        |                                                        |                                                |                   |
| startDateTime          |                                                        | Required: when adding an event.                | Timestamp         |
|                        |                                                        | The start date & time of the event.            |                   |
|                        |                                                        |                                                |                   |
| endDateTime            |                                                        | Required: when adding an event.                | Timestamp         |
|                        |                                                        | The end date & time of the event.              |                   |
|                        |                                                        | The value must be on or after                  |                   |
|                        |                                                        | startDateTime.                                 |                   |
|                        |                                                        |                                                |                   |
| capacity               |                                                        | The maximum number of attendees who            | Integer           |
|                        |                                                        | can register for the event.                    | \>= 0             |
|                        |                                                        | A value of 0 (zero) represents no limit.       |                   |
|                        |                                                        |                                                |                   |
| budget                 |                                                        | A budget amount assigned to the event.         | Float             |
|                        |                                                        |                                                |                   |
| costCenterId           |                                                        | A cost center assigned to the event.           | Integer           |
|                        |                                                        | The value is an identifier of a cost center in | \> 0              |
|                        |                                                        |                                                |                   |
|                        | 35                                                     |                                                |                   |
|                        |                                                        | the account, which must be assignable to       |                   |
|                        |                                                        | events.                                        |                   |
|                        |                                                        |                                                |                   |
| primaryContactUserId   | The primary contact user of the event.                 | Integer                                        |                   |
|                        |                                                        | The value is an identifier of a user in the    | \> 0              |
|                        |                                                        | account.                                       |                   |
|                        |                                                        |                                                |                   |
| secondaryContactUserId | The secondary contact user of the event.               | Integer                                        |                   |
|                        |                                                        | The value is an identifier of a user in the    | \> 0              |
|                        |                                                        | account.                                       |                   |
|                        |                                                        |                                                |                   |
| eventTypeIds           |                                                        | Zero or more tags assigned to the event.       | Array of Integers |
|                        |                                                        | The value is an array of event tag             |                   |
|                        |                                                        | identifiers.                                   |                   |
|                        |                                                        |                                                |                   |
| isAccommIncluded       | Whether or not the event requires                      | Boolean                                        |                   |
|                        |                                                        | accommodation.                                 |                   |
|                        |                                                        |                                                |                   |
| venueId                |                                                        | The venue assigned to the event.               | Integer           |
|                        |                                                        | The value is an identifier of an event venue   | \> 0              |
|                        |                                                        | in the account.                                |                   |
|                        |                                                        |                                                |                   |
| **Returns**            |                                                        |                                                |                   |
|                        |                                                        |                                                |                   |
| success                | Whether or not the action succeeded (i.e. the event as | Boolean                                        |                   |
|                        | added or updated).                                     |                                                |                   |
|                        |                                                        |                                                |                   |
| id                     | The event’s unique identifier.                         | Integer                                        |                   |
|                        | The value will be null on failure.                     | \> 0                                           |                   |
|                        |                                                        |                                                |                   |
| code                   | The event’s unique code.                               | String                                         |                   |
|                        | The value will be null on failure.                     | Max length: 12                                 |                   |
|                        |                                                        |                                                |                   |

>   This action call accepts the parameters of an event and will;

1.  Add a new event to the account

2.  Update an existing event in the account when the id parameter is provided.

>   NOTE: This action call only supports “Record Event Details” type events
>   (i.e.

>   eventType value of 12).

>   **Example Request:**

>   {

>   "eventType": 12,

>   "title": "A New Event",

>   "timezone": "Australia/Sydney",

>   "startDateTime": "2018-03-05 03:00:00 UTC",

>   36

>   "endDateTime": "2018-03-05 06:00:00 UTC",

>   "capacity": 10,

>   "budget": 150,

>   "costCenterId": 834,

>   "primaryContactUserId": 7821,

>   "eventTypeIds": [56,57],

>   "isAccommIncluded": false

>   }

>   **Example Response:**

>   {

>   "success": true,

>   "id": 98481,

>   "code": "BAS4G248"

>   }

>   **getEventList**

>   **Parameters**

| perPage                                        |                        |   | The number of events to get in a single api   | Must be an integer |                                             |                 |   |                |   |   |
|------------------------------------------------|------------------------|---|-----------------------------------------------|--------------------|---------------------------------------------|-----------------|---|----------------|---|---|
|                                                |                        |   |                                               |                    | call                                        |                 |   | greater than 0 |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| start                                          |                        |   | The starting result of the page. Note this is | Must be an integer |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    | zero based (i.e. sending start=0 will start | 0 or greater    |   |                |   |   |
|                                                |                        |   |                                               |                    | from the first result.)                     |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| includeVenueDetails                            |                        |   | If the response should include venue details  | Must be a boolean  |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| includeTicketDetails                           |                        |   | If the response should include ticket details | Must be a boolean  |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| includeInformationDetails                      |                        |   | If the response should include the event      | Must be a boolean  |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    | information                                 |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| includeHomepageContent                         |                        |   | If the response should include the            | Must be a boolean  |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    | homepage content of the website             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| orderBy                                        |                        |   | Sort results                                  |                    |                                             | Supported       |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   | parameter      |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   | “startDate”    |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| orderDir                                       |                        |   | Sort direction                                |                    |                                             | ‘asc’ or ‘desc’ |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| **Additional ​**[Filter](#page15)**​Properties** |                        |   |                                               |                    |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| afterDate                                      |                        |   | Filter by start date                          |                    | [iVvy Timestamp Format](#page92)            |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
|                                                |                        |   | 37                                            |                    |                                             |                 |   |                |   |   |
| beforeDate                                     | Filter by end date     |   | [iVvy Timestamp Format](#page92)              |                    |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |
| status                                         | Filter by status       |   | Must be an array                              |                    |                                             |                 |   |                |   |   |
|                                                | Array of the following |   |                                               |                    |                                             |                 |   |                |   |   |
|                                                | values                 |   |                                               |                    |                                             |                 |   |                |   |   |
|                                                | ●                      | 0 | = Draft                                       |                    |                                             |                 |   |                |   |   |
|                                                | ●                      | 1 | = Closed                                      |                    |                                             |                 |   |                |   |   |
|                                                | ●                      | 3 | = Launched                                    |                    |                                             |                 |   |                |   |   |
|                                                |                        |   |                                               |                    |                                             |                 |   |                |   |   |

>   **Returns**

>   A collection object with the following properties in the results

| id               | The unique event identifier            |                                                                            |                                            |                                            |                                             |                               |   |   |
|------------------|----------------------------------------|----------------------------------------------------------------------------|--------------------------------------------|--------------------------------------------|---------------------------------------------|-------------------------------|---|---|
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| code             | The code for the event                 |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| eventType        | The type of event.                     |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  | ●                                      | 0                                                                          | = Other                                    |                                            |                                             |                               |   |   |
|                  | ●                                      | 1                                                                          | = Party                                    |                                            |                                             |                               |   |   |
|                  | ●                                      | 2                                                                          | = Festival                                 |                                            |                                             |                               |   |   |
|                  | ● 3 = Golf Day                         |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  | ●                                      | 4                                                                          | = Wedding                                  |                                            |                                             |                               |   |   |
|                  | ●                                      | 5                                                                          | = Meeting                                  |                                            |                                             |                               |   |   |
|                  | ●                                      | 6                                                                          | = Seminar                                  |                                            |                                             |                               |   |   |
|                  | ●                                      | 7                                                                          | = Conference                               |                                            |                                             |                               |   |   |
|                  | ●                                      | 8                                                                          | = Exhibition                               |                                            |                                             |                               |   |   |
|                  | ●                                      | 9                                                                          | = Roadshow                                 |                                            |                                             |                               |   |   |
|                  | ●                                      | 10 = Simple                                                                |                                            |                                            |                                             |                               |   |   |
|                  | ● 11 = Party (21st / 18th)             |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  | ● 12 = Record Event Details            |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| title            | The title of the event                 |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| domainName       | The domain name of the event           |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| startDateTime    | The start of the event, at UTC         |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| endDateTime      | The end of the event, at UTC           |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| numRegistered    | The number of registrations            |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| currentStatus    | The current status of the event        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  | ●                                      | 0                                                                          | = Draft                                    |                                            |                                             |                               |   |   |
|                  | ●                                      | 1                                                                          | = Closed                                   |                                            |                                             |                               |   |   |
|                  | ●                                      | 3                                                                          | = Launched                                 |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| contactEmail     | The contact email address on the event |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | 38                                                                         |                                            |                                            |                                             |                               |   |   |
| websiteUrl       |                                        | The URL for the event website                                              |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| websiteTemplateB |                                        | Banner that is displayed on the website                                    |                                            |                                            |                                             |                               |   |   |
| annerImageUrl    |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| venue            |                                        | Details of the venue of the event (if the includeVenueDetails flag is set  |                                            |                                            |                                             |                               |   |   |
|                  |                                        | on the request)                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | name                                                                       | The venue name                             |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | description                                                                | The description of the venue               |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | address                                                                    | The address of the venue                   |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | imageUrl                                                                   | The URL to the image of the venue          |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| tickets          |                                        | The tickets of an event (if the includeTicketDetails flag is set on the    |                                            |                                            |                                             |                               |   |   |
|                  |                                        | request)                                                                   |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | id                                                                         |                                            |                                            | The unique identifier for the ticket        |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | title                                                                      |                                            |                                            | Title of the ticket                         |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | capacity                                                                   |                                            |                                            | Capacity of the ticket                      |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | description                                                                |                                            |                                            | Description of the ticket                   |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | amount                                                                     |                                            |                                            | Amount of the ticket                        |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | isTaxFree                                                                  |                                            |                                            | Amount of the ticket is tax free            |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | subscriptionGroups                                                         |                                            | Subscription groups assigned to the ticket |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            | This an array of objects with the following |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            | properties…                                 |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            | id                                          | The subscription group        |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             | identifier                    |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            | groupName                                   | The name for the group        |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            | tagColour                                   | The designated colour for the |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             | group                         |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  | 39                                     |                                                                            |                                            |                                            |                                             |                               |   |   |
| information      |                                        | Event website information (if the includeInformationDetails flag is set on |                                            |                                            |                                             |                               |   |   |
|                  |                                        | the request)                                                               |                                            |                                            |                                             |                               |   |   |
|                  |                                        | This is an array of objects with the following properties…                 |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | description                                                                | Description of the information             |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | information                                                                | Content of the information                 |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | fileUrl                                                                    | Attached file url of event information     |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | sortOrder                                                                  | The order in which to sort the information |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| homepageContent  |                                        | Content of the website home page (if the includeHomepageContent flag       |                                            |                                            |                                             |                               |   |   |
|                  |                                        | is set on the request). Note this is the contents of the HTML that is      |                                            |                                            |                                             |                               |   |   |
|                  |                                        | entered in as the home page content of the event.                          |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| eventTags        |                                        | The tags of the event                                                      |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | id                                                                         |                                            | The unique identifier for the event tag    |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        | name                                                                       |                                            | The name of the event tag                  |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |
| modifiedDate     |                                        | timestamp                                                                  |                                            |                                            |                                             |                               |   |   |
|                  |                                        |                                                                            |                                            |                                            |                                             |                               |   |   |

>   The result from this call will be a [​collection](#page14)​of all the events
>   the user has access to.

>   This call also accepts the [pagination​](#page14)​and
>   [filter​](#page15)​properties.

>   **getEvent**

>   **Parameters**

| id                | The event identifier | Required                                                           |                                         |
|-------------------|----------------------|--------------------------------------------------------------------|-----------------------------------------|
|                   |                      |                                                                    | Must be an integer                      |
|                   |                      |                                                                    |                                         |
| **Returns**       |                      |                                                                    |                                         |
| id                |                      | The unique event identifier                                        |                                         |
|                   |                      |                                                                    |                                         |
| code              |                      | The code for the event                                             |                                         |
|                   |                      |                                                                    |                                         |
| title             |                      | The title of the event                                             |                                         |
|                   |                      |                                                                    |                                         |
|                   | 40                   |                                                                    |                                         |
| domainName        |                      | The domain name of the event                                       |                                         |
|                   |                      |                                                                    |                                         |
| startDateTime     |                      | The start of the event, at UTC                                     |                                         |
|                   |                      |                                                                    |                                         |
| endDateTime       |                      | The end of the event, at UTC                                       |                                         |
|                   |                      |                                                                    |                                         |
| numRegistered     |                      | The number of registrations                                        |                                         |
|                   |                      |                                                                    |                                         |
| currentStatus     |                      | The current status of the event                                    |                                         |
|                   |                      |                                                                    |                                         |
| appTitle          |                      | The title to display on mobile platforms                           |                                         |
|                   |                      |                                                                    |                                         |
| twitter           |                      | Twitter hashtag for this event                                     |                                         |
|                   |                      |                                                                    |                                         |
| appBanner         |                      | Banner to display on mobile platforms                              |                                         |
|                   |                      |                                                                    |                                         |
| map               |                      | Map of the event                                                   |                                         |
|                   |                      |                                                                    |                                         |
| includeSpeakers   |                      | Whether or not the event includes speakers                         |                                         |
|                   |                      |                                                                    |                                         |
| displaySpeakers   |                      | Whether or not the speakers are displayed on the event website     |                                         |
|                   |                      |                                                                    |                                         |
| includeSponsors   |                      | Whether or not the event includes sponsors                         |                                         |
|                   |                      |                                                                    |                                         |
| displaySponsors   |                      | Whether or not there are sponsors displayed on the event website   |                                         |
|                   |                      |                                                                    |                                         |
| includeBooths     |                      | Whether or not the event includes exhibition booths                |                                         |
|                   |                      |                                                                    |                                         |
| displayExhibitors |                      | Whether or not there are exhibitors displayed on the event website |                                         |
|                   |                      |                                                                    |                                         |
| includeAbstracts  |                      | Whether or not the event includes abstracts                        |                                         |
|                   |                      |                                                                    |                                         |
| displayAbstracts  |                      | Whether or not there are abstracts displayed on the event website  |                                         |
|                   |                      |                                                                    |                                         |
| includeHotels     |                      | Whether or not the event includes hotel accommodation              |                                         |
|                   |                      |                                                                    |                                         |
| includeTravel     |                      | Whether or not the event includes travel (flights and transfers)   |                                         |
|                   |                      |                                                                    |                                         |
| includeMembership |                      | Whether or not the event includes memberships                      |                                         |
|                   |                      |                                                                    |                                         |
| eventTags         |                      | The tags of the event                                              |                                         |
|                   |                      |                                                                    |                                         |
|                   |                      | id                                                                 | The unique identifier for the event tag |
|                   |                      |                                                                    |                                         |
|                   |                      | name                                                               | The name of the event tag               |
|                   |                      |                                                                    |                                         |
|                   |                      |                                                                    |                                         |

>   **Throws**

>   41

| Specific Code: 24097 | Unable to find event |
|----------------------|----------------------|
|                      |                      |

>   The event identifier must be provided as part of this call to fetch the
>   specific event.

>   E.g. {"id":1} can be used to fetch the details of an event with the
>   identifier of 1.

>   **getRegistration**

>   **Parameters**

| id                   |                                                    | The registration identifier                        | Required |   |                    |
|----------------------|----------------------------------------------------|----------------------------------------------------|----------|---|--------------------|
|                      |                                                    |                                                    |          |   | Must be an integer |
|                      |                                                    |                                                    |          |   |                    |
| eventId              |                                                    | The event identifier to which registration belongs | Required |   |                    |
|                      |                                                    |                                                    |          |   | Must be an integer |
|                      |                                                    |                                                    |          |   |                    |
| **Returns**          |                                                    |                                                    |          |   |                    |
| id                   |                                                    | The unique registration identifier                 |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| currentStatus        | The current status of the event                    |                                                    |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| isExhibitor          |                                                    | Whether or not event registration is exhibitor     |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| completedDate        | The registered date time of event registration     |                                                    |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| firstName            |                                                    | The first name of the event registration           |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| lastName             |                                                    | The last name of the event registration            |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| phone                |                                                    | The phone number of event registration             |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| modifiedDate         | The date & time the registration was last modified |                                                    |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| **Throws**           |                                                    |                                                    |          |   |                    |
| Specific Code: 24207 |                                                    | Unable to find event                               |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| Specific Code: 24208 |                                                    | Invalid Registration Id                            |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |
| Specific Code: 24209 |                                                    | Registration not found                             |          |   |                    |
|                      |                                                    |                                                    |          |   |                    |

>   **getRegistrationList**

>   **Parameters**

| perPage |                                               | The number of registrations to get in a | Must be an integer |
|---------|-----------------------------------------------|-----------------------------------------|--------------------|
|         |                                               | single api call                         | greater than 0 and |
|         |                                               |                                         | maximum 100        |
|         |                                               |                                         |                    |
|         | 42                                            |                                         |                    |
| start   | The starting result of the page. Note this is | Must be an integer                      |                    |
|         | zero based (i.e. sending start=0 will start   | 0 or greater                            |                    |
|         | from the first result.)                       |                                         |                    |
|         |                                               |                                         |                    |
| eventId | The event identifier                          | Must be a Integer                       |                    |
|         |                                               |                                         |                    |

>   **Additional ​**[Filter](#page15)**​Properties**

| modifiedDate | Filter by modified date |   | [iVvy Timestamp Format](#page92) |
|--------------|-------------------------|---|----------------------------------|
|              |                         |   |                                  |

>   **Returns**

>   A collection object with the following properties in the results

| id               | The unique registration identifier                 |
|------------------|----------------------------------------------------|
|                  |                                                    |
| currentStatus    | The current status of the event                    |
|                  |                                                    |
| isExhibitor      | Whether or not event registration is exhibitor     |
|                  |                                                    |
| completedDate    | The registered date time of event registration     |
|                  |                                                    |
| mainContactId    | The main contact id of event registration          |
|                  |                                                    |
| firstName        | The first name of the event registration           |
|                  |                                                    |
| lastName         | The last name of the event registration            |
|                  |                                                    |
| phone            | The phone number of event registration             |
|                  |                                                    |
| invoiceTotalCost | The total cost of event registration               |
|                  |                                                    |
| invoiceTotalPaid | The total amount paid of event registration        |
|                  |                                                    |
| modifiedDate     | The date & time the registration was last modified |
|                  |                                                    |

>   The result from this call will be a [​collection](#page14)​of all the events
>   the user has access to.

>   This call also accepts the [pagination​](#page14)​and
>   [filter​](#page15)​properties.

>   **Throws**

| Specific Code: 24206 | Unable to find event |
|----------------------|----------------------|
|                      |                      |

>   **getAttendee**

>   **Parameters**

>   43

| id      | The attendee identifier                        | Required           |
|---------|------------------------------------------------|--------------------|
|         |                                                | Must be an integer |
|         |                                                |                    |
| eventId | The event identifier to which attendee belongs | Required           |
|         |                                                | Must be an integer |
|         |                                                |                    |

>   **Returns**

| id                 |    | The unique registration identifier                                   |                                            |   |
|--------------------|----|----------------------------------------------------------------------|--------------------------------------------|---|
|                    |    |                                                                      |                                            |   |
| registrationStatus |    | The registration status of the event attendee                        |                                            |   |
|                    |    |                                                                      |                                            |   |
| contactId          |    | The contactId of event attendee                                      |                                            |   |
|                    |    |                                                                      |                                            |   |
| registrationId     |    | The registration id of event attendee                                |                                            |   |
|                    |    |                                                                      |                                            |   |
| ticketTitle        |    | The title of ticket                                                  |                                            |   |
|                    |    |                                                                      |                                            |   |
| firstName          |    | The first name of the event attendee                                 |                                            |   |
|                    |    |                                                                      |                                            |   |
| lastName           |    | The last name of the event attendee                                  |                                            |   |
|                    |    |                                                                      |                                            |   |
| email              |    | The email address of the event attendee                              |                                            |   |
|                    |    |                                                                      |                                            |   |
| hasAttended        |    | Whether attendee has attended event or not                           |                                            |   |
|                    |    |                                                                      |                                            |   |
| sessionHasAttended |    | Whether attendee has attended session or not                         |                                            |   |
|                    |    |                                                                      |                                            |   |
| isPublic           |    | Whether event attendee is public or not                              |                                            |   |
|                    |    |                                                                      |                                            |   |
| barcode            |    | The barcode text of event attendee                                   |                                            |   |
|                    |    |                                                                      |                                            |   |
| barcodeUrl         |    | The barcode url of event attendee                                    |                                            |   |
|                    |    |                                                                      |                                            |   |
| ticketUrl          |    | The ticket url of event attendee                                     |                                            |   |
|                    |    |                                                                      |                                            |   |
| attendedDatetime   |    | The attended date time of event attendee                             |                                            |   |
|                    |    |                                                                      |                                            |   |
| sessionAttendedTim |    | The session attended date time of event attendee                     |                                            |   |
| estamp             |    |                                                                      |                                            |   |
|                    |    |                                                                      |                                            |   |
| cost               |    | The cost of ticket of event attendee                                 |                                            |   |
|                    |    |                                                                      |                                            |   |
| customFields       |    | The array of custom fields data of event attendee with below details |                                            |   |
|                    |    |                                                                      |                                            |   |
|                    |    | name                                                                 | The name of the custom field               |   |
|                    |    |                                                                      |                                            |   |
|                    |    | value                                                                | The value of the custom field for attendee |   |
|                    |    |                                                                      |                                            |   |
|                    |    |                                                                      |                                            |   |
|                    | 44 |                                                                      |                                            |   |

>   **Throws**

| Specific Code: 24211 | Unable to find event |
|----------------------|----------------------|
|                      |                      |
| Specific Code: 24212 | Invalid Attendee Id  |
|                      |                      |
| Specific Code: 24213 | Attendee not found   |
|                      |                      |

>   **getAttendeeList**

>   **Parameters**

| perPage | The number of attendees to get in a single    | Must be an integer |
|---------|-----------------------------------------------|--------------------|
|         | api call                                      | greater than 0 and |
|         |                                               | maximum 100        |
|         |                                               |                    |
| start   | The starting result of the page. Note this is | Must be an integer |
|         | zero based (i.e. sending start=0 will start   | 0 or greater       |
|         | from the first result.)                       |                    |
|         |                                               |                    |
| eventId | The event identifier                          | Must be a Integer  |
|         |                                               |                    |

>   **Additional ​**[Filter](#page15)**​Properties**

>   No filters available

>   **Returns**

>   A collection object with the following properties in the results

| id                 | The unique registration identifier            |                                                                      |                                            |   |
|--------------------|-----------------------------------------------|----------------------------------------------------------------------|--------------------------------------------|---|
|                    |                                               |                                                                      |                                            |   |
| registrationStatus | The registration status of the event attendee |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| contactId          | The contactId of event attendee               |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| ticketTitle        | The title of ticket                           |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| firstName          | The first name of the event attendee          |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| lastName           | The last name of the event attendee           |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| email              | The email address of the event attendee       |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| hasAttended        | Whether attendee has attended event or not    |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| sessionHasAttended | Whether attendee has attended session or not  |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| isPublic           | Whether event attndee is public or not        |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
|                    | 45                                            |                                                                      |                                            |   |
| barcode            |                                               | The barcode text of event attendee                                   |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| barcodeUrl         |                                               | The barcode url of event attendee                                    |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| ticketUrl          |                                               | The ticket url of event attendee                                     |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| attendedDatetime   |                                               | The attended date time of event attendee                             |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| sessionAttendedTim |                                               | The session attended date time of event attendee                     |                                            |   |
| estamp             |                                               |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| cost               |                                               | The cost of ticket of event attendee                                 |                                            |   |
|                    |                                               |                                                                      |                                            |   |
| customFields       |                                               | The array of custom fields data of event attendee with below details |                                            |   |
|                    |                                               |                                                                      |                                            |   |
|                    |                                               | name                                                                 | The name of the custom field               |   |
|                    |                                               |                                                                      |                                            |   |
|                    |                                               | value                                                                | The value of the custom field for attendee |   |
|                    |                                               |                                                                      |                                            |   |
|                    |                                               |                                                                      |                                            |   |

>   The result from this call will be a [​collection](#page14)​of all the events
>   the user has access to.

>   This call also accepts the [pagination​](#page14)​and
>   [filter​](#page15)​properties.

>   **Throws**

| Specific Code: 24210 | Unable to find event |
|----------------------|----------------------|
|                      |                      |

>   **inviteContacts**

>   **Parameters**

| event       |   |                                                   | The event identifier to invite the contact to    | Required.              |   |                  |   |   |
|-------------|---|---------------------------------------------------|--------------------------------------------------|------------------------|---|------------------|---|---|
|             |   |                                                   |                                                  |                        |   | Must be an       |   |   |
|             |   |                                                   |                                                  |                        |   | integer.         |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
| contacts    |   |                                                   | An array of contact identifiers to invite to the | Required               |   |                  |   |   |
|             |   |                                                   | event                                            |                        |   | Must be an array |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   | of integers      |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
| **Returns** |   |                                                   |                                                  |                        |   |                  |   |   |
| results     |   | An array of objects with the following properties |                                                  |                        |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   | contact                                           |                                                  | The contact identifier |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   |                                                   |                                                  | 46                     |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   | status                                            | The status of the request                        |                        |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   | inviteLinkYes                                     | Invitation link for the YES responses            |                        |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   | inviteLinkNo                                      | Invitation link fo the NO responses              |                        |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |
|             |   |                                                   |                                                  |                        |   |                  |   |   |

>   To invite a contact to the event, pass through the event identifier and an
>   array of contact identifiers through to this call. The result will be a an
>   array indicating if each of the contacts invitation was successful or not,
>   and if so the links for responding to the invitations for both yes and no.

>   *Example: Invite contacts with identifiers 1, 2 and 3 to event with the
>   identifier 4*

>   **Request:**

>   {"event":4,"contacts":[1,2,3]}

>   **Response:**

>   {

>   "results":[

>   {

>   "contact":1,

>   "status":true,

>   "inviteLinkYes":"http://....",

>   "inviteLinkNo":"http://...."

>   },

>   {"contact":2,"status":false},

>   {

>   "contact":3,

>   "status":true

>   "inviteLinkYes":"http://....",

>   "inviteLinkNo":"http://...."

>   }

>   ]

>   }

>   **getSponsorshipList**

>   **Parameters**

| event | The event identifier | Required           |
|-------|----------------------|--------------------|
|       |                      | Must be an integer |
|       |                      |                    |

>   **Returns**

>   A collection array with the following object properties in the results

| id | The unique sponsor identifier |
|----|-------------------------------|
|    |                               |

>   47

| name                  | The name of the sponsor                                        |
|-----------------------|----------------------------------------------------------------|
|                       |                                                                |
| description           | The description of the sponsor                                 |
|                       |                                                                |
| websiteAddress        | The URL to the sponsor details                                 |
|                       |                                                                |
| logoImageUrl          | The URL to the sponsor details                                 |
|                       |                                                                |
| level                 | The sponsorship level of the sponsor                           |
|                       |                                                                |
| customLevelId         | The custom level identifier if this sponsor has a custom level |
|                       | assigned to it                                                 |
|                       |                                                                |
| sponsorshipAmount     | How much this sponsorship is for                               |
|                       |                                                                |
| sponsorshipAmountPaid | How much has been paid by the sponsor so far                   |
|                       |                                                                |

>   **Throws**

| Specific Code: 24094 | Event does not have sponsors |
|----------------------|------------------------------|
|                      |                              |
| Specific Code: 24100 | Unable to find event         |
|                      |                              |

>   Lists the sponsors that are sponsoring the event.

>   *Example: Fetch the list of sponsors on an event*

>   **Request:**

>   {"event":15593}

>   **Response:**

>   {"meta":{"totalResults":1,"start":0,"perPage":1,"count":1},"results":[{"id":"1","nam

>   e":"Test Sponsor for event

>   1","description":"...","websiteAddress":"www.sponsor1.com","logoI

>   mageUrl":"https://.../554ac739bcc9a.png","level":"9","customLevelId":null,"sponsorsh

>   ipAmount":"44","sponsorshipAmountPaid":"4"}]}

>   **getSpeakerList**

>   **Parameters**

![](media/f40eb60c74913f136bbee789f48d569b.jpg)

| event | The event identifier | Required |
|-------|----------------------|----------|


>   Must be an integer

>   **Returns**

>   A collection object with the following properties of objects in the results

| id                 | The unique speaker identifier          |
|--------------------|----------------------------------------|
|                    |                                        |
|                    | 48                                     |
| fullName           | The speaker’s name                     |
|                    |                                        |
| organisation       | The speaker’s organisation             |
|                    |                                        |
| position           | The position of the speaker            |
|                    |                                        |
| profileDescription | The speaker’s profile                  |
|                    |                                        |
| profileImageUrl    | The URL to the speaker’s profile image |
|                    |                                        |

>   **Throws**

| Specific Code: 24124 | Event does not have speakers |
|----------------------|------------------------------|
|                      |                              |
| Specific Code: 24101 | Unable to find event         |
|                      |                              |

>   Lists the speakers of the event.

>   *Example: Fetch the list of speakers at an event*

>   **Request:**

>   {“event”:15593}

>   **Response:**

>   {"meta":{"totalResults":1,"start":0,"perPage":1,"count":1},"results":[{"id":"6","ful
>   lName":"Mr Speaker","organisation":"Google","position":"Lead
>   Developer","profileDescription":"...","profileImageUrl":"https://…./8869de9237bb1.pn
>   g"}]}

>   **createLoginToken**

>   **Parameters**

| event       |    | The event identifier for the contact to be logged in to                              | Required               |
|-------------|----|--------------------------------------------------------------------------------------|------------------------|
|             |    |                                                                                      | Must be a valid number |
|             |    |                                                                                      |                        |
| contact     |    | The contact identifier to allow the login                                            | Required               |
|             |    |                                                                                      | Must be a valid number |
|             |    |                                                                                      |                        |
| referrer    |    | Referrer of the request which will be used in validating                             |                        |
|             |    | the token later                                                                      |                        |
|             |    |                                                                                      |                        |
| **Returns** |    |                                                                                      |                        |
| token       |    | Single use, time restricted token for the contact to login to the iVvy Event Website |                        |
|             |    |                                                                                      |                        |
| loginUrl    |    | The URL that must be used to authenticate the user with the token                    |                        |
|             |    |                                                                                      |                        |
|             | 49 |                                                                                      |                        |

>   **Throws**

| Specific Code: 24099 | Unable to generate token |
|----------------------|--------------------------|
|                      |                          |
| Specific Code: 24098 | Unable to find event     |
|                      |                          |

>   Creates a login token that can be used to login to an event, on the behalf
>   of a registered contact. This call takes an event identifier and a contact
>   identifier and an optional referrer url to generate a single-use, time
>   restricted token.

>   The result will be the token and a URL that can be used to redirect the user
>   to have them logged in to view their registration details without the use of
>   a username and password.

>   If the referrer is provided when creating the token, the browser’s referrer
>   header will also be checked to ensure the request using the token has been
>   redirected from the specific website saved against the token.

>   *Example: Request a login token for a contact on an event*

>   **Request:**

>   {"event":15593,"contact":297466}

>   **Response:**

>   {"token":"fc877d1bae56ebc5a8e19b29a3df67de","loginUrl":"http://wired.ivvy.com/event/
>   SQ6EXR/registration/login/token?t=fc877d1bae56ebc5a8e19b29a3df67de&contact=297466"}

>   **Test Namespace (test)**

>   **ping**

>   Used for testing the access to the api. This call takes no parameters and
>   responds to the request with an ack message, with the
>   ​[timestamp](#page92)​from the server.

>   **Venue Namespace (venue)**

>   **getVenueList**

>   The result from this call will be a ​[collection](#page14)​of all the venues
>   to which the user has access. This call also accepts the
>   ​[pagination](#page14)​parameters.

>   **getVenue**

>   The result from this call will be the details of a specific venue to which
>   the user has access. The unique venue identifier is required, for example
>   {“id”:123}

>   50

>   *Example: Get a specific venue*

>   **Request:**

>   {"id":21}

>   **Response:**

>   {

>   "id": 21,

>   "hashId": "1efda3e35a75aabd13e8996037d35a79",

>   "businessName": "iVvy Conference Centre",

>   "businessNumber": 123123,

>   "phone": "1300 004 889",

>   "fax": "",

>   "websiteAddress": "",

>   "emailAddress": "support\@ivvy.com",

>   "description": "\<p\> Located by the River at Hamilton, this is the closest
>   5 star, full service Hotel to the Brisbane Cruise Terminal - Portside at
>   Hamilton, the Airport precinct, Gateway Arterial Bridge linking the Gold
>   Coast to the Sunshine Coast and is just minutes from the CBD.\<br /\>\<br
>   /\> Featuring 90 spacious, newly refurbished and well appointed
>   accommodation rooms, the hotel is an urban escape perfect for business or
>   leisure travellers alike. Most rooms feature magnificent views of the widest
>   reach of the Brisbane River spanning from the Brisbane City past the
>   Brisbane Cruise Terminal and to the Gateway Bridge.\<br /\>\<br /\> Enjoy
>   the resort style pool, spa, sauna, gym and complimentary car parking \&amp;
>   Wi-Fi for all delegates, guests and visitors.\<br /\>\<br /\> From the
>   grandeur of the column free Hamilton Ballroom which can easily divide into
>   smaller configurations, the intimacy of the Newstead Room or take advantage
>   of the newly refurbished Executive Boardroom the Brisbane Riverview Hotel
>   has an option to suit your budget and requirements. The resort style pool
>   area is a fantastic venue for breakout sessions or lunches. This is a
>   flexible and well equipped conference venue can cater for intimte boardroom
>   meeting of 6 people up to large corporate events for up to 300 delegates.
>   \<br /\>\<br /\> With expansive river views, Plates Restaurant offers a
>   seasonal menu showcasing superb produce from Queensland\&\#8217;s freshest
>   seafood, international cuisine, and wood fired steaks and pizzas. It is the
>   perfect place for business or pleasure, mixing excellent atmosphere with
>   great service.\</p\> ",

>   "checkinTime": "11:00:00",

>   "checkoutTime": "14:00:00",

>   "childAge": 0,

>   "infantAge": 0,

>   "currencyCode": "AUD",

>   "localeCode": "en_AU",

>   "timezone": "Australia/Brisbane",

>   "hasSpaces": true,

>   "hasAccommodation": true,

>   "numMeetingRooms": 0,

>   "numAccommodationRooms": 200,

>   "maxSpaceArea": null,

>   "totalSpaceArea": null,

>   "longitude": 153.4065773,

>   "latitude": -28.0067947,

>   "primaryAddress": {

>   "line1": "2 Boston Court",

>   "line2": "",

>   "line3": "",

>   "line4": "",

>   "city": "Varsity Lakes",

>   "stateCode": "QLD",

>   51

>   "stateName": null,

>   "countryCode": "AU",

>   "countryName": null,

>   "postalCode": 4227

>   },

>   "videoUrls": ["https://www.youtube.com/embed/rxiPVWurK7Q"],

>   "airportName": "Gold Coast (OOL)",

>   "airportDistance": 20,

>   "starRating": 5,

>   "ratingAuthority": 2,

>   "maxSpaceCapacity": 100,

>   "facilities": [2, 3, 6, 12, 14, 19, 20, 24, 27, 30, 31, 34, 35],

>   "mainImage": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/55403b462c0aa.jpg",

>   "originalFileName": "main function sapce 2.jpg",

>   "tags": [],

>   "size": 2647159,

>   "contentType": "image/jpeg"

>   },

>   "marketplaceBannerImage": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/banner/banner.jpg",

>   "originalFileName": "banner.jpg",

>   "tags": [],

>   "size": 2963936,

>   "contentType": "image/jpeg"

>   },

>   "brochureFile": null,

>   "imageLibrary": [{

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   imageLibrary/5513b498229a6.jpg",

>   "originalFileName":

>   "58443-room-types-5-vibe-hotel-sydney-executive-king.jpg",

>   "tags": ["General"],

>   "size": 46333,

>   "contentType": "image/jpeg",

>   "marketplaceEventTypes": [31]

>   }],

>   "packages": [{

>   "id": 5,

>   "name": "Day Delegate Package",

>   "minPax": 30,

>   "price": 98,

>   "priceMethod": 1,

>   "smallDescription": "At iVvy Conference Centre, intimate spaces are combined
>   with state-of-the-art technology and award-winning food. Our Day Delegate
>   Package is ideal for small to medium meetings or events, offering a range of
>   menus for your attendees",

>   "largeDescription": "\<p\> At iVvy Conference Centre, intimate spaces are
>   combined with state-of-the-art technology and award-winning food. Our Day
>   Delegate Package is ideal for small to medium meetings or events, offering a
>   range of menus designed by our team of chefs to create a unique dining
>   experience for your attendees.\</p\> \<p\> At just \$98 per person, our Day
>   Delegate Package includes the

>   52

>   following:\</p\> \<ul\>\<li\> Venue hire\</li\> \<li\> Pre-installed
>   technical equipment and services including\&\#160;a high definition
>   projector or display, a PA system and

>   a\&\#160;presentation computer\</li\> \<li\> Free Wi-Fi\</li\> \<li\>
>   Notepads and pens\</li\> \<li\> Iced water and sweets\</li\> \<li\> Tea and
>   coffee on arrival\</li\> \<li\> Morning tea\</li\> \<li\> Networking
>   lunch\</li\> \<li\> Afternoon tea.\</li\> \</ul\>",

>   "marketplaceName": "Day Delegate Package",

>   "marketplaceEventTypes": [11, 21]

>   }],

>   "functionSpaces": [{

>   "id": 6463,

>   "name": "Special events and public holidays",

>   "description": null,

>   "area": null,

>   "length": null,

>   "width": null,

>   "heightMaximum": null,

>   "heightMinimum": null,

>   "floorPressureMaximum": null,

>   "marketplaceName": null,

>   "minPax": 0,

>   "maxPax": 1,

>   "hasLayouts": true,

>   "image": null,

>   "layouts": []

>   }, {

>   "id": 169,

>   "name": "River Room",

>   "description": "\<p\> Ocean and river views are a focal point of the River
>   room. This room has floor-to-ceiling glass with full length curtains if
>   required, and access to a large, central area for meet-and-greets or
>   pre-dinner cocktails. The large projector screen is perfect for meetings or
>   special events and this room has been fully soundproofed for privacy.\</p\>
>   ",

>   "area": null,

>   "length": null,

>   "width": null,

>   "heightMaximum": null,

>   "heightMinimum": null,

>   "floorPressureMaximum": null,

>   "marketplaceName": "River Room",

>   "marketplaceEventTypes": [11, 21],

>   "minPax": 30,

>   "maxPax": 400,

>   "hasLayouts": true,

"image": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/spaces/169/5540362637d5f.jpg",

>   "originalFileName": "River Room.jpg",

>   "tags": [],

>   "size": 67933,

>   "contentType": "image/jpeg"

>   },

>   "layouts": [{

>   "id": 421,

>   "type": 7,

>   "paxMinimum": null,

>   53

>   "paxMaximum": 400,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "id": 425,

>   "type": 6,

>   "paxMinimum": null,

>   "paxMaximum": 150,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "id": 637,

>   "type": 1,

>   "paxMinimum": null,

>   "paxMaximum": 250,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "id": 9019,

>   "type": 5,

>   "paxMinimum": null,

>   "paxMaximum": 80,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "id": 9511,

>   "type": 8,

>   "paxMinimum": null,

>   "paxMaximum": 50,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "id": 9655,

>   "type": 4,

>   "paxMinimum": null,

>   "paxMaximum": 100,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "id": 9867,

>   "type": 3,

>   "paxMinimum": null,

>   "paxMaximum": 100,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }]

>   }],

>   "accommodation": [{

>   "id": 53,

>   "code": "14-53",

>   "name": "1 Bedroom Residence",

>   "description": "\<ul\>\<li\> A studio apartment sleeps 1-5 and contains a
>   queen bed plus a sofa that can folded out to a double bed.\</li\> \<li\>
>   Rollaways also available.\</li\> \</ul\>",

>   "numStandardAdults": 1,

>   "numExtraAdults": 1,

>   "extraAdultCost": 0,

>   54

>   "canSmoke": false,

>   "capacity": 20,

>   "marketplaceName": "Studio",

"image": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/accommodation/53/5540352c9c2ca.jpg",

>   "originalFileName": "Studio.jpg",

>   "tags": [],

>   "size": 48330,

>   "contentType": "image/jpeg"

>   }

>   }]

>   }

>   The following are properties in the example json response above that have
>   special values.

>   **ratingAuthority**

>   One of the following values:

-   1 = AAA rated

-   2 = Self rated

>   **facilities**

>   An array of the following values:

-   1 = Air Conditioning

-   2 = Airport Shuttle

-   3 = Audio Visual

-   4 = BBQ

-   6 = Business Centre

-   7 = Ceremony On Site

-   8 = Child Minding

-   9 = Disabled Access

-   10 = Dry Cleaning

-   11 = Express Checkout

-   12 = Free Parking

-   13 = Gaming Area

-   14 = Gymnasium

-   15 = Internet Access

-   16 = Laundry

-   39 = Liquor License

-   17 = Mobile Bar

-   18 = Open 24 Hours

-   19 = Outdoor Area

-   20 = Parking Available

-   21 = Pay TV

>   55

-   22 = Playground

-   23 = Printing Services

-   24 = Public Transport

-   25 = Restaurant On Site

-   26 = Sauna Steam Room

-   27 = Smoking Permitted

-   28 = Spa

-   29 = Staging

-   30 = Street Parking

-   31 = Swimming Pool

-   32 = Tour Desk

-   33 = Undercover Parking

-   34 = Valet Parking

-   35 = Wheelchair Access

-   36 = Wifi Access

-   37 = Outside Catering Allowed

-   38 = BYO Allowed

>   **priceMethod (package pricing)**

>   One of the following values:

-   1 = Per person

-   2 = Flat rate

>   **type (function space layout)**

>   One of the following values:

-   0 = Custom

-   1 = Theatre

-   2 = Classroom

-   3 = U-Shape

-   4 = Cabaret

-   5 = Boardroom

-   6 = Banquet

-   7 = Cocktail

-   8 = Hollow Square

>   **marketplaceEventTypes (packages, function spaces and image library
>   files)**

>   An array of the following values:

-   11 = Event

-   21 = Wedding

-   31 = Conference

-   41 = Meeting

>   56

>   **getBookingList**

>   The result from this call will be a ​[collection](#page14)​of all the Booking
>   of specific venue to which the user has access. This call also accepts the
>   ​[pagination](#page14)​parameters. The unique venue identifier and per page
>   value is required, for example {"venueId":"1","perPage":10}

>   *Example: Get a specific venue’s Booking List*

>   **Request:**

>   {"venueId":"1","perPage":1}

>   **Response:**

>   {

>   "meta":{

>   "totalResults":256,

>   "start":0,

>   "perPage":1,

>   "count":1

>   },

>   "results":[

>   {

>   "id":1,

>   "venueId":1,

>   "code":"HR5ZASGMQ1",

>   "name":"Some Booking",

>   "eventType":"Holiday",

>   "company":{

>   "id":4,

>   "businessName":"Some Business"

>   },

>   "contact":{

>   "id":3,

>   "firstName":"Quamar",

>   "lastName":"Boyer",

>   "email":"faly\@gmail.com",

>   "phone":"+247-92-9848064"

>   },

>   "currentStatus":3,

>   "totalAmount":105,

>   "totalTaxAmount":5,

>   "amountOutstanding":-425.3,

>   "accountTimezone":null,

>   "venueTimezone":null,

>   "createdDate":"2015-01-07 09:21:53 UTC",

>   "modifiedDate":"2016-04-06 07:51:56 UTC",

>   "dateEventStart":"2015-06-01 00:00:00 UTC",

>   "dateEventEnd":"2015-06-04 00:00:00 UTC",

>   "isAccommIncluded":true,

>   "dateAccomStart":"2015-06-01 00:00:00 UTC",

>   "dateAccomEnd":"2015-06-27 00:00:00 UTC",

>   "hasPackages":true,

>   "decisionDate":"",

>   "isBeoFinalised":true,

>   57

>   "beoFinalisedDate":"2015-02-09 03:37:39 UTC"

>   }

>   ]

>   }

>   **currentStatus:**

>   One of the following values:

-   1 = Prospective

-   2 = Tentative

-   3 = Confirmed

-   4 = Cancelled

-   5 = Ordering

-   8 = Not Accepted

>   **Additional** [​Filter](#page15)**​Properties**

| modifiedDateBefore | Filter by Modified Date |   | [iVvy Timestamp Format](#page92) |
|--------------------|-------------------------|---|----------------------------------|
|                    |                         |   |                                  |
| modifiedDateAfter  | Filter by Modified Date |   | [iVvy Timestamp Format](#page92) |
|                    |                         |   |                                  |

>   **getBookingListForAccount**

>   The result from this call will be a ​[collection](#page14)​of all the Booking
>   of an account to which the user has access. This call also accepts the
>   ​[pagination](#page14)​parameters. The per page value is required, for example
>   {"perPage":10}

>   *Example: Get Account’s Booking List*

>   **Request:**

>   {"perPage":1}

>   **Response:**

>   {

>   "meta":{

>   "totalResults":325,

>   "start":0,

>   "perPage":1,

>   "count":1

>   },

>   "results":[

>   {

>   "id":1,

>   "venueId":1,

>   "code":"HR5ZASGMQ1",

>   "name":"Some Booking",

>   "eventType":"Holiday",

>   "company":{

>   "id":4,

>   "businessName":"Some Business"

>   },

>   58

>   "contact":{

>   "id":3,

>   "firstName":"Quamar",

>   "lastName":"Boyer",

>   "email":"faly\@gmail.com",

>   "phone":"+247-92-9848064"

>   },

>   "currentStatus":3,

>   "totalAmount":105,

>   "totalTaxAmount":5,

>   "amountOutstanding":-425.3,

>   "accountTimezone":null,

>   "venueTimezone":"Australia/Brisbane",

>   "createdDate":"2015-01-07 09:21:53 UTC",

>   "modifiedDate":"2016-04-06 07:51:56 UTC",

>   "dateEventStart":"2015-06-01 00:00:00 UTC",

>   "dateEventEnd":"2015-06-04 00:00:00 UTC",

>   "isAccommIncluded":true,

>   "dateAccomStart":"2015-06-01 00:00:00 UTC",

>   "dateAccomEnd":"2015-06-27 00:00:00 UTC",

>   "hasPackages":true,

>   "decisionDate":"",

>   "isBeoFinalised":true,

>   "beoFinalisedDate":"2015-02-09 03:37:39 UTC"

>   }

>   ]

>   }

>   **currentStatus:**

>   One of the following values:

-   1 = Prospective

-   2 = Tentative

-   3 = Confirmed

-   4 = Cancelled

-   5 = Ordering

-   8 = Not Accepted

>   **Additional** [​Filter](#page15)**​Properties**

| modifiedDateBefore | Filter by Modified Date |   | [iVvy Timestamp Format](#page92) |
|--------------------|-------------------------|---|----------------------------------|
|                    |                         |   |                                  |
| modifiedDateAfter  | Filter by Modified Date |   | [iVvy Timestamp Format](#page92) |
|                    |                         |   |                                  |

>   **getBooking**

>   The result from this call will be the details of a specific booking to which
>   the user has access. The unique venue identifier is required, for example
>   {“id”:123}

>   *Example: Get a specific Booking*

>   59

>   **Request:**

>   {"id":3}

>   **Response:**

>   {

>   "id":3,

>   "venueId":1,

>   "code":"123a",

>   "name":"Ava Donovan",

>   "eventType":"Holiday",

>   "company":null,

>   "contact":null,

>   "currentStatus":3,

>   "totalAmount":2600,

>   "totalTaxAmount":0,

>   "amountOutstanding":2600,

>   "accountTimezone":"Australia/Brisbane",

>   "venueTimezone":"Australia/Brisbane",

>   "createdDate":"2015-01-21 09:50:49 UTC",

>   "modifiedDate":"2016-04-06 07:51:56 UTC",

>   "dateEventStart":"1996-02-19 00:00:00 UTC",

>   "dateEventEnd":"2002-11-06 00:00:00 UTC",

>   "isAccommIncluded":false,

>   "dateAccomStart":"",

>   "dateAccomEnd":"",

>   "hasPackages":true,

>   "decisionDate":"",

>   "isBeoFinalised":false,

>   "beoFinalisedDate":"",

>   "dailyRevenue":[

>   {

>   "costcenterId":1276,

>   "revenueDate":"2015-09-04",

>   "totalAmount":2500,

>   "totalTaxAmount":227.273

>   },

>   {

>   "costcenterId":1277,

>   "revenueDate":"2015-09-04",

>   "totalAmount":2500,

>   "totalTaxAmount":227.273

>   },

>   {

>   "costcenterId":1278,

>   "revenueDate":"2015-09-04",

>   "totalAmount":2500,

>   "totalTaxAmount":227.273

>   },

>   {

>   "costcenterId":1279,

>   "revenueDate":"2015-09-04",

>   "totalAmount":2500,

>   "totalTaxAmount":227.273

>   }

>   ]

>   }

>   60

>   **currentStatus:**

>   One of the following values:

-   1 = Prospective

-   2 = Tentative

-   3 = Confirmed

-   4 = Cancelled

-   5 = Ordering

-   8 = Not Accepted

>   **getVenueRoomList**

>   The result from this call will be a ​[collection](#page14)​of all the rooms of
>   an venue to which the user has access. This call also accepts the
>   ​[pagination](#page14)​parameters. The venueId is required, for example
>   {"venuId":10}

>   *Example: Get a specific Venue’s Room List*

>   **Request:**

>   {"venueId":1}

>   **Response:**

>   {

>   "meta":{

>   "totalResults":1,

>   "start":0,

>   "perPage":null,

>   "count":1

>   },

>   "results":[

>   {

>   "id":1,

>   "code":"2-1",

>   "name":"Family RoomFamily",

>   "description":"\<p\>The best family rooms:\</p\> \<ul\>\<li\>One double
>   bed\</li\> \<li\>Two child beds\</li\> \<li\>Sitting area\</li\>
>   \<li\>Balcony\</li\> \</ul\>",

>   "numStandardAdults":2,

>   "numExtraAdults":1,

>   "extraAdultCost":100,

>   "canSmoke":false,

>   "capacity":10,

>   "marketplaceName":null

>   }

>   ]

>   }

>   **getVenueRatePlanList**

>   The result from this call will be a ​[collection](#page14)​of all the rate
>   plans of an venue to which

>   61

>   the user has access. This call also accepts the
>   ​[pagination](#page14)​parameters. The venueId is required, for example
>   {"venuId":10}

>   *Example: Get a specific Venue’s Rate Plan List*

>   **Request:**

>   {"venueId":1}

>   **Response:**

>   {

>   "meta":{

>   "totalResults":2,

>   "start":0,

>   "perPage":null,

>   "count":2

>   },

>   "results":[

>   {

>   "id":1,

>   "name":"Basic Rate Plan",

>   "code":"2-1",

>   "description":"\<p\>Basic Room Pan\</p\> "

>   },

>   {

>   "id":2,

>   "name":"Luxrious Plan",

>   "code":"2-2",

>   "description":"\<p\>\<strong\>This is bit good:) here
>   \&\#160;\</strong\>\</p\> "

>   }

>   ]

>   }

>   **addItemsToBooking**

>   You can add one or more items to a booking with this API. The venueId and
>   BookingId is required. Multiple items can be added together. There must be
>   at least one additional item.

>   **Parameters**

| venueId  | The unique id of the venue to which the booking      | Required               |                        |           |   |   |
|----------|------------------------------------------------------|------------------------|------------------------|-----------|---|---|
|          | belongs                                              | Must be a valid number |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
| bookingI | The unique id of the booking to which the additional | Required               |                        |           |   |   |
| d        | items will be added                                  | Must be a valid number |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
| items    | Array of multiple items with additional item details | There must be at least |                        |           |   |   |
|          |                                                      | one additional item.   |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          | 62                                                   |                        |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | description            | The complete           | String    |   |   |
|          |                                                      |                        | description of the     |           |   |   |
|          |                                                      |                        | additional item        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | quantity               | The quantity of the    | Number    |   |   |
|          |                                                      |                        | additional item        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | salePrice              | The sale price per     | Number    |   |   |
|          |                                                      |                        | quantity of the        |           |   |   |
|          |                                                      |                        | additional item. This  |           |   |   |
|          |                                                      |                        | amount will be         |           |   |   |
|          |                                                      |                        | interpreted as         |           |   |   |
|          |                                                      |                        | including or           |           |   |   |
|          |                                                      |                        | excluding a tax        |           |   |   |
|          |                                                      |                        | component based        |           |   |   |
|          |                                                      |                        | on the venue’s tax     |           |   |   |
|          |                                                      |                        | settings.              |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | salePriceHasTa         | Whether or not the     | Boolean   |   |   |
|          |                                                      | x                      | sale price of the      |           |   |   |
|          |                                                      |                        | additional item has a  |           |   |   |
|          |                                                      |                        | tax component          |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | salePriceTaxId         | The unique identifier  | Number    |   |   |
|          |                                                      |                        | of the venue tax.      |           |   |   |
|          |                                                      |                        | Use getTaxList api     |           |   |   |
|          |                                                      |                        | to get the list of     |           |   |   |
|          |                                                      |                        | venue taxes.           |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | cost                   | The cost per           | Number    |   |   |
|          |                                                      |                        | quantity of the        |           |   |   |
|          |                                                      |                        | additional item        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | costHasTax             | Whether or not the     | Boolean   |   |   |
|          |                                                      |                        | cost of the additional |           |   |   |
|          |                                                      |                        | item has a tax         |           |   |   |
|          |                                                      |                        | component              |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | costCentreId           | The unique identifier  | Number    |   |   |
|          |                                                      |                        | of the cost centre to  |           |   |   |
|          |                                                      |                        | which the additional   |           |   |   |
|          |                                                      |                        | item will be assigned  |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | costCentreType         | The type of cost       | Number    |   |   |
|          |                                                      |                        | centre to which the    |           |   |   |
|          |                                                      |                        | additional item will   |           |   |   |
|          |                                                      |                        | be assigned            |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
| 63       |                                                      |                        |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | startDate              | Optionally the start   | Timestamp |   |   |
|          |                                                      |                        | date of the            |           |   |   |
|          |                                                      |                        | additional item,       |           |   |   |
|          |                                                      |                        | which must fall        |           |   |   |
|          |                                                      |                        | within the dates of    |           |   |   |
|          |                                                      |                        | the booking            |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | endDate                | Optionally the end     | Timestamp |   |   |
|          |                                                      |                        | date of the            |           |   |   |
|          |                                                      |                        | additional item,       |           |   |   |
|          |                                                      |                        | which must fall        |           |   |   |
|          |                                                      |                        | within the dates of    |           |   |   |
|          |                                                      |                        | the booking            |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      | excludedFromC          | Whether or not         | Boolean   |   |   |
|          |                                                      | ommissions             | agents receive         |           |   |   |
|          |                                                      |                        | commission for the     |           |   |   |
|          |                                                      |                        | additional item        |           |   |   |
|          |                                                      |                        |                        |           |   |   |
|          |                                                      |                        |                        |           |   |   |

>   **Returns**

| success              | Whether or not the items were added to the booking                              |   |
|----------------------|---------------------------------------------------------------------------------|---|
|                      |                                                                                 |   |
| items                | The unique identifiers of the additional items in the same order as the request |   |
|                      |                                                                                 |   |
| **Throws**           |                                                                                 |   |
| Specific Code: 24140 | There must be at least one additional item                                      |   |
|                      |                                                                                 |   |
| Specific Code: 24141 | An additional item has invalid data                                             |   |
|                      |                                                                                 |   |

>   *Example: Add items to booking*

>   **Request:**

>   {

>   "venueId":2,

>   "bookingId":2,

>   "items":[

>   {

>   "description":"The complete description of the additional item",

>   "quantity":10,

>   "salePrice":500,

>   "salePriceHasTax":true,

>   "salePriceTaxId":2,

>   "cost":15,

>   "costHasTax":true,

>   "costCentreId":5,

>   "costCentreType":2,

>   "startDate":"2015-01-19 00:00:00 UTC",

>   64

>   "endDate":"2015-01-22 00:00:00 UTC",

>   "excludedFromCommissions":true,

>   }

>   ]

>   }

>   **Response:**

>   {

>   "success":true,

>   "items":[

>   501

>   ]

>   }

>   **addPaymentToBooking**

>   We can add the payment details of a booking using this API. The venueId,
>   Booking Id and payment details are required. This will also create a payment
>   and booking invoice.

>   **Parameters**

| venueId  |    | The unique id of the venue to which the booking        | Required         |                 |   |                        |
|----------|----|--------------------------------------------------------|------------------|-----------------|---|------------------------|
|          |    | belongs                                                |                  |                 |   | Must be a valid number |
|          |    |                                                        |                  |                 |   |                        |
|          |    |                                                        |                  |                 |   |                        |
| bookingI |    | The unique id of the booking to which the payment will | Required         |                 |   |                        |
| d        |    | be added                                               |                  |                 |   | Must be a valid number |
|          |    |                                                        |                  |                 |   |                        |
|          |    |                                                        |                  |                 |   |                        |
| payment  |    |                                                        |                  |                 |   | The payment details to |
|          |    | paidDate                                               | The date & time  | Timestamp in    |   | add to the booking     |
|          |    |                                                        |                  |                 |   |                        |
|          |    |                                                        | of the payment   | UTC             |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          |    | amountPaid                                             | The payment      | Must be a valid |   |                        |
|          |    |                                                        | amount           | number          |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          |    | paymentMethod                                          | The payment      | 0=Unknown,      |   |                        |
|          |    |                                                        | method           | 1=Credit Card,  |   |                        |
|          |    |                                                        |                  | 2=BPay,         |   |                        |
|          |    |                                                        |                  | 3=Direct        |   |                        |
|          |    |                                                        |                  | Deposit,        |   |                        |
|          |    |                                                        |                  | 4=PayPal,       |   |                        |
|          |    |                                                        |                  | 5=Cheque,       |   |                        |
|          |    |                                                        |                  | 6=Cash,         |   |                        |
|          |    |                                                        |                  | 7=Custom        |   |                        |
|          |    |                                                        |                  | Gateway,        |   |                        |
|          |    |                                                        |                  | 8=Accounts      |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          | 65 |                                                        |                  |                 |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          |    |                                                        |                  | Receivable,     |   |                        |
|          |    |                                                        |                  | 9=EFTPOS,       |   |                        |
|          |    |                                                        |                  | 10=WriteOff,    |   |                        |
|          |    |                                                        |                  | 11=Point of     |   |                        |
|          |    |                                                        |                  | Sale,           |   |                        |
|          |    |                                                        |                  | 12=Wire         |   |                        |
|          |    |                                                        |                  | Transfer,       |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          |    | receiptNum                                             | A receipt        | string          |   |                        |
|          |    |                                                        | number of the    |                 |   |                        |
|          |    |                                                        | payment          |                 |   |                        |
|          |    |                                                        | transaction      |                 |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          |    | notes                                                  | Additional notes | string          |   |                        |
|          |    |                                                        | about the        |                 |   |                        |
|          |    |                                                        | payment          |                 |   |                        |
|          |    |                                                        |                  |                 |   |                        |
|          |    |                                                        |                  |                 |   |                        |

>   **Returns**

| success              | Whether or not the payment was added to the booking         |   |
|----------------------|-------------------------------------------------------------|---|
|                      |                                                             |   |
| invoiceId            | The unique id of the invoice to which the payment was added |   |
|                      |                                                             |   |
| paymentI             | The unique identifier of the payment made                   |   |
| d                    |                                                             |   |
|                      |                                                             |   |
| **Throws**           |                                                             |   |
| Specific Code: 24136 | The payment details are invalid                             |   |
|                      |                                                             |   |

>   *Example: Add payment to booking*

>   **Request:**

>   {

>   "venueId":2,

>   "bookingId":2,

>   "payment":{

>   "paidDate":"2015-01-22 00:00:00",

>   "amountPaid":100,

>   "paymentMethod":6,

>   "receiptNum":12345,

>   "notes":"Note for payment"

>   }

>   }

>   **Response:**

>   {

>   "Success":true,

>   "invoiceId":1736,

>   66

>   "paymentId":758

>   }

>   **addRefundToBooking**

>   We can add a refund to a booking using this API. The venueId, Booking Id and
>   refund details are required. All invoice of the booking will be check for
>   the refunded amount and if the amount is refundable then only the refund
>   amount will be added to invoice.

>   **Parameters**

| venueId              |                                                               |   | The unique id of the venue to which the booking          | Required                                           |    |                  |                 |                              |                        |                       |   |
|----------------------|---------------------------------------------------------------|---|----------------------------------------------------------|----------------------------------------------------|----|------------------|-----------------|------------------------------|------------------------|-----------------------|---|
|                      |                                                               |   | belongs                                                  |                                                    |    |                  |                 |                              | Must be a valid number |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| bookingI             |                                                               |   | The unique id of the booking to which the refund will be | Required                                           |    |                  |                 |                              |                        |                       |   |
| d                    |                                                               |   | added                                                    |                                                    |    |                  |                 |                              | Must be a valid number |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| refund               |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        | The paymentdetails to |   |
|                      |                                                               |   |                                                          | refundDate                                         |    | The date & time  | Timestamp in    |                              | add to the booking     |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    | of the refund    | UTC             |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          | amount                                             |    | The refund       | Must be a valid |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    | amount           | number          |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          | notes                                              |    | Additional notes | string          |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    | about the refund |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| **Returns**          |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| success              |                                                               |   |                                                          | Whether or not the refund was added to the booking |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| refundDet            |                                                               |   |                                                          | A collection of invoiceId and refundId values      |    |                  |                 |                              |                        |                       |   |
| ails                 |                                                               |   |                                                          | invoiceId                                          |    |                  |                 | The unique id of the invoice |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          | refundId                                           |    |                  |                 | The id of the invoice refund |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| **Throws**           |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| Specific Code: 24149 | The refund details are invalid                                |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| Specific Code: 24145 | The booking does not have an amount that can be refunded      |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
| Specific Code: 24146 | Cannot refund more than the total amount payable on a booking |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    |    |                  |                 |                              |                        |                       |   |
|                      |                                                               |   |                                                          |                                                    | 67 |                  |                 |                              |                        |                       |   |

![](media/3a238a347dec95d6b75b50d28f2500b0.jpg)

>   Specific Code: 24147 The refund amount must be greater than zero

>   Specific Code: 24148 The full refund amount could not be applied to the
>   booking

>   *Example: Add refund to booking*

>   **Request:**

>   {

>   "venueId":2,

>   "bookingId":2,

>   "refund":{

>   "refundDate":"2015-01-22 00:00:00 UTC",

>   "amount":100,

>   "notes":"Note for refund"

>   }

>   }

>   **Response:**

>   {

>   "Success":true,

>   "refundDetails":[

>   {

>   "invoiceId":1736,

>   "refundId":180

>   }

>   ]

>   }

>   **getTaxList**

>   This API will return all applicable tax list for the venue. venueId is
>   required parameter to get the list of taxes.

>   **Parameters**

| venueId | The unique identifier of venue to which | Must be an integer |
|---------|-----------------------------------------|--------------------|
|         | taxes belong                            | greater than 0     |
|         |                                         |                    |

>   **Returns**

>   A collection object with the following properties in the results

| id   | The unique invoice identifier |
|------|-------------------------------|
|      |                               |
| name | The name of Tax               |
|      |                               |

>   *Example: Get Venues Tax List*

>   **Request:**

>   {"venueId":2}

>   **Response:**

>   {

>   "meta":{

>   "totalResults":1,

>   "start":0,

>   68

>   "perPage":1,

>   "count":1

>   },

>   "results":[

>   {

>   "id":2,

>   "name":"GST"

>   }

>   ]

>   }

>   **Marketplace Namespace (marketplace)**

>   **getVenueList**

>   This api call allows you to search the iVvy marketplace for venues that
>   match the following criteria:

-   countryCode (required): The 2 letter country code (ISO_3166-1) of the venue

-   city (optional): The location city of the venue. Currently one of the
    following values:

    -   brisbane-qld

    -   sydney-nsw

-   eventTypes (optional): One or more of the following event types for which
    the venue can provide:

    -   11 = Event

    -   21 = Wedding

    -   31 = Conference

    -   41 = Meeting

-   availabilityStartDate (optional): The start date of the period from which to
    include the function space availability details of the venues. The value
    must be a string with the format YYYY-MM-DD, for example: 2015-05-20

-   availabilityEndDate (optional): The end date of the period from which to
    include the function space availability details of the venues. The value
    must be a string with the format YYYY-MM-DD, for example: 2015-05-25

>   This call also accepts the pagination parameters. By default, only the first
>   10 venues will be returned.

>   *Example: Find all the venues in Brisbane that can provide weddings. Include
>   their availability from 1st July 2015 to 7th July 2015*

>   **Request:**

>   {

>   "countryCode": "AU",

>   "city": "brisbane-qld",

>   69

>   "eventTypes": [11],

>   "availabilityStartDate": "2015-07-01",

>   "availabilityEndDate": "2015-07-07"

>   }

>   **Response:**

>   A collection of venues that match the criteria. A single venue will be
>   represented by the following json example:

>   {

>   "id": 21,

>   "hashId": "1efda3e35a75aabd13e8996037d35a79",

>   "businessName": "iVvy Conference Centre",

>   "businessNumber": 123123,

>   "phone": "1300 004 889",

>   "fax": "",

>   "websiteAddress": "",

>   "emailAddress": "james.greig\@ivvy.com",

>   "description": "\<p\> Located by the River at Hamilton, this is the closest
>   5 star, full service Hotel to the Brisbane Cruise Terminal - Portside at
>   Hamilton, the Airport precinct, Gateway Arterial Bridge linking the Gold
>   Coast to the Sunshine Coast and is just minutes from the CBD.\<br /\>\<br
>   /\> Featuring 90 spacious, newly refurbished and well appointed
>   accommodation rooms, the hotel is an urban escape perfect for business or
>   leisure travellers alike. Most rooms feature magnificent views of the widest
>   reach of the Brisbane River spanning from the Brisbane City past the
>   Brisbane Cruise Terminal and to the Gateway Bridge.\<br /\>\<br /\> Enjoy
>   the resort style pool, spa, sauna, gym and complimentary car parking \&amp;
>   Wi-Fi for all delegates, guests and visitors.\<br /\>\<br /\> From the
>   grandeur of the column free Hamilton Ballroom which can easily divide into
>   smaller configurations, the intimacy of the Newstead Room or take advantage
>   of the newly refurbished Executive Boardroom the Brisbane Riverview Hotel
>   has an option to suit your budget and requirements. The resort style pool
>   area is a fantastic venue for breakout sessions or lunches. This is a
>   flexible and well equipped conference venue can cater for intimte boardroom
>   meeting of 6 people up to large corporate events for up to 300 delegates.
>   \<br /\>\<br /\> With expansive river views, Plates Restaurant offers a
>   seasonal menu showcasing superb produce from Queensland\&\#8217;s freshest
>   seafood, international cuisine, and wood fired steaks and pizzas. It is the
>   perfect place for business or pleasure, mixing excellent atmosphere with
>   great service.\</p\> ",

>   "checkinTime": "11:00:00",

>   "checkoutTime": "14:00:00",

>   "childAge": 0,

>   "infantAge": 0,

>   "currencyCode": "AUD",

>   "localeCode": "en_AU",

>   "timezone": "Australia/Brisbane",

>   "hasSpaces": true,

>   "hasAccommodation": true,

>   "numMeetingRooms": 0,

>   "numAccommodationRooms": 200,

>   "maxSpaceArea": null,

>   "totalSpaceArea": null,

>   "longitude": 153.4065773,

>   "latitude": -28.0067947,

>   "primaryAddress": {

>   "line1": "2 Boston Court",

>   "line2": "",

>   "line3": "",

>   "line4": "",

>   70

>   "city": "Varsity Lakes",

>   "stateCode": "QLD",

>   "stateName": null,

>   "countryCode": "AU",

>   "countryName": null,

>   "postalCode": 4227

>   },

>   "instantBookUrl":

>   "http://stagemarketplace.ivvy.com/order/start?v=1efda3e35a75aabd13e8996037d35a79",
>   "availability": {

>   "2015-05-20": {

>   "isAvailable": true

>   },

>   "2015-05-21": {

>   "isAvailable": true

>   },

>   "2015-05-22": {

>   "isAvailable": true

>   },

>   "2015-05-23": {

>   "isAvailable": true

>   },

>   "2015-05-24": {

>   "isAvailable": true

>   },

>   "2015-05-25": {

>   "isAvailable": true

>   },

>   "2015-05-26": {

>   "isAvailable": true

>   }

>   }

>   }

>   **getVenue**

>   The result from this call will be the public details of a specific venue in
>   the iVvy marketplace. The unique venue hash identifier is required, for
>   example {“hashId”:”abcdefghijklmnop”}.

>   This call also accepts the ​*availabilityStartDate* and ​*availabilityEndDate*
>   parameters that are described by ​[getVenueList](#page50)​. The behaviour is
>   the same as getVenueList, but for only for the specific venue.

>   *Example: Get a specific venue and it’s availability from 1st July 2015 to
>   7th July 2015*

>   **Request:**

>   {

>   "hashId": "1efda3e35a75aabd13e8996037d35a79",

>   "availabilityStartDate": "2015-07-01",

>   "availabilityEndDate": "2015-07-07"

>   }

>   **Response:**

>   71

>   {

>   "id": 21,

>   "hashId": "1efda3e35a75aabd13e8996037d35a79",

>   "businessName": "iVvy Conference Centre",

>   "businessNumber": 123123,

>   "phone": "1300 004 889",

>   "fax": "",

>   "websiteAddress": "",

>   "emailAddress": "james.greig\@ivvy.com",

>   "description": "\<p\> Located by the River at Hamilton, this is the closest
>   5 star, full service Hotel to the Brisbane Cruise Terminal - Portside at
>   Hamilton, the Airport precinct, Gateway Arterial Bridge linking the Gold
>   Coast to the Sunshine Coast and is just minutes from the CBD.\<br /\>\<br
>   /\> Featuring 90 spacious, newly refurbished and well appointed
>   accommodation rooms, the hotel is an urban escape perfect for business or
>   leisure travellers alike. Most rooms feature magnificent views of the widest
>   reach of the Brisbane River spanning from the Brisbane City past the
>   Brisbane Cruise Terminal and to the Gateway Bridge.\<br /\>\<br /\> Enjoy
>   the resort style pool, spa, sauna, gym and complimentary car parking \&amp;
>   Wi-Fi for all delegates, guests and visitors.\<br /\>\<br /\> From the
>   grandeur of the column free Hamilton Ballroom which can easily divide into
>   smaller configurations, the intimacy of the Newstead Room or take advantage
>   of the newly refurbished Executive Boardroom the Brisbane Riverview Hotel
>   has an option to suit your budget and requirements. The resort style pool
>   area is a fantastic venue for breakout sessions or lunches. This is a
>   flexible and well equipped conference venue can cater for intimte boardroom
>   meeting of 6 people up to large corporate events for up to 300 delegates.
>   \<br /\>\<br /\> With expansive river views, Plates Restaurant offers a
>   seasonal menu showcasing superb produce from Queensland\&\#8217;s freshest
>   seafood, international cuisine, and wood fired steaks and pizzas. It is the
>   perfect place for business or pleasure, mixing excellent atmosphere with
>   great service.\</p\> ",

>   "checkinTime": "11:00:00",

>   "checkoutTime": "14:00:00",

>   "childAge": 0,

>   "infantAge": 0,

>   "currencyCode": "AUD",

>   "localeCode": "en_AU",

>   "timezone": "Australia/Brisbane",

>   "hasSpaces": true,

>   "hasAccommodation": true,

>   "numMeetingRooms": 0,

>   "numAccommodationRooms": 200,

>   "maxSpaceArea": null,

>   "totalSpaceArea": null,

>   "longitude": 153.4065773,

>   "latitude": -28.0067947,

>   "primaryAddress": {

>   "line1": "2 Boston Court",

>   "line2": "",

>   "line3": "",

>   "line4": "",

>   "city": "Varsity Lakes",

>   "stateCode": "QLD",

>   "stateName": null,

>   "countryCode": "AU",

>   "countryName": null,

>   "postalCode": 4227

>   },

>   "instantBookUrl":

>   72

>   "http://stagemarketplace.ivvy.com/order/start?v=1efda3e35a75aabd13e8996037d35a79",
>   "availability": {

>   "2015-07-01": {

>   "isAvailable": true

>   },

>   "2015-07-02": {

>   "isAvailable": true

>   },

>   "2015-07-03": {

>   "isAvailable": true

>   },

>   "2015-07-04": {

>   "isAvailable": true

>   },

>   "2015-07-05": {

>   "isAvailable": true

>   },

>   "2015-07-06": {

>   "isAvailable": true

>   },

>   "2015-07-07": {

>   "isAvailable": true

>   }

>   },

>   "videoUrls": ["https://www.youtube.com/embed/rxiPVWurK7Q"],

>   "airportName": "Gold Coast (OOL)",

>   "airportDistance": 20,

>   "starRating": 5,

>   "ratingAuthority": 2,

>   "maxSpaceCapacity": 100,

>   "facilities": [2, 3, 6, 12, 14, 19, 20, 24, 27, 30, 31, 34, 35],

>   "mainImage": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/55403b462c0aa.jpg",

>   "originalFileName": "main function sapce 2.jpg",

>   "tags": [],

>   "size": 2647159,

>   "contentType": "image/jpeg"

>   },

>   "marketplaceBannerImage": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/banner/banner.jpg",

>   "originalFileName": "banner.jpg",

>   "tags": [],

>   "size": 2963936,

>   "contentType": "image/jpeg"

>   },

>   "brochureFile": null,

>   "imageLibrary": [{

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   imageLibrary/5513b498229a6.jpg",

>   "originalFileName":

>   "58443-room-types-5-vibe-hotel-sydney-executive-king.jpg",

>   "tags": ["General"],

>   73

>   "size": 46333,

>   "contentType": "image/jpeg",

>   "marketplaceEventTypes": [21]

>   }],

>   "packages": [{

>   "marketplaceName": "Day Delegate Package",

>   "marketplaceEventTypes": [11, 21],

>   "minPax": 30,

>   "price": 98,

>   "priceMethod": 1,

>   "smallDescription": "At iVvy Conference Centre, intimate spaces are combined
>   with state-of-the-art technology and award-winning food. Our Day Delegate
>   Package is ideal for small to medium meetings or events, offering a range of
>   menus for your attendees",

>   "largeDescription": "\<p\> At iVvy Conference Centre, intimate spaces are
>   combined with state-of-the-art technology and award-winning food. Our Day
>   Delegate Package is ideal for small to medium meetings or events, offering a
>   range of menus designed by our team of chefs to create a unique dining
>   experience for your

>   attendees.\</p\> \<p\> At just \$98 per person, our Day Delegate Package
>   includes the following:\</p\> \<ul\>\<li\> Venue hire\</li\> \<li\>
>   Pre-installed technical equipment

>   and services including\&\#160;a high definition projector or display, a PA
>   system and a\&\#160;presentation computer\</li\> \<li\> Free Wi-Fi\</li\>
>   \<li\> Notepads and pens\</li\> \<li\> Iced water and sweets\</li\> \<li\>
>   Tea and coffee on arrival\</li\> \<li\> Morning tea\</li\> \<li\> Networking
>   lunch\</li\> \<li\> Afternoon tea.\</li\> \</ul\>"

>   }],

>   "functionSpaces": [{

>   "marketplaceName": "River Room",

>   "marketplaceEventTypes": [11, 21],

>   "description": "\<p\> Ocean and river views are a focal point of the River
>   room. This room has floor-to-ceiling glass with full length curtains if
>   required, and access to a large, central area for meet-and-greets or
>   pre-dinner cocktails. The large projector screen is perfect for meetings or
>   special events and this room has been fully soundproofed for privacy.\</p\>
>   ",

>   "area": null,

>   "length": null,

>   "width": null,

>   "heightMaximum": null,

>   "heightMinimum": null,

>   "floorPressureMaximum": null,

>   "minPax": 30,

>   "maxPax": 400,

>   "hasLayouts": true,

"image": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/spaces/169/5540362637d5f.jpg",

>   "originalFileName": "River Room.jpg",

>   "tags": [],

>   "size": 67933,

>   "contentType": "image/jpeg"

>   },

>   "layouts": [{

>   "type": 7,

>   "paxMinimum": null,

>   "paxMaximum": 400,

>   "timeForSetup": null,

>   74

>   "timeForTakedown": null

>   }, {

>   "type": 6,

>   "paxMinimum": null,

>   "paxMaximum": 150,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "type": 1,

>   "paxMinimum": null,

>   "paxMaximum": 250,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "type": 5,

>   "paxMinimum": null,

>   "paxMaximum": 80,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "type": 8,

>   "paxMinimum": null,

>   "paxMaximum": 50,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "type": 4,

>   "paxMinimum": null,

>   "paxMaximum": 100,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }, {

>   "type": 3,

>   "paxMinimum": null,

>   "paxMaximum": 100,

>   "timeForSetup": null,

>   "timeForTakedown": null

>   }]

>   }],

>   "accommodation": [{

>   "code": "14-53",

>   "marketplaceName": "Studio",

>   "description": "\<ul\>\<li\> A studio apartment sleeps 1-5 and contains a
>   queen bed plus a sofa that can folded out to a double bed.\</li\> \<li\>
>   Rollaways also available.\</li\> \</ul\>",

>   "numStandardAdults": 1,

>   "numExtraAdults": 1,

>   "extraAdultCost": 0,

>   "canSmoke": false,

>   "capacity": 20,

"image": {

>   "url":

>   "https://s3-ap-southeast-2.amazonaws.com/ap-southeast-2.accounts.ivvy.com/account14/

>   venues/21/accommodation/53/5540352c9c2ca.jpg",

>   "originalFileName": "Studio.jpg",

>   "tags": [],

>   "size": 48330,

>   75

>   "contentType": "image/jpeg"

>   }

>   }]

>   }

>   The following are properties in the example json response above that have
>   special values.

>   **ratingAuthority**

>   One of the following values:

-   1 = AAA rated

-   2 = Self rated

>   **facilities**

>   An array of the following values:

-   1 = Air Conditioning

-   2 = Airport Shuttle

-   3 = Audio Visual

-   4 = BBQ

-   6 = Business Centre

-   7 = Ceremony On Site

-   8 = Child Minding

-   9 = Disabled Access

-   10 = Dry Cleaning

-   11 = Express Checkout

-   12 = Free Parking

-   13 = Gaming Area

-   14 = Gymnasium

-   15 = Internet Access

-   16 = Laundry

-   39 = Liquor License

-   17 = Mobile Bar

-   18 = Open 24 Hours

-   19 = Outdoor Area

-   20 = Parking Available

-   21 = Pay TV

-   22 = Playground

-   23 = Printing Services

-   24 = Public Transport

-   25 = Restaurant On Site

-   26 = Sauna Steam Room

-   27 = Smoking Permitted

-   28 = Spa

-   29 = Staging

>   76

-   30 = Street Parking

-   31 = Swimming Pool

-   32 = Tour Desk

-   33 = Undercover Parking

-   34 = Valet Parking

-   35 = Wheelchair Access

-   36 = Wifi Access

-   37 = Outside Catering Allowed

-   38 = BYO Allowed

>   **priceMethod (package pricing)**

>   One of the following values:

-   1 = Per person

-   2 = Flat rate

>   **type (function space layout)**

>   One of the following values:

-   0 = Custom

-   1 = Theatre

-   2 = Classroom

-   3 = U-Shape

-   4 = Cabaret

-   5 = Boardroom

-   6 = Banquet

-   7 = Cocktail

-   8 = Hollow Square

>   **marketplaceEventTypes (packages, function spaces and image library
>   files)**

>   An array of the following values:

-   11 = Event

-   21 = Wedding

-   31 = Conference

-   41 = Meeting

>   **Invoice Namespace (invoice)**

>   **getInvoiceList**

>   **Parameters**

| perPage |                                               | The number of invoices to get in a single api | Must be an integer |
|---------|-----------------------------------------------|-----------------------------------------------|--------------------|
|         |                                               | call                                          | greater than 0     |
|         |                                               |                                               |                    |
|         | 77                                            |                                               |                    |
| start   | The starting result of the page. Note this is | Must be an integer                            |                    |
|         | zero based (i.e. sending start=0 will start   | 0 or greater                                  |                    |
|         | from the first result.)                       |                                               |                    |
|         |                                               |                                               |                    |

>   **Additional ​**[Filter](#page15)**​Properties**

| fromModifiedDate | Filter by Modified Date     |                      | [iVvy Timestamp Format](#page92) |   |   |
|------------------|-----------------------------|----------------------|----------------------------------|---|---|
|                  |                             |                      |                                  |   |   |
| toModifiedDate   | Filter by Modified Date     |                      | [iVvy Timestamp Format](#page92) |   |   |
|                  |                             |                      |                                  |   |   |
| venueId          | Filter invoices that belong |                      | Must be an integer               |   |   |
|                  | to a specific Venue         |                      | greater than 0                   |   |   |
|                  |                             |                      |                                  |   |   |
| refType          | Filter by a specific        |                      | Must be an integer               |   |   |
|                  | reference type              |                      |                                  |   |   |
|                  | The reference type of the   |                      |                                  |   |   |
|                  | invoice                     |                      |                                  |   |   |
|                  | 0                           | = Custom             |                                  |   |   |
|                  | 1                           | = Event Registration |                                  |   |   |
|                  | 2                           | = Membership Sign Up |                                  |   |   |
|                  | 3                           | = Membership Renewal |                                  |   |   |
|                  | 4                           | = Venue Booking      |                                  |   |   |
|                  |                             |                      |                                  |   |   |

>   **Returns**

>   A collection object with the following properties in the results

| id             | The unique invoice identifier              |                                                                 |                                           |                                              |   |
|----------------|--------------------------------------------|-----------------------------------------------------------------|-------------------------------------------|----------------------------------------------|---|
|                |                                            |                                                                 |                                           |                                              |   |
| reference      | The unique reference number of the invoice |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| title          | The title of the invoice                   |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| description    | The description of the invoice             |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| currency       | The currency of the invoice                |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| totalCost      | The total of the invoice                   |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| totalTaxCost   | The tax of the invoice                     |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| amountPaid     | The amount paid against the invoice        |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| toContactEmail | The contact email of the invoice           |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| toContactName  | The contact name of the invoice            |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| currentStatus  | The status of the invoice                  |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                | 78                                         |                                                                 |                                           |                                              |   |
|                |                                            | ● 0 = Not Paid                                                  |                                           |                                              |   |
|                |                                            | ● 1 = Un-confirmed Paid                                         |                                           |                                              |   |
|                |                                            | ●                                                               | 2 = Paid                                  |                                              |   |
|                |                                            | ● 3 = Written Off                                               |                                           |                                              |   |
|                |                                            | ●                                                               | 4 = Cancelled                             |                                              |   |
|                |                                            | ●                                                               | 5 = Refunded                              |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| createdDate    |                                            | The created date of the invoice                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| modifiedDate   |                                            | The modified date of the invoice                                |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| refType        |                                            | The reference type of the invoice                               |                                           |                                              |   |
|                |                                            | ●                                                               | 0 = Custom                                |                                              |   |
|                |                                            | ● 1 = Event Registration                                        |                                           |                                              |   |
|                |                                            | ● 2 = Membership Sign Up                                        |                                           |                                              |   |
|                |                                            | ● 3 = Membership Renewal                                        |                                           |                                              |   |
|                |                                            | ● 4 = Venue Booking                                             |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| refId          |                                            | The reference Id of the invoice                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| taxRateUsed    |                                            | The tax rate percent applied to invoice                         |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| isTaxCharged   |                                            | Whether tax charged on the invoice                              |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| paymentDueDate |                                            | Payment due date of the invoice                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| eventId        |                                            | Event Identifier to which invoice is belongs to                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| venueId        |                                            | Venue Identifier to which invoice is belongs to                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| toContactId    |                                            | Contact Id against which invoice is created                     |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| toAddress      |                                            | The “to” Address of the invoice                                 |                                           |                                              |   |
|                |                                            | line1                                                           |                                           | Line 1 of the address (part of the "street") |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | line2                                                           |                                           | Line 2 of the address (part of the "street") |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | line3                                                           |                                           | Line 3 of the address (part of the "street") |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | line4                                                           |                                           | Line 4 of the address (part of the "street") |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | city                                                            |                                           | The city name of the address                 |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | stateCode                                                       | The state code of the address (e.g. QLD)  |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | stateName                                                       | The state name of the address (e.g.       |                                              |   |
|                |                                            |                                                                 |                                           | Queensland)                                  |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | countryCode                                                     | The country code of the address (e.g. AU) |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                | 79                                         |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | countryName                                                     | The country name of the address (e.g.     |                                              |   |
|                |                                            |                                                                 | Australia)                                |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            | postalCode                                                      | The postal code of the address            |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |
| bookingCode    |                                            | The unique reference code of the booking if refType is 4 (Venue |                                           |                                              |   |
|                |                                            | Booking)                                                        |                                           |                                              |   |
|                |                                            |                                                                 |                                           |                                              |   |

>   The result from this call will be a [​collection](#page14)​of all the invoices
>   the user has access to.

>   This call also accepts the [pagination​](#page14)​properties.

>   **getInvoice**

>   **Parameters**

| id                   |                                            | The invoice identifier                                                    | Required       |                                                  |                                              |                                           |   |   |
|----------------------|--------------------------------------------|---------------------------------------------------------------------------|----------------|--------------------------------------------------|----------------------------------------------|-------------------------------------------|---|---|
|                      |                                            |                                                                           |                | Must be an integer                               |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| **Returns**          |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| id                   |                                            | The unique invoice identifier                                             |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| reference            | The unique reference number of the invoice |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| title                |                                            | The title of the invoice                                                  |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| description          | The description of the invoice             |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| currency             |                                            | The currency of the invoice                                               |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| totalCost            |                                            | The total of the invoice                                                  |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| totalTaxCost         | The tax of the invoice                     |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| amountPaid           | The amount paid against the invoice        |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| toContactEmail       | The contact email of the invoice           |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| toContactName        | The contact name of the invoice            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| currentStatus        | The status of the invoice                  |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | ● 0 = Not Paid |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | 80             |                                                  |                                              |                                           |   |   |
|                      |                                            | ● 1 = Un-confirmed Paid                                                   |                |                                                  |                                              |                                           |   |   |
|                      |                                            | ●                                                                         | 2 = Paid       |                                                  |                                              |                                           |   |   |
|                      |                                            | ● 3 = Written Off                                                         |                |                                                  |                                              |                                           |   |   |
|                      |                                            | ●                                                                         | 4 = Cancelled  |                                                  |                                              |                                           |   |   |
|                      |                                            | ●                                                                         | 5 = Refunded   |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| createdDate          |                                            | The created date of the invoice                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| modifiedDate         |                                            | The modified date of the invoice                                          |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| refType              |                                            | The reference type of the invoice                                         |                |                                                  |                                              |                                           |   |   |
|                      |                                            | ●                                                                         | 0 = Custom     |                                                  |                                              |                                           |   |   |
|                      |                                            | ● 1 = Event Registration                                                  |                |                                                  |                                              |                                           |   |   |
|                      |                                            | ● 2 = Membership Sign Up                                                  |                |                                                  |                                              |                                           |   |   |
|                      |                                            | ● 3 = Membership Renewal                                                  |                |                                                  |                                              |                                           |   |   |
|                      |                                            | ● 4 = Venue Booking                                                       |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| refId                |                                            | The reference Id of the invoice                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| taxRateUsed          |                                            | The tax rate percent applied to invoice                                   |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| isTaxCharged         |                                            | Whether tax charged on the invoice                                        |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| paymentDueDate       |                                            | Payment due date of the invoice                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| eventId              |                                            | Event Identifier to which invoice is belongs to                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| venueId              |                                            | Venue Identifier to which invoice is belongs to                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| toContactId          |                                            | Contact Id against which invoice is created                               |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| toAddress            |                                            | The “to” Address of the invoice                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | line1                                                                     |                |                                                  | Line 1 of the address (part of the "street") |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | line2                                                                     |                |                                                  | Line 2 of the address (part of the "street") |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | line3                                                                     |                |                                                  | Line 3 of the address (part of the "street") |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | line4                                                                     |                |                                                  | Line 4 of the address (part of the "street") |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | city                                                                      |                |                                                  | The city name of the address                 |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | stateCode                                                                 |                | The state code of the address (e.g. QLD)         |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | stateName                                                                 |                | The state name of the address (e.g. Queensland)  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | countryCode                                                               |                | The country code of the address (e.g. AU)        |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | countryName                                                               |                | The country name of the address (e.g. Australia) |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      | 81                                         |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | postalCode     |                                                  | The postal code of the address               |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| items                |                                            | List of invoice items                                                     |                |                                                  |                                              |                                           |   |   |
|                      |                                            | Item Details                                                              |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | description    |                                                  | The description of the item                  |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | quantity       |                                                  | Quantity of the item                         |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | unitCost       |                                                  | The unit cost of the item                    |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | totalCost      |                                                  | The total cost of the item                   |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | totalTaxCost   |                                                  | The tax of the item                          |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | amountPaid     |                                                  | The amount paid of the item'                 |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | refType        |                                                  | The reference type of the item               |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| payments             |                                            | List of payments of the invoice                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | Payment Details                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | paymentId      |                                                  |                                              | The identifier of the payment             |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | receiptNum     |                                                  |                                              | The receipt number of the payment         |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | amountPaid     |                                                  |                                              | The amount paid of the payment            |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | notes          |                                                  |                                              | The notes of the payment                  |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | chequeNumber   |                                                  |                                              | The chequeNumber of the payment           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | paymentMethod  |                                                  |                                              | The payment method of the payment         |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | paidDate       |                                                  |                                              | The paid timestamp of the payment         |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | feePercentage  |                                                  |                                              | The percentage fee included in amountPaid |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | feeAmount      |                                                  |                                              | The fee amount included in amountPaid     |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | Note about fee:                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            | If the payment is applied to multiple invoices, the fee amount is applied |                |                                                  |                                              |                                           |   |   |
|                      |                                            | to the first invoice only.                                                |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| **Throws**           |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
| Specific Code: 24137 |                                            | Unable to find invoice                                                    |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           |                |                                                  |                                              |                                           |   |   |
|                      |                                            |                                                                           | 82             |                                                  |                                              |                                           |   |   |

>   The invoice identifier must be provided as part of this call to fetch the
>   specific invoice. E.g. {"id":1} can be used to fetch the details of an
>   invoice with the identifier of 1.

>   **getOptions**

>   The invoice and item response contains a field called "refType". These are
>   constants in the iVvy system to match the invoice or item to a specific
>   entity. To find out a description of what these constants refer to, you can
>   make a call to the api to get the complete list

>   **Parameters**

>   No parameters required.

>   **Returns**

| invoiceRefTypes     | The refType identifier and description of refTypes found in the invoice  |
|---------------------|--------------------------------------------------------------------------|
|                     | response.                                                                |
|                     |                                                                          |
| invoiceLineRefTypes | The refType identifier and description of refTypes found in the items of |
|                     | the invoice response.                                                    |
|                     |                                                                          |
| paymentMethods      | The complete list of payment methods that might appear against a         |
|                     | payment made on an invoice                                               |
|                     |                                                                          |

>   **Account Namespace (account)**

>   **addOrUpdateCostCenter**

>   Add or update cost center details to the account. The cost center name and
>   code are required.

>   **Parameters**

| id          | The unique identifier of the cost center (Leave | Must be a valid number |
|-------------|-------------------------------------------------|------------------------|
|             | empty to add the cost center to the account.)   |                        |
|             |                                                 |                        |
| name        | The name of the cost center                     | Required               |
|             |                                                 | String Value           |
|             |                                                 |                        |
| code        | The code of the cost center                     | Required               |
|             |                                                 | String Value           |
|             |                                                 |                        |
| description | The complete description of the cost center     | Optional               |
|             |                                                 |                        |
|             | 83                                              |                        |

![](media/e6c93cf7c23a68f7202c2ba21e0414e9.jpg)

>   String Value

>   **Returns**

| success              | Whether or not the cost center was added to the account |   |
|----------------------|---------------------------------------------------------|---|
|                      |                                                         |   |
| id                   | The unique identifier of the cost center                |   |
|                      |                                                         |   |
| **Throws**           |                                                         |   |
| Specific Code: 24150 | Account does not exist                                  |   |
|                      |                                                         |   |
| Specific Code: 24150 | The cost centers details are invalid                    |   |
|                      |                                                         |   |

>   *Example: Add a cost center to an account*

>   **Request:**

>   {

>   "name":"test cost center",

>   "code":"AB12",

>   "description":"The complete description of the cost center"

>   }

>   **Response:**

>   {

>   "Success":true,

>   "Id":5452

>   }

>   **getCostCenterList**

>   Fetches the list of cost centers in the account. No request params required.

>   **Returns**

| id                   | The unique identifier of the cost center    |    |
|----------------------|---------------------------------------------|----|
|                      |                                             |    |
| name                 | The name of the cost center                 |    |
|                      |                                             |    |
| code                 | The code of the cost center                 |    |
|                      |                                             |    |
| description          | The complete description of the cost center |    |
|                      |                                             |    |
| defaultType          | Set if one of the default cost centers      |    |
|                      |                                             |    |
| **Throws**           |                                             |    |
| Specific Code: 24150 | Account does not exist                      |    |
|                      |                                             |    |
|                      |                                             | 84 |

>   *Example: get cost center list of the account*

>   **Response:**

>   {

>   "meta":{

>   "totalResults":2,

>   "start":0,

>   "perPage":2,

>   "count":2

>   },

>   "results":[

>   {

>   "id":5451,

>   "name":"test cost center",

>   "code":2,

>   "description":null,

>   "defaultType":null

>   },

>   {

>   "id":5452,

>   "name":"test cost center",

>   "code":"AB12",

>   "description":null,

>   "defaultType":null

>   }

>   ]

>   }

>   **getEmailLogList**

>   The result from this call will be a ​[collection](#page14)​of all the email
>   logs of specific account to which the user has access. This call also
>   accepts the ​[pagination](#page14)​parameters.

>   **Returns**

| id                   | The unique identifier of the email        |   |
|----------------------|-------------------------------------------|---|
|                      |                                           |   |
| contactId            | The contact id of of the email            |   |
|                      |                                           |   |
| userId               | The user id of of the email               |   |
|                      |                                           |   |
| eventId              | The event id of of the email              |   |
|                      |                                           |   |
| type                 | The type of of the email                  |   |
|                      |                                           |   |
| refType              | The reference type id of of the email     |   |
|                      |                                           |   |
| refId                | The reference id of of the email          |   |
|                      |                                           |   |
| from                 | The from address of of the email          |   |
|                      |                                           |   |
| to                   | The to address of the email               |   |
|                      |                                           |   |
|                      | 85                                        |   |
| bcc                  | The bcc of the email                      |   |
|                      |                                           |   |
| subject              | The subject of the email                  |   |
|                      |                                           |   |
| body                 | The body of the email                     |   |
|                      |                                           |   |
| sentTime             | The sent time of the email in UTC         |   |
|                      |                                           |   |
| success              | Whether or not email has been sent or not |   |
|                      |                                           |   |
| **Throws**           |                                           |   |
| Specific Code: 24151 | Account does not exist                    |   |
|                      |                                           |   |

>   *Example: Get a specific account’s Email Logs List*

>   **Response:**

>   {

>   "meta": {

>   "totalResults": 1,

>   "start": 0,

>   "perPage": 100,

>   "count": 1

>   },

>   "results": [

>   {

>   "id": 2,

>   "contactId": 25943,

>   "userId": null,

>   "eventId": 50,

>   "type": 1,

>   "refType": 5,

>   "refId": 184133,

>   "from": "5U2ZD\@V5P7T.com",

>   "to": "8X2PEZ\@FF1UAL.com",

>   "bcc": null,

>   "subject": "CCWXL3A8",

>   "body": "3N5RU3V5",

>   "sentTime": "2013-07-04 07:18:29 UTC",

>   "success": true

>   }

>   ]

>   }

>   **refType:**

>   One of the following values:

-   0 = Other

-   1 = Contact

-   2 = Event

-   3 = Membership

>   86

-   4 = Abstract

-   5 = Registration

-   6 = Invoice

-   7 = Author

-   8 = Task

-   9 = Credit Note

-   10 = Survey

-   11 = Venue Marketplace

-   12 = Booking

-   13 = Company

-   14 = Floor Plan

>   **type:**

>   One of the following values:

-   0 = Unknown

-   1 = Completed Event Registration

-   2 = Completed Event Registration (Waiting on Payment)

-   3 = Accommodation Confirmation

-   4 = Travel Confirmation

-   5 = Registration Payment Reminder

-   8 = Exhibitor Final Confirmation

-   11 = Abstract/Paper Submission Created

-   12 = Abstract/Paper Changes Requested

-   13 = Abstract/Paper Submission Rejected

-   14 = Abstract/Paper Submission Accepted

-   15 = Abstract/Paper Reviewer Added

-   16 = Contact Changed

-   17 = Hotel Changed

-   18 = Flight Changed

-   19 = Tickets Changed

-   20 = Exhibitor Confirmation

-   21 = Session Confirmation

-   22 = Session Changed

-   23 = Abstract Changed

-   24 = Final Confirmation

-   30 = Event Feedback

-   31 = Event Reminder

-   26 = Abstract

-   27 = API Leadtracker

-   28 = Contact Subscribed

-   29 = Transfer Changed

-   32 = Incomplete Registration

-   1000 = Password Reset

>   87

-   1001 = Notification

-   1002 = Task

-   1500 = Statement

-   1501 = Invoice

-   1502 = Credit Note

-   2000 = Membership Signup

-   2001 = Membership Renewal

-   2002 = Renewal Notice

-   3000 = Survey

-   1003 = New Company Added

-   4000 = Venue Booking Document

-   4001 = Venue Booking Floor Plan

>   **Appendix A: Algorithms/Code**

>   **Calculating MD5**

>   The body of the request must have an MD5 hash calculated to ensure the body
>   has not been altered during transport. It is important this is calculated
>   the same as the iVvy API server to ensure the signature is calculated
>   correctly and the request is authorized.

>   *Bash (Linux Command Line)*

-   echo -e "string to hash" \| md5sum 2fcc83d76f9b2d8ef372271d807a3364 -

>   Note that any white space either side of the string will also be hashed,
>   creating a different hash

>   \$ echo -e " string to hash " \| md5sum

>   6b9202a3b05bd22803fe54767b30ee10 -

>   It is important you strip off any whitespace before hashing the string.

>   Note also it is possible to hash an empty string (in the case there is no
>   body in the request)...

-   echo -e -n "" \| md5sum d41d8cd98f00b204e9800998ecf8427e -

>   88

>   *C\#*

>   // Convert a string to a MD5 hash

>   static private string GetMd5Hash(string input) {

>   MD5 md5Hash = MD5.Create();

>   byte[] data = md5Hash.ComputeHash(Encoding.UTF8.GetBytes(input)); return
>   ByteToString(data);

>   }

-   Helper function to convert a byte array to a string. static private string
    ByteToString(byte[] data) {

>   StringBuilder sBuilder = new StringBuilder(); for (int i = 0; i \<
>   data.Length; i++) {

>   sBuilder.Append(data[i].ToString("x2"));

>   }

>   return sBuilder.ToString();

>   }

>   *Java*

>   import java.security.\*;

>   import java.io.File;

>   import java.io.FileReader;

>   import java.io.IOException;

>   public class MD5Test

>   {

>   public static void main (String args[]) throws Exception { String s =
>   "string to hash";

>   MessageDigest md = MessageDigest.getInstance("MD5");

>   byte[] bytesOfMessage = s.getBytes("UTF-8");

>   byte[] thedigest = md.digest(bytesOfMessage);

>   System.out.println(

>   javax.xml.bind.DatatypeConverter.printHexBinary(thedigest).toLowerCase());

>   }

>   }

>   *Javascript*

>   \<script

>   src="http://crypto-js.googlecode.com/svn/tags/3.1.2/build/rollups/md5.js"\>\</script\>

>   \<script\>

>   var hash = CryptoJS.MD5("string to hash\\n");

>   alert("" + hash);

>   \</script\>

>   *Nodejs*

>   This code assumes you have the crypto-js library installed (npm install
>   crypto-js)

>   \$ cat md5.js

>   var CryptoJS = require('crypto-js');

>   89

>   var hash = CryptoJS.MD5('string to hash\\n');

>   console.log("" + hash);

-   node md5.js 2fcc83d76f9b2d8ef372271d807a3364

>   *Objective-C*

>   MD5 funcationlity can be be included in IOS code by first adding the
>   CommonCrypto library to your target, and including the following function in
>   your appDelegate (or appropriate class)

>   \#import \<CommonCrypto/CommonDigest.h\>

>   ...

>   \+(NSString\*) md5:(NSString\*)input

>   {

>   const char \*cInput = [input UTF8String];

>   unsigned char digest[CC_MD5_DIGEST_LENGTH];

>   CC_MD5(cInput, strlen(cInput), digest);

>   NSMutableString \*output = [NSMutableString

>   stringWithCapacity:CC_MD5_DIGEST_LENGTH \* 2];

>   for (int i = 0; i \< CC_MD5_DIGEST_LENGTH; i++) {

>   [output appendFormat:\@"%02x", digest[i]];

>   }

>   return output;

>   }

>   ...

>   *PHP*

>   echo md5('string to hash\\n')

>   **HMAC-SHA1**

>   *Bash*

>   The openssl package available in most linux distributions include a way of
>   creating the HMAC-SHA1 string from the command line…

>   echo -n "string to sign" \| openssl dgst -sha1 -hmac "my secret key"

>   (stdin)= a993876ea1218921a1c8551923473da7b310dfae

>   *C\#*

>   Encoding encoding = Encoding.UTF8;

>   byte[] secretBytes = encoding.GetBytes(“my secret key”); HMACSHA1 hmacsha1 =
>   new HMACSHA1(secretBytes); hmacsha1.ComputeHash(encoding.GetBytes(“string to
>   sign”)); byte[] data = hmacsha1.Hash;

>   90

>   *Javascript*

>   Cryptographic functions are available from the CryptJS libaray at
>   <https://code.google.com/p/crypto-js/>​.

>   var stringToSign = “string to sign”;

>   var secret = “my secret key”;

>   var signature = CryptoJS.HmacSHA1(stringToSign, secret);

>   *NodeJS*

>   This code assumes you have the crypto-js library installed (npm install
>   crypto-js)

>   \$ cat hmacsha1.js

>   var CryptoJS = require('crypto-js'),

>   message = "string to sign",

>   secret = "my secret key",

>   sig = CryptoJS.HmacSHA1(message, secret);

>   console.log("" + sig);

-   node hmacsha1.js a993876ea1218921a1c8551923473da7b310dfae

>   *Objective-C*

>   HMAC-SHA1 functionality can be be included in IOS code by first adding the
>   CommonCrypto library to your target, and including the following function in
>   your appDelegate (or appropriate class)

>   \#import \<CommonCrypto/CommonDigest.h\>

>   ...

>   \+(NSString\*) hmac_sha1:(NSString\*)input usingSecret:(NSString\*)key

>   {

>   const char \*cKey = [key UTF8String];

>   const char \*cInput = [input UTF8String];

>   unsigned char digest[CC_SHA1_DIGEST_LENGTH];

>   if (cKey == nil \|\| cInput == nil) {

>   return \@"";

>   }

>   NSMutableString \*output = [NSMutableString

>   stringWithCapacity:CC_SHA1_DIGEST_LENGTH \* 2];

>   CCHmac(kCCHmacAlgSHA1, cKey, strlen(cKey), cInput, strlen(cInput), digest);
>   for (int i = 0; i \< CC_SHA1_DIGEST_LENGTH; i++) {

>   [output appendFormat:\@"%02x", digest[i]];

>   }

>   return output;

>   }

>   ...

>   91

>   *PHP*

>   Generating the HMAC-SHA1 in PHP can be done using the following code.

>   \<?php

>   \$stringToSign = “string to sign”;

>   \$keySecret = “my secret key”;

>   \$signature = hash_hmac(”sha1”, \$stringToSign, \$keySecret);

>   echo \$signature;’

>   ?\>

>   This will generate an encrypted hash of the string. In this case the string
>   will be

>   a993876ea1218921a1c8551923473da7b310dfae

>   *Ruby*

>   Start up the ‘irb’ and try the following

>   irb(main):001:0\> require('openssl')

>   =\> true

>   irb(main):002:0\> OpenSSL::HMAC.hexdigest('sha1', 'my secret key', 'string
>   to sign')

>   =\> "a993876ea1218921a1c8551923473da7b310dfae"

>   **JSON Encoding**

>   JSON (JavaScript Object Notation) is an efficient way to describe data
>   structures in a text document, that is easy for computers to parse as well
>   as humans to read. The best description of JSON is from the website.
>   ​<http://json.org/>​.

>   **Timestamp Format**

>   The iVvy API uses a timestamp format to represent dates and times. Every
>   date used in the API is in UTC. It is up to the consumer of the API to
>   convert the time to the correct timezone of the final recipient of the data.
>   The format is a simple text-based format in the following form:

>   yyyy-mm-dd HH:mm:ss

>   Where

-   yyyy = The 4 digit year of the date

-   mm = The two digit month of the date, where January = 01 and December = 12

-   dd = The two digit day of the month

-   HH = The two digit hour

-   mm = The two digit minute

>   92

-   ss = The two digit second

>   **Date Format**

>   The iVvy API uses a date format to represent dates. The format is a simple
>   text-based format in the following form:

>   yyyy-mm-dd

>   Where

-   yyyy = The 4 digit year of the date

-   mm = The two digit month of the date, where January = 01 and December = 12

-   dd = The two digit day of the month

>   **URLEncoding**

>   To help pass special or reserved characters through URL’s to the
>   application, they must first be urlencoded. Most platforms provide such a
>   feature. Following is a limited list of reserved characters you can provide
>   the encoding to. Note this is NOT a comprehensive list, but a limited set
>   provided for example only. For a more comprehensive list, see
>   ​<http://www.w3schools.com/tags/ref_urlencode.asp>

| Character | Encoded |
|-----------|---------|
|           |         |
| \<space\> | %20     |
|           |         |
| ?         | %3F     |
|           |         |
| &         | %26     |
|           |         |
| “         | %22     |
|           |         |
| %         | %25     |
|           |         |
| /         | %2F     |
|           |         |
| =         | %3D     |
|           |         |
| \+        | %2B     |
|           |         |

>   **Timezone List**

>   93

| **Timezone**                    | **Value**            |
|---------------------------------|----------------------|
|                                 |                      |
| (UTC-11:00) Midway              | Pacific/Midway       |
|                                 |                      |
| (UTC-11:00) Niue                | Pacific/Niue         |
|                                 |                      |
| (UTC-11:00) Pago Pago           | Pacific/Pago_Pago    |
|                                 |                      |
| (UTC-10:00) Hawaii Time         | US/Hawaii            |
|                                 |                      |
| (UTC-10:00) Rarotonga           | Pacific/Rarotonga    |
|                                 |                      |
| (UTC-10:00) Tahiti              | Pacific/Tahiti       |
|                                 |                      |
| (UTC-09:30) Marquesas           | Pacific/Marquesas    |
|                                 |                      |
| (UTC-09:00) Alaska Time         | US/Alaska            |
|                                 |                      |
| (UTC-09:00) Gambier             | Pacific/Gambier      |
|                                 |                      |
| (UTC-08:00) Los Angeles         | America/Los_Angeles  |
|                                 |                      |
| (UTC-08:00) Tijuana             | America/Tijuana      |
|                                 |                      |
| (UTC-08:00) Vancouver           | America/Vancouver    |
|                                 |                      |
| (UTC-08:00) Whitehorse          | America/Whitehorse   |
|                                 |                      |
| (UTC-08:00) Pitcairn            | Pacific/Pitcairn     |
|                                 |                      |
| (UTC-07:00) Arizona             | US/Arizona           |
|                                 |                      |
| (UTC-07:00) Chihuahua, Mazatlan | America/Chihuahua    |
|                                 |                      |
| (UTC-07:00) Dawson Creek        | America/Dawson_Creek |
|                                 |                      |
| (UTC-07:00) Edmonton            | America/Edmonton     |
|                                 |                      |
| (UTC-07:00) Hermosillo          | America/Hermosillo   |
|                                 |                      |
| (UTC-07:00) Yellowknife         | America/Yellowknife  |
|                                 |                      |
| (UTC-06:00) Belize              | America/Belize       |
|                                 |                      |
| (UTC-06:00) Mexico City         | America/Mexico_City  |
|                                 |                      |
| (UTC-06:00) Regina              | America/Regina       |
|                                 |                      |
| (UTC-06:00) Tegucigalpa         | America/Tegucigalpa  |
|                                 |                      |
| (UTC-06:00) Winnipeg            | America/Winnipeg     |
|                                 |                      |
| (UTC-06:00) Costa Rica          | America/Costa_Rica   |
|                                 |                      |
| (UTC-06:00) Easter Island       | Chile/EasterIsland   |
|                                 |                      |
| (UTC-03:00) Salvador            | America/El_Salvador  |
|                                 |                      |
| (UTC-06:00) Galapagos           | Pacific/Galapagos    |
|                                 |                      |
| (UTC-06:00) Guatemala           | America/Guatemala    |
|                                 |                      |
| (UTC-06:00) Managua             | America/Managua      |
|                                 |                      |
| (UTC-05:00) Bogota              | America/Bogota       |
|                                 |                      |
| (UTC-05:00) Cayman              | America/Cayman       |
|                                 |                      |

>   94

| (UTC-05:00) Iqaluit                       | America/Iqaluit        |
|-------------------------------------------|------------------------|
|                                           |                        |
| (UTC-05:00) Montreal                      | America/Montreal       |
|                                           |                        |
| (UTC-05:00) Toronto                       | America/Toronto        |
|                                           |                        |
| (UTC-05:00) Grand Turk                    | America/Grand_Turk     |
|                                           |                        |
| (UTC-05:00) Guayaquil                     | America/Guayaquil      |
|                                           |                        |
| (UTC-05:00) Havana                        | America/Havana         |
|                                           |                        |
| (UTC-05:00) Jamaica                       | America/Jamaica        |
|                                           |                        |
| (UTC-05:00) Lima                          | America/Lima           |
|                                           |                        |
| (UTC-05:00) Nassau                        | America/Nassau         |
|                                           |                        |
| (UTC-05:00) Panama                        | America/Panama         |
|                                           |                        |
| (UTC-05:00) Port-au-Prince                | America/Port-au-Prince |
|                                           |                        |
| (UTC-05:00) Rio Branco                    | America/Rio_Branco     |
|                                           |                        |
| (UTC-04:30) Caracas                       | America/Caracas        |
|                                           |                        |
| (UTC-04:00) Antigua                       | America/Antigua        |
|                                           |                        |
| (UTC-04:00) Asuncion                      | America/Asuncion       |
|                                           |                        |
| (UTC-04:00) Atlantic Time - Halifax       | America/Halifax        |
|                                           |                        |
| (UTC-04:00) Barbados                      | America/Barbados       |
|                                           |                        |
| (UTC-04:00) Bermuda                       | Atlantic/Bermuda       |
|                                           |                        |
| (UTC-04:00) Boa Vista                     | America/Boa_Vista      |
|                                           |                        |
| (UTC-04:00) Campo Grande                  | America/Campo_Grande   |
|                                           |                        |
| (UTC-04:00) Cuiaba                        | America/Cuiaba         |
|                                           |                        |
| (UTC-04:00) Curacao                       | America/Curacao        |
|                                           |                        |
| (UTC-04:00) Guyana                        | America/Guyana         |
|                                           |                        |
| (UTC-04:00) La Paz                        | America/La_Paz         |
|                                           |                        |
| (UTC-04:00) Manaus                        | America/Manaus         |
|                                           |                        |
| (UTC-04:00) Martinique                    | America/Martinique     |
|                                           |                        |
| (UTC-04:00) Palmer                        | Antarctica/Palmer      |
|                                           |                        |
| (UTC-04:00) Port of Spain                 | America/Port_of_Spain  |
|                                           |                        |
| (UTC-04:00) Porto Velho                   | America/Porto_Velho    |
|                                           |                        |
| (UTC-04:00) Puerto Rico                   | America/Puerto_Rico    |
|                                           |                        |
| (UTC-04:00) Santiago                      | America/Santiago       |
|                                           |                        |
| (UTC-04:00) Santo Domingo                 | America/Santo_Domingo  |
|                                           |                        |
| (UTC-04:00) Thule                         | America/Thule          |
|                                           |                        |
| (UTC-03:30) Newfoundland Time - St. Johns | America/St_Johns       |
|                                           |                        |

>   95

| (UTC-03:00) Araguaina                  | America/Araguaina                |
|----------------------------------------|----------------------------------|
|                                        |                                  |
| (UTC-03:00) Belem                      | America/Belem                    |
|                                        |                                  |
| (UTC-03:00) Buenos Aires               | America/Buenos_Aires             |
|                                        |                                  |
| (UTC-03:00) Cayenne                    | America/Cayenne                  |
|                                        |                                  |
| (UTC-03:00) Fortaleza                  | America/Fortaleza                |
|                                        |                                  |
| (UTC-03:00) Godthab                    | America/Godthab                  |
|                                        |                                  |
| (UTC-03:00) Maceio                     | America/Maceio                   |
|                                        |                                  |
| (UTC-03:00) Miquelon                   | America/Miquelon                 |
|                                        |                                  |
| (UTC-03:00) Montevideo                 | America/Montevideo               |
|                                        |                                  |
| (UTC-03:00) Paramaribo                 | America/Paramaribo               |
|                                        |                                  |
| (UTC-03:00) Recife                     | America/Recife                   |
|                                        |                                  |
| (UTC-03:00) Rothera                    | Antarctica/Rothera               |
|                                        |                                  |
| (UTC-03:00) Sao Paulo                  | America/Sao_Paulo                |
|                                        |                                  |
| (UTC-03:00) Stanley                    | Atlantic/Stanley                 |
|                                        |                                  |
| (UTC-02:00) Noronha                    | America/Noronha Brazil/DeNoronha |
|                                        |                                  |
| (UTC-02:00) South Georgia              | Atlantic/South_Georgia           |
|                                        |                                  |
| (UTC-01:00) Azores                     | Atlantic/Azores                  |
|                                        |                                  |
| (UTC-01:00) Cape Verde                 | Atlantic/Cape_Verde              |
|                                        |                                  |
| (UTC-01:00) Scoresbysund               | America/Scoresbysund             |
|                                        |                                  |
| (UTC+00:00) Abidjan                    | Africa/Abidjan                   |
|                                        |                                  |
| (UTC+00:00) Accra                      | Africa/Accra                     |
|                                        |                                  |
| (UTC+00:00) Bamako                     | Africa/Bamako                    |
|                                        |                                  |
| (UTC+00:00) Banjul                     | Africa/Banjul                    |
|                                        |                                  |
| (UTC+00:00) Bissau                     | Africa/Bissau                    |
|                                        |                                  |
| (UTC+00:00) Canary Islands             | Atlantic/Canary                  |
|                                        |                                  |
| (UTC+00:00) Casablanca                 | Africa/Casablanca                |
|                                        |                                  |
| (UTC+00:00) Conakry                    | Africa/Conakry                   |
|                                        |                                  |
| (UTC+00:00) Dakar                      | Africa/Dakar                     |
|                                        |                                  |
| (UTC+00:00) Danmarkshavn               | America/Danmarkshavn             |
|                                        |                                  |
| (UTC+00:00) Dublin                     | Europe/Dublin                    |
|                                        |                                  |
| (UTC+00:00) El Aaiun                   | Africa/El_Aaiun                  |
|                                        |                                  |
| (UTC+00:00) Faeroe                     | Atlantic/Faeroe                  |
|                                        |                                  |
| (UTC+00:00) Freetown                   | Africa/Freetown                  |
|                                        |                                  |
| (UTC+00:00) Coordinated Universal Time | UTC                              |
|                                        |                                  |

>   96

| (UTC+00:00) Lisbon      | Europe/Lisbon      |
|-------------------------|--------------------|
|                         |                    |
| (UTC+00:00) Lome        | Africa/Lome        |
|                         |                    |
| (UTC+00:00) London      | Europe/London      |
|                         |                    |
| (UTC+00:00) Monrovia    | Africa/Monrovia    |
|                         |                    |
| (UTC+00:00) Nouakchott  | Africa/Nouakchott  |
|                         |                    |
| (UTC+00:00) Ouagadougou | Africa/Ouagadougou |
|                         |                    |
| (UTC+00:00) Reykjavik   | Atlantic/Reykjavik |
|                         |                    |
| (UTC+00:00) Sao Tome    | Africa/Sao_Tome    |
|                         |                    |
| (UTC+00:00) St Helena   | Atlantic/St_Helena |
|                         |                    |
| (UTC+01:00) Algiers     | Africa/Algiers     |
|                         |                    |
| (UTC+01:00) Amsterdam   | Europe/Amsterdam   |
|                         |                    |
| (UTC+01:00) Andorra     | Europe/Andorra     |
|                         |                    |
| (UTC+01:00) Bangui      | Africa/Bangui      |
|                         |                    |
| (UTC+01:00) Berlin      | Europe/Berlin      |
|                         |                    |
| (UTC+01:00) Brazzaville | Africa/Brazzaville |
|                         |                    |
| (UTC+01:00) Brussels    | Europe/Brussels    |
|                         |                    |
| (UTC+01:00) Budapest    | Europe/Budapest    |
|                         |                    |
| (UTC+01:00) Belgrade    | Europe/Belgrade    |
|                         |                    |
| (UTC+01:00) Prague      | Europe/Prague      |
|                         |                    |
| (UTC+01:00) Ceuta       | Africa/Ceuta       |
|                         |                    |
| (UTC+01:00) Copenhagen  | Europe/Copenhagen  |
|                         |                    |
| (UTC+01:00) Douala      | Africa/Douala      |
|                         |                    |
| (UTC+01:00) Gibraltar   | Europe/Gibraltar   |
|                         |                    |
| (UTC+01:00) Kinshasa    | Africa/Kinshasa    |
|                         |                    |
| (UTC+01:00) Lagos       | Africa/Lagos       |
|                         |                    |
| (UTC+01:00) Libreville  | Africa/Libreville  |
|                         |                    |
| (UTC+01:00) Luanda      | Africa/Luanda      |
|                         |                    |
| (UTC+01:00) Luxembourg  | Europe/Luxembourg  |
|                         |                    |
| (UTC+01:00) Madrid      | Europe/Madrid      |
|                         |                    |
| (UTC+01:00) Malabo      | Africa/Malabo      |
|                         |                    |
| (UTC+01:00) Malta       | Europe/Malta       |
|                         |                    |
| (UTC+01:00) Monaco      | Europe/Monaco      |
|                         |                    |
| (UTC+01:00) Ndjamena    | Africa/Ndjamena    |
|                         |                    |
| (UTC+01:00) Niamey      | Africa/Niamey      |
|                         |                    |

>   97

| (UTC+01:00) Oslo         | Europe/Oslo                   |
|--------------------------|-------------------------------|
|                          |                               |
| (UTC+01:00) Paris        | Europe/Paris                  |
|                          |                               |
| (UTC+01:00) Porto-Novo   | Africa/Porto-Novo             |
|                          |                               |
| (UTC+01:00) Rome         | Europe/Rome                   |
|                          |                               |
| (UTC+01:00) Stockholm    | Europe/Stockholm              |
|                          |                               |
| (UTC+01:00) Tirane       | Europe/Tirane                 |
|                          |                               |
| (UTC+01:00) Tunis        | Africa/Tunis                  |
|                          |                               |
| (UTC+01:00) Vienna       | Europe/Vienna                 |
|                          |                               |
| (UTC+01:00) Warsaw       | Europe/Warsaw                 |
|                          |                               |
| (UTC+01:00) Windhoek     | Africa/Windhoek               |
|                          |                               |
| (UTC+01:00) Zurich       | Europe/Zurich                 |
|                          |                               |
| (UTC+02:00) Amman        | Asia/Amman                    |
|                          |                               |
| (UTC+02:00) Athens       | Europe/Athens                 |
|                          |                               |
| (UTC+02:00) Beirut       | Asia/Beirut                   |
|                          |                               |
| (UTC+02:00) Blantyre     | Africa/Blantyre               |
|                          |                               |
| (UTC+02:00) Bucharest    | Europe/Bucharest              |
|                          |                               |
| (UTC+02:00) Bujumbura    | Africa/Bujumbura              |
|                          |                               |
| (UTC+02:00) Cairo        | Africa/Cairo                  |
|                          |                               |
| (UTC+02:00) Chisinau     | Europe/Chisinau               |
|                          |                               |
| (UTC+02:00) Damascus     | Asia/Damascus                 |
|                          |                               |
| (UTC+02:00) Gaborone     | Africa/Gaborone               |
|                          |                               |
| (UTC+02:00) Gaza         | Asia/Gaza                     |
|                          |                               |
| (UTC+02:00) Harare       | Africa/Harare                 |
|                          |                               |
| (UTC+02:00) Helsinki     | Europe/Helsinki               |
|                          |                               |
| (UTC+02:00) Istanbul     | Asia/Istanbul Europe/Istanbul |
|                          |                               |
| (UTC+02:00) Jerusalem    | Asia/Jerusalem                |
|                          |                               |
| (UTC+02:00) Johannesburg | Africa/Johannesburg           |
|                          |                               |
| (UTC+02:00) Kiev         | Europe/Kiev                   |
|                          |                               |
| (UTC+02:00) Kigali       | Africa/Kigali                 |
|                          |                               |
| (UTC+02:00) Lubumbashi   | Africa/Lubumbashi             |
|                          |                               |
| (UTC+02:00) Lusaka       | Africa/Lusaka                 |
|                          |                               |
| (UTC+02:00) Maputo       | Africa/Maputo                 |
|                          |                               |
| (UTC+02:00) Maseru       | Africa/Maseru                 |
|                          |                               |
| (UTC+02:00) Mbabane      | Africa/Mbabane                |
|                          |                               |

>   98

| (UTC+02:00) Nicosia       | Asia/Nicosia Europe/Nicosia |
|---------------------------|-----------------------------|
|                           |                             |
| (UTC+02:00) Riga          | Europe/Riga                 |
|                           |                             |
| (UTC+02:00) Sofia         | Europe/Sofia                |
|                           |                             |
| (UTC+02:00) Tallinn       | Europe/Tallinn              |
|                           |                             |
| (UTC+02:00) Tripoli       | Africa/Tripoli              |
|                           |                             |
| (UTC+02:00) Vilnius       | Europe/Vilnius              |
|                           |                             |
| (UTC+03:00) Addis Ababa   | Africa/Addis_Ababa          |
|                           |                             |
| (UTC+03:00) Aden          | Asia/Aden                   |
|                           |                             |
| (UTC+03:00) Antananarivo  | Indian/Antananarivo         |
|                           |                             |
| (UTC+03:00) Asmera        | Africa/Asmera               |
|                           |                             |
| (UTC+03:00) Baghdad       | Asia/Baghdad                |
|                           |                             |
| (UTC+03:00) Bahrain       | Asia/Bahrain                |
|                           |                             |
| (UTC+03:00) Comoro        | Indian/Comoro               |
|                           |                             |
| (UTC+03:00) Dar es Salaam | Africa/Dar_es_Salaam        |
|                           |                             |
| (UTC+03:00) Djibouti      | Africa/Djibouti             |
|                           |                             |
| (UTC+03:00) Kampala       | Africa/Kampala              |
|                           |                             |
| (UTC+03:00) Khartoum      | Africa/Khartoum             |
|                           |                             |
| (UTC+03:00) Kuwait        | Asia/Kuwait                 |
|                           |                             |
| (UTC+03:00) Mayotte       | Indian/Mayotte              |
|                           |                             |
| (UTC+03:00) Minsk         | Europe/Minsk                |
|                           |                             |
| (UTC+03:00) Mogadishu     | Africa/Mogadishu            |
|                           |                             |
| (UTC+03:00) Kaliningrad   | Europe/Kaliningrad          |
|                           |                             |
| (UTC+03:00) Nairobi       | Africa/Nairobi              |
|                           |                             |
| (UTC+03:00) Qatar         | Asia/Qatar                  |
|                           |                             |
| (UTC+03:00) Riyadh        | Asia/Riyadh                 |
|                           |                             |
| (UTC+03:00) Syowa         | Antarctica/Syowa            |
|                           |                             |
| (UTC+03:30) Tehran        | Asia/Tehran                 |
|                           |                             |
| (UTC+04:00) Baku          | Asia/Baku                   |
|                           |                             |
| (UTC+04:00) Dubai         | Asia/Dubai                  |
|                           |                             |
| (UTC+04:00) Mahe          | Indian/Mahe                 |
|                           |                             |
| (UTC+04:00) Mauritius     | Indian/Mauritius            |
|                           |                             |
| (UTC+04:00) Moscow        | Europe/Moscow               |
|                           |                             |
| (UTC+04:00) Samara        | Europe/Samara               |
|                           |                             |
| (UTC+04:00) Muscat        | Asia/Muscat                 |
|                           |                             |

>   99

| (UTC+04:00) Reunion           | Indian/Reunion     |
|-------------------------------|--------------------|
|                               |                    |
| (UTC+04:00) Tbilisi           | Asia/Tbilisi       |
|                               |                    |
| (UTC+04:00) Yerevan           | Asia/Yerevan       |
|                               |                    |
| (UTC+04:30) Kabul             | Asia/Kabul         |
|                               |                    |
| (UTC+05:00) Aqtau             | Asia/Aqtau         |
|                               |                    |
| (UTC+05:00) Aqtobe            | Asia/Aqtobe        |
|                               |                    |
| (UTC+05:00) Ashgabat          | Asia/Ashgabat      |
|                               |                    |
| (UTC+05:00) Dushanbe          | Asia/Dushanbe      |
|                               |                    |
| (UTC+05:00) Karachi           | Asia/Karachi       |
|                               |                    |
| (UTC+05:00) Kerguelen         | Indian/Kerguelen   |
|                               |                    |
| (UTC+05:00) Maldives          | Indian/Maldives    |
|                               |                    |
| (UTC+05:00) Mawson            | Antarctica/Mawson  |
|                               |                    |
| (UTC+05:00) Tashkent          | Asia/Tashkent      |
|                               |                    |
| (UTC+05:30) Colombo           | Asia/Colombo       |
|                               |                    |
| (UTC+05:45) Katmandu          | Asia/Katmandu      |
|                               |                    |
| (UTC+06:00) Almaty            | Asia/Almaty        |
|                               |                    |
| (UTC+06:00) Bishkek           | Asia/Bishkek       |
|                               |                    |
| (UTC+06:00) Chagos            | Indian/Chagos      |
|                               |                    |
| (UTC+06:00) Dhaka             | Asia/Dhaka         |
|                               |                    |
| (UTC+06:00) Yekaterinburg     | Asia/Yekaterinburg |
|                               |                    |
| (UTC+06:00) Thimphu           | Asia/Thimphu       |
|                               |                    |
| (UTC+06:00) Vostok            | Antarctica/Vostok  |
|                               |                    |
| (UTC+06:30) Cocos             | Indian/Cocos       |
|                               |                    |
| (UTC+06:30) Rangoon           | Asia/Rangoon       |
|                               |                    |
| (UTC+07:00) Bangkok           | Asia/Bangkok       |
|                               |                    |
| (UTC+07:00) Christmas         | Indian/Christmas   |
|                               |                    |
| (UTC+07:00) Davis             | Antarctica/Davis   |
|                               |                    |
| (UTC+07:00) Hovd              | Asia/Hovd          |
|                               |                    |
| (UTC+07:00) Jakarta           | Asia/Jakarta       |
|                               |                    |
| (UTC+07:00) Omsk, Novosibirsk | Asia/Novosibirsk   |
|                               |                    |
| (UTC+07:00) Phnom Penh        | Asia/Phnom_Penh    |
|                               |                    |
| (UTC+07:00) Vientiane         | Asia/Vientiane     |
|                               |                    |
| (UTC+08:00) Brunei            | Asia/Brunei        |
|                               |                    |
| (UTC+08:00) Casey             | Antarctica/Casey   |
|                               |                    |

>   100

| (UTC+08:00) Choibalsan       | Asia/Choibalsan           |
|------------------------------|---------------------------|
|                              |                           |
| (UTC+08:00) Hong Kong        | Asia/Hong_Kong            |
|                              |                           |
| (UTC+08:00) Kuala Lumpur     | Asia/Kuala_Lumpur         |
|                              |                           |
| (UTC+08:00) Macau            | Asia/Macau                |
|                              |                           |
| (UTC+08:00) Makassar         | Asia/Makassar             |
|                              |                           |
| (UTC+08:00) Manila           | Asia/Manila               |
|                              |                           |
| (UTC+08:00) Krasnoyarsk      | Asia/Krasnoyarsk          |
|                              |                           |
| (UTC+08:00) Singapore        | Asia/Singapore            |
|                              |                           |
| (UTC+08:00) Taipei           | Asia/Taipei               |
|                              |                           |
| (UTC+08:00) Ulaanbaatar      | Asia/Ulaanbaatar          |
|                              |                           |
| (UTC+08:00) Perth            | Australia/Perth           |
|                              |                           |
| (UTC+09:00) Dili             | Asia/Dili                 |
|                              |                           |
| (UTC+09:00) Jayapura         | Asia/Jayapura             |
|                              |                           |
| (UTC+09:00) Irkutsk          | Asia/Irkutsk              |
|                              |                           |
| (UTC+09:00) Palau            | Pacific/Palau             |
|                              |                           |
| (UTC+09:00) Pyongyang        | Asia/Pyongyang            |
|                              |                           |
| (UTC+09:00) Seoul            | Asia/Seoul                |
|                              |                           |
| (UTC+09:00) Tokyo            | Asia/Tokyo                |
|                              |                           |
| (UTC+09:30) Adelaide         | Australia/Adelaide        |
|                              |                           |
| (UTC+09:30) Darwin           | Australia/Darwin          |
|                              |                           |
| (UTC+10:00) Dumont D'Urville | Antarctica/DumontDUrville |
|                              |                           |
| (UTC+10:00) Brisbane         | Australia/Brisbane        |
|                              |                           |
| (UTC+10:00) Canberra         | Australia/Canberra        |
|                              |                           |
| (UTC+10:00) Hobart           | Australia/Hobart          |
|                              |                           |
| (UTC+10:00) Melbourne        | Australia/Melbourne       |
|                              |                           |
| (UTC+10:00) Sydney           | Australia/Sydney          |
|                              |                           |
| (UTC+10:00) Guam             | Pacific/Guam              |
|                              |                           |
| (UTC+10:00) Yakutsk          | Asia/Yakutsk              |
|                              |                           |
| (UTC+10:00) Port Moresby     | Pacific/Port_Moresby      |
|                              |                           |
| (UTC+10:00) Saipan           | Pacific/Saipan            |
|                              |                           |
| (UTC+10:00) Truk             | Pacific/Truk              |
|                              |                           |
| (UTC+10:30 Lord Howe Island) | Australia/Lord_Howe       |
|                              |                           |
| (UTC+11:00) Efate            | Pacific/Efate             |
|                              |                           |
| (UTC+11:00) Guadalcanal      | Pacific/Guadalcanal       |
|                              |                           |

>   101

| (UTC+11:00) Kosrae     | Pacific/Kosrae     |
|------------------------|--------------------|
|                        |                    |
| (UTC+11:00) Noumea     | Pacific/Noumea     |
|                        |                    |
| (UTC+11:00) Ponape     | Pacific/Ponape     |
|                        |                    |
| (UTC+11:30) Norfolk    | Pacific/Norfolk    |
|                        |                    |
| (UTC+12:00) Auckland   | Pacific/Auckland   |
|                        |                    |
| (UTC+12:00) Fiji       | Pacific/Fiji       |
|                        |                    |
| (UTC+12:00) Funafuti   | Pacific/Funafuti   |
|                        |                    |
| (UTC+12:00) Kwajalein  | Pacific/Kwajalein  |
|                        |                    |
| (UTC+12:00) Majuro     | Pacific/Majuro     |
|                        |                    |
| (UTC+12:00) Magadan    | Asia/Magadan       |
|                        |                    |
| (UTC+12:00) Nauru      | Pacific/Nauru      |
|                        |                    |
| (UTC+12:00) Tarawa     | Pacific/Tarawa     |
|                        |                    |
| (UTC+12:00) Wake       | Pacific/Wake       |
|                        |                    |
| (UTC+12:00) Wallis     | Pacific/Wallis     |
|                        |                    |
| (UTC+13:00) Apia       | Pacific/Apia       |
|                        |                    |
| (UTC+13:00) Enderbury  | Pacific/Enderbury  |
|                        |                    |
| (UTC+13:00) Fakaofo    | Pacific/Fakaofo    |
|                        |                    |
| (UTC+13:00) Tongatapu  | Pacific/Tongatapu  |
|                        |                    |
| (UTC+14:00) Kiritimati | Pacific/Kiritimati |
|                        |                    |

>   102
