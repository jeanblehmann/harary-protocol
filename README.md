# The Harary Protocol 
## Scalable, Sybil-Resistant Anonymous Communication via Harary Graph Topologies

## Status: 

Research & Specification Phase (NGI Application)

## License: 

AGPLv3 (Planned)

## I - Overview

The Harary Protocol is a next-generation anonymous communication layer designed to solve the scalability and Sybil-resistance bottlenecks of traditional DC-Nets.

While classical Dining Cryptographers Networks (DC-Nets) offer information-theoretic anonymity (perfect sender/receiver untraceability), they fail to scale beyond small groups due to $O(N^2)$ complexity. 

The Harary Protocol addresses this by partitioning the network into manageable "Pods" connected via an inter-pod routing layer, utilizing sparse Harary Graph topologies to guarantee connectivity while minimizing overhead. 

## II - Key Innovations

### 1. Linear Scalability via Sparse Graphs

We utilize Harary graph constructions (based on the Erdős-Gallai theorem) to build the sparsest possible intra-pod topology that guarantees $k$-connectivity. This reduces communication complexity from Quadratic $O(N^2)$ to Linear $O(N)$, enabling Pods to scale to 1,000+ users.

### 2. Sybil Resistance via Economic Stake

To prevent "cheap" identities from flooding the network, we integrate a Crypto-Economic Admission Layer. Users must prove ownership of funds or stake using Ring Signatures (similar to Monero) to join a Pod. This makes Sybil attacks economically prohibitive without compromising user anonymity.

### 3. Blind Aggregation over Finite Fields

We employ a relay-based architecture where a server aggregates user inputs over a Finite Field ($\mathbb{F}_p$). This allows for high-throughput slot reservation and collision detection in $O(1)$ time, without the relay ever learning individual messages.

## III - Architecture

The system is defined by five core modules:

### 1. Intra-Pod Connectivity: 

Users form a sparse Harary graph ($H_{k,n}$) to share keys for information-theoretic security.

### 2. The Blind Relay: 

A server-side component that performs blind aggregation of inputs.

### 3. Inter-Pod Routing: 

A global Mix-Network layer where entire Pods act as mix-nodes, mathematically hiding the final recipient.

### 4. Finite Field Logic: 

A reservation system that distinguishes between Idle, Success, and Collision states algebraically.

### 5. The "Trap" Protocol: 

An automated accountability mechanism to identify jammers without halting the network. 

## IV - Comparison with State of the Art

The Harary Protocol bridges the gap between the strong privacy of DC-Nets and the usability of modern networks.

| Feature | Tor | Classical DC-Nets | Vuvuzela | **Harary Protocol** |
| :--- | :--- | :--- | :--- | :--- |
| **Anonymity Type** | Computational (Onion Routing) | Information-Theoretic | Computational (Noise) | **Information-Theoretic** |
| **Scalability** | High (Millions) | Low (<100 users) | Medium | **High-Linear $O(N)$** |
| **Latency** | Low | Low | High (Seconds/Minutes) | **Low (Algebraic Logic)** |
| **Traffic Analysis**| Vulnerable to Correlation | Resistant | Resistant | **Resistant** |
| **Sybil Defense**| Centralized Directory | None (Assumed Trust) | None | **Crypto-Economic (PoS)** |

### Key Differentiators

* **Linear Scalability:** Unlike classical DC-Nets which suffer from **Quadratic Complexity $O(N^2)$**, the Harary Protocol utilizes sparse graph topologies to achieve **Linear Complexity $O(N)$**. This allows Pods to scale to 1,000+ users without the bandwidth exploding.
* **No "Cover Traffic" Overhead:** Unlike systems like *Vuvuzela* that rely on generating massive amounts of fake noise to hide users, our protocol uses **Finite Field algebra**. Users hide within the valid traffic of the Pod, preserving bandwidth for real data.
* **Sybil Resistance:** We replace centralized directories (like Tor's authorities) with a decentralized **Proof-of-Stake Admission Layer**. Users verify themselves using ring signatures, making Sybil attacks economically prohibitive.

## V - Roadmap

This project is currently seeking funding to move from theoretical proofs (IBM Zurich Research) to a reference implementation in Rust.

### Milestone 1: 

Formal Specification & Pod Admission Logic

### Milestone 2: 

Harary Topology Generator & Python Simulation

### Milestone 3: 

Blind Relay Prototype (Rust/Go)

### Milestone 4: 

Documentation & Developer Testing  

## VI - Authors & Contact

Jean Lehmann - Cyber Capital HQ

Based on the original research conducted at the IBM Zurich Research Laboratory.

This repository serves as the home for the Harary Protocol specification and future open-source code.

The mathematical proofs for the Harary Graph topology are derived from the author's original research at IBM Zurich. 
The foundational thesis is available here: [docs/reference/Master Thesis IBM Jean Lehmann.pdf](https://github.com/jeanblehmann/DC-Net/blob/main/docs/reference/)
