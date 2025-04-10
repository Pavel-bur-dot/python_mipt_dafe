# Vector2D

Решения необходимо отправить через систему [Яндекс.Контест](https://contest.yandex.ru/contest/71311/enter/?retPage=).

## Условие

Студент К. очень любит компьютерные игры, особенно ему нравятся игры в жанре платформер. Также студент К. очень любит программировать на Python. Однажды К. решил совместить свои увлечения и написать свою игру в жанре платформер. Из различных материалов он узнал, что при разработке компьютерных игр в жанре платформер часто используются двумерные вектора для описания скоростей и ускорений объектов. Поскольку К. не хотел зависеть ни от каких сторонних библиотек, всю логику работы с двумерными векторами он решил реализовать самостоятельно.

По задумке K. двумерный вектор будет описываться объектом типа `Vector2D`. К данному объекту были сформулированы следующие требования:

- `Vector2D` должен иметь два атрибута типа `float`: `abscissa` и `ordinate` - абсцисса и ордината вектора. Данные атрибуты определяются в момент инициализации нового объекта типа `Point2D`. По умолчанию значения этих атрибутов - `0.0` Также эти атрибуты должны быть доступны только на чтение. Пример использования:
    ```python
    vector = Vector2D(1, 3)
    print(vector.abscissa, vector.ordinate)
    # 1 3

    vector = Vector2D()
    print(vector.abscissa, vector.ordinate)
    # 0 0

    vector.abscissa = 42
    # AttributeError
    ```

- При использовании объекта типа `Vector2D` в качестве аргумента функции `print()` в консоль должна печататься строка, представляющая собой команду создания данного объекта. Пример:
    ```python
    vector = Vector2D(1, 3)
    print(vector)
    # Vector2D(abscissa=1, ordinate=3)
    ```

- Объекты типа `Vector2D` должны поддерживать использование операторов `==` и `!=`. Причем два объекта типа `Vector2D` считаются равными друг другу, если значения их абсцисс и ординат равны между собой.

- Для объектов типа `Vector2D` определены отношения порядка. Т.е. определены операторы `<`, `<=`, `>`, `>=`. Объект `v1` тип `Vector2D` считается меньше объекта `v2` типа `Vector2D`, если `v1.abscissa < v2.abscissa` или если `v1.abscissa == v2.abscissa && v1.ordinate < v2.ordinate`.

- Для объекта типа `Vector2D` определена операция `abs`. Результат выполнение этой операции - действительное число - длина вектора, рассчитанная в соответствии с l2 нормой (Евклидово расстояние).

- Для объекта типа `Vector2D` определено преобразование в логический тип данных с помощью `bool`. Причем операция должна возвращать `False`, если длина вектора равна `0`, и `True` - иначе.

- Для объекта типа `Vector2D` определено умножение на число справа и умножение на число слева. Результат умножения - новый объект типа `Vector2D`, абсцисса и ордината которого - абсцисса и ордината исходного объекта, умноженные на число. Пример:
    ```python
    vector = Vector2D(1, 1)
    print(vector * 5)
    # Vector2D(abscissa=5, ordinate=5)
    print(5 * vector)
    # Vector2D(abscissa=5, ordinate=5)
    print((5 * vector) is vector)
    # False
    ```

- Для объекта типа `Vector2D` определена операция деления на число. Результат деления - новый объект типа `Vector2D`, абсцисса и ордината которого - абсцисса и ордината исходного объекта, умноженные на число, обратное данному. Причем операция деления числа на вектор не определена. Пример:
    ```python
    vector = Vector2D(5, 5)
    print(vector / 5)
    # Vector2D(abscissa=1, ordinate=1)
    print((vector / 5) is vector)
    # False
    print(5 / vector)
    # TypeError
    ```

- Для объекта типа `Vector2D` определены операции сложения с числом справа, сложения с числом слева и сложение с другим объектом `Vector2D`. Результат сложения - новый объект типа `Vector2D`. При сложении с числом, абсцисса и ордината нового вектора - абсцисса и ордината исходного вектора, увеличенные на заданное число. При сложении с другим вектором, абсцисса и ордината полученного вектора - сумма абсцисс и ординат векторов, соответственно.

- Для объекта типа `Vector2D` определены операции вычитания числа справа и вычитание другого объекта `Vector2D` по аналогии со сложением.

- Для объекта типа `Vector2D` определена операция унарного минуса. Результат выполнения операции - новый объект типа `Vector2D`, направление которого противоположно направлению исходного вектора. 

- Для объекта типа `Vector2D` определены операции преобразования во все числовые типы данных. При преобразовании `Vector2D` в `complex` на выходе необходимо получить комплексное число, действительная часть которого соответствует абсциссе вектора, а мнимая - ординате. При преобразовании `Vector2D` во `float` результат соответствует длине вектора. При преобразовании в `int` результат - целая часть длины вектора.

- Для объектов типа `Vector2D` определено скалярное произведение, которое осуществляется с помощью оператора `@`. Результат - действительное число. Пример:
    ```python
    vector1 = Vector(0, 1)
    vector2 = Vector(1, 0)
    print(vector1 @ vector2)
    # 0
    ```

- Для объектов типа `Vector2D` определена операция `get_angle(self, other: Vector2D)`, которая позволяет вычислить угол между двумя векторами. Результат выполнения операции - действительное число. При попытке рассчитать угол между данным вектором и нулевым вектором `Vector2D(0, 0)` необходимо возбудить исключение `ValueError`. Текст сообщения об ошибке должен сообщить пользователю, что расчет угла между данным вектором и нулевым вектором невозможен.

- Для объектов типа `Vector2D` определена операция вычисления сопряженного вектора. Для вектора `v1` с абсциссой `abs1` и ординатой `ord1` сопряженным вектором будет называться такой вектор `v1`, абсцисса которого `abs2` будет равна `abs1`, а ордината `ord2` будет равна `-ord1`. Операция должна возвращать новый объект типа `Vector2D`.

Помогите К. реализовать задуманный объект.
