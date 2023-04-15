<h2 align="center"> Postman - Homework_2</h2>

|                        Task                                |                     
| -------------------------------------------------------    | 
| Запит 1: `http://162.55.220.72:5005/first`                 |                                                
|   1. Отправить запрос, cтатус код 200                      | 
|   2. Проверить, что в body приходит правильный string.     |

<h3 align="center"> Answer </h3> 

1.  `cтатус код 200` \
   pm.test("Status code is 200", function () { \
   pm.response.to.have.status(200);\
});
`

2. `Проверить, что в body приходит правильный string.`\
   pm.test("Body is correct", function () { \
   pm.response.to.have.body("This is the first responce from server!ss"); \
});




|                        Task                                |                     
| -------------------------------------------------------    | 
| Запит 2: `http://162.55.220.72:5005/user_info_3`           |                                                
|   1. Отправить запрос, cтатус код 200                      | 
|   2. Спарсить response body в json. |
|   3. Проверить, что name в ответе равно name s request (name вбить руками.)|
|   4. Проверить, что age в ответе равно age s request (age вбить руками.)|
|   5. Проверить, что salary в ответе равно salary s request (salary вбить руками.) |
|   6. Спарсить request.|
|   7. Проверить, что name в ответе равно name s request (name забрать из request.)|
|   8. Проверить, что age в ответе равно age s request (age забрать из request.)|
|   9. Проверить, что salary в ответе равно salary s request (salary забрать из request.)|
|  10. Вывести в консоль параметр family из response.|
|  11. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request) |



<h3 align="center"> Answer </h3> 

1.  `cтатус код 200` \
   pm.test("Status code is 200", function () { \
   pm.response.to.have.status(200);\
});

2. `Спарсить response body в json`\
   var jsonData = pm.response.json();\
3. `Проверить, что name в ответе равно name s request`\ 
  var resp_name = jsonData.name; \
console.log("Response name: " + resp_name); \
pm.test("Request response NAME check",\
function() {\
    pm.expect(resp_name).to.equal("Igor");\
});
4. `Проверить, что age в ответе равно age s request`\
  var resp_age = +jsonData.age;\
console.log("Response age: " + resp_age);\
pm.test("Request response AGE check",\
function() {\
    pm.expect(resp_age).to.equal(24)\
});
5. `//Check that response salary is the same value as salary in the request (salary type manually)` \
var resp_salary = jsonData.salary;\
console.log("Response age: " + resp_salary);\
 pm.test("Request response SALARY check",\
 function() {\
     pm.expect(resp_salary).to.equal(3300)\
 });
 6. `//Спарсити request`\
var req = request.data;
7. `//Check that name from response is equal to name from request(name pull out from request)` \
console.log("Request data: ",req); \
var req_name = req.name; \
console.log("Request name: ",req_name);\
pm.test ("Request response NAME check", \
function() { \
pm.expect(resp_name).to.equal(req_name) \
});
8. `//Check that age from response is equal to age from request(age pull out from request)` \
var req_age = +req.age;\
console.log("Request age: ", req_age);\
pm.test ("Request response AGE check",\
function() {\
pm.expect(resp_age).to.equal(req_age)\
});
9. `//Check that salary from response is equal to salary from request(salary pull out from request)` \
var req_salary = +req.salary; \
console.log("Request salary: ", req_salary); \
pm.test ("Request response SALARY check", \
function() { \
pm.expect(resp_salary).to.equal(req_salary) \
});
10. `// Вивести в консоль параметр family from response`\
var resp_family = jsonData.family; \
console.log("Response family: " + resp_family); \
for (var key in resp_family){ \
    console.log(key + " : " + resp_family[key]); \
}
11. `//Check that u_salary_1_5_year in response equals to salary*4(salary take from request)` \
var req_u_salary_1_5_year = req.salary*4; \
console.log("Request u_salary_1_5_year: ", req_u_salary_1_5_year); \
var resp_u_salary_1_5_year = jsonData.family.u_salary_1_5_year; \
console.log("Response u_salary_1_5_year: ", resp_u_salary_1_5_year); \
pm.test("Request response U_SALARY_1_5_YEAR check: ", \
function(){ \
    pm.expect(resp_u_salary_1_5_year).to.equal(req_u_salary_1_5_year) \
});

|                        Task                                |                     
| -------------------------------------------------------    | 
| Запит 3: `http://162.55.220.72:5005/object_info_3`         |                                                
|   1. Отправить запрос, cтатус код 200                      |
|   2. Спарсить response body в json.|
|   3. Спарсить request.|
|   4. Проверить, что name в ответе равно name s request (name забрать из request.)|
|   5. Проверить, что age в ответе равно age s request (age забрать из request.)|
|   6. Проверить, что salary в ответе равно salary s request (salary забрать из request.)|
|   7. Вывести в консоль параметр family из response.|
|   8. Проверить, что у параметра dog есть параметры name.|
|   9. Проверить, что у параметра dog есть параметры age.|
|  10. Проверить, что параметр name имеет значение Luky. |
|  11. Проверить, что параметр age имеет значение 4.     |

<h3 align="center"> Answer </h3> 

1. `Send a request`\
    pm.sendRequest("http://162.55.220.72:5005/object_info_3?name=Alyona&age=20&salary=300", function (err, response) {\
    console.log(response.json());
});  
   `Status code is 200` \
   pm.test("Status code is 200", function () { \
   pm.response.to.have.status(200);\
});

2. `Parse response body into json`\
   var jsonData = pm.response.json();
   
3. `Parse request`\
   var req = pm.request.url.query.toObject();
   
4. `Check that name in response equals to name in request (name take from request)`\
   pm.test("Response request NAME check",\
   function(){\
    pm.expect(req.name).to.equal(jsonData_resp.name)\
   });
