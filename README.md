# Ex06 BMI Calculator
## Date: 29.05.

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

APP.JSX
```
import { useState } from "react";
import "./App.css";

function App() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState("");
  const [status, setStatus] = useState("");

  const calculateBMI = () => {
    const h = height / 100;
    const result = (weight / (h * h)).toFixed(2);

    setBmi(result);

    if (result < 18.5) {
      setStatus("Underweight");
    } else if (result >= 18.5 && result < 25) {
      setStatus("Normal Weight");
    } else if (result >= 25 && result < 30) {
      setStatus("Overweight");
    } else {
      setStatus("Obese");
    }
  };

  return (
    <div className="container">
      <div className="box">
        <h1>BMI Calculator</h1>

        <input
          type="number"
          placeholder="Enter Weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />

        <input
          type="number"
          placeholder="Enter Height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />

        <button onClick={calculateBMI}>Calculate</button>

        {bmi && (
          <div className="result">
            <h2>Your BMI: {bmi}</h2>
            <h3>{status}</h3>
          </div>
        )}
      </div>
    </div>
  );
}

export default App;
```

APP.CSS
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f8f4ff;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.box {
  background: #ffffff;
  padding: 35px;
  border-radius: 20px;
  width: 320px;
  text-align: center;
  box-shadow: 0 4px 15px rgba(180, 160, 255, 0.3);
  border: 2px solid #e6dcff;
}

h1 {
  margin-bottom: 20px;
  color: #7b5cff;
}

input {
  width: 90%;
  padding: 12px;
  margin: 10px 0;
  font-size: 16px;
  border-radius: 10px;
  border: 1px solid #d6c7ff;
  outline: none;
  background-color: #faf8ff;
}

input:focus {
  border: 2px solid #a78bfa;
}

button {
  padding: 12px 25px;
  background-color: #a78bfa;
  color: white;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  margin-top: 15px;
  font-size: 16px;
  transition: 0.3s;
}

button:hover {
  background-color: #8b6df5;
}

.result {
  margin-top: 20px;
  background-color: #f3efff;
  padding: 15px;
  border-radius: 12px;
}

.result h2 {
  color: #6d4cff;
}

.result h3 {
  color: #444;
}
```

## OUTPUT

<img width="1292" height="779" alt="Screenshot 2026-05-29 103208" src="https://github.com/user-attachments/assets/43cc204d-2c3b-4630-b2e0-516467df81e6" />


## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
