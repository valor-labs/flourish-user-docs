---
title: "Payments"
linkTitle: "Payments"
simple_list: true
weight: 20
---

The following document gives a general overview about the different integration types and Flourish payment process. To learn more about the different payment-related topics follow our [API Documentation](). It will take you to a more detailed description including interactive examples.

## Transaction Process

![](transaction-states.png)

## Managing Payment Types

### List Payment Types

To return the list of all available payment types and providers, use following API endpoint:

```json
Name:         "GetPaymentTypes",
Method:       "GET",
Pattern:      "/v1/api/grow/paymenttypes",
```

as a result, you will receive a list of currently available payment options

```
PaymentTypeIDCash              = 1
PaymentTypeIDCanPay            = 2
PaymentTypeIDCheck             = 3
PaymentTypeIDCreditCard        = 4
PaymentTypeIDDebitCard         = 5
PaymentTypeIDGiftCard          = 6
PaymentTypeIDLinx              = 7
PaymentTypeIDManual            = 8
PaymentTypeIDStoreCredit       = 9
PaymentTypeIDStoreCreditIssued = 10
```

### Enabling / Disabling Payment Type

To enable or disable certain payment type, use following API requests, where `PaymentTypeID` is a corresponding number from the list of currently available payment types:

#### API

Enable:

```json
Name:         "EnablePaymentType",
Method:       "PUT",
Pattern:      "/v1/api/grow/paymenttypes/{" + orderPaymentTypeIDKey + "}/enable",
```

Disable:

```json
Name:         "DisablePaymentType",
Method:       "PUT",
Pattern:      "/v1/api/grow/paymenttypes/{" + orderPaymentTypeIDKey + "}/disable",
```

## LinX

LINX is the primary provider of credit and debit merchant processing services for legal cannabis dispensaries in the United States.

```json
Name:         "LinxBalanceCheck",
Method:       "POST",
Pattern:      "/v1/api/payments/linx/balance",
```

```json
Name:         "LinxGetAccessToken",
Method:       "GET",
Pattern:      "/v1/api/payments/linx/accesstoken",
```

## CanPay

CanPay offers payment solutions for the State Regulated Cannabis Industry and other emerging markets

```json
No Info Found
```

## Manual Payment

**Manual Payments:** Payments that supposed to be transacted with a third-party transaction, via LINX or CanPay, but for one reason or another, they weren't able to be processed in Flourish. The transaction still needs to be recorded in Flourish, and this is possible via Manual Payment.

To proceed with Manual Payment, merchant needs to enter the amount of payment received via transaction that needs to be recorded, the date (defaults to today) the transaction occurred, the payment method (either LINX or CanPay), and last, the ID of the transaction that was received.

### API

To submit a transaction, use following API call:

```json
Name:         "PostOrderPaymentTransaction",
Pattern:      "/v1/api/grow/customers/{" + customerIDKey + "}/orders/{" + orderIDKey + "}/payment",
Method:       "POST",
```

Important request strings:

`"payment_type_id": 8,` - PaymentTypeID, 8 is Manual
`"payment_location_id": 1,` - Always 1, stands for *InStore*
`"till_id": 2,` - Purchase till number, required for CanPay & Linx & Manual
`"reference_token":` - "LINX"  or "CANPAY"
`"reference_id": "12345"` -  Linx or CanPay reference ID

## DataMotio

DataMotio is a third party virtual credit card payment solution, that provides the ability to accept credit card payments through a customer handled standard and secured CC terminal / chip reader. Having this functionality allows us to quickly and securely accept credit card payments without needing to handle the customer’s credit card.

The DataMotio credit card solution requires two company level sets of credentials, one for the terminal API endpoints and one for the charge endpoints. These are the company level credentials and can be stored directly in the Flourish system with no UI. The Merchant ID is facility specific and can be found in the "Payment Methods" tab in the facility settings. In this tab it is also possible enable/disable the payment method at a facility.

### API

To generate payment receipt for DataMotio transaction, use following API call:

```json
Name:         "GenerateDataMotioPaymentReceipt",
Method:       "GET",
Pattern:      BaseFacilityURL + "/transactions/{" + transactionIDKey + "}/datamotio/receipt",
```

## Purchase Order Payment Creation

### Validation

- Valid lot code is required
- Unit price is required
- Quantity is required
- Payment timestamp is required
- Passed lot code should be valid

**Valid Lot Code:** lot code is considered valid, if it matches all lot codes of orderlines tied to the payement.

## Post Order Payment Transaction

### Validation

Validation:

- Order ID required
- Facility ID required
- Only Cash & Credit
- Suported payment locations : Only **"Mobile"** and **"In Store"**
- Reference Token is required for CanPay method
- Tills shouldn't be closed
- LinX:
  - Reference Token is required (ref token = card number)
  - Customer identification number is required
  - Customer identification type should be "Driver License" or "Passport"
  - If customer identification type is "Driver License" there's should be a drivers license state (CustomerState field in code)
  - If "passport" there's should be a passport country
  - Customer name is required
