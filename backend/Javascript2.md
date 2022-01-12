## Higher Order Function

Higher order functions are functions which take other function as a parameter or return a function as a value. The function passed as a parameter is called callback.

### Callback

A callback is a function which can be passed as parameter to other function. See the example below.

```js
// a callback function, the function could be any name
const callback = (n) => {
  return n ** 2
}
​
// function take other function as a callback
function cube(callback, n) {
  return callback(n) * n
}
​
console.log(cube(callback, 3))
```

### Returning function

Higher order functions return function as a value
​

```js
// Higher order function returning an other function
const higherOrder = (n) => {
  const doSomething = (m) => {
    const doWhatEver = (t) => {
      return 2 * n + 3 * m + t;
    };
    return doWhatEver;
  };
  return doSomething;
};
console.log(higherOrder(2)(3)(10));
```

Let us see were we use call back functions.For instance the _forEach_ method uses call back.

```js
const numbers = [1, 2, 3, 4]
​
const sumArray = arr => {
  let sum = 0
  const callBack = function(element) {
    sum += element
  }
  numbers.forEach(callback)
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

The above example can be simplified as follows:

```js
const numbers = [1, 2, 3, 4]
​
const sumArray = arr => {
  let sum = 0
  numbers.forEach(function(element) {
    sum += element
  })
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

### setting time

In JavaScript we can execute some activity on certain interval of time or we can schedule(wait) for sometime to execute some activities.

- setInterval
- setTimeout

#### setInterval

In JavaScript, we use setInterval higher order function to do some activity continuously with in some interval of time. The setInterval global method take a callback function and a duration as a parameter. The duration is in milliseconds and the callback will be always called in that interval of time.

```js
// syntax
function callBack() {
  // code goes here
}
setInterval(callback, duration);
```

```js
function sayHello() {
  console.log("Hello");
}
setInterval(sayHello, 2000); // it prints hello in every 2 seconds
```

#### setTimeout

In JavaScript, we use setTimeout higher order function to execute some action at some time in the future. The setTimeout global method take a callback function and a duration as a parameter. The duration is in milliseconds and the callback wait for that amount of time.

```js
// syntax
function callback() {
  // code goes here
}
setTimeout(callback, duration); // duration in milliseconds
```

```js
function sayHello() {
  console.log("Hello");
}
setTimeout(sayHello, 2000); // it prints hello after it waits for 2 seconds.
```

## Functional Programming

Instead of writing regular loop, latest version of JavaScript introduced lots of built in methods which can help us to solve complicated problems. All builtin methods take callback function. In this section, we will see _forEach_, _map_, _filter_, _reduce_, _find_, _every_, _some_, and _sort_.

### forEach

_forEach_: Iterate an array elements. We use _forEach_ only with arrays. It takes a callback function with elements, index parameter and array itself. The index and the array optional.

```js
arr.forEach(function (element, index, arr) {
  console.log(index, element, arr);
});
// The above code can be written using arrow function
arr.forEach((element, index, arr) => {
  console.log(index, element, arr);
});
// The above code can be written using arrow function and explicit return
arr.forEach((element, index, arr) => console.log(index, element, arr));
```

```js
let sum = 0;
const numbers = [1,2,3,4,5];
numbers.forEach(num => console.log(num)))

console.log(sum)
```

```sh
1
2
3
4
5
```

```js
let sum = 0;
const numbers = [1,2,3,4,5];
numbers.forEach(num => sum += num))

console.log(sum)
```

```sh
15
```

```js
const countries = ["Finland", "Denmark", "Sweden", "Norway", "Iceland"];
countries.forEach((element) => console.log(element.toUpperCase()));
```

```sh
FINLAND
DENMARK
SWEDEN
NORWAY
ICELAND
```

### map

_map_: Iterate an array elements and modify the array elements. It takes a callback function with elements, index , array parameter and return a new array.

```js
const modifiedArray = arr.map(function (element, index, arr) {
  return element;
});
```

```js
/*Arrow function and explicit return
const modifiedArray = arr.map((element,index) => element);
*/
//Example
const numbers = [1, 2, 3, 4, 5];
const numbersSquare = numbers.map((num) => num * num);

console.log(numbersSquare);
```

```sh
[1, 4, 9, 16, 25]
```

```js
const names = ["Asabeneh", "Mathias", "Elias", "Brook"];
const namesToUpperCase = names.map((name) => name.toUpperCase());
console.log(namesToUpperCase);
```

```sh
['ASABENEH', 'MATHIAS', 'ELIAS', 'BROOK']
```

```js
const countries = [
  "Albania",
  "Bolivia",
  "Canada",
  "Denmark",
  "Ethiopia",
  "Finland",
  "Germany",
  "Hungary",
  "Ireland",
  "Japan",
  "Kenya",
];
const countriesToUpperCase = countries.map((country) => country.toUpperCase());
console.log(countriesToUpperCase);

/*
// Arrow function
const countriesToUpperCase = countries.map((country) => {
  return country.toUpperCase();
})
//Explicit return arrow function
const countriesToUpperCase = countries.map(country => country.toUpperCase());
*/
```

```sh
['ALBANIA', 'BOLIVIA', 'CANADA', 'DENMARK', 'ETHIOPIA', 'FINLAND', 'GERMANY', 'HUNGARY', 'IRELAND', 'JAPAN', 'KENYA']
```

```js
const countriesFirstThreeLetters = countries.map((country) =>
  country.toUpperCase().slice(0, 3)
);
```

```sh
 ["ALB", "BOL", "CAN", "DEN", "ETH", "FIN", "GER", "HUN", "IRE", "JAP", "KEN"]
```

### filter

_Filter_: Filter out items which full fill filtering conditions and return a new array.

```js
//Filter countries containing land
const countriesContainingLand = countries.filter((country) =>
  country.includes("land")
);
console.log(countriesContainingLand);
```

```sh
['Finland', 'Ireland']
```

```js
const countriesEndsByia = countries.filter((country) => country.endsWith("ia"));
console.log(countriesEndsByia);
```

```sh
['Albania', 'Bolivia','Ethiopia']
```

```js
const countriesHaveFiveLetters = countries.filter(
  (country) => country.length === 5
);
console.log(countriesHaveFiveLetters);
```

```sh
['Japan', 'Kenya']
```

```js
const scores = [
  { name: "Asabeneh", score: 95 },
  { name: "Mathias", score: 80 },
  { name: "Elias", score: 50 },
  { name: "Martha", score: 85 },
  { name: "John", score: 100 },
];

const scoresGreaterEight = scores.filter((score) => score.score > 80);
console.log(scoresGreaterEight);
```

```sh
[{name: 'Asabeneh', score: 95}, {name: 'Martha', score: 85},{name: 'John', score: 100}]
```

### reduce

_reduce_: Reduce takes a callback function. The call back function takes accumulator, current, and optional initial value as a parameter and returns a single value. It is a good practice to define an initial value for the accumulator value. If we do not specify this parameter, by default accumulator will get array `first value`. If our array is an _empty array_, then `Javascript` will throw an error.

```js
arr.reduce((acc, cur) => {
  // some operations goes here before returning a value
  return;
}, initialValue);
```

```js
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, cur) => acc + cur, 0);

console.log(sum);
```

```js
15;
```

### every

_every_: Check if all the elements are similar in one aspect. It returns boolean

```js
const names = ["Asabeneh", "Mathias", "Elias", "Brook"];
const areAllStr = names.every((name) => typeof name === "string");

console.log(arrAllStr);
```

```sh
true
```

```js
const bools = [true, true, true, true];
const areAllTrue = bools.every((b) => {
  return b === true;
});

console.log(areAllTrue); //true
```

```sh
true

```

### find

_find_: Return the first element which satisfies the condition

```js
const ages = [24, 22, 25, 32, 35, 18];
const age = ages.find((age) => age < 20);

console.log(age);
```

```js
18;
```

```js
const names = ["Asabeneh", "Mathias", "Elias", "Brook"];
const result = names.find((name) => name.length > 7);
console.log(result);
```

```sh
Asabeneh
```

```js
const scores = [
  { name: "Asabeneh", score: 95 },
  { name: "Mathias", score: 80 },
  { name: "Elias", score: 50 },
  { name: "Martha", score: 85 },
  { name: "John", score: 100 },
];

const score = scores.find((user) => {
  return user.score > 80;
});
console.log(score);
```

```sh
{ name: "Asabeneh", score: 95 }
```

### findIndex

_findIndex_: Return the position of the first element which satisfies the condition

```js
const names = ["Asabeneh", "Mathias", "Elias", "Brook"];
const ages = [24, 22, 25, 32, 35, 18];

const result = names.findIndex((name) => name.length > 7);
console.log(result); // 0

const age = ages.findIndex((age) => age < 20);
console.log(age); // 5
```

### some

_some_: Check if some of the elements are similar in one aspect. It returns boolean

```js
const names = ["Asabeneh", "Mathias", "Elias", "Brook"];
const bools = [true, true, true, true];

const areSomeTrue = bools.some((b) => {
  return b === true;
});

console.log(areSomeTrue); //true
```

```js
const areAllStr = names.some((name) => typeof name === "number");
console.log(areAllStr); // false
```

### sort

_sort_: The sort methods arranges the array elements either ascending or descending order. By default, the **_sort()_** method sorts values as strings.This works well for string array items but not for numbers. If number values are sorted as strings and it give us wrong result. Sort method modify the original array. It is recommended to copy the original data before you start using _sort_ method.

#### Sorting string values

```js
const products = ["Milk", "Coffee", "Sugar", "Honey", "Apple", "Carrot"];
console.log(products.sort()); // ['Apple', 'Carrot', 'Coffee', 'Honey', 'Milk', 'Sugar']
//Now the original products array  is also sorted
```

#### Sorting Numeric values

As you can see in the example below, 100 came first after sorted in ascending order. Sort converts items to string , since '100' and other numbers compared, 1 which the beginning of the string '100' became the smallest. To avoid this, we use a compare call back function inside the sort method, which return a negative, zero or positive.

```js
const numbers = [9.81, 3.14, 100, 37];
// Using sort method to sort number items provide a wrong result. see below
console.log(numbers.sort()); //[100, 3.14, 37, 9.81]
numbers.sort(function (a, b) {
  return a - b;
});

console.log(numbers); // [3.14, 9.81, 37, 100]

numbers.sort(function (a, b) {
  return b - a;
});
console.log(numbers); //[100, 37, 9.81, 3.14]
```

#### Sorting Object Arrays

When ever we sort objects in an array. We use the object key to compare. Lets see the example below.

```js
objArr.sort(function (a, b) {
  if (a.key < b.key) return -1;
  if (a.key > b.key) return 1;
  return 0;
});

// or

objArr.sort(function (a, b) {
  if (a["key"] < b["key"]) return -1;
  if (a["key"] > b["key"]) return 1;
  return 0;
});

const users = [
  { name: "Asabeneh", age: 150 },
  { name: "Brook", age: 50 },
  { name: "Eyo", age: 100 },
  { name: "Elias", age: 22 },
];
users.sort((a, b) => {
  if (a.age < b.age) return -1;
  if (a.age > b.age) return 1;
  return 0;
});
console.log(users); // sorted ascending
//[{…}, {…}, {…}, {…}]
```

🌕 You are doing great.Never give up because great things take time. You have just completed day 9 challenges and you are 9 steps a head in to your way to greatness. Now do some exercises for your brain and for your muscle.

## 💻 Exercises

### Exercises: Level 1

```js
const countries = ["Finland", "Sweden", "Denmark", "Norway", "IceLand"];
const names = ["Asabeneh", "Mathias", "Elias", "Brook"];
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const products = [
  { product: "banana", price: 3 },
  { product: "mango", price: 6 },
  { product: "potato", price: " " },
  { product: "avocado", price: 8 },
  { product: "coffee", price: 10 },
  { product: "tea", price: "" },
];
```

1. Explain the difference between **_forEach, map, filter, and reduce_**.
2. Define a call function before you them in forEach, map, filter or reduce.
3. Use **_forEach_** to console.log each country in the countries array.
4. Use **_forEach_** to console.log each name in the names array.
5. Use **_forEach_** to console.log each number in the numbers array.
6. Use **_map_** to create a new array by changing each country to uppercase in the countries array.
7. Use **_map_** to change to each name to uppercase in the names array
8. Use **_map_** to map the products array to its corresponding prices.
9. Use **_filter_** to filter out countries containing **_land_**.
10. Use **_filter_** to filter out countries having six character.
11. Use **_filter_** to filter out countries containing six letters and more in the country array.
12. Use **_filter_** to filter out country start with 'E';
13. Use **_filter_** to filter out only prices with values.
14. Declare a function called getStringLists which takes an array as a parameter and then returns an array only with string items.
15. Use **_reduce_** to sum all the numbers in the numbers array.
16. Use **_reduce_** to concatenate all the countries and to produce this sentence: **_Estonia, Finland, Sweden, Denmark, Norway, and IceLand are north European countries_**
17. Explain the difference between **_some_** and **_every_**
18. Use **_some_** to check if some names' length greater than seven in names array
19. Use **_every_** to check if all the countries contain the word land
20. Explain the difference between **_find_** and **_findIndex_**.
    Use **_find_** to find the first country containing only six letters in the countries array
21. Use **_findIndex_** to find the position of the first country containing only six letters in the countries array
22. Use **_findIndex_** to find the position of **_Norway_** if it doesn't exist in the array you will get -1.
23. Use **_findIndex_** to find the position of **_Russia_** if it doesn't exist in the array you will get -1.

### Exercises: Level 2

1. Find the total price of products by chaining two or more array iterators(eg. arr.map(callback).filter(callback).reduce(callback))
1. Find the sum of price of products using only reduce reduce(callback))
1. Declare a function called **_categorizeCountries_** which returns an array of countries which have some common pattern(you find the countries array in this repository as countries.js(eg 'land', 'ia', 'island','stan')).
1. Create a function which return an array of objects, which is the letter and the number of times the letter use to start with a name of a country.
1. Declare a **_getFirstTenCountries_** function and return an array of ten countries. Use different functional programming to work on the countries.js array
1. Declare a **_getLastTenCountries_** function which which returns the last ten countries in the countries array.
1. Find out which _letter_ is used many _times_ as initial for a country name from the countries array (eg. Finland, Fiji, France etc)

