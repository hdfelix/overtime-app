# Overtime App

Key requirements: Company needs documentation that salaried employees did or did not get overtime each week

## Models
Post: date (date) rationale (text)
User: (Devise gem)
AdminUser (STI)

## Features
* Approval workflow
* SMS - Send a link to approval or overtime input
* Admin dashboard for managers to review, accept overtime entries, view logs, etc.
* Email summary to to managers for approval
* Important: keep record (document) if an employee did not log overtime hours
* Use Bootstrap for simple layout formatting