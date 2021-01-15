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

### :fire: Merge Trigger Email With Attachments

https://docs.oracle.com/en/cloud/saas/marketing/responsys-rest-api/op-rest-api-v1.3-campaigns-campaignname-emailattachments-post.html

POST /rest/api/v1.3/campaigns/{campaignName}/emailAttachments

```json
{
  "mergeTriggerRecordDataWithAttachments": {
    "mergeTriggerRecordsWithAttachments": [
      {
        "fieldValues": [
          "johndoe@mail.com"
        ],
        "optionalData": [
          {
            "name": "firstName",
            "value": "John"
          }
        ],
        "attachmentData": [
          {
            "name": "Hello World.pdf",
            "value": "JVBERi0xLjQKJYCAgIAKMSAwIG9iago8PC9QYWdlcyAyIDAgUiAvVmlld2VyUHJlZmVyZW5jZXMgOCAwIFIgL1R5cGUgL0NhdGFsb2cgPj4KZW5kb2JqCjIgMCBvYmoKPDwvQ291bnQgMSAvTWVkaWFCb3ggWzAgMCA1OTYgODQyIF0gL1R5cGUgL1BhZ2VzIC9SZXNvdXJjZXMgMyAwIFIgL0tpZHMgWzUgMCBSIF0gPj4KZW5kb2JqCjMgMCBvYmoKPDwvRm9udCA3IDAgUiA+PgplbmRvYmoKNCAwIG9iago8PC9GaWx0ZXIgL0ZsYXRlRGVjb2RlIC9MZW5ndGggNjAgPj4Kc3RyZWFtCnic0zdUMDZSCEnjcgrhMlQwAEKwgLm5sZ6FuZGBoUJILpeGR2pOTr5CeH5RToqipkJIFpdrCBcAWMsNBgplbmRzdHJlYW0KZW5kb2JqCjUgMCBvYmoKPDwvUGFyZW50IDIgMCBSIC9UeXBlIC9QYWdlIC9Db250ZW50cyA0IDAgUiA+PgplbmRvYmoKNiAwIG9iago8PC9CYXNlRm9udCAvQ291cmllci1Cb2xkIC9TdWJ0eXBlIC9UeXBlMSAvRW5jb2RpbmcgL1dpbkFuc2lFbmNvZGluZyAvVHlwZSAvRm9udCA+PgplbmRvYmoKNyAwIG9iago8PC8xIDYgMCBSID4+CmVuZG9iago4IDAgb2JqCjw8L0Rpc3BsYXlEb2NUaXRsZSB0cnVlID4+CmVuZG9iago5IDAgb2JqCjw8L1N1YmplY3QgKP7/AFMAYQBtAHAAbABlACAAYQBiAG8AdQB0ACAAYQAgAHMAaQBtAHAAbABlACAAJwBoAGUAbABsAG8AIAB3AG8AcgBsAGQAJwAgAHUAcwBpAG4AZwAgAFAARABGACAAQwBsAG8AdwBuKSAvQ3JlYXRvciAo/v8AbwByAGcALgBwAGQAZgBjAGwAbwB3AG4ALgBzAGEAbQBwAGwAZQBzAC4AYwBsAGkALgBIAGUAbABsAG8AVwBvAHIAbABkAFMAYQBtAHAAbABlKSAvQXV0aG9yICj+/wBTAHQAZQBmAGEAbgBvACAAQwBoAGkAegB6AG8AbABpAG4AaSkgL0NyZWF0aW9uRGF0ZSAoRDoyMDExMDMwNTIwMDYxNSswMScwMCcpIC9Qcm9kdWNlciAo/v8AUABEAEYAIABDAGwAbwB3AG4AIABmAG8AcgAgAEoAYQB2AGEAIAAwAC4AMQAuADApIC9UaXRsZSAo/v8AUABEAEYAIABDAGwAbwB3AG4AIAAtACAASABlAGwAbABvACAAdwBvAHIAbABkACAAcwBhAG0AcABsAGUpID4+CmVuZG9iagp4cmVmCjAgMTAKMDAwMDAwMDAwMCA2NTUzNSBmDQowMDAwMDAwMDE1IDAwMDAwIG4NCjAwMDAwMDAwODggMDAwMDAgbg0KMDAwMDAwMDE4NyAwMDAwMCBuDQowMDAwMDAwMjE5IDAwMDAwIG4NCjAwMDAwMDAzNDkgMDAwMDAgbg0KMDAwMDAwMDQxMSAwMDAwMCBuDQowMDAwMDAwNTEwIDAwMDAwIG4NCjAwMDAwMDA1MzkgMDAwMDAgbg0KMDAwMDAwMDU4MSAwMDAwMCBuDQp0cmFpbGVyCjw8L1Jvb3QgMSAwIFIgL0luZm8gOSAwIFIgL1NpemUgMTAgPj4Kc3RhcnR4cmVmCjEwMzcKJSVFT0Y="
          },
          {
            "name": "weather.jpg",
            "value": "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"
          }
        ]
      }
    ],
    "fieldNames": [
      "EMAIL_ADDRESS_"
    ]
  },
  "mergeRule": {
    "htmlValue": "H",
    "matchColumnName1": "EMAIL_ADDRESS_",
    "matchColumnName2": null,
    "optoutValue": "O",
    "optinValue": "I",
    "insertOnNoMatch": true,
    "defaultPermissionStatus": "OPTIN",
    "rejectRecordIfChannelEmpty": "E",
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
    "recipientId": 1001109,
    "success": true
  }
]
```

**Important!**
- Each email can contain a maximum of 10 attachments total
- Total size of all attachments for a single email is limited to 500 KB 

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
      "href": "/rest/api/v1.3/lists/{listName}/members",
      "method": "POST"
    },
    {
      "rel": "retrieveListRecipientsRIID",
      "href": "/rest/api/v1.3/lists/{listName}/members/<riid>",
      "method": "GET"
    },
    {
      "rel": "deleteListRecipientsRIID",
      "href": "/rest/api/v1.3/lists/{listName}/members/<riid>",
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