## Destructuring and Spread

Destructuring is a way to unpack arrays, and objects and assigning to a distinct variable.

### Destructing Arrays

```js
const numbers = [1, 2, 3];
let [numOne, numTwo, numThree] = numbers;

console.log(numOne, numTwo, numThree);
```

```sh
  1 2 3
```

const class = [classhhhhhhhh a, class b, class c];
let [toyin,tola,titi] = class;
log(toyin)

```js
  const names = ['Asabeneh', 'Brook', 'David', 'John']
  let [firstPerson, secondPerson, thirdPerson, fourth Person] = names

  console.log(firstName, secondPerson,thirdPerson, fourthPerson)
```

```sh
Asabeneh Brook David John
```

```js
const scientificConstants = [2.72, 3.14, 9.81, 37, 100];
let [e, pi, gravity, bodyTemp, boilingTemp] = scientificConstants;

console.log(e, pi, gravity, bodyTemp, boilingTemp);
```

```sh
2.72 3.14 9.81 37 100
```

```js
const fullStack = [
  ["HTML", "CSS", "JS", "React"],
  ["Node", "Express", "MongoDB"],
];
const [frontEnd, backEnd] = fullStack;

console.log(frontEnd);
console.log(backEnd);
```

```sh
["HTML", "CSS", "JS", "React"]
["Node", "Express", "MongoDB"]
```

