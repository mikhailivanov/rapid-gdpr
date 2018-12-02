# API

## Methods <a id="methods"></a>

### SubmitPrivacySource <a id="submitprivacysource"></a>

Submits consents of Consent Pack given by Data Subject.

#### Signature <a id="signature"></a>

```java
@InvocableMethod(Label = 'Submit Privacy Source')
global static void RGDPR.ApiSubmitPrivacySource.action(
        RGDPR.ApiSubmitPrivacySource.ActionRequest[] requestActionInList)
```

#### Parameters <a id="parameters"></a>

_requestActionInList_

> ActionRequest object stored in a list variable. ActionRequest object has the following signature. Read _Description_ modifier inside of _@InvocableVariable_ annotation next to each parameter for more details:
>
> ```java
> global with sharing class ActionRequest {
>     @InvocableVariable(
>             Label = 'Data Subject ID'
>             Description = 'ID of a Lead or Contact who is giving permissions'
>             Required = true)
>     global Id dataSubjectId;
> ​
>     @InvocableVariable(
>             Label = 'Privacy Source Name'
>             Description = 'Unique name of Privacy Source the giving permissions will be associated with'
>             Required = true)
>     global String privacySourceName;
> ​
>     @InvocableVariable(
>             Label = 'Consents JSON'
>             Description = 'Consents the data subject gave in JSON format')
>     global String consentsJson;
> }
> ```

_consentsJson parameter of ActionRequest_

> There is a format of the JSON:
>
> ```javascript
> [
>   {
>     // Unique name of consent request. Required. Cannot be set to null.
>     "consentRequest": "...",
>
>     // Unique name of point of contact. Optional. Can be omitted or set to null.
>     "contactPoint": "...",
>
>     // Frequency String. Can be set to the following values: 
>     //     Once a Week, Twice a Week, 
>     //     Once a Month, Twice a Month, 
>     //     Once a Year, Twice a Year.
>     // Optional. Can be omitted or set to null.
>     "frequency": "..."
>   },
>   {
>     "consentRequest": "...",
>     "contactPoint": "...",
>     "frequency": "..."
>   }
> ]
> ```

#### Examples <a id="examples"></a>

_**Apex Code**_

You can call this method from Apex Code.

```java
RGDPR.ApiSubmitPrivacySource.ActionRequest requestAction =
        new RGDPR.ApiSubmitPrivacySource.ActionRequest();

requestAction.dataSubjectId = '0036A00000Zid1oQAB';
requestAction.privacySourceName = 'Web';
requestAction.consentsJson = '[' +
        '{"consentRequest":"Call/Marketing/Football","contactPoint":null,"frequency":null},' +
        '{"consentRequest":"Email","frequency":"Once a Week"}]';

RGDPR.ApiSubmitPrivacySource.action(
        new RGDPR.ApiSubmitPrivacySource.ActionRequest[] { requestAction });
```

_**Process Builder**_

You can call this method from Process Builder.

_**REST API**_

You can call this method by REST API. You can read more [here](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/resources_actions_invocable_custom.htm).

URL: /services/data/vXX.X/actions/custom/apex/RGDPR\_\_ApiSubmitPrivacySource

{% hint style="warning" %}
You must escape every "-character of consentsJson with \-character. See example below:
{% endhint %}

```javascript
{
  "inputs": [
    {
      "dataSubjectId": "0036A00000Zid1oQAB",
      "privacySourceName": "Web",
      "consentsJson": "[{\"consentRequest\":\"Call/Marketing/Football\",\"contactPoint\":null,\"frequency\":null},{\"consentRequest\":\"Email\",\"frequency\":\"Once a Week\"}]"
    }
  ]
}
```

