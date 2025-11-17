# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

### Program:
```sql
CREATE OR REPLACE PROCEDURE find_square(p_number IN NUMBER) IS
    v_square NUMBER;
BEGIN
    v_square := p_number * p_number;
    DBMS_OUTPUT.PUT_LINE('Square of ' || p_number || ' is ' || v_square);
END;
/

SET SERVEROUTPUT ON;

BEGIN
    find_square(6);
END;
/
```

**Expected Output:**  
Square of 6 is 36

### Output:
![image](https://github.com/user-attachments/assets/2649b7d8-e315-44b6-81f2-5741db5d0072)

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

### Program:
```sql
SET SERVEROUTPUT ON;


CREATE OR REPLACE FUNCTION get_factorial(p_number IN NUMBER)
RETURN NUMBER
IS
   v_result NUMBER := 1;
BEGIN
   IF p_number < 0 THEN
      RETURN NULL;  
   END IF;

   FOR i IN 1..p_number LOOP
      v_result := v_result * i;
   END LOOP;

   RETURN v_result;
END;
/

DECLARE
   v_input NUMBER := 5;
   v_output NUMBER;
BEGIN
   v_output := get_factorial(v_input);
   DBMS_OUTPUT.PUT_LINE('Factorial of ' || v_input || ' is ' || v_output);
END;
/
```

**Expected Output:**  
Factorial of 5 is 120

### Output:

![image](https://github.com/user-attachments/assets/6da32c65-95b0-4e9b-95c0-a7aa9b35019f)

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

### Program:
```sql
SET SERVEROUTPUT ON;


CREATE OR REPLACE PROCEDURE check_even_odd(p_number IN NUMBER) IS
BEGIN
  
   IF MOD(p_number, 2) = 0 THEN
      DBMS_OUTPUT.PUT_LINE(p_number || ' is Even');
   ELSE
      DBMS_OUTPUT.PUT_LINE(p_number || ' is Odd');
   END IF;
END;
/

BEGIN
   check_even_odd(12);  
END;
/
```

**Expected Output:**  
12 is Even

### Output:

![image](https://github.com/user-attachments/assets/8d6471fe-5cc5-4250-8ea1-36a56724e3d0)

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

### Program:
```sql
CREATE OR REPLACE FUNCTION reverse_number(p_number IN NUMBER)
RETURN NUMBER IS
    v_number     NUMBER := p_number;
    v_reversed   NUMBER := 0;
    v_digit      NUMBER;
BEGIN
    WHILE v_number > 0 LOOP
        v_digit := MOD(v_number, 10);
        v_reversed := (v_reversed * 10) + v_digit;
        v_number := TRUNC(v_number / 10);
    END LOOP;
    RETURN v_reversed;
END;
/

SET SERVEROUTPUT ON;

DECLARE
    v_input    NUMBER := 1234;
    v_result   NUMBER;
BEGIN
    v_result := reverse_number(v_input);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || v_input || ' is ' || v_result);
END;
/
```

**Expected Output:**  
Reversed number of 1234 is 4321

### Output:

![image](https://github.com/user-attachments/assets/7eaac8fe-d020-48c7-b82c-638a83691b34)

---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

### Program:
```sql
CREATE OR REPLACE PROCEDURE print_table(p_number IN NUMBER) IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || p_number || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(p_number || ' x ' || i || ' = ' || (p_number * i));
    END LOOP;
END;
/

SET SERVEROUTPUT ON;

BEGIN
    print_table(5);
END;
/
```

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

### Output:

![image](https://github.com/user-attachments/assets/7555eb8e-f83e-4d6a-84ab-289f227a6c17)


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