If we like to skip on of the values in the array we use additional comma. The comma helps to omit the value at that specific index

```js
const numbers = [1, 2, 3];
let [numOne, , numThree] = numbers; //2 is omitted

console.log(numOne, numThree);
```

```sh
1 3
```

```js
const names = ["Asabeneh", "Brook", "David", "John"];
let [, secondPerson, , fourthPerson] = name; // first and third person is omitted
console.log(secondPerson, fourthPerson);
```

```sh
Brook John
```

We can use default value in case the value of array for that index is undefined:

```js
const names = [undefined, "Brook", "David"];
let [
  firstPerson = "Asabeneh",
  secondPerson,
  thirdPerson,
  fourthPerson = "John",
] = names;

console.log(firstPerson, secondPerson, thirdPerson, fourthPerson);
```

```sh
Asabeneh Brook David John
```

We can not assign variable to all the elements in the array. We can destructure few of the first and we can get the remaining as array using spread operator(...).

```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let [num1, num2, num3, ...rest] = nums;

console.log(num1, num2, num3);
console.log(rest);
```

```sh
1 2 3
[4, 5, 6, 7, 8, 9, 10]
```

### Destructuring during iteration

```js
const countries = [
  ["Finland", "Helsinki"],
  ["Sweden", "Stockholm"],
  ["Norway", "Oslo"],
];

for (const [country, city] of countries) {
  console.log(country, city);
}
```

```sh
Finland Helsinki
Sweden Stockholm
Norway Oslo
```

```js
const fullStack = [
  ["HTML", "CSS", "JS", "React"],
  ["Node", "Express", "MongoDB"],
];

for (const [first, second, third] of fullStack) {
  console.log(first, second, third);
}
```

```sh
HTML CSS JS
Node Express MongoDB
```

### Destructuring Object

When we destructure the name of the variable we use to destructure should be exactly the same as the key or property of the object. See the example below.

```js
const rectangle = {
  width: 20,
  height: 10,
  area: 200,
};
let { width, height, area, perimeter } = rectangle;

console.log(width, height, area, perimeter);
```

```sh
20 10 200 undefined
```

### Renaming during structuring

```js
const rectangle = {
  width: 20,
  height: 10,
  area: 200,
};
let { width: w, heigh: h, area: a, perimeter: p } = rectangle;

console.log(w, h, a, p);
```

```sh
20 10 200 undefined
```

If the key is not found in the object the variable will be assigned to undefined. In case, the key is not in the object we can give a default value during declaration. See the example.

