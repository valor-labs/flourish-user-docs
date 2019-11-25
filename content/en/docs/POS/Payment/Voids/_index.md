---
title: "Void Transactions"
linkTitle: "Void Transactions"
simple_list: true
weight: 20
---

Problematic transaction can be voided—even though it hasn't settled. Since the transaction is pending and has not cleared the customer's account, it means the sale can be prevented from going through.

## Glossary

- **Void transaction:**  Transaction that is canceled by a merchant or vendor before it settles through a consumer's debit or credit card account. It may appear as a pending transaction when the customer checks their account online.

## Understanding void transactions

When a transaction takes place, the merchant swipes the customer's debit or credit card. If there are enough funds in the customer's account, the terminal authorizes the transaction. But the transaction is not fully settled, as payment has to be released from the customer's account to the merchant.

If there is a problem with the transaction, it can be voided—even though it hasn't settled. Since the transaction is pending and has not cleared the customer's account, it means the sale can be prevented from going through.

In order to void the transaction, the customer must contact the merchant and request the transaction be reversed. Once it is voided, the transaction will show up on the customer's account as a pending transaction, which disappears after a certain amount of time.

The hold can last anywhere from 24 hours to several days, causing the customer an inconvenience because he or she won’t be able to access the money during that time.

A void transaction takes place on the same day as the original transaction.

## Voiding transactions

The manager can void cash and manual payment transactions in POS on the same day they occur. This allows for correcting human errors when a cash payment, manual LINX, or manual CanPay payment is recorded incorrectly.

### Transaction history

![](https://i.imgur.com/p1zU5rt.png)

![](https://i.imgur.com/k17T9ow.png)

On purchases that have transactions, there is a "Transactions History" button inside of POS. When this button is selected, a modal will open showing a transaction history table that is similar to the transaction history table on the web. Next to "Cash" and "Manual Payments", there is a "Void" button/link. The void button/link appears only  on "Cash" and "Manual Payment" transactions, on transactions that occurred today, on transactions that occurred at the  same facility the user is currently authenticated, and for transactions that hasn’t been voided already. When the void link is selected the void transaction modal will be shown.

![](https://i.imgur.com/Jt2lNss.png)

When the void link on the POS transaction history modal is selected, the user will see this void transaction modal. A manager (permission based) reviews the transaction details, will enter their pin, and will select "Submit" button, to void the transaction. After submitting, the screen gos to the "create payment" screen with the balance due reflecting the recently voided transactions.

### API Calls

**GET** ```go_api/grow/report/transactions``` - gets all transactions which were made during the purchase;
**POST** ```go_api/retail/payments/${transactionId}/void``` - void a particular transaction;

### Validation

- The void functionality is available only for the transaction, which:
  - Has "Cash" or "Manual Payment" payment method;
  - Transactions older than one day can't be voided;
  - Occur at the same facility the customer is currently authenticated;
  - Hasn't been voided already;
  - If there is no returned item in the purchase;
  - Facility ID returned from `processRequest` transaction should be the same as the facility ID on the original order payment transaction record
  - If there is at least one refund transaction in the order, voiding transactions in this order becomes impossible.