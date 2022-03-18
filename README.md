## Table of Contents
1. [Getting started](#Getting-started)
2. [The sandbox environment](#The-sandbox-environment)
    1. [Postman collection](#Postman-collection)
        1. [Supported use cases](#Supported-use-cases)
            1. [AIS](#AIS)
            2. [PIS](#PIS)



# Getting started
In order to access the production APIs, approval from Finanstilsynet in Norway is required. This in turn will enable you to acquire a Qualified Certificate for Website Authentication (QWAC) for PSD2 from an official certificate authority. The certificate is mandatory for use of both the PSD2 sandbox and production interfaces.

The base address for the sandbox API is https://psd2-sandbox.spvapi.no. No registration is required.

Please note that the production API can only be used with Sparebanken Vest customers.

# The sandbox environment
The Sandbox contains synthetic test-data only. This means that in order to complete the full process of a payment, specific customer data is required as input. For this reason we are supplying a Postman collection encompassing most supported use cases in the sandbox. Nevertheless, do play around with the data. The PSD2 sandbox instance is - except for the synthetic customer data - identical to the production instance. You will therefore still be able to test most of the possible error scenarios you'll encounter in production.

# Postman collection
The collection should be quite easy to navigate since it is structured based on interface and products.

It is a rule of thumb to start with the Postman tests on the top of the collection. E.g. when creating a `norwegian-domestic-credit-transfers` payment, the paymentId will be stored in the postman environment. So, when you afterwards call `Get Payment`, the newly created payment will be returned.

The postman collection can be found under the postman folder in this repository.

##  Strong Customer Authentication
Strong Customer Authentication(SCA) is completed by following the SCA-Redirect URLs in the response of a post/create operation. The SCA view for the sandbox will only accept and be usable for a limited set of synthetic customers.

### Customer IDs
Each postman test contains the header field PSU-ID. This field indicates which customer to select/input in the SCA process when confirming either a consent or a payment. Since the backend data is synthetic, a specific SCA customer ID is expected.

For Consents
- Nora Hansen - ID: 01015450068

For bulk-payments
- Emil Andersen - ID: 04015450156

For all other payment products
- Nora Hansen - ID: 01015450068

## Supported use cases
For all products, the level of authorisation tests will vary based on need. The available authorisation operations are
- Create
- List
- Get status
- Create cancellation
- List cancellation
- Get cancellation status

### Account information service (AIS)
#### Consent
- Create
- Get
- Get status
- Delete
#### Operations
- List accounts
- Get account w/wo balances
- Get balances
- Get transactions
- Get transaction
- List card accounts w/wo balances
- Get card account
- Get card balances
- Get card transactions

### Payment initiation service (PIS)
#### Norwegian domestic credit transfers
- Payment initiate
- Get
- Get status
- Cancel before SCA
- Cancel

#### Cross border credit transfers
- Payment initiate
- Get

#### Periodic payments
- Create
- Get
- Get status
- Cancel

#### Norwegian domestic credit transfers - bulk
- Payment initiate
- Get
- Get status
- Get sub payment
- Cancel

#### Signing-basket
- Payment initiate
- Get
- Get status
- Get sub payment status
- Cancel