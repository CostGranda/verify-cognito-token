# Verify Cognito Token

Verify either the ID token or the access token provided by AWS Cognito.

This is a Node friendly refactor of AWS labs' [decode-verify-jwt](https://github.com/awslabs/aws-support-tools/blob/master/Cognito/decode-verify-jwt/decode-verify-jwt.js). The process is explained in the section __Using ID Tokens and Access Tokens in your Web APIs__ from this [AWS Document](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-with-identity-providers.html).

Install with `npm install verify-cognito-token -S`

Usage: 

```
const params = {
  region: '<your-aws-region>',
  userPoolId: '<your-user-pool-id>',
  appClientId: '<optional>'
}

const verify = require('verify-cognito-token')(params);

verify(token)
.then(result =>{
  //result will be `true` if token is valid or non-expired
  //result will be `false` if token is invalid or expired
})

```

The `userPoolId` parameter is available from Cognito/Manage Your User Pools/<Your Pool Name>/General Settings. 

The `appClientId` is an optional parameter used to match against the ID token's audience claim.