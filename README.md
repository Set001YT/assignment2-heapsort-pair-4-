# assignment2-heapsort-pair-4-
# Max-Heap Implementation

Implementation of **Max-Heap** data structure with `increase-key` and `extract-max` operations for Assignment 2.

## Description

Max-Heap is a complete binary tree where each parent is greater than or equal to its children. The maximum element is always at the root.

### Core Operations:

| Operation | Description | Complexity |
|----------|----------|-----------|
| `insert(value)` | Insert element | O(log n) |
| `extractMax()` | Extract maximum | O(log n) |
| `increaseKey(index, newValue)` | Increase element value | O(log n) |
| `peek()` | View maximum without removal | O(1) |


### Requirements
- Java 11+
- Maven 3.6+

### Installation

```bash
# Clone repository
git clone https://github.com/your-username/max-heap-implementation.git
cd max-heap-implementation

# Build project
mvn clean install

# Run tests
mvn test

# Run benchmarks
mvn exec:java -Dexec.mainClass="cli.BenchmarkRunner"
```

## 📁 Project Structure

```
assignment2-heapsort-pair-4/
├── src/
│   ├── main/java/
│   │   ├── algorithms/
│   │   │   └── MaxHeap.java              # Core implementation
│   │   ├── metrics/
│   │   │   └── PerformanceTracker.java   # Metrics collection
│   │   └── cli/
│   │       └── BenchmarkRunner.java      # CLI for benchmarks
│   └── test/java/
│       └── algorithms/
│           └── MaxHeapTest.java          # Unit tests
│                      
├── docs/
│   ├── analysis-report.pdf               # Partner's analysis report
│   └── performance-plots/                # Performance graphs & CSV results
├── README.md                             # summary of my work and linking to the report.
└── pom.xml
```

## 💡 Usage Examples

### Basic Usage

```java
MaxHeap heap = new MaxHeap();

// Insert elements
heap.insert(10);
heap.insert(30);
heap.insert(20);

// View maximum
System.out.println(heap.peek()); // Output: 30

// Extract maximum
int max = heap.extractMax(); // Returns 30
System.out.println(max);

// Increase key
heap.increaseKey(0, 50); // Increase element at index 0 to 50
```

### With Metrics Tracking

```java
MaxHeap heap = new MaxHeap();
PerformanceTracker tracker = new PerformanceTracker();

tracker.startTimer();

// Insert elements with tracking
for (int i = 0; i < 1000; i++) {
    heap.insert(i, tracker);
}

tracker.stopTimer();

// Print statistics
tracker.printStats();

// Export to CSV
tracker.exportToCSV("results.csv", 1000);
```

##  Testing

The project includes **30+ unit tests** using JUnit 5, covering:

- ✅ Basic operations (insert, extractMax, peek)
- ✅ Increase-key operation
- ✅ Edge cases (empty heap, single element, duplicates)
- ✅ Max-heap property correctness
- ✅ Negative numbers handling
- ✅ Large datasets (up to 100,000 elements)

## Complexity Analysis

### Time Complexity

| Operation | Best Case | Average Case | Worst Case |
|----------|-----------|--------------|------------|
| insert | Θ(1) | Θ(log n) | Θ(log n) |
| extractMax | Θ(log n) | Θ(log n) | Θ(log n) |
| increaseKey | Θ(1) | Θ(log n) | Θ(log n) |
| peek | Θ(1) | Θ(1) | Θ(1) |

**Justification:**
- `insert`: element added at end in O(1), then bubbled up log n levels
- `extractMax`: root removal in O(1), heap restoration in O(log n)
- `increaseKey`: value update in O(1), bubble up in O(log n)

### Space Complexity

- **Auxiliary space**: Θ(1) - all operations performed in-place
- **Total space**: Θ(n) - for storing n elements in ArrayList

## Benchmarks

Performance results on various data sizes:

| Input Size | Insert (ms) | Extract-Max (ms) | Increase-Key (ms) |
|-----------|-------------|------------------|-------------------|
| 100       | < 1         | < 1              | < 1               |
| 1,000     | 2           | 3                | 1                 |
| 10,000    | 25          | 35               | 15                |
| 100,000   | 350         | 500              | 200               |

*Results obtained on: Intel i5, 8GB RAM*

## 📝 Real-World Applications

1. **Priority Queue** - task scheduling in operating systems
2. **Dijkstra's Algorithm** - shortest path in graphs
3. **Heap Sort** - efficient sorting
4. **Event-driven simulations** - processing events by timestamp
5. **Top-K elements** - finding K maximum elements in a stream

## 👤 Author

**Asset Iglikov**
- GitHub: [@Set001YT](https://github.com/Set001YT)

## 🙏 Acknowledgments

- Aidana Aidynkyzy for the assignment
- Ruslan Dussenbayev for Min-Heap implementation

---

**Version:** 1.0  
**Last Updated:** 5 October 2025
