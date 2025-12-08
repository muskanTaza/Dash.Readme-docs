---
title: Payout Webhooks
deprecated: false
hidden: false
metadata:
  robots: index
---
## Payout status specific events

| Event                               | Description                                    | Default |
| ----------------------------------- | ---------------------------------------------- | ------- |
| `payout.requires_approval`          | Triggered when the status is requires_approval | Off     |
| `payout.requires_action`            | Triggered when the status is requires_action   | Off     |
| `payout.requires_funding`           | Triggered when the status is requires_funding  | On      |
| `payout.processing`                 | Triggered when the status is processing        | On      |
| `payout.succeeded`                  | Triggered when the status is succeeded         | On      |
| `payout.failed`                     | Triggered when the status is failed            | On      |
| `payout.cancelled`                  | Triggered when the payout is cancelled         | On      |
| `payout.proof_of_payment_generated` | Triggered when the proof of payment is updated | On      |

## Other Events

| Event                             | Description                                     | Default (On / Off) |
| --------------------------------- | ----------------------------------------------- | ------------------ |
| `payout.created`                  | Triggered when a payout is created              | Off                |
| `payout.mt103_generated`          | Triggered when MT103 is added to a payout       | Off                |
| `payout.mt199_generated`          | Triggered when MT199 is added to a payout       | Off                |
| `payout.firc_generated`           | Triggered when FIRC is added to a payout        | Off                |
| `payout.other_document_generated` | Triggered when any other document type is added | Off                |

## Sample Events

### payout.created

```
{
  "type": "payout.created",
  "id": "evt_ctbvv9o1l435sdu911tg",
  "object": "event",
  "created_at": "2024-12-10T08:45:27.349281559Z",
  "data": {
    "created_at": "2024-12-10T08:45:25.12005Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "bank_code": "INGBAU2SXXX",
            "branch_code": "INGBAU2SXXX"
          },
          "bank_name": "Central Bank",
          "country": "BR",
          "currency": "BRL",
          "account_type": "savings"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "55"
      },
      "name": "Roman",
      "email": "musk@gmail.com",
      "type": "individual",
      "tax_id": "123.456.789-87"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "BRL",
        "amount": 10000
      },
      "final": {
        "currency": "BRL",
        "amount": 10000
      },
      "id": "fx_ctbvv905ha8onnfg24s0",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "local",
    "status": "processing",
    "purpose": "PYR001",
    "id": "pot_ctbvv96hi567m07e7q40",
    "holding_currency": "INR",
    "currency": "BRL",
    "beneficiary": "bnf_cs8bf4m6rf9979b4isq0",
    "object": "payout",
    "balance_transaction": "btr_ctbvv9ehi567m07e7q80",
    "amount": 10000
  }
}
```

### payout.processing

```
{
  "type": "payout.processing",
  "id": "evt_ctbvv9o1l435sdu911t0",
  "object": "event",
  "created_at": "2024-12-10T08:45:27.305264108Z",
  "data": {
    "created_at": "2024-12-10T08:45:25.12005Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "bank_code": "INGBAU2SXXX",
            "branch_code": "INGBAU2SXXX"
          },
          "bank_name": "Central Bank",
          "country": "BR",
          "currency": "BRL",
          "account_type": "savings"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "55"
      },
      "name": "Test1",
      "email": "musk@gmail.com",
      "type": "individual",
      "tax_id": "123"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "BRL",
        "amount": 10000
      },
      "final": {
        "currency": "BRL",
        "amount": 10000
      },
      "id": "fx_ctbvv905ha8onnfg24s0",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "local",
    "status": "processing",
    "purpose": "PYR001",
    "id": "pot_ctbvv96hi567m07e7q40",
    "holding_currency": "INR",
    "currency": "BRL",
    "beneficiary": "bnf_cs8bf4m6rf9979b4isq0",
    "object": "payout",
    "balance_transaction": "btr_ctbvv9ehi567m07e7q80",
    "amount": 10000
  }
}
```

### payout.succeeded

