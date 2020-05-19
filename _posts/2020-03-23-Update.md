# Memoization

In a generic sense, when we're solving a problem over time, it's helpful for us to remember how we solved a previous part of the problem before and not have to go through the process of solving it again. 

## Writing a faster Fibonacci function

You might think about memoization in the context of doing something like writing a function to calculate the Fibonacci value of a number. 

The Fibonacci value of a natural number n greater than 1 is:

```
fibonacci(n)=(n-1)+(n-2)
```

We define the Fibonacci value of 0 as 0 and the Fibonacci value of 1 as 1. We can generate this sequence in Python up to a value we specify:

```
def fibonacci_naive(n):
	if n <= 1:
		return n
	return fibonacci_naive(n – 1) + fibonacci_naive(n – 2)
```

Every time we call `fibonacci_naive(n-1)` and `fibonacci_naive(n-2)`, we make two more function calls from our current context on the stack. If we were calculating `fibonacci_naive(8)`, we would need to calculate `fibonacci_naive(7)` and `fibonacci_naive(6)`. To calculate `fibonacci_naive(7)`, we would need to calculate `fibonacci_naive(6)` and `fibonacci_naive(5)`, and so on. We see that we would be calculating the same values multiple times, and this problem would quickly blow up once the numbers got larger.

Instead of doing that, we’re going to store the values we’ve already found so we don’t have to calculate them more than once. We’re using a dictionary to store the values as we calculate them the first time, and checking the dictionary each time to see if they’re already there. 

```
fibMap = {}
def fibonacci_memoized(n):
    if n <= 1:
        return n
    if n not in fibMap.keys():
        fibMap[n] = fibonacci_memoized(n - 1) + fibonacci_memoized(n - 2)
    return fibMap[n]
```

When I'm calculating the Fibonacci value of 36 on my machine, the slow function takes about 4 seconds and the fast function 0.00005 seconds, or about 0.001% of the time. Even for calculating relatively small Fibonacci values, the slowdown in performance of the naïve function is noticeable to the point of being prohibitive. 

Besides being able to store static values so that we don't have to calculate them over and over, it's also helpful to be able to keep recorded estimates of a value we're predicting over time so we don't have to regenerate those estimates at every calculation cycle.
