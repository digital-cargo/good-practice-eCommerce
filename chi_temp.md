## Process Description

### Shipper´s process and data
 
This section provides the process description for the Shipper’s responsibilities aligned with the data structures described in the following chapters (“Product”, “Item”, “Pieces”) and the sequence diagram.
 
The process starts with the Shipper providing the information on the items to be transported in its WMS / operational system. Based on this data, the Shipper creates the corresponding ONE Record logistics objects and exposes them to the other stakeholders.
 
The process description for the Shipper as Shipper is as follows:
 
1. The Shipper creates the commercial order data for the e-commerce shipment in its WMS / operational system.  
   On this basis, the Shipper generates ONE Record `Product`, `Item` and `Piece` logistics objects according to the mappings described above:  
   - `Product` with description, HS code and uniqueIdentifier,  
   - `Item` with price, weight, dimensions and the various identifiers (customer id, consignee id, shipping order id, parcel id, invoice number, external tracking code, article identifiers, country of origin and destination),  
   - `Piece` with parcel id and special handling codes, linking the contained `Item` objects via `containedItems`.  
   All logistics objects are created with unique IDs on the Shipper’s ONE Record server and are correctly linked (e.g. `Item.ofProduct`, `Piece.containedItems`, optional backlinks such as `Item.inPiece` via PATCH).
 
2. After creation, the Shipper exposes these logistics objects on its ONE Record endpoint and sends a notification to the Forwarder that new `Pieces` (and related `Items` / `Products`) are available.  
   The Forwarder then retrieves (`GET`) the relevant logistics objects from the Shipper, as reflected in the sequence diagram (“Notification for creation of Pieces” and subsequent `GET Pieces, Items`).
 
3. When Customs has performed the PLACI screening, the result is represented as `Check` and `CheckTotalResult` logistics objects linked to the `Piece`. Customs patches the PLACI status into the `Piece` on the Shipper’s ONE Record endpoint.  
   the Shipper consumes this update and sends notifications to the Forwarder, CHA Export and Carrier about the updated PLACI status (“Notification for update of placi check”), ensuring that all parties work with the current risk status before further physical handling.
 
4. In parallel to the digital process, the Shipper prepares the physical parcels corresponding to the `Piece` objects and hands over the physical freight (Pieces) to the Forwarder (“Provide physical freight (Pieces)”).  
   The physical handover is aligned with the digital `Piece` representation so that each parcel can be traced back to its corresponding ONE Record `Piece`.
 
5. After Customs has performed the customs presentation check on piece level, the result is again shared via `Check` and `CheckTotalResult` logistics objects linked to the `Piece`. Customs patches the customs presentation status into the `Piece`.  
   The Shipper consumes this update and notifies the Carrier about the updated customs presentation status (“Notification for update of customs presentation status”). In this way, the Shipper ensures that the regulatory status on piece level (PLACI and customs presentation) is consistently available to all relevant actors via the `Piece` and the linked `Check` logistics objects.

## Final output