```
{
  "type": "payout.succeeded",
  "id": "evt_ctc007o1l435sdu91250",
  "object": "event",
  "created_at": "2024-12-10T08:47:27.446050128Z",
  "data": {
    "tracking_details": {
      "tracking_number": "UETR20240311001",
      "tracking_type": "uetr"
    },
    "created_at": "2024-12-10T08:45:25.12005Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "bank_code": "INGBAU2SXXX",
            "branch_code": "INGBAU2SXXX"
          },
          "bank_name": "Central Bank",
          "country": "BR",
          "currency": "BRL",
          "account_type": "savings"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "55"
      },
      "name": "Test1",
      "email": "musk@gmail.com",
      "type": "individual",
      "tax_id": "123"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "BRL",
        "amount": 10000
      },
      "final": {
        "currency": "BRL",
        "amount": 10000
      },
      "id": "fx_ctbvv905ha8onnfg24s0",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "local",
    "status": "succeeded",
    "purpose": "PYR001",
    "id": "pot_ctbvv96hi567m07e7q40",
    "holding_currency": "INR",
    "currency": "BRL",
    "beneficiary": "bnf_cs8bf4m6rf9979b4isq0",
    "object": "payout",
    "balance_transaction": "btr_ctbvv9ehi567m07e7q80",
    "amount": 10000
  }
}        
```

### payout.requires_funding

```
{
  "type": "payout.requires_funding",
  "id": "evt_ctc02681l435sdu912pg",
  "object": "event",
  "created_at": "2024-12-10T08:51:37.346373409Z",
  "data": {
    "created_at": "2024-12-10T08:51:34.128328Z",
    "beneficiary_details": {
      "address": {
        "line1": "MG Road",
        "line2": "Adj ST Mary School",
        "postal_code": "10038",
        "city": "Delhi",
        "state": "Delhi",
        "country": "IN"
      },
      "destination_details": {
        "bank": {
          "bank_codes": {
            "ifsc_code": "HDFR8897CA",
            "swift_code": "INGBAU2SXXX"
          },
          "account_number": "1276472008763",
          "bank_name": "hdfc",
          "country": "IN",
          "currency": "INR",
          "purpose_code": "Test",
          "firc_required": true
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "91"
      },
      "name": "test",
      "email": "test@example.com",
      "type": "individual"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "INR",
        "amount": 1000000000
      },
      "final": {
        "currency": "INR",
        "amount": 1000000000
      },
      "id": "fx_ctc025g5ha8onnfg2510",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "local",
    "status": "requires_funding",
    "purpose": "PYR001",
    "id": "pot_ctc025mhi567m07e7r50",
    "holding_currency": "GBP",
    "currency": "INR",
    "beneficiary": "bnf_crv7k31h1l071n2fkbjg",
    "object": "payout",
    "amount": 1000000000
  }
}
```

### payout.requires_approval

```
{
  "type": "payout.requires_approval",
  "id": "evt_ctc0bit3iqh25ihhl1bg",
  "object": "event",
  "created_at": "2024-12-10T09:11:39.659702396Z",
  "data": {
    "created_at": "2024-12-10T09:11:37.418151Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "INGBAU2SXXX"
          },
          "account_number": "1234675423679987",
          "bank_name": "Central Bank",
          "country": "US",
          "currency": "SGD"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1"
      },
      "name": "aaaaa",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "SGD",
        "amount": 1000
      },
      "final": {
        "currency": "SGD",
        "amount": 1000
      },
      "id": "fx_ctc0bidpk5p8ci8rf57g",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "swift",
    "status": "requires_approval",
    "charge_type": "ours",
    "purpose": "PYR001",
    "id": "pot_ctc0bidf9sjsk2si3qpg",
    "holding_currency": "AUD",
    "currency": "SGD",
    "beneficiary": "bnf_crqfjhsbvd1o6tv0gku0",
    "object": "payout",
    "statement_descriptor": "Muskan",
    "on_behalf_of": "ent_csorc2c1kl1roj58r2hg",
    "amount": 1000
  }
}
```

### payout.failed

