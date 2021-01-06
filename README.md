# oracle-responsys-rest-api
Personal documentation with examples.

### :fire: Merge Trigger Email
https://docs.oracle.com/en/cloud/saas/marketing/responsys-rest-api/op-rest-api-v1.3-campaigns-campaignname-email-post.html

POST https://rest001.rsys9.net/rest/api/v1.3/campaigns/TRIGR_EMAIL_API/email

``` json
{
  "mergeTriggerRecordData": {
    "mergeTriggerRecords": [
      {
        "fieldValues": [
          "bruno.pereira@compasso.com.br"
        ],
        "optionalData": [
          {
            "name": "NOME",
            "value": "John Doe"
          },
          {
            "name": "EMAIL",
            "value": "contact@johndoe.com"
          },
          {
            "name": "TELEFONE",
            "value": "(00) 00000-0000"
          },
          {
            "name": "ASSUNTO",
            "value": "Dúvidas"
          },
          {
            "name": "PEDIDO",
            "value": "0123456789"
          },
          {
            "name": "MENSAGEM",
            "value": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio. Quisque volutpat mattis eros. Nullam malesuada erat ut turpis. Suspendisse urna nibh, viverra non, semper suscipit, posuere a, pede."
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

``` json
[
  {
    "errorMessage": null,
    "success": true,
    "recipientId": 1001109
  }
]
```

**Campaign code**
``` html
<html>
  <head>
    <title></title>
  </head>
  <body>
    <div>
      <p><b>Nome</b>: TOKEN_|alias="DynamicVariable.NOME"|</p>
      <p><b>E-mail</b>: TOKEN_|alias="DynamicVariable.EMAIL"|</p>
      <p><b>Telefone</b>: TOKEN_|alias="DynamicVariable.TELEFONE"|</p>
      <p><b>Assunto</b>: TOKEN_|alias="DynamicVariable.ASSUNTO"|</p>
      <p><b>Pedido</b>: TOKEN_|alias="DynamicVariable.PEDIDO"|</p>
      <p><b>Mensagem</b>: TOKEN_|alias="DynamicVariable.MENSAGEM"|</p>
    </div>
  </body>
</html>
```