# Leads

|Name|Required|Data Type|Description|
|--- |--- |--- |--- |
|affiliate_campaign||String|Opaque string for the affiliate to use to store their campaign name. Max length of 255 characters.|
|affiliate_lead_id||String|The ID of the lead in the affiliate's system. Max length of 255 characters.|
|affiliate_notes||String|Free form text from the affiliate. Max length of 1024 characters.|
|alternate_call_time||Time of Day|The preferred time to call the alternate phone.|
|alternate_payment_method||Payment Method|A second way for the caregiver to pay for the care.|
|alternate_phone_number||Phone Number|A second phone number.|
|browser|✓|String|The user-agent string of the caregiver's browser. Max length of 255 characters.|
|campaign_url||String|The URL that the caregiver entered on. Caring.com may access this URL for quality assurance purposes. Max length of 255 characters.|
|care_location||String|The City and State (formatted as "City, State") or Zipcode where care is desired. For home-care services, a zip code is preferred over a city. Caring.com will validate that this is a valid US region.|
|email_address|✓|Email Address|The email address of the caregiver. In addition to being well-formed, Email addresses are validated using a 3rd party data verification service.|
|first_name|✓|String|The first name of the caregiver. Max length of 255 characters.|
|relationship_name|✓ (*)|Relationship Name|The relationship of the caregiver to the care recipient. (*) Only one of relationship_name or inquiry_for must be included.|
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
|type_of_care|✓|Care Type|What kind of care is being sought.|