```
{
  "type": "payout.failed",
  "id": "evt_ctc145tvggacf0fci0a0",
  "object": "event",
  "created_at": "2024-12-10T10:04:07.654463614Z",
  "data": {
    "tracking_details": {
      "tracking_number": "67543890",
      "tracking_type": "utr"
    },
    "created_at": "2024-12-10T09:15:59.251488Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "INGBAU2SXXX"
          },
          "account_number": "1234562787358912",
          "bank_name": "Central Bank",
          "country": "US",
          "currency": "SGD"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1"
      },
      "name": "Roman",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "SGD",
        "amount": 100
      },
      "final": {
        "currency": "SGD",
        "amount": 100
      },
      "id": "fx_ctc0djtpk5p8ci8rf700",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "swift",
    "status_description": "PO1008 entity_approval_rejected",
    "status": "failed",
    "charge_type": "ours",
    "purpose": "PYR003",
    "id": "pot_ctc0djtf9sjsk2si3uf0",
    "holding_currency": "AUD",
    "currency": "SGD",
    "beneficiary": "bnf_crqfjhsbvd1o6tv0gku0",
    "object": "payout",
    "statement_descriptor": "Muskan",
    "on_behalf_of": "ent_ct2ovl9f5lhf6huap5cg",
    "amount": 100
  }
}
```

### payout.cancelled

```
{
  "type": "payout.cancelled",
  "id": "evt_ctgjf5ncu42kd3rmm3r0",
  "object": "event",
  "created_at": "2024-12-17T08:34:30.98072183Z",
  "data": {
    "created_at": "2024-12-17T08:33:48.059177Z",
    "beneficiary_details": {
      "address": {
        "line1": "MG Road",
        "line2": "Adj ST Mary School",
        "postal_code": "10038",
        "city": "Delhi",
        "state": "Delhi",
        "country": "IN"
      },
      "destination_details": {
        "bank": {
          "bank_codes": {
            "aba_code": "123478789",
            "swift_code": "INGBAU2SXXX"
          },
          "account_number": "1234456775333",
          "bank_name": "CityBank",
          "country": "US",
          "currency": "USD"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1",
        "number": "12312312312"
      },
      "name": "Test 7",
      "email": "test@example.com",
      "type": "individual",
      "tax_id": "1234123"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "USD",
        "amount": 100000
      },
      "final": {
        "currency": "USD",
        "amount": 100000
      },
      "id": "fx_ctgjeqtpk5p8ci903jcg",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "local",
    "status": "cancelled",
    "purpose": "PYR001",
    "id": "pot_ctgjeqvg9n1vh5nsb3ng",
    "holding_currency": "AUD",
    "currency": "USD",
    "beneficiary": "bnf_crv5o44fd64iheof2r70",
    "object": "payout",
    "statement_descriptor": "erf",
    "on_behalf_of": "ent_ctdv4tt97ubkibq2km2g",
    "amount": 100000
  }
}
```

### payout.requires_action

```
{
  "type": "payout.requires_action",
  "id": "evt_ctgll361mt84a8u1dvgg",
  "object": "event",
  "created_at": "2024-12-17T11:03:41.089728899Z",
  "data": {
    "tracking_details": {
      "tracking_number": "566975432",
      "tracking_type": "utr"
    },
    "created_at": "2024-12-17T08:42:14.107051Z",
    "beneficiary_details": {
      "address": {
        "line1": "MG Road",
        "line2": "Adj ST Mary School",
        "postal_code": "10038",
        "city": "Delhi",
        "state": "Delhi",
        "country": "IN"
      },
      "destination_details": {
        "bank": {
          "bank_codes": {
            "aba_code": "123478789",
            "swift_code": "INGBAU2SXXX"
          },
          "account_number": "Test7",
          "bank_name": "CityBank",
          "country": "US",
          "currency": "USD"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1",
        "number": "12312312312"
      },
      "name": "Roman",
      "email": "test@example.com",
      "type": "individual",
      "tax_id": "911-92-3333"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "USD",
        "amount": 1000
      },
      "final": {
        "currency": "USD",
        "amount": 1000
      },
      "id": "fx_ctgjipdpk5p8ci903nt0",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "local",
    "status": "requires_action",
    "purpose": "PYR003",
    "id": "pot_ctgjipfg9n1vh5nsbcug",
    "holding_currency": "USD",
    "currency": "USD",
    "beneficiary": "bnf_crv5o44fd64iheof2r70",
    "object": "payout",
    "statement_descriptor": "Muskan",
    "balance_transaction": "btr_ctgjipng9n1vh5nsbd20",
    "on_behalf_of": "ent_ctc0kk9sgkgeelcl87i0",
    "amount": 1000
  }
}
```

