## Базовые команды PL/SQL

В данном уроке приведен обзор команд PL/SQL. Вы поймете больше через примеры в следующих частях.

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

