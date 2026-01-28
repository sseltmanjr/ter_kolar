```mermaid
flowchart TB

subgraph NS[Oracle NetSuite - CRM and Invoicing]
direction TB
NS1[Lead]
NS2[Prospect]
NS3[Opportunity Created<br/>Documentation only no integration trigger]
NS4[Project Created<br/>Linked to Prospect or Customer]
NS45[Store Rocketlane IDs on<br/>NetSuite Customer and Project]
NS5[Invoice Created in NetSuite]
NS6[Invoice PDF Sent to Customer]
NS7[Customer Payment Applied in NetSuite]

NS1 --> NS2 --> NS3 --> NS4
NS5 --> NS6 --> NS7
end

subgraph RL[Rocketlane - PSA and Billing]
direction TB
RL1{Customer Exists in Rocketlane}
RL2[Create Customer in Rocketlane]
RL3[Create or Upsert Project in Rocketlane]
RL4[Delivery and Billing Workflow]
RL5[Invoice Created and Approved in Rocketlane]
RL6[Invoice and Payment Updated in Rocketlane]

RL2 --> RL3 --> RL4 --> RL5 --> RL6
end

NS4 -->|Trigger A Project Created Start Onboarding| RL1
RL1 -->|No Customer Missing| RL2
RL1 -->|Yes Customer Exists| RL3
RL3 -->|Writeback Rocketlane IDs| NS45
RL5 -->|Trigger B Push Approved Invoice| NS5
NS7 -->|Trigger C Sync Payment Status and Amount| RL6
