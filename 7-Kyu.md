# Total Complete: 27

## Easy Wallpaper
https://www.codewars.com/kata/easy-wallpaper

John wants to decorate a room with wallpaper. He has been said that making sure he has the right amount of wallpaper is more complex than it sounds. He wants a fool-proof method to getting it right.

John knows that the rectangular room has a length of l meters, a width of w meters, a height of h meters. The standard width of the rolls he wants to buy is 52 centimeters. The length of a roll is 10 meters. He bears in mind however, that it’s best to have an extra length of wallpaper handy in case of mistakes or miscalculations so he wants to buy a length 15% greater than the one he needs.

Last time he did these calculations he caught a headache so could you help John? Your function wallpaper(l, w, h) should return as a plain English word in lower case the number of rolls he must buy.

#Example: wallpaper(4, 3.5, 3) should return "ten"

#Notes:

all rolls (even with incomplete width) are put edge to edge
0 <= l, w, h (floating numbers), it can happens that w x h x l is zero
the integer r (number of rolls) will always be less or equal to 20

```javascript
function wallpaper(l,w,h){
	 var numbers = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine', 'ten', 'eleven', 'twelve', 'thirteen', 'fourteen', 'fifteen', 'sixteen', 'seventeen', 'eighteen', 'nineteen', 'twenty'];
	return !l || !w || !h ? 'zero' : numbers[Math.ceil(2*h*(l+w)/0.52/10 * 1.15)];
}
```
## Mumbling
https://www.codewars.com/kata/mumbling/train/javascript

This time no story, no theory. The examples below show you how to write function accum:

Examples:

accum("abcd");    // "A-Bb-Ccc-Dddd"
accum("RqaEzty"); // "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt");    // "C-Ww-Aaa-Tttt"
The parameter of accum is a string which includes only letters from a..z and A..Z.

```javascript
function accum(str){
	return str.split('').reduce((acc, val, index) => {
		acc.push(Array.apply(null, {length: index+1 }).map((x,i) => !i ? val.toUpperCase() : val.toLowerCase()).join(''))
		return acc
	}, []).join('-')
	
}
```

## Get The Middle Character
https://www.codewars.com/kata/get-the-middle-character

You are going to be given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.

```javascript
function mid(str){
	return str.length % 2 === 0 ? str[(str.length/2)-1] + str[(str.length/2)] 
	: str[Math.floor(str.length/2)]
}
```

## Isograms
https://www.codewars.com/kata/isograms/javascript

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

```javascript
function isIsogram(str){
	return str.toLowerCase().split('').reduce((acc, curr, ind, arr) => {
		if(acc){
			acc = arr.lastIndexOf(curr) !== ind ? false : true
		}
		return acc
	}, true)
}
```

## Growth of a Population
https://www.codewars.com/kata/growth-of-a-population/j

In a small town the population is p0 = 1000 at the beginning of a year. The population regularly increases by 2 percent per year and moreover 50 new inhabitants per year come to live in the town. How many years does the town need to see its population greater or equal to p = 1200 inhabitants?

More generally given parameters:

p0, percent, aug (inhabitants coming or leaving each year), p (population to surpass)

the function nb_year should return n number of entire years needed to get a population greater or equal to p.

aug is an integer, percent a positive or null number, p0 and p are positive integers (> 0)




```javascript
function nbYear(p0, percent, aug, p) {
    let count = 0
    while (p0 < p){
    	p0 += (p0 * (percent / 100) + aug)
    	count ++
    }
    return count
}
```

## Highest and Lowest
https://www.codewars.com/kata/highest-and-lowest/train/javascript

In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

Example:

highAndLow("1 2 3 4 5"); // return "5 1"
highAndLow("1 2 -3 4 5"); // return "5 -3"
highAndLow("1 9 3 4 -5"); // return "9 -5"
Notes:

All numbers are valid Int32, no need to validate them.
There will always be at least one number in the input string.
Output string must be two numbers separated by a single space, and highest number is first.


```javascript
function highAndLow(numbers){
  return `${Math.max(...numbers.split(' '))} ${Math.min(...numbers.split(' '))}`
}
```

## Shortest Word
https://www.codewars.com/kata/shortest-word/train/javascript

x Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.

```javascript
function findShort(s){
  s = s.split(' ');
  
  var shortest = s[0];
  
  for(var i = 0; i < s.length; i++){
    if(shortest.length > s[i].length){
      shortest = s[i];
    }
  }
  return shortest.length;
}
```

## Vowel Count
https://www.codewars.com/kata/vowel-count/train/javascript

