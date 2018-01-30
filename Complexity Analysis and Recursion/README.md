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
  <li>O(10*n2 + 5n + 20) --> O(n2)</li>
  <li>O(n * n) --> O(n2)</li>
  <li>O(n*log(n) + 30000 * n) --> O(n * log(n))</li>
</ul>

<p>Chú ý vào tất cả các ví dụ trên, các biến số được thay bằng 1 như số 500 ở case đầu tiên, hoặc case 99999999999 ở case thứ 2. Các thành phần nhỏ cũng sẽ bị bỏ qua, ví dụ như ở case thứ 3, các thành phần như 5n + 20 sẽ bị bỏ qua, hằng số 10 sẽ trở thành 1. Quy tắc tương tự cho các trường hợp tiếp theo</p>

<h3>Examples Big O Runtimes</h3>

<p>Tiếp theo, hãy cùng tìm hiểu về việc phân tích thuật toán bằng cách sử dụng ký hiệu <strong>Big O</strong></p>

<strong>O(1)</strong>
<hr />
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
<hr />
<br />
<p>Những thuật toán sau là <strong>O(n)</strong> hoặc là <strong>linear time</strong>, bởi vì độ phức tạp thuật toán dựa vào tham số truyền vào</p>

```javascript
function sayHello(numberOfTimes) {
    for (var i = 0; i < numberOfTimes; i++) {
        console.log("Hello");
    }
}
```
