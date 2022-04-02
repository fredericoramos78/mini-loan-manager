# mini-loan-manager
This project is intended for study purposes only. I'm trying a diff approach to learning Haskell where I have a project on a well-known language/technology first - in this case Scala/Akka - and then try to port it into Haskell. If this is successful as a learning strategy, I willplan future iterations on other languages like Earlang (yes, I'm a big fan of the actor model ;-) )

The `master` branch will be kept lean: just this README file and some tracking/updates on where I'm at on this study journey. Each language will have it's own branch, which right now includes:
 * `scala2-akka` 

As I progress, more will come.


## Why a loan manager?

When I started this project I was (maybe still am?) working on a banking platform company and more specifically on a team that handles loand applications & life cycle. And since this project is intended as a study workbench for the technology used in such company, sounds natural to me to play around the business case I'm inserted at. Of course this is a absurdly simplified version of all that!

## What this loan manager does?

This is the functional scope of this project. 

We'll have a HTTP API to allow interfacing with the business components. This API will expose the following operations:

 * Apply for a new loan
 * Get the summary of a user's balance / loans
 * Get the details of a user's loan
 * Request withdraws from a loan
 * Push payment receipts

For simplicity sake:
 1. interest will be calculated on the fly each time we get details of a loan OR a payment is made
 2. payment amount is first allocated towards interest and whatever is left is put towards the principal
 3. Loan application can fail in two scenarios:
     a. if the user has unpaid loans that sum > 50K
     b. the amount requested is over 100K (configurable) 

Other importante notes:
 * Loans here are not a line of credit; Even after paid any withdrawn amount won't be available back.
 * There's no application tracking. If the application was approved it will become a Loan; if not, nothing is stored in the db.

## Entity / Models

### Users 
 * email 
 * createdAt
 * loans []
 * openBalance 
 * loanSoFar
 * paidSoFar

### Loans
 * id
 * createdAt
 * fullyPaidAt
 * totalAmount
 * availableAmount
 * openBalance
 * lastPaymentAt
 -- used in case the last payment was not enough to pay down all interest
 * openInterestAmount
 * interestRate



Thanks!


