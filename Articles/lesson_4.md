## Курсор (Cursor)

Cursor это структурная переменная, позволяющая вам обрабатывать данные с несколькими строками. 
Количество строк зависит от команды запроса данных после нее. 
В процессе обработки, вы можете манипулировать с  Cursor через каждую строку данных. 
Эта строка данных определена курсором. Перемещая курсор, вы можете получить все данные текущей строки.

Синтаксис объявления курсора:

```
-- Куросор без параметров
CURSOR <Cursor_Name>
IS
<Select_Statement>
 
-- Курсор с параметрами
CURSOR <Cursor_Name>(<Parameter_List>)
IS
<Select_Statement>
```

Пример:

```
-- Объявляем куросор без параметров
Cursor Emp_Cur Is
 Select Emp.Emp_Id
       ,Emp.First_Name
       ,Emp.Last_Name
 From   Employee Emp;
 
-- Объявляем курсор с параметрами
Cursor Emp_Cur(p_Dept_Id   Number
        ,p_Branch_Id Number)
Is
Select Emp.Emp_Id
   ,Emp.First_Name
   ,Emp.Last_Name
   ,Emp.Assigned_Branch_Id
   ,Emp.Dept_Id
From   Employee Emp
Where  (Emp.Dept_Id = p_Dept_Id Or p_Dept_Id Is Null)
And    (Emp.Assigned_Branch_Id = p_Branch_Id Or p_Branch_Id Is Null);
```
