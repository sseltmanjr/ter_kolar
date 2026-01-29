```mermaid
flowchart TB

%% =============================
%% Rocketlane — Billing
%% =============================
subgraph RL["Rocketlane — Billing"]
  direction TB

  RL_PAD[" "]:::pad
  RL3["Project Delivery and\nBilling Workflow"]
  RL5["Invoice Created and\nApproved in Rocketlane"]

  RL_PAD --> RL3 --> RL5
end

%% =============================
%% Integration Triggers
%% =============================
TR_B["Trigger B\nPush Approved Invoice"]
TR_C["Trigger C\nSync Payment Status\nand Amount"]

%% =============================
%% Oracle NetSuite — Invoicing & AR
%% =============================
subgraph NS["Oracle NetSuite — Invoicing and AR"]
  direction TB

  NS_PAD[" "]:::pad
  NS5["Invoice Created in NetSuite"]
  NS6["Invoice PDF Sent to Customer"]
  NS7["Customer Payment Applied\nin NetSuite"]

  NS_PAD --> NS5 --> NS6 --> NS7
end

%% =============================
%% Cross-system flow
%% =============================
RL5 --> TR_B --> NS5
NS7 --> TR_C --> RL5

%% =============================
%% Styling helpers
%% =============================
classDef pad fill:transparent,stroke:transparent;
