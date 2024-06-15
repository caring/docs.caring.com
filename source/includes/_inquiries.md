# Inquiries

An Inquiry is basically a lead without a `provider_id`. For a list of parameters [See Creating a Lead](#creating-a-lead)

## Creating an Inquiry

### HTTP Request

`POST https://dir.caring.com/api/v2/inquiries.json`

```shell
curl "https://dir.caring.com/api/v2/inquiries.json" \
  -H "Caring-Partner: TOKEN_VALUE" \
  -d '{
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
