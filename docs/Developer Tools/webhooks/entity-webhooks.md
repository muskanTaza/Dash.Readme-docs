---
title: Entity
excerpt: These are the events for which webhooks will be triggered
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Entity approval status specific events

| Event                             | Description                                                   | Default |
| --------------------------------- | ------------------------------------------------------------- | ------- |
| `entity.approval_processing`      | Triggered when the entity approval status is processing       | On      |
| `entity.approval_requires_action` | Triggered when the entity approval status is requires\_action | On      |
| `entity.approval_succeeded`       | Triggered when the entity approval status is succeeded        | On      |
| `entity.approval_rejected`        | Triggered when the entity approval status is rejected         | On      |

## Sample Events

### entity.approval\_processing

```
{
  "type": "entity.approval_processing",
  "id": "evt_ctc0lfqe4e771g7bbof0",
  "object": "event",
  "created_at": "2024-12-10T09:32:48.115085309Z",
  "data": {
    "email": "",
    "submitted_at": "2024-12-10T09:32:45.82634Z",
    "created_at": "2024-12-10T09:30:57.404923Z",
    "operating_address": {
      "line1": "delhi",
      "postal_code": "110017",
      "city": "delhi",
      "state": "delhi",
      "country": "IN"
    },
    "registration_address": {
      "line1": "delhi",
      "postal_code": "110017",
      "city": "delhi",
      "state": "delhi",
      "country": "IN"
    },
    "object": "entity",
    "approval_status": "submitted",
    "name": "Muskan",
    "tax_id": "ARWOI9983F",
    "vertical": "Digital Products-Digital Merchandise",
    "registration_number": "1243",
    "registration_date": "2024-12-02T18:30:00.000Z",
    "statement_descriptor": "Muskan",
    "id": "ent_ctc0kk9sgkgeelcl87i0",
    "individual": {
      "national_identification_number": {
          "type": "passport",
          "number": "2345678"
      },
      "date_of_birth": "2001-09-21",
      "nationality": "IN"
    },
    "type": "company",
    "representatives": [
      {
        "address": {},
        "phone": {},
        "created_at": "2024-12-10T09:32:42.102724Z",
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "first_name": "test",
        "last_name": "test",
        "date_of_birth": "2024-12-01T18:30:00.000Z",
        "nationality": "IN",
        "person_id": "psn_ctc0lejij03etefsheb0",
        "roles": [
          "authorised_signatory"
        ],
        "documents": [
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshecg",
            "type": "address",
            "sub_type": "other",
            "file_name": "kyb_doc28422_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Recent utility bill",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc28422_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093248Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=a11eeb171c74a9014ea3cabdb6398a53c5d94090516ffb03397eab5aad594b8e"
          },
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshebg",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc87867_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport front",
            "tag": "identityProofTypeFrontDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc87867_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093248Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=70e5d63795a2e4325e98e3ccb29b9743a1e297a572c608fd3d764ceb31ff431c"
          },
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshec0",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc68349_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport back",
            "tag": "identityProofTypeBackDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc68349_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093248Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=e71bf8ee46f66ed7dd0abfc381f32a30bb0fa67c06e7ec1fb2c65eeb8d89cdbd"
          }
        ],
        "ownership_percentage": 10
      }
    ],
    "documents": [
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefshefg",
        "type": "address",
        "sub_type": "other",
        "file_name": "kyb_doc56357_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Operating address proof",
        "tag": "AddressProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc56357_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093248Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=a165a649003f7c12791e8b09de534c7dd033c1351cb095b8934d1e4e951c287a"
      },
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefsheg0",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc65201_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business shareholding structure",
        "tag": "beneficialOwnershipDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc65201_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093248Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=b5b9b4a7195ade72a68e48b21102bc71d18808fb48c69afa91c5ef358919260a"
      },
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefshef0",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc74277_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business registration proof",
        "tag": "registrationProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc74277_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093248Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=6c21477fcae54c09291bd00f170355cb84a9845d5e197a2cc85c6241a4036a7d"
      }
    ],
    "submit": true
  }
}
```

