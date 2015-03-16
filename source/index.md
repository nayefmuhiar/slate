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
  The API is still under construction and changes might occur at any time, major changes will also increase the version of the API.

  Current API version: 1.0

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization:Token token=APIKEY"
```

Eon Access expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization:Token token=APIKEY`

<aside class="notice">
You must replace `APIKEY` with your personal API key.
</aside>

# Cases

## Get All Cases
You can filter cases by status.

A list of available statuses:

1- pending_conversion.


```shell
curl "http://access.eonaligner.com/api/v1/cases"
  -H "Authorization:Token token=APIKEY"
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

`GET http://access.eonaligner.com/api/v1/cases`

### Query Parameters

Parameter | Description | Required?
--------- | ----------- | -----------
filter | If set to one of the allowed filters, returns cases with status equal to the filter. | No


<aside class="success">
Remember — Authentication is required!
</aside>

## Get a specific Case

This endpoint takes a flag to return latest active treatment setup id along with the case.


```shell
curl "http://access.eonaligner.com/api/v1/cases/1887"
  -H "Authorization:Token token=APIKEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": "1887",
  "case_type": "Full",
  "clinical_findings": {"molar"=>"{\"class1\"=>{\"R\"=>\"true\", \"L\"=>\"false\"}, \"class2\"=>{\"R\"=>\"false\", \"L\"=>\"true\"}, \"class3\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}}", "canine"=>"{\"class1\"=>{\"R\"=>\"true\", \"L\"=>\"false\"}, \"class2\"=>{\"R\"=>\"false\", \"L\"=>\"true\"}, \"class3\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}}", "skeletal"=>"I", "restriction"=>"{\"R\"=>{\"U8\"=>\"false\", \"U7\"=>\"false\", \"U6\"=>\"false\", \"U5\"=>\"false\", \"U4\"=>\"false\", \"U3\"=>\"false\", \"U2\"=>\"false\", \"U1\"=>\"false\", \"L8\"=>\"false\", \"L7\"=>\"false\", \"L6\"=>\"false\", \"L5\"=>\"false\", \"L4\"=>\"false\", \"L3\"=>\"false\", \"L2\"=>\"false\", \"L1\"=>\"false\"}, \"L\"=>{\"U1\"=>\"false\", \"U2\"=>\"false\", \"U3\"=>\"false\", \"U4\"=>\"false\", \"U5\"=>\"false\", \"U6\"=>\"false\", \"U7\"=>\"false\", \"U8\"=>\"false\", \"L1\"=>\"false\", \"L2\"=>\"false\", \"L3\"=>\"false\", \"L4\"=>\"false\", \"L5\"=>\"false\", \"L6\"=>\"false\", \"L7\"=>\"false\", \"L8\"=>\"false\"}}", "lower_midline"=>"centered", "no_attachment"=>"{\"R\"=>{\"U8\"=>\"false\", \"U7\"=>\"false\", \"U6\"=>\"false\", \"U5\"=>\"false\", \"U4\"=>\"false\", \"U3\"=>\"false\", \"U2\"=>\"false\", \"U1\"=>\"false\", \"L8\"=>\"false\", \"L7\"=>\"false\", \"L6\"=>\"false\", \"L5\"=>\"false\", \"L4\"=>\"false\", \"L3\"=>\"false\", \"L2\"=>\"false\", \"L1\"=>\"false\"}, \"L\"=>{\"U1\"=>\"false\", \"U2\"=>\"false\", \"U3\"=>\"false\", \"U4\"=>\"false\", \"U5\"=>\"false\", \"U6\"=>\"false\", \"U7\"=>\"false\", \"U8\"=>\"false\", \"L1\"=>\"false\", \"L2\"=>\"false\", \"L3\"=>\"false\", \"L4\"=>\"false\", \"L5\"=>\"false\", \"L6\"=>\"false\", \"L7\"=>\"false\", \"L8\"=>\"false\"}}", "upper_midline"=>"centered", "chief_complaint"=>"Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.", "lower_midline_displacement"=>"", "upper_midline_displacement"=>""},
  "treatment_goals": {"molar"=>"{\"class1\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}, \"class2\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}, \"class3\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}}", "canine"=>"{\"class1\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}, \"class2\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}, \"class3\"=>{\"R\"=>\"false\", \"L\"=>\"false\"}}", "ap_goal"=>"{\"ipr36\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}, \"distalization\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}, \"mezialization\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}}", "overjet"=>"maintain", "overbite"=>"maintain", "arch_form"=>"maintain", "crossbites"=>"{\"R\"=>{\"U8\"=>\"false\", \"U7\"=>\"false\", \"U6\"=>\"false\", \"U5\"=>\"false\", \"U4\"=>\"false\", \"U3\"=>\"false\", \"U2\"=>\"false\", \"U1\"=>\"false\", \"L8\"=>\"false\", \"L7\"=>\"false\", \"L6\"=>\"false\", \"L5\"=>\"false\", \"L4\"=>\"false\", \"L3\"=>\"false\", \"L2\"=>\"false\", \"L1\"=>\"false\"}, \"L\"=>{\"U1\"=>\"false\", \"U2\"=>\"false\", \"U3\"=>\"false\", \"U4\"=>\"false\", \"U5\"=>\"false\", \"U6\"=>\"false\", \"U7\"=>\"false\", \"U8\"=>\"false\", \"L1\"=>\"false\", \"L2\"=>\"false\", \"L3\"=>\"false\", \"L4\"=>\"false\", \"L5\"=>\"false\", \"L6\"=>\"false\", \"L7\"=>\"false\", \"L8\"=>\"false\"}}", "extraction"=>"{\"R\"=>{\"U8\"=>\"false\", \"U7\"=>\"false\", \"U6\"=>\"false\", \"U5\"=>\"false\", \"U4\"=>\"false\", \"U3\"=>\"false\", \"U2\"=>\"false\", \"U1\"=>\"false\", \"L8\"=>\"false\", \"L7\"=>\"false\", \"L6\"=>\"false\", \"L5\"=>\"false\", \"L4\"=>\"false\", \"L3\"=>\"false\", \"L2\"=>\"false\", \"L1\"=>\"false\"}, \"L\"=>{\"U1\"=>\"false\", \"U2\"=>\"false\", \"U3\"=>\"false\", \"U4\"=>\"false\", \"U5\"=>\"false\", \"U6\"=>\"false\", \"U7\"=>\"false\", \"U8\"=>\"false\", \"L1\"=>\"false\", \"L2\"=>\"false\", \"L3\"=>\"false\", \"L4\"=>\"false\", \"L5\"=>\"false\", \"L6\"=>\"false\", \"L7\"=>\"false\", \"L8\"=>\"false\"}}", "leave_space"=>"{\"R\"=>{\"U8\"=>\"false\", \"U7\"=>\"false\", \"U6\"=>\"false\", \"U5\"=>\"false\", \"U4\"=>\"false\", \"U3\"=>\"false\", \"U2\"=>\"false\", \"U1\"=>\"false\", \"L8\"=>\"false\", \"L7\"=>\"false\", \"L6\"=>\"false\", \"L5\"=>\"false\", \"L4\"=>\"false\", \"L3\"=>\"false\", \"L2\"=>\"false\", \"L1\"=>\"false\"}, \"L\"=>{\"U1\"=>\"false\", \"U2\"=>\"false\", \"U3\"=>\"false\", \"U4\"=>\"false\", \"U5\"=>\"false\", \"U6\"=>\"false\", \"U7\"=>\"false\", \"U8\"=>\"false\", \"L1\"=>\"false\", \"L2\"=>\"false\", \"L3\"=>\"false\", \"L4\"=>\"false\", \"L5\"=>\"false\", \"L6\"=>\"false\", \"L7\"=>\"false\", \"L8\"=>\"false\"}}", "treat_arches"=>"upper_only", "lower_midline"=>"maintain", "upper_midline"=>"maintain", "resolve_crowding"=>"{\"procline\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}, \"procline_in\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}, \"expand\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}, \"expand_in\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}, \"ipr\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}, \"ipr_in\"=>{\"U\"=>\"false\", \"L\"=>\"false\"}}"},
  "treatment_summary": "text",
  "special_instructions": "text",
  "created_at": "2015-02-24 16:45:26",
  "updated_at": "2015-02-24 17:03:13",
  "status": "pending_courier_notification",
  "step": "summary",
  "uid": "150205140JD",
  "notes": "string",
  "upper_steps": "27",
  "lower_steps": "21",
  "steps_per_stage": "string",
  "ipr_file_name": "110-1305012RM_20FirstName_20LastName_20IPR_20indicator.pdf",
  "ipr_content_type": "application/octet-stream",
  "ipr_file_size": "327611",
  "sps_file_name": "110-1305012RM_20FirstName_20LastName_20Stage_20progress_20sheet.pdf",
  "sps_content_type": "application/octet-stream",
  "sps_file_size": "131994",
  "anterior": "Class 1",
  "posterior": "Class 2 Div 2",
  "irregularities": ["", "Anterior OpenBite"],
  "severity": "Severe",
  "ts_notes": "text"
}
```