### payout.proof_of_payment_generated

```
{
  "type": "payout.proof_of_payment_generated",
  "id": "evt_cv4m2bk2ojhhksnte5r0",
  "object": "event",
  "created_at": "2025-03-06T08:47:42.820264412Z",
  "data": {
    "tracking_details": {
      "tracking_number": "",
      "tracking_type": ""
    },
    "created_at": "2025-03-06T08:46:31.535372Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "testswift"
          },
          "account_number": "123456789",
          "bank_name": "test bank",
          "country": "SG",
          "currency": "SGD"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "65"
      },
      "name": "John Doe",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "SGD",
        "amount": 10000
      },
      "final": {
        "currency": "SGD",
        "amount": 10000
      },
      "id": "fx_cv4m1pr6tce7o3q54es0",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "type": "swift",
    "status": "succeeded",
    "charge_type": "ours",
    "purpose": "PYR001",
    "id": "pot_cv4m1po9mkr4ca8pbu5g",
    "holding_currency": "USD",
    "currency": "SGD",
    "beneficiary": "bnf_cv4m1po9mkr4ca8pbu60",
    "object": "payout",
    "balance_transaction": "btr_cv4m1po9mkr4ca8pbu9g",
    "mt103": "{1:F01SCBLSG22AXXX0740170000}{2:I103CHASSGSGXXXXN}{3:{103:MEP}{113:NORQ}{108:SE1\n0502503040286}{111:001}{121:0c795041-3248-4dac-9c60-f0e916452bc5}}{4:\n:20:SE10502503040286\n:23B:CRED\n:32A:250304SGD4300,00\n:33B:SGD4300,00\n:50K:/7540731\nNreach Online Services Inc\n8th The Green Ste A Delaware 19901\nUNITED STATES\n:52D:/0105553026\nTAZAPAY PTE. LTD.\n7 TEMASEK BOULEVARD,20-06 SUNTEC TO\nWER ONE,SINGAPORE,ZIP 038987\n/SINGAPORE\n:57A:CHASSGSGXXX\n:59:/8830045245\nQWIKCILVER SOLUTIONS PTE. LTD.\n:70:Xoxo Day Payout on 03rd March 2025\n:71A:OUR\n-}",
    "amount": 10000
  }
}
```

### payout.mt103_generated

```
{
  "type": "payout.mt103_generated",
  "id": "evt_d086g9ri9cotns8qase0",
  "object": "event",
  "created_at": "2025-04-29T05:48:23.846543614Z",
  "data": {
    "local": {},
    "tracking_details": {
      "tracking_number": "",
      "tracking_type": "utr"
    },
    "created_at": "2025-04-08T11:31:04.54606Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "57567678"
          },
          "account_number": "678686",
          "bank_name": "citi",
          "country": "US",
          "currency": "AUD"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1"
      },
      "name": "test",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "AUD",
        "amount": 78700
      },
      "final": {
        "currency": "AUD",
        "amount": 78700
      },
      "id": "fx_cvqghu3q4fulre35bvrg",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "id": "pot_cvqghu1dgfht6k9a6n30",
    "mt103": "{1:F01SCBLSG22AXXX0740170000}{2:I103CHASSGSGXXXXN}{3:{103:MEP}{113:NORQ}{108:SE1\n0502503040286}{111:001}{121:0c795041-3248-4dac-9c60-f0e916452bc5}}{4:\n:20:SE10502503040286\n:23B:CRED\n:32A:250304SGD4300,00\n:33B:SGD4300,00\n:50K:/7540731\nNreach Online Services Inc\n8th The Green Ste A Delaware 19901\nUNITED STATES\n:52D:/0105553026\nTAZAPAY PTE. LTD.\n7 TEMASEK BOULEVARD,20-06 SUNTEC TO\nWER ONE,SINGAPORE,ZIP 038987\n/SINGAPORE\n:57A:CHASSGSGXXX\n:59:/8830045245\nQWIKCILVER SOLUTIONS PTE. LTD.\n:70:Xoxo Day Payout on 03rd March 2025\n:71A:OUR\n-}",
    "status": "succeeded",
    "charge_type": "ours",
    "purpose": "PYR001",
    "holding_currency": "INR",
    "currency": "AUD",
    "beneficiary": "bnf_cvqghu1dgfht6k9a6n3g",
    "balance_transaction": "btr_cvqghu1dgfht6k9a6opg",
    "type": "swift",
    "confirmation_documents": [
      {
        "key": "mt103",
        "type": "string",
        "value": "test"
      }
    ],
    "amount": 78700
  }
}
```

