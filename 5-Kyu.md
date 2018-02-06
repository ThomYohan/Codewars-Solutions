# Total Complete : 8


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

## Weight for Weight
https://www.codewars.com/kata/weight-for-weight

My friend John and I are members of the "Fat to Fit Club (FFC)". John is worried because each month a list with the weights of members is published and each month he is the last on the list which means he is the heaviest.

I am the one who establishes the list so I told him: "Don't worry any more, I will modify the order of the list". It was decided to attribute a "weight" to numbers. The weight of a number will be from now on the sum of its digits.

For example 99 will have "weight" 18, 100 will have "weight" 1 so in the list 100 will come before 99. Given a string with the weights of FFC members in normal order can you give this string ordered by "weights" of these numbers?

Example:
"56 65 74 100 99 68 86 180 90" ordered by numbers weights becomes: "100 180 90 56 65 74 68 86 99"

When two numbers have the same "weight", let us class them as if they were strings and not numbers: 100 is before 180 because its "weight" (1) is less than the one of 180 (9) and 180 is before 90 since, having the same "weight" (9) it comes before as a string.

All numbers in the list are positive numbers and the list can be empty.

```javascript
function orderWeight(str) {

  return str.split(' ').sort((a,b) => {
      return strSum(a) === strSum(b) ? a.localeCompare(b) : strSum(a) - strSum(b);
    }).join(" ");
}

function strSum(str) {
  return str.split('').reduce((a,b) => {
    return a + Number(b);
  }, 0);
}
```
## Calculating with Functions
https://www.codewars.com/kata/calculating-with-functions

This time we want to write calculations using functions and get the results. Let's have a look at some examples:

```javascript
seven(times(five())); // must return 35
four(plus(nine())); // must return 13
eight(minus(three())); // must return 5
six(dividedBy(two())); // must return 3
```

Requirements:

There must be a function for each number from 0 ("zero") to 9 ("nine")
There must be a function for each of the following mathematical operations: plus, minus, times, dividedBy (divided_by in Ruby)
Each calculation consist of exactly one operation and two numbers
The most outer function represents the left operand, the most inner function represents the right operand

```javascript
function expression(number, operation){
	if(!operation)
		return number;
	return operation(number);
}

function zero(operation) { return expression(0, operation); }
function one(operation) { return expression(1, operation); }
function two(operation) { return expression(2, operation); }
function three(operation) { return expression(3, operation); }
function four(operation) { return expression(4, operation); }
function five(operation) { return expression(5, operation); }
function six(operation) { return expression(6, operation); }
function seven(operation) { return expression(7, operation); }
function eight(operation) { return expression(8, operation); }
function nine(operation) { return expression(9, operation); }

function plus(x) {
	return function(y) {
		return y + x;
	}
}
function minus(x) {
	return function(y) {
		return y - x;
	}
}
function times(x) {
	return function(y) {
		return y * x;
	}
}
function dividedBy(x) {
	return function(y) {
		return y / x;
	}
}
```

## Where my anagrams at?
https://www.codewars.com/kata/where-my-anagrams-at

Write a function that will find all the anagrams of a word from a list. You will be given two inputs a word and an array with words. You should return an array of all the anagrams or an empty array if there are none. For example:

anagrams('abba', ['aabb', 'abcd', 'bbaa', 'dada']) => ['aabb', 'bbaa']

anagrams('racer', ['crazer', 'carer', 'racar', 'caers', 'racer']) => ['carer', 'racer']

anagrams('laser', ['lazing', 'lazy',  'lacer']) => []

```javascript
function anagrams(word, words) {
  return words.filter(function(item){
    return item.split('').sort().join('') === word.split('').sort().join('');
  });
}
```

## Double Cola
https://www.codewars.com/kata/double-cola

Sheldon, Leonard, Penny, Rajesh and Howard are in the queue for a "Double Cola" drink vending machine; there are no other people in the queue. The first one in the queue (Sheldon) buys a can, drinks it and doubles! The resulting two Sheldons go to the end of the queue. Then the next in the queue (Leonard) buys a can, drinks it and gets to the end of the queue as two Leonards, and so on.

For example, Penny drinks the third can of cola and the queue will look like this:

Rajesh, Howard, Sheldon, Sheldon, Leonard, Leonard, Penny, Penny
Write a program that will return the name of the person who will drink the n-th cola.

Note that in the very beginning the queue looks like that:

Sheldon, Leonard, Penny, Rajesh, Howard
##Input

The input data consist of an array which contains at least 1 name, and single integer n.

(1 ≤ n ≤ 1000000000).
##Output / Examples Return the single line — the name of the person who drinks the n-th can of cola. The cans are numbered starting from 1. Please note that you should spell the names like this: "Sheldon", "Leonard", "Penny", "Rajesh", "Howard" (without the quotes). In that order precisely the friends are in the queue initially.

```javascript
function whoIsNext(names, r) {
	var l = names.length;
	while (r >= l) {
		r -= l;
		l *= 2;
	}
	return names[Math.ceil(names.length * r / l) - 1];
}
```

## Valid Parentheses 
https://www.codewars.com/kata/valid-parentheses

Write a function called that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return true if the string is valid, and false if it's invalid.

Examples
"()"              =>  true
")(()))"          =>  false
"("               =>  false
"(())((()())())"  =>  true
Constraints
0 <= input.length <= 100

You may assume that the input string will only contain opening and closing parenthesis and will not be an empty string.

```javascript
function validParentheses(str) {
	for (var i = 0; i <= str.length / 2; ++i) {
		str = str.replace('()', '');
	}

	return str === '';
}
```

## Human Readable Time
https://www.codewars.com/kata/human-readable-time/train/javascript

Write a function, which takes a non-negative integer (seconds) as input and returns the time in a human-readable format (HH:MM:SS)

HH = hours, padded to 2 digits, range: 00 - 99
MM = minutes, padded to 2 digits, range: 00 - 59
SS = seconds, padded to 2 digits, range: 00 - 59
The maximum time never exceeds 359999 (99:59:59)

You can find some examples in the test fixtures.

```javascript
function humanReadable(seconds) {
	var fix = x => {
		if (x < 10) {
			return '0' + x;
		} else {
			return x;
		}
	};
	return (
		fix(parseInt(seconds / (60 * 60))) +
		':' +
		fix(parseInt(seconds / 60 % 60)) +
		':' +
		fix(seconds % 60)
	);
}
```
## One Line Task : Count Down 1
https://www.codewars.com/kata/one-line-task-count-down-i/train/javascript

Count down 3 times to an positive integer n, return these 3 numbers as a string, separated by exclamation mark(!).

Code Limit
Less than 30 characters.

Example
For n = 1, the output should be "3!2!1".

count down from 3 to 1

For n = 10, the output should be "12!11!10".

count down from 12 to 10

For n = 100, the output should be "102!101!100".

count down from 102 to 100

```javascript
countDown=n=>n+2+`!${n+1}!`+n
```

## Simple Pig Latin
https://www.codewars.com/kata/simple-pig-latin/train/javascript

Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.

Examples
pigIt('Pig latin is cool'); // igPay atinlay siay oolcay
pigIt('Hello world !');     // elloHay orldWay !

```javascript
function pigIt(str){
  const a = []
  str.split(' ').map(w => {
    const b = w.split('')
    b.shift()
    const s = b.join('')
    a.push(`${s}${w[0]}ay`)
  })
  return a.join(' ')
}
```

