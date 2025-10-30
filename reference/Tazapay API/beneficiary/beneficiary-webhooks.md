---
title: Beneficiary Webhooks
excerpt: >-
  These are currently relevant for wallet beneficiaries (i.e. where
  `destination_details.type` is 'wallet')
deprecated: false
hidden: false
metadata:
  robots: index
---
**Beneficiary verification_status specific events**

| Event                       | Description                                                          | Default |
| :-------------------------- | :------------------------------------------------------------------- | :------ |
| beneficiary.processing      | Triggered when verification_status of beneficiary is processing      | off     |
| beneficiary.requires_action | Triggered when verification_status of beneficiary is requires_action | off     |
| beneficiary.succeeded       | Triggered when verification_status of beneficiary is succeeded       | off     |
| beneficiary.failed          | Triggered when verification_status of beneficiary is failed          | off     |

<br />

**Sample Events**

**beneficiary.processing**

```json
{
  "type": "beneficiary.processing",
  "id": "evt_d40u3boduff039n5h1t0",
  "object": "event",
  "created_at": "2025-10-29T09:43:11.83145611Z",
  "data": {
    "created_at": "2025-10-29T09:43:09.471921Z",
    "party_classification": "self",
    "registration_number": "12345",
    "name": "vibhui",
    "type": "business",
    "destination": "pwa_d40u3b9rcvj50sse4oe0",
    "id": "bnf_d40u3bbgrdjvil4n3q7g",
    "object": "beneficiary",
    "verification_status": "processing",
    "address": {
      "city": "bnds",
      "country": "DZ",
      "line1": "C-222",
      "line2": "123",
      "postal_code": "21334",
      "state": "fssd"
    },
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "currency": "USDC",
        "deposit_address": "ox2323",
        "hosted": "yes",
        "type": "ethereum",
        "vasp_name": "testing ",
        "vasp_website": "https://dashboard-brown.tazapay.com/beneficiary/view"
      }
    },
    "phone": {},
    "metadata": {},
    "documents": [
      {
        "type": "screenshot",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-beneficiary-document-qa/bnf_d40u3bbgrdjvil4n3q7g/1761730927028440823_deemed_university_AIQ.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Checksum-Mode=ENABLED&X-Amz-Credential=ASIAQKC7OY4NR3C52PE2%2F20251029%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20251029T094311Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEBkaDmFwLXNvdXRoZWFzdC0xIkgwRgIhAM%2BbltkEA41%2B%2F%2FUKdPZJ33XSExjrzd7um%2Bo2oJ3CPtrXAiEAyblN84DSc4r3R4KUmIqOf4o4ZG%2FAnVBAZ1176FPc3s0qiwQI0v%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARABGgwwMjE2NzUwMzQzOTUiDP3TJwq9YbcS5plRbyrfA31ENBSe4ccr15JlS1H1hg9wDbgxpXV7vEGCrdVOJgd3emv0EnYyaOl8JV9ij%2FDTXLw78oLoafB2zLfFgBi%2BO6c%2FVnOdUPdjOxHa9lBAzyfbGxZuMCJ8Y7%2B8KS0p%2B7wzA%2B2DvQTx7TQvWgbN4Ou23FPHDDOgObIJa9HIDl54vzWV8wr%2BwUYzJjh8yopcbatKj9AD2ZRPhzj%2BJYqxoZm%2Ft%2Bl1NwBHX%2BSLEKj468CT%2FuMuqVSHBPwqwwdhR39PQ%2FoXubXdA473j1LzQg%2F6o5j29NCeZ9sin3%2BQekv581ZzZUFOGPu%2Fq369YnXKjx%2F%2FYU6xJYoSsQjG72JyyXOxUVmEs5r5KeY%2BrNBcASbHLVOVQht25s5O3gjTIewzj8aMpKjLkARgsZNLQOY3ODJ6laH38RYctLjskJCd4RNGHtViyLCm2SpIuEAylmzL1xWNNVJXF50K0iX15GAy7X4sqBp7px0dQ%2F0FoF8GxdYWAd6%2BQtc10WsC4zbWOuzGUoFSJaCKMLIbrdxuKPHAVfN1AmdCFJGWXH2PmRbePCEoVS90nfPMoHKWmyFgI%2B%2BCQfkij0oRluhxpggJ1b5P6wVj4zPOubo5epAiq055CvZtHFvoTlnPibK3DiY0ImP7vA76xPZKMLq4h8gGOqQB9CGOPOnLxOGrKECNBM8hTmNc0saBmYy7oX8kdMFPTvT6%2BNo32b3%2FXvSAa79IIPVhP5T87uItyAU15qIy5VtEqfzKDN5GtW%2FYMGDg%2Fk0u8mApx1g%2BHq1tb5piA75GsNRbOH3SUrhBbW4XJ%2F03S2aUCAwLeQ57KhKP1cYW0JVaEdCAVxrdeacnKKQF7HOncyPF6z%2FunSbIgOK8337Ng1VhaUIlG0Y%3D&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=application%2Fpdf&x-id=GetObject&X-Amz-Signature=9eff71e9faf1e5e221c44c2835954c8c98835da9c8fa5de5fefe755049fcfe02"
      }
    ],
    "is_doc_verification_required": true
  }
}
```

