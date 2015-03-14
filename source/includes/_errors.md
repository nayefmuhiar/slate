# Errors

The Eon Access API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Incorrect request
401 | Unauthorized -- Your API key is wrong
404 | Not Found -- The specified case could not be found
405 | Method Not Allowed -- You tried to access a case with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The case requested has been removed from our servers
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.