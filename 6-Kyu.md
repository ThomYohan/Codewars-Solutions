# Total Solved: 21

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

##### Examples
songDecoder("WUBWEWUBAREWUBWUBTHEWUBCHAMPIONSWUBMYWUBFRIENDWUB") =>  WE ARE THE CHAMPIONS MY FRIEND


```javascript
function songDecoder(arr){
return arr.split('WUB').filter((x,i)=> {
	return  x!== "WUB"
}).filter(Boolean).join(' ')
}
```

## Who likes it? 
https://www.codewars.com/kata/who-likes-it

You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function likes :: [String] -> String, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:

##### Examples
```javascript
likes [] // must be "no one likes this"
likes ["Peter"] // must be "Peter likes this"
likes ["Jacob", "Alex"] // must be "Jacob and Alex like this"
likes ["Max", "John", "Mark"] // must be "Max, John and Mark like this"
likes ["Alex", "Jacob", "Mark", "Max"] // must be "Alex, Jacob and 2 others like this"
For more than 4 names, the number in and 2 others simply increases.
```

```javascript
function likes(names) {
	if (!names.length) {
		return "no one likes this"
	} else if (names.length === 1) {
		return `${names[0]} likes this`
	} else if (names.length === 2) {
		return `${names.join(' and ')} like this`
	} else if (names.length === 3) {
		return `${names[0]}, ${names[1]} and ${names[2]} like this`
	} else if (names.length >= 4){
		return `${names[0]}, ${names[1]} and ${names.length -2 } others like this`
	}
}
```

## Perfect Square
https://www.codewars.com/kata/perfect-square

Task
Write function which validate string input.If string is a perfect square return true,false otherwise.

What is perfect square?
We assume that charcater "."(dot) is a perfect square 1x1.

-Perfect square is only build from "." characters.It cant contain any other characters beside "." and "\n" (Line feed).
-Square must have same width and height -> cpt.Obvious
-Square size is random!

```javascript
function perfectSquare(str) {
	if (!RegExp(/\n/).test(str) && str.length !== 1) {
		return false;
	}
	str = str.replace(',', '').split('\n');
	return str.every((curr, ind) => {
		if(curr.length === 1 && typeof str[ind+1] === 'undefined') {
			return true
		}
		return curr.length === str[0].length && curr.length > 1
	});
}
```

## Find the divisors!
https://www.codewars.com/kata/find-the-divisors


Create a function named divisors/Divisors that takes an integer and returns an array with all of the integer's divisors(except for 1 and the number itself). If the number is prime return the string '(integer) is prime' 

```javascript
function div(num) {
	const arr = [...Array(num)].map((_, i) => {
		return i + 1;
	});

	let filtered = arr.filter(curr => {
		if (curr > 1 && curr !== num) {
			return !(num % curr);
		}
	});

	return filtered.length > 1 ? filtered : `${num} is prime`;
}
```


## Sort odd and even numbers in different order
https://www.codewars.com/kata/sort-odd-and-even-numbers-in-different-order/

You have an array of numbers. Your task is to sort ascending odd numbers and descending even numbers.

Note that zero is even number. If you have an empty array, you need to return it.

##### Example

```javascript
sortArray([5, 3, 2, 8, 1, 4]) == [1, 3, 8, 4, 5, 2]
```

```javascript
function sortArray(array) {
    const odd = array.filter((x) => x % 2).sort((a,b) => a - b);
    const even = array.filter((x) => ! (x % 2)).sort((a,b) => b - a);
    return array.map((x) => x % 2 ? odd.shift() : even.shift());
}
```


## Give me a diamond
https://www.codewars.com/kata/give-me-a-diamond/

This kata is to practice simple string output. Jamie is a programmer, and James' girlfriend. She likes diamonds, and wants a diamond string from James. Since James doesn't know how to make this happen, he needs your help.

###Task:

You need to return a string that displays a diamond shape on the screen using asterisk ("*") characters. Please see provided test cases for exact output format.

The shape that will be returned from print method resembles a diamond, where the number provided as input represents the number of *’s printed on the middle line. The line above and below will be centered and will have 2 less *’s than the middle line. This reduction by 2 *’s for each line continues until a line with a single * is printed at the top and bottom of the figure.

Return null if input is even number or negative (as it is not possible to print diamond with even number or negative number).

```javascript
function diamond(n){
  if (n <= 0 || n%2 === 0){
    return null;
  }else{
    var stars = n;
    var output = '';
    var firstLine = true;
    while(stars > 0){
      var j;
      if (!firstLine){
        output = '\n' + output;
        for (j = 0; j < (n-stars)/2; j++){
          output += ' ';
        }
      }
      for (var i = 0; i < stars; i++){
        output += '*';
        if (!firstLine){
          output = '*' + output;
        }
      }
      if (!firstLine){
        for (j = 0; j < (n-stars)/2; j++){
          output = ' ' + output;
        }
      }
      output = output + '\n';
      stars -= 2;
      firstLine = false;
    }
    return ' ' + output.substring(1);
  }
}
```