**beneficiary.requires_action**

```json
{
  "type": "beneficiary.requires_action",
  "id": "evt_d40u3boduff039n5h1t0",
  "object": "event",
  "created_at": "2025-10-29T09:43:11.83145611Z",
  "data": {
    "created_at": "2025-10-29T09:43:09.471921Z",
    "party_classification": "self",
    "registration_number": "12345",
    "name": "vibhui",
    "type": "business",
    "destination": "pwa_d40u3b9rcvj50sse4oe0",
    "id": "bnf_d40u3bbgrdjvil4n3q7g",
    "object": "beneficiary",
    "verification_status": "requires_action",
    "address": {
      "city": "bnds",
      "country": "DZ",
      "line1": "C-222",
      "line2": "123",
      "postal_code": "21334",
      "state": "fssd"
    },
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "currency": "USDC",
        "deposit_address": "ox2323",
        "hosted": "yes",
        "type": "ethereum",
        "vasp_name": "testing ",
        "vasp_website": "https://dashboard-brown.tazapay.com/beneficiary/view"
      }
    },
    "phone": {},
    "metadata": {},
    "documents": [
      {
        "type": "screenshot",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-beneficiary-document-qa/bnf_d40u3bbgrdjvil4n3q7g/1761730927028440823_deemed_university_AIQ.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Checksum-Mode=ENABLED&X-Amz-Credential=ASIAQKC7OY4NR3C52PE2%2F20251029%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20251029T094311Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEBkaDmFwLXNvdXRoZWFzdC0xIkgwRgIhAM%2BbltkEA41%2B%2F%2FUKdPZJ33XSExjrzd7um%2Bo2oJ3CPtrXAiEAyblN84DSc4r3R4KUmIqOf4o4ZG%2FAnVBAZ1176FPc3s0qiwQI0v%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARABGgwwMjE2NzUwMzQzOTUiDP3TJwq9YbcS5plRbyrfA31ENBSe4ccr15JlS1H1hg9wDbgxpXV7vEGCrdVOJgd3emv0EnYyaOl8JV9ij%2FDTXLw78oLoafB2zLfFgBi%2BO6c%2FVnOdUPdjOxHa9lBAzyfbGxZuMCJ8Y7%2B8KS0p%2B7wzA%2B2DvQTx7TQvWgbN4Ou23FPHDDOgObIJa9HIDl54vzWV8wr%2BwUYzJjh8yopcbatKj9AD2ZRPhzj%2BJYqxoZm%2Ft%2Bl1NwBHX%2BSLEKj468CT%2FuMuqVSHBPwqwwdhR39PQ%2FoXubXdA473j1LzQg%2F6o5j29NCeZ9sin3%2BQekv581ZzZUFOGPu%2Fq369YnXKjx%2F%2FYU6xJYoSsQjG72JyyXOxUVmEs5r5KeY%2BrNBcASbHLVOVQht25s5O3gjTIewzj8aMpKjLkARgsZNLQOY3ODJ6laH38RYctLjskJCd4RNGHtViyLCm2SpIuEAylmzL1xWNNVJXF50K0iX15GAy7X4sqBp7px0dQ%2F0FoF8GxdYWAd6%2BQtc10WsC4zbWOuzGUoFSJaCKMLIbrdxuKPHAVfN1AmdCFJGWXH2PmRbePCEoVS90nfPMoHKWmyFgI%2B%2BCQfkij0oRluhxpggJ1b5P6wVj4zPOubo5epAiq055CvZtHFvoTlnPibK3DiY0ImP7vA76xPZKMLq4h8gGOqQB9CGOPOnLxOGrKECNBM8hTmNc0saBmYy7oX8kdMFPTvT6%2BNo32b3%2FXvSAa79IIPVhP5T87uItyAU15qIy5VtEqfzKDN5GtW%2FYMGDg%2Fk0u8mApx1g%2BHq1tb5piA75GsNRbOH3SUrhBbW4XJ%2F03S2aUCAwLeQ57KhKP1cYW0JVaEdCAVxrdeacnKKQF7HOncyPF6z%2FunSbIgOK8337Ng1VhaUIlG0Y%3D&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=application%2Fpdf&x-id=GetObject&X-Amz-Signature=9eff71e9faf1e5e221c44c2835954c8c98835da9c8fa5de5fefe755049fcfe02"
      }
    ],
    "is_doc_verification_required": true
  }
}
```