```json
{
  "@context": {
    "@vocab": "https://onerecord.iata.org/ns/cargo#"
  },

  "@graph": [
    {
      "@type": "Party",
      "@id": "https://1r.example.com/logistics-objects/party-consignor",
      "name": "Yucan Info Tech Co., Ltd",
      "accountNumbers": [
        {
          "@type": "AccountNumber",
          "accountNumberType": {
            "@id": "https://onerecord.iata.org/ns/coreCodeLists#AccountType_CONSIGNOR"
          },
          "textualValue": "IOSS-DE-1234567"
        }
      ],
      "address": {
        "@id": "https://1r.example.com/logistics-objects/address-consignor"
      }
    },

    {
      "@type": "Address",
      "@id": "https://1r.example.com/logistics-objects/address-consignor",
      "street": "ConsignorStreet 1",
      "postalCode": "12345",
      "cityName": "ConsignorCity",
      "country": {
        "@id": "https://onerecord.iata.org/ns/coreCodeLists#CountryCode_DE"
      }
    },

    {
      "@type": "Party",
      "@id": "https://1r.example.com/logistics-objects/party-buyer",
      "name": "Buyer Name",
      "address": {
        "@id": "https://1r.example.com/logistics-objects/address-buyer"
      }
    },

    {
      "@type": "Address",
      "@id": "https://1r.example.com/logistics-objects/address-buyer",
      "street": "BuyerStreet 10",
      "postalCode": "54321",
      "cityName": "BuyerCity",
      "country": {
        "@id": "https://onerecord.iata.org/ns/coreCodeLists#CountryCode_DE"
      }
    },

    {
      "@type": "Waybill",
      "@id": "https://1r.example.com/logistics-objects/[MAWB-NUMBER]",
      "waybillPrefix": "112",
      "waybillNumber": "39023246",
      "waybillType": { "@id": "https://onerecord.iata.org/ns/cargo#MASTER" },
      "shipment": {
        "@id": "https://1r.example.com/logistics-objects/[BOX-ID]"
      }
    },

    {
      "@type": "Shipment",
      "@id": "https://1r.example.com/logistics-objects/[BOX-ID]",
      "waybill": {
        "@id": "https://1r.example.com/logistics-objects/[MAWB-NUMBER]"
      },
      "pieces": [
        {
          "@id": "https://1r.example.com/logistics-objects/[REFERENCE-ID]"
        }
      ],
      "totalGrossWeight": {
        "@type": "Value",
        "value": {
          "@type": "http://www.w3.org/2001/XMLSchema#double",
          "@value": "3.704"
        },
        "unit": {
          "@id": "https://onerecord.iata.org/ns/coreCodeLists#MeasurementUnitCode_KGM"
        }
      },
      "shipper": {
        "@id": "https://1r.example.com/logistics-objects/party-consignor"
      },
      "consignee": {
        "@id": "https://1r.example.com/logistics-objects/party-buyer"
      }
    },

    {
      "@type": "Piece",
      "@id": "https://1r.example.com/logistics-objects/[REFERENCE-ID]",
      "ofShipment": {
        "@id": "https://1r.example.com/logistics-objects/[BOX-ID]"
      },
      "slac": 1,

      "grossWeight": {
        "@type": "Value",
        "value": {
          "@type": "http://www.w3.org/2001/XMLSchema#double",
          "@value": "3.704"
        },
        "unit": {
          "@id": "https://onerecord.iata.org/ns/coreCodeLists#MeasurementUnitCode_KGM"
        }
      },
      "containedItems": [
        {
          "@id": "https://1r.example.com/logistics-objects/[ITEM-ID-1]"
        },
        {
          "@id": "https://1r.example.com/logistics-objects/[ITEM-ID-2]"
        }
      ]
    },

    {
      "@type": "Item",
      "@id": "https://1r.example.com/logistics-objects/[ITEM-ID-1]",
      "description": "Assorted goods in bag",
      "itemQuantity": 1,
      "ofProduct": {
        "@id": "https://1r.example.com/logistics-objects/[PRODUCT-ID-1]"
      }
    },

    {
      "@type": "Item",
      "@id": "https://1r.example.com/logistics-objects/[ITEM-ID-2]",
      "description": "Assorted goods in bag",
      "itemQuantity": 1,
      "ofProduct": {
        "@id": "https://1r.example.com/logistics-objects/[PRODUCT-ID-2]"
      }
    },

    {
      "@id": "https://1r.example.com/logistics-objects/[PRODUCT-ID-1]",
      "@type": "Product",
      "description": "T-Shirt cotton black size M",
      "hsCode": "61091000",
      "quantity": 2,
      "grossWeight": {
        "@type": "Value",
        "value": {
          "@type": "http://www.w3.org/2001/XMLSchema#double",
          "@value": "1.200"
        },
        "unit": {
          "@id": "https://onerecord.iata.org/ns/coreCodeLists#MeasurementUnitCode_KGM"
        }
      },
      "unitPrice": {
        "@type": "Value",
        "value": {
          "@type": "http://www.w3.org/2001/XMLSchema#double",
          "@value": "19.99"
        },
        "unit": {
          "@id": "https://onerecord.iata.org/ns/coreCodeLists#CurrencyCode_EUR"
        }
      }
    },
    {
      "@id": "https://1r.example.com/logistics-objects/[PRODUCT-ID-2]",
      "@type": "Product",
      "description": "Wireless earbuds",
      "hsCode": "85183095",
      "quantity": 1,
      "grossWeight": {
        "@type": "Value",
        "value": {
          "@type": "http://www.w3.org/2001/XMLSchema#double",
          "@value": "2.504"
        },
        "unit": {
          "@id": "https://onerecord.iata.org/ns/coreCodeLists#MeasurementUnitCode_KGM"
        }
      },
      "unitPrice": {
        "@type": "Value",
        "value": {
          "@type": "http://www.w3.org/2001/XMLSchema#double",
          "@value": "49.90"
        },
        "unit": {
          "@id": "https://onerecord.iata.org/ns/coreCodeLists#CurrencyCode_EUR"
        }
      }
    }
  ]
}
```