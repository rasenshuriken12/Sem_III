## What is a Schedule?

A schedule is simply the order in which operations from different transactions are executed.

## Serializability

Imagine you’re at a bank with two tellers (transactions T1 and T2) serving customers (database operations).
If both tellers try to update the same account at the same time, chaos ensues.
We want concurrency (both tellers working) but consistency (no wrong balances).

*Example:*

- T1: Read(A), Write(A)
- T2: Read(A), Write(A)

A possible schedule:
- T1: Read(A) → T2: Read(A) → T1: Write(A) → T2: Write(A)

**Serializability** = The result should look like one teller finished before the other started, even if they actually worked at the same time.

> “Run transactions in parallel, but make the result look serial.”

## Serial Schedule

A serial schedule executes transactions one after another, with no interleaving.
Copy code

T1 → T2 → T3

*Example*

- T1: R(A) W(A)
- T2: R(A) W(A)

Serial order:

T1 completes fully → then T2 starts

## Non-Serial Schedule

A non-serial schedule interleaves operations of multiple transactions.
Copy code

R1(A) → R2(A) → W1(A) → W2(A)

*Example (problematic)*

- T1 reads A = 100
- T2 reads A = 100
- T1 writes 90
- T2 writes 80

Final value should be 70 → but becomes 80 ❌

| Feature | Serial | Non-Serial |Serializable | 
|--|--|--|--|
| Execution | One by one | Interleaved | Interleaved |
| Concurrency | ❌ No | ✔ Yes | ✔ Yes |
| Correctness | ✔ Always | ❌ Not guaranteed | ✔ Guaranteed
| Performance | ❌ Slow | ✔ Fast | ✔ Fast + Safe