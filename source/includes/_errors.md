# Errors

<!-- <aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside> -->

TireCoop follows the conventions for HTTP response codes:

- 2xx indicate success;
- 4xx indicate errors; and
- 5xx indicate server errors with TireCoop API itself.


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid
401 | Unauthorized -- Your API key is could not be validated
403 | Forbidden -- The endpoint you are trying to reach is not available to you.
404 | Not Found -- The end point could not be found
500 | Internal Server Error -- We had a problem with our server. Try again later.

