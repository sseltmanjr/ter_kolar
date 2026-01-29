flowchart TB

subgraph RL[Rocketlane - Billing]
direction TB
RL3[Project Delivery and Billing Workflow]
RL5[Invoice Created and Approved in Rocketlane]
RL3 --> RL5
end

subgraph NS[Oracle NetSuite - Invoicing and AR]
direction TB
NS5[Invoice Created in NetSuite]
NS6[Invoice PDF Sent to Customer]
NS7[Customer Payment Applied in NetSuite]
NS5 --> NS6 --> NS7
end

RL5 -->|Trigger B Push Approved Invoice| NS5
NS7 -->|Trigger C Sync Payment Status and Amount| RL5
