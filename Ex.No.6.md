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
```
import React, { useState } from 'react';
import './BMICalculator.css'; 
const BMICalculator = () => {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState('');
  const [error, setError] = useState('');

  const calculateBMI = (e) => {
    e.preventDefault(); 
    if (!weight || !height) {
      setError('Please enter both weight and height.');
      setBmi(null);
      setMessage('');
      return;
    }

    const weightKg = parseFloat(weight);
    const heightCm = parseFloat(height);

    if (weightKg <= 0 || heightCm <= 0) {
      setError('Weight and height must be positive numbers.');
      setBmi(null);
      setMessage('');
      return;
    }
    
    setError('');

    const heightMeters = heightCm / 100;
    
    const bmiValue = (weightKg / (heightMeters * heightMeters)).toFixed(1);
    setBmi(bmiValue);

    let resultMessage = '';
    if (bmiValue < 18.5) {
      resultMessage = 'Underweight';
    } else if (bmiValue >= 18.5 && bmiValue <= 24.9) {
      resultMessage = 'Normal Weight (Healthy)';
    } else if (bmiValue >= 25 && bmiValue <= 29.9) {
      resultMessage = 'Overweight';
    } else {
      resultMessage = 'Obese';
    }
    setMessage(resultMessage);
  };

  const handleReset = () => {
    setWeight('');
    setHeight('');
    setBmi(null);
    setMessage('');
    setError('');
  };

  return (
    <div className='bmi-container'>
      <div className='container'>
        <h2 className='center'>BMI Calculator</h2>
        
        <form onSubmit={calculateBMI}>
          <div>
            <label>Weight (kg)</label>
            <input 
              type='number' 
              value={weight} 
              onChange={(e) => setWeight(e.target.value)} 
              placeholder='Enter weight in kg'
            />
          </div>
          
          <div>
            <label>Height (cm)</label>
            <input 
              type='number' 
              value={height} 
              onChange={(e) => setHeight(e.target.value)} 
              placeholder='Enter height in cm'
            />
          </div>
          
          <div className='btn-group'>
            <button className='btn' type='submit'>
              Calculate BMI
            </button>
            <button className='btn btn-outline' type='button' onClick={handleReset}>
              Reset
            </button>
          </div>
        </form>

        {error && <p className='error-message'>{error}</p>}

        {bmi && (
          <div className='center-result'>
            <h3>Your BMI is: {bmi}</h3>
            <p className='message'>{message}</p>
            <img 
              src={message === 'Normal Weight (Healthy)' ? 'healthy_icon.png' : 'warning_icon.png'} 
              alt={message} 
              style={{width: '60px', marginTop: '10px'}}
            />
          </div>
        )}
      </div>
    </div>
  );
};

export default BMICalculator;
```
Css file
```
.bmi-container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: #f4f4f9;
    font-family: Arial, sans-serif;
}

.container {
    background-color: #ffffff;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 400px;
    box-sizing: border-box;
}

.center {
    text-align: center;
    color: #333;
    margin-bottom: 25px;
}

form div {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 8px;
    font-weight: bold;
    color: #555;
    font-size: 14px;
}

input[type='number'] {
    width: 100%;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 6px;
    box-sizing: border-box;
    font-size: 16px;
    transition: border-color 0.3s;
}

input[type='number']:focus {
    border-color: #007bff;
    outline: none;
}

.btn-group {
    display: flex;
    justify-content: space-between;
    gap: 10px;
    margin-top: 25px;
}

.btn {
    flex-grow: 1;
    padding: 12px 20px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    transition: background-color 0.3s, transform 0.1s;
}

.btn:not(.btn-outline) {
    background-color: #007bff;
    color: white;
}

.btn:not(.btn-outline):hover {
    background-color: #0056b3;
    transform: translateY(-1px);
}

.btn-outline {
    background-color: transparent;
    color: #007bff;
    border: 2px solid #007bff;
}

.btn-outline:hover {
    background-color: #e6f0ff;
}

.center-result {
    text-align: center;
    margin-top: 30px;
    padding-top: 20px;
    border-top: 1px solid #eee;
}

.center-result h3 {
    color: #28a745;
    font-size: 24px;
    margin-bottom: 5px;
}

.message {
    font-size: 18px;
    font-weight: 600;
    margin-top: 5px;
}

.error-message {
    color: #dc3545;
    text-align: center;
    margin-top: 15px;
    font-weight: bold;
    border: 1px solid #f5c6cb;
    background-color: #f8d7da;
    padding: 10px;
    border-radius: 6px;
}

```
## OUTPUT
<img width="832" height="863" alt="image" src="https://github.com/user-attachments/assets/ef73e2ed-f010-44cd-8b54-533426f58692" />

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