<br />

### entity.approval\_requires\_action

```
{
  "type": "entity.approval_requires_action",
  "id": "evt_ctc0mqjrbou0rnkv7ce0",
  "object": "event",
  "created_at": "2024-12-10T09:35:39.064978871Z",
  "data": {
    "email": "",
    "submitted_at": "2024-12-10T09:32:45.82634Z",
    "created_at": "2024-12-10T09:30:57.404923Z",
    "operating_address": {
      "line1": "delhi",
      "postal_code": "110017",
      "city": "delhi",
      "state": "delhi",
      "country": "IN"
    },
    "registration_address": {
      "line1": "delhi",
      "postal_code": "110017",
      "city": "delhi",
      "state": "delhi",
      "country": "IN"
    },
    "object": "entity",
    "approval_status": "requires_action",
    "name": "Muskan",
    "tax_id": "ARWOI9983F",
    "vertical": "Digital Products-Digital Merchandise",
    "registration_number": "1243",
    "registration_date": "2024-12-02T18:30:00.000Z",
    "statement_descriptor": "Muskan",
    "id": "ent_ctc0kk9sgkgeelcl87i0",
    "individual": {
      "national_identification_number": {
          "type": "passport",
          "number": "2345678"
      },
      "date_of_birth": "2001-09-21",
      "nationality": "IN"
    },
    "type": "company",
    "representatives": [
      {
        "address": {
          "line1": "MG Road",
          "line2": "Adj ST Mary School",
          "postal_code": "10038",
          "city": "Delhi",
          "state": "Delhi",
          "country": "IN"
        },
        "phone": {},
        "created_at": "2024-12-10T09:32:42.102724Z",
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "first_name": "test",
        "last_name": "test",
        "date_of_birth": "2024-12-01T18:30:00.000Z",
        "nationality": "IN",
        "person_id": "psn_ctc0lejij03etefsheb0",
        "roles": [
          "authorised_signatory"
        ],
        "documents": [
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshecg",
            "type": "address",
            "sub_type": "other",
            "file_name": "kyb_doc28422_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Recent utility bill",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc28422_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093538Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=05bcb8de3eaca6b12d826369a4bd5d534e263daf88f5cdc1737fec54df1aaac2"
          },
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshec0",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc68349_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport back",
            "tag": "identityProofTypeBackDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc68349_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093539Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=17288dec83529e9d7af844c884393c8dc9cac2385b45e32017a28ca757c02d91"
          },
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshebg",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc87867_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport front",
            "tag": "identityProofTypeFrontDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc87867_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093539Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=5215277b56aa2ac89a042e9f1c11ee734bf962b999d58a47d70ca4eef947b322"
          }
        ],
        "ownership_percentage": 10
      }
    ],
    "documents": [
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefshefg",
        "type": "address",
        "sub_type": "other",
        "file_name": "kyb_doc56357_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Operating address proof",
        "tag": "AddressProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc56357_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093538Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=639dc91488ffd0e098af1a61f2bd972e6030b0dea6682f60c38b8795df7f79e3"
      },
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefsheg0",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc65201_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business shareholding structure",
        "tag": "beneficialOwnershipDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc65201_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093539Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=1d80dc52194252aed82494011fad3991515a8b78a14e124d8f1f87a3e61126c3"
      },
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefshef0",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc74277_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business registration proof",
        "tag": "registrationProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc74277_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093539Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=fd98abf0a081d761ad4517e0d7b9014d87ed62d3543ce8078d331a017e41636b"
      }
    ],
    "pending_documents": [
      "Invoice"
    ],
    "submit": true
  }
}
```

<br />

### entity.approval\_succeeded

