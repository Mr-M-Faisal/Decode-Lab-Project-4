# Project 4: The Serverless Logic

## Project Overview
This project demonstrates a serverless function built using AWS Lambda and Python. The function accepts two numbers, calculates their sum, and returns the result in JSON format.

## Objectives
- Create an AWS Lambda function.
- Write Python code to process input values.
- Test the function with different numbers.
- Verify successful execution using AWS Lambda test events and execution logs.

## Technologies Used
- **Cloud Platform:** Amazon Web Services (AWS)
- **Service:** AWS Lambda
- **Programming Language:** Python
- **Testing:** AWS Lambda Console

## Function Details
- **Function Name:** `CostCalculatorAPI`
- **Handler:** `lambda_function.lambda_handler`
- **Input Parameters:** `num1`, `num2`
- **Output:** Sum of the two numbers

## Python Code
The Lambda function reads two numbers from the event, adds them, and returns the result.

```python
import json

def lambda_handler(event, context):
    try:
        num1 = int(event["num1"])
        num2 = int(event["num2"])

        total = num1 + num2

        return {
            "statusCode": 200,
            "body": json.dumps({
                "Sum": total
            })
        }

    except (KeyError, TypeError, ValueError):
        return {
            "statusCode": 400,
            "body": json.dumps({
                "error": "Please provide two valid numbers: num1 and num2"
            })
        }
```

## Test Input

```json
{
  "num1": 10,
  "num2": 20
}
```

## Expected Output

```json
{
  "statusCode": 200,
  "body": "{\"Sum\": 30}"
}
```

## Testing and Results
The function was tested using the AWS Lambda Console with a test event named `AdditionTest`.

The initial test completed successfully with status code `200` and returned a sum of `30`.

Additional test cases should be documented after they have been executed successfully.

## Screenshots

### 1. Lambda Function Created
<img width="1914" height="881" alt="image" src="https://github.com/user-attachments/assets/c674c571-a86f-4b0e-9f3a-64b4d84b105a" />


### 2. Python Code
<img width="1845" height="672" alt="image" src="https://github.com/user-attachments/assets/70eb085d-c841-488a-81b2-cea960b9c0e8" />


### 3. Successful Test Execution
<img width="1810" height="588" alt="image" src="https://github.com/user-attachments/assets/9cdfeec2-c0c3-4d38-8e6e-60be7cce990e" />



## Conclusion
This project demonstrates how to create, deploy, and test a serverless Python function using AWS Lambda without managing a server.

The function successfully adds two input numbers and returns the calculated result.
