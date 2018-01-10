
## Sum of Pairs
https://www.codewars.com/kata/sum-of-pairs/

Given a list of integers and a single sum value, return the first two values (parse from the left please) in order of appearance that add up to form the sum.

Negative numbers and duplicate numbers can and will appear.

NOTE: There will also be lists tested of lengths upwards of 10,000,000 elements. Be sure your code doesn't time out.

```javascript
function sumPairs(arr, sum){
 var results = {}
  for (var i = 0; i < arr.length; ++i) {
    if (results[sum - arr[i]]) return [sum - arr[i], arr[i]];
    results[arr[i]] = true
  }
}
```
