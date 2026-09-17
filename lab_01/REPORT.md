# Часть 1.
### Выполнение выражения в консоли(REPL):
<img width="302" height="86" alt="image" src="https://github.com/user-attachments/assets/97a854c7-a01e-4af7-9e6d-4bf07a464748" />

### Выполнение выражения в файле:
<img width="277" height="296" alt="image" src="https://github.com/user-attachments/assets/2bc1f884-bf10-4478-8c0e-3a2e72bd8d9d" />


#### В REPL результат отображается автоматически, так как он автоматически считывает и выводит результат выражения в консоль. 
#### В скриптовом режиме, при запуске файла task_1.py интерпретатор последовательно выполняет команды, данные ему. Он получает выражение 2+3*4 (14), но не выводит, так как не была дана команда print.

### Измененный корректный файл:
<img width="288" height="290" alt="image" src="https://github.com/user-attachments/assets/9fcf8ad9-adb7-4073-ac14-780ad6822646" />





# Часть 2.
``` python
course = "Python"
hours = 4 * 2
print(f"{course}: {hours} часов")
```
### Выражения:
#### строка: "Python"
#### числа: 4 2
#### арифметическое выражение: 4 * 2
#### переменные: course hours
#### f-строка/форматирование: f"{course}: {hours} часов"
#### вызов функции: print(f"{course}: {hours} часов")


### Инструкции:
#### присваивание: course = "Python" и hours = 4 * 2
#### вызов функции: print(f"{course}: {hours} часов")


### Литералы:
#### "Python", ": ", " часов", 4, 2


### Создаваемые имена:
#### course и hours


# Часть 3.
```
> python --version
Python 3.13.5
```

```
> python -m ast task_1.py
Module(
   body=[
      Assign(
         targets=[
            Name(id='course', ctx=Store())],
         value=Constant(value='Python')),
      Assign(
         targets=[
            Name(id='hours', ctx=Store())],
         value=BinOp(
            left=Constant(value=4),
            op=Mult(),
            right=Constant(value=2))),
      Expr(
         value=Call(
            func=Name(id='print', ctx=Load()),
            args=[
               JoinedStr(
                  values=[
                     FormattedValue(
                        value=Name(id='course', ctx=Load()),
                        conversion=-1),
                     Constant(value=': '),
                     FormattedValue(
                        value=Name(id='hours', ctx=Load()),
                        conversion=-1),
                     Constant(value=' часов')])]))])
```
### Присваивание
```
Assign(
         targets=[
            Name(id='course', ctx=Store())],
         value=Constant(value='Python')),
Assign(
         targets=[
            Name(id='hours', ctx=Store())],
```
### Арифметическая операция
```
value=BinOp(
            left=Constant(value=4),
            op=Mult(),
            right=Constant(value=2))),
```
### Вызов print
```
value=Call(
            func=Name(id='print', ctx=Load()),
```

## Дизассемблирование
```
> python -m dis task_1.py
  0           RESUME                   0

  2           LOAD_CONST               0 ('Python')
              STORE_NAME               0 (course)

  3           LOAD_CONST               1 (8)
              STORE_NAME               1 (hours)

  4           LOAD_NAME                2 (print)
              PUSH_NULL
              LOAD_NAME                0 (course)
              FORMAT_SIMPLE
              LOAD_CONST               2 (': ')
              LOAD_NAME                1 (hours)
              FORMAT_SIMPLE
              LOAD_CONST               3 (' часов')
              BUILD_STRING             4
              CALL                     1
              POP_TOP
              RETURN_CONST             4 (None)
```

### Загрузка константы 
```
  2           LOAD_CONST               0 ('Python')
```
### Вызов функции 
```
              CALL                     1
```

## Почему байткод CPython нельзя считать машинным кодом процессора?
#### Машинный код процессора выполняется напрямую физическим процессором, он считывает команы и подает электрические сигналы. 
#### Байткод выполняется виртуальной машиной CPython.