```js
const rectangle = {
  width: 20,
  height: 10,
  area: 200,
};
let { width, heigh, area, perimeter = 60 } = rectangle;

console.log(width, height, area, perimeter); //20 10 200 60
//Lets modify the object:width to 30 and perimeter to 80
```

```js
const rectangle = {
  width: 30,
  height: 10,
  area: 200,
  perimeter: 80,
};
let { width, heigh, area, perimeter = 60 } = rectangle;
console.log(width, height, area, perimeter); //20 10 200 60
```

Destructuring keys as a function parameters. Lets create a function which take a rectangle object and it return a perimeter of a rectangle.

### Object parameter without destructuring

```js
// Without destructuring
const rect = {
  width: 20,
  height: 10,
};
const calculatePerimeter = (rect) => {
  let {width,height} = rect
  log(width)= //20
  return 2 * (width + height);
};

console.log(calculatePerimeter(rect)); // 60
//with destructuring
```

```js
//Another Example
const person = {
  firstName: "Asabeneh",
  lastName: "Yetayeh",
  age: 250,
  country: "Finland",
  job: "Instructor and Developer",
  skills: [
    "HTML",
    "CSS",
    "JavaScript",
    "React",
    "Redux",
    "Node",
    "MongoDB",
    "Python",
    "D3.js",
  ],
  languages: ["Amharic", "English", "Suomi(Finnish)"],
};
// Lets create a function which give information about the person object without destructuring

const getPersonInfo = (obj) => {
  const skills = obj.skills;
  const formattedSkills = skills.slice(0, -1).join(", ");
  const languages = obj.languages;
  const formattedLanguages = languages.slice(0, -1).join(", ");

  personInfo = `${obj.firstName} ${obj.lastName} lives in ${
    obj.country
  }. He is  ${obj.age} years old. He is an ${
    obj.job
  }. He teaches ${formattedSkills} and ${
    skills[skills.length - 1]
  }. He speaks ${formattedLanguages} and a little bit of ${languages[2]}.`;

  return personInfo;
};

console.log(getPersonInfo(person));
```

### Object parameter with destructuring

```js
const calculatePerimeter = ({ width, height }) => {
  return 2 * (width + height);
};

console.log(calculatePerimeter(rect)); // 60
```

```js
// Lets create a function which give information about the person object with destructuring
const getPersonInfo = ({
  firstName,
  lastName,
  age,
  country,
  job,
  skills,
  languages,
}) => {
  const formattedSkills = skills.slice(0, -1).join(", ");
  const formattedLanguages = languages.slice(0, -1).join(", ");

  personInfo = `${firstName} ${lastName} lives in ${country}. He is ${age} years old. He is an ${job}. He teaches ${formattedSkills} and ${
    skills[skills.length - 1]
  }. He speaks ${formattedLanguages} and a little bit of ${languages[2]}.`;

  return personInfo;
};
console.log(getPersonInfo(person));
/*
Asabeneh Yetayeh lives in Finland. He is  200 years old. He is an Instructor and Developer. He teaches HTML, CSS, JavaScript, React, Redux, Node, MongoDB, Python and D3.js. He speaks Amharic, English and a little bit of Suomi(Finnish)
*/
```

### Destructuring object during iteration

```js
const todoList = [
  {
    task: "Prepare JS Test",
    time: "4/1/2020 8:30",
    completed: true,
  },
  {
    task: "Give JS Test",
    time: "4/1/2020 10:00",
    completed: false,
  },
  {
    task: "Assess Test Result",
    time: "4/1/2020 1:00",
    completed: false,
  },
];

for (const { task, time, completed } of todoList) {
  console.log(task, time, completed);
}
```

```sh
Prepare JS Test 4/1/2020 8:30 true
Give JS Test 4/1/2020 10:00 false
Assess Test Result 4/1/2020 1:00 false
```

### Spread or Rest Operator

When we destructure an array we use the spread operator(...) to get the rest elements as array. In addition to that we use spread operator to spread arr elements to another array.

### Spread operator to get the rest of array elements

```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
let [num1, num2, num3, ...rest] = nums
​
console.log(num1, num2, num3)
console.log(rest)
```

```sh
1 2 3
[4, 5, 6, 7, 8, 9, 10]
```

```js
const countries = [
  "Germany",
  "France",
  "Belgium",
  "Finland",
  "Sweden",
  "Norway",
  "Denmark",
  "Iceland",
];

let [gem, fra, , ...nordicCountries] = countries;

console.log(gem);
console.log(fra);
console.log(nordicCountries);
```

```sh
Germany
France
["Finland", "Sweden", "Norway", "Denmark", "Iceland"]
```

### Spread operator to copy array

```js
const evens = [0, 2, 4, 6, 8, 10];
const evenNumbers = [...evens];

const odds = [1, 3, 5, 7, 9];
const oddNumbers = [...odds];

const wholeNumbers = [...evens, ...odds];

console.log(evenNumbers);
console.log(oddNumbers);
console.log(wholeNumbers);
```

```sh
[0, 2, 4, 6, 8, 10]
[1, 3, 5, 7, 9]
[0, 2, 4, 6, 8, 10, 1, 3, 5, 7, 9]
```

```js
const frontEnd = ["HTML", "CSS", "JS", "React"];
const backEnd = ["Node", "Express", "MongoDB"];
const fullStack = [...frontEnd, ...backEnd];

console.log(fullStack);
```

```sh
["HTML", "CSS", "JS", "React", "Node", "Express", "MongoDB"]
```

### Spread operator to copy object

We can copy an object using a spread operator

```js
const user = {
  name: "Asabeneh",
  title: "Programmer",
  country: "Finland",
  city: "Helsinki",
};

const copiedUser = { ...user };
console.log(copiedUser);
```

```sh
{name: "Asabeneh", title: "Programmer", country: "Finland", city: "Helsinki"}
```

Modifying or changing the object while copying

```js
const user = {
  name: "Asabeneh",
  title: "Programmer",
  country: "Finland",
  city: "Helsinki",
};

const copiedUser = { ...user, title: "instructor" };
console.log(copiedUser);
```

