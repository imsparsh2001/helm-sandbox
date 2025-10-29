Example Scenario

Let’s say you want to deploy a MySQL cluster with 3 replicas.

You need:

Each MySQL pod to have its own database files (persistent)

Each pod to have a stable name (so replication works, like mysql-0, mysql-1, mysql-2)