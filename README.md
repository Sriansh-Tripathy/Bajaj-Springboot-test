# SQL Webhook Solver (Spring Boot)

##  Important Note
I was not able to complete this assignment because my **IntelliJ IDE crashed repeatedly** while I was setting up and coding the project. As a result, I couldn’t build and submit a viable, runnable Spring Boot application in time.  

However, I had a clear plan in mind for how I intended to implement the solution.  
I am documenting those intended steps below, along with the SQL query for my assigned question (**Question 1 — Odd RegNo**).

---

## 🛠 Intended Steps

### Step 1 — App Startup
- Use **Spring Boot** with a `CommandLineRunner` so that the logic executes automatically when the app starts.

### Step 2 — Generate Webhook
- Send a `POST` request to:

- Body:
```json
{
  "name": "John Doe",
  "regNo": "REG12347",
  "email": "john@example.com"
}

SELECT 
    p.AMOUNT AS SALARY,
    CONCAT(e.FIRST_NAME, ' ', e.LAST_NAME) AS NAME,
    TIMESTAMPDIFF(YEAR, e.DOB, CURDATE()) AS AGE,
    d.DEPARTMENT_NAME
FROM PAYMENTS p
JOIN EMPLOYEE e ON p.EMP_ID = e.EMP_ID
JOIN DEPARTMENT d ON e.DEPARTMENT = d.DEPARTMENT_ID
WHERE DAY(p.PAYMENT_TIME) <> 1
ORDER BY p.AMOUNT DESC
LIMIT 1;
Authorization: <accessToken>
Content-Type: application/json
