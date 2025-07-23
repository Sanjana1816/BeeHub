# BeeHub: The Private, Federated Knowledge System

**BeeHub is a peer-to-peer knowledge management system built from first principles in C++ for absolute data sovereignty and private, intelligent collaboration. It enables trusted groups to create a collective knowledge base that is verifiably secure, resilient, and entirely owned by them.**

This project evolved in three distinct phases, from a secure local datastore to a distributed system powered by a federated, on-device AI, implementing advanced GenAI concepts from the ground up.

---

## V1: The Personal, Verifiable Datastore (The Fortress)

The MVP's goal was to build a bulletproof, single-user system that delivers on the core promise of trust and verifiability. This foundational layer was built entirely in C++.

### Key Features
*   **Content-Addressable Storage:** Data is chunked, hashed, and stored based on its content on top of a RocksDB foundation.
*   **Fully Encrypted:** Every data chunk is encrypted at rest using industry-standard cryptography (libsodium).
*   **The Verifiable Log (Hash Chain):** Every write operation is a transaction that is cryptographically chained to the previous one, creating a tamper-proof log of all changes.
*   **Merkle Tree Snapshots:** The entire state of the database is represented by a single Merkle root hash for efficient verification.

### Core Tech Stack
| Category | Technology | Purpose |
|:---|:---|:---|
| **Language** | C++ | For high-performance, low-level systems programming. |
| **Datastore** | RocksDB | High-performance embedded key-value store. |
| **Cryptography** | libsodium | Secure cryptography for identity, encryption, and hashing. |

### Project Deadline
October/2025

---

## V2: The Distributed, Self-Healing Team Knowledge Base (The Network)

V2 connected the secure fortresses of V1 into a resilient, decentralized network that automatically synchronizes and can withstand failure.

### Key Features
*   **Peer-to-Peer Gossiped Sync:** Nodes discover each other and securely exchange data using a custom P2P protocol built with Boost.Asio.
*   **End-to-End Encrypted Comms:** All communication between peers is fully end-to-end encrypted.
*   **Efficient Merkle Reconciliation:** When a node reconnects, it syncs *only the data it missed* by comparing Merkle roots with its peers.
*   **Polished Desktop UI:** A desktop application (Qt/Electron) was introduced for a seamless user experience.

### Core Tech Stack
| Category | Technology | Purpose |
|:---|:---|:---|
| **Networking** | Boost.Asio | Building the custom P2P gossip and sync protocols. |
| **Data Integrity**| Merkle Trees | For highly efficient, verifiable state reconciliation. |
| **UI** | Qt / Electron | A polished desktop client for user interaction. |

---

## V3: The Intelligent, Federated Knowledge System (The Hive Mind)

The final version makes the distributed knowledge base intelligent. It implements a private, federated **AI Agent** and **Retrieval-Augmented Generation (RAG)** system entirely in C++, using a local LLM.

### Key Features
*   **Private AI Engine:** Integrated **llama.cpp** to run a powerful Large Language Model (LLM) *locally* on the user's own machine.
*   **Custom Federated RAG Engine:** BeeHub implements a distributed **RAG** system from scratch. The system retrieves context by querying trusted peers on the network, all without a central database.
*   **Custom C++ AI Agent:** An **AI Agent**, built in C++, orchestrates the entire process. It decomposes a user's complex question into a **dynamic chain of tasks**:
    1.  Generate sub-queries.
    2.  Broadcast them to the federated RAG engine.
    3.  Gather the encrypted results.
    4.  Augment a final prompt with the retrieved context.
    5.  Query the local LLM for synthesis.
*   **Zero Data Leakage:** The entire RAG and Agent workflow happens on the users' own devices, ensuring absolute privacy.

### Core GenAI & Tech Stack
| Category | Technology | Purpose |
|:---|:---|:---|
| **AI - Architecture** | **Custom Federated RAG Engine** | A from-scratch C++ implementation of the RAG pattern for a distributed network. |
| **AI - Orchestration**| **Custom C++ AI Agent & Chains** | Custom logic to manage the state and dynamic chain of tasks for federated queries. |
| **AI - Reasoning** | **llama.cpp (Local LLM)** | The on-device brain for private query synthesis. |
| **Core** | C++, Boost.Asio, etc. | (Foundation Unchanged) |