**beneficiary.succeeded**  

```json
{
  "type": "beneficiary.succeeded",
  "id": "evt_d40u3boduff039n5h1t0",
  "object": "event",
  "created_at": "2025-10-29T09:43:11.83145611Z",
  "data": {
    "created_at": "2025-10-29T09:43:09.471921Z",
    "party_classification": "self",
    "registration_number": "12345",
    "name": "vibhui",
    "type": "business",
    "destination": "pwa_d40u3b9rcvj50sse4oe0",
    "id": "bnf_d40u3bbgrdjvil4n3q7g",
    "object": "beneficiary",
    "verification_status": "succeeded",
    "address": {
      "city": "bnds",
      "country": "DZ",
      "line1": "C-222",
      "line2": "123",
      "postal_code": "21334",
      "state": "fssd"
    },
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "currency": "USDC",
        "deposit_address": "ox2323",
        "hosted": "yes",
        "type": "ethereum",
        "vasp_name": "testing ",
        "vasp_website": "https://dashboard-brown.tazapay.com/beneficiary/view"
      }
    },
    "phone": {},
    "metadata": {},
    "documents": [
      {
        "type": "screenshot",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-beneficiary-document-qa/bnf_d40u3bbgrdjvil4n3q7g/1761730927028440823_deemed_university_AIQ.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Checksum-Mode=ENABLED&X-Amz-Credential=ASIAQKC7OY4NR3C52PE2%2F20251029%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20251029T094311Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEBkaDmFwLXNvdXRoZWFzdC0xIkgwRgIhAM%2BbltkEA41%2B%2F%2FUKdPZJ33XSExjrzd7um%2Bo2oJ3CPtrXAiEAyblN84DSc4r3R4KUmIqOf4o4ZG%2FAnVBAZ1176FPc3s0qiwQI0v%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARABGgwwMjE2NzUwMzQzOTUiDP3TJwq9YbcS5plRbyrfA31ENBSe4ccr15JlS1H1hg9wDbgxpXV7vEGCrdVOJgd3emv0EnYyaOl8JV9ij%2FDTXLw78oLoafB2zLfFgBi%2BO6c%2FVnOdUPdjOxHa9lBAzyfbGxZuMCJ8Y7%2B8KS0p%2B7wzA%2B2DvQTx7TQvWgbN4Ou23FPHDDOgObIJa9HIDl54vzWV8wr%2BwUYzJjh8yopcbatKj9AD2ZRPhzj%2BJYqxoZm%2Ft%2Bl1NwBHX%2BSLEKj468CT%2FuMuqVSHBPwqwwdhR39PQ%2FoXubXdA473j1LzQg%2F6o5j29NCeZ9sin3%2BQekv581ZzZUFOGPu%2Fq369YnXKjx%2F%2FYU6xJYoSsQjG72JyyXOxUVmEs5r5KeY%2BrNBcASbHLVOVQht25s5O3gjTIewzj8aMpKjLkARgsZNLQOY3ODJ6laH38RYctLjskJCd4RNGHtViyLCm2SpIuEAylmzL1xWNNVJXF50K0iX15GAy7X4sqBp7px0dQ%2F0FoF8GxdYWAd6%2BQtc10WsC4zbWOuzGUoFSJaCKMLIbrdxuKPHAVfN1AmdCFJGWXH2PmRbePCEoVS90nfPMoHKWmyFgI%2B%2BCQfkij0oRluhxpggJ1b5P6wVj4zPOubo5epAiq055CvZtHFvoTlnPibK3DiY0ImP7vA76xPZKMLq4h8gGOqQB9CGOPOnLxOGrKECNBM8hTmNc0saBmYy7oX8kdMFPTvT6%2BNo32b3%2FXvSAa79IIPVhP5T87uItyAU15qIy5VtEqfzKDN5GtW%2FYMGDg%2Fk0u8mApx1g%2BHq1tb5piA75GsNRbOH3SUrhBbW4XJ%2F03S2aUCAwLeQ57KhKP1cYW0JVaEdCAVxrdeacnKKQF7HOncyPF6z%2FunSbIgOK8337Ng1VhaUIlG0Y%3D&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=application%2Fpdf&x-id=GetObject&X-Amz-Signature=9eff71e9faf1e5e221c44c2835954c8c98835da9c8fa5de5fefe755049fcfe02"
      }
    ],
    "is_doc_verification_required": true
  }
}
```

