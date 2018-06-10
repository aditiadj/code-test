# Simple Q&A Code

### Question 1

Implement the removeProperty function which takes an object and property name, and does the following:

If the object obj has a property prop, the function removes the property from the object and returns true; in all other cases it returns false.

Starting code:

```sh
function removeProperty(obj, prop) {
  return null;
}
```

### Solution 1

```sh
function removeProperty(obj, prop) {
if(prop in obj) {
  delete obj[prop];
  return true;
  } else {
  return false;
 }
}
```

### Question 2

Write a function that converts user entered date formatted as M/D/YYYY to a format required by an API (YYYYMMDD). The parameter "userDate" and the return value are strings.

For example, it should convert user entered date "12/31/2014" to "20141231" suitable for the API.

Starting code:

```sh
function formatDate(userDate) {
  // format from M/D/YYYY to YYYYMMDD
}

console.log(formatDate("12/31/2014"));
```

### Solution 2

```sh
function formatDate(userDate) {
  userDate = new Date(userDate);
  y = userDate.getFullYear().toString();
  m = (userDate.getMonth() + 1).toString();
  d = userDate.getDate().toString();
  if (m.length == 1) m = '0' + m;
  if (d.length == 1) d = '0' + d;
  return y + m + d;
}
```

### Question 3

An image gallery is a set of images with corresponding remove buttons. This is the HTML code for a gallery with two images:

```sh
<div class="image">
  <img src="https://goo.gl/kjzfbE" alt="First">
  <button class="remove">X</button>
</div>
<div class="image">
  <img src="https://goo.gl/d2JncW" alt="Second">
  <button class="remove">X</button>
</div>
```

Implement the setup function that registers a click event handler and implements the following logic: When the button of class remove is clicked, its parent <div> element should be removed from the gallery.

For example, after the first image has been removed from the gallery above, it's HTML code should look like this:

```sh
<div class="image">
  <img src="https://goo.gl/d2JncW" alt="Second">
  <button class="remove">X</button>
</div>
```

Starting code:

```sh
function setup () {
  // Write your code here.
}

// Example case.
document.body.innerHTML = `
<div class="image">
  <img src="https://goo.gl/kjzfbE" alt="First">
  <button class="remove">X</button>
</div>
<div class="image">
  <img src="https://goo.gl/d2JncW" alt="Second">
  <button class="remove">X</button>
</div>`;

setup();

$(".remove").get(0).click();
console.log(document.body.innerHTML);
```

### Solution 3

```sh
function setup() {
  var els = document.getElementsByClassName('remove');

for (var i = 0; i < els.length; i++) {
  els[i].addEventListener('click', function () {
    this.parentNode.remove();
  });
 }
}

// Example case.
document.body.innerHTML = `
<div class="image">
  <img src="https://goo.gl/kjzfbE" alt="First">
  <button class="remove">X</button>
</div>
<div class="image">
  <img src="https://goo.gl/d2JncW" alt="Second">
  <button class="remove">X</button>
</div>`;

setup();

$(".remove").get(0).click();
console.log(document.body.innerHTML);
```

### Question 4

The createProductCodeForm function is used to create a new form that accepts a product code from a user.

The current version of the form contains the hint: 'The product code can be found on the label'. This hint is currently always visible to the user.

Improve the form so that the hint is only rendered when the input element is the focused element.


Starting code:

```sh
function createProductCodeForm(parent) {
  var form = $("<form/>");

  form.append($("<label>").text('Product Code:'));
  form.append($("<input>").attr('name', 'productCode').attr('type', 'text'));
  form.append($("<label>").attr('name', 'hint').text('The product code can be found on the label.'));

  form.append('<br>');

  form.append($("<input>").attr('type', 'submit'));

  parent.append(form);
}
```

### Solution 4

