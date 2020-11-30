[![Build Status](https://travis-ci.org/chrispruitt/cognitojwt.svg?branch=master)](https://travis-ci.org/chrispruitt/cognitojwt)

# Decode and verify [Amazon Cognito](https://aws.amazon.com/cognito/) JWT tokens

### Note: tested on Python >= 3.6

### Installation

`pip install clp-cognitojwt`

### Usage

```python
import cognitojwt

id_token = '<YOUR_TOKEN_HERE>'
REGION = '**-****-*'
USERPOOL_ID = 'eu-west-1_*******'
APP_CLIENT_ID = '1p3*********'

# Sync mode
verified_claims: dict = cognitojwt.decode(
    id_token,
    REGION,
    USERPOOL_ID,
    app_client_id=APP_CLIENT_ID,  # Optional
    testmode=True  # Disable token expiration check for testing purposes
)

# Async mode
verified_claims: dict = await cognitojwt.decode_async(
    id_token,
    REGION,
    USERPOOL_ID,
    app_client_id=APP_CLIENT_ID,  # Optional
    testmode=True  # Disable token expiration check for testing purposes
)

```

Note: if the application is deployed inside a private vpc without internet gateway, the application will not be able to download the JWKS file.
In this case set the `AWS_COGNITO_JWSK_PATH` environment variable referencing the absolute or relative path of the jwks.json file.

This project was originally forked from https://github.com/borisrozumnuk/cognitojwt
