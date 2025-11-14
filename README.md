≤<!--
---
title: good-practice-eCommerce
repository: https://github.com/digital-cargo/good-practice-eCommerce
version: 0.0.1
maintainers: 
- Philipp Billion
ontologies:
- https://onerecord.iata.org/ns/cargo/3.0.0
- https://onerecord.iata.org/ns/api/2.0.0
- https://onerecord.iata.org/ns/coreCodeLists/0.0.3
data-classes:
- https://onerecord.iata.org/ns/cargo#Waybill
- https://onerecord.iata.org/ns/cargo#Shipment
- https://onerecord.iata.org/ns/cargo#Piece
- https://onerecord.iata.org/ns/cargo#TransportMovement
- https://onerecord.iata.org/ns/cargo#Organization
- https://onerecord.iata.org/ns/cargo#LogisticsEvents
- https://onerecord.iata.org/ns/cargo#Location
- https://onerecord.iata.org/ns/cargo#Company
- https://onerecord.iata.org/ns/cargo#Carrier
- https://onerecord.iata.org/ns/cargo#Value
- https://onerecord.iata.org/ns/cargo#Loading
data-properties:
- https://onerecord.iata.org/ns/cargo#actions
- https://onerecord.iata.org/ns/cargo#arrivalLocation
- https://onerecord.iata.org/ns/cargo#departureLocation
- https://onerecord.iata.org/ns/cargo#involvedInActions
- https://onerecord.iata.org/ns/cargo#shipment
- https://onerecord.iata.org/ns/cargo#partofShipment
- https://onerecord.iata.org/ns/cargo#transportIdentifier
- https://onerecord.iata.org/ns/cargo#loadedPieces
- https://onerecord.iata.org/ns/cargo#servedActivity
- https://onerecord.iata.org/ns/cargo#events
- https://onerecord.iata.org/ns/cargo#pieces
- https://onerecord.iata.org/ns/cargo#waybillNumber
- https://onerecord.iata.org/ns/cargo#waybillType
api-version:
- 2.0.0
api-endpoints:
- method: GET 
  path: /logistics-objects/{logisticsObjectId} 
- method: GET 
  path: /logistics-objects/{logisticsObjectId}
- method: GET 
  path: /logistics-objects/{logisticsObjectId}/logistics-events
- method: GET 
  path: /logistics-objects/{logisticsObjectId}/logistics-events/{logisticsEventId}
- method: POST 
  path: /notifications
- method: GET 
  path: /subscriptions
- method: POST 
  path: /subscriptions
- method: GET 
  path: /action-requests/{actionRequestId} 
- method: DELETE
  path: /action-requests/{actionRequestId}
---
-->

