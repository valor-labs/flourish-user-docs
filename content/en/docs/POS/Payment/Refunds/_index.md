---
title: "Returns & Refunds"
linkTitle: "Returns & Refunds"
simple_list: true
weight: 20
---

Whether a purchase is made in physical store or online (via Credit Card, LINX, or CanPay) the customer has the option of returning and refunding the sale. This article provides details on the process of each of those transactions.

## Glossary

Here are some quick definitions of relevant terms:

- **Product Return:** is the process of a customer taking previously purchased merchandise back to the retailer, and in turn exchanging for another item (identical or different) or receiving a refund in cash, or a account credit.

- **Account credit refunds**: Customer may request a full or partial refund of a sale, resulting in the client account balance, that he can spend on future purchases.

- **Cash refunds:** Customer may request a full or partial refund of a sale in cash, this method helps to increase customer satisfaction.

- **Manual Payments:** Payments that supposed to be transacted with a third-party transaction (LINX or CanPay), but for one reason or another, they weren't able to be processed in Flourish. The transaction still needs to be recorded in Flourish, and this is possible via Manual Payment

## Things to know

- Returns must be done at the same dispensary that made the initial sale.
- The PackageLabel needs to be the same as the original sale to maintain compliant traceability records
- The `PatientLicenseNumber` and/or `CaregiverNumber` that was recorded on the original receipt should be on the new return receipt. This is critical in states where recurring purchase allotments are programmatically governed;
- Returns can be processed even if the original sale has been finalized.
- Returns can be processed even if the original package has been consumed.

## Refund options

![](https://i.imgur.com/0mA59VG.png)

![](https://i.imgur.com/rHUHkhN.png)

![](https://i.imgur.com/SGpG6Kf.png)

## Refunds

There are two methods to make a refund  - cash and account credit.

The manager has the ability to choose cash as the refund method instead of the default method, account credit. This functionality allows issuing cash refunds to customers in cases where an account credit refund isn't acceptable.

The refund method will always default to "Account Credit." Changing the refund method to "Cash" will require a manager pin approval every time. When a refund is processed via cash, the till will need to be updated with a transaction to reflect the outgoing cash.

### API Calls

**GET** ```go_api/grow/order/refundtypes``` - get all available refund methods

**POST** ```go_api/grow/facilities/${facility_id}/refund``` - create a new transaction, initiate refund

**GET** ```go_api/grow/facilities/${facility_id}/order/${order_id}/refunds``` - get refunded items for current order

### Validation

- Customer can't refund more than the initial purchase amount;
- Returns possible infinite amount of time;
- If customer refunded the purchase, the same transaction can't be voided;
- Partial returns are possible;
- When multiples of an item are purchased, the sale cannot be partially returned. Example: A client wants to return one of two prerolls that they bought. He will need to return both joints;