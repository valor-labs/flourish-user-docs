# Marijuana Customer Status Validation

This article will walk through the identity verification process for Customers within the Flourish system, to check, whether the Customer is eligible to purchase Marijuana containing products or not.

## Glossary

Here are some quick definitions of relevant terms:

**Customer** represents an individual that intends to make a purchase of any kind of products through Flourish system.

The main difference between medical cannabis and recreational cannabis is the Cannabidiol (CBD) and Tetrahydrocannabinol (THC) content, the active ingredients in marijuana:

**Recreational** marijuana has more THC content than the medicinal CBD, THC is responsible for making users feel high.

**Medical** marijuana with a high content of CBD, proven to have anti-inflammatory, anti-anxiety, anti-oxidant, anti-carcinogenic and antipsychotic properties.

**Underage** The legal age for using recreational marijuana is 21, while the legal age for medical marijuana is 18. In Flourish, customer is considered underage if he is younger than 21. For Customers under the age of 18 with a qualifying medical condition, obtaining a medical card requires two physician recommendations and a parent/guardian approval.

**MMID** A medical cannabis card (MMID) or medical marijuana (MMJ) card is a state issued identification card that enables a patient with a doctor's recommendation to obtain, possess, or cultivate cannabis for medicinal use despite marijuana's lack of the normal Food and Drug Administration testing for safety and efficacy.

## Customer Eligibility

Flourish has two 2 customer verification statuses - **Verified** / **Not verified**. *Verified* can be of 2 types - **Medical** & **Recreational.** *Not Verified* can be of 3 types - **Recreational,** **Underage,** **Not Verified**.

**Note:** It is important where the customer's Medical Card is issued, as it depends on whether he/she can buy cannabis goods or not. This can be seen in the "Medical Card is issued in the facility's state" column in the table below. To get a clear understanding of state regulations

Customer status can be viewed or changed inside the POS application in his or her profile, as seen on the image

![Customer Profile Status](https://i.imgur.com/GBWXKYJ.png)

### Source code reference

**POS:**

All customer verification is checked using the `getCustomerVerification` function in `auth.service.ts`

**WEB:**

All customer verification is checked using `getCustomerVerification` function inside `customer-auth.service` service

### Database level reference

Customer status is stored in the [**Company Level** database](../Database/General&#32;Information.md), inside `customer` table there is the `is_verified` column.

## POS Authentication Token Life Cycle

Authentication is a part of customer validation. In this part of an article, we will delve into the differences between WEB and POS modules authentication pipeline and, token lifecycle.

**Log in:**

POS module authentication system has two tokens - `terminal_token` and `token`. When customer logs in using email+password combination, we set both `terminal_token` and `token` to the same value, and after that, if PIN login is used, we leave the `terminal_token` alone but replace the `token` with the new one for the PIN'ned-in user.

**Log out:**

When customer decides to log out, the auth logout function checks both `terminal_token` and `token` tokens, and if they are

- *Different:* customer is then redirected to PIN-request page and `token` becomes equal to the `terminal_token`;

- *Same:* then both `terminal_token` and `token` are deleted and customer log all the way out to the email login screen.