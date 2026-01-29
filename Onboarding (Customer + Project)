flowchart TB

subgraph NS[Oracle NetSuite - CRM and Project Initiation]
direction TB
NS1[Lead]
NS2[Prospect]
NS3[Opportunity Created<br/>Documentation only no integration trigger]
NS4[Project Created<br/>Linked to Prospect or Customer]
NS45[Store Rocketlane IDs on<br/>NetSuite Customer and Project]
NS1 --> NS2 --> NS3 --> NS4
end

subgraph RL[Rocketlane - PSA Onboarding]
direction TB
RL1{Customer Exists in Rocketlane}
RL2[Create Customer in Rocketlane]
RL3[Create or Upsert Project in Rocketlane]
RL1 -->|No Customer Missing| RL2
RL2 --> RL3
RL1 -->|Yes Customer Exists| RL3
end

NS4 -->|Trigger A Project Created Start Onboarding| RL1
RL3 -->|Writeback Rocketlane IDs| NS45
