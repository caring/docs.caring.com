# Lead Statuses

## Creating a Lead Status

### HTTP Request

`POST https://dir.caring.com/api/v2/lead-status.json`

```shell
curl "https://dir.caring.com/api/v2/lead-status.json" \
  -H "Caring-Partner: TOKEN_VALUE" \
  -d '{
        "lead_id": "1234",
        "status": "valid_lead",
        "sub_status": "timeframe_30",
        "notes": "After speaking with the customer, they will likely be moving within 30 days."
    }'
```

### Request Attributes

Parameter | Type | Description
--------- | ----------- | -----------
lead_id | String | The id returned of the lead created on the API
affiliate_lead_id | String | The id of the lead in your system. If you passed us this field on creation, you may use this param in place of `lead_id` for sending statuses. Normally, prefer `lead_id`
status | String | One of the allowed lead statuses. [See Allowed Statuses](#allowed-statuses)
sub_status | String | A more granular reason for the lead status. [See Allowed Statuses](#allowed-statuses)
tour_time | DateTime String | An Hour of Day and a Date separated by a space. Ex: `07:00 01/31/2019`, `13:00 12/25/2019`
notes | String | A string providing extra information about a lead. Limit 2,000 characters.

> A successful response will respond with a `200 OK` and JSON like this:

```json
{
    "lead_id": 1234,
    "source": "affiliate",
    "status": "valid_lead",
    "sub_status": "timeframe_30",
    "notes": "After speaking with the customer, they will likely be moving within 30 days.",
    "tour_date": null,
    "tour_time": "",
    "tour_completed_at": null,
    "moved_in_at": null,
    "created_at": "2019-02-28T17:07:09.000-08:00",
    "processed": false,
    "created_by": ""
}
```

> Error responses will contain JSON API formatted error messages:

```json
{
    "error_code": 400,
    "error_message": "Validation Failed",
    "errors": [
        {
            "field": "status",
            "message": "status \"valid_leads\" is not a legal status. Must be one of valid_lead, accepted, changed_community, closed, community_not_appropriate, dummy_closed, email_only, inactive, interested_later, invalid_lead, memo, move_in_commitment, move_in_canceled, moved_in, moved_in_elsewhere, moved_in_elsewhere_commitment, moved_in_regulatory_exception, moved_out, mystery_shopper, no_interest_community, not_qualified, owner_changed, provider_qualified, reported_moved_in, reported_wait_list, tour_cancelled, tour_completed, tour_confirmed, tour_scheduled, tour_rescheduling, wait_list, reserved, receiving_care, pending, sold, credited_move_in, lead_received, lead_not_received"
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

## Allowed Statuses

The following is a complete set of status and substatus pairs that we allow to be sent for updates.

Status | Sub Status
------ | ----------
valid_lead | timeframe_30
valid_lead | timeframe_90
valid_lead | timeframe_gt_90
closed | required_care_unavailable
closed | received_lead_previously
closed | deceased
invalid_lead | unable_to_contact
invalid_lead | deceased
invalid_lead | bad_contact_information
not_qualified | too_young
owner_changed | N/A
tour_completed | N/A
tour_confirmed | N/A
tour_scheduled | N/A
tour_rescheduling | N/A
wait_list | N/A
closed | too_independent
closed | too_much_care
closed | too_young
closed | budget_too_low
