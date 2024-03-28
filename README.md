# QCMP_screening_test

## TASK 2:

```python
def simulate_odd_to_even_quantum_and_plot(n, number, shots=1000):
    # Calculate k from n, where n = 2^k
    k = math.ceil(math.log2(n))
```

##### This function simulate_odd_to_even_quantum_and_plot is the main part of the algorithm. It takes three parameters: n (the upper limit of the range), number (the number to be checked), and shots (number of shots for simulation, defaulting to 1000). It calculates the value of k based on n, where n is assumed to be a power of 2.


```python
if not (1 <= number < n):
        print(f"Number {number} is outside the range [1, {n})")
        return
```

##### This condition checks if the given number is within the specified range [1, n). If not, it prints a message and returns.

```python
 if number % 2 == 0:
        print(f"Number {number} is even, returned as is.")
        return number, None
```
##### If the number is even, the function returns the number as is, since determining whether it's odd or even is trivial.

```python
    qc = QuantumCircuit(k, k)
```
##### A quantum circuit is initialized with k qubits and k classical bits.

```python
    operation = "increment" if random.choice([True, False]) or number == 1 else "decrement"
```
##### An operation ("increment" or "decrement") is randomly chosen, with a bias towards "increment" unless the number is 1.

```python
    for i in range(k):
        if number & (1 << i):
            qc.x(i)
```

##### This loop sets the qubits in the quantum circuit based on the binary representation of the number.

```python

if operation == "increment":
        qc.x(0)  # Flip LSB to increment
    elif operation == "decrement":
        qc.x(0)  # Flip LSB to decrement
```
##### Depending on the chosen operation, the least significant bit (LSB) of the quantum circuit is flipped to either increment or decrement.

```python
    qc.measure(range(k), range(k))
    print(f"Quantum Circuit for Number: {number} ({operation})")
    display(qc.draw(output='mpl'))  # Draw and display the circuit
    simulator = Aer.get_backend('qasm_simulator')
    compiled_circuit = transpile(qc, simulator)
    result = execute(compiled_circuit, simulator, shots=shots).result()
    counts = result.get_counts()
    plot_histogram(counts)
    plt.show()

```
##### Measurement is applied to all qubits. The quantum circuit is transpiled for the simulator, executed shots times, and the results are collected.


