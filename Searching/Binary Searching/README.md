# Binary Search

## 📌 Problem

Given a **sorted array** and a target element, find the index of the target element using Binary Search.

If the element is not present, return `-1`.

---

## 💡 What is Binary Search?

Binary Search is an efficient searching algorithm that works on a **sorted array**.

Instead of checking every element one by one, it repeatedly divides the search space into half.

### Example

```text
Array:  [10, 20, 30, 40, 50, 60, 70]
Target: 50
```

We start with:

```text
low = 0
high = 6
```

Find the middle:

```java
int mid = low + (high - low) / 2;
```

If `arr[mid]` is:

* Equal to target → Element found
* Less than target → Search the right half
* Greater than target → Search the left half

---

## 🔄 Algorithm

1. Set `low = 0`.
2. Set `high = arr.length - 1`.
3. Find the middle index:

   ```java
   int mid = low + (high - low) / 2;
   ```
4. Compare `arr[mid]` with the target.
5. If `arr[mid] == target`, return `mid`.
6. If `arr[mid] < target`, move to the right half:

   ```java
   low = mid + 1;
   ```
7. If `arr[mid] > target`, move to the left half:

   ```java
   high = mid - 1;
   ```
8. Repeat until `low > high`.
9. If the loop ends, the element is not present.

##

---

## 🧠 Approach

The main idea is to **eliminate half of the array after every comparison**.

For example:

```text
[10, 20, 30, 40, 50, 60, 70]
              ↑
             mid
```

If the target is `60`:

```text
60 > 40
```

So there is no need to search:

```text
[10, 20, 30, 40]
```

We only search:

```text
[50, 60, 70]
```

Then we repeat the same process.

---

## 🔢 Dry Run

Given:

```text
arr = [10, 20, 30, 40, 50, 60, 70]
target = 60
```

### Step 1

```text
low = 0
high = 6

mid = 0 + (6 - 0) / 2
mid = 3
```

```text
arr[3] = 40
```

Since:

```text
40 < 60
```

Search the right half:

```text
low = mid + 1
low = 4
```

### Step 2

```text
low = 4
high = 6

mid = 4 + (6 - 4) / 2
mid = 5
```

```text
arr[5] = 60
```

Target found!

```text
Index = 5
```

---

## ⏱️ Time Complexity

### Best Case

Target is found at the middle during the first comparison.

```text
O(1)
```

### Average Case

```text
O(log n)
```

### Worst Case

The search continues until the search space becomes empty.

```text
O(log n)
```

---

## 💾 Space Complexity

For the iterative implementation:

```text
O(1)
```

Only a few variables such as `low`, `high`, and `mid` are used.

---

## ⚠️ Important Condition

Binary Search requires the array to be **sorted**.

```text
✅ [10, 20, 30, 40, 50]
```

```text
❌ [30, 10, 50, 20, 40]
```

---

## ⭐ Important Formula

Instead of:

```java
int mid = (low + high) / 2;
```

Prefer:

```java
int mid = low + (high - low) / 2;
```

This avoids possible **integer overflow** when `low` and `high` are very large.

---

## 🔑 Key Points

* Binary Search works on a **sorted array**.
* It divides the search space into two halves.
* `low` represents the starting index.
* `high` represents the ending index.
* `mid` represents the middle index.
* If target is greater than `arr[mid]`, move right.
* If target is smaller than `arr[mid]`, move left.
* Time Complexity: **O(log n)**
* Space Complexity: **O(1)** for iterative implementation.
* Recommended middle formula:

  ```java
  int mid = low + (high - low) / 2;
  ```
