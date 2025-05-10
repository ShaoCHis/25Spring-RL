25Spring-RL

This is 25Spring-RL Final Project Repository

# Project Title:
Intelligent and Privacy-Preserving Resource Scheduling in IoT Using Deep Reinforcement Learning

## 1. Project Background and Motivation:
The Internet of Things (IoT) connects billions of devices, ranging from sensors and mobile phones to industrial machines, all generating massive volumes of data. Efficient resource scheduling and task allocation across distributed edge and cloud systems is essential for performance and scalability in IoT networks. However, IoT environments are inherently dynamic, heterogeneous, and privacy-sensitive.

Deep Reinforcement Learning (DRL) offers a powerful mechanism to learn optimal policies through continuous interaction with the environment. However, in practice, DRL faces several challenges in IoT systems:
- Privacy concerns when raw data or model gradients are shared with the cloud.
- Scalability limitations, as most DRL models are not generalizable across multiple edge nodes.
- Coordination challenges when learning across multiple agents (devices, edge servers) with different resources and goals.

To address these issues, this project proposes a federated, collaborative DRL framework for intelligent IoT systems that:
- Learns task and resource allocation policies jointly across devices.
- Preserves user privacy using local differential privacy (LDP).
- Enables fast adaptation for new devices through centralized policy sharing.

## 2. Objectives:
- Design a collaborative DRL framework for multi-agent IoT systems that jointly learns scheduling and resource allocation policies.
- Apply federated learning to enable distributed learning without raw data sharing.
- Integrate local differential privacy mechanisms to ensure edge device privacy even under untrusted cloud servers.
- Develop a task-selection mechanism for efficient and fair training under limited cloud resources.
- Evaluate performance on multiple IoT scenarios (e.g., task offloading, resource sharing, radio scheduling).

## 3. System Architecture Overview:
Cloud–Edge–Terminal IoT Architecture:
- IoT Devices generate tasks
- Edge Hosts make DRL-based decisions on scheduling and resource use.
- Cloud Server coordinates global learning using federated updates.

Collaborative DRL Learning Process:
- Each edge agent trains a local DRL policy using local interactions.
- Periodically, edge models are shared (as noisy gradients) with the cloud.
- The cloud aggregates policies using FRL and updates a global model.
- New devices download global models and avoid long cold-start periods.

Privacy Preservation via Local Differential Privacy (LDP):
- Gradient updates are perturbed locally using Gaussian noise.
- Prevents model inversion and membership inference attacks.

## 4. Methodology:
### 4.1 DRL Modeling:
- State: Task queue, resource availability, network load.
- Action: Resource allocation decision, task scheduling, offload decision.
- Reward: Latency minimization, throughput, energy efficiency, privacy cost.

### 4.2 Federated Reinforcement Learning (FRL):
- Inspired by Kim et al. (2024), we adopt edge-agnostic policy networks.
- The cloud periodically aggregates local policies and updates global models.
- An adaptive task selection algorithm selects tasks that maximize participation and fairness.

### 4.3 Concurrent Learning with LDP:
- As in Zhou et al. (2024), edge agents add noise to gradients before uploading.
- Concurrency is achieved through joint decision-making between edge and server while preserving model privacy.

## 5. Expected Outcomes:
- A DRL-based system that autonomously learns to allocate IoT resources with minimal supervision.
- A scalable and privacy-preserving FRL protocol that ensures efficient learning without exposing user data.
- A practical solution for real-world IoT scenarios, including smart cities, smart grids, and healthcare monitoring.
- A flexible and reusable framework that can be extended to multi-task and multi-device systems.

## 6. Evaluation Plan:
Simulation Setup
- Multiple edge hosts, each managing a subset of IoT devices.
- Tasks modeled as dynamic job queues

Performance Metrics:
- Reward per episode, learning convergence, latency, system throughput.
- Privacy leakage measured via attack simulations
- Communication overhead with and without LDP.

Baselines:
- Centralized DRL without FRL.
- Federated DRL without privacy protection.
- Static scheduling policies. 