```sh
{name: "Asabeneh", title: "instructor", country: "Finland", city: "Helsinki"}
```

#### Spread operator with arrow function

Whenever we like to write an arrow function which takes unlimited number of arguments we use a spread operator. If we use a spread operator as a parameter, the argument passed when we invoke a function will change to an array.

```js
const sumAllNums = (...args) => {
  console.log(args);
};

sumAllNums(1, 2, 3, 4, 5);
```

```sh
[1, 2, 3, 4, 5]

```

```js
const sumAllNums = (...args) => {
  let sum = 0;
  for (const num of args) {
    sum += num;
  }
  return sum;
};

console.log(sumAllNums(1, 2, 3, 4, 5));
```

```sh
15

```

## Exercises

### Exercises: Level 1

```js
const constants = [2.72, 3.14, 9.81, 37, 100];
const countries = ["Finland", "Estonia", "Sweden", "Denmark", "Norway"];
const rectangle = {
  width: 20,
  height: 10,
  area: 200,
  perimeter: 60,
};
const users = [
  {
    name: "Brook",
    scores: 75,
    skills: ["HTM", "CSS", "JS"],
    age: 16,
  },
  {
    name: "Alex",
    scores: 80,
    skills: ["HTM", "CSS", "JS"],
    age: 18,
  },
  {
    name: "David",
    scores: 75,
    skills: ["HTM", "CSS"],
    age: 22,
  },
  {
    name: "John",
    scores: 85,
    skills: ["HTML"],
    age: 25,
  },
  {
    name: "Sara",
    scores: 95,
    skills: ["HTM", "CSS", "JS"],
    age: 26,
  },
  {
    name: "Martha",
    scores: 80,
    skills: ["HTM", "CSS", "JS"],
    age: 18,
  },
  {
    name: "Thomas",
    scores: 90,
    skills: ["HTM", "CSS", "JS"],
    age: 20,
  },
];
```

1. Destructure and assign the elements of constants array to e, pi, gravity, humanBodyTemp, waterBoilingTemp.
2. Destructure and assign the elements of countries array to fin, est, sw, den, nor
3. Destructure the rectangle object by its properties or keys.

### Exercises: Level 2

1. Iterate through the users array and get all the keys of the object using destructuring
2. Find the persons who have less than two skills

### Exercises: Level 3

1. Destructure the countries object print name, capital, population and languages of all countries
2. A junior developer structure student name, skills and score in array of arrays which may not easy to read. Destructure the following array name to name, skills array to skills, scores array to scores, JavaScript score to jsScore and React score to reactScore variable in one line.

```js
const student = ["David", ["HTML", "CSS", "JS", "React"], [98, 85, 90, 95]];
console.log(name, skills, jsScore, reactScore);
let student = [
  "David",
  ["HTML", "CSS", "JS", "React"],
  [98, 85, 90, 95],
].reduce((name, skills) => ({ ...name, [skills]: skills }), {});
```

```sh
David (4) ["HTM", "CSS", "JS", "React"] 90 95
```

3. Write a function called _convertArrayToObject_ which can convert the array to a structure object.

```js
const students = [
  ["David", ["HTM", "CSS", "JS", "React"], [98, 85, 90, 95]],
  ["John", ["HTM", "CSS", "JS", "React"], [85, 80, 85, 80]],
];

console.log(convertArrayToObject(students))[
  ({
    name: "David",
    skills: ["HTM", "CSS", "JS", "React"],
    scores: [98, 85, 90, 95],
  },
  {
    name: "John",
    skills: ["HTM", "CSS", "JS", "React"],
    scores: [85, 80, 85, 80],
  })
];
```

## Document Object Model (DOM) - Day 1

HTML document is structured as a JavaScript Object. Every HTML element has a different properties which can help to manipulate it. It is possible to get, create, append or remove HTML elements using JavaScript. Check the examples below. Selecting HTML element using JavaScript is similar to selecting using CSS. To select an HTML element, we use tag name, id, class name or other attributes.

### Getting Element

We can access already created element or elements using JavaScript. To access or get elements we use different methods. The code below has four _h1_ elements. Let us see the different methods to access the _h1_ elements.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>
  <body>
    <h1 class="title" id="first-title">First Title</h1>
    <h1 class="title" id="second-title">Second Title</h1>
    <h1 class="title" id="third-title">Third Titl9ike</h1>
  </body>
</html>
```

#### Getting elements by tag name

**_getElementsByTagName()_**:takes a take name as a string parameter and this method returns an HTMLCollection object. An HTMLCollection is an array like object of HTML elements. The length property provides the size of the collection. Whenever we use this method we access the individual elements using index or after loop through each individual items. An HTMLCollection does not support all array methods therefore we should use regular for loop instead of forEach.

```js
// syntax
document.getElementsByTagName("tagname");
```

```js
const allTitles = document.getElementsByTagName("h1");

console.log(allTitles); //HTMCollections
console.log(allTitles.length); // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]); // prints each elements in the HTMLCollection
}
```

#### Getting elements by class name

**_getElementsByClassName()_** method returns an HTMLCollection object. An HTMLCollection is an array like list of HTML elements. The length property provides the size of the collection. It is possible to loop through all the HTMLCollection elements. See the example below

```js
//syntax
document.getElementsByClassName("classname");
```

```js
const allTitles = document.getElementsByClassName("title");

console.log(allTitles); //HTMCollections
console.log(allTitles.length); // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]); // prints each elements in the HTMLCollection
}
```

#### Getting an element by id

**_getElementsById()_** targets a single HTML element. We pass the id without # as an argument.

```js
//syntax
document.getElementById("id");
```

```js
let firstTitle = document.getElementById("first-title");
console.log(firstTitle); // <h1>First Title</h1>
```

#### Getting elements by using querySelector methods

The _document.querySelector_ method can select an HTML or HTML elements by tag name, by id or by class name.

**_querySelector_**: can be used to select HTML element by its tag name, id or class. If the tag name is used it selects only the first element.

```js
let firstTitle = document.querySelector("h1"); // select the first available h2 element
let firstTitle = document.querySelector("#first-title"); // select id with first-title
let firstTitle = document.querySelector(".title"); // select the first available h2 element with class title
```

**_querySelectorAll_**: can be used to select html element by its tag name or class. It return a nodeList which is an array like object which support array methods. We can use **_for loop_** or **_forEach_** to loop through each nodeList elements.

```js
const allTitles = document.querySelectorAll("h1");

