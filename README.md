# Split bill
 Split bill and settlement plan in group activities



## Acknowledgement

Javascript linear programming solver: [jsLPSolver](https://github.com/JWally/jsLPSolver)



## Minimize number of transfers

(1) Notations

Define **due value** of a group member, is the value they is allocated to minus the value they has already paid. If this value is negative, they has overpaid and is the payee in the following settlement. If the value is positive, they has underpaid and is the payer in the following settlement.

Define the due value of payer is supply value, and "zero minus the due value" of payee is demand value. 

Let $m$ be the number of payers, and $n$ be the number of payees. Let $p_1, p_2, ..., p_m$ be the supply value of payers, and $q_1, q_2, ..., q_n$ be the demand value of payees.

(2) Variables

Let $x_{i,j}$ in matrix $X_{[m \times n]}$ be the value which should be transferred from the $i$-th payer to the $j$-th payee.

Let $a_{i,j} = 1$ in matrix $A_{[m\times n]}$ if the $i$-th payer should transfer to the $j$-th payee, otherwise $a_{i,j} = 0$.

(3) The objective function

The objective is to minimize the transfers in the whole settlement.

$$
\min z = \sum_{i=1}^m \sum_{j=1}^n a_{i,j}
$$

(4) Constraints

The supply constraint: 

$$
\sum_{j=1}^n x_{i,j} \leq p_i, \quad \forall i = 1, ..., m
$$

The demand constraint:

$$
\sum_{i=1}^m x_{i,j} \geq q_j, \quad \forall j = 1, ..., n
$$

If $a_{i,j} = 0$, $x_{i,j}$ can only be 0; if $a_{i, j} = 1$, $x_{i,j}$ can be sufficiently large.

$$
x_{i, j} \leq M a_{i,j}, \quad \forall i = 1, ..., m, \quad \forall j = 1, ..., n, \quad \\
M = \min(\max(p_1, ..., p_m), \max(q_1, ..., q_n))
$$

Non-negative constraint: $x_{i,j} \geq 0, \forall i = 1, ..., m, \forall j = 1, ..., n$

Binary variable constraint: $a_{i,j} \in \{0, 1\}, \forall i = 1, ..., m, \forall j = 1, ..., n$