Return the number (count) of vowels in the given string.

We will consider a, e, i, o, and u as vowels for this Kata.

The input string will only consist of lower case letters and/or spaces.

```javascript
function getCount(str) {
  return (str.match(/[aeiou]/ig)||[]).length;
}

```
## List Filtering
https://www.codewars.com/kata/list-filtering/train/javascript

In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

Example
filter_list([1,2,'a','b']) == [1,2]
filter_list([1,'a','b',0,15]) == [1,0,15]
filter_list([1,2,'aasf','1','123',123]) == [1,2,123]

```javascript
function filter_list(arr) {
	return arr.reduce((acc, curr) => {
		typeof curr === 'number' ? acc.push(curr) : null;
		return acc;
	}, []);
}
```

## Unique Sum
https://www.codewars.com/kata/unique-sum/train/javascript

Given a list of integers values, your job is to return the sum of the values; however, if the same integer value appears multiple times in the list, you can only count it once in your sum.

For example:

[ 1, 2, 3] ==> 6

[ 1, 3, 8, 1, 8] ==> 12

[ -1, -1, 5, 2, -7] ==> -1

[] ==> null
Good Luck!

```javascript
function uniqueSum(arr) {
	return !arr.length
		? null
		: [...new Set(arr)].reduce((acc, curr) => {
				acc += curr;
				return acc;
			});
}
```

## Find the smallest integer in an array
https://www.codewars.com/kata/find-the-smallest-integer-in-the-array/train/javascript

Given an array of integers your solution should find the smallest integer.

For example:
Given [34, 15, 88, 2] your solution will return 2
Given [34, -345, -1, 100] your solution will return -345
You can assume, for the purpose of this kata, that the supplied array will not be empty.

```javascript
class SmallestIntegerFinder {
	findSmallestInt(args) {
		return Math.min(...args);
	}
}
```
## Exes and Ohs
https://www.codewars.com/kata/exes-and-ohs/train/javascript

Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.

Examples input/output:

XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false
```javascript
function XO(str) {
	same = str.toLowerCase();
	let x = 0;
	let o = 0;
	for (var i = 0; i < same.length; i++) {
		if (same[i] === 'x') {
			x++;
		} else if (same[i] === 'o') {
			o++;
		}
	}
	return x === o;
}
```

## Beginner Series #3 Sum of Numbers
https://www.codewars.com/kata/beginner-series-number-3-sum-of-numbers/train/javascript

Given two integers a and b, which can be positive or negative, find the sum of all the numbers between including them too and return it. If the two numbers are equal return a or b.

Note: a and b are not ordered!

Examples
GetSum(1, 0) == 1   // 1 + 0 = 1
GetSum(1, 2) == 3   // 1 + 2 = 3
GetSum(0, 1) == 1   // 0 + 1 = 1
GetSum(1, 1) == 1   // 1 Since both are same
GetSum(-1, 0) == -1 // -1 + 0 = -1
GetSum(-1, 2) == 2  // -1 + 0 + 1 + 2 = 2


```javascript
function GetSum( a,b )
{
  var max = Math.max(a, b),
      current = Math.min(a, b),
      summ = 0;
  while (current <= max) {
    summ += current++;
  }
  return a === b ? a : summ;
}
```

## Square every number
https://www.codewars.com/kata/square-every-digit/train/javascript

Welcome. In this kata, you are asked to square every digit of a number.

For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

Note: The function accepts an integer and returns an integer

```javascript
squareDigits = (num) => {
  let numString = num.toString()
  let arr = []
  
  for(var i = 0; i < numString.length; i++) {
    arr[i] = numString[i] * numString[i]
  }
  return Number(arr.join(''))
  
}
```

## Descending Order
https://www.codewars.com/kata/descending-order/train/javascript


Your task is to make a function that can take any non-negative integer as a argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.

Examples:
Input: 21445 Output: 54421

Input: 145263 Output: 654321

Input: 1254859723 Output: 9875543221

```javascript
function descendingOrder(num) {
	return Number(
		num
		.toString(10)
		.split('')
		.sort((a, b) => {
			return b - a;
		})
		.join('')
	);
}
```

## Find the vowels
https://www.codewars.com/kata/find-the-vowels/train/javascript

We want to know the index of the vowels in a given word, for example, there are two vowels in the word super (the second and fourth letters).

So given a string "super", we should return a list of [2, 4].

Some examples:
Mmmm  => []
Super => [2,4]
Apple => [1,5]
YoMama -> [1,2,4,6]
NOTE: Vowels in this context refers to English Language Vowels - a e i o u y

