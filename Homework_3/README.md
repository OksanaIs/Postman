### HW Task_3 Postman

#### 1. Login required
POST
http://162.55.220.72:5005/login
```
login : str (кроме /)
password : str
```
The incoming token must be passed to all other requests
Further all requests require a token

#### 2. http://162.55.220.72:5005/user_info
```
Req. (RAW JSON)
POST
age: int
salary: int
name: str
auth_token
```
```
Resp.
{'start_qa_salary':salary,
 'qa_salary_after_6_months': salary * 2,
 'qa_salary_after_12_months': salary * 2.9,
 'person': {'u_name': [user_name, salary, age],
                                'u_age': age,
                                'u_salary_1.5_year': salary * 4}
}
```
Tests:
1) Status code 200
2) Checking the JSON structure in the response
3) In the answer, indicate the coefficients for multiplying wages, write tests to verify the correctness of the result of multiplying by the coefficient
4) Get the value from the "u_salary_1.5_year" field and send the request to the salary field http://162.55.220.72:5005/get_test_user

#### 3. http://162.55.220.72:5005/new_data
```
Req.
POST
age: int
salary: int
name: str
auth_token
```
```
Resp.
{'name':name,
  'age': int(age),
  'salary': [salary, str(salary*2), str(salary*3)]
}
```
Tests:
1) Status code 200
2) Checking JSON structure in response
3) In the answer, indicate the coefficients for multiplying wages, write tests to verify the correctness of the result of multiplying by the coefficient.
4) Check that the 2nd element of the salary array is greater than the 1st and 0th

#### 4. http://162.55.220.72:5005/test_pet_info
```
Req.
POST
age: int
weight: int
name: str
auth_token
```
```
Resp.
{'name': name,
 'age': age,
 'daily_food':weight * 0.012,
 'daily_sleep': weight * 2.5
}
```
Tests:
1) Status code 200
2) Checking the JSON structure in the response
3) The answer indicates the multiplication coefficients weight, write tests to check the correctness of the result of multiplication by the coefficient

#### 5. http://162.55.220.72:5005/get_test_user
```
req.
POST
age: int
salary: int
name: str
auth_token
```
```
Resp.
{'name': name,
 'age':age,
 'salary': salary,
 'family': {
 'children':[['Alex', 24],['Kate', 12]],
 'u_salary_1.5_year': salary * 4}
}
```
Tests:
1) Status code 200
2) Checking the JSON structure in the response
3) Check that the value of the name field = the value of the name variable from the environment
4) Check that the value of the age field in the response matches the value of the age field sent in the request

#### 6. http://162.55.220.72:5005/currency
```
Req.
POST
auth_token
```
```
Resp.
[
{"Cur_Abbreviation": str,
 "Cur_ID": int,
 "Cur_Name": str
}
…
{"Cur_Abbreviation": str,
 "Cur_ID": int,
 "Cur_Name": str
}
]
```
Tests:
1) You can take any object from the sent list, use JS random
2) In the object, take Cur_ID and pass it through the environment to the next request

#### 7. http://162.55.220.72:5005/curr_byn
```
Req.
POST
auth_token
curr_code: int
```
```
Resp.
{
    "Cur_Abbreviation": str
    "Cur_ID": int,
    "Cur_Name": str,
    "Cur_OfficialRate": float,
    "Cur_Scale": int,
    "Date": str
}
```
Tests:
1) Status code is 200
2) Checking the JSON structure in the response
