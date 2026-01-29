```mermaid
flowchart LR

%% -----------------------------
%% Oracle NetSuite (left)
%% -----------------------------
subgraph NS["Oracle NetSuite — CRM and Project Initiation"]
  direction TB

  NS_PAD[" "]:::pad
  NS1["Lead"]
  NS2["Prospect"]
  NS3["Opportunity Created"]
  NS4["Project Created\nDocumentation only — no integration trigger"]
  NS5["Rocketlane IDs on NetSuite\nCustomer and Project"]

  NS_PAD --> NS1 --> NS2 --> NS3 --> NS4 --> NS5
end

%% -----------------------------
%% Rocketlane (right)
%% -----------------------------
subgraph RL["Rocketlane — PSA Onboarding"]
  direction TB

  RL_PAD[" "]:::pad
  RL1{"Customer exists in\nRocketlane?"}
  RL2["Create customer in Rocketlane"]
  RL3["Create or upsert project in Rocketlane"]

  RL_PAD --> RL1
  RL1 -->|No| RL2 --> RL3
  RL1 -->|Yes| RL3
end

%% -----------------------------
%% Cross-system integration lines
%% -----------------------------
NS4 -->|"Trigger: Project Created"| RL1
RL3 -->|"Write back Rocketlane IDs"| NS5

%% -----------------------------
%% Styling helpers
%% -----------------------------
classDef pad fill:transparent,stroke:transparent;
