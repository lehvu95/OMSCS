# Unit 2 — Runtime and Big-O Notation

> Source: https://www.cs.cmu.edu/~15110/practice/unit2/runtime-bigO.html — CMU 15-110, Unit 2 practice problems.

[15.1] What is the Big-O notation of an algorithm whose runtime doubles with each additional element in the input set?

A. O(n)

B. O(n^2)

C. O(log n)

D. O(2^n)

**Answer:** O(2^n)

[15.2] What is the best case for linear search? What is the worst case for linear search?

What's the best case for linear search? Answer: a list where the item we search for is in the first position

What's the worst case for linear search? Answer: a list where the item we search for is not in the list.

[15.3] An algorithm that checks each element of a list against every other element has a Big-O notation of _______.

**Answer:** O(n^2)

[15.4] Explain why an algorithm with O(1) complexity is referred to as having constant time complexity.

**Answer:** An O(1) complexity algorithm is referred to as having constant time complexity because its runtime remains constant regardless of the size of the input data. The execution time does not increase as the input size increases.

[15.5] Consider the following code snippet. What is the time complexity?

    i = 1
    while i < n:
        i = i * 2

**Answer:** The time complexity is O(log n) because i doubles each time, meaning the loop's iterations grow logarithmically with respect to n.

[15.6] What is the Big-O notation for an algorithm that makes two separate passes through a list of n elements?

**Answer:** O(n) (Linear time complexity; the constant factor 2 is ignored in Big-O)

[15.7] Given the following Python function, what is its Big-O complexity?

    def find_pairs(numbers, target_sum):
        count = 0
        for i in range(len(numbers)):
            for j in range(5, len(numbers)):
                if numbers[i] + numbers[j] == target_sum:
                    count += 1
        return count

**Answer:** O(n^2) Nested loop, each for loop runs n times, so in total n^2. The body of the loop, is O(1)

[15.8] Why is the worst-case time complexity often more significant than the best-case complexity when analyzing algorithms?

**Answer:** The worst-case time complexity is more significant because it provides an upper bound on the time an algorithm will take to complete, ensuring that the algorithm's runtime will not exceed this bound regardless of the input size or conditions. It helps in understanding the scalability and efficiency of the algorithm under the most demanding scenarios.

[15.9] Given the following Python function, what is its time complexity?

    def process_data(data):
        total = 0
        for i in range(0, len(data), 2):  # increment by 2
            total += data[i]
        return total

**Answer:** The time complexity is O(n/2) which simplifies to O(n), as the function iterates through approximately half of the elements in the input list, but in Big-O notation, we drop constant factors.

[15.10] The Big-O notation O(n^2 + n) simplifies to O(n^2)? True or False?

**Answer:** True (In Big-O notation, lower-order terms are dropped as they become insignificant for large n.)

[15.11] Is the Big-O notation used to express the best-case performance of an algorithm?

**Answer:** No (Big-O notation is generally used to describe the upper bound or worst-case performance of an algorithm, not the best-case scenario.)

[15.12] Given the following Python function, what is its time complexity?

    def varied_loops(n):
        count = 0
        for i in range(n):
            for j in range(1, 100):
                count += 1
        return count

**Answer:** O(n) (The number of iterations in the inner loop is constant, while the outer loop runs in n. In total, the runtime is n * 1 = O(n))

[15.13] Given the following Python function, what is its time complexity?

    def mixed_operations(n):
        sum = 0
        for i in range(n):
            sum += i
            k = n
            while k > 0:
                k //= 2
        return sum

**Answer:** O(n log n) (The for loop runs in O(n) time, and the inner while loop runs in O(log n) time for each iteration of the for loop. So total, O(n log n))

[15.14] Given the following recursive Python function, what is its time complexity?

    def recursive_function(n):
        if n == 1:
            return n
        else:
            return recursive_function(n - 1)

**Answer:** O(n) (In total, the recursive function is called n times, thus the runtime is O(n))

[15.15] Given the following recursive Python function, what is its time complexity?

    def recursive_function(n):
        if n <= 1:
            return n
        else:
            return recursive_function(n - 1) + recursive_function(n - 2)

**Answer:** O(2^n) (This is a Fibonacci sequence calculation, which has an exponential time complexity because it generates two recursive calls for each call.)

[15.16] Given the following recursive Python function, what is its time complexity?

    def complex_loops(n):
        total = 0
        for i in range(n):
            for j in range(n):
                for k in range(n):
                    total += i * j * k
        return total

**Answer:** O(n^3) (Each of the loops runs in O(n), but they are nested so total of O(n^3))

