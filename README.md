# Using Grover’s Algorithm for factorisation of bi-primes
## Submitted by Sukrit Jindal (sukjingitsit) [22125037, DSAI]

### Overview of the Algorithm
Factorization of bi-primes is an important problem in mathematics and cryptography, and is the basis of the most widely used encryption scheme, viz. RSA. The success of RSA relies on the practical difficulty in solving the factorization of bi-primes efficiently. While classically, this problem requires time-consuming algorithm, the introduction of quantum computing presents certain advantages over the classical scheme.

In quantum computing, Grover's algorithm is a search algorithm which efficiently searches for a 'marked state' in O(√N) queries. This is a considerable speedup over the classical O(N). It searches for the correct state by relying on an oracle function which applies a phase shift of π to the correct states, and keeping the rest unchanged. Thereafter, a diffuser is used to amplify the magnitude of the correct states and diffuse the magnitude of the rest.

For the case of bi-prime factorization, we maintain two registers (p and q) for the factors of the bi-primes. These registers are initialised in a superposition indicating the equal probability of all states. We also maintain a register z as a temporary register. The oracle then multiplies the registers of p and q and stores the result in z. It then flips the bits corresponding to a product of N, and uncomputes the multiplication to reset z. After this, the diffuser for Grover search is applied and the process is repeated an O(√N) times for convergence.

Finally, the probabilities of each state in p and q is calculated and the two maximal values correspond to the prime factors of the bi-prime (one in case the bi-prime is the square of a prime).

### About the Code

The code is commented and annotated, and each step of the code is explained properly. Before running the code, make sure to specify the number to be factored as N. This number should be a bi-prime to ensure the correctness of the algorithm, else it may have errors. The dependencies required for this code are Pennylane, Matplotlib and Numpy alongside the in-built Python library math. The code runs well for the case of 35 and 115, albeit the convergence is very slow for 893.

### Potential Optimizations
The algorithm can be optimized further by reducing the number of bits used to store p and q to an optimal size which allows them to store the divisors of p and q by utilising the fact that the number of bits to represent p should be less than or equal to half the bits. Further, we can also optimize the algorithm using the result derived in the paper Quantum Factoring Algorithm using Grover Search.
