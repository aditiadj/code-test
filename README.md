# Q&A Code

### Question 1

Implement the removeProperty function which takes an object and property name, and does the following:

If the object obj has a property prop, the function removes the property from the object and returns true; in all other cases it returns false.

Starting code:

```sh
function removeProperty(obj, prop) {
  return null;
}
```

### Answer 1

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

### Answer 2

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

### Answer 3

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

#### Starting code:

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

### Answer 4

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

Thanks to [TestDome](https://www.testdome.com), [Stack Overflow](https://stackoverflow.com/) and [Codewars](https://www.codewars.com/)