This endpoint retrieves a specific Case.


### HTTP Request

`GET http://access.eonaligner.com/api/v1/cases/:case_id`

### URL Parameters

Parameter | Description | Required?
--------- | ----------- | -----------
:case_id | The ID of the case to retreive. | Yes

<aside class="success">
Remember — Authentication is required!
</aside>


## Get a specfic Treatment Setup

```shell
curl "http://access.eonaligner.com/api/v1/cases/:case_id/treatment_setups"
  -H "Authorization:Token token=APIKEY"
```

> The above command returns JSON structured like this:

```json
[{
  "id": "719",
  "version": "1",
  "case_id": "669",
  "created_at": "2013-09-24 10:22:32",
  "updated_at": "2014-05-17 15:05:31",
  "title": "string",
  "legacy_id": "519b7e14cf1e8c170c000494",
  "state": "active",
  "ipr_file_name": "110-1305012RM_20FirstName_20LastName_20IPR_20indicator.pdf",
  "ipr_content_type": "application/octet-stream",
  "ipr_file_size": "327611",
  "sps_file_name": "110-1305012RM_20FirstName_20LastName_20Stage_20progress_20sheet.pdf",
  "sps_content_type": "application/octet-stream",
  "sps_file_size": "131994",
  "ts_notes": "text",
  "notes": "text",
  "activated_at": "2014-05-17 15:03:32"
},
{
  "id": "722",
  "version": "2",
  "case_id": "669",
  "created_at": "2013-09-24 10:22:32",
  "updated_at": "2014-05-17 15:05:31",
  "title": "string",
  "legacy_id": "519b7e14cf1e8c170c000494",
  "state": "active",
  "ipr_file_name": "110-1305012RM_20FirstName_20LastName_20IPR_20indicator.pdf",
  "ipr_content_type": "application/octet-stream",
  "ipr_file_size": "327611",
  "sps_file_name": "110-1305012RM_20FirstName_20LastName_20Stage_20progress_20sheet.pdf",
  "sps_content_type": "application/octet-stream",
  "sps_file_size": "131994",
  "ts_notes": "text",
  "notes": "text",
  "activated_at": "2014-05-17 15:03:32"
}]
```

