# Total Complete: 6

## Return Negative
https://www.codewars.com/kata/return-negative/train/javascript

In this simple assignment you are given a number and have to make it negative. But maybe the number is already negative?

Example:

makeNegative(1); // return -1
makeNegative(-5); // return -5
makeNegative(0); // return 0
Notes:

The number can be negative already, in which case no change is required.
Zero (0) can't be negative, see examples above.

```javascript
function makeNegative(num) {
return  Math.sign(num) < 0 ? num : num * -1
}
```

## Calculate BMI
https://www.codewars.com/kata/calculate-bmi/train/javascript

Write function bmi that calculates body mass index (bmi = weight / height ^ 2).

if bmi <= 18.5 return "Underweight"

if bmi <= 25.0 return "Normal"

if bmi <= 30.0 return "Overweight"

if bmi > 30 return "Obese"

```javascript
function bmi(weight, height) {
	var bodyMass = weight / Math.pow(height, 2);
	console.log(bodyMass);
	if (bodyMass <= 18.5) {
		return 'Underweight';
	} else if (bodyMass <= 25) {
		return 'Normal';
	} else if (bodyMass <= 30) {
		return 'Overweight';
	} else if (bodyMass > 30) {
		return 'Obese';
	}
}
```

## Find the Difference in Age between Oldest and Youngest Family Members
https://www.codewars.com/kata/find-the-difference-in-age-between-oldest-and-youngest-family-members/train/javascript

At the annual family gathering, the family likes to find the oldest living family member’s age and the youngest family member’s age and calculate the difference between them.

You will be given an array of all the family members' ages, in any order. The ages will be given in whole numbers, so a baby of 5 months, will have an ascribed ‘age’ of 0. Return a new array with [youngest age, oldest age, difference between the youngest and oldest age].

```javascript
function differenceInAges(ages) {
	var arr = [];
	var old = Math.max.apply(null, ages);
	var young = Math.min.apply(null, ages);
	arr.push(young, old, old - young);
	return arr;
}
```

## Grasshopper - If/else syntax debug
https://www.codewars.com/kata/grasshopper-if-slash-else-syntax-debug/train/javascript

While making a game, your partner, Greg, decided to create a function to check if the user is still alive called checkAlive/CheckAlive. Unfortunately, Greg made some errors while creating the function.

checkAlive/CheckAlive should return true if the player's health is greater than 0 or false if it is 0 or below.

checkAlive receives one parameter health which will always be a whole number between -10 and 10.

```javascript
function checkAlive (health) {
  if (health <= 0) {
    return false
  } 
  else if (health > 0) {
    return true
  }
}
```

## BASIC: Making Six Toast
https://www.codewars.com/kata/basic-making-six-toast/train/javascript

You are going to make toast fast, you think that you should make multiple pieces of toasts and once. So, you try to make 6 pieces of toast.
PROBLEM:
You forgot to count the number of toast you put into there, you don't know if you put exactly six pieces of toast into the toasters.
WHAT TO DO:
Make a function that counts how many more (or less) pieces of toast you need in the toasters. Even though you need more or less, the number will still be positive, not negative.

```javascript
function sixToast(num) {
  if (num > 5) {
  return num - 6
  }
  else {
  return num
  }
}
```

## Double Char
https://www.codewars.com/kata/double-char/train/javascript

Given a string, you have to return a string in which each character (case-sensitive) is repeated once.

```javascript
function doubleChar(str) {
 return str.split('').reduce((acc,curr) => {
  acc.push(curr.repeat(2))
  return acc
}, []).join('')
}
```
