📊 Detailed Comparison
Feature	| Savepoint	| Checkpoint
|-|-|-|
Purpose	| To roll back part of a transaction	| To speed up crash recovery
Scope	| Within a single transaction	| Entire database system
Who Controls	| Application Programmer (user)	| DBMS (system)
Syntax	| SAVEPOINT point_name; ROLLBACK TO point_name;	| Automatic or admin-triggered
Persistence	| Temporary - exists only during transaction |	Permanent - written to disk


📊 Conflict Serializability vs View Serializability
Aspect	|  Conflict Serializability	| View Serializability
|--|--|--|
Definition	| Schedule can be transformed to serial schedule by swapping non-conflicting operations	| Schedule has the same view as some serial schedule
Basis	| Based on conflicting operations	| Based on read-write dependencies
Flexibility |	Stricter - fewer schedules qualify	| More flexible - more schedules qualify
Blind Writes |	Not allowed	| Allowed
Testing Method	| Precedence graph (check for cycles)	| Polygraph or view equivalence rules
Performance	| Easier to check	| Harder to check (NP-complete)

Ref: [Gate Smashers Lec 82](https://youtu.be/s8QlJoL1G6w?si=QZqc1YWRXkQf18Rj), 83, 84, 85

🎯 Step-by-Step Rules for Solving Serializability Problems
📊 METHOD 1: Conflict Serializability (Using Precedence Graph)
Step 1: Identify All Operations
List all read/write operations with their transaction numbers.

Example Schedule:

text
T1: R(A), W(A), R(B), W(B)
T2: R(A), W(A), R(C), W(C)
T3: R(B), W(B), R(C), W(C)
Step 2: Find Conflicting Pairs
Look for RW, WR, WW on same data item between different transactions.

Conflicts found:

T1→T2: W(A) conflicts with R(A) and W(A)

T1→T3: W(B) conflicts with R(B) and W(B)

T2→T3: W(C) conflicts with R(C) and W(C)

Step 3: Draw Precedence Graph
Create nodes for each transaction

Add edges for conflicts

text
T1 → T2 (due to A)
T1 → T3 (due to B)  
T2 → T3 (due to C)
Step 4: Check for Cycles
If no cycles → Conflict Serializable

If cycles exist → Not Conflict Serializable

Result: ✅ No cycles = Conflict Serializable

👁️ METHOD 2: View Serializability (3 Rules Check)
Step 1: Check Initial Read Rule
If Ti reads initial value of X in original schedule, it must read initial value in serial schedule too.

Step 2: Check Read-Write Dependency
If Ti writes X before Tj reads it in original, same order in serial.

Step 3: Check Final Write Rule
Transaction doing final write on X in original must do final write in serial.