NOTE: this is indexed from [1..n] (not zero indexed!)

```javascript
function vowelIndices(word) {
	word = word.toLowerCase();
	var results = [];
	var vowels = ['a', 'e', 'i', 'o', 'u', 'y'];
	for (var i = 0; i < word.length; i++) {
		if (vowels.indexOf(word[i]) >= 0) {
			results.push(i + 1);
		}
	}
	return results;
}
```

## No Oddities Here
https://www.codewars.com/kata/no-oddities-here/train/javascript

Write a small function that returns the values of an array that are not odd.

All values in the array will be integers. Return the good values in the order they are given.

```javascript
function noOdds(values) {
	return values.filter(x => {
		return !(x % 2) || !x;
	});
}
```

## Isograms
https://www.codewars.com/kata/isograms/train/javascript

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

```javascript
function isIsogram(str) {
	return str.toLowerCase().split('').reduce((acc, curr, ind, arr) => {
		if (acc) {
			acc = arr.lastIndexOf(curr) !== ind ? false : true;
		}
		return acc;
	}, true);
}
```


## Folding your way to the moon
https://www.codewars.com/kata/folding-your-way-to-the-moon/train/javascript

Have you heard about the myth that if you fold a paper enough times, you can reach the moon with it? Sure you do, but exactly how many? Maybe it's time to write a program to figure it out.