### payout.mt199_generated

```
{
  "type": "payout.mt199_generated",
  "id": "evt_d086g9ri9cotns8qase0",
  "object": "event",
  "created_at": "2025-04-29T05:48:23.846543614Z",
  "data": {
    "local": {},
    "tracking_details": {
      "tracking_number": "",
      "tracking_type": "utr"
    },
    "created_at": "2025-04-08T11:31:04.54606Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "57567678"
          },
          "account_number": "678686",
          "bank_name": "citi",
          "country": "US",
          "currency": "AUD"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1"
      },
      "name": "test",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "AUD",
        "amount": 78700
      },
      "final": {
        "currency": "AUD",
        "amount": 78700
      },
      "id": "fx_cvqghu3q4fulre35bvrg",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "id": "pot_cvqghu1dgfht6k9a6n30",
    "mt103": "{1:F01SCBLSG22AXXX0740170000}{2:I103CHASSGSGXXXXN}{3:{103:MEP}{113:NORQ}{108:SE1\n0502503040286}{111:001}{121:0c795041-3248-4dac-9c60-f0e916452bc5}}{4:\n:20:SE10502503040286\n:23B:CRED\n:32A:250304SGD4300,00\n:33B:SGD4300,00\n:50K:/7540731\nNreach Online Services Inc\n8th The Green Ste A Delaware 19901\nUNITED STATES\n:52D:/0105553026\nTAZAPAY PTE. LTD.\n7 TEMASEK BOULEVARD,20-06 SUNTEC TO\nWER ONE,SINGAPORE,ZIP 038987\n/SINGAPORE\n:57A:CHASSGSGXXX\n:59:/8830045245\nQWIKCILVER SOLUTIONS PTE. LTD.\n:70:Xoxo Day Payout on 03rd March 2025\n:71A:OUR\n-}",
    "status": "succeeded",
    "charge_type": "ours",
    "purpose": "PYR001",
    "holding_currency": "INR",
    "currency": "AUD",
    "beneficiary": "bnf_cvqghu1dgfht6k9a6n3g",
    "balance_transaction": "btr_cvqghu1dgfht6k9a6opg",
    "type": "swift",
    "confirmation_documents": [
      {
        "key": "mt103",
        "type": "string",
        "value": "test"
      },
      {
          "key": "mt199",
          "type": "string",
          "value": "test"
        }
    ],
    "amount": 78700
  }
}
```

### payout.firc_generated

```
{
  "type": "payout.mt199_generated",
  "id": "evt_d086g9ri9cotns8qase0",
  "object": "event",
  "created_at": "2025-04-29T05:48:23.846543614Z",
  "data": {
    "local": {},
    "tracking_details": {
      "tracking_number": "",
      "tracking_type": "utr"
    },
    "created_at": "2025-04-08T11:31:04.54606Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "57567678"
          },
          "account_number": "678686",
          "bank_name": "HDFC",
          "country": "IN",
          "currency": "INR"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1"
      },
      "name": "test",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "INR",
        "amount": 78700
      },
      "final": {
        "currency": "INR",
        "amount": 78700
      },
      "id": "fx_cvqghu3q4fulre35bvrg",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "id": "pot_cvqghu1dgfht6k9a6n30",
    "mt103": "",
    "status": "succeeded",
    "charge_type": "",
    "purpose": "PYR001",
    "holding_currency": "INR",
    "currency": "INR",
    "beneficiary": "bnf_cvqghu1dgfht6k9a6n3g",
    "balance_transaction": "btr_cvqghu1dgfht6k9a6opg",
    "type": "local",
    "confirmation_documents": [
      {
        "key": "firc",
        "type": "url",
        "value": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc96573_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=f9df595274faec769a77a7712a87954db65003702ea055782404fdd75a3fdcd1"
      }
    ],
    "amount": 78700
  }
}
```

