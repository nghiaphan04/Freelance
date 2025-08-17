---
title: Freelancer Web3 Platform Diagram
---

# Freelancer Web3 Platform – System Overview

This system is designed to build a **decentralized freelance marketplace (Web3)** on the Cardano blockchain.  
The main components include:

- **User**:  
  - **Client**: Posts projects, funds escrow, and can raise disputes.  
  - **Freelancer**: Registers, stakes a deposit, and can also raise disputes when necessary.

- **Platform (Web3 Freelance Platform)**:  
  Acts as the core layer that connects clients and freelancers, manages escrow contracts, and routes dispute processes.

- **AI Verification**:  
  Provides identity and reputation services through face/ID verification, reputation scoring, job recommendations, and vote suggestions.  
  Connected to the **DID Contract** for decentralized identity verification recorded on-chain.

- **Escrow Reward**:  
  Manages the **Escrow Contract** and the **Reward Pool Contract**, ensuring that project funds and staking rewards are securely handled.

- **Governance**:  
  A **DAO / Expert Arbitrators Contract** is responsible for dispute resolution and governance, ensuring fair and transparent decision-making.

- **Blockchain (Cardano)**:  
  All DID records, escrow deposits, rewards, and DAO governance are executed and verified on the Cardano blockchain for security, transparency, and decentralization.

```mermaid
flowchart LR

%% ========== USER ==========
subgraph User
    Client[Client]
    Freelancer[Freelancer]

    Client -->|Post Projects / Fund Escrow| Platform
    Client -->|Request Dispute| Platform

    Freelancer -->|Register / Stake Deposit| Platform
    Freelancer -->|Request Dispute| Platform
end

%% ========== PLATFORM ==========
subgraph Platform
    Web3[Web3 Freelance Platform]
end

%% ========== AI VERIFICATION ==========
subgraph AI_Verification["AI Verification"]
    AI[AI Engine\nFace/ID Verification\nReputation Scoring\nJob Matching\nVote Suggestion]
    Jobs[Suggest Jobs]
    Vote[Suggest Vote / Recommendations]
    DID[DID Contract]

    AI --> Jobs --> Freelancer
    AI --> Vote --> Governance
    AI --> DID --> Blockchain
end

%% ========== ESCROW REWARD ==========
subgraph Escrow_Reward["Escrow Reward"]
    Escrow[Escrow Contract]
    Reward[Reward Pool Contract]
end

%% ========== GOVERNANCE ==========
subgraph Governance
    DAO[DAO / Expert Arbitrators Contract]
end

%% ========== BLOCKCHAIN ==========
subgraph Blockchain
    Cardano[Cardano Blockchain]
end

%% ========== CONNECTIONS ==========
Platform --> Web3
Platform --> Escrow
Platform --> DAO

Escrow --> Reward
Reward --> DAO

Escrow --> Cardano
Reward --> Cardano
DAO --> Cardano

DID --> Cardano
