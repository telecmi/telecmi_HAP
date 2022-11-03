

## TeleCMI <--> HAP 


### Step 1

When customer call to HAP number (18000xxxx) ,TeleCMI will send following data in POST method and waiting for response too play Music file based on the role or location ,etc


Below is the  parameters send from TeleCMI in JSON 

| Attribute     |      Description                   |  Allowed Values	| Default Value |
|  ---          |    ---                             | ---              | ---           |
| action          | Type of the call Inbound or Outbound	         | string           | inbound          |
| from         | HAP customer number	   | String      | 91xxxxx        |
| to      | HAP Tollfree number	  | String | 1800xxxx          |
| time      | Time of the call | timestamp   | 1560008080           |
| cmiuuid      | Unique ID of the call | String   | 4249d25c-d181-4f3e-9d71-804f13d8aa24          |

Bellow is the sample request from TeleCMI

```javascript
{
 action: 'inbound',
 from: ' 9198xxxxxx',
 to: ' 1800xxxxx',
 time: 1667456463000,
 cmiuuid: '4249d25c-d181-4f3e-9d71-804f13d8aa24'
}
```



### Step 2

Once TeleCMI receive JSON response from HAP server , TeleCMI will play music to HAP customer and get input like press 1 for Tamil,2 for English.Once customer will press the button TeleCMI will POST HTTP  JSON data with following parameters 


Below is the  parameters send from TeleCMI in JSON 

| Attribute     |      Description                   |  Allowed Values	| Default Value |
|  ---          |    ---                             | ---              | ---           |
| dtmf          | Customer pressed button	         | string           | 1         |
| from         | HAP customer number	   | String      | 91xxxxx        |
| to      | HAP Tollfree number	  | String | 1800xxxx          |
| cmiuuid      | Unique ID of the call | String   | 4249d25c-d181-4f3e-9d71-804f13d8aa24          |

Bellow is the sample request from TeleCMI

```javascript
{
 from: 919894269392,
 to: 19178094404,
 dtmf: '2',
 cmuuid: 'c2fe1cae-4bbc-4d0c-934f-945667a21fcc',
 extra_params: '{}'
}
```








