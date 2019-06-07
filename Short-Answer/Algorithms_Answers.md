Add your answers to the Algorithms exercises here.

```
a)  a = 0                     ---  O(1)
    while (a < n * n * n):    ---  [depends on how a iterates]
      a = a + n * n           ---  a is iterating at n^2


      if n=2:
         will loop  2 times
      if n=4:
        n**3 = 64
        first loop a = 16
        second loop a = 32
        third loop a=48
        fourth loop a =64 **end loop**


answer: the runtime complexity of this code is O(n) because as n gets larger is needs n amount of loops to break out of the while loop
```

```
b)  sum = 0                               -- O(1)
    for i in range(n):                    -- O(n)
      i += 1                              -- O(1)
      for j in range(i + 1, n):           -- O(n)
        j += 1                            -- O(1)
        for k in range(j + 1, n):         -- O(n)
          k += 1                          -- O(1)
          for l in range(k + 1, 10 + k):  -- 0(1) (always looping                               10 times regardless of n)
            l += 1                       -- O(1)
            sum += 1                      -- O(1)

            1 + (n * 1 * (n * 1) * (n * 1) * 1 * 1 * 1)

    answer: This will run with O(n^3) time complexity since there is a loop through n which is nested in a loop through n whic is also nested in a loop through n. The final loop will always run 10 times regardless of what n is so it can be considered a constant
```

```
c)  def bunnyEars(bunnies):
      if bunnies == 0:      -- O(1)
        return 0            -- O(1)

      return 2 + bunnyEars(bunnies-1)      --O(n)


      answer: this will run with O(n) runtime complexity because the recursive function will be called n amount of times. If bunnies = 1 on the original call it will end up calling itself 1 additional time. If the main funtion is called with bunnies = 4, it will call itself recursively 4 additional times. This is a linear relationship.
```

## Exercise II

Suppose that you have an _n_-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor _f_ or higher, and doesn't get broken if dropped off a floor less than floor _f_. Devise a strategy to determine the value of _f_ such that the number of dropped eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode and give the runtime complexity of your solution.

```
answer:
Assuming we don't already know that in real life an egg will crack if dropped from about 6 inches, I think the best approach to this hypothetical situation would to search for _f_ in a similar manner as a binary search.

low = 0
high = n
mid = n // 2

while low <= high:
    go to mid and drop egg
    if egg breaks: (we are too high)
        high = mid - 1
        mid = high - low // 2
    if egg does not break: (we are not high enough)
        low = mid + 1
        mid = high - low // 2

repeat this until we narrow it down two floors:
    -if the final two sequences are Break then No Break, then we know f is the latter floor

    -if the final two sequences are No Break and then Break, then we know f is the former floor

This would have a runtime complexity of O(log n) since the field of possible correct answers is being halved on every loop

```