[15.17] Given the following Python function, what is its time complexity?

    1. def sumEvens(lst): # n = len(lst)
    2.    result = 0
    3.    for i in range(len(lst)):
    4.        if lst[i] % 2 == 0:
    5.          result = result + lst[i]
    6.    return result

**Answer:**

- Line 2, 4, 5 and 6 are constant.
- LLine 3 is a for loop which runs in linear time O(n)
- Runtime: constant + n * (constant + constant + constant) = O(n)

[15.18] Given the following Python function, what is its time complexity?

    1: def example(lst): # n is len(lst)
    2:      result = []
    3:      for i in range(0, len(lst), 2):
    4:          if lst[i] != lst[i+1]:
    5:              average = (lst[i] + lst[i+1]) / 2
    6:              if average in lst:
    7:                  result.append(average)
    8:      return count

**Answer:**

- Line 3 iterates n/2 times – we should multiply that by the work done by the loop body.
- Line 4 is a conditional with a constant check – add it to the rest of the loop body.
- Line 6 is a conditional with a O(n) check – add n to the rest of the body.
- Lines 2, 5, 7, and 8 don't depend on the size of the input; they're constant actions.
- Runtime: constant + n/2 * (constant + constant + n + constant) = constant + constant * (n^2) + constant * n = O(n^2)

[15.19] Given the following recursive Python function, what is its time complexity?

    def countdown(n): # n = n
     if n <= 0:
        print("Finished!")
     else:
        print(n)
        countdown(n - 5)

**Answer:** The runtime for recursive functions depends on the number of recursive calls the function will need to make. For example, for the function above, if you call the function on 100, it will make the next call on 95, then 90, etc; 20 total calls will be made. If you double the input, 40 calls will be made. The function is O(n).

[15.20] What is the runtime of the following code block?

    def swap(lst, i, j): # n = len(lst)
     tmp = lst[i]
     lst[i] = lst[j]
     lst[j] = tmp

**Answer:** This algorithm is constant time or O(1); its time does not change with the size of the input.

[15.21] What is the runtime of the following code block?

    def countDigits(n): # n = n
     count = 0
     while n > 0:
        n = n // 15
        count = count + 1
     return count

**Answer:** Every time you increase n by a factor of 15, you run the loop one more time. All the operations in the loop are constant time.
Similar to binary search, the algorithm is logarithmic time, or O(log n).
Why? O(log 2n) = O(log n) + 1 - you add one action per doubling of the input.
Even though this is log 15 (n), we don't include the base in the Big-O notation because a change of base is just a multiplicative factor

[15.22] What is the runtime of the following code block?

    def count(n): # n = n
     for i in range(n, 0, -10):
        print(i)

**Answer:** This code will loop n/10 times overall. If we double the size of n, how many more times do we go through the loop?
We double the number of times through the loop. That is linear time, or O(n), as it is proportional to the size of n. Stepping by 10 doesn't change the function family.

[15.23] What is the runtime of the following code block?

    def example(x): # n = x
     x = x + 5
     y = x + 2
     print(x, y)

**Answer:** If you have statements that run sequentially, the runtime for each statement is added to the total runtime. This happens because each new statement adds another amount of time.

    def example(x): # n = x
     x = x + 10005 # O(1)
     y = x + 2345 # O(1)
     print(x, y) # O(1)

     # Total: O(1)

[15.24] What is the runtime of the following code block?

    def printContains(lst, x): # n = len(lst)
     result = linearSearch(lst, x)
     print(x, "in lst?", result)

**Answer:** Linear Search runs in O(n)! All the other statements run in O(1) so in total, O(n).

    def printContains(lst, x): # n = len(lst)
     result = linearSearch(lst, x) # O(n)
     print(x, "in lst?", result) # O(1)

     # Total: O(n)

[15.25] What is the runtime of the following code block?

    def printContains(lst, x): # n = len(lst)
     result = binarySearch(lst, x)
     print(x, "in lst?", result)

**Answer:** Binary Search runs in O(log n)! All the other statements run in O(1) so in total, O(log n).

    def printContains(lst, x): # n = len(lst)
     result = binarySearch(lst, x) # O(log n)
     print(x, "in lst?", result) # O(1)

     # Total: O(log n)

[15.26] What is the runtime of the following code block?

    def countAll(lst): # n = len(lst)
     for i in range(len(lst)):
        count = lst.count(i)
        print(i, "occurs", count, "times")

**Answer:** The function `count` runs in O(n). The for loop also runs in O(n). Thus total, O(n^2).

    def countAll(lst): # n = len(lst)
     for i in range(len(lst)): # n repetitions
        count = lst.count(i) # O(n)
        print(i, "occurs", count, "times") # O(1)
    # Total: O(n^2)