```sh
function createProductCodeForm(parent) {
  var form = $("<form/>");

  form.append($("<label>").text('Product Code:'));
  form.append($("<input>").attr('name', 'productCode').attr('type', 'text').attr('onfocus','$("label[name]").show()').attr('onblur','$("label[name]").hide()'));
  form.append($("<label>").attr('name', 'hint').text('The product code can be found on the label.').attr('style','display:none'));

  form.append('<br>');

  form.append($("<input>").attr('type', 'submit'));

  parent.append(form);
}
createProductCodeForm($('.container'))
```

### Question 5

Will you make it?

You were camping with your friends far away from home, but when it's time to go back, you realize that you fuel is running out and the nearest pump is 50 miles away! You know that on average, your car runs on about 25 miles per gallon. There are 2 gallons left. Considering these factors, write a function that tells you if it is possible to get to the pump or not. Function should return true if it is possible and false if not.

### Sample Tests:

```sh
const assert = require("chai").assert;

describe("zeroFill", function() {
  it("Sample Tests", function() {
    assert.equal(zeroFuel(50, 25, 2), true);
    assert.equal(zeroFuel(100, 50, 1), false);
  });
});
```

### Solution 5

```sh
const zeroFuel = (distanceToPump, mpg, fuelLeft) => {
  return mpg * fuelLeft >= distanceToPump
};
```

### Question 6

How to determine if a number is odd or even?

### Solution 6

```sh
var input = prompt("How many numbers?");
var even = 0;
var odd = 0;

function printOddEven(input) {
	for (var i = 1; i <= input; i++) {
		if (i === 0) {
			document.write(i + " is even<br>");
			even++;
		} else if (i % 2 === 0) {
			document.write(i + " is even<br>");
			even++;			
		} else {
			document.write(i + " is odd<br>");
			odd++;
		}
	}
}

printOddEven(input);
alert("Total number of even: " + even + "\nTotal number of odd: " + odd);
```

### Question 7

If you found a syntax below:
```sh
function multiply(a, b){
  a * b
}
```

You just add console log and return a * b like the answer below

### Solution 7 

```sh
function multiply(a, b){
  console.log(a * b);
  return a * b;
}
```

### Question 8

Implement the ensure function so that it throws an error if called without arguments or the argument is undefined. Otherwise it should return the given value.

### Solution 8

```sh
 function noValueException(value) {
       this.value = value;
       this.name = 'noValueException';
    }

    function ensure(value) {
      if(value === undefined) {
          throw new noValueException('No argument passed');       
      } else { 
      return value;
      }
    }
```

### Question 9

Implement the removeProperty function which takes an object and property name, and does the following:

If the object obj has a property prop, the function removes the property from the object and returns true; in all other cases it returns false.

### Solution 9

```sh
function removeProperty(obj, prop) {
  if (obj[prop] !== undefined) {
    console.log(obj);
    delete obj[prop];
    return true;
  }
  return false;
};

var obj= {
  name:'Dono'
};

removeProperty(obj,'name');
```

### Question 10

Write a function that converts user entered date formatted as M/D/YYYY to a format required by an API (YYYYMMDD). The parameter "userDate" and the return value are strings.

For example, it should convert user entered date "12/31/2014" to "20141231" suitable for the API.

### Solution 10

```sh
function formatDate(userDate) {
  var parts = userDate.split('/');
  if (parts[0].length == 1) parts[0] = '0' + parts[0];
  if (parts[1].length == 1) parts[1] = '0' + parts[1];
  return parts[2] + parts[0] + parts[1];
}

console.log(formatDate("12/31/2014"));
```

### Question 11

Fix the bugs in the registerHandlers function. An alert should display anchor's zero-based index within a document instead of following the link.

For example, in the document below, the alert should display "2" when Google anchor is clicked since it is the third anchor element in the document and its zero-based index is 2.

```sh
<body>
  In my life, I used the following web search engines:<br/>
  <a href="//www.yahoo.com">Yahoo!</a><br/>
  <a href="//www.altavista.com">AltaVista</a><br/>
  <a href="//www.google.com">Google</a><br/>
</body>
```

### Solution 11

