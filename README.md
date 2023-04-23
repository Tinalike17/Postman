<h2 align="center"> Postman - Homework_1 - створити запити в Postman </h2>

For all methods this fields are the same: Protocol: `http`, IP: `162.55.220.72`, Port: `5005`


| EP_1 |            Response |                           
| --- |                --- |
| 1. Protocol: `http`      |       `[ "Str", "Str" ]` |
| 2. IP: `162.55.220.72` |      |
| 3. Port: `5005` | |
| 5. Method: `GET` | |
| 6. EndPoint: `/get_method` | |
| 7. request url params: | |
| - `name`: str | |
| - `age`: int| |


| EP_2 | Response |
| --- | --- | 
| 1. Method: `POST` | `{ 'age': age, 'salary': salary, 'family': {'children': [['Alex',24], ['Kate',12]], 'u_salary_1_5_year': salary * 4}}` | 
| 2. EndPoint: `/user_info_3` | | 
| 3. request url params: | |
| - `name`: str | | 
| - `age`: int| | | 
| - `salary`: int| | 


| EP_3 | Response |
| --- | --- | 
| 1. Method: `GET` | `{'name': name, 'age': age, 'daily_food': weight * 0.012,'daily_sleep': weight * 2.5}` | 
| 2. EndPoint: `/object_info_1` | | 
| 3. request url params: | |
| - `name`: str | | 
| - `age`: int| | | 
| - `weight`: int| | 


| EP_4 | Method: `GET`  |
| --- | --- | 
| Endpoint          |`/object_info_2`                                              |
| Request URL Params| name: `str`                                                   |
|                   | age: `int`                                                    |
|                   | salary: `int`                                                 |
| Response          | `{`                                                        |
|                   | &nbsp;&nbsp;&nbsp;&nbsp;`'start_qa_salary': salary,`         |
|                   | &nbsp;&nbsp;&nbsp;&nbsp;`'qa_salary_after_6_months': salary * 2,`|
|                   | &nbsp;&nbsp;&nbsp;&nbsp;`'qa_salary_after_12_months': salary * 2.7,`|
|                   | &nbsp;&nbsp;&nbsp;&nbsp;`'qa_salary_after_1.5_year': salary * 3.3,`|
|                   | &nbsp;&nbsp;&nbsp;&nbsp;`'qa_salary_after_3.5_years': salary * 3.8,`|
|                   | &nbsp;&nbsp;&nbsp;&nbsp;`'person': {`                          |
|                   | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`'u_name': [user_name, salary, age],` |
|                   | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`'u_age': age,`|
|                   | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`'u_salary_5_years': salary * 4.2`|
|                   | &nbsp;&nbsp;&nbsp;&nbsp;`}`                                   |
|                   | `}`                                                        |











