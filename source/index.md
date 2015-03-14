---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href="#"> Eon access API </a>
  - <a href="#">Buttercloud</a>



includes:
  - errors

search: true
---

# Introduction

  This API is designed to work with Eon Converter and Eon viewer, it supports recieveing and sending of data related to cases and treatment setups.
  The API is still under construction and changes might occur at any time, major changes will also increase the versin of the API.

  Current API version: 1.0

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: APIKEY"
```

Eon Access expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: APIKEY`

<aside class="notice">
You must replace `APIKEY` with your personal API key.
</aside>

# Cases

## Get All Cases
You can filter cases by status.

A list of available statuses:

1- pending_conversion.


```shell
curl "http://access.eonaligner.com/api/cases"
  -H "Authorization: APIKEY"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "integer",
    "case_type": "string",
    "created_at": "datetime",
    "updated_at": "datetime",
    "status": "string",
    "uid": "string"
  },
  {
    "id": "integer",
    "case_type": "string",
    "created_at": "datetime",
    "updated_at": "datetime",
    "status": "string",
    "uid": "string"
  }
]
```

This endpoint retrieves all Cases in eon access.

### HTTP Request

`GET http://access.eonaligner.com/api/cases`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
filter | none | If set to one of the allowed filters, returns cases with status equal to the filter.


<aside class="success">
Remember — Authentication is required!
</aside>

## Get a specific Case

This endpoint takes a flag to return latest active treatment setup id along with the case.


```shell
curl "http://access.eonaligner.com/cases/<ID>"
  -H "Authorization: APIKEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": "integer",
  "case_type": "string",
  "clinical_findings": "hstore",
  "treatment_goals": "hstore",
  "treatment_summary": "text",
  "special_instructions": "text",
  "created_at": "datetime",
  "updated_at": "datetime",
  "status": "string",
  "step": "string",
  "uid": "string",
  "notes": "string",
  "upper_steps": "integer",
  "lower_steps": "integer",
  "steps_per_stage": "string",
  "ipr_file_name": "string",
  "ipr_content_type": "string",
  "ipr_file_size": "integer",
  "sps_file_name": "string",
  "sps_content_type": "string",
  "sps_file_size": "integer",
  "anterior": "string",
  "posterior": "string",
  "irregularities": "string",
  "severity": "string",
  "ts_notes": "text"
}
```

This endpoint retrieves a specific Case.


### HTTP Request

`GET http://access.eonaligner.com/cases/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the case to retreive

<aside class="success">
Remember — Authentication is required!
</aside>


## Get a specfic Treatment Setup

```shell
curl "http://access.eonaligner.com/api/cases/<CASE_ID>/treatment_setups"
  -H "Authorization: APIKEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": "integer",
  "version": "integer",
  "case_id": "integer",
  "created_at": "datetime",
  "updated_at": "datetime",
  "title": "string",
  "legacy_id": "string",
  "state": "string",
  "sps_file_name": "string",
  "sps_content_type": "string",
  "sps_file_size": "integer",
  "ipr_file_name": "string",
  "ipr_content_type": "string",
  "ipr_file_size": "integer",
  "ts_notes": "text",
  "notes": "text",
  "activated_at": "datetime"
}
```

This endpoint retrieves a specfic Treatment Setup.

### HTTP Request

`GET http://access.eonaligner.com/api/cases/<CASE_ID>/treatment_setups`

### Query Parameters

Parameter | Description
--------- | -----------
CASE_ID | The ID of the case in which treatment setups are retrieved for

<aside class="success">
Remember — Authentication is required!
</aside>



## Update Treatment Setup

Alberto can decide what format the teeth movements are sent.

```shell
curl "http://access.eonaligner.com/api/cases/<CASE_ID>/treatment_setups/<TS_ID>"
  -H "Authorization: APIKEY"
```

> The above command returns JSON structured like this:

```json

    [ 
      {
        "1": {
        "rotation_degree": null,
        "translation_mm": 2,
        "torque_degree": null,
        "tipping_degree": null,
        "ipr_amount_mm": null,
        "ipr_at_step": null,
        "attachement_placement": true,
        "attachement_placement_at_step": 4,
        "attachement_removal_at_step": 9,
        "extraction": true,
        "pontic": false
        }
      },

      {
        "2": {
        "rotation_degree": null,
        "translation_mm": 2,
        "torque_degree": null,
        "tipping_degree": null,
        "ipr_amount_mm": null,
        "ipr_at_step": null,
        "attachement_placement": true,
        "attachement_placement_at_step": 4,
        "attachement_removal_at_step": 9,
        "extraction": false,
        "pontic": true
        }
      }
    ]
```

This endpoint updates Treatment Setup

### HTTP Request

`GET http://access.eonaligner.com/api/cases/<CASE_ID>/treatment_setups/<TS_ID>`

### Query Parameters

Parameter | Description
--------- | -----------
CASE_ID | The ID of the case
TS_ID | The ID of the treatment setup to retreive


<aside class="success">
Remember — Authentication is required!
</aside>
