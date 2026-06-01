# Ex06 BMI Calculator
## Date: 01-06-2026
## Name: RAJASHRI I
## Registration Number: 212224040261

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
App.jsx
```
import { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState("");
  const [status, setStatus] = useState("");

  const calculateBMI = () => {
    if (height === "" || weight === "") {
      alert("Please enter height and weight");
      return;
    }

    const heightInMeter = height / 100;
    const bmiValue = weight / (heightInMeter * heightInMeter);

    setBmi(bmiValue.toFixed(2));

    if (bmiValue < 18.5) {
      setStatus("Underweight");
    } else if (bmiValue >= 18.5 && bmiValue < 25) {
      setStatus("Normal Weight");
    } else if (bmiValue >= 25 && bmiValue < 30) {
      setStatus("Overweight");
    } else {
      setStatus("Obese");
    }
  };

  const clearData = () => {
    setHeight("");
    setWeight("");
    setBmi("");
    setStatus("");
  };

  return (
    <div className="container">
      <div className="card">
        <h1>BMI Calculator</h1>

        <input
          type="number"
          placeholder="Enter height in cm"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />

        <input
          type="number"
          placeholder="Enter weight in kg"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />

        <button onClick={calculateBMI}>Calculate BMI</button>
        <button className="clear" onClick={clearData}>Clear</button>

        {bmi && (
          <div className="result">
            <h2>Your BMI: {bmi}</h2>
            <h3>Status: {status}</h3>
          </div>
        )}
      </div>
    </div>
  );
}

export default App;
```
App.css
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
}

.container {
  height: 100vh;
  background: linear-gradient(135deg, #74ebd5, #9face6);
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  width: 350px;
  background: white;
  padding: 25px;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
}

h1 {
  color: #333;
  margin-bottom: 20px;
}

input {
  width: 90%;
  padding: 12px;
  margin: 10px 0;
  font-size: 16px;
  border: 1px solid #aaa;
  border-radius: 8px;
}

button {
  width: 95%;
  padding: 12px;
  margin-top: 12px;
  border: none;
  border-radius: 8px;
  background: #4b7bec;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background: #3867d6;
}

.clear {
  background: #eb3b5a;
}

.clear:hover {
  background: #c23616;
}

.result {
  margin-top: 20px;
  background: #f1f2f6;
  padding: 15px;
  border-radius: 10px;
}

.result h2 {
  color: #2d3436;
}

.result h3 {
  color: #4b0082;
}
```
## OUTPUT

<img width="1917" height="1027" alt="image" src="https://github.com/user-attachments/assets/be025aeb-0e93-4178-a3c3-e3b029643382" />



## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