```sh
function registerHandlers() {
  var as = document.getElementsByTagName('a');
  for (var i = 0; i < as.length; i++) {
    as[i].onclick = (
      function(i){
        return function() {
          alert(i); 
          return false;
        }
      }(i)
    )      
  }
}

/* HTML code for testing purposes (do not submit uncommented):
<body>
  In my life, I used the following web search engines:<br/>
  <a href="//www.yahoo.com">Yahoo!</a><br/>
  <a href="//www.altavista.com">AltaVista</a><br/>
  <a href="//www.google.com">Google</a><br/>
</body>
*/
```

### Question 12

Implement the ensure function so that it throws an error if called without arguments or an argument is undefined. Otherwise it should return the given value.

### Solution 12

```sh
function noValueException(value) {
       this.value = value;
       this.name = 'noValueException';
    }

    function ensure(value) {
      if(value === undefined){
          throw new noValueException('No argument passed');       
      }else{ return value;}
    }
```

### Question 13

With the new HTML5 features, modify the form so that:

- The formula input field has an autocomplete option with the following options: "sin", "cos", "tan" and "cot".
- The iterations input field is a slider with possible values from 1 to 10.
- The precision input field is a number picker with possible values from 1 to 100, where 50 is the default value.

### Solution 13

```sh
<!DOCTYPE html>
<html>

  <head>
    <meta charset="utf-8">
    <title>Advanced form</title>
    <style type="text/css">
      
      a {
        text-decoration: none;
        text-transform: uppercase;
        cursor: help;
      }
      
      a:after {
        content: "<";
      }
      
      a:before {
        content: ">";
      }

    </style>
  </head>

  <body>
    <h1>
    Stylink link
    </h1>
    <a href="http://www.testdome.com">Check documentation</a>
    <br />
    <h1>
    
    Simple login form
    </h1>
    <form id="login">
      Email: <input type="email" name="email">
      <br>
      <br>
      Password: <input type="password" name="password">
      <input type="submit" value="Submit" name="submit">
    </form>
    <h1>
    Advanced form
    </h1>
    <form>
      Formula:
      <datalist id="op">
        <option value="sin">
          <option value="cos">
            <option value="tan">
              <option value="cot">
      </datalist>
      <input name="formula" list="op">
      <br /> Iterations:
      <input name="iterations" type="range" min="1" max="10" step="1" />
      <br /> Precision:
      <input name="precision" type="number" min="1" max="100" value="50" />
      <br />
    </form>
  </body>

</html>
```
### Question 14

Task
Given a Divisor and a Bound, Find the largest integer N, such that

Conditions :
- N is divisible by divisor
- N is less than or equal to bound
- N is greater than 0.

Notes
The parameters (divisor, bound) passed to the function are only positve values
It's guaranteed that a divisor is Found

Input > Output Examples:
```maxMultiple (2,7) ==> return (6)```

Explanation:
(6) is divisible by (2) , (6) is less than or equal to bound (7) , and (6) is > 0

### Solution 14

```
function maxMultiple(d, b) {
    return b-b%d
}
console.log(maxMultiple(2,7))
```

### Question 15

Given a number, write a function to output its reverse digits. (e.g. given 123 the answer is 321)

Numbers should preserve their sign; i.e. a negative number should still be negative when reversed.

Examples:
```
123 ->  321
-456 -> -654
1000 ->    1
```

### Solution 15

```
function reverseNumber(n) {
  const newNum = n.toString().split("").reverse().join("")
  return parseInt(newNum) * Math.sign(n)
}
```

### Question 16

Given a number, 3 for example, return a string with a murmur: "1 sheep...2 sheep...3 sheep..."

Note:
You will always receive a positive integer.

### Solution 16

```
let countSheep = num => {
  let str = `${num} sheep...`;
  return num == 1 ? str : countSheep(num - 1) + str;
} 
```

Thanks to [Github](https://github.com/skananitos/programmingChallenges/tree/master/html-css), [TestDome](https://www.testdome.com), [Codewars](https://www.codewars.com/) and [Stack Overflow](https://stackoverflow.com/)
