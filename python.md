## 匿名函数

1. `lambda arguments: expression` 

   ### 1. 基本语法

   **`arguments`**：函数的参数，可以是一个或多个，参数之间用逗号分隔。

   **`expression`**：一个表达式，定义了函数的返回值。这个表达式会被计算并返回。

   ### 2. 特点

   - `lambda` 函数可以有多个参数，但只能有一个表达式，且没有 `return` 语句。这个表达式的结果会自动作为返回值。
   - `lambda` 函数不需要显式命名，因此通常称为**匿名函数**。
   - `lambda` 函数的返回值是表达式的值，不像普通函数那样通过 `return` 返回。

   ### 3. 示例

   #### 1. 简单的 `lambda` 函数

   ```
   python复制代码# 计算两个数的和
   add = lambda x, y: x + y
   print(add(3, 5))  # 输出: 8
   ```

   这个例子中，`lambda x, y: x + y` 定义了一个匿名函数，它接收两个参数 `x` 和 `y`，并返回它们的和。然后将这个匿名函数赋值给变量 `add`，从而可以像调用普通函数一样使用它。

   #### 2. 使用 `lambda` 与 `sorted` 一起排序

   ```
   python复制代码# 按照字符串的长度对列表进行排序
   words = ["apple", "banana", "cherry", "date"]
   sorted_words = sorted(words, key=lambda word: len(word))
   print(sorted_words)  # 输出: ['date', 'apple', 'banana', 'cherry']
   ```

   这里，`lambda word: len(word)` 是一个接受单个参数 `word` 的匿名函数，它返回 `word` 的长度。`sorted()` 函数使用这个 `lambda` 函数作为 `key` 参数，对字符串列表按照长度进行排序。

   #### 3. 多个参数的 `lambda` 函数

   ```
   python复制代码# 求两个数的最大值
   max_value = lambda a, b: a if a > b else b
   print(max_value(4, 7))  # 输出: 7
   ```

   在这个例子中，`lambda` 函数有两个参数 `a` 和 `b`，它返回两个数中的较大值。

   #### 4. 与 `map` 或 `filter` 等函数结合使用

   - **`map()`**：对可迭代对象中的每个元素应用 `lambda` 函数。

   ```
   python复制代码numbers = [1, 2, 3, 4, 5]
   squared = map(lambda x: x ** 2, numbers)
   print(list(squared))  # 输出: [1, 4, 9, 16, 25]
   ```

   - **`filter()`**：过滤出符合条件的元素。

   ```
   python复制代码numbers = [1, 2, 3, 4, 5, 6]
   even_numbers = filter(lambda x: x % 2 == 0, numbers)
   print(list(even_numbers))  # 输出: [2, 4, 6]
   ```

   ### 4. 与普通函数的对比

   `lambda` 函数通常用于编写短小的函数，其代码形式比常规的 `def` 函数更简洁。然而，它只能包含一个表达式，不能有复杂的语句或多行代码。

   例如，普通函数和 `lambda` 函数的对比：

   ```
   python复制代码# 使用普通函数
   def add(x, y):
       return x + y
   
   # 使用lambda函数
   add_lambda = lambda x, y: x + y
   
   print(add(3, 4))        # 输出: 7
   print(add_lambda(3, 4))  # 输出: 7
   ```

   ### 5. 常见用途

   - **作为高阶函数的参数**：`lambda` 常用在如 `map()`, `filter()`, `reduce()`, `sorted()` 等函数中，作为回调函数。
   - **简化代码**：在需要快速实现简单函数时，`lambda` 提供了简洁的语法，避免了定义冗长的命名函数。

   ### 6. 限制

   - 由于 `lambda` 函数只能包含一个表达式，因此它无法处理复杂的逻辑，比如多行代码、循环、条件语句等。
   - 在需要进行多次调用时，使用普通函数（通过 `def`）会更为清晰和易于调试。

## 内置函数

1. `sorted(iterable, key=None, reverse=False)`

   **参数：**

   - `iterable`：待排序的可迭代对象（如列表、元组、字符串、字典等）。
   - `key`：一个函数，用于从每个元素中提取出用于比较的值，默认是 `None`，表示直接比较元素的值。如果指定了 `key`，则会根据 `key` 函数的返回值来进行排序。
   - `reverse`：布尔值，默认为 `False`。如果设为 `True`，则将按降序排序；如果设为 `False`，则按升序排序。

   **返回值：**

   - 返回一个排序后的新列表，原始的可迭代对象不会被修改。

   **举例：**

   1. **使用 `key` 参数自定义排序规则**。例如，根据字符串的长度排序：

      ```
      words = ["apple", "banana", "cherry", "date"]
      sorted_words = sorted(words, key=len)
      print(sorted_words)  # 输出: ['date', 'apple', 'banana', 'cherry']
      ```

   2. **对字典进行排序**。
      `sorted()` 可以对字典的键进行排序：

      ```
      my_dict = {"apple": 3, "banana": 2, "cherry": 5}
      sorted_keys = sorted(my_dict)
      print(sorted_keys)  # 输出: ['apple', 'banana', 'cherry']
      ```

      如果要按字典的值排序：

      ```
      sorted_by_value = sorted(my_dict.items(), key=lambda item: item[1])
      print(sorted_by_value)  # 输出: [('banana', 2), ('apple', 3), ('cherry', 5)]
      ```

      

