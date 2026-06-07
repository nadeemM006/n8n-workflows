# Customer Feedback Logger Workflow

## Overview

This n8n workflow collects customer feedback through a web form, determines whether a customer should receive a discount based on their feedback, and stores all collected information in Google Sheets.

The workflow automates the process of gathering feedback, evaluating customer sentiment, and maintaining a centralized feedback database.

---

## Workflow Purpose

The main objectives of this workflow are:

* Collect customer information and feedback.
* Identify customers who provide positive feedback.
* Mark eligible customers for discounts.
* Store all customer records in Google Sheets for future analysis.

---

## Workflow Architecture

### Nodes Used

1. **Form Trigger**
2. **IF Node**
3. **Set Node (Discount_Yes)**
4. **Set Node (Discount_No)**
5. **Google Sheets Node**

---

## Workflow Steps

### Step 1: Customer Submits Form

A customer fills out a feedback form containing:

* Name
* Email Address
* Age
* Feedback

Available feedback options:

* Positive
* Neutral
* Negative

---

### Step 2: Feedback Evaluation

The IF node checks the submitted feedback.

**Condition:**

```text
Feedback = Positive
```

---

### Step 3: Assign Discount Status

#### If Feedback is Positive

The workflow assigns:

```text
Give_Discount = Yes
```

#### If Feedback is Neutral or Negative

The workflow assigns:

```text
Give_Discount = No
```

---

### Step 4: Store Data in Google Sheets

The workflow appends a new row to Google Sheets containing:

| Field         | Description          |
| ------------- | -------------------- |
| Name          | Customer Name        |
| Email_Id      | Customer Email       |
| Age           | Customer Age         |
| Feedback      | Submitted Feedback   |
| Give_Discount | Discount Eligibility |

---

## Workflow Logic

```text
Form Submission
       │
       ▼
      IF
       │
 ┌─────┴─────┐
 │           │
 ▼           ▼
Positive   Others
 │           │
 ▼           ▼
Discount   Discount
   Yes        No
 │           │
 └─────┬─────┘
       ▼
 Google Sheets
```

---

## Benefits

* Automated customer feedback collection.
* No manual data entry required.
* Quick identification of satisfied customers.
* Easy integration with future marketing campaigns.
* Centralized storage using Google Sheets.

---

## Technologies Used

* n8n
* Google Forms (via n8n Form Trigger)
* Google Sheets
* Conditional Logic (IF Node)

---

## Future Enhancements

Possible improvements include:

* Sending discount coupons automatically via email.
* Generating customer satisfaction reports.
* Integrating with CRM systems.
* Sending notifications to the sales team.
* Adding sentiment analysis using AI.

---
