+++
date = '2020-09-03T14:24:19+02:00'
draft = false
title = 'Building a Loan Calculator using React Hooks'
tags = ['react', 'programming']
+++

# Building a Loan Calculator using React Hooks

![React Hooks ](/img/ReactHooks.png)

Are you just starting with React? Are you wondering what you can build that’s simple and achievable? Well, so was I, and so I wrote this article to share my experience and learning with you.

### What are we building? 💻

Like I promised, we're going to keep it simple and build a basic loan calculator that will take user input for the loan amount, interest rate and loan term, and display a monthly payment, and totals for the repayment amount and interest.

We're going to build a form to receive the input values and display the results. Along the way, we’ll manage form state, handle validation, and define event handlers to tie everything together.

To follow along you’ll need basic understanding of JavaScript, particularly ES6 features such as [destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment), the [spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) and [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions). You also need to have Node.js installed, and a text editor of your choice. I personally use Visual Studio Code.

### Why? 🤔

I did this project in vanilla JavaScript while doing a course from [Brad Traversy](https://www.traversymedia.com/) on [Udemy](https://www.udemy.com/course/modern-javascript-from-the-beginning/) and I loved the experience of building the whole application from scratch. I decided to rebuild this project using React Hooks to see the benefits React brings when you need to manage and manipulate the UI such as grabbing inputs from the UI and also creating new elements to display the results to the user.

I also wanted to demonstrate the React hooks API, which allows function components to have state and utilise lifecycle methods under the hood. In past versions of React, class components were the only way to manage state. This makes for a much better development experience 🤩.

You can also find the code for this project here:
<https://github.com/suzanamelomoraes/loan-calculator-react-hooks>

### Shall we start? 👍

Section 1 - [Create-React-App](#section1)

Section 2 - [Add some CSS](#section2)

Section 3 - [Create the component](#section3)

Section 4 - [Add state](#section4)

Section 5 - [Create a form / controlled component](#section5)

Section 6 - [Form Submission](#section6)

Section 7 - [Calculate the results](#section7)

Section 8 - [Display the results](#section8)

Section 9 - [Validate the results / Manage errors](#section9)

Section 10 - [Recalculate](#section10)

## Section 1 {#section1}

**Create-React-app**

We don't need anything complicated to make this project so we'll use the boilerplate [Create-React-App](https://reactjs.org/docs/create-a-new-react-app.html) gives us. To create the project, navigate to a directory of your choice and type:

```node
npm i -g create-react-app
create-react-app loan-calculator
```

Or optionally:

```node
npx create-react-app loan-calculator
```

Once the create-react-app finishes running, you can navigate into the project:

```node
cd loan-calculator
```

To open the project in Visual Code (or your preferred editor):

```node
code .
```

Finally, to run the project:

```node
npm start
```

You can clear up your boilerplate as you wish. I usually delete the icons and related stuff, but it’s totally up to you. If you accidentally delete some essential file, just repeat the steps and create a new boilerplate.

## Section 2 {#section2}

**CSS**

Styling won't be the focus of this tutorial, so feel free to copy this CSS into your _App.css_ if you want — or add any styling you prefer. You can also find how I applied my classes in my repository on GitHub.

_src/App.css_

```css
body {
  background-color: black;
}

input {
  display: block;
  width: 95%;
  margin: 3px 0;
  border-radius: 4px;
  border-color: lightgray;
}

p {
  color: red;
  font-size: 10px;
  text-align: left;
}

h4 {
  color: #555;
}

.calculator {
  display: flex;
  justify-content: center;
}

.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: white;
  width: 50%;
  border-radius: 4px;
  margin-top: 30px;
}

.form-items {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 3px;
}

.button {
  background-color: black;
  color: white;
  border: none;
  margin: 10px 0;
  padding: 5px 10px;
  cursor: pointer;
}

.button:hover {
  opacity: 0.8;
}

#label {
  font-size: 12px;
  text-align: left;
}
```

## Section 3 {#section3}

**Create the component**

Inside the _src_ folder, we will create another folder called _components_ and then, inside it, create a file called _Calculator.jsx_.

_Calculator.jsx_ is a functional component which sets a header and imports React. Your initial Calculator component will look like this:

_src/components/Calculator.jsx_

```react
import React from 'react'

const Calculator = () => {
   return (
       <div>
          <h1>Loan Calculator</h1>
       </div>
   )
}

export default Calculator;
```

Now you can include your _Calculator.jsx_ in _App.js_ like this:

```react
import React from 'react';
import Calculator from './components/Calculator';
import './App.css';

function App() {
 return (
   <div>
       <Calculator />
   </div>
 );
}

export default App;
```

## Section 4 {#section4}

**Adding state**

Remember from earlier that we need three pieces of information from the user to perform the loan calculation: the loan amount, interest rate, and the loan term. We’ll use state to hold these values for us.

Ready to make our component stateful? First up, we’re going to add the _useState_ hook, which allows React to manage your components’ state. Back in your _Calculator.jsx_, amend the first line to include React’s state handler, _useState_.

_src/components/Calculator.jsx_

```react
import React, {useState} from 'react';
```

Then we need to “use” the hook. The React documentation gives us this pattern:

```react
const [state, setState] = useState()
```

And we’ll implement it, above our _return_, like this:

```react
 const [userValues, setUserValues] = useState({
   amount: '',
   interest: '',
   years: '',
 });
```

The first item we’re destructuring, _userValues_ is the name of our state and where we will store the input values given by the user. You can give it any name you want, however, it is good practice to choose meaningful names related to your application.

The second item, _setUserValues_ is a method returned by the _useState_ hook, that allows us to set the state.

Finally, the argument we provide to _useState_ is the value we want to be the default value of the state. In this case, we have an object with these three properties, each assigned an empty string.

## Section 5 {#section5}

**Create a form / controlled component**

To perform our calculation we need to collect information from the user, so let’s include the form with the inputs we need to receive this data. Initially, our form will look like this:

```react
<form>
  <div>
    <div>
      <label>Amount:</label>
      <input
        type='text'
        name='amount'
        placeholder='Loan amount'
      />
    </div>
    <div>
      <label>Interest:</label>
      <input
        type='text'
        name='interest'
        placeholder='Interest'
      />
    </div>
More code...
```

**Controlled components**

Usually, React forms are implemented using [controlled components](https://reactjs.org/docs/forms.html) - where the data is handled by a React component.

Let's go ahead and implement our components as controlled components:

Assign the value of the input from the state like this:

```react
<input
  type='text'
  name='amount'
  placeholder='Loan amount'
  value={userValues.amount}
/>
```

Then, write an event handler on the _onChange_ prop to update the state when the user enters a loan amount.

Include an _onChange_ prop to each input and set it to a function to handle the change:

```react
<input
  type='text'
  name='amount'
  placeholder='Loan amount'
  value={userValues.amount}
  onChange={handleInputChange}
/>
```

Next, add a function to handle the state change. You can use the spread operator inside the new function to update the _userValues_ state:

```react
const handleInputChange = (event) =>
   setUserValues({ ...userValues, [event.target.name]: event.target.value });
```

We need to do the same with all three inputs we want in our application (amount, interest and years) to make sure we are adding the right values given by the user to our _userValues_ state.

As you can notice, we are using bracket notation here instead of writing a function to address each input. You can read more about it [here](https://github.com/nodesecurity/eslint-plugin-security/blob/master/docs/the-dangers-of-square-bracket-notation.md) and [here](https://stackoverflow.com/questions/57960770/securely-set-unknown-property-mitigate-square-bracket-object-injection-attacks/58179430#58179430).

## Section 6 {#section6}

**Form Submission**

At this point, we have captured the values and stored them in state. Now it is time to do something with the given data on submission.

Let’s include a submit button in our form.

```react
<input type='submit'/>
```

We also need to handle the values given by the user once they submit the form. To do this, we need to call the _onSubmit_ method and pass our function that handles this submission as an argument like this:

```react
<form onSubmit={handleSubmitValues}>
```

Now, after the _handleInputChange_ handler, we can write our _handleSubmitValues_ function that will receive the event as an argument.

There's one thing we need to do first though. On form submission, the default behaviour is to reload/redirect the page. To avoid this, we need to call the _[preventDefault()](https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault)_ method on the event.

At this point, we can log the input values in the console, and our function will look like this:

```react
 const handleSubmitValues = (e) => {
   e.preventDefault();
   console.log(userValues);
 };
```

## Section 7 {#section7}

**Calculate the results**

At this point, you should be able to receive the data from the user and see it in your console, If it’s not happening, don’t panic. Welcome to the world of software development!
Breathe, review the steps and check my repository on [GitHub](https://github.com/suzanamelomoraes/loan-calculator-react-hooks) if you wish.

Once we have the data, it’s time to calculate! But first, the calculation will generate new values, and we need to store them somewhere. So, to make the code more readable and easy to maintain let’s create another state to store these results, so they can be displayed in the UI.

```react
 const [results, setResults] = useState({
   monthlyPayment: '',
   totalPayment: '',
   totalInterest: '',
   isResult: false,
 });
```

Note I also included a fourth variable _isResult_ that will help the component know whether it needs to display the results to the user. Don't worry about it now; it will make more sense soon.

You can now delete the _console.log_ and call the _calculateResults_ function when handling the values submitted and send the data into it as an argument like this:

```react
 const handleSubmitValues = (e) => {
   e.preventDefault();
   calculateResults(userValues);
 };
```

Once we have a place where we can store the values given by the user and another one to store the results, we can perform the calculation itself.

I’m not gonna go in details of how this calculation works, as this is a method you can find easily on the internet, and it is not the focus of this article, but some points of this function are important to highlight.

- By default, inputs capture user input as strings, not numbers (to avoid this, we could use [number inputs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number), but browsers render these inputs with stepper arrows, which I wanted to avoid here). To turn our strings into numbers, we need to wrap our values inside _Number()_.
- You can call your variables whatever you wish, but keep in mind the names must make sense to whoever looks at code again in the future.

Here is our function:

```react
 const calculateResults = ({ amount, interest, years }) => {
   const userAmount = Number(amount);
   const calculatedInterest = Number(interest) / 100 / 12;
   const calculatedPayments = Number(years) * 12;
   const x = Math.pow(1 + calculatedInterest, calculatedPayments);
   const monthly = (userAmount * x * calculatedInterest) / (x - 1);

   if (isFinite(monthly)) {
     const monthlyPaymentCalculated = monthly.toFixed(2);
     const totalPaymentCalculated = (monthly * calculatedPayments).toFixed(2);
     const totalInterestCalculated = (monthly * calculatedPayments - userAmount).toFixed(2);

     // Set up results to the state to be displayed to the user
     setResults({
       monthlyPayment: monthlyPaymentCalculated,
       totalPayment: totalPaymentCalculated,
       totalInterest: totalInterestCalculated,
       isResult: true,
     });
   }
   return;
 };
```

We are destructuring _userValues_ data to perform the calculation and putting the results into the _results_ state.

Note that, to do this, we are setting all the values at the same time and replacing the whole object at once.

## Section 8 {#section8}

**Display the results**

Yeah! We have results! If you _console.log(newResults)_ you will now see the results you are getting from your calculation. Now let’s show these values to the user. After all, they are waiting for it!

Let’s create a form to display the results. I wanted to keep the same layout and style of the first form. The difference now is, as you are creating a form only to display data, don’t forget to disable the inputs.

We want a field with a corresponding label for each result. Also, it is good to remind the user of the values they gave to us, so let’s include this information again to make sure our user has all the information they need.

Our form will look like this:

```react
<div>
  <h4>
    Loan amount: ${userValues.amount} <br />
    Interest:{userValues.interest}% <br />
    Years to repay: {userValues.years}
  </h4>
  <div>
    <label>Monthly Payment:</label>
    <input type='text' value={results.monthlyPayment} disabled />
  </div>
  <div>
    <label>Total Payment: </label>
    <input type='text' value={results.totalPayment} disabled
    />
  </div>
  <div>
    <label>Total Interest:</label>
    <input type='text' value={results.totalInterest} disabled
    />
  </div>
</div>
```

Finally, we can include a [ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) to render the form differently, depending on whether we have results to display. Do you remember the _isResult_ variable from earlier? I told you it will help us to display the results later!

The default value of _isResult_ is false, but when the calculation is done and we add the results to the state, we also set this condition to true.

What does it mean? We can apply it to define what we are going to display. When _isResult_ is false we show the part of the form that collects the data from the user; then once we calculate the loan, we also change _isResult_ to true, and this way we display only the part with the results.

```react
<form onSubmit={handleSubmitValues}>
  {!results.isResult ? (
    //   Form to collect data from the user
  ) : (
    //   Form to display the results to the user
  )}
</form>
```

## Section 9 {#section9}

**Validate the results / Manage errors**

We are almost done, and everything is working. Beautiful! 😍

But hold on; we cannot forget an important step: we need to validate the values given to us to avoid issues with our calculation. Also, we need to tell the user if something goes wrong.

First, let’s create another state to help us to manage the error:

```react
const [error, setError] = useState('');
```

Now, we can write a function whose only goal in life is to check for input errors and set the message related to this error. This function should return true if all of the inputs were valid, or false if there were any problems with the input.

We will check if the user forgot to provide any values, also if the values are all numbers, and finally if the numbers are positive. For purposes of this application, we consider 0 not to be a positive number.

Our function will look like this:

```react
 const isValid = () => {
   const { amount, interest, years } = userValues;
   let actualError = '';
   // Validate if there are values
   if (!amount || !interest || !years) {
     actualError = 'All the values are required';
   }
   // Validade if the values are numbers
   if (isNaN(amount) || isNaN(interest) || isNaN(years)) {
     actualError = 'All the values must be a valid number';
   }
   // Validade if the values are positive numbers
   if (
     Number(amount) <= 0 ||
     Number(interest) <= 0 ||
     Number(years) <= 0
   ) {
     actualError = 'All the values must be a positive number';
   }
   if (actualError) {
     setError(actualError);
     return false;
   }
   return true;
 };
```

Now we also can update our function that handles the submit:

```react
 const handleSubmitValues = (e) => {
   e.preventDefault();
       if (isValid()) {
     setError('');
     calculateResults(userValues);
   }
 };
```

Now the data is validated on submit, valid data will reset the error message to null, and then we calculate and display the results to the user. To display the error message, you can include it from your state just above your form.
Don’t worry, it will be displayed only when _error_ has a non-empty value.

```react
<h1>Loan Calculator</h1>
<p>{error}</p>
<form onSubmit={handleSubmitValues}>
```

## Section 10 {#section10}

**Recalculate**

Great job! You finished your loan calculator! 🤝

Now it’s time to get the application ready to be used again.

We need to include a button in the form that displays the results and call a function to clear the fields like this:

```react
<input
  value='Calculate again'
  type='button'
  onClick={clearFields}
/>
```

Clearing the fields is really simple. We just need to set all the user-provided values in state to empty strings again and change _isResult_ to false like this:

```react
 const clearFields = () => {
   setUserValues({
     amount: '',
     interest: '',
     years: '',
   });

   setResults({
     monthlyPayment: '',
     totalPayment: '',
     totalInterest: '',
     isResult: false,
   });
 };
```

Congratulations! Very well done! 👏

Now you know a little more how to create forms, handle validation, manipulate data, and work with event handlers.

There are lots to do from here. You can play around with more kinds of calculations and validations, or maybe you want to include a UI library. There is much more to discover...

Believe me, this is just the beginning and this is the way!

Happy coding! 🖖
