
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
