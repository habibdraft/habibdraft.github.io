When we're solving a problem over time, it's helpful for us to remember how we solved a previous part of the problem before and not have to go through the process of solving it again. This process is called memoization.

## Writing a faster Fibonacci function

Here's a naive recursive function to calculate the Fibonacci value of a number. 

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

Instead of doing that, we’re going to store the values we’ve already found so we don’t have to calculate them more than once. In the function below we’re using a dictionary to store the values as we calculate them the first time, and checking the dictionary each time to see if they’re already there. 

```
fibMap = {}
def fibonacci_memoized(n):
    if n <= 1:
        return n
    if n not in fibMap.keys():
        fibMap[n] = fibonacci_memoized(n - 1) + fibonacci_memoized(n - 2)
    return fibMap[n]
``` 

## Time and space complexity

The time complexity of the naive Fibonacci function is O(2<sup>N</sup>). Calling `fibonacci_naive(8)` triggers two calls to `fibonacci_naive(7)` and `fibonacci_naive(6)`. At the next recursive level of the stack, we make four calls to `fibonacci_naive(6)`, `fibonacci_naive(5)`, `fibonacci(5)`, and `fibonacci(4)`. The next level will have eight calls, and the level after that 16 calls. The space complexity is O(N) since we won't have more than N levels of calls on the stack. Once we get to `fibonacci_naive(1)`, we don't have to make any more recursive calls and the calls we've made already start returning. 

Using the memoized function, we'll only need to calculate each individual Fibonacci value once for a total of N calculations, making the time complexity O(N). Similarly, the space complexity is O(N) since we don't have to make more than N levels of calls and each level will have only one call. 

When I calculate the Fibonacci value of 36 on my machine, the slow function takes about 4 seconds and the fast function 0.00005 seconds, or about 0.001% of the time. Even for calculating relatively small Fibonacci values, the slowdown in performance of the naïve function is noticeable to the point of being prohibitive. 
