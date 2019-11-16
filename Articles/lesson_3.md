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

