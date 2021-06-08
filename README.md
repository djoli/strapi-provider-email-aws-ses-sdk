# strapi-provider-email-amazon-ses-sdk

An email provider for Strapi email plugin which supports mail through AWS SES, using the AWS SDK.

## Links

* [Strapi](https://strapi.io)
* [AWS SDK](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS.html)

## Prerequisites

You need to have the following installed in your Strapi project:
* `strapi-plugin-email`
* `aws-sdk`

## Installation
```
# using yarn
yarn add strapi-provider-email-amazon-ses-sdk

# using npm
npm install strapi-provider-email-amazon-ses-sdk --save

```

## Configuration

| Variable                | Type                    | Description                                                                                                                | Required | Default   |
| ----------------------- | ----------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------- | --------- |
| provider                | string                  | The name of the provider you use                                                                                           | yes      |           |
| providerOptions         | object                  | Will be directly given to AWS config. Please refer to [AWS Config](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/Config.html#constructor-property) doc for possible options. | yes      |           |
| settings                | object                  | Settings                                                                                                                   | no       | {}        |
| settings.defaultFrom    | string                  | Default sender mail address                                                                                                | no       | undefined |
| settings.defaultReplyTo | string \| array<string> | Default address or addresses the receiver is asked to reply to                                                             | no       | undefined |

> :warning: The Shipper Email (or defaultfrom) may also need to be changed in the `Email Templates` tab on the admin panel for emails to send properly
### Example

**Path -** `config/plugins.js`

```js
module.exports = ({ env }) => ({
  // ...
  email: {
    provider: 'amazon-ses-sdk',
    providerOptions: {
      region: 'us-east-1',
    },
    settings: {
      defaultFrom: 'from@mail.com',
      defaultReplyTo: 'reply@mail.com',
    },
  },
  // ...
});
```
