# Total Complete: 4

## Reverse it - quickly!
https://www.codewars.com/kata/reverse-it-quickly

Typically, reversing an array is a pretty straightforward task even for novice programmers. But not when a crowd of angry zombies scratching your door, looking for a fresh brains. In this case even skilled ninja-geek probably prefer to quickly push his code on github to have enough time to find a chainsaw. So there's two obstacles:

Your code needs to be as short as possible, in fact not longer than 28 characters
Because you are scared and stressed you have forgotten how to use the standard reverse() method
#Input: an array containing data of any types. Ex: [1,2,3,'a','b','c',[]]

#Output: [[],'c','b','a',3,2,1]

```javascript
turnaround=a=>a.sort(x=>1)
```

## Hello W... wait what?
https://www.codewars.com/kata/hello-w-dot-dot-dot-wait-what

In order to stop too much communication from happening, your overlords declare that you are no longer allowed to use certain functionality in your code!

Disallowed functionality:

Strings
Numbers
Regular Expressions
Functions named "Hello", "World", "HelloWorld" or anything similar.
Object keys named "Hello", "World", "HelloWorld" or anything similar.
Without using the above, output the string "Hello World!" to prove that there is always a way.


```javascript
let uas = () => {
  let emptyString = new String();
  let l = (new String(null)).split(emptyString).pop();
  
  let earr = (new String(undefined)).split(emptyString);
  let d = earr.pop();
  let e = earr.pop();
  
  let oarr = (new String(Object())).split(emptyString);
  oarr.shift(); 
  let o = oarr.shift();
  oarr.shift(); 
  oarr.shift(); 
  oarr.shift(); 
  oarr.shift(); 
  oarr.shift(); 
  let space = oarr.shift();
  let spaceCode = space.charCodeAt();
  spaceCode++;
  let excl = String.fromCharCode(spaceCode);
  
  let aarr = Array.name.split(emptyString);
  aarr.shift(); 
  let r = aarr.shift();
  
  let w = WeakMap.name.split(emptyString).shift();
  
  let marray = Math.toString().split(emptyString);
  marray.pop(); 
  let h = marray.pop().toUpperCase();
  
  return h+e+l+l+o+space+w+o+r+l+d+excl;
};

let helloWorld = uas;
```

## Sum of Intervals
https://www.codewars.com/kata/sum-of-intervals/

Write a function called sumIntervals/sum_intervals() that accepts an array of intervals, and returns the sum of all the interval lengths. Overlapping intervals should only be counted once.

Intervals
Intervals are represented by a pair of integers in the form of an array. The first value of the interval will always be less than the second value. Interval example: [1, 5] is an interval from 1 to 5. The length of this interval is 4.

Overlapping Intervals
List containing overlapping intervals:

[
   [1,4],
   [7, 10],
   [3, 5]
]
The sum of the lengths of these intervals is 7. Since [1, 4] and [3, 5] overlap, we can treat the interval as [1, 5], which has a length of 4.


```javascript
function sumIntervals(intervals) {
	let total = 0,
		i;
	intervals = intervals.sort((a, b) => {
		return a[0] > b[0];
	});
	if (intervals.length > 1) {
		intervals.forEach((x, i) => {
			if (
				intervals[i - 1][0] <= intervals[i][0] &&
				intervals[i][0] <= intervals[i - 1][1]
			) {
				if (intervals[i - 1][1] < intervals[i][1]) {
					intervals[i - 1][1] = intervals[i][1];
				}
				intervals.splice(i, 1);
				i--;
			}
		});
	}

	intervals.forEach((x, i) => {
		total += intervals[i][1] - intervals[i][0];
	});

	return total;
}

```

## Adding Big Numbers
https://www.codewars.com/kata/adding-big-numbers

We need to sum big numbers and we require your help.

Write a function that returns the sum of two numbers. The input numbers are strings and the function must return a string.

Example
add("123", "321"); -> "444"
add("11", "99"); -> "110"
Notes
The input numbers are big.
The input is a string of only digits
The numbers are positives

```javascript
function add(a, b) {
	let res = '',
	answer = 0;
	a = a.split('');
	b = b.split('');
	while (a.length || b.length || answer) {
		answer += ~~a.pop() + ~~b.pop();
		res = answer % 10 + res;
		answer = answer > 9;
	}
	return res;
}
```

