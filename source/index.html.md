---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Contact us for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - resources
  - leads
  - lead_statuses
  - inquiries
  - reviews

search: true
---

# JSON API Introduction

Caring.com provides a JSON API over HTTPS. Examples are provided for shell assuming basic usage of Curl. Other language examples can be provided if requested.

You can report API bugs with [github issues](https://github.com/caring/docs.caring.com/issues)

# Authentication

Requests require an API key that you can obtain by contacting us at engineering AT caring.com

> Authentication header example:

```shell
curl "https://dir.caring.com/api/v2/example.json" -H "Caring-Partner: TOKEN_VALUE"
```

> Make sure to replace `TOKEN_VALUE` with your API key.

Caring.com Directory expects for the API key to be included as a header in all API requests and for the requests to be made over HTTPS.

**Request Header:** `Caring-Partner: TOKEN_VALUE`

<aside class="notice">
You must replace <code>TOKEN_VALUE</code> with your API key.
</aside>

# Testing Sandbox

For testing and debugging, we maintain a fully featured testing sandbox. To use the sandbox replace the hostname `dir.caring.com` with `sandbox-dir.caring.com`.

> Example request to the Sandbox environment:

```shell
curl "https://sandbox-dir.caring.com/api/v2/example.json" -H "Caring-Partner: TOKEN_VALUE"
```

# Error Codes

<aside class="notice">These are some, but not all, of the error codes you can get from us for varying reasons.</aside>

The Caring.com JSON API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is malformed.
401 | Unauthorized -- Your API key is wrong, or you're trying to be sneaky.
404 | Not Found -- The requested resource was not found.
406 | Not Acceptable -- You requested a format that we don't support.
422 | Unprocessable Entity -- There was a validation error in your request. See the returned error messages.
500 | Internal Server Error -- Our server encountered an unexpected condition that prevented it from fulfilling the request. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