```
{
  "type": "entity.approval_succeeded",
  "id": "evt_ctc0n9tvggacf0fceob0",
  "object": "event",
  "created_at": "2024-12-10T09:36:39.221318285Z",
  "data": {
    "email": "",
    "approved_at": "2024-12-10T09:36:36.922974Z",
    "submitted_at": "2024-12-10T09:32:45.82634Z",
    "created_at": "2024-12-10T09:30:57.404923Z",
    "operating_address": {
      "line1": "delhi",
      "postal_code": "110017",
      "city": "delhi",
      "state": "delhi",
      "country": "IN"
    },
    "registration_address": {
      "line1": "delhi",
      "postal_code": "110017",
      "city": "delhi",
      "state": "delhi",
      "country": "IN"
    },
    "object": "entity",
    "approval_status": "approved",
    "name": "Muskan",
    "tax_id": "ARWOI9983F",
    "vertical": "Digital Products-Digital Merchandise",
    "registration_number": "1243",
    "registration_date": "2024-12-02T18:30:00.000Z",
    "statement_descriptor": "Muskan",
    "id": "ent_ctc0kk9sgkgeelcl87i0",
    "type": "company",
    "individual": {
      "national_identification_number": {
          "type": "passport",
          "number": "2345678"
      },
      "date_of_birth": "2001-09-21",
      "nationality": "IN"
    },
    "representatives": [
      {
        "address": {
          "line1": "MG Road",
          "line2": "Adj ST Mary School",
          "postal_code": "10038",
          "city": "Delhi",
          "state": "Delhi",
          "country": "IN"
        },
        "phone": {},
        "created_at": "2024-12-10T09:32:42.102724Z",
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "first_name": "test",
        "last_name": "test",
        "date_of_birth": "2024-12-01T18:30:00.000Z",
        "nationality": "IN",
        "person_id": "psn_ctc0lejij03etefsheb0",
        "roles": [
          "authorised_signatory"
        ],
        "documents": [
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshecg",
            "type": "address",
            "sub_type": "other",
            "file_name": "kyb_doc28422_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Recent utility bill",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc28422_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093639Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=880d82ddce7a526baf1015e1148ccd1fee1d81278ceca74c3323d6f4dcf2a470"
          },
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshec0",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc68349_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport back",
            "tag": "identityProofTypeBackDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc68349_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093639Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=1e1e4148b07960ce0ef02e4e8a38f542871129e28c7a98fe07d7a0a6577c70ab"
          },
          {
            "updated_at": "2024-12-10T09:32:45.825839Z",
            "document_id": "doc_ctc0lejij03etefshebg",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc87867_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport front",
            "tag": "identityProofTypeFrontDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc87867_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093639Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=675258683bb9220adc45c90259c6536b64d5f029632b83672b9e490d1a53842f"
          }
        ],
        "ownership_percentage": 10
      }
    ],
    "documents": [
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefsheg0",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc65201_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business shareholding structure",
        "tag": "beneficialOwnershipDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc65201_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093639Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=dc570778ee4dff3ec7438bb624eba3d31d131a9f684c4e3afcbcff602973afcb"
      },
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefshef0",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc74277_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business registration proof",
        "tag": "registrationProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc74277_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093639Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=23e8c67f17a85379dd672ec098640020d4000c5c8de178d821e1398ed49499df"
      },
      {
        "updated_at": "2024-12-10T09:32:45.825839Z",
        "document_id": "doc_ctc0lfbij03etefshefg",
        "type": "address",
        "sub_type": "other",
        "file_name": "kyb_doc56357_10December2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Operating address proof",
        "tag": "AddressProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ctc0kkbij03etefshdt0/kyb_doc56357_10December2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T093639Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=f105dac9b22a5333604130914707dd91d61206a76cd1cfcee9b3cf89b4e05d87"
      }
    ],
    "pending_documents": [
      "Invoice"
    ],
    "submit": true
  }
}
```

<br />

### entity.approval\_rejected

