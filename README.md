# QCMP_screening_test

## TASK 2:

```python
def simulate_odd_to_even_quantum_and_plot(n, number, shots=1000):
    # Calculate k from n, where n = 2^k
    k = math.ceil(math.log2(n))
```

##### This function simulate_odd_to_even_quantum_and_plot is the main part of the algorithm. It takes three parameters: n (the upper limit of the range), number (the number to be checked), and shots (number of shots for simulation, defaulting to 1000). It calculates the value of k based on n, where n is assumed to be a power of 2.


