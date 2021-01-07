# oracle-responsys-rest-api

Personal documentation with examples.

### :fire: Merge Trigger Email

https://docs.oracle.com/en/cloud/saas/marketing/responsys-rest-api/op-rest-api-v1.3-campaigns-campaignname-email-post.html

POST /rest/api/v1.3/campaigns/{campaignName}/email

```json
{
  "mergeTriggerRecordData": {
    "mergeTriggerRecords": [
      {
        "fieldValues": ["contato@mail.com"],
        "optionalData": [
          {
            "name": "FIRSTNAME",
            "value": "John"
          },
          {
            "name": "LASTNAME",
            "value": "Doe"
          },
          {
            "name": "MENSAGEM",
            "value": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio. Quisque volutpat mattis eros. Nullam malesuada erat ut turpis. Suspendisse urna nibh, viverra non, semper suscipit, posuere a, pede."
          }
        ]
      }
    ],
    "fieldNames": ["EMAIL_ADDRESS_"]
  },
  "mergeRule": {
    "htmlValue": "H",
    "matchColumnName1": "EMAIL_ADDRESS_",
    "matchColumnName2": null,
    "optoutValue": "O",
    "insertOnNoMatch": true,
    "defaultPermissionStatus": "OPTIN",
    "rejectRecordIfChannelEmpty": "E",
    "optinValue": "I",
    "updateOnMatch": "REPLACE_ALL",
    "textValue": "T",
    "matchOperator": "NONE"
  }
}
```

```json
[
  {
    "errorMessage": null,
    "success": true,
    "recipientId": 1001109
  }
]
```

**Campaign code**

```html
<html>
  <head>
    <title></title>
  </head>
  <body>
    <div>
      <p><b>First Nome</b>: TOKEN_|alias="DynamicVariable.FIRSTNAME"|</p>
      <p><b>Last Name</b>: TOKEN_|alias="DynamicVariable.LASTNAME"|</p>
      <p><b>Mensagem</b>: TOKEN_|alias="DynamicVariable.MENSAGEM"|</p>
    </div>
  </body>
</html>
```

### :fire: Merge List Recipients

https://docs.oracle.com/en/cloud/saas/marketing/responsys-rest-api/op-rest-api-v1.3-lists-listname-members-post.html

POST /rest/api/v1.3/lists/{listName}/members

```json
{
  "recordData": {
    "fieldNames": ["EMAIL_ADDRESS_"],
    "records": [["contact@johndoe.com"]],
    "mapTemplateName": null
  },
  "mergeRule": {
    "htmlValue": "H",
    "matchColumnName1": "EMAIL_ADDRESS_",
    "matchColumnName2": null,
    "optoutValue": "O",
    "insertOnNoMatch": true,
    "defaultPermissionStatus": "OPTIN",
    "rejectRecordIfChannelEmpty": "E",
    "optinValue": "I",
    "updateOnMatch": "REPLACE_ALL",
    "textValue": "T",
    "matchOperator": "NONE"
  }
}
```

```json
{
  "recordData": {
    "fieldNames": ["RIID_"],
    "records": [["2001029"]],
    "mapTemplateName": null
  },
  "mergeRule": {
    "textValue": "T",
    "htmlValue": "H",
    "optinValue": "I",
    "insertOnNoMatch": true,
    "updateOnMatch": "REPLACE_ALL",
    "matchColumnName1": "EMAIL_ADDRESS_",
    "matchColumnName2": null,
    "matchOperator": "NONE",
    "optoutValue": "O",
    "rejectRecordIfChannelEmpty": "E",
    "defaultPermissionStatus": "OPTIN",
    "matchColumnName3": null
  },
  "links": [
    {
      "rel": "self",
      "href": "/rest/api/v1.3/lists/Teste_Compasso/members",
      "method": "POST"
    },
    {
      "rel": "retrieveListRecipientsRIID",
      "href": "/rest/api/v1.3/lists/Teste_Compasso/members/<riid>",
      "method": "GET"
    },
    {
      "rel": "deleteListRecipientsRIID",
      "href": "/rest/api/v1.3/lists/Teste_Compasso/members/<riid>",
      "method": "DELETE"
    }
  ]
}
```

### :fire: Merge Profile Extension Recipients

https://docs.oracle.com/en/cloud/saas/marketing/responsys-rest-api/op-rest-api-v1.3-lists-listname-listextensions-petname-members-post.html

POST /rest/api/v1.3/lists/{listName}/listExtensions/{petName}/members

```json
{
  "recordData": {
    "fieldNames": ["RIID_", "EMAIL_ADDRESS", "ORDERID"],
    "records": [
      ["2001029", "contact@johndoe.com", "o12345"],
      ["2001049", "contact@janedoe.com", "o67890"]
    ],
    "mapTemplateName": null
  },
  "insertOnNoMatch": true,
  "updateOnMatch": "REPLACE_ALL",
  "matchColumnName1": "RIID"
}
```

```json
{
  "recordData": {
    "fieldNames": ["RIID_"],
    "records": [["2001029"], ["2001049"]],
    "mapTemplateName": null
  },
  "insertOnNoMatch": true,
  "updateOnMatch": "REPLACE_ALL",
  "matchColumnName1": "RIID",
  "matchColumnName2": null,
  "links": [
    {
      "rel": "self",
      "href": "/rest/api/v1.3/lists/{listName}/listExtensions/{petName}/members",
      "method": "POST"
    },
    {
      "rel": "deleteProfileExtensionRecipientsRIID",
      "href": "/rest/api/v1.3/lists/{listName}/listExtensions/{petName}/members/<riid>",
      "method": "DELETE"
    },
    {
      "rel": "retrieveProfileExtensionRecipientsRIID",
      "href": "/rest/api/v1.3/lists/{listName}/listExtensions/{petName}/members/<riid>",
      "method": "GET"
    }
  ]
}
```