## Calculating with Functions
https://www.codewars.com/kata/give-me-a-diamond/

This time we want to write calculations using functions and get the results. Let's have a look at some examples:

seven(times(five())); // must return 35
four(plus(nine())); // must return 13
eight(minus(three())); // must return 5
six(dividedBy(two())); // must return 3
Requirements:

There must be a function for each number from 0 ("zero") to 9 ("nine")
There must be a function for each of the following mathematical operations: plus, minus, times, dividedBy (divided_by in Ruby)
Each calculation consist of exactly one operation and two numbers
The most outer function represents the left operand, the most inner function represents the right operand

```javascript
function expression(number, operation) {
	if (!operation) return number;
	return operation(number);
}

function zero(operation) {
	return expression(0, operation);
}
function one(operation) {
	return expression(1, operation);
}
function two(operation) {
	return expression(2, operation);
}
function three(operation) {
	return expression(3, operation);
}
function four(operation) {
	return expression(4, operation);
}
function five(operation) {
	return expression(5, operation);
}
function six(operation) {
	return expression(6, operation);
}
function seven(operation) {
	return expression(7, operation);
}
function eight(operation) {
	return expression(8, operation);
}
function nine(operation) {
	return expression(9, operation);
}

function plus(x) {
	return function(y) {
		return y + x;
	};
}
function minus(x) {
	return function(y) {
		return y - x;
	};
}
function times(x) {
	return function(y) {
		return y * x;
	};
}
function dividedBy(x) {
	return function(y) {
		return y / x;
	};
}
```

## Array.diff
https://www.codewars.com/kata/array-dot-diff/

Your goal in this kata is to implement an difference function, which subtracts one list from another.

It should remove all values from list a, which are present in list b.

array_diff([1,2],[1]) == [2]
If a value is present in b, all of its occurrences must be removed from the other:

array_diff([1,2,2,2,3],[2]) == [1,3]

```javascript
function array_diff(a, b) {
  return a.filter((x,i) => {
		return b.indexOf(x) < 0
	})
}
````


## Are they the same?
https://www.codewars.com/kata/are-they-the-same/

Given two arrays a and b write a function comp(a, b) (compSame(a, b) in Clojure) that checks whether the two arrays have the "same" elements, with the same multiplicities. "Same" means, here, that the elements in b are the elements in a squared, regardless of the order.

```javascript
function comp(array1, array2){
  if (array1 === null || array2 === null)
    return false;
  if (array1.length != array2.length)
    return false;
  array1 = array1.sort((a, b) => a-b);
  array2 = array2.sort((a, b) => a-b);
  for (let i = 0; i < array1.length; i++)
  {
    if (array2[i] != array1[i] * array1[i])
      return false;
  }
  return true;
}
```

## Vasya - Clerk
https://www.codewars.com/kata/vasya-clerk

The new "Avengers" movie has just been released! There are a lot of people at the cinema box office standing in a huge line. Each of them has a single 100, 50 or 25 dollars bill. An "Avengers" ticket costs 25 dollars.

Vasya is currently working as a clerk. He wants to sell a ticket to every single person in this line.

Can Vasya sell a ticket to each person and give the change if he initially has no money and sells the tickets strictly in the order people follow in the line?

Return YES, if Vasya can sell a ticket to each person and give the change with the bills he has at hand at that moment. Otherwise return NO.
```javascript
function tickets(arr){
var a25 = 0,a50 = 0;
  for(var i = 0;i<arr.length;i++){
    if(arr[i] == 25){
      a25 += 1;
    }
    if(arr[i] == 50){
      a25 -= 1; a50 += 1;
    }
    if(arr[i] == 100){
      if(a50 == 0 && a25 >= 3){
        a25 -= 3;
      }else{
        a25 -= 1; a50 -= 1;
      }
    }
    if(a25 < 0 || a50 < 0){
      return 'NO';
    }
  }
  return 'YES';
}
```

## Only Duplicates
https://www.codewars.com/kata/only-duplicates

Given a string, remove any characters that are unique from the string.

Example:

input: "abccdefee"

output: "cceee"

```javascript
function onlyDuplicates(str) {
	let split = str.split('')
	let arr = []
	
	split.map((x,i) => {
		if(split.lastIndexOf(x) !== i){
			arr.push(x)
		} else if (
			arr.includes(x)
			) { 
			arr.push(x)
			}
	})
	return arr.join('')
}
```

## Length of the longest sequence of consecutive integers
https://www.codewars.com/kata/length-of-the-longest-sequence-of-consecutive-integers

Given an array of integers, the sequences we are looking for are formed of consecutive numbers from the array, but not with necessarily consecutive indices. The order of the indices must be ascending though.

Consecutive in this context means numbers in increasing order, that differ by at most one unit (they can be equal). 1,2,3 are consecutive, but also 1,1,1,2,3 and 10,10,10

Example:

For this array: [1,1,2,5,3] the possible such sequences are:

[1], [2], [5], [3], [1, 1], [1, 2], [2, 3], [1, 1, 2], [1, 2, 3], [1, 1, 2, 3]
The function to be implemented must return the length of the longest such sequence, in this case 4.

For this version of the problem the test cases don't include very large arrays, so naive implementations will work.

```javascript
function maxConsecutiveSequenceLength(arr) {
  const dp = new Array(arr.length + 1).fill(0);

  for (let i = 0; i < arr.length; ++i) {
    for (let j = 0; j < i; ++j) {
      if (arr[i] >= arr[j] && arr[i] - arr[j] <= 1) {
        dp[i] = Math.max(dp[j], dp[i]);
      }
    }
    dp[i]++;
  }
  return Math.max(...dp);
}
```

## Array Helpers
https://www.codewars.com/kata/array-helpers/

This kata is designed to test your ability to extend the functionality of built-in ruby classes. In this case, we want you to extend the built-in Array class with the following methods: square(), cube(), average(), sum(), even() and odd().

Explanation:

square() must return a copy of the array, containing all values squared, the original array must not be changed
cube() must return a copy of the array, containing all values cubed, the original array must not be changed
average() must return the average of all array values, average() on an empty array must return NaN
sum() must return the sum of all array values
even() must return an array of all even numbers, the original array must not be changed
odd() must return an array of all odd numbers, the original array must not be changed

```javascript
Array.prototype.square = function() {
  return this.map((x)=> {
    return Math.pow(x,2)
  })
}


