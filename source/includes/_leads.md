# Leads

A lead is the record for tracking customer interest for a resosource in the Caring.com catalog. For tracking we allow an `affiliate_lead_id` parameter to be passed so you can conveneiently use your internal record IDs to lookup a lead record or provide a status updates.

## Creating a Lead

### HTTP Request

`POST https://dir.caring.com/api/v2/leads.json`

```shell
curl "https://dir.caring.com/api/v2/leads.json" \
  -H "Caring-Partner: TOKEN_VALUE" \
  -d '{
        "provider_id": "CARING_PROVIDER_ID",
        "affiliate_lead_id": "ID_OF_THE_LEAD_IN_YOUR_SYSTEM",
        "email_address": "caring-lead@example.com",
        "browser": "Some User-Agent string",
        "care_location": "90210",
        "first_name": "Max",
        "last_name": "Powers",
        "relationship_name": "spouse",
        "phone_number": "3335551212",
        "tour_time": "09:00 03/13/2019",
        "type_of_care": "alzheimers_care_facilities",
        "phone_qualified": "no",
        "utm_source": "bamedical",
        "utm_campaign": "b2b+marketing",
        "ip_address": "0.0.0.0"
    }'
```

### Request Attributes

|Name|Required|Data Type|Description|
|--- |--- |--- |--- |
|affiliate_campaign||String|Opaque string for the affiliate to use to store their campaign name. Max length of 255 characters.|
|affiliate_lead_id||String|The ID of the lead your system if you want to continue to use that ID to track updates on the API. Max length of 255 characters.|
|affiliate_notes||String|Free form text from the affiliate. Max length of 1024 characters.|
|alternate_call_time||Time of Day|The preferred time to call the alternate phone.|
|alternate_payment_method||Payment Method|A second way for the caregiver to pay for the care.|
|alternate_phone_number||Phone Number|A second phone number.|
|browser|✓|String|The user-agent string of the caregiver's browser. Max length of 255 characters.|
|campaign_url||String|The URL that the caregiver entered on. Caring.com may access this URL for quality assurance purposes. Max length of 255 characters.|
|care_location||String|The City and State (formatted as "City, State") or Zipcode where care is desired. For home-care services, a zip code is preferred over a city. Caring.com will validate that this is a valid US region.|
|email_address|✓|Email Address|The email address of the caregiver. In addition to being well-formed, Email addresses are validated using a 3rd party data verification service.|
|first_name|✓|String|The first name of the caregiver. Max length of 255 characters.|
|relationship_name|✓ (*)|String|The relationship of the caregiver to the care recipient. **_Allowed Values:_** **spouse, son, son_in_law, daughter, daughter_in_law, granddaughter, grandson, sister, brother, friend, myself, patient_client, job, other_relative, unknown.** |
|ip_address|✓|IP Address|The IP Address of the caregiver.|
|last_name|✓|String|The last name of the caregiver. Max length of 255 characters.|
|living_situation||Living Situation|The current living situation of the care recipient.|
|max_budget||Integer|The maximum amount the caregiver can afford in US dollars/month.|
|min_budget||Integer|The least amount the caregiver is expecting to pay in US dollars/month.|
|notes||String|Free form text from the caregiver. Max length of 1024 characters.|
|payment_method||Payment Method|How will the caregiver pay for the care.|
|phone_number|✓|Phone Number|The primary phone number for contacting the caregiver.|
|phone_qualified|✓|Affirmation|Whether the affiliate has qualified the caregiver by phone.|
|preferred_call_time||Time of Day|The preferred time to call the primary phone.|
|provider_id|✓|String|The ID of the provider for which this lead is being submitted.|
|source_channel||Traffic Channel|The traffic source used to acquire the lead.|
|tour_time||Appointment|The date and time when the caregiver will tour the provider.|
|type_of_care|✓|Care Type|What kind of care is being sought. **_Allowed Values:_** **alzheimers_care_facilities, assisted_living_facilities, continuing_care_retirement_communities, geriatric_care_managers, home_healthcare_agencies, homecare_agencies, hospices, independent_living, nursing_homes**. |
|utm_source||String|Inbound tracking params for things like GA.|
|utm_campaign||String|Inbound tracking params for things like GA.|

> A successful response will respond with `HTTP 200 OK` and JSON like this:

```json
{
    "result": {
        "id": 7558089,
        "tour_time": "09:00 03/13/2019",
        "affiliate_campaign": null,
        "affiliate_lead_id": "ID_OF_THE_LEAD_IN_YOUR_SYSTEM",
        "affiliate_notes": null,
        "alternate_call_time": null,
        "alternate_payment_method": null,
        "alternate_phone_number": null,
        "browser": "Some User-Agent string",
        "campaign_url": null,
        "care_location": "90210",
        "email_address": "caring-lead@example.com",
        "first_name": "Max",
        "inquiry_for": "Spouse",
        "ip_address": "0.0.0.0",
        "last_name": "Powers",
        "living_situation": null,
        "max_budget": 0,
        "min_budget": 0,
        "notes": null,
        "payment_method": null,
        "phone_number": "(333) 555-1212",
        "phone_qualified": "no",
        "preferred_call_time": null,
        "price": null,
        "provider_id": 115,
        "source_channel": null,
        "care_level": null
    }
}
```

> Errors will respond with `HTTP 400 Bad Request` and contain JSON formatted error messages:

```json
{
    "error_code": 400,
    "error_message": "Validation Failed",
    "errors": [
        {
            "field": "ip_address",
            "message": "ip_address is required."
        },
        {
            "field": "phone_qualified",
            "message": "phone_qualified is required."
        },
        {
            "field": "phone_qualified",
            "message": "phone_qualified must be 'yes' or 'no'."
        },
        {
            "field": "provider_id",
            "message": "provider_id with ID CARING_PROVIDER_ID does not exist."
        }
    ]
}
```

### HTTP Response Statuses

Status | Description
--------- | -----------
200 | Success
400 | Validation Failed
401 | Unauthorized
