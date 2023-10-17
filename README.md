![Logo](assets/logo.png)

# Kayna Widget

Kayna enables Carriers and Brokers to embed their insurance products within any Vertical SaaS platform. This supports seamless distribution to the platform's client base.
Using business data, risk is priced accurately, policies update in real-time adapting to business changes, ensuring the correct insurance level always!


## Integration of widget
### 1. Fetching the Token

1. Create a new 'authorizer' API on your Platform server
2. In the API, call Kayna's authorizer API with the following payload:
    * *'accessKey'* - Given by Kayna
    * *'secret'* - Given by Kayna
    * *'extCustomerId'* - Passed as a parameter to your API from your frontend
3. Return the received 'token' as a response from the API

**Important:** Just a reminder, it's crucial to integrate this API on your server and not on the client side. This precaution ensures that the keys used to acquire the token remain hidden and secure, preventing their exposure in the developer tools.

#### Get Token

```http
  POST https://staging-api.kayna.io/authorizer/token
```

#### Payload

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `accessKey` | `string` | **Required**. Your Platform's Access key |
| `secret` | `string` | **Required**. Your Platform's Secret key |
| `extCustomerId` | `string` | **Required**. The ID of the Platform user |

#### Response

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `token`      | `string` | Token that will initialize the widget |


### 2. Adding Kayna Widget to your Platform

```html
<html>
<head>[...]</head>
<body>
  [...]
  <div id="kayna"></div>
  [...]
  
  <script type="text/javascript" src="https://staging-widget.kayna.io/kayna.js" defer></script>
  <script type="text/javascript">
    const body = document.querySelector('body');
    body.onload = function () {
      const kaynaParams = {
        extCustomerName: '...',
        extCustomerEmail: '...',
        extCustomerID: '...',
        productId: '...',
        applicationFormData: {...}
      };

      const style = {
        width: '...',
        height: '...',
        primaryColor: '...',
        secondaryColor: '...',
      };

      const keys = {
        token: "..." //token received from the endpoint
        platformId: "...",
      };

      window.Kayna.init(kaynaParams, {
        style,
        keys
      });
    };
  </script>
</body>
</html>
```
Great news! Your widget has been successfully integrated!

Just a heads up, this is just an example of how you might integrate a widget using HTML and JS. Keep in mind that the actual steps could vary depending on the platform's technology stack. Feel free to adapt it as needed!
## Support

If you need assistance, feel free to reach out via email at info@kayna.io.