This endpoint retrieves a specfic Treatment Setup.

### HTTP Request

`GET http://access.eonaligner.com/api/v1/cases/:case_id/treatment_setups`

### Query Parameters

Parameter | Description | Required?
--------- | ----------- | -----------
:case_id | The ID of the case in which treatment setups are retrieved for. | Yes

<aside class="success">
Remember — Authentication is required!
</aside>



## Update Treatment Setup

Alberto can decide what format the teeth movements are sent.

```shell
curl -X POST -H "Content-Type: application/json" "http://access.eonaligner.com/api/v1/cases/:case_id/treatment_setups/:ts_id" 
-H "Authorization:Token token=APIKEY" -d 
'{
     "teeth_movement": 
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
    ],
    "converted_file_url": "url.s3.amazon.com"
}'
```

> The above command returns the updated treatment setup as JSON structured like this:

```json
{
  "id": "719",
  "version": "1",
  "case_id": "669",
  "created_at": "2013-09-24 10:22:32",
  "updated_at": "2014-05-17 15:05:31",
  "title": "string",
  "legacy_id": "519b7e14cf1e8c170c000494",
  "state": "active",
  "ipr_file_name": "110-1305012RM_20FirstName_20LastName_20IPR_20indicator.pdf",
  "ipr_content_type": "application/octet-stream",
  "ipr_file_size": "327611",
  "sps_file_name": "110-1305012RM_20FirstName_20LastName_20Stage_20progress_20sheet.pdf",
  "sps_content_type": "application/octet-stream",
  "sps_file_size": "131994",
  "ts_notes": "text",
  "notes": "text",
  "activated_at": "2014-05-17 15:03:32",
  "teeth_movement": 
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
    ],
  "converted_file_url": "url.s3.amazon.com"
}

    
```

This endpoint updates Treatment Setup

### HTTP Request

`POST http://access.eonaligner.com/api/v1/cases/:case_id/treatment_setups/:ts_id` -d

### Query Parameters

Parameter | Description | Required?
--------- | ----------- | -----------
:case_id | The ID of the case | Yes
:ts_id | The ID of the treatment setup to update. | Yes


<aside class="success">
Remember — Authentication is required!
</aside>
