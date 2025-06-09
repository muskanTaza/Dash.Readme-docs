---
title: Error Codes
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Tazapay uses conventional HTTP responses to indicate success or failure of a request and its intended operation. 2xx status codes denote that a requested operation was performed successfully. 5xx status codes denote an error with Tazapay's servers. 4xx status codes denote that the operation could not be performed given the information passed on the request body, they can be handled by modifying the request body. 

> 📘
>
> 4xx status codes carry <a href = "https://tazapay-api-developer.readme.io/reference/users-2" target="_blank">error codes</a> which explain in brief the reason the request failed to perform the operation.

### HTTP Status Codes:

| Error Code | Meaning                                                                                                                                                                                   |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 400        | Bad Request : Your request is invalid                                                                                                                                                     |
| 401        | Unauthorized : The API key entered is invalid. Please check if you are using the sandbox key on the production end point or vice versa                                                    |
| 403        | Forbidden : You are not authorised to access the requested resource                                                                                                                       |
| 404        | Not Found : The server cannot find the requested resource                                                                                                                                 |
| 405        | Method Not Allowed : You tried to access with an invalid method. The server knows the request method, but the target resource doesn't support this method. eg: inputting an incorrect URL |
| 406        | Not Acceptable : You requested a format that isn't JSON. Please check the file extension, syntax and/or formatting.                                                                       |
| 410        | Not Available : The requested resource has been removed from our servers                                                                                                                  |
| 429        | Too Many Requests: You've sent too many requests in a given amount of time                                                                                                                |
| 500        | Internal Server Error : We had a problem with our server. Try again later                                                                                                                 |
| 503        | Service Unavailable : We're temporarily offline for maintenance. Please try again later                                                                                                   |
