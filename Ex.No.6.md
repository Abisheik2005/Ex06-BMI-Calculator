# Ex06 BMI Calculator
## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
Home.jsx
```
import React from 'react';

function Home() {
  return (
    <div style={{ textAlign: 'center', marginTop: '2rem' }}>
      <h1>Welcome to the Health App</h1>
      <p>Use the navigation above to calculate your BMI.</p>
    </div>
  );
}

export default Home;


```
BMICalculator.jsx
```
import React, { useState } from 'react';

function BMICalculator() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [status, setStatus] = useState('');

  const calculateBMI = (e) => {
    e.preventDefault();
    if (!weight || !height) return;

    const heightInMeters = height / 100;
    const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);
    setBmi(bmiValue);

    if (bmiValue < 18.5) setStatus('Underweight');
    else if (bmiValue >= 18.5 && bmiValue < 24.9) setStatus('Normal weight');
    else if (bmiValue >= 25 && bmiValue < 29.9) setStatus('Overweight');
    else setStatus('Obese');
  };

  // Status colors
  const statusColors = {
    "Underweight": "#f39c12",
    "Normal weight": "#27ae60",
    "Overweight": "#e67e22",
    "Obese": "#c0392b",
  };

  const containerStyle = {
    display: 'flex',
    justifyContent: 'center',
    alignItems: 'center',
    minHeight: '90vh',
    background: 'linear-gradient(135deg, #6a11cb 0%, #2575fc 100%)',
    fontFamily: 'Segoe UI, Tahoma, Geneva, Verdana, sans-serif',
  };

  const cardStyle = {
    background: 'white',
    padding: '2rem 3rem',
    borderRadius: '15px',
    boxShadow: '0 10px 25px rgba(0,0,0,0.2)',
    textAlign: 'center',
    width: '350px',
    transition: 'transform 0.3s ease',
  };

  const inputStyle = {
    width: '80%',
    padding: '0.7rem',
    margin: '0.5rem 0',
    border: '1px solid #ddd',
    borderRadius: '10px',
    fontSize: '1rem',
    outline: 'none',
  };

  const buttonStyle = {
    background: '#2575fc',
    color: 'white',
    border: 'none',
    padding: '0.8rem 2rem',
    marginTop: '1rem',
    borderRadius: '10px',
    fontSize: '1rem',
    cursor: 'pointer',
  };

  const resultStyle = {
    marginTop: '1.5rem',
    fontSize: '1.1rem',
  };

  const statusStyle = {
    fontWeight: 'bold',
    padding: '0.2rem 0.5rem',
    borderRadius: '5px',
    color: 'white',
    backgroundColor: statusColors[status] || 'grey',
  };

  return (
    <div style={containerStyle}>
      <div
        style={cardStyle}
        onMouseEnter={(e) => e.currentTarget.style.transform = 'translateY(-5px)'}
        onMouseLeave={(e) => e.currentTarget.style.transform = 'translateY(0)'}
      >
        <h2>BMI Calculator</h2>
        <form onSubmit={calculateBMI}>
          <input
            type="number"
            placeholder="Weight (kg)"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
            style={inputStyle}
          />
          <input
            type="number"
            placeholder="Height (cm)"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
            style={inputStyle}
          />
          <br />
          <button type="submit" style={buttonStyle}
            onMouseEnter={(e) => e.currentTarget.style.backgroundColor = '#6a11cb'}
            onMouseLeave={(e) => e.currentTarget.style.backgroundColor = '#2575fc'}
          >
            Calculate
          </button>
        </form>

        {bmi && (
          <div style={resultStyle}>
            <h3>Your BMI: {bmi}</h3>
            <p>Status: <span style={statusStyle}>{status}</span></p>
          </div>
        )}
      </div>
    </div>
  );
}

export default BMICalculator;
```
App.jsx
```
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './Home';
import BMICalculator from './BMICalculator';

function App() {
  return (
    <Router>
      <nav style={{ padding: '1rem', background: '#f0f0f0' }}>
        <Link to="/" style={{ marginRight: '1rem' }}>Home</Link>
        <Link to="/bmi">BMI Calculator</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/bmi" element={<BMICalculator />} />
      </Routes>
    </Router>
  );
}

export default App;
```

## OUTPUT
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/3bed9b8a-5ede-4de4-a115-5986c6180009" />
<img width="1916" height="1079" alt="image" src="https://github.com/user-attachments/assets/571c9682-e489-4750-bbfa-d1bff130ef26" />


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
