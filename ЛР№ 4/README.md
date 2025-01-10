# Результаты выполнения
Весь код можно посмотреть в репозитории
## 1 задание
### gen_fib.py
Реализована сопрограмма `my_genn`, которая принимает число `n` и возвращает список из первых `n` чисел ряда Фибоначчи.

Для удобства работы добавлен декоратор fib_coroutine, автоматически инициализирующий генератор:
```python
@fib_coroutine
def my_genn():
    ...
```
Результы работы программы:

![image](https://github.com/user-attachments/assets/377994f6-0ae9-4325-8f04-bee0cdb3e4a0)
### test_fib.py
Написаны тесты с использованием pytest, которые проверяют корректность работы генератора (тесты проверяют правильность вычисления чисел Фибоначчи для разных значений n)

Результаты тестов:

![image](https://github.com/user-attachments/assets/58f7433d-b1a2-4a9b-b222-24f3eec8b9f9)

## 2 задание
### fibonacchi_lst.py
Создан класс FibonacchiLst, который фильтрует заданный список, возвращая только элементы, принадлежащие ряду Фибоначчи:

```python
lst = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 1]
fib_iterator = FibonacchiLst(lst)
print(list(fib_iterator))  # [0, 1, 2, 3, 5, 8, 1]
```
Для фильтрации заранее генерируется множество чисел Фибоначчи до максимального значения в списке:

```python
def _generate_fib_set(self, max_value):
    a, b = 0, 1
    fib_set = {a, b}
    while b <= max_value:
        a, b = b, a + b
        fib_set.add(b)
    return fib_set
```
Итератор реализован с помощью методов __iter__ и __next__, которые возвращают только элементы из ряда Фибоначчи:

```python
def __next__(self):
    while self.idx < len(self.lst):
        value = self.lst[self.idx]
        self.idx += 1
        if value in self.fib_set:
            return value
    raise StopIteration
```
Результаты работы:


![image](https://github.com/user-attachments/assets/513bd803-5ce6-4134-b333-5fc80808f6e5)

### test_fibonacchi_lst.py
Для проверки работы итератора были написаны тесты.

Результат работы тестирования итератора:

![image](https://github.com/user-attachments/assets/706f96d2-77a5-4e0d-b7b8-0f907963e767)

