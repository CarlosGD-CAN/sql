# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

ANSWER:
Logical Model for a Small Bookstore
Entities and Relationships

1. Book
Columns:
BookID (PK)
Title
Author
ISBN
Price
StockQuantity
Genre

2. Customer
Columns:
CustomerID (PK)
FirstName
LastName
Email
PhoneNumber

3. Order
Columns:
OrderID (PK)
CustomerID (FK)
OrderDate
TotalAmount

4. Sales
Columns:
SaleID (PK)
OrderID (FK)
BookID (FK)
Quantity
SalePrice

5. Employee
Columns:
EmployeeID (PK)
FirstName
LastName
Position
HireDate

6. Date
Columns:
DateID (PK)
Date
Month
Year
DayOfWeek

***Relationships:
Customer (1) to Order (M)
Order (1) to Sales (M)
Book (1) to Sales (M)
Employee (1) to Order (M) (if employees process orders)

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

ANSWER:
Employee Shifts
To add employee shifts, we can create a new entity:

Employee_Shift
Columns:
ShiftID (PK)
EmployeeID (FK)
ShiftDate
ShiftTime (e.g., Morning, Evening)

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Your answer...
```

ANSWER
CUSTOMER_ADDRESS Table Architectures

1. Type 1 Architecture (Overwrite):
Table Structure:
CustomerID (PK, FK)
AddressLine1
AddressLine2
City
State
ZipCode
This approach simply overwrites the existing address.

2.Type 2 Architecture (Retain Changes):
Table Structure:
AddressID (PK)
CustomerID (FK)
AddressLine1
AddressLine2
City
State
ZipCode
EffectiveDate
ExpirationDate
This maintains a history of addresses, allowing tracking of changes over time.

Bonus: Privacy Implications
Yes, there are privacy implications related to storing customer addresses. Retaining historical address data (Type 2) could potentially expose sensitive information if not managed properly. Data breaches could lead to unauthorized access to personal information, requiring robust security measures and compliance with data protection regulations (e.g., GDPR).

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Your answer...
```

ANSWER:

Comparison with AdventureWorks Schema

Differences:
1. Complexity: The AdventureWorks schema is significantly more complex, with many more entities like products, categories, suppliers, and detailed order processes. My ERD is simpler, focusing only on the bookstore's primary functions.

2. Normalizations: AdventureWorks employs a higher degree of normalization with many related tables (e.g., for sales territories, promotions). My model keeps it straightforward, which may simplify operations but could lead to data redundancy.

Changes: While my model meets the bookstore's needs, incorporating some elements of normalization from AdventureWorks could improve data integrity and reporting capabilities, especially for future scalability.


# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `June 1, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
