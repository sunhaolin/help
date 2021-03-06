# Workflow Request

Permission: Only administrators of space can send requests below.

#### Create a draft request

Request:
```bash
curl -X POST https://us.steedos.com/uf/api/instances -H "X-Auth-Token: f2KpRW7KeN9aPmjSZ" 
     -H "X-User-Id: fbdpsNf4oHiX79vMJ" -H "X-Space-Id: wsw1re12TdeP223sC"
```
```json
{
  "flow": "8hdjk8skas8sdsa",
  "applicant": "sjad832jhewd8",
  "values": { 
    "field_name_1": "valueoffield1",
    "field_name_2": "valueoffield2",
    "field_name_3": "valueoffield3",
    "subtable_name_1":[
      {
        "subfield_name_1": "valueofsubfield1",
        "subfield_name_2": "valueofsubfield2",
        "subfield_name_3": "valueofsubfield3"
      },
      {
        "subfield_name_1": "valueofsubfield1-2",
        "subfield_name_2": "valueofsubfield2-2",
        "subfield_name_3": "valueofsubfield3-2"
      }
    ]
  }
}

```
Note:

（1）"flow" is FlowID, "applicant" is UserID of applicant, "Values" is the details of the form, including the field and its value.

（2）The field names and field values in “values” must match the actual form. If there is a mistake, the form may display exception, because the server can not verify data integrity and format type.

Response:

（1）If the call is successful, status will returned to “success”, and data will be an Object Instance.

```json
{
  "status": "success",
  "data": {
    "id": "jdhas8sdsjasasad",
    "space": "sakd89s8d9sdksfa",
    "flow": "98sdfasd9ssdaff",
    "form": "kjsahdfkdsa78sd",
    "name": "answer of MIT",
    "applicant": "8wewqweqs8dafskw",  
    "applicant_name": "MJ",
    "applicant_organization": "82134kehfqw8awwer",
    "applicant_organization_name": "Sales",
    "submit_date": "2015-10-08T08:16:53.541Z",
    "values": {
      "field_name_1": "valueoffield1",
      "field_name_2": "valueoffield2",
    },
    "traces": [
      {  
        "id": "876asas88sakjdasfk",
        ......
      }
    ]     
  }
}
```
Note："id" is ID of this draft request instance, "space" is ID of this workspace, "flow" is ID of this flow, "form" is ID of this form, "name" is title, "applicant" is UserID of this applicant, "applicant_name" is name of this applicant, "applicant_organization" is GroupID of applicant's organization, "applicant_organization_name" is name of applicant's organization, "submit_date" is submit time, "values" is the details of the form, including the field and its value, "traces" is history records of this request instance.

（2）If the call is fail, status will returned to fail, and message will be the infomation of error.

```json
{
  "status": "fail",
  "message": "Session Expired"
}
```


#### Get pending request list

Request:
```bash
curl -X GET https://us.steedos.com/uf/api/instances?state=pending&userid=aksjhkdshasd 
     -H "X-Auth-Token: f2KpRW7KeN9aPmjSZ" -H "X-User-Id: fbdpsNf4oHiX79vMJ" 
     -H "X-Space-Id: wsw1re12TdeP223sC"
```

Response:

（1）If the call is successful, status will returned to “success”, and data will be an Array of Instances.

```json
{
  "status": "success",
  "data": [
    {
      "id": "oFpdgAMMr123A7P3a", 
      "flow_name": "buy ITC",
      "space_name": "mycompany",
      "name": "HP Printer", 
      "applicant_name": "Adam", 
      "applicant_organization_name": "Sales", 
      "submit_date": "2015-09-26T08:22:53.541Z", 
      "step_name":"Department Manager Review"      
    },
    {
      "id": "XoMMENu5hEe63XdTP", 
      "flow_name": "buy ITC",
      "space_name": "mycompany",
      "name": "DELL X218", 
      "applicant_name": "Cherry Chen", 
      "applicant_organization_name": "IT", 
      "submit_date": "2015-09-27T10:18:53.541Z", 
      "step_name":"Office Comfirm"      
    }
  ]
}
```
Note："id" is ID of this request instance, "flow_name" is name of this flow, "space_name" is name of this sapce, "name" is title,  "applicant_name" is name of this applicant, "applicant_organization_name" is name of applicant's organization, "submit_date" is submit time, "step_name" is current step name of this instance.