### payout.other_document_generated

```
{
  "type": "payout.other_document_generated",
  "id": "evt_d086g9ri9cotns8qase0",
  "object": "event",
  "created_at": "2025-04-29T05:48:23.846543614Z",
  "data": {
    "local": {},
    "tracking_details": {
      "tracking_number": "",
      "tracking_type": "utr"
    },
    "created_at": "2025-04-08T11:31:04.54606Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "57567678"
          },
          "account_number": "678686",
          "bank_name": "HDFC",
          "country": "IN",
          "currency": "INR"
        },
        "type": "bank"
      },
      "phone": {
        "calling_code": "1"
      },
      "name": "test",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "INR",
        "amount": 78700
      },
      "final": {
        "currency": "INR",
        "amount": 78700
      },
      "id": "fx_cvqghu3q4fulre35bvrg",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "id": "pot_cvqghu1dgfht6k9a6n30",
    "mt103": "",
    "status": "succeeded",
    "charge_type": "",
    "purpose": "PYR001",
    "holding_currency": "INR",
    "currency": "INR",
    "beneficiary": "bnf_cvqghu1dgfht6k9a6n3g",
    "balance_transaction": "btr_cvqghu1dgfht6k9a6opg",
    "type": "local",
    "confirmation_documents": [
      {
        "key": "abc", // abc is Other document type
        "type": "url",
        "value": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc96573_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=f9df595274faec769a77a7712a87954db65003702ea055782404fdd75a3fdcd1"
      }
    ],
    "amount": 78700
  }
}
```

<br />

### payout.compliance_hold 

```json
{
  "type": "payout.compliance_hold",
  "id": "evt_d3n3iavvima100lp71kg",
  "object": "event",
  "created_at": "2025-10-14T11:51:07.422226364Z",
  "data": {
    "local": {},
    "created_at": "2025-10-14T11:50:56.075199Z",
    "beneficiary_details": {
      "destination_details": {
        "bank": {
          "bank_codes": {
            "swift_code": "sw32432"
          },
          "account_number": "3423435427899",
          "bank_name": "Central Bank",
          "country": "CN",
          "currency": "CNY"
        },
        "type": "bank"
      },
      "name": "Allen",
      "type": "business"
    },
    "payout_fx_transaction": {
      "initial": {
        "currency": "CNY",
        "amount": 10000
      },
      "final": {
        "currency": "CNY",
        "amount": 10000
      },
      "id": "fx_d3n3i7tfs5v4tkcn6ktg",
      "object": "fx_transaction",
      "exchange_rate": 1
    },
    "purpose": "PYR004",
    "status": "compliance_hold",
    "charge_type": "ours",
    "id": "pot_d3n3i7t2amni271p7qd0",
    "holding_currency": "EUR",
    "currency": "CNY",
    "beneficiary": "bnf_d3n3hrl2amni271p7q8g",
    "transaction_description": "asd",
    "balance_transaction": "btr_d3n3i852amni271p7qh0",
    "type": "swift",
    "holding_fx_quote": "fx_d3n3i7tfs5v4tkcn6ku0",
    "destination_fx_quote": "fx_d3n3i7tfs5v4tkcn6ktg",
    "documents": [
      {
        "id": "doc_d3n3i852amni271p7qdg",
        "type": "invoice",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-payout-document-qa/pot_d3n3i7t2amni271p7qd0"
      }
    ],
    "amount": 10000
  }
}
```
