```mermaid
flowchart TB

subgraph NS[Oracle NetSuite - CRM and Project Initiation]
    direction TB
    NS1[Lead]
    NS2[Prospect]
    NS3[Opportunity Created]
    NS4[Project Created<br/>(documentation only, no integration trigger)]
    NS5[Rocketlane IDs on NetSuite Customer and Project]

    NS1 --> NS2 --> NS3 --> NS4 --> NS5
end

subgraph RL[Rocketlane - PSA Onboarding]
    direction TB
    RL1[Customer Exists in Rocketlane?]
    RL2[Create Customer in Rocketlane]
    RL3[Create or Upsert Project in Rocketlane]

    RL1 -->|No| RL2 --> RL3
    RL1 -->|Yes| RL3
end

NS4 -->|Trigger: Project Created| RL1
RL3 -->|Writeback Rocketlane IDs| NS5

