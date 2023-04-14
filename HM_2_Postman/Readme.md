<h2 align="center"> Postman - Homework_2</h2>

|Task                                                        |                     
| -------------------------------------------------------    | 
| Запит 1: `http://162.55.220.72:5005/first`                 |                                                
|   1. Отправить запрос, cтатус код 200                      | 
|   2. Проверить, что в body приходит правильный string.     |

## Answer

1. 
```pm.test("Status code is 200", function () {
   pm.response.to.have.status(200);
});```

2. 
```pm.test("Body is correct", function () {
   pm.response.to.have.body("This is the first responce from server!ss");
});```
