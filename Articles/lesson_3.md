## Базовые команды PL/SQL

В данном уроке приведен обзор команд PL/SQL. Вы поймете больше через примеры в следующих частях.

### CREATE TABLE

Оператор Oracle/PLSQL CREATE TABLE позволяет создавать и определять таблицу.

Синтаксис:
```
CREATE TABLE table_name
(column1 datatype [ NULL | NOT NULL ],
 column2 datatype [ NULL | NOT NULL ],
  …
 column_n datatype [ NULL | NOT NULL ]);
```
Параметры или аргументы:
```
table_name - имя таблицы, которую вы хотите создать.
column1, column2, … column_n - столбцы, которые вы создаете в таблице. 
Каждый столбец должен иметь тип данных. Столбец должен быть определен либо как «NULL» либо «NOT NULL», 
если это значение не указывается, то по умолчанию устанавливается «NULL».
```
Пример:
```
Рассмотрим на примере как использовать в Oracle/PLSQL CREATE TABLE.

Oracle PL/SQL
CREATE TABLE customers
( customer_id number(10) NOT NULL,
  customer_name varchar2(50) NOT NULL,
  city varchar2(50));
```
В этом примере CREATE TABLE создает таблицу customers, которая имеет 3 столбца.

- Первый столбец _customer_id_, который создается с числовым типом данных (максимум 10 цифр в длину) 
и не может принимать значение NULL.
- Второй столбец _customer_name_ с типом данных varchar2 (максимум 50 символов), также не может принимать значение NULL.
- Третий столбец _city_, у которого тип данных varchar2, он может принимать значение NULL.

Теперь единственная проблема в Oracle/PLSQL CREATE TABLE, что не определен primary key (первичный ключ) для таблицы customers. Мы изменим содержание предложения CREATE TABLE и определим customer_id в качестве первичного ключа следующим образом:
```
Oracle PL/SQL
CREATE TABLE customers
( customer_id number(10) NOT NULL,
  customer_name varchar2(50) NOT NULL,
  city varchar2(50),
  CONSTRAINT customers_pk PRIMARY KEY (customer_id));
```

### Команда If-elsif-else

_Синтаксис:_

```
IF <condition 1> THEN
    Job 1;
[ELSIF <condition 2> THEN
     Job 2;
]
[ELSE
     Job n + 1;
]
END IF;
```

Пример:

```
If v_Option = 1 Then
   v_Action := 'Run';
Elsif v_Option = 2 Then
   v_Action := 'Backup';
Elsif v_Option = 3 Then
   v_Action := 'Stop';
Else
   v_Action := 'Invalid';
End If;
```

### CASE

В Oracle/PLSQL оператор CASE имеет функциональность IF-THEN-ELSE. Начиная с Oracle 9i, вы можете использовать оператор CASE в SQL предложении.

Синтаксис
```
CASE [ expression ]

   WHEN condition_1 THEN result_1

   WHEN condition_2 THEN result_2
   …
   WHEN condition_n THEN result_n
   ELSE result
END
```

_Параметры или аргументы:_

_expression_ не является обязательным. 
Это значение, которое вы сравниваете с условиями (то есть: condition_1, condition_2 … condition_n).

_condition_1 .. condition_n_ должны быть одного типа. Условия оцениваются по порядку, одно за другим. 
После того, как условие примет значение TRUE (истина), оператор CASE вернет результат, и не будет оценивать условия дальше.

_result_1 .. result_n_ все должны быть одного типа данных. 
Это значение возвращается единожды, когда условие примет TRUE (истина).

Пример:

```
SELECT table_name,
CASE owner
  WHEN 'SYS' THEN 'The owner is SYS'
  WHEN 'SYSTEM' THEN 'The owner is SYSTEM'
  ELSE 'The owner is another value'
END
FROM all_tables;
```

### Команда NULL
Каждая команда программы, как правило, выполняет некоторое действие. Однако бывают
случаи, когда нужно просто указать компилятору PL/SQL, чтобы он не делал ничего, и тогда на помощь приходит оператор NULL. 
Он имеет следующий формат:
```
NULL;
```
Команда NULL состоит из ключевого слова NULL,  за которым следует точка с запятой (;) — она указывает, 
что это команда, а не значение NULL. В программе эта команда не делает ничего, если не считать передачи 
управления следующей исполняемой команде.

Если переменной присваивается значение по умолчанию, вы также можете указать, что переменная всегда должна оставаться определенной (отличной от NULL). Для этого в объявление включается выражение NOT NULL. Например, следующее объявление инициализирует переменную company_name и указывает, что переменная всегда должна оставаться отличной от NULL:
```
company_name VARCHAR2(60) NOT NULL DEFAULT 'PCS R US';
```
При попытке выполнения следующей операции в программе будет инициировано исключение VALUE_ERROR:
```
company_name := NULL;
```
Кроме того, следующее объявление приводит к ошибке компиляции, так как в объявлении не указано исходное значение:
```
company_name VARCHAR2(60) NOT NULL; -- NOT NULL требует исходного значения!
```

### Не предопределенный цикл (LOOP)

_Синтаксис:_

```
LOOP
 -- Выполняются определенные команды
EXIT WHEN <Condition>;
END LOOP;
```

Пример:

```
x := 0;
Loop
 x := x + 1;
 y := y - x;
Exit When x > y;
End Loop;
```

### Предопределенный цикл (FOR LOOP)

_Синтаксис:_

```
FOR v_Index IN <Min value> .. <Max value>
LOOP
 -- Do something here
END LOOP;
```

Пример:

```
x := 0;
For v_Idx In 1 .. 100 Loop
 x := x + 1;
End Loop;
```

### Цикл while (WHILE)

```
WHILE <Condition> LOOP
 -- Do something here
END LOOP;
```

Пример:

```
v_Text Varchar2(100);
...
 
While Length(v_Text) < 50 Loop
   v_Text := v_Text || '00';
End Loop;
```