console.log(allTitles.length); // 4
for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]);
}

allTitles.forEach((title) => console.log(title));
const allTitles = document.querySelectorAll(".title"); // the same goes for selecting using class
```

### Adding attribute

An attribute is added in the opening tag of HTML which gives additional information about the element. Common HTML attributes: id, class, src, style, href,disabled, title, alt. Lets add id and class for the fourth title.

```js
const titles = document.querySelectorAll("h1");
titles[3].class = "title";
titles[3].id = "fourth-title";
```

#### Adding attribute using setAttribute

The **_setAttribute()_** method set any html attribute. It takes two parameters the type of the attribute and the name of the attribute.
Let's add class and id attribute for the fourth title.

```js
const titles = document.querySelectorAll("h1");
titles[3].setAttribute("class", "title");
titles[3].setAttribute("id", "fourth-title");
```

#### Adding attribute without setAttribute

We can use normal object setting method to set an attribute but this can not work for all elements. Some attributes are DOM object property and they can be set directly. For instance id and class

```js
//another way to setting an attribute
titles[3].className = "title";
titles[3].id = "fourth-title";
```

#### Adding class using classList

The class list method is a good method to append additional class. It does not override the original class if a class exists rather it adds additional class for the element.

```js
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.add("title", "header-title");
```

#### Removing class using remove

Similar to adding we can also remove class from an element. We can remove a specific class from an element.

```js
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.remove("title", "header-title");
```

### Adding Text to HTML element

An HTML is a build block of an opening tag, a closing tag and a text content. We can add a text content using the property _textContent_ or \*innerHTML.

#### Adding Text content using textContent

The _textContent_ property is used to add text to an HTML element.

```js
const titles = document.querySelectorAll("h1");
titles[3].textContent = "Fourth Title";
```

#### Adding Text Content using innHTML

Most people get confused between _textContent_ and _innerHTML_. _textContent_ is meant to add text to an HTML element, however innerHTML can add a text or HTML element or elements as a child.

##### Text Content

We assign _textContent_ HTML object property to a text

```js
const titles = document.querySelectorAll("h1");
titles[3].textContent = "Fourth Title";
```

##### Inner HTML

We use innerHTML property when we like to replace or a completely new children content to a parent element.
It value we assign is going to be a string of HTML elements.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
      <h1>Asabeneh Yetayeh challenges in 2020</h1>
      <h2>30DaysOfJavaScript Challenge</h2>
      <ul></ul>
    </div>
    <script>
      const lists = `
    <li>30DaysOfPython Challenge Done</li>
            <li>30DaysOfJavaScript Challenge Ongoing</li>
            <li>30DaysOfReact Challenge Coming</li>
            <li>30DaysOfReactNative Challenge Coming</li>
            <li>30DaysOfMachineLearning Challenge Coming</li>`;
      const ul = document.querySelector("ul");
      ul.innerHTML = lists;
    </script>
  </body>
</html>
```

The innerHTML property can allow us also to remove all the children of a parent element. Instead of using removeChild() I would recommend the following method.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
      <h1>Asabeneh Yetayeh challenges in 2020</h1>
      <h2>30DaysOfJavaScript Challenge</h2>
      <ul>
        <li>30DaysOfPython Challenge Done</li>
        <li>30DaysOfJavaScript Challenge Ongoing</li>
        <li>30DaysOfReact Challenge Coming</li>
        <li>30DaysOfFullStack Challenge Coming</li>
        <li>30DaysOfDataAnalysis Challenge Coming</li>
        <li>30DaysOfReactNative Challenge Coming</li>
        <li>30DaysOfMachineLearning Challenge Coming</li>
      </ul>
    </div>
    <script>
      const ul = document.querySelector("ul");
      ul.innerHTML = "";
    </script>
  </body>
</html>
```

### Adding style

#### Adding Style Color

Let us add some style to our titles. If the element has even index we give it green color else red.

```js
const titles = document.querySelectorAll("h1");
titles.forEach((title, i) => {
  title.style.fontSize = "24px"; // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.color = "green";
  } else {
    title.style.color = "red";
  }
});
```

#### Adding Style Background Color

Let us add some style to our titles. If the element has even index we give it green color else red.

```js
const titles = document.querySelectorAll("h1");
titles.forEach((title, i) => {
  title.style.fontSize = "24px"; // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.backgroundColor = "green";
  } else {
    title.style.backgroundColor = "red";
  }
});
```

#### Adding Style Font Size

Let us add some style to our titles. If the element has even index we give it 20px else 30px

```js
const titles = document.querySelectorAll("h1");
titles.forEach((title, i) => {
  title.style.fontSize = "24px"; // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.fontSize = "20px";
  } else {
    title.style.fontSize = "30px";
  }
});
```

As you have notice, the properties of css when we use it in JavaScript is going to be a camelCase. The following CSS properties change from background-color to backgroundColor, font-size to fontSize, font-family to fontFamily, margin-bottom to marginBottom.

---

🌕 Now, you are fully charged with a super power, you have completed the most important and challenging part of the challenge and in general JavaScript. You learned DOM and now you have the capability to build and develop applications. Now do some exercises for your brain and for your muscle.

## Exercises

### Exercise: Level 1

1. Create an index.html file and put four p elements as above: Get the first paragraph by using **_document.querySelector(tagname)_** and tag name
2. Get get each of the the paragraph using **_document.querySelector('#id')_** and by their id
3. Get all the p as nodeList using **_document.querySelectorAll(tagname)_** and by their tag name
4. Loop through the nodeList and get the text content of each paragraph
5. Set a text content to paragraph the fourth paragraph,**_Fourth Paragraph_**
6. Set id and class attribute for all the paragraphs using different attribute setting methods

## DOM(Document Object Model)-Day 2

### Creating an Element

To create an HTML element we use tag name. Creating an HTML element using JavaScript is very simple and straight forward. We use the method _document.createElement()_. The method takes an HTML element tag name as a string parameter.

```js
// syntax
document.createElement("tagname");
```

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <script>
      let title = document.createElement("h1");
      title.className = "title";
      title.style.fontSize = "24px";
      title.textContent = "Creating HTML element DOM Day 2";

      console.log(title);
    </script>
  </body>
</html>
```