**beneficiary.failed**

```json
{
  "type": "beneficiary.failed",
  "id": "evt_d40u3boduff039n5h1t0",
  "object": "event",
  "created_at": "2025-10-29T09:43:11.83145611Z",
  "data": {
    "created_at": "2025-10-29T09:43:09.471921Z",
    "party_classification": "self",
    "registration_number": "12345",
    "name": "vibhui",
    "type": "business",
    "destination": "pwa_d40u3b9rcvj50sse4oe0",
    "id": "bnf_d40u3bbgrdjvil4n3q7g",
    "object": "beneficiary",
    "verification_status": "failed",
    "address": {
      "city": "bnds",
      "country": "DZ",
      "line1": "C-222",
      "line2": "123",
      "postal_code": "21334",
      "state": "fssd"
    },
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "currency": "USDC",
        "deposit_address": "ox2323",
        "hosted": "yes",
        "type": "ethereum",
        "vasp_name": "testing ",
        "vasp_website": "https://dashboard-brown.tazapay.com/beneficiary/view"
      }
    },
    "phone": {},
    "metadata": {},
    "documents": [
      {
        "type": "screenshot",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-beneficiary-document-qa/bnf_d40u3bbgrdjvil4n3q7g/1761730927028440823_deemed_university_AIQ.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Checksum-Mode=ENABLED&X-Amz-Credential=ASIAQKC7OY4NR3C52PE2%2F20251029%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20251029T094311Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEBkaDmFwLXNvdXRoZWFzdC0xIkgwRgIhAM%2BbltkEA41%2B%2F%2FUKdPZJ33XSExjrzd7um%2Bo2oJ3CPtrXAiEAyblN84DSc4r3R4KUmIqOf4o4ZG%2FAnVBAZ1176FPc3s0qiwQI0v%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARABGgwwMjE2NzUwMzQzOTUiDP3TJwq9YbcS5plRbyrfA31ENBSe4ccr15JlS1H1hg9wDbgxpXV7vEGCrdVOJgd3emv0EnYyaOl8JV9ij%2FDTXLw78oLoafB2zLfFgBi%2BO6c%2FVnOdUPdjOxHa9lBAzyfbGxZuMCJ8Y7%2B8KS0p%2B7wzA%2B2DvQTx7TQvWgbN4Ou23FPHDDOgObIJa9HIDl54vzWV8wr%2BwUYzJjh8yopcbatKj9AD2ZRPhzj%2BJYqxoZm%2Ft%2Bl1NwBHX%2BSLEKj468CT%2FuMuqVSHBPwqwwdhR39PQ%2FoXubXdA473j1LzQg%2F6o5j29NCeZ9sin3%2BQekv581ZzZUFOGPu%2Fq369YnXKjx%2F%2FYU6xJYoSsQjG72JyyXOxUVmEs5r5KeY%2BrNBcASbHLVOVQht25s5O3gjTIewzj8aMpKjLkARgsZNLQOY3ODJ6laH38RYctLjskJCd4RNGHtViyLCm2SpIuEAylmzL1xWNNVJXF50K0iX15GAy7X4sqBp7px0dQ%2F0FoF8GxdYWAd6%2BQtc10WsC4zbWOuzGUoFSJaCKMLIbrdxuKPHAVfN1AmdCFJGWXH2PmRbePCEoVS90nfPMoHKWmyFgI%2B%2BCQfkij0oRluhxpggJ1b5P6wVj4zPOubo5epAiq055CvZtHFvoTlnPibK3DiY0ImP7vA76xPZKMLq4h8gGOqQB9CGOPOnLxOGrKECNBM8hTmNc0saBmYy7oX8kdMFPTvT6%2BNo32b3%2FXvSAa79IIPVhP5T87uItyAU15qIy5VtEqfzKDN5GtW%2FYMGDg%2Fk0u8mApx1g%2BHq1tb5piA75GsNRbOH3SUrhBbW4XJ%2F03S2aUCAwLeQ57KhKP1cYW0JVaEdCAVxrdeacnKKQF7HOncyPF6z%2FunSbIgOK8337Ng1VhaUIlG0Y%3D&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=application%2Fpdf&x-id=GetObject&X-Amz-Signature=9eff71e9faf1e5e221c44c2835954c8c98835da9c8fa5de5fefe755049fcfe02"
      }
    ],
    "is_doc_verification_required": true
  }
}
```

<br />

<br />
