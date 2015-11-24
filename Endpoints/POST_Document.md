

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
The example below creates a minimal order in Counterpoint
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
In this example, an order with a single order line is created. The price ($200.00) was passed in with the line and will be honored. Credit payment information was taken, but no deposit/charge is made on the card (as the AMT was not provided), and the card will be tokenized (if store MAIN is a Secure Pay store) or encrypted (if store MAIN is a CPG store), and saved for use as a final payment (FINAL_PMT: "Y") when the order is released.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the document was successfully added to Counterpoint

#### Sample Response Body

```
{
  "Documents": [
    {
      "DOC_ID": 107437187047504,
      "reference": "Order",
      "Link": {
        "uri": "http://localhost:81/Document/107437187047504",
        "method": "get"
      },
      "PaymentResponses": []
    }
  ],
  "ErrorCode": "SUCCESS"
}
```
If any payments were applied at the time the order was added, you'd see information for those payments in the array of PaymentResponses in the result. For credit charges, that would include Auth codes.
