<h1>Complexity Analysis and Recursion</h1>

<h2>Introduction to Big O Notation</h2>
<h3>Objective</h3>
<p>Khi kết thúc bài này, bạn sẽ có khả năng:</p>
<ul>
  <li>Mô tả về ký hiệu <strong>Big O</strong></li>
  <li>Đánh giá được thời gian chạy của thuật toán dựa vào ký hiệu Big O</li>
  <li>So sánh được thời gian chạy nhanh nhất và thời gian chạy chậm nhất của độ phức tạp tiệm cận (ví dụ: O(1), O(log(n)), O(n), O(nlog(n)), O(n2)</li>
  <li>Giải thích sự khác nhau giữa <strong>time complexity</strong> và <strong>space complexity</strong></li>
</ul>

<h3>Algorithm Performance</h3>
<p>Khi bạn làm việc với một giải pháp cho một vấn đề, bạn sẽ thường phải tự hỏi rằng giải pháp của bạn chạy nhanh như thế nào. Không may rằng, có nhiều thứ ảnh hưởng tới tốc độ của chương trình. Ví dụ như, phần cứng trong máy tính của bạn, bộ dữ liệu mà bạn đang sử dụng, chương trình đang chạy trong máy tính của bạn, và thậm chí nhiệt độ xung quanh cũng hoàn toàn có thể làm ảnh hưởng tới chương trình của bạn. Vì vậy, bạn có thể dùng một bộ đo thời gian để đo thời gian chạy của chương trình, điều này cũng có thể hữu ích nhưng nó có thể không phải là một cách đáng tin cậy để so sánh trong một số cách thực hiện khác</p>

<h3>Big O Notation: Background</h3>
<p>Một cách lý thuyết hơn để so sánh các thuật toán với nhau là dùng ký hiệu <strong>Big O</strong></p>
<p><strong>Big O</strong> là một khái niệm được vay mượn từ toán học và nó sẽ cung cấp cho bạn một khoảng thời gian gần đúng trên thời gian chạy của thuật toán dựa vào kích cỡ của bộ dữ liệu mà thuật toán sẽ sử dụng. Nếu bạn muốn biết về những định nghĩa của ký hiệu thì có thể đọc bài viết <a href="https://en.wikipedia.org/wiki/Big_O_notation">này</a>. Còn bây giờ, chúng ta sẽ tập trung vào việc củng cố kiến thức trực quan về các ký hiệu cho bạn để bạn có thể áp dụng hiệu quả</p>

<h3>Big O Notation</h3>
<p>Để bắt đầu với ký hiệu <strong>Big O</strong>, sẽ hữu ích nếu hiểu được nó là gì và không là gì. Có nhiều quy tắc với ký hiệu mà chúng ta cần nhớ:</p>

<ul>
  <li>1. Các hằng số sẽ bị bỏ qua</li>
  <li>2. Các thành phần nhỏ sẽ bị bỏ qua</li>
</ul>
<p>Hãy nhớ kỹ những quy tắc đó và nhìn những ví dụ dưới đây:</p>
<ul>
  <li>O(500 * n) --> O(n)</li>
  <li>O(99999999999) --> O(1)</li>
  <li>O(10*n^2 + 5n + 20) --> O(n^2)</li>
  <li>O(n * n) --> O(n^2)</li>
  <li>O(n*log(n) + 30000 * n) --> O(n * log(n))</li>
</ul>

<p>Chú ý vào tất cả các ví dụ trên, các biến số được thay bằng 1 như số 500 ở case đầu tiên, hoặc case 99999999999 ở case thứ 2. Các thành phần nhỏ cũng sẽ bị bỏ qua, ví dụ như ở case thứ 3, các thành phần như 5n + 20 sẽ bị bỏ qua, hằng số 10 sẽ trở thành 1. Quy tắc tương tự cho các trường hợp tiếp theo</p>

<h3>Examples Big O Runtimes</h3>

<p>Tiếp theo, hãy cùng tìm hiểu về việc phân tích thuật toán bằng cách sử dụng ký hiệu <strong>Big O</strong></p>

<strong>O(1)</strong>
<br />
<p>Function dưới dây gọi là <strong>O(1)</strong> hoặc là <strong>constant time</strong> bởi vì độ phức tạp thuật toán không phụ thuộc vào kích thước dữ liệu của biến đầu vào. Nói cách khác, bất kể kích thước của đầu vào, thời gian chạy của thuật toán sẽ không phát triển vượt ra khỏi kích thước tập biến đầu vào. Trong đa số trường hợp, thời gian chạy của thuật toán gần như bằng nhau bất kể kích thước đầu vào</p>

```javascript
function add(num1, num2, num3) {
   return num1 + num2 + num3;
}
```

<p>Trong ví dụ trên, function <strong>add</strong> dù có bao nhiêu tham số truyền vào cũng không làm thay đổi độ phức tạp thuật toán</p>

```javascript
function sayHello() {
    for (var i = 0; i < 100; i++) {
       console.log("Hello");
    }
}
```

<p>Function <strong>sayHello</strong> hiển thị một tin nhắn 100 lần vào console mỗi khi function được gọi. Function này cũng là function <strong>O(1)</strong> và nó không có bất cứ một tham số đầu vào nào</p>

```javascript
function logMultiples(num) {
    for (var i = 0; i < 10; i++) {
        console.log(i * num);
    }
}
```

<p>Function <strong>logMultiples</strong> hiển thị 10 số là tích của i và tham số truyền vào. Bất kể tham số truyền vào là bao nhiêu, chỉ 10 số được hiển thị. Nói cách khác, thời gian mỗi lần chương trình chạy lại không ảnh hưởng bởi tham số truyền vào, và function này cũng là function <strong>O(1)</strong></p>

<strong>O(n)</strong>
<br />
<p>Những thuật toán sau là <strong>O(n)</strong> hoặc là <strong>linear time</strong>, bởi vì độ phức tạp thuật toán dựa vào tham số truyền vào</p>

```javascript
function sayHello(numberOfTimes) {
    for (var i = 0; i < numberOfTimes; i++) {
        console.log("Hello");
    }
}
```
<p>Function <strong>sayHello</strong> nhận một tham số, nó sẽ tùy chỉnh số lần <strong>Hello</strong> được in ra màn hình console. Trong trường hợp này, thời gian chạy của function tỉ lệ thuận với tham số truyền vào. Tham số truyền vào càng lớn thì thời gian chạy càng nhiều. Đặt <strong>numberOfTimes</strong> là <strong>n</strong>, là đầu vào của function, điều này có nghĩa là thời gian chạy của function là <strong>O(n)</strong></p>

```javascript
function doubleThenTriple(numbers) {
    var doubled = numbers.map(function(num) {
        return num * 2;
    });

    return doubled.map(function(num) {
        return num * 3;
    });
}
```

<p>Trong ví dụ trên, chúng ta <strong>map</strong> qua dữ liệu đầu vào hai lần. Do vậy bạn có thể nói thời gian chạy là <strong>O(n + n)</strong> hoặc là <strong>O(2 * n)</strong>. Tuy nhiên, trong ký hiệu <strong>big O</strong>, những hằng số sẽ được bỏ qua. Vì vậy, <strong>O(2 * n)</strong> sẽ bằng với <strong>O(n)</strong>. Điều quan trọng ở đây là thời chạy chiếm tỉ lệ tương ứng với kích thước đầu vào chứ không phải là chi tiết tỉ lệ của mối quan hệ</p>

<strong>O(n^2)</strong>
<br />

```javascript
function allPairs(arr) {
    var pairs = [];
    for (var i = 0; i < arr.length; i++) {
        for (var j = i + 1; j < arr.length; j++) {
            pairs.push([arr[i], arr[j]]);
        }
    }

    return pairs;
}
```

```javascript
function bubbleSort(arr) {
  var len = arr.length;
  var lastSwap;
  var temp
  while (len != 0) {
    lastSwap = 0;
    for (var i = 1; i < len; i++) {
      if (arr[i - 1] > arr[i]) {
        // Swap the two elements
        temp = arr[i-1];
        arr[i-1] = arr[i];
        arr[i] = temp;
        lastSwap = i;
      }
    }
    len = lastSwap;
  }
}
```

<p>Trong những ví dụ trên, chúng ta lặp qua mỗi thành phần của một mảng, và trong vòng lặp đó, chúng ta lại lặp một lần nữa. Vì vậy, thời gian chạy của function sẽ là <strong>O(n * n)</strong>hoặc là <strong>O(n^2)</strong></p>

<p>Nếu bạn nhìn thấy vòng lặp lồng nhau thì thời gian chạy sẽ là <strong>O(n^(số vòng lặp lồng nhau))</strong>. Nói cách khác, nếu có một vòng lặp thì thời gian chạy là <strong>O(n)</strong>, nếu có hai vòng lặp lồng nhau thì thời gian chạy là <strong>O(n^2)</strong>, nếu có ba vòng lặp lồng nhau thì thời gian chạy là <strong>O(n^3)</strong> và cứ như vậy. Tuy nhiên, quy tắc không phải lúc nào cũng như vậy, xem ví dụ dưới đây:</p>

```javascript
function logMultiples(n) {
    for (var num1 = 1; num1 <= n; num1++) {
        for (var num2 = 1; num2 <= n; num2++) {
            console.log(num1 * num2);
        }
    }
}

function logSomeMultiples(n) {
    for (var num1 = 1; num1 < n=; num1++) {
        for (var num2 = 1; num2 <= Math.min(n, 10); num2++) {
            console.log(num1 * num2);
        }
    }
}
```

<p>Function đầu tiên <strong>logMultiples</strong> là <strong>O(n^2)</strong>. Vì thời gian chạy của cả hai vòng lặp đều phụ thuộc vào tham số đầu vào, điều này có nghĩa là cả hai vòng lặp đều là <strong>O(n)</strong> và chúng ta có hai <strong>O(n)</strong> lồng nhau, vì vậy function này sẽ là <strong>O(n^2)</strong></p>

<p>Function thứ hai trong cũng có vẻ là <strong>O(n^2)</strong> nhưng thực ra không phải. Vòng lặp đầu tiên là <strong>O(n)</strong> vì thời gian chạy của nó phụ thuộc vào tham số truyền vào. Còn thời gian chạy của vòng lặp thứ hai lại không phải như vậy, vòng lặp thứ 2 có số vòng lặp tối đa là 10 lần. Vì vậy vòng lặp này sẽ là <strong>O(1)</strong>. Vòng lặp bên ngoài là <strong>O(n)</strong>, vòng lặp bên trong là <strong>O(1)</strong>, như vậy thời gian chạy của function sẽ là <strong>O(n)</strong> chứ không phải là <strong>O(n^2)</strong></p>

<h3>Comparing Common Big O Runtimes</h3>

<p>Trong hình dưới đây, trục X(trục ngang) đại diện cho kích thước đầu vào, trục Y(trục dọc) đại diện cho thời gian chạy thuật toán</p>

<img href="">
