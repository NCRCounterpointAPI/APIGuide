@@ -0,0 +1,59 @@
# NCR Counterpoint API v2.3 Release Notes
Version 2.3 of the NCR Counterpoint API addresses several issues, including:

### Issue CP-10751 REST API: Adding a payment using the CPAPI generates out-of-balance G/L distributions

When adding documents with payments and posting the ticket, Counterpoint reports an out-of-balance distributions error.

Payments can be posted in two ways:

1. /Document - A single call for inserting a document with a payment
2. /Document/<DOC_ID>/Payments - For adding a payment to an existing document (i.e. to be used as a 2nd call after inserting a document with no payment using option #1)

When posting a document/ticket that was inserted either way results in an out of balanced distributions.
In this version we have fixed the payment application so that the payment is applied to the corresponding document avoiding any out of balance distribution.
