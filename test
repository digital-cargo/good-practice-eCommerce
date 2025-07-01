
# DTAC TPA.AP1 – ONE Record Swimlane Flow

This diagram shows a simplified end-to-end process for parcel handling, PLACI evaluation, RFID usage, and customs interaction in a ONE Record-based DTAC TPA.AP1 use case.

> ⚠️ Make sure GitHub's markdown preview or your editor supports **Mermaid diagrams**.

```mermaid
%%{init: {"theme":"default","flowchart":{"curve":"linear"}}}%%
flowchart TD
    %% Simulated swimlanes using subgraphs

    subgraph Shipper
        A1[Prepare Parcels + HCC Codes]
        A2[Send to Forwarder]
    end

    subgraph Forwarder
        B1[Transfer Parcels + Data to CHA @ Origin]
    end

    subgraph CHA_Origin
        C1[Accept Parcels]
        C2[Check PLACI Status]
        C3{PLACI OK?}
        C4[Reject Shipment]
        C5[Build Boxes]
        C6[Label Boxes (RFID + Paper)]
        C7[Transport to Zoll if required]
        C8[Return from Zoll]
        C9[Check Zollerledigung]
        C10[Build ULDs]
    end

    subgraph ONE_Record
        D1[PATCH RCS with parcel data]
        D2[Trigger PLACI Evaluation]
        D3[Store Milestones & Status]
    end

    subgraph Customs_IT
        E1[Evaluate PLACI]
        E2[Return Status]
    end

    subgraph Customs
        F1[Perform Zollbeschau]
        F2[Zollerledigung Clearance]
    end

    subgraph Carrier
        G1[A/C Loading (DEP)]
        G2[Flight]
        G3[A/C Unloading (ARR)]
    end

    subgraph CHA_Destination
        H1[Auto Scan Boxes (RFID)]
        H2[Check Zollerledigung]
    end

    subgraph Consignee
        I1[Handover to Consignee]
    end

    %% Flow connections
    A1 --> A2 --> B1 --> C1 --> C2 --> D1 --> D2 --> E1 --> E2 --> D3 --> C2
    C2 --> C3
    C3 -- No --> C4
    C3 -- Yes --> C5 --> C6 --> C10 --> G1 --> G2 --> G3 --> H1 --> H2 --> I1
    C6 --> D3
    C3 --> C7 --> F1 --> C8 --> C9 --> C10
    H2 --> F2 --> I1
```
