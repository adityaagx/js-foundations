
Javascript controls logic and behaviour of websites.
Js is a single threaded interpreted dynamic language which runs line by line and moves fast
Variables - containers used to store data values - let, var, const
Let value can be changed, const value remains constant.
Data types - define the nature of data stored. Primitive and non-primtive.
Primitive data types - include String Number Boolean Null Undefined
Non Primitve Complex data types - include Arrays Obljects Functions
Arrays - single variable used to store an ordered collection.
Objects - used to store collections of related data & functionaility/ key-value pair.
Operators - include + - * / %= == === > < >= <= && || !
If/else statemnts - conditional statements which execute if specified condition is true or false.
Loops - structures that repeat a block of code multiple times until a specified condition is met.
Functions - Set of stmts that performs a task or calculates a value.Takes some input and return an output.
Callback function - A function passed as an argument to another function.
Anonymous function - A function that does not have a name associated with it./ Defined inline, used for one-time tasks.
Async function - Multiple things are running parallely at the same time, context switching with each other, runs in parts.
Sync function - Sequential, only one thing is happening at a time.
Javascript can context witch using async functions.
Promise - represents a value that will be available in the future.
Async - makes a function return a Promise
Await - pauses execution until a Promise resolves.
Try/Catch - used for error handling in async await.
DOM - Document Object Model is a tree-like structure created by the browser that represents HTML elements and allows JavaScript
	  to manipulate the webpage dynamically.It lets JavaScript talk to HTML and change the page dynamically.
Events - Events are actions performed by the user or browser that JavaScript can listen to and respond to.

		  
ARRAY METHODS SYNTAX CHEATSHEET
map(), filter(), reduce()

/* ==================================================
MAP()
- Transforms each element
- Returns a NEW array
- Same length as original array
================================================== */

// SHORT VERSION (most common)
const newArray = array.map(element => transformedElement);


// EXAMPLE
{
    const numbers = [1, 2, 3, 4, 5];

    const doubled = numbers.map(num => num * 2);

    console.log(doubled);
    // [2, 4, 6, 8, 10]
}

/* ==================================================
FILTER()
- Selects elements based on condition
- Returns a NEW array
- Length can be smaller
================================================== */

// SHORT VERSION
const filteredArrayShort = array.filter(element => condition);


// EXAMPLE
{
    const numbers = [1, 2, 3, 4, 5];

    const greaterThanThree = numbers.filter(num => num > 3);

    console.log(greaterThanThree);
    // [4, 5]
}

/* ==================================================
REDUCE()
- Combines all values into ONE value
- Can return number, string, object, array
================================================== */

// SYNTAX
const result = array.reduce((acc, item) => acc + item, initialValue);

// EXAMPLE (SUM)
{
    const numbers = [1, 2, 3, 4, 5];

    const sum = numbers.reduce((total, num) => {
        return total + num;
    }, 0);

    console.log(sum);
    // 15
}



/* ==================================================
MAP + FILTER + REDUCE (REAL WORLD FLOW)
================================================== */

{
    const employees = [
        { name: "A", salary: 3000, active: true },
        { name: "B", salary: 2000, active: false },
        { name: "C", salary: 4000, active: true }
    ];

    const totalSalary = employees
        .filter(employee => employee.active)
        .map(employee => employee.salary)
        .reduce((total, salary) => total + salary, 0);

    console.log(totalSalary);
    // 7000
}


/************************************
 JAVASCRIPT BUILT-IN OBJECTS CHEAT SHEET
************************************/

/* ===== DATE OBJECT ===== */
Date();
Date.now(); getFullYear(); getMonth(); getDate(); getDay(); getHours(); getMinutes(); getSeconds(); getMilliseconds();getTime(); setFullYear(); 
setMonth(); setDate(); toDateString(); toTimeString(); toISOString();

/* ===== MATH OBJECT ===== */
Math.PI; Math.E; Math.round(); Math.floor(); Math.ceil(); Math.trunc(); Math.max(); Math.min(); Math.pow(); Math.sqrt(); Math.abs(); Math.random();

/* ===== JSON OBJECT ===== */
JSON.stringify(); JSON.parse();

/* ===== OBJECT OBJECT ===== */
Object.keys();Object.values();Object.entries();Object.assign();Object.freeze();Object.seal();Object.hasOwn();Object.create();

/* ===== ARRAY OBJECT ===== */
length;
push(); pop(); shift(); unshift(); slice(); splice(); concat(); join(); indexOf(); includes(); map(); filter(); reduce(); forEach(); find(); findIndex();
some(); every(); sort(); reverse();

/* ===== STRING OBJECT ===== */
length;
toUpperCase(); toLowerCase(); trim(); trimStart(); trimEnd(); slice(); substring(); replace(); replaceAll(); split();
includes(); startsWith(); endsWith(); indexOf();

/* ===== NUMBER OBJECT ===== */
toFixed(); toString(); Number(); parseInt(); parseFloat(); Number.isInteger(); Number.isNaN(); Number.MAX_VALUE; Number.MIN_VALUE;

/* ===== BOOLEAN OBJECT ===== */
Boolean();

/* ===== FUNCTION OBJECT ===== */
call(); apply(); bind();

/* ===== TIMER / ASYNC ===== */
setTimeout(); clearTimeout(); setInterval(); clearInterval();

/* ===== PROMISE OBJECT ===== */
Promise(); then(); catch(); finally(); Promise.resolve(); Promise.reject(); Promise.all(); Promise.race();

/* ===== DOM / BROWSER ===== */
document.querySelector(); document.querySelectorAll(); document.getElementById(); document.createElement(); appendChild(); remove(); 
classList.add(); classList.remove(); classList.toggle(); addEventListener(); preventDefault();


Examples - 
Variables - 
	let, const,
    let a = 1; console.log(a);
Loops - 
	for(let i=0; i<5; i++){
	console.log(i);
Array - 
	let fruits = [apple, orange, banana]
Objects - 
	Key:Value pair
	let person = { name:aditya, age:21, gender:male }
Function - 
	function calculatesum (a,b) {
     return a + b;
    }
    let a = calculatesum(2,3)
    console.log(a)
Callback Function - 
	function calculate(a, b, callback) {
    let result = a + b;
    callback(result);
    }
    function display(result) {
    console.log("Result is:", result);
    }
    calculate(5, 3, display);
Async + Await -
	async function greet() {
    let message = await Promise.resolve("Hello World");
    console.log(message);
    } 
	greet();
Promise -
	const promise = new Promise((resolve, reject) => {
    resolve("Success!");
    });
    promise.then(result => {
    console.log(result);
    });
Map -
	const numbers = [1, 2, 3, 4, 5];
	const doubled = numbers.map(num => num * 2);
    console.log(doubled);
DOM -
	let body = document.querySelector("body")
    body.innertext = "Hello world"

Event - 
	button.addEventListener("click", sayHello);

Filter -
	const evenNumbers = numbers.filter(num => num % 2 === 0);
    console.log(evenNumbers);
