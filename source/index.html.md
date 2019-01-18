---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Contact us for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - reviews

search: true
---

# JSON API Introduction

Caring.com provides [JSON API](http://jsonapi.org/) compliant APIs over HTTPS. Examples are provided for shell assuming basic usage of Curl. Other language exmaples can be provided if requested.

You can report API bugs with [github issues](https://github.com/caring/reviews-api-docs/issues)

# Authentication

Requests require an API key that you can obtain by contacting us.

> Authentication header example:

```shell
curl "https://dir.caring.com/api/v2/example.jsonapi" -H "Caring-Partner: TOKEN_VALUE"
```

> Make sure to replace `TOKEN_VALUE` with your API key.

Caring.com Directory expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Caring-Partner: TOKEN_VALUE`

<aside class="notice">
You must replace <code>TOKEN_VALUE</code> with your API key.
</aside>

# Errors

<aside class="notice">These are not all, but some of the error codes you can get from us for varying reasons.</aside>

The Caring.com JSON API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is malformed.
401 | Unauthorized -- Your API key is wrong, or you're trying to be sneaky.
404 | Not Found -- not found.
406 | Not Acceptable -- You requested a format that we don't support.
422 | Unprocessable Entity -- There was an validation error in your request. See the returned error messages.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
