

# POST /Document

#### Description
Adds a completed document/ticket to the database. This is the call that is used to create a sale, order, layaway, etc. document in Counterpoint. It has a large amount of data that can be included, but most data can be ommitted and left with default values. Any credit payments that are submitted will be processed if necessary based on the processor settings for the STR_ID provided. Note that only stores using Secure Pay can process credit payments. Attempts to process credit payments for a CPG store will result in an error. However, it is possible to submit credit payment data for a final payment against a CPG store. In this case, the credit payment will be encrypted per Counterpoint standards and saved. That payment will be charged when the order is released in Counterpoint.

Also note that currently, the API server has not gone through PA-DSS validation, so credit payments should not yet be used in production systems. Credit processing functionality may be disabled in the final release of the API server until PA-DSS certification is complete.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`POST https://localhost:81/Document`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

**Body**
The example below creates a minimal order in Counterpoint.

In this example, an order with a single order line is created. The price ($200.00) was passed in with the line and will be honored. Credit payment information was taken, but no deposit/charge is made on the card (as the AMT was not provided), and the card will be tokenized (if store MAIN is a Secure Pay store) or encrypted (if store MAIN is a CPG store), and saved for use as a final payment (FINAL_PMT: "Y") when the order is released.
```
{
  "PS_DOC_HDR": {
    "STR_ID": "MAIN",
    "STA_ID": "1",
    "DRW_ID": "1",
    "TKT_TYP": "T",
    "DOC_TYP": "O",
    "USR_ID": "MGR",
    "PS_DOC_NOTE": [
      {
        "NOTE_ID": "TEST",
        "NOTE": "This is a note!"
      }
    ],
    "PS_DOC_LIN": [
      {
        "LIN_TYP": "O",
        "ITEM_NO": "ADM-SCD",
        "PRC":"200",
        "USR_ENTD_PRC":"Y",
        "QTY_SOLD": "1.0"
      }
    ],
    "PS_DOC_PMT": [
      {
        "PAY_COD": "VISA",
        "FINAL_PMT": "Y",
        "PS_DOC_PMT_CR_CARD": {
          "CR_CARD_NO": "4111111111111111",
          "CR_CARD_NAM": "JOHN DOE",
          "AVS_ZIP_COD": "12345",
          "CR_CARD_EXP_DAT": "12/2018"
        }
      }
    ],
    "PS_DOC_TAX": [
    {
      "AUTH_COD": "MEMPHIS",
      "RUL_COD": "TAX",
      "TAX_DOC_PART": "O",
      "LIN_AMT": "200",
      "TXBL_LIN_AMT": "200",
      "TXBL_QTY": "1.00",
      "TAX_AMT": "4.00",
      "TOT_TXBL_AMT": "200"
    },
    {
      "AUTH_COD": "SHELBY",
      "RUL_COD": "TAX",
      "TAX_DOC_PART": "O",
      "LIN_AMT": "200",
      "TXBL_LIN_AMT": "200",
      "TXBL_QTY": "1.00",
      "TAX_AMT": "6.00",
      "TOT_TXBL_AMT": "200"
    },
    {
      "AUTH_COD": "TN",
      "RUL_COD": "TAX",
      "TAX_DOC_PART": "O",
      "LIN_AMT": "200",
      "TXBL_LIN_AMT": "200",
      "TXBL_QTY": "1.00",
      "TAX_AMT": "6.00",
      "TOT_TXBL_AMT": "200"
    }
    ]
  }
}
```

 The example below is a typical eCommerce order that could be created in Counterpoint via the /Document POST endpoint. This order contains:
 * "Bill to" and "Ship to" contacts
 * A document note
 * A profile code (in this case alpha profile code 1 is used to track the shipping method
 * A package tracking number
 * A Miscellaneous charge (in this case misc charge 1 is used for shipping/freight charges)
 * A PS_TAX record showing the overall tax on the order
 * A PS_DOC_TAX record showing the tax allocation to (in this case) a single authority and tax rule
 * Cash payment for the document total
 
Since the order is submitted as being paid in full by cash, it should be ready to be released in Counterpoint whenever the item is shipped.
 
 ```
 {
  "PS_DOC_HDR": {
    "STR_ID": "MAIN",
    "STA_ID": "1",
    "DRW_ID": "1",
    "TKT_TYP": "T",
    "DOC_TYP": "O",
    "USR_ID": "MGR",
    "TAX_COD": "1",
    "NORM_TAX_COD": "1",
    "BILL_TO_CONTACT": {
      "FST_NAM": "John",
      "LST_NAM": "Do",
      "ADRS_1": "100 Main St",
      "CITY": "Memphis",
      "ZIP_COD": "38119",
      "STATE": "TN",
      "PHONE_1": "(901) 555-2222",
      "NAM_TYP": "P"
    },
    "SHIP_TO_CONTACT": {
      "FST_NAM": "John",
      "LST_NAM": "Do",
      "ADRS_1": "100 Main St",
      "CITY": "Memphis",
      "ZIP_COD": "38119",
      "STATE": "TN",
      "PHONE_1": "(901) 555-2222",
      "NAM_TYP": "P"
    },
    "PS_DOC_NOTE": [
      {
        "NOTE_ID": "NOTE1",
        "NOTE": "eCommerce order 54"
      }
    ],
    "PS_DOC_HDR_PROF": {
      "PROF_ALPHA_1": "USPS"
    },
    "PS_DOC_LIN": [
      {
        "LIN_TYP": "O",
        "ITEM_NO": "ADM-SCD",
        "PRC": "119.95",
        "USR_ENTD_PRC": "Y",
        "QTY_SOLD": "1"
      }
    ],
    "PS_DOC_HDR_MISC_CHRG": [
      {
        "TOT_TYP": "O",
        "MISC_CHRG_NO": "1",
        "MISC_TYP": "A",
        "MISC_AMT": "5.99"
      }
    ],
    "PS_DOC_PKG_TRK_NO": [
      {
        "PKG_TRK_NO": "23423423"
      }
    ],
    "PS_DOC_PMT": [
      {
        "AMT": "137.93",
        "PAY_COD": "Cash",
        "FINAL_PMT": "N"
      }
    ],
    "PS_DOC_TAX": [
      {
        "AUTH_COD": "MEMPHIS",
        "RUL_COD": "TAX",
        "TAX_DOC_PART": "O",
        "TAX_AMT": "11.99",
        "TOT_TXBL_AMT": "119.95"
      }
    ]
  },
  "PS_TAX": {
    "ORD_NORM_TAX_AMT": "11.99",
    "ORD_TAX_AMT": "11.99"
  }
}
 ```
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the document was successfully added to Counterpoint

#### Sample Response Body

If any payments were applied at the time the order was added, you'd see information for those payments in the array of PaymentResponses in the result. For credit charges, that would include Auth codes.

The response below is for the "eCommerce" order submitted above. Since the order had a cash payment included, 2 documents were created in Counterpoint:
* The first document ("Ticket" reference) contains the cash payment for the line for accounting purposes
* The second document ("Order" reference) is for order tracking and is linked to the first document. Since this order has been paid in full, the order document can be released when the item ships with no further payment required. 
```
{
{
  "Documents": [
    {
      "DOC_ID": 107437162115401,
      "reference": "Ticket",
      "Link": {
        "uri": "http://localhost:91/Document/107437162115401",
        "method": "get"
      },
      "PaymentResponses": [
        {
          "PMT_SEQ_NO": 1,
          "Response": "ACCEPTED"
        }
      ]
    },
    {
      "DOC_ID": 107437162167698,
      "reference": "Order",
      "Link": {
        "uri": "http://localhost:91/Document/107437162167698",
        "method": "get"
      },
      "PaymentResponses": []
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

