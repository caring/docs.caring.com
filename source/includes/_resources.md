# Resources

A resource is a care provider. To create leads within the Caring.com APIs you will need to know the resource `ID`.

## Querying the collection

`GET https://dir.caring.com/api/v2/resources.json`

```shell
curl "https://dir.caring.com/api/v2/resources.json" \
  -H "Caring-Partner: TOKEN_VALUE"
```

> The above command returns a paginated JSON response like this:

```json
{
  "results": [
    {
      "id": 551,
      "address": {
        "address_line1": "2280 North Highway 29",
        "address_line2": "",
        "city": "Newnan",
        "county": "Coweta County",
        "state": "GA",
        "zip_code": "30265",
        "latitude": 33.4931,
        "longitude": -84.6741
      },
      "care_type": "retirement_community",
      "caring_url": "https://www.caring.com/senior-living/georgia/newnan/wesley-woods-of-newnan",
      "chain": "Wesley Woods Senior Living, Inc.",
      "description": "Refund Plans: 90% of Entrance Fee; Traditional (Price: 66% (Avg.) of Entrance Fee). Assisted Living and Nursing Care on Fee-For-Service basis.",
      "name": "Wesley Woods of Newnan",
      "photos": [
        "https://d13iq96prksfh0.cloudfront.net/cdn/photos/218935/original.jpeg",
        "https://d13iq96prksfh0.cloudfront.net/cdn/photos/217572/original.png",
        "https://d13iq96prksfh0.cloudfront.net/cdn/photos/217573/original.png",
        "https://d13iq96prksfh0.cloudfront.net/cdn/photos/217574/original.png",
        "https://d13iq96prksfh0.cloudfront.net/cdn/photos/217575/original.png"
      ],
      "thumbnail": "https://d13iq96prksfh0.cloudfront.net/cdn/photos/218935/150x150%23.jpeg",
      "national_aggregator": false,
      "enhanced": true,
      "pets_allowed": "",
      "no_self_qualified": true,
      "special_comment_extra": "Experience the best of both worlds, small and large. Wesley Woods is a warm and friendly community located in Newnan, a charming historic town that boasts all of the modern conveniences and is just a short drive from Atlanta with its metropolitan perks and world-class airport. Click here for directions to Wesley Woods of Newnan.",
      "resident_capacity": 162,
      "local_resource_types": [
        "continuing_care_retirement_communities"
      ],
      "homecare_pulse_awards": "",
      "dma_region_code": 524,
      "features": {
        "alzheimers_care": false,
        "diet": [],
        "languages": []
      },
      "data_version": "69341935f928bf66fb339197103b371c"
    }
  ],
  "page": 1,
  "page_size": 50,
  "next_page": 2,
  "prev_page": null,
  "total_entries": 14572,
  "total_pages": 292,
  "next": "https://dir.caring.com/api/v2/resources.json?page=2&page_size=50",
  "prev": null
}
```

### Response Attributes

|Name|Description|
|--- |--- |
| results | A JSON array of resources |
| page | The current page number of the collection |
| page_size | The number of results on the page |
| next_page | The next page number of the collection |
| prev_page | The previous page number of the collection |
| total_entries | The total number of results across all pages |
| total_pages | The total number of pages that make up the collection |
| next | The URL to the next page of results |
| prev | The URL to the previous page of results |
