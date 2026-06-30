# Production-Ready PostgreSQL 16 HA Cluster with repmgr

This repository contains step-by-step documentation and configuration guidelines for deploying a highly available **PostgreSQL 16** database cluster with **repmgr** (Replication Manager) for automatic failover on Ubuntu servers.

---

## 🏗️ Cluster Architecture

The cluster consists of 3 dedicated virtual machines acting in a Primary-Standby architecture with automated failover tracking:
[ Client Application ]

                │
                ▼

   ┌─────────────────────────┐
   │   Node 1: Primary       │
   │   (Read / Write)        │
   └───────────┬─────────────┘
               │
     ┌─────────┴─────────┐
     ▼                   ▼
┌─────────────────┐ ┌─────────────────┐
│ Node 2: Standby │ │ Node 3: Standby │
│   (Read Only)   │ │   (Read Only)   │
└─────────────────┘ └─────────────────┘