# Good Practice: eCommerce
[![Made with love for Digital Cargo](https://img.shields.io/badge/Made%20with%20%E2%9D%A4%20for-Digital%20Cargo-dce435)](https://digital-cargo.org)
![Made with support of the German Federal Ministry for Digital Transformation and Government Modernisation](https://img.shields.io/badge/Made%20with%20support%20of%20the-%20German%20Federal%20Ministry%20for%20Digital%20Transformation%20and%20Government%20Modernisation-dce435)
[![GitHub](https://img.shields.io/github/license/digital-cargo/good-practice-shipment-tracking)](https://creativecommons.org/licenses/by/4.0/)
[![Releases](https://img.shields.io/github/v/release/digital-cargo/good-practice-eCommerce)](https://github.com/digital-cargo/good-practice-eCommerce/releases)

This repository contains the good practice to implement data exchange in the context of eCommerce air cargo based on the ONE Record standard.

## DELME: STATUS / Open Issues

- RFID must be separated into a separate good practice
- PUB/SUB examples
- Replace placeholders for servers
- DESIGN ADDITIONAL DATA FIELDS
- Add PUB/SUB in Sequence Diagram
	- Data owner triggered SUB by Shipper and FF
- ChatGPT to optimize
- RFID: potential for other application when 1R URI written into Tag 


## DELME: Status

| **Step**                         | **Implementing party** | **AP1.2: Process Description** | **AP1.2: Sequence Diagram** | **AP1.2: LO Description** | **AP1.2: API Feature application** | **AP1.3: Postman Collection, Test-Execution, etc** | 
|----------------------------------|------------------------|-------------------------|----------------------|--------------------|---------------------|------------------------|
| **eCom Shipper: Data provision** | CHI                    | nok                     | nok                  | nok                | nok                 | nok                    |
| **Customs: PLACI**               | LH Cargo               | 50%                     | nok                  | 50%                | nok                 | nok                    |
| **Forwarder: BU**                | Schenker               | nok                     | nok                  | nok                | nok                 | nok                    |
| **Forwarder: RFID part**         | LH Cargo               | nok                     | nok                  | nok                | nok                 | nok                    |
| **Carrier: core transport**      | LH Cargo               | nok                     | nok                  | nok                | nok                 | nok                    |
| **Customs: presentation status** | LH Cargo               | nok                     | nok                  | nok                | nok                 | nok                    |
| **GHA Import**                   | CHI                    | nok                     | nok                  | nok                | nok                 | nok                    |


## Abstract

ECommerce is a constantly growing commodity with unprecidented challengedes to both, the physical handling and the data management to ensure compliance, safety and efficiency. But the logistics and cargo industry grapples with a prevalent and pressing issue: there is no standard to share eCommerce data sharing throughout the supply chain. The consequence of this lack of standardization is evident: stakeholders are burdened with the expensive and time-consuming task of individualized integrations, harmonization of incompatible data formats from different sources, leading to compliance issues, inefficiencies, misunderstandings, and subsequent maintenance costs. The ONE record standard remedies this situation. This good practice document describes a sequence of required steps to share eCommerce data via ONE Record. 

Based on the ONE Record API version 2.x.x and the ONE Record Data Model version 3.x,x, this document provides guidance on how to share eCommerce data in an easy-to-use and standardized manner.

This good practice is an outcome of the collaboration of major stakeholders within the German "Digital Testbed Air Cargo"-Consortium, sponsored by the German Federal Ministry for Digital Transformation and Government Modernisation. Lufthansa Cargo and Fraunhofer IML were in the lead.

## Introduction

DTAC intro

In the dynamic world of logistics and cargo, eCommerce shipments set new challenges for both, the physical handling of goods and the sharing and management of data. Yet, as businesses expand and systems diversify, the industry faces a challenge: the myriad of non-standardized tracking systems, each requiring unique integration and understanding. This fragmentation not only complicates operations but also escalates costs and reduces efficiency.

Initiated and moderated by the International Air Transportation Association (IATA), ONE Record aims to be the standard to enable and simplify data sharing in  transportation industry. By leveraging the ONE Record standard, stakeholders can draw on a unified data model and API that promotes seamless integration across various platforms and improves collaboration between various organizations. 
This standardization comes with a number of benefits, from reducing the complexity and cost of custom integrations to enhancing transparency and trust.
It lays the foundation for standardization, enabling a consistent data model and API across diverse platforms, thereby streamlining integrations and collaborations.
This uniformity heightens transparency, allowing stakeholders to effortlessly interpret shipment data, fostering trust throughout the supply chain.
Moreover, the standardized approach curtails complexities tied to integration, conserving both time and resources that might otherwise be diverted to bespoke solutions. 

The purpose of this document is to explain how eCommerce data can be shared most efficiently by using ONE Record. Among other things, the goal is to highlight ONE Record's unique value proposition and motivate technical and business audiences to move to this standardized approach.

### Scope

This good practice details the application of the ONE Record standard specifically in the context of shipment tracking. 
By using this good practice, organizations can understand, adopt, and streamline their shipment tracking offering to global best practice.

**What this document covers:**

- **Business context**: Assumptions, prerequisites, and the broader business scenario where this good practice is applicable.
- **Technical examples**: Detailed descriptions and examples of the API calls, data model classes, data mappings, and their applications in the context of shipment tracking.
- **Transition recommendations**: Recommendations and guidelines that businesses should consider for a smooth and effective transition to ONE Record.

**What this document does not cover:**

- **Compelete implementations**: This good practice includes sample code to support knowledge transfer, it does not provide detailed implementation or out-of-the-box software.
- **Comparison with other standards**: This good practice describes the implementation with the ONE Record Standard. A comparison with other standards in the industry is not covered.
- **Vendor-specific implementations**: This document focuses on the standard itself and does not address specific third-party tools or solutions.
- **Complete technical specifications**: This document focuses solely on the ONE Record aspects pertinent to eCommerce data sharing and doesn't encompass the entire technical breadth of the standard.

This guide is based on the published ONE Record specifications prevalent as of `xxxx-xx-xx`. 
As the industry evolves, it is imperative for stakeholders to keep up to date on subsequent versions or changes to the standard.

The interpretations is following 


**Target audience**

This document is intended for anyone interested in this topic. This can range from logistics professionals, supply chain managers, software developers, and other stakeholders involved in shipment tracking and data exchange within the logistics and cargo industry. It is designed to cater to both technical and business-oriented individuals interested in adopting standardized practices for efficient eCommerce data sharing.

**General definitions within eCommerce data sharing**

A `shipment` is defined as pieces under one contract and is not limited to the Air Waybill (AWB), which is used particularly in air freight. Since ONE Record aims at multimodality, this good practice should also be applicable to transport modes other than air transport.

A `piece` refers to an individual item or unit of cargo that is part of a larger shipment. It could be a single package, container, pallet, or any other distinct physical unit.

An `item`....

A `parcel`....

`GHA`: Ground Handling Agent

**Geographical coverage**

This eCommerce data sharing best practice is globally applicable, unhindered by regional or national distinctions. 
With no legal or operational barriers to its adoption, the outlined solution is primed for worldwide deployment. 
As a result, companies of any size, at any location, can take advantage of the standardized workflows and increased efficiencies created by ONE Record.

### Variants

This section explores different scenarios within the context of the ONE Record Standard, delineating various approaches to data exchange in the realm of eCommerce data sharing. These scenarios encompass diverse arrangements of data sharing and update processes among stakeholders involved in the logistics and cargo industry.
(...)

## Background

### ONE Record Standard

The implementation of shipment tracking as described in this good practice is based entirely on the [ONE Record standard](https://github.com/IATA-Cargo/ONE-Record).

This good practice incorporates data classes of the [ONE Record cargo ontology v3.0.0](https://onerecord.iata.org/ns/cargo)
and the [ONE Record core code lists ontology v0.0.3](https://onerecord.iata.org/ns/coreCodeLists).

Furthermore, it utilises the [ONE Record API specificaiton v2.0.0](https://iata-cargo.github.io/ONE-Record/).

### Related Good Practices

The [ShipmentTracking](https://github.com/digital-cargo/good-practice-shipment-tracking) use case is closely related to the [ShipmentRecord](https://github.com/digital-cargo/good-practice-shipment-record) use case which is also based on the ONE Record standard. However, the eCommerce Data Sharing use case is focused to the exchange of eCommerce related information with other parties.

### Piece-centricity and physics-orientation

Today in air cargo, tracking information is typically provided at the shipment level, but the ONE Record data model follows the principle of piece-centricity as a core design principle.
Another design principle of ONE Record is its aim to reflect the actual physical world, its objects and activities. 

For example, in ONE Record, it is not a legal object or a paper document such as the Air Waybill (AWB) that marks the progress of a shipment until it reaches a milestone. Instead, it is the actual [Piece](https://onerecord.iata.org/ns/cargo#Piece), the wrapping [Shipment](https://onerecord.iata.org/ns/cargo#Shipment), or a [TransportMovement](https://onerecord.iata.org/ns/cargo#TransportMovement) activity that reaches a milestone in the journey. 
For example, when every piece in a shipment has been loaded and the aircraft departs, we consider the entire shipment as having departed.

### skeletonIndicator

The [skeletonIndicator](https://onerecord.iata.org/ns/cargo#skeletonIndicator) is a specific marker or flag used within data objects in the ONE Record standard. 
The skeletonIndicator signifies that the data object and its properties act as placeholders and do not represent granular, individual data points. Instead, they offer a high-level or "skeletal" representation of the data, primarily for modeling piece-level data.

It enables piece-level modeling of shipment data in a not fully piece-level environment that is in transition, but provides the basis for future developments. 
This can be useful (1) when piece-level granularity is not required, (2) when non-integrable data sets are involved, (3) or when piece-level processing is not yet feasible in physical handling operations.

## Business Process and Data Sharing

### Business Process overview

Remark: For the business interaction, all ONE Record data sharing is displayed as a separte swimlane. This is not to be interpreted as a single server or storage. It includes all de-central ONE Record servers by the different stakeholders. 

```mermaid
sequenceDiagram
    %% Jede Lifeline repraesentiert den Stakeholder inkl. seines ONE Record Endpoints
    participant Shipper 
    participant Forwarder
    participant CHA Export
    participant Customs
    participant Carrier
    participant Consignee

    activate Shipper
    Shipper->>Shipper: CREATE Pieces, Items
    Shipper->>Forwarder: Notification for creation of Pieces
    deactivate Shipper
    activate Forwarder
    Forwarder->>Shipper: GET Pieces, Items
    Forwarder->>Forwarder: Check data, perform planning (updates)
    Forwarder->>Forwarder: CREATE or PATCH Waybill(MAWB/HAWB), ULDs
    deactivate Forwarder
    Forwarder->>CHA Export: Notification for creation of Waybills, ULDs
    Forwarder->>Customs: Notification for creation of Waybills, ULDs
    Forwarder->>Carrier: Notification for creation of Waybills, ULDs
    CHA Export->>Forwarder: GET Waybills, ULDs
    CHA Export->>Shipper: GET Pieces, Items
    CHA Export->>CHA Export: Check data, perform planning (updates)
    Customs->>Forwarder: GET Waybills, ULDs
    Customs->>Shipper: GET Pieces, Items
    Carrier->>Forwarder: GET Waybills, ULDs
    Carrier->>Shipper: GET Pieces, Items
    Carrier->>Carrier: Check data, perform planning (updates)
    Customs->>Customs: CREATE check for placi status
    Customs->>Shipper: PATCH placi status into Piece
    Shipper->>Forwarder: Notification for update of placi check
    Shipper->>CHA Export: Notification for update of placi check
    Shipper->>Carrier: Notification for update of placi check

    Shipper-->>Forwarder: Provide physical freight (Pieces)
    activate Forwarder
    Forwarder-->>Forwarder: Build up ULDs
    Forwarder->>CHA Export: Provide physical freight (ULDs)
    deactivate Forwarder
    activate CHA Export
    CHA Export-->>CHA Export: Perform physical acceptance check
    CHA Export->>Shipper: PATCH Status Update RCS into Pieces (Event)
    CHA Export-->>Carrier: Handy over physical freight (ULDs)
    CHA Export->>Shipper: PATCH Status Update FOW into Pieces (Event)
    Shipper->>Customs: Notification for Status Update FOW
    deactivate CHA Export
    activate Customs
    Customs->>Customs: CREATE check for customs presentation
    Customs->>Shipper: PATCH customs presentation status into Piece
    deactivate Customs
    Shipper->>Carrier: Notification for update of customs presentation status
    activate Carrier
    Carrier->>Shipper: PATCH Status Update DEP into Pieces (Event)
    Carrier-->>Carrier: Perform flight (DEP, ARR) and unload
    deactivate Carrier

    %% 6) Zollvorlage & Praesentation
    alt Presentation not required
        Carrier-->>Consignee: Deliver shipment
    else Presentation required
        Carrier-->>Customs: Present boxes 
        Customs->>Shipper: PATCH customs presentation status update into Piece
        Shipper->>Carrier: Notification for update of customs presentation status
        Carrier-->>Consignee: Deliver shipment
    end 


```

#### Remarks
* The traditional Customs Declaration process is not integrated here - as it doesn´t differ from the conventional customs declaration process
* The role "Carrier" includes the import Cargo Handling Agent role at the carrier hub, which is - in this case - also the import station
* Logististics Objects are always mentioned in plural if it is likely that more than one object is used; still some objects, like ULD can have occure as single or multiple physical entities
* Updates / Corrections are always possible, but not explicitly mentioned here. Any stakeholder can set a Change- / Clarification request at any time, and the data owner can react accordingly; in case of changes to data, all subscribed stakeholders would get notified and could react according to their processes
* Full line: information flow; dotted line: physical flow
* Notifications (PUB/SUB) are only mentioned when essential for the process; further notification, e.g. for the shipper, providing a significant additional benefit through improved transparency, are not mentioned here.


### Initial Data Infrastructure

```mermaid
sequenceDiagram
    %% Jede Lifeline repraesentiert den Stakeholder inkl. seines ONE Record Endpoints
    participant Shipper as "eCommerce Shipper"
    participant Forwarder
    participant GHA as "Cargo Handling Agent"
    participant Carrier
    participant Customs
    participant Consignee
    participant CHI as "CHI Import Team"

    %% 0) Access & Subscription

    Shipper->>Forwarder: GRANT Access Delegation (CREATE Authorization)
    Forwarder->>Shipper: Register Subscription (PUB/SUB setup)
```


### Shipper´s process and data

The process starts by the Shipper providing the information on the items to be transported. Theoretically, the process could also be started by an order of the consignee, but the application of this process is unlikely, as the order of the consignee is usually not managed by the TMS.

Today, the following data fields are typically provided on a non-standardized basis, as csv, excel, non-standadized API or in an eMail:

| **Field**                             | **Value**                                      |
|--------------------------------------|------------------------------------------------|
| customer id                          | f147c4d1-a91d-49a3-a00e-74893cc9b7f8           |
| consignee id                         | 113493c5-8b04-4836-b7d8-c2fb54bb78d4           |
| shipping order id                    | d193bb65-61fa-402a-b5cf-71cd02476070           |
| external tracking code               | 63300065206929301280429                        |
| destination airport iata             | MAD                                            |
| amount                               | 22.73                                          |
| currency                             | EUR                                            |
| parcel id                            | HWMMEVJMXX3Y                                   |
| has milk powder                      | FALSE                                          |
| invoice number                       | YE21771201                                     |
| weight in g                          | 650                                              |
| has dangerous goods                  | FALSE                                          |
| width in cm                          | 9                                              |
| height in cm                         | 20                                             |
| length in cm                         | 15                                             |
| final weight in g                | 800                                            |
| dangerous goods regulations type     |                                                |
| postal code                          | 28042                                          |
| region                               |                                                |
| country                              | ES                                             |
| special handling codes               | BUP,CSL,EAW,ECC,GEN,SLY                        |
| article_sku                          | YEP_MT_01_002                                  |
| article_name                         | ALARM CLOCKS                                |
| article\_price\_amount               | 2273 |
| article\_price\_currency               | EUR |
| article_hsCode                       | 7754859                                        |
| article_quantity                     | 1                                              |
| article_articleId                    | d193bb65-61fa-402a-b5cf-71cd02476070-0         |
| article_weightInGrams               | 650                                              |
| article_countryOfOrigin             | KR                                             |

As some data is redundant (e.g. amount, currency and article\_price\_amount and article\_price\_currency), the more populated and more accurate data field was chosen (here: amount, currency).

From a conceptual side, this data is to be distributed amongst the ONE Record Logistics Objects product (i.e. iPhone 16 pro), item (a single iPhone 16 pro), and piece (15 iPhones in one Box). 

**Basic Logistic objects (places, organizations)**

tbd


**Product**

The product in ONE Record is supposed to provide the following information:
  - uniqueIdentfier
  - description
  - hsCode

In our data example, only the following data fields exist: 

|**ONE Record Logistics Object** | **Field**                              | **Value**                                      |
|---------------------------------------|---------------------------------------|------------------------------------------------|
| description | article_name                          | ALARM CLOCKS                                 |
| hsCode | article_hsCode                        | 7754859                                     |
| uniqueIdentifier | article_articleId                     | d193bb65-61fa-402a-b5cf-71cd02476070-0          |


As the current data structure doesn´t provide sufficient information for generating proper products, we will generate one product per item.  

```json
{
    "@context": {
        "@vocab": "https://onerecord.iata.org/ns/cargo#"
    },
    "@type": "product",
    "@id": "https://1r.example.com/logistics-objects/product-8cdf33e4-7629-483f-a4dd-e16c05c1630e-0",
    "hsCode": "973348",
    "description": "SWEATERS knitted",
    "describedObjects": [
    {
		 "@id": "http://{shipperDomain}/logistics-objects/item-effd84fa-60e5-4729-8b25-816423f9a715-0"
    }
}
```

Remarks:

- The id does not need to follow standardization, it must only be unique on the server. Here, the following schema was used: LO-Type - uniqueID for better transparency (e.g. "https://1r.example.com/logistics-objects/product-8cdf33e4-7629-483f-a4dd-e16c05c1630e-0").
- describedObjects contains the links to the linked items.


**Item**

Within this example, the item will provide the following information:
  - price: currency, amount
  - different IDs: articleID, customerID, consigneeID, shipping order ID, parcelID, invoiceNumber, external tracking code
  - dangerous goods indicator
  - weight / measured weight per item 
  - dimensions of item
  - country of consignee
  - country of production

In our data example, only the following data fields exist: 

| **ONE Record Logistics Object** | **Field**                 | **Value**                                    |
|----------------------------------|----------------------------|-----------------------------------------------|
| otherIdentifier                  | customer id               | f147c4d1-a91d-49a3-a00e-74893cc9b7f8          |
| otherIdentifier                  | consignee id              | 113493c5-8b04-4836-b7d8-c2fb54bb78d4          |
| otherIdentifier                  | shipping order id         | d193bb65-61fa-402a-b5cf-71cd02476070          |
| otherIdentifier                  | external tracking code    | 63300065206929301280429                       |
| numericValue                     | amount                    | 22.73                                         |
| currencyUnit                     | currency                  | EUR                                           |
| otherIdentifier                  | parcel id                 | HWMMEVJMXX3Y                                  |
| otherIdentifier                  | invoice number            | YE21771201                                    |
| grossWeight                      | weight in g               | 650                                           |
| dimensions                       | width in cm               | 9                                             |
| dimensions                       | height in cm              | 20                                            |
| dimensions                       | length in cm              | 15                                            |
| targetCountry                    | country                   | ES                                            |
| otherIdentifier                  | article_sku               | YEP_MT_01_002                                 |
| otherIdentifier                  | article_articleId         | d193bb65-61fa-402a-b5cf-71cd02476070-0        |
| productionCountry                | article_countryOfOrigin   | KR                                            |


As the current data structure doesn´t provide sufficient information for generating proper products, we will generate one product per item.  

```json
{
  "@context": {
    "@vocab": "https://onerecord.iata.org/ns/cargo#",
    "coreCodeLists": "https://onerecord.iata.org/ns/coreCodeLists#",
    "xsd": "http://www.w3.org/2001/XMLSchema#"
  },
  "@type": "Item",
  "@id": "https://1r.example.com/logistics-objects/item-d193bb65-61fa-402a-b5cf-71cd02476070-0",
  "ofProduct": [
    {
      "@id": "http://{shipperDomain}/logistics-objects/product-d193bb65-61fa-402a-b5cf-71cd02476070-0"
    }
  ],
  "grossWeight": {
    "@type": "Value",
    "value": {
      "@value": "0.65",
      "@type": "xsd:double"
    },
    "unit": {
      "@id": "coreCodeLists:MeasurementUnitCode_KGM"
    }
  },
  "unitPrice": {
    "@type": "Value",
    "value": {
      "@value": "22.73",
      "@type": "xsd:double"
    },
    "unit": {
      "@id": "coreCodeLists:CurrencyCode_EUR"
    }
  },
  "dimensions": {
    "width": {
      "@type": "Value",
      "value": {
        "@value": "15",
        "@type": "xsd:double"
      },
      "unit": {
        "@id": "coreCodeLists:MeasurementUnitCode_CMT"
      }
    },
    "height": {
      "@type": "Value",
      "value": {
        "@value": "20",
        "@type": "xsd:double"
      },
      "unit": {
        "@id": "coreCodeLists:MeasurementUnitCode_CMT"
      }
    },
    "length": {
      "@type": "Value",
      "value": {
        "@value": "9",
        "@type": "xsd:double"
      },
      "unit": {
        "@id": "coreCodeLists:MeasurementUnitCode_CMT"
      }
    }
  },
  "productionCountry": {
    "@type": "CodeListElement",
    "code": "DE",
    "codeListName": "UN/LOCODE",
    "codeListReference": "https://unece.org/trade/cefact/unlocode-code-list-country-and-territory",
    "codeListVersion": "223-1"
  },
  "targetCountry": {
    "@type": "CodeListElement",
    "code": "ES",
    "codeListName": "UN/LOCODE",
    "codeListReference": "https://unece.org/trade/cefact/unlocode-code-list-country-and-territory",
    "codeListVersion": "223-1"
  },
  "otherIdentifiers": [
    {
      "otherIdentifierType": "customer id",
      "textualValue": "f147c4d1-a91d-49a3-a00e-74893cc9b7f8"
    },
    {
      "otherIdentifierType": "consignee id",
      "textualValue": "113493c5-8b04-4836-b7d8-c2fb54bb78d4"
    },
    {
      "otherIdentifierType": "shipper order id",
      "textualValue": "d193bb65-61fa-402a-b5cf-71cd02476070"
    },
    {
      "otherIdentifierType": "external tracking code",
      "textualValue": "63300065206929301280429"
    },
    {
      "otherIdentifierType": "article_articleId",
      "textualValue": "d193bb65-61fa-402a-b5cf-71cd02476070-0"
    }
  ]
}
```


Remarks:

- As article_quantity is alway "1", there´s no need to create more instances of the same object.
- The data field ofProduct contains the link to the product, inPiece the link to the physical piece the item is included in.
- As the WeightUnit is either KGM, LBR, or ONZ in ONE Record, we have to convert the weight into KGM.

**Pieces** 

An additional level of physical consolidation are the parcels, that contain one or more items. They are boxes containing more than one In the ONE Record data model, they are pieces. 

| **ONE Record Logistics Object** | **Field**               | **Value**                          |
|----------------------------------|-------------------------|------------------------------------|
| otherIdentifiers                 | parcel id               | HWMMEVJMXX3Y                       |
| specialHandlingCode              | special handling codes  | BUP,CSL,EAW,ECC,GEN,SLY            |

```json
{
   "@context":{
      "@vocab":"https://onerecord.iata.org/ns/cargo#"
   },
   "@type":"piece",
   "@id":"https://1r.example.com/logistics-objects/piece-XXXXXXXX",
   "specialHandlingCodes":[
      {
         "@id":"https://onerecord.iata.org/ns/code-lists/SpecialHandlingCode#BUP"
      },
      {
         "@id":"https://onerecord.iata.org/ns/code-lists/SpecialHandlingCode#CSL"
      },
      {
         "@id":"https://onerecord.iata.org/ns/code-lists/SpecialHandlingCode#EAW"
      },
      {
         "@id":"https://onerecord.iata.org/ns/code-lists/SpecialHandlingCode#ECC"
      },
      {
         "@id":"https://onerecord.iata.org/ns/code-lists/SpecialHandlingCode#GEN"
      },
      {
         "@id":"https://onerecord.iata.org/ns/code-lists/SpecialHandlingCode#SLY"
      }
   ],
   "containedItems":[
      {
         "@id":"http://{shipperDomain}/logistics-objects/item-XXXXXXXX"
      }
   ],
   "otherIdentifiers":[
      {
         "otherIdentifierType":"parcel ID",
         "textualValue":"XXXXXXX"
      }
   ]
}}
```

To make data easier to understand, the prefix does not only contain the ONE Record Logistics objects type, but also the a component identifying the function of the pieces ("parcel").

At this point of time, a backlink in the item to the piece ("inPiece"-Data field) must also be set via a patch request.  


### Forwarder´s process and data


**Pieces**

The forwarder puts the parcels into boxes. In a ONE Record environment, boxes are pieces including the parcels, that are also represented as pieces.


```json
{
    "@context": {
        "@vocab": "https://onerecord.iata.org/ns/cargo#"
    },
    "@type": "piece",
    "@id": "https://1r.example.com/logistics-objects/piece-box-MXJJFNWN44",
    "containedPieces": [
    {
		 "@id": "http://{shipperDomain}/logistics-objects/piece-parcel-HWMMEVJMXX3Y",
		 "@id": "http://{shipperDomain}/logistics-objects/piece-parcel-HWMMEVJMXdd3"
    }
  ]
}
```

The backlink in the pieces must also be set in the "inPiece"-data field.


**Shipment**

As a next steps of the forwarder´s part in the process is to negotiate the AWB with the carrier and attribute the pieces to this contract as well as handing over the physical side of the shipment to the carrier. As an specific agreement for our setting, one Master AWB equals one ULD, and HAWB data structure are not used here. This is a workaround for a lack of transparency on the attribution of pieces to ULDs. ONE Record could solve this problem in a better way by reflecting the physical world with correct linking of pieces to the ULD, but as we are trying to implement the current data exchange in ONE Record, we´ll follow the given frame conditions.

The Shipment - as the physical side of the pieces under one contract - typically looks like this:


```json
{
    "@id": "http://{{forwarderDomain}}/logistics-objects/shipment-020-2222222",
    "@type": "https://onerecord.iata.org/ns/cargo#Shipment",
    "https://onerecord.iata.org/ns/cargo#totalGrossWeight":[  
        {
            "https://onerecord.iata.org/ns/cargo#numericValue":"19",
            "https://onerecord.iata.org/ns/cargo#unit":"kg"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#Pieces":
    [  
        {    
        	"@id": "https://1r.example.com/logistics-objects/piece-box-MXJJFNWN44",
        	"@id": "https://1r.example.com/logistics-objects/piece-box-MXJJFNWN45"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#Waybill":
    [  
        {
            "@id": "http://{{forwarderDomain}}/logistics-objects/waybill-020-2222222"
        }
    ]
}
```

It is also neccessary to set a backlink in the pieces, in the "ofShipment"-data field.


**Waybill**

The Waybill - as the contract - links the Shipment with the AWB-Number and Origin / Destination of the contract: 

```json
{
    "@id": "http://{{forwarderDomain}}/logistics-objects/waybill-020-2222222",
    "@type": "https://onerecord.iata.org/ns/cargo#Waybill",
    "https://onerecord.iata.org/ns/cargo#numericValue":"19",
    "https://onerecord.iata.org/ns/cargo#waybillType":"MASTER",
    "https://onerecord.iata.org/ns/cargo#waybillPrefix":"020",
    "https://onerecord.iata.org/ns/cargo#waybillNumber":"2222222",
    "https://onerecord.iata.org/ns/cargo#Shipment":
    [  
        {
            "@id": "http://{{forwarderDomain}}/logistics-objects/shipment-020-2222222"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#arrivalLocation":
    [  
        {
            "@id": "http://{{carrierDomain}}/logistics-objects/HKG"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#departureLocation":
    [  
        {
            "@id": "http://{{carrierDomain}}/logistics-objects/FRA"
        }
    ]
}
```

The backward link in the shipment must be set in the "waybill"-data field.

The WaybillLO-data can also be provided by the Carrier, but here we follow the established process.

### Carrier´s process and data

**TransportMovement**

The transportMovement reflects the transportation on the air segment. It is provided by the carrier.

```json
{
    "@id": "http://{{carrierDomain}}/logistics-objects/LH797-26-01-09",
    "@type": "https://onerecord.iata.org/ns/cargo#TransportMovement",
    "https://onerecord.iata.org/ns/cargo#distanceMeasured":[  
        {
            "https://onerecord.iata.org/ns/cargo#numericValue":"1533",
            "https://onerecord.iata.org/ns/cargo#unit":"nm"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#departureLocation":
    [  
        {
            "@id": "http://{{carrierDomain}}/logistics-objects/HKG"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#arrivalLocation":
    [  
        {
            "@id": "http://{{carrierDomain}}/logistics-objects/FRA"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#loadingActions":[  
        {
            "@id": "http://{{carrierDomain}}/logistics-objects/Loading-LH797-26-01-09"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#operatingTransportMeans":[  
        {
            "@id": "http://{{carrierDomain}}/logistics-objects/D-AIHF"
        }
    ]
}
```

In our case, the required loadingActivity is also provided by the carrier, as we assume, that the CHA is not using ONE Record yet:

```json
{
    "@id": "http://{{ghaDomain}}/logistics-objects/Loading-LH797-26-01-09",
    "@type": "https://onerecord.iata.org/ns/cargo#Loading",
    "https://onerecord.iata.org/ns/cargo#loadedUnits":[
        {
            "@id": "http://{{ghaDomain}}/logistics-objects/AKE-4711"
        }
    ],
     "https://onerecord.iata.org/ns/cargo#servedActivity":[  
        {
            "@id": "http://{{carrierDomain}}/logistics-objects/LH797-26-01-09"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#loadingType": "LOADING"
}
```

### Custom´s process and data: PLACI Check

# Pre-Loading Data Elements (7 + 1)

To enable effective air cargo security screening before departure, regulatory authorities such as the European Union (ICS2), the United States (ACAS), and other jurisdictions have introduced Pre-Loading Advance Cargo Information (PLACI) programs. These frameworks require carriers and freight forwarders to electronically submit a small but essential set of data elements about each consignment prior to loading the goods onto the aircraft. The purpose is to allow a pre-departure risk assessment, enabling customs and security agencies to identify potentially high-risk consignments without disrupting the overall cargo flow.

Rather than demanding full documentation at this early stage, PLACI initiatives rely on a minimal dataset—often referred to as the “7 + 1 data elements.” These elements represent the critical information needed to identify the parties involved, describe the goods, and connect the shipment to its specific transport leg. The “7” core elements describe the shipment itself, while the “+1” element provides the link to the transport details, ensuring that the data can be matched to a particular aircraft and flight.

The seven core data elements cover the essential identifiers for a shipment:

- Shipper name and address — identifying the original consignor responsible for sending the goods.
- Consignee name and address — identifying the intended receiver of the goods.
- Goods description — a clear, specific, and intelligible description of the cargo contents, avoiding generic terms such as “freight” or “consolidated cargo.”
- Total number of pieces — the count of individual packages or handling units within the shipment.
- Gross weight — the overall shipment weight, including packaging.
- Air Waybill number — the unique shipment identifier that links all documents and transactions.
- Country of origin and destination — derived from the shipper’s and consignee’s addresses, enabling routing and risk profiling.

The “+1” element completes the dataset by providing transport information, such as the carrier code, flight number, and planned departure date. This allows authorities to perform the screening before loading and to issue status messages like “OK to Load”, “Request for Information”, or “Do Not Load.”

For this simulation, we´ll follow the current legal requirements, although a ONE Record infrastructure will provide 

#### Trigger

##### Pub/Sub (Publish and Subscribe)

Since the FF holds the data, the Customs Authority must be registered as a Subscriber to the House Waybill.

In the case where the Forwarder needs to ensure the Customs Authority is subscribed (Publisher-initiated Subscription).

Scenario: FF Ensures Customs Subscribes to HAWB for PLACI Event Notifications

| # | Actor | Action/Object | Technical Detail (API Focus) |
|---|-------------|----------------|----------------------------------------------------|
| 1. FF Requests Subscription Information| FF (Publisher) | GET /subscriptions. | The FF retrieves the subscription details from the Customs server (Subscriber) using query parameters identifying the specific HAWB URI. |
| 2.  Customs Returns Configuration | Customs Server | 200 OK + api:Subscription | The Customs server returns the necessary Subscription object containing configuration details, including the desired api:includeSubscriptionEventType.|
| 3. FF Creates Subscription Request | FF  | POST /action-requests api:SubscriptionRequest | The FF formally registers the subscription on its own server using the details received from Customs. This registration allows the FF server to trigger future notifications. |
| 4. Notification Sent | FF Server | POST api:Notification | The FF server automatically sends an api:Notification to the Customs callback URL, alerting them to the new event. |

FF Requesting Subscription:

GET https://{{customsDomain}}/subscriptions?topicType=https://onerecord.iata.org/ns/api#LOGISTICS_OBJECT_IDENTIFIER&topic=http://{{forwarderDomain}}/logistics-objects/waybill-020-2222222
Authorization: Bearer <FF_JWT_Token>

Customs Server Response (200 OK, excerpt):

```json
{
  "@context": { "api": "https://onerecord.iata.org/ns/api#" },
  "@type": "api:Subscription",
  "api:hasTopicType": [
    { "@id": "https://onerecord.iata.org/ns/api#LOGISTICS_OBJECT_IDENTIFIER" }
  ],
  "api:hasTopic": [
    { "@value": "http://{{forwarderDomain}}/logistics-objects/waybill-020-2222222" }
  ],
  "api:hasSubscriber": [
    { "@id": "https://{{customsDomain}}/organizations/customs" }
  ],
  "api:includeSubscriptionEventType": [
    { "@id": "https://onerecord.iata.org/ns/api#LOGISTICS_EVENT_RECEIVED" },
    { "@id": "https://onerecord.iata.org/ns/api#LOGISTICS_OBJECT_UPDATED" }
  ]
}
```

FF Posts Subscription Request to its own Server

The FF registers the subscription configuration on its local server using a SubscriptionRequest.

POST https://{{forwarderDomain}}/action-requests
Accept: application/ld+json
Content-Type: application/ld+json

```json
{
  "@context": { "api": "https://onerecord.iata.org/ns/api#" },
  "@type": "api:SubscriptionRequest",
  "api:hasSubscription": [
    "@type": "api:Subscription",
	  "api:hasTopicType": [
	    { "@id": "https://onerecord.iata.org/ns/api#LOGISTICS_OBJECT_IDENTIFIER" }
	  ],
	  "api:hasTopic": [
	    { "@value": "http://{{forwarderDomain}}/logistics-objects/waybill-020-2222222" }
	  ],
	  "api:hasSubscriber": [
	    { "@id": "https://{{customsDomain}}/organizations/customs" }
	  ],
	  "api:includeSubscriptionEventType": [
	    { "@id": "https://onerecord.iata.org/ns/api#LOGISTICS_EVENT_RECEIVED" },
	    { "@id": "https://onerecord.iata.org/ns/api#LOGISTICS_OBJECT_UPDATED" }
	  ]
  ],
  "api:isRequestedBy": [
    { "@id": "https://{{forwarderDomain}}/organizations/forwarder" }
  ]
}
```

#### Access Delegation

Access Delegation grants the Customs Authority  the right to directly retrieve (pull) the complete data set required for PLACI.

| # | Actor | Action/Object | Technical Detail (API Focus) |
|---|-------------|----------------|----------------------------------------------------|
| 1. Delegation Request | FF (Delegator) | POST /action-delegations | The FF creates an AccessDelegation specifying the HAWB URI as the target object and granting api:GET_LOGISTICS_OBJECT permission to the Customs Authority organization. |
| 2. Delegation Approval | FF Server | 201 Created | The request is accepted, and access control lists (ACLs) are updated on the FF server. The request moves to api:REQUEST_ACCEPTED state. |
| 3. Data Retrieval | Customs (Delegate) | GET Logistics Object | Customs can now pull the specific HAWB/Shipment data directly from the FF’s ONE Record server when needed, ensuring access to the latest data version. |

Creating an Access Delegation Request

The FF posts the request to its own server, granting GET rights for the specific HAWB URI.

POST https://{{forwarderDomain}}/access-delegations
Content-Type: application/ld+json

```json
{
  "@context": {
    "api": "https://onerecord.iata.org/ns/api#",
    "cargo": "https://onerecord.iata.org/ns/cargo#"
  },
  "@type": "api:AccessDelegation",
	"api:hasDescription": "Require access for PLACI",	
	"api:hasPermission": [
        {
            "@id": "api:GET_LOGISTICS_OBJECT"
        }
    ],
    "api:isRequestedFor": [
        {
            "@id": "https://{{customsDomain}}/organizations/customs"
        }
    ],
    "api:notifyRequestStatusChange": True,
    "api:hasLogisticsObject": [
        {
            "@id": "http://{{forwarderDomain}}/logistics-objects/waybill-020-2222222"
        }
    ]
}
```

**Data pull**

According to the current framework, the 7+1 data elements must be provided for fulfilling pre-loading information requirements. Although ONE Record offers a lot more data at higher quality at an earlier stage, we will focus on providing these essential data fields. The additional potential is briefely described in the chapter "Further potential".

One of the assumptions is that customs will work on piece level, as this is the operationally best option.

As soon as there´s a notification on available data, the customs party in this environment will pull the following Logistics objects and process the relevant data fields:

- Piece only?
	- Shipper: PieceLO
	- C´nee: PieceLO
	- Weight: PieceLO
	- Number of Pieces: *irrelevant, as single piece reporting*
	- Goods Description / HS Code: ProductLO
	- AWB Number: WaybillLO (BUT CAN BE LINKED TO MAWB AND HAWB)
	- Transport Document Type: *ONE Record Data Set?*
	- UCR: *likely not reqd*

	
- or separated objects?


| # | Data Field | Description | ONE Record Mapping (LogisticsObject.DataField) | Example | Remark| 
|---|-------------|----------------|----------------------------------------------------|----------|----------|
| 1 | Shipper name and address | Full name and address of the original consignor responsible for sending the goods. Used to identify the origin of the shipment for risk assessment. | **piece.involvedParties** => **party.details** (party.partyRole) => **company** (company.name, company.location) | SHP, BrightWave Technologies Inc., 2450 Industrial Park Drive, Bloomington, IL 61704, US ||
| 2 | Consignee name and address | Full name and address of the intended receiver of the goods. Enables identification and screening of the receiving party. | **piece.involvedParties** => **party.details** (party.partyRole) => **company** (company.name, company.location)| CNE, Shanghai Import Co. Ltd., Pudong Blvd. 55, Shanghai, CN |
| 3 | Goods description | Clear, specific, and intelligible description of the cargo contents. Generic terms such as “freight” or “cargo” are not acceptable. | **piece.goodsDescription** | Smartphone accessories – chargers and cables |There are two options for the "Goods Description": either use the string field in the PieceLO, or use the linked Item/Product. The first option is pragmatic and easy, the second requires a more sophisticated system, but reveals an easy identification if many objects with identical nature of goods are provided. |
| 4 | Total number of pieces | Total count of individual packages or handling units in the shipment. | - | 1 | One of the assumptions is that customs will work on piece level, as this is the operationally best option.|
| 5 | Gross weight | Overall shipment weight including packaging, expressed with unit of measure. | **piece.grossWeight**| 145.0 kg |
| 6 | Air Waybill number | Unique shipment identifier at master or house level; connects all shipment data and related events. | **piece.ofShipment** => **shipment.waybill** (waybill.waybillPrefix, waybill.waybillNumber)| 020-12345675 ||
| 7 | Country of origin and destination | Derived from shipper and consignee addresses; used for routing and regulatory screening. | **piece.involvedParties** => **party.details** (party.partyRole) => **company** (company.name, company.location) | US → CN | Origian from *party.partyRole* = "SHP", destination from *party.partyRole* = CNE| 
| +1 | Transport information | Links the consignment to its actual transport leg, including carrier, flight number, and departure date. | **piece.involvedInActions** => **loading.servedActivity** => **transportMovement**( transportMovement.transportIdentifier, ransportMovement.movementTimestamp | LH8406 // 2025-10-06 | selection of correct leg via Origin: outside EU / DEST: inside  




**CheckLO for PLACI**

Pre-Loading Clearance require the 

PreArrival CheckLO

OPEN: USE OF MILESTONES

WICHTIG: Check_Name
		

```json
{
    "@id": "http://{{customsDomain}}/logistics-objects/PLACI-2399393-check",
    "@type": "https://onerecord.iata.org/ns/cargo#Check",
    "https://onerecord.iata.org/ns/cargo#checkedObjects":[
        {
            "@id": "https://1r.example.com/logistics-objects/piece-XXXXXXXX"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#checkTotalResult":[
        {
            "@id": "https://1r.example.com/logistics-objects/PLACI-2399393-result"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#checker": "1r.zoll.de",
    "https://onerecord.iata.org/ns/cargo#actionEndTime": "xxxxxx"
}
```

```json
{
    "@id": "http://{{customsDomain}}/logistics-objects/PLACI-2399393-result",
    "@type": "https://onerecord.iata.org/ns/cargo#CheckTotalResult",
    "https://onerecord.iata.org/ns/cargo#resultOfCheck":[
        {
            "@id": "http://{{customsDomain}}/logistics-objects/PLACI-2399393-check"
        }
    ],
    "https://onerecord.iata.org/ns/cargo#passed": "yes",
    "https://onerecord.iata.org/ns/cargo#checkRemark": "ACCEPTED / CLEAR"
}
```

Important: the "passed"-data field must only be "yes" if the result code "ACCEPTED / CLEAR", in all other cases, it must be "no".

**CheckLO for Customs inspection**


## Further potential

- Potential beyond 7+1: with examples
- Event for PLACI status?

## Special Cases:

Item / Piece

## Guidelines for implementation

## Glossary
see [digita-cargo/glossary](https://github.com/IATA-Cargo/ONE-Record/blob/fc8527959754a69a00fcc36d97a0c446618f435f/working_draft/API/docs/glossary.md)

## References

- ...
- ...
- ...
  
## Acknowledgements

tbd. [Philipp Billion](https://github.com/DrPhilippBillion) of Lufthansa Cargo as chairman.

Special thanks to [Niclas Scheiber](https://github.com/NiclasScheiber), Frankfurt University of Applied Sciences for preparing version 3.0.0 of the 
ONE Record core ontology in coordination with the IATA ONE Record data model focus group.

## Community

### Contribute

See [CONTRIBUTING](CONTRIBUTING.md) for more details on how to contribute on this good practice.

### Issues
Issues related to this good practice are tracked on GitHub

- [View open issues](https://github.com/digital-cargo/good-practice-shipment-tracking/issues)
- [Create a new issue](https://github.com/digital-cargo/good-practice-shipment-tracking/issues/new)

### Maintainers

> Each good practice MUST have at least one maintainer who is responsible for ongoing development and quality assurance. 
> Every maintainer MUST have commit access to the good practice repository.

- Oliver Ditz, Fraunhofer IML
- Christopher Enriquez Urban, Fraunhofer IML
- [Philipp Billion](https://github.com/DrPhilippBillion), Lufthansa Cargo

_(sorted alphabetically)_

### Contributors

> Every good practice is the result of the work of the community, and therefore the contribution of each individual should be recognized and appreciated. 
> Below is a list of all the people who have actively contributed to this good practice.

- Oliver Ditz, Fraunhofer IML
- Oliver Meschkov, CHI
- [Philipp Billion](https://github.com/DrPhilippBillion), Lufthansa Cargo
- Christopher Enriquez Urban, Fraunhofer IML

_(sorted alphabetically)_