```
{
  "type": "entity.approval_rejected",
  "id": "evt_ctc144tvggacf0fchvsg",
  "object": "event",
  "created_at": "2024-12-10T10:04:03.463812239Z",
  "data": {
    "email": "",
    "submitted_at": "2024-11-26T09:09:17.934764Z",
    "created_at": "2024-11-26T09:07:33.605574Z",
    "operating_address": {
      "line1": "SD",
      "postal_code": "DS",
      "city": "SD",
      "state": "A",
      "country": "IN"
    },
    "registration_address": {
      "line1": "SD",
      "postal_code": "DS",
      "city": "SD",
      "state": "A",
      "country": "IN"
    },
    "object": "entity",
    "approval_status": "rejected",
    "name": "Muskan",
    "tax_id": "ARWPI6789A",
    "vertical": "Ecommerce-Custom made clothing (to order)",
    "registration_number": "EFR",
    "registration_date": "2024-11-02T18:30:00.000Z",
    "statement_descriptor": "Muskan",
    "id": "ent_ct2ovl9f5lhf6huap5cg",
    "individual": {
      "national_identification_number": {
          "type": "passport",
          "number": "2345678"
      },
      "date_of_birth": "2001-09-21",
      "nationality": "IN"
    },
    "type": "company",
    "representatives": [
      {
        "address": {
          "line1": "MG Road",
          "line2": "Adj ST Mary School",
          "postal_code": "10038",
          "city": "Delhi",
          "state": "Delhi",
          "country": "IN"
        },
        "phone": {},
        "created_at": "2024-11-26T09:09:13.423008Z",
        "updated_at": "2024-11-26T09:09:17.934534Z",
        "first_name": "ER",
        "last_name": "F",
        "date_of_birth": "2024-11-03T18:30:00.000Z",
        "nationality": "IN",
        "person_id": "psn_ct2p0efvfes2ls2icgu0",
        "roles": [
          "director"
        ],
        "documents": [
          {
            "updated_at": "2024-11-26T09:09:17.934534Z",
            "document_id": "doc_ct2p0efvfes2ls2icgvg",
            "type": "address",
            "sub_type": "other",
            "file_name": "kyb_doc96573_26November2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Recent utility bill",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc96573_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=f9df595274faec769a77a7712a87954db65003702ea055782404fdd75a3fdcd1"
          },
          {
            "updated_at": "2024-11-26T09:09:17.934534Z",
            "document_id": "doc_ct2p0efvfes2ls2icgv0",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc13976_26November2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport back",
            "tag": "identityProofTypeBackDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc13976_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=e13844d1b52a46787ebadd9bd531a9fd33b0504e128571eab3149e0fe0c39dd0"
          },
          {
            "updated_at": "2024-11-26T09:09:17.934534Z",
            "document_id": "doc_ct2p0efvfes2ls2icgug",
            "type": "identity",
            "sub_type": "passport",
            "file_name": "kyb_doc39908_26November2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
            "description": "Passport front",
            "tag": "identityProofTypeFrontDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc39908_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=ee7367a4a7539ca6080980357ede7456eb15645a85da24a1a506bea6700cb271"
          }
        ],
        "ownership_percentage": 10
      }
    ],
    "documents": [
      {
        "updated_at": "2024-11-26T09:09:17.934534Z",
        "document_id": "doc_ct2p0ffvfes2ls2ich20",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc62092_26November2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business shareholding structure",
        "tag": "beneficialOwnershipDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc62092_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=4a1e3bd59a502e0de1ff3eb4be5193087991b7cc800de51d6a455751cabfd63e"
      },
      {
        "updated_at": "2024-11-26T09:09:17.934534Z",
        "document_id": "doc_ct2p0fnvfes2ls2ich30",
        "type": "address",
        "sub_type": "other",
        "file_name": "kyb_doc39576_26November2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Operating address proof",
        "tag": "AddressProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc39576_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=10ad26768df8fb52890df74a9b867f0b595b2d6c8c6c472cd289cdb62615a41a"
      },
      {
        "updated_at": "2024-11-26T09:09:17.934534Z",
        "document_id": "doc_ct2p0fnvfes2ls2ich2g",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc88341_26November2024_Screenshot 2024-11-26 at 2.31.42 PM.png",
        "description": "Business registration proof",
        "tag": "registrationProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc88341_26November2024_Screenshot%202024-11-26%20at%202.31.42%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=8db4ef0b2efdf459af2bebee25f6eae1cdfcb75cfa77a8acbf208f032abad872"
      },
      {
        "updated_at": "2024-12-10T10:04:00.055814Z",
        "document_id": "doc_ctc0nvrij03etefshf4g",
        "type": "other",
        "sub_type": "other",
        "file_name": "kyb_doc26527_10December2024_Screenshot 2024-10-25 at 4.49.15 PM.png",
        "tag": "requestedDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_ct2ovlfvfes2ls2icfig/kyb_doc26527_10December2024_Screenshot%202024-10-25%20at%204.49.15%20PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=ASIAUGJYD3OSULG77W43%2F20241210%2Fap-southeast-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20241210T100403Z&amp;X-Amz-Expires=3600&amp;X-Amz-Security-Token=IQoJb3JpZ2luX2VjEM7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgSy1gj4k2zToD2pZE1PSMWAY70e2nKcroRpipB4S4ImECIQCEeblV2ql1kb3PXqgB%2FU8upPkQyqMLqSh1KmsWGHhCPCr9AwiH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM4ZfXfG6g3ceTQd2XKtED44GmL%2FOCSPsHUdqVeBsPjh%2FW4%2Bksc5fleV7%2FA3Aoy%2FRo8teNG5xFjmU%2FWpBJ0cgZuoJJnVhyMrPnqZIBm%2BIst6u80PPxwdUYEYgv4hI7%2B24lTEoeiNYjFIwSPeMkAx%2BRtyzilTFzMOnIUD4QLn%2B%2FP7U96c0JUHw8DNImaG8OajPTV8OtxW0S0HWdO%2FsbrviEv4bOQMhWo9m2%2BvWHibILNLGh6FeTtVC2fTddRhtMuPpJKtUnbFLf4%2F%2B7x2RXi%2BwRyT7X%2FOUl4V9Hs%2F9FDwZhiDSr3xKKEOzlDgEmSBQpWDlV7XtevPn%2FEpQ3QnDyQcSPhLg6BxuZpjElf%2FSaPsKdZbt2XynisR87S6pfsEESLRFHbv68ARGDy7cnO2x%2Fif9bzgFE31M4Y74EjHnNV%2Fc1%2F%2FSg5KxRedCZ35IW%2BE9R9geeAVp5DI7FcoSYibkgseoF2Ysr903Mg9KWjQrI4vqUsgSsV6nAJC%2FiAwQZDVGOUQyfAJn1SxQpcIDnTWwBnbJcB7GS1HPuMlg0%2FMvM%2FJDXTmgPsSCPmFjhmsjVypIbSV2YjKQiPOvEJYAGn54IdkkhtohIUa5jR0%2FTDkOLDXWzkG279LpebCwFug92bFFaES8zMPS137oGOqUBF8I%2BhtHyPcwLIei2om2Wa8tXua2SSBauLK2kcvVFz7r7Syk7ZUWqMVZUPibolxSxnH1P5lrsbWbpuG4kJj5qOCyWm6v8MHMQ%2FkUFewvJ8bL6xTeOub1N8cr2WnjkfXpmYvoV70amooUPUJ0HRw%2FYMVTJXJhMJ0r2HyZYnFLz%2B14VPgRufOTdgz28YhY%2BYslIjv8OLvlGCVR0AkPwColVc9ZaqPY2&amp;X-Amz-SignedHeaders=host&amp;response-content-disposition=attachment%3B&amp;response-content-type=image%2Fpng&amp;x-id=GetObject&amp;X-Amz-Signature=fc35742a94bd45ccca553d4aa52b484eaebec8322ae0ac9e6f0a7db834c60211"
      }
    ],
    "submit": true
  }
}
```