5. `Check that age in response equals to age in request (age take from request)`\
   pm.test("Response request AGE check", \
   function(){ \
   pm.expect(req.age).to.equal(jsonData_resp.age)\
   });  
6. `Check that salary in response equals to salary in request (salary take from request)`\
    var req_salary = +req.salary;\
    pm.test("Response request SALARY check",\
    function(){\
    pm.expect(req_salary).to.equal(jsonData_resp.salary)\
    });
7. `Вивести в консоль параметр family from response`\
    var resp_family =  JSON.stringify(jsonData_resp.family);\
    console.log("Response family: " + resp_family);
8.  `Перевірити що параметр dog має name`\
     var dog = jsonData_resp.family.pets.dog;\
     console.log("Dog", dog);\
     pm.test("Check that dog HAS NAME",\
     function () {\
     pm.expect(dog).to.have.property('name');\
     });
9.  `Перевірити що параметр dog має age`\
     var dog = jsonData_resp.family.pets.dog;\
     pm.test("Check that dog HAS AGE",\
     function () {\
     pm.expect(dog).to.have.property('age');\
     });
10. `Check that parameter name has value "Luky" `\
     var dog_name = jsonData_resp.family.pets.dog\["name"\];
     pm.test("Check that dog HAS value Luky"\,
     function () {\
     pm.expect(dog_name).to.equal('Luky');\
     });
11. `Check that parameter age has value "4"`\
     var dog_age = jsonData_resp.family.pets.dog\["age"\];\
     pm.test("Check that dog HAS value 4"\, \
     function () {\
     pm.expect(dog_age).to.equal(4);\
     });
     
|                        Task                                |                     
| -------------------------------------------------------    | 
| Запит 4: `http://162.55.220.72:5005/object_info_4`         |                                                
|   1. Отправить запрос, cтатус код 200                      |
|   2. Спарсить response body в json.|
|   3. Спарсить request.|
|   4. Проверить, что name в ответе равно name s request (name забрать из request.)|
|   5. Проверить, что age в ответе равно age s request (age забрать из request.)|
|   6. Вывести в консоль параметр salary из request.|
|   7. Вывести в консоль параметр salary из response.|
|   8. Вывести в консоль 0-й элемент параметра salary из response.|
|   9. Вывести в консоль 1-й элемент параметра salary параметр salary из response. |
|  10. Вывести в консоль 2-й элемент параметра salary параметр salary из response.    |
|  11. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)| 
|  12. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)| 
|  13. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)| 
|  14. Создать в окружении переменную name| 
|  15. Создать в окружении переменную age| 
|  16. Создать в окружении переменную salary| 
|  17. Передать в окружение переменную name| 
|  18. Передать в окружение переменную age| 
|  19. Передать в окружение переменную salary| 
|  20. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.| 

<h3 align="center"> Answer </h3> 

1. `Status code is 200` \
   pm.test("Status code is 200", function () { \
   pm.response.to.have.status(200);\
});

2. `Parse response body into json`\
    var resp_jsonData = pm.response.json();
   
3. `Parse request`\
    var req_url = pm.request.url.query.toObject();
    
4. `Проверить, что name в ответе равно name s request (name забрать из request.)`\
   var resp_name = resp_jsonData.name;\
   pm.test("Response request NAME check"\,\
   function(){\
   pm.expect(req_url.name).to.equal(resp_name)\
   });\

5. `Проверить, что age в ответе равно age из request (age забрать из request.)`\
`   pm.test("Request response AGE check", \
    function(){\
    pm.expect(+req_url.age).to.equal(resp_jsonData.age);\
    });
6. `Вывести в консоль параметр salary из request.`\
    console.log(req_url.salary);

7. `Вывести в консоль параметр salary из response.`\
    console.log(resp_jsonData.salary);
8. `Вывести в консоль 0-й элемент параметра salary из response.`\
    console.log(resp_jsonData.salary[0]);
9. `Вывести в консоль 1-й элемент параметра salary параметр salary из response.`\
    console.log(resp_jsonData.salary[1]);
10. `Вывести в консоль 2-й элемент параметра salary параметр salary из response.`\
     console.log(resp_jsonData.salary[2]);
11. `Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)`\
    pm.test("Request response SALARY check", \
    function(){\
    pm.expect(+req_url.salary).to.equal(resp_jsonData.salary[0]);\
    });
12. `Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)`\
     pm.test("Request response SALARY*2 to equal the first element of response salary array check", \
     function(){ \
     pm.expect(req_url.salary*2).to.equal(+resp_jsonData.salary[1]);\
     });
13. `Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)`\
    pm.test("Request response SALARY*3 to equal the first element of response salary array check", \
    function(){\
    pm.expect(req_url.salary*3).to.equal(+resp_jsonData.salary[2]);\
    });
14.  `Создать в окружении переменную name`
15.  `Создать в окружении переменную age`
16.  `Создать в окружении переменную salary`

| Variable         |          Current value |
| :---:              |                    :---: |
|   age               |                19   |
|   name              |               Emma  |
|  salary            |                200   |

17.  `Передать в окружение переменную name`\
      console.log(req_url.name);\
      pm.environment.set("name", req_url.name);
18   `Передать в окружение переменную age`\
      console.log(req_url.age);\
      pm.environment.set("age", req_url.age);
19.  `Передать в окружение переменную salary`\
      console.log(req_url.salary);\
      pm.environment.set("salary",req_url.salary);
20.  `Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.`\
      var resp_salary = resp_jsonData.salary;\
      let count_el = "";\
      for (let x in resp_salary) { \
      count_el += resp_salary[x] + ' ';\
      }\
      console.log('Salary elements : ', count_el);