You know that a piece of paper has a thickness of 0.0001m. Given distance in units of meters, calculate how many times you have to fold the paper to make the paper reach this distance.
(If you're not familiar with the concept of folding a paper: Each fold doubles its total thickness.)

Note: Of course you can't do half a fold. You should know what this means ;P

Also, if somebody is giving you a non-positive distance, it's clearly bogus and you should yell at them by returning null (or whatever equivalent in your language).

```javascript
function foldTo(distance) {
  var paper = 0.0001;
  var counter = 0;
  if (distance > 0 ) {
    while (paper < distance) {
      paper = paper * 2;
      counter++;
    }
  }
    else {
      return null
    }
  return counter;
}
```

## Is this a triangle?
https://www.codewars.com/kata/is-this-a-triangle/train/javascript
Implement a method that accepts 3 integer values a, b, c. The method should return true if a triangle can be built with the sides of given length and false in any other case.

(In this case, all triangles must have surface greater than 0 to be accepted).

```javascript
function isTriangle(a, b, c) {
  let max = Math.max(a, b, c);
  let sum = a + b + c;
  return sum - max > max;
}
```

## Help Suzuki rake his garden!
https://www.codewars.com/kata/help-suzuki-rake-his-garden/train/javascript

Help Suzuki rake his garden!

The monastery has a magnificent Zen garden made of white gravel and rocks and it is raked diligently everyday by the monks. Suzuki having a keen eye is always on the lookout for anything creeping into the garden that must be removed during the daily raking such as insects or moss.

You will be given a string representing the garden such as:

garden = 'gravel gravel gravel gravel gravel gravel gravel gravel gravel rock slug ant gravel gravel snail rock gravel gravel gravel gravel gravel gravel gravel slug gravel ant gravel gravel gravel gravel rock slug gravel gravel gravel gravel gravel snail gravel gravel rock gravel snail slug gravel gravel spider gravel gravel gravel gravel gravel gravel gravel gravel moss gravel gravel gravel snail gravel gravel gravel ant gravel gravel moss gravel gravel gravel gravel snail gravel gravel gravel gravel slug gravel rock gravel gravel rock gravel gravel gravel gravel snail gravel gravel rock gravel gravel gravel gravel gravel spider gravel rock gravel gravel'
Rake out any items that are not a rock or gravel and replace them with gravel such that:

garden = 'slug spider rock gravel gravel gravel gravel gravel gravel gravel'
Returns a string with all items except a rock or gravel replaced with gravel:

garden = 'gravel gravel rock gravel gravel gravel gravel gravel gravel gravel'


```javascript
function rakeGarden(garden) {
	return garden
		.split(' ')
		.map(e => (e != 'rock' ? 'gravel' : 'rock'))
		.join(' ');
}
```

## The iccanobiF Sequence
https://www.codewars.com/kata/the-iccanobif-sequence/train/javascript

Your task is to create an array of size n with the values of the Fibonnaci sequence, and reverse the order in which the sequence is displayed.

For example: [1, 1, 2, 3, 5] would become [5, 3, 2, 1, 1]

You can assume that n will always be a positive integer between and including, 1 and 64.

Note: If you receive a server timeout - Check your code and re-run the tests.

```javascript
function iccanobif(num) {
  var newNum = num-1;
  var fibArr = []
  for(var i = 0; i <= newNum; i ++){
    fibArr.push((fibArr[i-1] || 1) + (fibArr[i-2] || 0))
  }
  return fibArr.reverse()
}
```

## The Coupon Code
https://www.codewars.com/kata/the-coupon-code/train/javascript

Your online store likes to give out coupons for special occasions. Some customers try to cheat the system by entering invalid codes or using expired coupons.

Your mission: 
Write a function called checkCoupon to verify that a coupon is valid and not expired. If the coupon is good, return true. Otherwise, return false.

A coupon expires at the END of the expiration date. All dates will be passed in as strings in this format: "June 15, 2014"

```javascript
function checkCoupon(enteredCode, correctCode, currentDate, expirationDate) {
  
  var convertCurrent = new Date(currentDate);
  var convertExpire = new Date(expirationDate);  
  
  if ((enteredCode === correctCode) && (convertCurrent <= convertExpire)) {
    return true;
  }
  return false;
};
```

## Find the next perfect square
https://www.codewars.com/kata/find-the-next-perfect-square/train/javascript

You might know some pretty large perfect squares. But what about the NEXT one?

Complete the findNextSquare method that finds the next integral perfect square after the one passed as a parameter. Recall that an integral perfect square is an integer n such that sqrt(n) is also an integer.

If the parameter is itself not a perfect square, than -1 should be returned. You may assume the parameter is positive.

Examples:

findNextSquare(121) --> returns 144
findNextSquare(625) --> returns 676
findNextSquare(114) --> returns -1 since 114 is not a perfect

```javascript
function findNextSquare(num) {
	return Math.sqrt(num) % 1 === 0 ? Math.pow(Math.sqrt(num) + 1, 2) : -1;
}
```

## Money, Money, Money
https://www.codewars.com/kata/money-money-money/train/javascript

Mr. Scrooge has a sum of money 'P' that wants to invest, and he wants to know how many years 'Y' this sum has to be kept in the bank in order for this sum of money to amount to 'D'.

The sum is kept for 'Y' years in the bank where interest 'I' is paid yearly, and the new sum is re-invested yearly after paying tax 'T'

Note that the principal is not taxed but only the year's accrued interest

Example:

  Let P be the Principal = 1000.00      
  Let I be the Interest Rate = 0.05      
  Let T be the Tax Rate = 0.18      
  Let D be the Desired Sum = 1100.00


After 1st Year -->
  P = 1041.00
After 2nd Year -->
  P = 1083.86
After 3rd Year -->
  P = 1128.30
Thus Mr. Scrooge has to wait for 3 years for the initial pricipal to ammount to the desired sum.

Your task is to complete the method provided and return the number of years 'Y' as a whole in order for Mr. Scrooge to get the desired sum.

Assumptions : Assume that Desired Principal 'D' is always greater than the initial principal, however it is best to take into consideration that if the Desired Principal 'D' is equal to Principal 'P' this should return 0 Years.

```javascript
function calculateYears(principal, interest, tax, desired) {
	let years = 0;
	while (principal < desired) {
		years++;
		income = principal * interest;
		principal += income - income * tax;
	}

	return years;
}
```

## Generate HTML links
https://www.codewars.com/kata/generate-html-links/train/javascript

We need a HTML menu.... but writing HTML over and-over-again is boooring... Let's just generate it instead!

Task:
Write a function generateMenu() with the following inputs/output:

Inputs:

menuItems: An array of objects (with url and text properties), which represents our menu items

Output:

A string of HTML containing an anchor tag for each element of menuItems (with the appropriate href attribute and text content)

```javascript
function generateMenu (menuItems) {
  var outputString = "";
  for (var i = 0; i < menuItems.length; i++){
    var anchorString = "<a href=\"" + menuItems[i].url + "\">" + menuItems[i].text + "</a>";
    outputString += anchorString;
  }
  return outputString;
}
```

## Hide password from URL
https://www.codewars.com/kata/hide-password-from-jdbc-url

We have to create a function that receives a connection string with password included and you have to mask the password i.e. change password by asterisks.

Preconditions:

non empty valid url
password always next to string section password=
assume password will not contain ampersand sign for sake of simplicity
to make it more real it has non ASCII characters
"password=" and "user" will occur only once

```javascript
function password(url) {
	return url.replace(
		/password=([^&]*)/,
		(_, pass) => `password=${'*'.repeat(pass.length)}`
	);
}
)
```
