## GoMedigap Direct Post API Documentation

This specification details the direct post interaction between lead vendors and GMG.

### Spec
**POST** `https://mediapp.gomedigap.com/api/leads/add`

*Receive new lead payload from vendor. Used to create new record in Mediapp.*

### Content Type

Consumes | Produces
-------- | --------
`application/json` | `application/json`

### Parameters

**body** *(required)*

```json
{
    "CampaignId": "<Provided by GMG>",
    "firstname": "Johnny",
    "lastname": "Appleseed",
    "phone": "5125551234",
    "email": "johnny.appleseed@example.com",
    "zip": 78746,
    "city": "Austin",
    "state": "TX",
    "birthday": "MM/DD/YYYY",
    "tobacco": "Y",
    "gender": "M",
    "ip": "127.0.0.1",
    "rid": "your_sub_source_identifier",
    "gclid": "the_google_click_identifier",
    "campaign": "your_ppc_campaign_identifier",
    "src": "your_source_identifier",
    "xid": "your_lead_id",
    "alliance": {
        "allianceId": "gmg_12345",
        "allianceUid": "gmg_u_12345",
        "alliancePartnerId": "gmg_partner_12345"
    },
    "tcpa_token": "tcpa_token_value",
    "tcpa_text": "tcpa_text_value"
}
```

#### Parameter Notes (internal use)

Parameter | Notes | DB Column
----------|-------|----------
`rid` | Limit 45 characters. Overwrites "src". | leads.rid & leads.visit_source
`gclid` | Limit 100 characters. | leads.gclid
`campaign` | Limit 100 characters. | leads.ppc_campaign
`src` | Limit 45 characters. | leads.visit_source

### Responses

**Code** `200`

*Received payload successfully and created lead.*

```json
{
    "status": "success"
}
```

**Code** `500`

*Server Error*

```json
{
  "message": "Server Error"
}
```

### Contact

Responsibility | Name | Email
---------------|------|------
Lead Buying | Jacob Von Feldt | <jacob.vonfeldt@gomedigap.com>
Marketing | Maddy Contois | <maddy.contois@gomedigap.com>
API Development | Patrick Guevara | <patrick.guevara@gomedigap.com>
