# Big O Notation Exercises

### Part 1

Đơn giản hóa các biểu thức sau đây hết mức có thể:

1. `O(n + 10)` (result: <strong>O(n)</strong>)
2. `O(100 * n)` (result: <strong>O(n)</strong>)
3. `O(25)` (result: <strong>O(1)</strong>)
4. `O(n^2 + n^3)` (result: <strong>O(n^2 + n^3)</strong>)
5. `O(n + n + n + n)` (result: <strong>O(n)</strong>)
6. `O(1000 * log(n) + n)` (result: <strong>O(log(n))</strong>)
7. `O(1000 * n * log(n) + n)` (result: <strong>O(n * log(n))</strong>)
8. `O(2^n + n^2)` (result: <strong>O(n^2)</strong>)
9. `O(5 + 3 + 1)` (result: <strong>O(1)</strong>)
10. `O(n + n^(1/2) + n^2 + n * log(n)^10)` (result: <strong>O(n * log(n)^10)</strong>)

### Part 2

Xác định độ phức tạp về thời gian và độ phức tạp về bộ nhớ của những function sau đây:


```javascript
// 1.

function logUpTo(n) {
    for (var i = 1; i <= n; i++) {
        console.log(i);
    }
}
```

<strong>Time complexity</strong>: O(n)
<strong>Space complexity</strong>: O(1)

```javascript
// 2. 

function logAtMost10(n) {
    for (var i = 1; i <= Math.min(n, 10); i++) {
        console.log(i);
    }
}
```

<strong>Time complexity</strong>: O(1)
<strong>Space complexity</strong>: O(1)

```javascript
// 3. 

function logAtLeast10(n) {
    for (var i = 1; i <= Math.max(n, 10); i++) {
        console.log(i);
    }
}
```

<strong>Time complexity</strong>: O(n)
<strong>Space complexity</strong>: O(1)

```javascript
// 4.

function onlyElementsAtEvenIndex(array) {
    var newArray = Array(Math.ceil(array.length / 2));
    for (var i = 0; i < array.length; i++) {
        if (i % 2 === 0) {
            newArray[i / 2] = array[i];
        }
    }
    return newArray;
}
```

<strong>Time complexity</strong>: O(n)
<strong>Space complexity</strong>: O(n)

```javascript
// 5. 

function subtotals(array) {
    var subtotalArray = Array(array.length);
    for (var i = 0; i < array.length; i++) {
        var subtotal = 0;
        for (var j = 0; j <= i; j++) {
            subtotal += array[j];
        }
        subtotalArray[i] = subtotal;
    }
    return subtotalArray;
}
```

<strong>Time complexity</strong>: O(n)
<strong>Space complexity</strong>: O(n)
