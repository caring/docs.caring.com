# Reviews

## Querying reviews

```shell
curl "https://dir.caring.com/api/v2/reviews.jsonapi?filter[resource_id]=1229142" \
  -H "Caring-Partner: TOKEN_VALUE"
```

> The above command returns [JSON API](http://jsonapi.org/) response structured like this:

```json
{
    "data": [
        {
            "id": "1148701",
            "type": "local_reviews",
            "attributes": {
                "resource_id": 1229142,
                "resource_url": "http://www.caring.com/local/memory-care-facilities-in-dallas-texas/villages-of-lake-highlands",
                "resource_name": "Villages of Lake Highlands",
                "title": "I am a friend or relative of a current/past resident",
                "content": "This is a really good review",
                "rating": 5,
                "staff_score": 4,
                "activities_score": 3,
                "food_score": 2,
                "facilities_score": 1,
                "value_score": 0,
                "provider_response": "Thank you for your wonderful review",
                "moderation_status": "approved",
                "moderated_at": "2017-07-20T14:42:44.000-07:00",
                "author": {
                    "name": "Satisfied Reviewer",
                    "email": "8225995e75243d26@example.com",
                    "url": "https://www.example.com/people/satisfied-reviewer"
                },
                "origin_url": "https://www.caring.com/local/memory-care-facilities-in-dallas-texas/villages-of-lake-highlands#reviews",
                "created_at": "2017-07-17T10:35:15.000-07:00",
                "updated_at": "2017-07-21T19:23:11.000-07:00"
            }
        }
    ],
    "links": {
        "self": "https://dir.caring.com/api/v2/reviews.jsonapi?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "next": "https://dir.caring.com/api/v2/reviews.jsonapi?page%5Bnumber%5D=2&page%5Bsize%5D=1",
        "last": "https://dir.caring.com/api/v2/reviews.jsonapi?page%5Bnumber%5D=1799&page%5Bsize%5D=1"
    }
}
```

This endpoint retrieves a paginated list of reviews ordered by `last_modified` by default.

To stay up to date, we recommend that you periodically check the reviews collection ordered by `last_modified` so you can efficently get the updates you need as moderation statuses or review content changes.

### Filter Parameters

To filter the collection you can use any of the following parameters in the `filter` parameter.

`GET https://dir.caring.com/api/v2/reviews.jsonapi?filter[resource_id]=1229142&filter[moderation_status]=approved`

Parameter | Type | Description
--------- | ------- | -----------
resource_id | List of comma separated resource IDs | ID of the reviewed resource. Ex: `filter[resource_id]=1234,5678` for multiple resources or `filter[resource_id]=1234` for single one.
property_id | List of comma separated property IDs | ID of the property that connects multiple resource type. Ex: `filter[property_id]=1234,5678` for multiple properties or `filter[property_id]=1234` for single one.
resource_url | Url | The caring.com url of the reviewed resource.
resource_name | String | The name of the reviewed resource.
chain_name | String |The name of the chain owning the reviewed resource.
author_name | String | The screen name of the author of the review.
author_email | Email Address | The email address of the user posting the review.
author_url | Url | A personal url to the author of the review.
moderation_status | Enum('approved', 'rejected', 'further_review', 'spam') | The moderation status of the review.
sort | String | A sort clause made up of a field and direction Ex: `filter[sort]=id+asc` filters ids ascending.

### Pagination Parameters

`GET https://dir.caring.com/api/v2/reviews.jsonapi?page[number]=1&page[size]=50`

Parameter | Type | Description
--------- | ------- | -----------
number | Integer | The page number.
size | Integer | The number of items per requested page.


### Review Data Attributes

<aside class="notice">
For all of the numeric attributes 0 is equal to N/A
</aside>

Attribute | Type     | Description
--------- | --------- | ---------
resource_id | Integer | The primary key ID of the service provider that was reviewed
resource_url | Url | The public URL of the service provider that was reviewed.
resource_name | String | The Name of the service provider that was reviewed
author | Object | `name`, `email` and `url` fields for the Author of the review.
title | String | The headline of the review, typically a description of the reviewers relation to the service provider provider.
content | Text | The full text of the review.
origin_url | Url | A url to the site the review was created on.
moderation_webhook_url | Url | A URL where you can receive moderation status updates as a webhook.
rating | 1-5 | Overall Raring.
staff_score | 1-5 | Staff Rating.
activities_score | 1-5 | Rating of Leisure Activities.
food_score | 1-5 | Rating of the food available.
facilities_score | 1-5 | Rating of the facility quality and cleanliness.
value_score | 1-5 | Rating of the value.
provider_response | Text | A response to the review from the service provider.
moderated_at | Timestamp | The timestamp of when the review was moderated.
created_at | Timestamp | The timestamp of the review creation
updated_at | Timestamp | The timestamp of the last time the review was modified.

## Get a single Review

```shell
curl "https://dir.caring.com/api/v2/reviews/2.jsonapi" \
  -H "Caring-Partner: TOKEN_VALUE"
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "1132501",
        "type": "local_reviews",
        "attributes": {
            "resource_id": 1225974,
            "resource_url": "http://www.caring.com/local/assisted-living-facilities-in-salisbury-maryland/lakeside-assisted-living-salisbury",
            "resource_name": "Lakeside Assisted Living",
            "title": "I visited this facility",
            "content": "Lakeside Assisted Living was nice, and I enjoyed the tour we had. The food was excellent, and the dining area was very clean and very appeasing to the eye. The staff was very nice, very informative, and met us as soon as we walked in. They had a beauty and barber shop.",
            "rating": 4,
            "staff_score": 5,
            "activities_score": 0,
            "food_score": 4,
            "facilities_score": 5,
            "value_score": 0,
            "provider_response": "Thank you for your wonderful review Daniel!  You are welcome anytime. We strive to provide quality of life here at Lakeside.",
            "moderation_status": "approved",
            "moderated_at": "2017-07-20T14:42:44.000-07:00",
            "author": {
                "name": "Daniel",
                "email": "b7da7994a7a270ac@example.com",
                "url": null
            },
            "origin_url": "https://www.seniorhomes.com/f/md/lakeside-assisted-living-salisbury#reviews",
            "created_at": "2017-07-17T10:35:15.000-07:00",
            "updated_at": "2017-07-21T19:23:11.000-07:00"
        }
    }
}
```

This endpoint retrieves a single review.

### HTTP Request

`GET https://dir.caring.com/api/v2/reviews/:id.jsonapi`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the review to retrieve

## Creating a Review

### HTTP Request

`POST https://dir.caring.com/api/v2/reviews.jsonapi`

```shell
curl "https://dir.caring.com/api/v2/reviews.jsonapi" \
  -H "Caring-Partner: TOKEN_VALUE" \
  -d '{
        "data": {
            "attributes": {
                "resource_id": 1225974,
                "title": "I visited this facility",
                "content": "The facility was new and in good repair. The staff was warm and friendly.",
                "rating": 5,
                "staff_score": 5,
                "activities_score": 5,
                "food_score": 4,
                "facilities_score": 5,
                "value_score": 5,
                "origin_url": "https://www.partner-site.com/assisted-living-in-california/nice-provider#reviews",
                "author": {
                    "name": "SatisfiedReviewer11",
                    "email": "SatisfiedReviewer11@example.com",
                    "url": "https://www.twitter.com/SatisfiedReviewer11"
                }

            }
        }
    }'
```

> A successful response will respond with JSON like this:

```json
{
    "data": {
        "id": "1148702",
        "type": "local_reviews",
        "attributes": {
            "resource_id": 1225974,
            "property_id": 123,
            "resource_url": "http://www.caring.test/local/assisted-living-facilities-in-salisbury-maryland/lakeside-assisted-living-salisbury",
            "resource_name": "Lakeside Assisted Living",
            "title": "I visited this facility",
            "content": "The facility was new and in good repair. The staff was warm and friendly.",
            "rating": 5,
            "staff_score": 5,
            "activities_score": 5,
            "food_score": 4,
            "facilities_score": 5,
            "value_score": 5,
            "provider_response": null,
            "moderation_status": "unmoderated",
            "moderated_at": null,
            "author": {
                "name": "SatisfiedReviewer11",
                "email": "SatisfiedReviewer11@example.com",
                "url": "https://www.twitter.com/SatisfiedReviewer11"
            },
            "origin_url": "https://www.partner-site.com/assisted-living-in-california/nice-provider#reviews",
            "created_at": "2017-07-28T14:34:47.259-07:00",
            "updated_at": "2017-07-28T14:34:47.259-07:00"
        }
    }
}
```

> Error responses will contain JSON API formatted error messages:

```json
{
    "errors": [
        {
            "source": {
                "pointer": "/data/attributes/content"
            },
            "detail": "can't be blank"
        }
    ]
}
```

### Review Data Attributes

<aside class="notice">
For all of the numeric attributes 0 is equal to N/A
</aside>

Attribute | Type     | Description
--------- | --------- | ---------
resource_id | Integer | The primary key ID of the service provider that was reviewed
property_id | Integer | ID of the property that connects multiple resource type
resource_url | Url | The public URL of the service provider that was reviewed.
resource_name | String | The Name of the service provider that was reviewed
author | Object | `name`, `email` and `url` fields for the Author of the review.
title | String | The headline of the review, typically a description of the reviewers relation to the service provider provider.
content | Text | The full text of the review.
origin_url | Url | A url to the site the review was created on.
moderation_webhook_url | Url | A URL where you can receive moderation status updates as a webhook.
rating | 1-5 | Overall Raring.
staff_score | 1-5 | Staff Rating.
activities_score | 1-5 | Rating of Leisure Activities.
food_score | 1-5 | Rating of the food available.
facilities_score | 1-5 | Rating of the facility quality and cleanliness.
value_score | 1-5 | Rating of the value.

### HTTP Response Statuses

Status | Description
--------- | -----------
201 | Created
422 | Unprocessable Entity

## Creating a Response to a Review

### HTTP Request

`POST https://dir.caring.com/api/v2/reviews/:id/responses.jsonapi`

```shell
curl "https://dir.caring.com/api/v2/reviews/2/responses.jsonapi" \
  -H "Caring-Partner: TOKEN_VALUE" \
  -d '{
        "data": {
            "attributes": {
                public_response: "Thanks for the positive review.",
                "author": {
                    "name": "Jane Doe",
                    "email": "jane.doe@example.com",
                    "title": "Community Manager"
                }

            }
        }
    }'
```

### Request Attributes

Parameter | Type | Description
--------- | ----------- | -----------
public_response | Text | The body of the response to the review.
author_name | String | Name of the Author of the Review Response.
author_title | String | Job title of the person responding to the review.
author_email | String | Email address of the Author of the Review Response.
author | Object | Convenient assignment of `name` ,`title` and `email` fields for the Author of the review.

> A successful response will respond with `HTTP 201 Created` and JSON like this:

```json
{
    "data": {
        "id": "1",
        "type": "provider_review_responses",
        "attributes": {
            "local_review_id": 2,
            "author": {
                "title": "Community Manager",
                "name": "Jane Doe",
                "email": "jane.doe@example.com"
            },
            "public_response": "Thank you for your honesty, we'll work to address those issues.",
            "status": "pending",
            "created_at": "2017-07-31T20:58:33.849-07:00",
            "updated_at": "2017-07-31T20:58:33.849-07:00"
        }
    }
}
```

> Errors will respond with `HTTP 422 Unprocessable Entity` and contain JSON API formatted error messages:

```json
{
    "errors": [
        {
            "source": {
                "pointer": "/data/attributes/author_title"
            },
            "detail": "can't be blank"
        }
    ]
}
```

## Querying a Response by Review

```shell
curl "https://dir.caring.com/api/v2/reviews/2/responses.jsonapi" \
  -H "Caring-Partner: TOKEN_VALUE"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2000",
    "type": "provider_review_responses",
    "attributes": {
      "local_review_id": 2,
      "author": {
        "title": "Community Manager",
        "name": "Jane Doe",
        "email": "jane.doe@example.com"
      },
      "public_response": "Thanks for the positive review.",
      "status": "pending",
      "created_at": "2021-10-08T14:56:45.000-07:00",
      "updated_at": "2021-10-08T14:56:45.000-07:00"
    }
  }
}
```

This endpoint retrieves a single response to a review.

### HTTP Request

`GET https://dir.caring.com/api/v2/reviews/:id/responses.jsonapi`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the review whose response is to be retrieved

## Querying a Response to a Review

```shell
curl "https://dir.caring.com/api/v2/provider_review_responses/2000.jsonapi" \
  -H "Caring-Partner: TOKEN_VALUE"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "2000",
    "type": "provider_review_responses",
    "attributes": {
      "local_review_id": 2,
      "author": {
        "title": "Community Manager",
        "name": "Jane Doe",
        "email": "jane.doe@example.com"
      },
      "public_response": "Thanks for the positive review.",
      "status": "pending",
      "created_at": "2021-10-08T14:56:45.000-07:00",
      "updated_at": "2021-10-08T14:56:45.000-07:00"
    }
  }
}
```

This endpoint retrieves a single response to a review.

### HTTP Request

`GET https://dir.caring.com/api/v2/provider_review_responses/:id.jsonapi`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the response to a review to retrieve

## Moderation Webhook

If a review is created with the `moderation_webhook_url` attribute set, a moderation action will trigger a request will be sent to that URL with an `HTTP POST`. This request includes all of the attributes that make up the review. The `POST` request will have a `User-Agent` header of `Caring.com Review Moderation Webhook` and a `Referer` header of `https://dir.caring.com`.

> Example Webhook Payload

```json
{
  "review": {
    "id": 1579647,
    "resource_id": 2664,
    "resource_url": "http://www.caring.test/local/assisted-living-facilities-in-salisbury-maryland/lakeside-assisted-living",
    "resource_name": "Lakeside Assisted Living",
    "chain_name": null,
    "title": "I am a friend or relative of a current/past resident",
    "content": "My grandmother and grandfather stayed at this facility for several years.",
    "rating": 5.0,
    "staff_score": 5.0,
    "activities_score": 5.0,
    "food_score": 4.0,
    "facilities_score": 4.0,
    "value_score": 5.0,
    "provider_response": null,
    "moderation_status": "unmoderated",
    "rejection_reason": null,
    "moderated_at": null,
    "author": {
        "name": "SatisfiedReviewer11",
        "email": "SatisfiedReviewer11@example.com",
        "url": "https://www.twitter.com/SatisfiedReviewer11"
    },
    "origin_url": null,
    "created_at": "2019-05-17T01:58:37.000-07:00",
    "updated_at": "2019-05-17T02:10:34.000-07:00"
  }
}
```