### Creating elements

To create multiple elements we should use loop. Using loop we can create as many HTML elements as we want.
After we create the element we can assign value to the different properties of the HTML object.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <script>
      let title;
      for (let i = 0; i < 3; i++) {
        title = document.createElement("h1");
        title.className = "title";
        title.style.fontSize = "24px";
        title.textContent = i;
        console.log(title);
      }
    </script>
  </body>
</html>
```

### Appending child to a parent element

To see a created element on the HTML document we should append it to the parent as a child element. We can access the HTML document body using _document.body_. The _document.body_ support the _appendChild()_ method. See the example below.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Days Of JavaScript</title>
  </head>

  <body>
    <script>
      // creating multiple elements and appending to parent element
      let title;
      for (let i = 0; i < 3; i++) {
        title = document.createElement("h1");
        title.className = "title";
        title.style.fontSize = "24px";
        title.textContent = i;
        document.body.appendChild(title);
      }
    </script>
  </body>
</html>
```

### Removing a child element from a parent node

After creating an HTML, we may want to remove element or elements and we can use the _removeChild()_ method.

**Example:**

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>
    <h1>Removing child Node</h1>
    <h2>Asabeneh Yetayeh challenges in 2020</h1>
    <ul>
        <li>30DaysOfPython Challenge Done</li>
        <li>30DaysOfJavaScript Challenge Done</li>
        <li>30DaysOfReact Challenge Coming</li>
        <li>30DaysOfReactNative Challenge Coming</li>
        <li>30DaysOfMachineLearning Challenge Coming</li>
    </ul>

    <script>
        const ul = document.querySelector('ul')
        const lists = document.querySelectorAll('li')
        for (const list of lists) {
            ul.removeChild(list)

        }
    </script>
</body>

</html>
```

As we have see in the previous section there is a better way to eliminate all the inner HTML elements or the children of a parent element using the method _innerHTML_ properties.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>
    <h1>Removing child Node</h1>
    <h2>Asabeneh Yetayeh challenges in 2020</h1>
    <ul>
        <li>30DaysOfPython Challenge Done</li>
        <li>30DaysOfJavaScript Challenge Done</li>
        <li>30DaysOfReact Challenge Coming</li>
    </ul>

    <script>
        const ul = document.querySelector('ul')
        ul.innerHTML = ''
    </script>
</body>

</html>
```

The above snippet of code cleared all the child elements.

---

## Exercises

### Exercises: Level 1

1. Create a div container on HTML document and create 100 to 100 numbers dynamically and append to the container div.

   - Even numbers background is green
   - Odd numbers background is yellow
   - Prime numbers background is red

Project 1

```HTML
 <main>
    <div class="container">
      <h2>background color : <span class="color">#f1f5f8</span></h2>
      <button class="btn btn-hero" id="btn">click me</button>
    </div>
  </main>
```

```CSS
@import url('https://fonts.googleapis.com/css2?family=Ranchers&display=swap');

main {
  min-height: calc(100vh - 3rem);
  display: grid;
  place-items: center;
}
.container {
  text-align: center;
}
.container h2 {
  background: #222;
  color: #fff;
  padding: 1rem;
  border-radius: 0.25rem;
  margin-bottom: 2.5rem;
}
.color {
  color: hsl(205, 78%, 60%);
}

.btn-hero {
  font-family: "Ranchers", sans-serif;
  text-transform: uppercase;
  background: transparent;
  color: #222;
  letter-spacing: 0.1rem;
  display: inline-block;
  font-weight: 700;
  transition: all 0.3s linear;
  border: 2px solid #222;
  cursor: pointer;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
  border-radius: 0.25rem;
  font-size: 1rem;
  padding: 0.75rem 1.25rem;
}
.btn-hero:hover {
  color: #fff;
  background: #222;
}
```

```javascript
const colors = [
  "#000080",
  "#00008B",
  "#0000CD",
  "#0000FF",
  "#006400",
  "#008000",
  "#008080",
  "#008B8B",
  "#00BFFF",
  "#00CED1",
  "#00FA9A",
  "#00FF00",
  "#00FF7F",
  "#00FFFF",
  "#00FFFF",
  "#191970",
  "#1E90FF",
  "#20B2AA",
  "#228B22",
  "#2E8B57",
  "#2F4F4F",
  "#2F4F4F",
  "#32CD32",
  "#3CB371",
  "#40E0D0",
  "#4169E1",
  "#4682B4",
  "#483D8B",
  "#48D1CC",
  "#4B0082",
  "#556B2F",
  "#5F9EA0",
  "#6495ED",
  "#663399",
  "#66CDAA",
  "#696969",
  "#696969",
  "#6A5ACD",
  "#6B8E23",
  "#708090",
  "#708090",
  "#778899",
  "#778899",
  "#7B68EE",
  "#7CFC00",
  "#7FFF00",
  "#7FFFD4",
  "#800000",
  "#800080",
  "#808000",
  "#808080",
  "#808080",
];
const btn = document.getElementById("btn");
const color = document.querySelector(".color");

btn.addEventListener("click", () => {
  const randomNumber = getRandomNumber();
  document.body.style.backgroundColor = colors[randomNumber];
  color.textContent = colors[randomNumber];
});

function getRandomNumber() {
  return Math.floor(Math.random() * colors.length);
}
```

Project 2

```HTML
<div class="main-project-wrapper">
    <div class="project-6-page-wrapper">
        <h2> Counter Project</h2>
        <div class="project-6-wrapper">
            <div class="counter-box-wrapper">
                <div class="counter-number" id="counter-placeholder"> 0 </div>
                <button class="count-btns" id="btn-increment"> Increment </button>
                <button class="count-btns" id="btn-decrement"> Decrement </button>
            </div>
        </div>
    </div>

</div>
```