Array.prototype.cube = function() {
  return this.map((x)=> {
    return Math.pow(x,3)
  })
}

Array.prototype.average = function (){
  if(this.length === 0) {return NaN}
  return this.reduce(function(p, c) {return p+c;}) / this.length
}

Array.prototype.sum = function () {
  if(this.length === 0) {return 0}
  return this.reduce(function(a,b) {
    return a+b
  })
}

Array.prototype.even = function () {
  return this.filter(function(x) {
    return x % 2 == 0
  })
}

Array.prototype.odd = function () {
  return this.filter(function(x) {
    return x % 2 == 1
  })
}
```

## Persistent Bugger
https://www.codewars.com/kata/persistent-bugger

Write a function, persistence, that takes in a positive parameter num and returns its multiplicative persistence, which is the number of times you must multiply the digits in num until you reach a single digit.

```javascript
function persistence(num) {
   var times = 0;
   
   num = num.toString();
   
   while (num.length > 1) {
     times++;
     num = num.split('').map(Number).reduce((a, b) => a * b).toString();
   }
   
   return times;
}
```

## Decode the Morse code
https://www.codewars.com/kata/decode-the-morse-code

In this kata you have to write a simple Morse code decoder. While the Morse code is now mostly superceded by voice and digital data communication channels, it still has its use in some applications around the world.
The Morse code encodes every character as a sequence of "dots" and "dashes". For example, the letter A is coded as ·−, letter Q is coded as −−·−, and digit 1 is coded as ·−−−. The Morse code is case-insensitive, traditionally capital letters are used. When the message is written in Morse code, a single space is used to separate the character codes and 3 spaces are used to separate words. For example, the message HEY JUDE in Morse code is ···· · −·−−   ·−−− ··− −·· ·.

NOTE: Extra spaces before or after the code have no meaning and should be ignored.

In addition to letters, digits and some punctuation, there are some special service codes, the most notorious of those is the international distress signal SOS (that was first issued by Titanic), that is coded as ···−−−···. These special codes are treated as single special characters, and usually are transmitted as separate words.

Your task is to implement a function that would take the morse code as input and return a decoded human-readable string.

```javascript
decodeMorse = function(morseCode){
  var decodeString = '';
  var morseCodeWords = morseCode.split('   ');
  for (var i in morseCodeWords) {
    var morseCodeArray = morseCodeWords[i].split(' ');
    for (var j in morseCodeArray) {
      if (MORSE_CODE[morseCodeArray[j]] !== undefined) {
        decodeString += MORSE_CODE[morseCodeArray[j]];
      }
    }
    decodeString += ' ';
  }
  decodeString = decodeString.trim();  
  return decodeString;
}
```

## Counting Duplicates
https://www.codewars.com/kata/counting-duplicates

Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

```javascript
function duplicateCount(text){
  var arr = [], dupArr = [];
  for(var i=0; i<text.length; i++) {
    var t = text[i].toLowerCase();
    if(arr.indexOf(t)<0) arr.push(t);
    else if(dupArr.indexOf(t)<0) dupArr.push(t);
  }
  return dupArr.length;
}
```
