# NCR Counterpoint API v2.3 Release Notes
Version 2.3 of the NCR Counterpoint API addresses several issues, including:

### Issue CP-10751 REST API: Adding a payment using the CPAPI generates out-of-balance G/L distributions

When adding documents with payments and posting the ticket, Counterpoint reports an out-of-balance distributions error.

Payments can be posted in two ways:

1. /Document - For inserting a new document with a payment
2. /Document/<DOC_ID>/Payments - For adding a payment to an existing document (i.e., to be used as a 2nd call after inserting a document with no payment using the prior call)

Posting a ticket that was inserted either way results in out-of-balance distributions. In this version, we have corrected this issue.
