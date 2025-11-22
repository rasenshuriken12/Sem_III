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
