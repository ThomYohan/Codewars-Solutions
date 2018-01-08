

## Multiples of 3 or 5 
https://www.codewars.com/kata/multiples-of-3-or-5/javascript

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

Note: If the number is a multiple of both 3 and 5, only count it once.


```javascript
function solution(n) {
	return n <= 0 ? 0 : Array.from({ length: n }, (_, i) => (i % 3 == 0 || i % 5 == 0 ? i : 0)).reduce((x, y) => x + y);
}

solution(10);

```



