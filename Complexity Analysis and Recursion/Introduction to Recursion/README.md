<h1>Introduction to Recursion</h1>

<h2>Mục tiêu</h2>
Khi kết thúc bài này, bạn sẽ có thể:
<ul>
  <li>Định nghĩa được đệ quy là gì và có thể giải thich được những điểm lợi và bất lợi của đệ quy</li>
  <li>Đảm bảo tất cả các hàm đệ quy có môt <strong>base case</strong>(trường hợp để dừng đệ quy), tránh việc <strong>call stack</strong> bị quá tải</li>
  <li>Có thể cấu trúc lại các hàm lặp dùng đệ quy<li>
</ul>

<h2>What is recursion?</h2>

<p>Một hàm đệ quy là một hàm gọi lại chính nó. Nghe có vẻ điên rồ và tại sao chúng ta phải làm như vậy? Thường thì đệ quy là một sự lựa chọn thay thế cho vòng lặp và trong nhiều trường hợp nó thực sự có thể trông dễ đọc hơn và code sẽ ngắn gọn hơn. Tuy nhiên, rất cần thiết phải có một thứ gọi là <strong>base case</strong> trong tất cả các hàm đệ quy, cũng như là phải có một sự hiểu biết về <strong>call stack</strong></p>

<h2>Why use recursion?</h2>

<p>Trong nhiều trường hợp, đệ quy có thể giải quyết được những vấn đề giống nhau, nhưng trong một cách dễ hiểu hơn. Có những trường hợp khác, đệ quy còn hữu ích hơn nhiều khi giải quyết một vài loại vấn đề nhất định. Thử một ví dụ sau:</p>

<p>Tưởng tượng chúng ta có một object và chúng ta đang có gắng tìm ra một giá trị nhất định tồn tại trong object đó. Chúng ta có thể dễ dàng lặp qua các phần tử của object đó và lấy ra giá trị cần tìm, nhưng điều gì sẽ xảy ra nếu giá trị cần tìm lại là một đối tượng khác? Chúng ta có ọbject dưới đây:</p>

```javascript
var obj = {
    data: {
        info: {
            innerData: {
                moreInfo: {
                    name: "Bob"
                }
            }
        }
    }
}
```

<p>Chúng ta có thể lặp qua object <strong>obj</strong>, và các biến <strong>data</strong>, <strong>info</strong>, <strong>innerData</strong> và <strong>moreInfo</strong>. Thay vì việc phải viết nhiều vòng lặp khác nhau, chúng ta có thể gọi lại function lần nữa nhưng với một tham số khác. Ý tưởng này được gọi là đệ quy. Với hàm đệ quy, mỗi lời gọi đệ quy là khác nhau</p>

<p>Always have a base case</p>

<p>Điều quan trọng nhất phải có trong hàm đệ quy là <strong>base case</strong>. Một <strong>base case</strong> là một trường hợp để dừng những lời gọi đệ quy. Nếu không có <strong>base case</strong>, hàm đệ quy của bạn sẽ liên tục gọi đến chính nó cho đến khi hết bộ nhớ</p>

<p>Đây là một ví dụ của hàm đệ quy mà không có <strong>base case</strong></p>

```javascript
function thisIsAProblem() {
    thisIsAProblem();
}
```

<h2>Visualize the call stack</h2>

<p>Khi chạy qua một hàm đệ quy, bạn luôn luôn phải cố gắng tính toán call stack. Chrome dev tool có thể giúp bạn làm được điều này. Bất cứ khi nào bạn gọi lại function một lần nữa, nghĩ về cách mà bạn thêm nó vào trong stack. Cuối cùng, nhớ rằng stack là một <strong>LIFO</strong>(Last In First Out). Function cuối cùng được đẩy vào stack sẽ là function được thực thi và đẩy ra đầu tiên</p>

<h2>Getting started</h2>

```javascript
function sumRange(num){
   if(num === 1) return 1; 
   return num + sumRange(num-1);
}
```

<p>Hãy cùng nhìn vào một hàm đệ quy mà không throw ra một <strong>RangeError</strong>. Chúng ta sẽ gọi function <strong>sumRange</strong>. Nó sẽ nhận vào một số và trả về tổng của tất cả các số từ 1 đến số được truyền vào. Ví dụ <strong>sumRange(3)</strong> sẽ trả về 1 + 2 + 3 = 6</p>

<p>Mỗi khi viết một hàm đệ quy, chúng ta cần làm rõ hai điều sau đây:</p>

<ul>
  <li><strong>base case</strong> - cách mà chúng ta sẽ dừng lời gọi đệ quy</li>
  <li>Chúng ta nên gọi hàm đệ quy thế nào?</li>
</ul>

<p><strong>Base case</strong> trong function <strong>sumRange</strong> là đoạn code ở dòng đầu tiên. Dòng thứ hai chính là cách mà function tự gọi lại chính nó</p>


<h2>Scope in Recursion</h2>
<p>Để có thể hiểu rõ về scope trong đệ quy, chúng ta có thể tạo <strong>wrapper</strong> hoặc <strong>helper</strong> function mà sẽ gọi nhiều lần trong một hàm bên ngoài (để có thể scope). Điều này được thực hiện qua một quá trình được gọi là <strong>helper method recursion</strong>. Hãy bắt đầu bằng việc viết một function gọi là <strong>all</strong> sẽ nhận vào một mảng và một callback sau đó sẽ trả về <strong>true</strong> nếu mọi giá trị của mảng trả về <strong>true</strong> khi truyền giá trị đó như một tham số vào callback. Đây là một giải pháp lặp:</p>

<h3>Iterative Solution</h3>

```javascript
function all(array, condition){
    for(var i = 0; i < array.length; i++){
        if(!(condition(array[i]))){
            return false;
        }
    }
    return true;
}

all([1,2,3,4], function(val){
    return val > 0;
}); // true

all(["1","2",3,"4"], function(val){
    return typeof val === 'string';
}); // false
```

<h3>Helper Method Recursion</h3>

<p>Bây giờ hãy cùng xem chúng ta cùng giải quyết vấn đề này bằng việc sử dụng <strong>helper method recursion</strong>:</p>

```javascript
function allRecursive(array, condition) {
    var copy = array.slice();  
    function allRecursiveHelper(arr, cb){
        if (arr.length === 0) return true;
        if (condition(arr[0])){
            arr.shift();
            return allRecursive(arr,condition);
        } else {
            return false;
        }
    }
    return allRecursiveHelper(copy, condition);
}

var numbersArray = [1,2,3,4,5];
allRecursive(numbersArray, function(v) {
    return v > 0;
});

```

<h3>Pure Recursion</h3>

<p>Chúng ta cũng có thể giải quyết vấn đề trên mà không cần dùng đến <strong>helper method recursion</strong>. Dưới đây là một cách phổ biến để giải quyết bằng việc truyền vào một tham số nhỏ dần qua từng lần gọi đệ quy. Hãy cùng nhìn vào function dưới đây:</p>

```javascript
function allRecursive(array, condition) {
    var copy = copy || array.slice();
    if (copy.length === 0) return true;
    if (condition(copy[0])){
        copy.shift();
        return allRecursive(copy,condition);
    } else {
        return false;
    }
}

var numbersArray = [1,2,3,4,5];
allRecursive(numbersArray, function(v) {
    return v > 0;
});
```

<h2>Additional Resources</h2>

<a href="https://youtu.be/Mv9NEXX1VHc">Computerphile Recursion</a>
<a href="https://youtu.be/k7-N8R0-KY4">FunFunFunction Recursion</a>
