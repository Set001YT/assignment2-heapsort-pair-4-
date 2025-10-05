# Assignment 2: Heap Data Structures (Pair 4)
# Max-Heap Implementation

This is my implementation of a Max-Heap for Assignment 2. It's a binary heap where the biggest element is always at the top.

## What is this?

A Max-Heap is basically a tree stored in an array. The rule is simple: every parent must be bigger than its kids. This means finding the maximum takes zero time - it's always at position 0.

### Main operations:

| What it does | How long it takes |
|-------------|-------------------|
| `insert(value)` | O(log n) |
| `extractMax()` | O(log n) |
| `increaseKey(index, newValue)` | O(log n) |
| `peek()` | O(1) |

## Getting started

You'll need:
- Java 11 or newer
- Maven

```bash
# Clone and build
git clone https://github.com/your-username/max-heap-implementation.git
cd max-heap-implementation
mvn clean install

# Run tests
mvn test

# Run benchmarks
mvn exec:java -Dexec.mainClass="cli.BenchmarkRunner"
```

## Project structure

```
src/
├── main/java/
│   ├── algorithms/MaxHeap.java           # The actual heap
│   ├── metrics/PerformanceTracker.java   # For counting operations
│   └── cli/BenchmarkRunner.java          # Testing performance
└── test/java/
    └── algorithms/MaxHeapTest.java       # 30+ unit tests
```

## How to use it

### Basic example

```java
MaxHeap heap = new MaxHeap();

// Add some numbers
heap.insert(10);
heap.insert(30);
heap.insert(20);

// Check the max (doesn't remove it)
System.out.println(heap.peek()); // prints 30

// Take out the max
int max = heap.extractMax(); // returns 30

// Make a value bigger
heap.increaseKey(0, 50); // element at index 0 becomes 50
```

### With performance tracking

```java
MaxHeap heap = new MaxHeap();
PerformanceTracker tracker = new PerformanceTracker();

tracker.startTimer();

for (int i = 0; i < 1000; i++) {
    heap.insert(i, tracker);
}

tracker.stopTimer();
tracker.printStats();  // Shows comparisons, swaps, time
```

## Tests

I wrote 30+ tests covering everything:
- Normal operations
- Edge cases (empty heap, single element, duplicates)
- The increase-key operation
- Large datasets (100,000 elements)
- Random vs sorted data

Run them with `mvn test`.

## How it works (complexity)

The heap is stored in an array. For any element at index i:
- Parent is at `(i-1)/2`
- Left child is at `2i+1`
- Right child is at `2i+2`

**Time complexity:**
- Insert: Add at end, bubble up. Takes O(log n) because tree height is log n.
- ExtractMax: Remove root, put last element there, bubble down. Also O(log n).
- IncreaseKey: Update value and bubble up if needed. O(log n).
- Peek: Just return first element. O(1).

**Space:** Uses O(n) space for n elements. Array grows by 1.5x when full.

## Performance results

Tested on my laptop (Intel i5, 8GB RAM):

| Elements | Insert | ExtractMax | IncreaseKey |
|----------|--------|------------|-------------|
| 100      | < 1 ms | < 1 ms     | < 1 ms      |
| 1,000    | 2 ms   | 3 ms       | 1 ms        |
| 10,000   | 25 ms  | 35 ms      | 15 ms       |
| 100,000  | 350 ms | 500 ms     | 200 ms      |

## Real-world uses

Max-heaps are everywhere:
- **Task scheduling** - run highest priority task first
- **Heap sort** - efficient sorting algorithm
- **Finding top K elements** - like "top 10 highest scores"
- **Event processing** - handle events by priority
- **Graph algorithms** - used in some shortest path algorithms

## My approach

I started with the basic insert and extract operations, then added increase-key. The trickiest part was making sure the heap property stays valid after every operation.

I added a performance tracker because I wanted to see exactly how many comparisons and swaps happen. Turns out insert does about 50% fewer comparisons than the theoretical worst case - makes sense since elements don't always bubble all the way to the top.

## What I learned

- The math actually works out - O(log n) is real
- Testing edge cases is super important (empty heap, single element, etc.)
- Constant factors matter - even O(1) operations add up
- Array-based heaps are way faster than pointer-based trees

## Author

Asset Iglikov SE-2434 
GitHub: [@Set001YT](https://github.com/Set001YT)

---

Built for Design & Analysis of Algorithms course, 5 October 2025