（2）If the call is fail, status will returned to fail, and message will be the infomation of error.

```json
{
  "status": "fail",
  "message": "state is null"
}
```

#### Query request details

Request:
```bash
curl -X GET https://us.steedos.com/uf/api/instances/oFpdgAMMr7F5A7P3a 
     -H "X-Auth-Token: f2KpRW7KeN9aPmjSZ" -H "X-User-Id: fbdpsNf4oHiX79vMJ" 
     -H "X-Space-Id: wsw1re12TdeP223sC"
```

Note："oFpdgAMMr7F5A7P3a" in URL is ID of this request instance.

Response:

（1）If the call is successful, status will returned to “success”, and data will be an Array of Instances.

```json
{
  "status": "success",
  "data": {
    "id": "jdhas8sdsjasasad",
    "space": "sakd89s8d9sdksfa",
    "flow": "98sdfasd9ssdaff",
    "form": "kjsahdfkdsa78sd",
    "name": "answer of MIT",
    "applicant": "8wewqweqs8dafskw",  
    "applicant_name": "MJ",
    "applicant_organization": "82134kehfqw8awwer",
    "applicant_organization_name": "Sales",
    "submit_date": "2015-10-08T08:16:53.541Z",
    "values": {
      "field_name_1": "valueoffield1",
      "field_name_2": "valueoffield2",
    },
    "traces": [
      {  
        "id": "sahdsj89sdfkjs8sfas",
        ......
      }
    ]     
  }
}
```
Note："id" is ID of this request instance, "space" is ID of this workspace, "flow" is ID of this flow, "form" is ID of this form, "name" is title, "applicant" is UserID of this applicant, "applicant_name" is name of this applicant, "applicant_organization" is GroupID of applicant's organization, "applicant_organization_name" is name of applicant's organization, "submit_date" is submit time, "values" is the details of the form, including the field and its value, "traces" is history records of this instance.

（2）If the call is fail, status will returned to fail, and message will be the infomation of error.

```json
{
  "status": "fail",
  "message": "instance is not found"
}
```

#### Submit request to next step

Request:
```bash
curl -X POST https://us.steedos.com/uf/api/instances/oFpdgAMMr7F5A7P3a 
     -H "X-Auth-Token: f2KpRW7KeN9aPmjSZ" -H "X-User-Id: fbdpsNf4oHiX79vMJ" 
     -H "X-Space-Id: wsw1re12TdeP223sC"
```
```json
{
  "nextstep_name": "Manager Approval",
  "nextstep_users": ["aFpdgAMMr7F5A7P3a"]
}
```
Note："oFpdgAMMr7F5A7P3a" in URL is ID of this request instance. "nextstep_name" is name od next step, "nextstep_users" is an array, include userID of next step users.

Response:

（1）If the call is successful, status will returned to “success”, and data will be an Array of Instances.

```json
{
  "status": "success",
  "data": {
    "id": "jdhas8sdsjasasad",
    "space": "sakd89s8d9sdksfa",
    "flow": "98sdfasd9ssdaff",
    "form": "kjsahdfkdsa78sd",
    "name": "answer of MIT",
    "applicant": "8wewqweqs8dafskw",  
    "applicant_name": "MJ",
    "applicant_organization": "82134kehfqw8awwer",
    "applicant_organization_name": "Sales",
    "submit_date": "2015-10-08T08:16:53.541Z",
    "values": {
      "field_name_1": "valueoffield1",
      "field_name_2": "valueoffield2",
    },
    "traces": [
      {  
        "id": "ksafsdsd899sdfsdkf",
        ......
      }
    ]     
  }
}
```
Note："id" is ID of this draft request instance, "space" is ID of this workspace, "flow" is ID of this flow, "form" is ID of this form, "name" is title, "applicant" is UserID of this applicant, "applicant_name" is name of this applicant, "applicant_organization" is GroupID of applicant's organization, "applicant_organization_name" is name of applicant's organization, "submit_date" is submit time, "values" is the details of the form, including the field and its value, "traces" is history records of this instance.

（2）If the call is fail, status will returned to fail, and message will be the infomation of error.

```json
{
  "status": "fail",
  "message": "nextstep_users is null"
}
```
