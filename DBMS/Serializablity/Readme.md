## What is a Schedule?

A schedule is simply the order in which operations from different transactions are executed.

## Why Serializability?

Imagine you’re at a bank with two tellers (transactions T1 and T2) serving customers (database operations).
If both tellers try to update the same account at the same time, chaos ensues.
We want concurrency (both tellers working) but consistency (no wrong balances).

**Serializability** = The result should look like one teller finished before the other started, even if they actually worked at the same time.

> “Run transactions in parallel, but make the result look serial.”