```CSS
.project-6-page-wrapper{
  background-color: rgb(56, 23, 4);
  display: flex;
  justify-content: center;
  align-content: center;
  flex-direction: column;
  align-items: center;
}

.project-6-page-wrapper >h2{
  padding: 10px 35px;
  margin-bottom: 10px;
  border: 1px solid rgb(233, 201, 174);
  text-align: center;
  color: rgb(192, 231, 243);
  font-family: Arial, Helvetica, sans-serif;
}


.project-6-wrapper{
  width: 100%;
  height: 400px;
  background-color: rgb(202, 114, 73);
}

.counter-box-wrapper{
  width: auto;
  margin: 50px;
  height: 300px;
  background-color: rgb(192, 166, 137);
  box-shadow: 0px 0px 10px 10px rgb(71, 52, 22);
  text-align: center;
}

.counter-number{
  font-size: 150px;
  color: white;
}

.count-btns{
  padding: 10px;
  width: auto;
  background-color: rgb(85, 53, 2);
  font-size: 18px;
  cursor: pointer;
  margin-top: 10px;
  margin-right: 5px;
  font-family: Arial, Helvetica, sans-serif;
  border-radius: 10px;
  border: 2px solid rgb(1, 250, 237);
  color: white;
  outline: none;
}

.count-btns:hover{
  background-color: rgb(133, 70, 42);
}
```

```JAVASCRIPT
// Declaring variables for each IDS
var counterPlaceHolder = document.getElementById("counter-placeholder");
var btnIncrement = document.getElementById("btn-increment");
var btnDecrement = document.getElementById("btn-decrement");

var number = 0;

// Function to change color of the number
// If number is less than 0 color is red, if more than 0 color is green and if 0, color is white.

function changeColor(number){
    var color = "";
    if(number < 0 ){
        color = "red";
    }else if (number > 0 ){
        color = "green";
    }else{
        color="white";
    }
    return color;
}

btnIncrement.addEventListener("click", function(){
    number++;
    counterPlaceHolder.innerHTML = number;
    counterPlaceHolder.style.color = changeColor(number);
});

btnDecrement.addEventListener("click", function(){
    number--;
    counterPlaceHolder.innerHTML = number;
    counterPlaceHolder.style.color = changeColor(number);
});
```

Project 3

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Rock Paper Scissor Game</title>
    <!--Fontawesome-->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.2/css/all.min.css">
    <!--Google Font-->
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="container">
        <div class="scores">
            <p>Computer :
                <span id="computer_score">0</span>
            </p>
            <p>
                You :
                <span id="user_score">0</span>
            </p>
        </div>
        <div class="weapons">
            <button onclick="checker('rock')">
                <i class="far fa-hand-rock"></i>
            </button>
            <button onclick="checker('paper')">
                <i class="far fa-hand-paper"></i>
            </button>
            <button onclick="checker('scissor')">
                <i class="far fa-hand-scissors"></i>
            </button>
        </div>
        <div class="details">
            <p id="user_choice"></p>
            <p id="comp_choice"></p>
            <p id="result"></p>
        </div>
    </div>

<!--linking the javascript file-->
<script src="app.js"></script>
</body>
```

```CSS
*,
*:before,
*:after{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
body{
    height: 100vh;
    background: linear-gradient(
        135deg,
        #ffcf1b,
        #ff8b1b
    );
}
.container{
    width: 45%;
    min-width: 500px;
    background-color: #ffffff;
    padding: 40px 30px;
    position: absolute;
    transform: translate(-50%,-50%);
    top: 50%;
    left: 50%;
    border-radius: 10px;
    box-shadow: 0 15px 25px rgba(0,0,0,0.15);
}
.scores{
    margin-bottom: 50px;
    text-align: right;
}
.weapons{
    width: 90%;
    margin: auto;
    display: flex;
    justify-content: space-around;
}
.weapons button{
    background-color: #ffd51b;
    color: #000000;
    border: none;
    font-size: 50px;
    height: 100px;
    width: 100px;
    border-radius: 50%;
    outline: none;
    cursor: pointer;
}
.details{
    margin-top: 30px;
    text-align: center;
}
.scores,.details{
    font-family: 'Poppins',sans-serif;
    font-weight: 400;
    font-size: 15px;
}
#result{
    width: 180px;
    padding: 10px 0;
    margin: 30px auto;
    font-weight: 600;
    letter-spacing: 0.5px;
}
#user_choice,
#computer_choice{
    font-weight: 400;
    margin-bottom: 10px;
}
span{
    font-weight: 600;
}
```

```Javascript
let [computer_score,user_score]=[0,0];
let result_ref = document.getElementById("result");
let choices_object = {
    'rock' : {
        'rock' : 'draw',
        'scissor' : 'win',
        'paper' : 'lose'
    },
    'scissor' : {
        'rock' : 'lose',
        'scissor' : 'draw',
        'paper' : 'win'
    },
    'paper' : {
        'rock' : 'win',
        'scissor' : 'lose',
        'paper' : 'draw'
    }

}

function checker(input){
    var choices = ["rock", "paper", "scissor"];
    var num = Math.floor(Math.random()*3);

    document.getElementById("comp_choice").innerHTML =
    ` Computer choose <span> ${choices[num].toUpperCase()} </span>`;

    document.getElementById("user_choice").innerHTML =
    ` You choose <span> ${input.toUpperCase()} </span>`;

    let computer_choice = choices[num];

    switch(choices_object[input][computer_choice]){
        case 'win':
            result_ref.style.cssText = "background-color: #cefdce; color: #689f38";
            result_ref.innerHTML = "YOU WIN";
            user_score++;
            break;
        case 'lose':
            result_ref.style.cssText = "background-color: #ffdde0; color: #d32f2f";
            result_ref.innerHTML = "YOU LOSE";
            computer_score++;
            break;
        default:
            result_ref.style.cssText = "background-color: #e5e5e5; color: #808080";
            result_ref.innerHTML = "DRAW";
            break;
    }

    document.getElementById("computer_score").innerHTML = computer_score;
    document.getElementById("user_score").innerHTML = user_score;
}
```
