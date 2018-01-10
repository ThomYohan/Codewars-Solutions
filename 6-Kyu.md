

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

## Playing with digits
https://www.codewars.com/kata/playing-with-digits/javascript

Some numbers have funny properties. For example:

89 --> 8¹ + 9² = 89 * 1

695 --> 6² + 9³ + 5⁴= 1390 = 695 * 2

46288 --> 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51

Given a positive integer n written as abcd... (a, b, c, d... being digits) and a positive integer p we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k * n. In other words:

Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^ (p+3) + ...) = n * k

If it is the case we will return k, if not return -1.

Note: n, p will always be given as strictly positive integers.

```javascript
function digPow(n, p){
	let c = 0
		n.toString(10).split('').map((x,i) => {
			c += Math.pow(x, p + (i))
		})
	return c%n ===0 ? c / n : -1
}
```

## Consecutive Strings
https://www.codewars.com/kata/consecutive-strings/javascript

You are given an array strarr of strings and an integer k. Your task is to return the first longest string consisting of k consecutive strings taken in the array.

#Example: longest_consec(["zone", "abigail", "theta", "form", "libe", "zas", "theta", "abigail"], 2) --> "abigailtheta"

n being the length of the string array, if n = 0 or k > n or k <= 0 return "".
```javascript

function longestConsec(strarr, k) {
	let word = "";
	strarr.map((x, i) => {
		strarr.length > k && k > 0
			? (word = strarr.slice(i, k + i).join("").length > word.length ? strarr.slice(i, k + i).join("") : word)
			: (word = "");
	});
	return word;
}
```

## Find The Parity Outlier
https://www.codewars.com/kata/find-the-parity-outlier

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.

```javascript
function sorter(arr){
	let evens = []
	let odds = []
	arr.map((x,i) => {
	  x%2 ? odds.push(x) : evens.push(x)
	})
	return odds.length === 1 ? odds[0] : evens[0]
}
```

## Stop gninnipS My sdroW!
https://www.codewars.com/kata/stop-gninnips-my-sdrow

Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.


```javascript
function spinWords(words){
	return words.split(' ').reduce((acc, val) => {
		val.split('').length >=5  ? acc.push(val.split('').reverse().join('')) : acc.push(val)
return acc		
	}, []).join(' ')
}
```
## Dubstep
https://www.codewars.com/kata/dubstep/

Input
The input consists of a single non-empty string, consisting only of uppercase English letters, the string's length doesn't exceed 200 characters

Output
Return the words of the initial song that Polycarpus used to make a dubsteb remix. Separate the words with a space.

Examples
songDecoder("WUBWEWUBAREWUBWUBTHEWUBCHAMPIONSWUBMYWUBFRIENDWUB") =>  WE ARE THE CHAMPIONS MY FRIEND


```javascript
function songDecoder(arr){
return arr.split('WUB').filter((x,i)=> {
	return  x!== "WUB"
}).filter(Boolean).join(' ')
}
```
