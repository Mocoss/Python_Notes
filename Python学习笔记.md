# 🐍 Python 超详细学习笔记（完整版）

> **适用人群**：零基础入门 / 系统复习 / 随时查阅  
> **版本**：Python 3.x  
> **更新说明**：每学完一节，在「我的笔记」补充自己的理解和代码


[toc]

---

## 第一篇：基础入门

---

### 一、Python 简介与环境搭建

#### 1.1 Python 是什么
- 高级编程语言，语法简洁，接近自然语言
- 解释型语言，不需要编译，写完直接运行
- 跨平台：Windows / Mac / Linux 都能跑
- 应用领域：Web开发、数据分析、人工智能、自动化、爬虫、运维等

#### 1.2 安装 Python
**Windows：**
1. 官网下载：python.org/downloads
2. 安装时勾选「Add Python to PATH」
3. 打开 cmd，输入 `python --version` 验证

**Mac：**
```bash
# 方式1：官网下载安装包
# 方式2：Homebrew
brew install python3
```

#### 1.3 第一个 Python 程序
```python
# hello.py
print("Hello, Python!")
print("我正在学习Python")
```

**运行方式：**
```bash
python hello.py
```

#### 1.4 交互式模式（REPL）
直接在终端输入 `python` 进入交互模式，一行一行执行：
```python
>>> 1 + 1
2
>>> print("hi")
hi
>>> exit()  # 退出
```

**我的笔记：**
> 

---

### 二、基础语法规则

#### 2.1 缩进（最重要！）
Python **用缩进区分代码块**，不是大括号 `{}`。
- 推荐用 **4个空格** 缩进
- 同一层级代码必须对齐
- 缩进错误会直接报错 `IndentationError`

```python
# ✅ 正确
if True:
    print("第一行")
    print("第二行")

# ❌ 错误（缩进不一致）
if True:
    print("第一行")
      print("第二行")  # 报错！
```

#### 2.2 注释
```python
# 这是单行注释，#后面的内容都会被忽略

"""
这是多行注释
也叫文档字符串 docstring
通常用在函数、类、模块开头说明用途
"""

'''
也可以用三个单引号
效果一样
'''
```

#### 2.3 语句换行
```python
# 一行一条语句
print("hello")
print("world")

# 一行多条语句（用分号分隔，不推荐）
print("a"); print("b")

# 一条语句多行（用反斜杠，或括号自动换行）
total = 1 + 2 + 3 + \
        4 + 5

# 推荐：用括号自动换行
total = (1 + 2 + 3 +
         4 + 5)
```

#### 2.4 标识符命名规则
变量名、函数名、类名等统称为标识符：
1. 由**字母、数字、下划线**组成
2. **不能以数字开头**
3. 不能是 Python 关键字（保留字）
4. **区分大小写**（`age` 和 `Age` 是两个不同变量）

```python
# ✅ 合法命名
name = "Tom"
age_1 = 18
_user = "test"

# ❌ 非法命名
1name = "Tom"    # 数字开头
my-name = "Tom"  # 含减号
$money = 100     # 含特殊符号
```

#### 2.5 命名规范（约定俗成）
- **变量/函数名**：小写+下划线（蛇形命名）`user_name`
- **类名**：大驼峰 `MyClass`
- **常量**：全大写 `MAX_SIZE`
- **模块名**：小写+下划线 `my_module.py`

#### 2.6 Python 关键字（保留字）
共 35 个，不能用作变量名：
```
False, None, True, and, as, assert, async, await,
break, class, continue, def, del, elif, else, except,
finally, for, from, global, if, import, in, is,
lambda, match, nonlocal, not, or, pass, raise, return,
try, while, with, yield, case
```

**查看方法：**
```python
import keyword
print(keyword.kwlist)       # 列出所有关键字
print(keyword.iskeyword("if"))  # 判断是否为关键字
```

**我的笔记：**
> 

---

### 三、变量与数据类型

#### 3.1 什么是变量
变量就是给数据起个名字，方便后面使用。
```python
name = "张三"  # 把字符串"张三"存到变量name里
age = 18       # 把数字18存到变量age里
print(name)    # 使用变量
print(age)
```

#### 3.2 变量的特点
- Python 是**动态类型**语言，变量不需要声明类型
- 同一个变量可以反复赋值不同类型
- 变量本质是「标签」，贴在数据对象上

```python
x = 10      # x是整数
print(type(x))  # <class 'int'>

x = "hello" # x变成字符串
print(type(x))  # <class 'str'>
```

#### 3.3 多变量赋值
```python
# 同时给多个变量赋值
a, b, c = 1, 2, 3

# 多个变量赋同一个值
x = y = z = 0

# 交换两个变量（Python特有，不用临时变量）
a, b = b, a
```

#### 3.4 Python 基本数据类型总览

| 类型分类 | 具体类型 | 说明 | 示例 |
|----------|----------|------|------|
| 数值类型 | `int` | 整数（任意精度） | `10`, `-5` |
| 数值类型 | `float` | 浮点数（小数） | `3.14`, `1.5e2` |
| 数值类型 | `bool` | 布尔值 | `True`, `False` |
| 数值类型 | `complex` | 复数 | `1+2j` |
| 序列类型 | `str` | 字符串 | `"hello"` |
| 序列类型 | `list` | 列表 | `[1, 2, 3]` |
| 序列类型 | `tuple` | 元组 | `(1, 2, 3)` |
| 序列类型 | `range` | 范围 | `range(10)` |
| 映射类型 | `dict` | 字典 | `{"a": 1}` |
| 集合类型 | `set` | 集合 | `{1, 2, 3}` |
| 集合类型 | `frozenset` | 不可变集合 | `frozenset([1,2])` |
| 空类型 | `NoneType` | 空值 | `None` |

#### 3.5 查看数据类型
```python
print(type(10))        # <class 'int'>
print(type("hello"))   # <class 'str'>
print(type([1,2,3]))   # <class 'list'>

# 判断类型
isinstance(10, int)        # True
isinstance("hi", str)      # True
isinstance([1,2], list)    # True
```

#### 3.6 类型转换
```python
# 转整数 int()
int("123")      # 123
int(3.14)       # 3（截断小数部分，不是四舍五入）
int(True)       # 1

# 转浮点数 float()
float("3.14")   # 3.14
float(10)       # 10.0

# 转字符串 str()
str(123)        # "123"
str(3.14)       # "3.14"
str(True)       # "True"

# 转列表 list()
list("abc")     # ['a', 'b', 'c']
list((1,2,3))   # [1, 2, 3]

# 转元组 tuple()
tuple([1,2,3])  # (1, 2, 3)

# 转集合 set()
set([1,2,2,3])  # {1, 2, 3}（自动去重）

# 转布尔值 bool()
bool(0)         # False
bool(1)         # True
bool("")        # False
bool("hello")   # True
bool([])        # False
bool([1,2])     # True
```

**我的笔记：**
> 

---

---

## 第二篇：数据类型详解

---

### 四、数值类型 int/float/bool

#### 4.1 整数 int
Python 的整数**没有大小限制**，可以无限大：
```python
a = 10
b = -100
c = 9999999999999999999999999999  # 超大数也没问题
print(c)
```

**不同进制表示：**
```python
# 十进制（默认）
10

# 二进制（0b开头）
0b1010   # 等于十进制的10

# 八进制（0o开头）
0o12     # 等于十进制的10

# 十六进制（0x开头）
0xA      # 等于十进制的10

# 进制转换函数
bin(10)   # 转二进制：'0b1010'
oct(10)   # 转八进制：'0o12'
hex(10)   # 转十六进制：'0xa'
```

#### 4.2 浮点数 float
就是小数，有两种写法：
```python
# 普通写法
3.14
-2.5

# 科学计数法
1.5e2    # 1.5 × 10² = 150.0
1.5e-2   # 1.5 × 10⁻² = 0.015
```

**⚠️ 浮点数精度问题：**
```python
print(0.1 + 0.2)  # 0.30000000000000004（不是0.3！）
```
原因：计算机用二进制存储浮点数，有些小数无法精确表示。
解决：用 `decimal` 模块做精确计算。

#### 4.3 布尔值 bool
只有两个值：`True` 和 `False`（首字母大写）
```python
is_ok = True
is_error = False
```

**布尔值本质是整数的子类：**
```python
print(True == 1)   # True
print(False == 0)  # True
print(True + 1)    # 2
print(False + 10)  # 10
```

**什么情况下值为 False？**
以下值在布尔判断中都是 `False`：
```python
bool(False)    # False
bool(None)     # False
bool(0)        # False（整数0）
bool(0.0)      # False（浮点数0）
bool("")       # False（空字符串）
bool([])       # False（空列表）
bool(())       # False（空元组）
bool({})       # False（空字典/空集合）
bool(set())    # False（空集合）
```
其他所有值都是 `True`。

#### 4.4 常用数学函数
```python
abs(-10)        # 10（绝对值）
round(3.14159, 2)  # 3.14（四舍五入，保留2位小数）
max(1, 5, 3)    # 5（最大值）
min(1, 5, 3)    # 1（最小值）
sum([1,2,3,4])  # 10（求和）
pow(2, 3)       # 8（幂运算，等价于2**3）
divmod(7, 3)    # (2, 1)（商和余数）
```

#### 4.5 math 模块常用函数
```python
import math

math.sqrt(16)       # 4.0（平方根）
math.pow(2, 3)      # 8.0（幂运算）
math.floor(3.7)     # 3（向下取整）
math.ceil(3.2)      # 4（向上取整）
math.trunc(3.7)     # 3（截断小数部分）
math.pi             # 3.1415926535...（圆周率）
math.e              # 2.718281828...（自然常数）
math.sin(math.pi/2) # 1.0（正弦）
math.cos(0)         # 1.0（余弦）
math.log(100, 10)   # 2.0（对数）
math.factorial(5)   # 120（阶乘）
math.gcd(12, 8)     # 4（最大公约数）
```

**我的笔记：**
> 

---

### 五、字符串 str 详解

#### 5.1 字符串定义
```python
# 单引号
s1 = 'hello'

# 双引号
s2 = "world"

# 三引号（多行字符串）
s3 = """第一行
第二行
第三行"""

# 空字符串
s4 = ""
```

**单双引号嵌套：**
```python
# 外面用双引号，里面可以直接用单引号
print("I'm Tom")

# 外面用单引号，里面可以直接用双引号
print('他说："你好"')
```

#### 5.2 转义字符
用 `\` 开头的特殊字符：

| 转义字符 | 含义 |
|----------|------|
| `\n` | 换行 |
| `\t` | 制表符（Tab） |
| `\\` | 反斜杠本身 |
| `\'` | 单引号 |
| `\"` | 双引号 |
| `\r` | 回车 |
| `\b` | 退格 |

```python
print("hello\nworld")  # 换行
print("hello\tworld")  # Tab缩进
print("C:\\Users\\Tom")  # 路径中的反斜杠
```

**原始字符串 r''：**
在字符串前加 `r`，转义字符失效，原样输出：
```python
print(r"C:\Users\Tom")  # 不用写双反斜杠了
print(r"\n\t")          # 直接输出\n\t
```

#### 5.3 字符串索引和切片
字符串是**有序序列**，每个字符都有下标（索引），从 **0** 开始。

```
  0   1   2   3   4   5
  P   y   t   h   o   n
 -6  -5  -4  -3  -2  -1
```

```python
s = "Python"

# 索引取值
s[0]    # 'P'（第一个）
s[5]    # 'n'（最后一个）
s[-1]   # 'n'（倒数第一个）
s[-2]   # 'o'（倒数第二个）
```

**切片：** 取子串，格式 `s[start:end:step]`
- 含头不含尾（包含start，不包含end）
- start省略默认从头开始
- end省略默认到末尾
- step省略默认步长为1

```python
s = "Python"

s[1:4]     # 'yth'（索引1到3）
s[:3]      # 'Pyt'（前3个）
s[3:]      # 'hon'（从第3个到末尾）
s[:]       # 'Python'（整个字符串，复制一份）
s[::2]     # 'Pto'（每隔一个取一个）
s[::-1]    # 'nohtyP'（反转字符串）
s[-3:-1]   # 'ho'
```

#### 5.4 字符串运算
```python
# 拼接 +
"Hello" + " " + "World"  # 'Hello World'

# 重复 *
"Hi" * 3   # 'HiHiHi'

# 成员判断 in / not in
"P" in "Python"     # True
"abc" in "Python"   # False

# 长度 len()
len("Python")       # 6
```

#### 5.5 字符串方法大全

##### 🔍 查找与判断
```python
s = "Hello World"

# 查找子串位置
s.find("World")     # 6（找到返回起始索引）
s.find("abc")       # -1（找不到返回-1）
s.rfind("o")        # 7（从右边找）

# 查找子串（找不到报错）
s.index("World")    # 6
# s.index("abc")   # 报错 ValueError

# 统计出现次数
s.count("o")        # 2
s.count("l")        # 3

# 判断开头/结尾
s.startswith("Hello")  # True
s.endswith("ld")       # True

# 判断内容
s.isalpha()        # False（有空格，不全是字母）
"abc".isalpha()    # True（全是字母）
"123".isdigit()    # True（全是数字）
"abc123".isalnum() # True（字母+数字）
"  ".isspace()     # True（全是空白字符）
"Hello".isupper()  # False（不全大写）
"HELLO".isupper()  # True
"hello".islower()  # True
"Hello World".istitle()  # True（每个单词首字母大写）
```

##### ✂️ 大小写转换
```python
s = "Hello World"

s.upper()          # 'HELLO WORLD'（全大写）
s.lower()          # 'hello world'（全小写）
s.swapcase()       # 'hELLO wORLD'（大小写互换）
s.title()          # 'Hello World'（每个单词首字母大写）
s.capitalize()     # 'Hello world'（首字母大写，其余小写）
```

##### 🧹 去除空白
```python
s = "  hello  "

s.strip()          # 'hello'（去掉两边空白）
s.lstrip()         # 'hello  '（去掉左边空白）
s.rstrip()         # '  hello'（去掉右边空白）

# 也可以去掉指定字符
"***hello***".strip("*")  # 'hello'
```

##### 🔗 分割与拼接
```python
# 分割
s = "a,b,c,d"
s.split(",")       # ['a', 'b', 'c', 'd']（按逗号分割）
"hello world".split()  # ['hello', 'world']（默认按空白分割）

# 按行分割
"line1\nline2\nline3".splitlines()  # ['line1', 'line2', 'line3']

# 拼接（用指定字符连接列表）
"-".join(["a", "b", "c"])   # 'a-b-c'
" ".join(["Hello", "World"]) # 'Hello World'
```

##### 🔄 替换
```python
s = "Hello World"

s.replace("World", "Python")   # 'Hello Python'
"aabbaa".replace("a", "x")     # 'xxbbxx'（全部替换）
"aabbaa".replace("a", "x", 2)  # 'xxbbaa'（只替换前2个）
```

##### 📏 对齐填充
```python
s = "hi"

s.center(10)        # '   hi   '（居中，总宽10）
s.center(10, "*")   # '****hi****'

s.ljust(10)         # 'hi        '（左对齐）
s.rjust(10)         # '        hi'（右对齐）

s.zfill(5)          # '000hi'（左边补0，总宽5）
"123".zfill(5)      # '00123'
```

##### 🔤 编码
```python
# 字符串转字节
"你好".encode("utf-8")   # b'\xe4\xbd\xa0\xe5\xa5\xbd'

# 字节转字符串
b'\xe4\xbd\xa0\xe5\xa5\xbd'.decode("utf-8")  # '你好'
```

#### 5.6 字符串格式化

##### 方式1：% 格式化（老式）
```python
name = "Tom"
age = 18

"我叫%s，今年%d岁" % (name, age)
# '我叫Tom，今年18岁'
```

| 占位符 | 含义 |
|--------|------|
| `%s` | 字符串 |
| `%d` | 整数 |
| `%f` | 浮点数 |
| `%.2f` | 保留2位小数的浮点数 |
| `%x` | 十六进制 |

```python
"%.2f" % 3.14159   # '3.14'
"%5d" % 123        # '  123'（占5位，右对齐）
"%-5d" % 123       # '123  '（左对齐）
```

##### 方式2：format() 方法（推荐）
```python
name = "Tom"
age = 18

"我叫{}，今年{}岁".format(name, age)
# '我叫Tom，今年18岁'

# 按索引
"{0}今年{1}岁，{0}喜欢Python".format(name, age)

# 按名字
"我叫{name}，今年{age}岁".format(name="Tom", age=18)

# 格式化数字
"{:.2f}".format(3.14159)     # '3.14'
"{:0>5d}".format(123)        # '00123'（补0，右对齐）
"{:,}".format(1000000)       # '1,000,000'（千分位）
"{:.1%}".format(0.25)        # '25.0%'（百分比）
```

##### 方式3：f-string（最推荐，Python 3.6+）
在字符串前加 `f`，直接在 `{}` 里写变量或表达式：
```python
name = "Tom"
age = 18

f"我叫{name}，今年{age}岁"
# '我叫Tom，今年18岁'

# 可以写表达式
f"明年我{age + 1}岁"

# 格式化数字
pi = 3.1415926
f"{pi:.2f}"       # '3.14'
f"{pi:0>10.2f}"   # '0000003.14'

# 千分位
num = 1000000
f"{num:,}"        # '1,000,000'

# 百分比
f"{0.25:.1%}"     # '25.0%'
```

#### 5.7 字符串遍历
```python
s = "Python"

# 方式1：遍历每个字符
for char in s:
    print(char)

# 方式2：带索引遍历
for i, char in enumerate(s):
    print(i, char)

# 方式3：按索引遍历
for i in range(len(s)):
    print(s[i])
```

**我的笔记：**
> 

---

### 六、列表 list 详解

#### 6.1 列表定义
列表是**有序、可变**的容器，元素类型可以任意。
```python
# 空列表
lst = []
lst = list()

# 有元素的列表
lst = [1, 2, 3, 4, 5]
lst = ["a", "b", "c"]
lst = [1, "hello", 3.14, True, [1,2,3]]  # 混合类型
```

#### 6.2 列表索引和切片
和字符串完全一样：
```python
lst = ["a", "b", "c", "d", "e"]

lst[0]      # 'a'
lst[-1]     # 'e'
lst[1:4]    # ['b', 'c', 'd']
lst[::2]    # ['a', 'c', 'e']
lst[::-1]   # ['e', 'd', 'c', 'b', 'a']（反转）
```

**列表是可变的，可以通过索引修改：**
```python
lst = ["a", "b", "c"]
lst[0] = "A"
print(lst)  # ['A', 'b', 'c']

# 切片批量修改
lst[1:3] = ["B", "C"]
print(lst)  # ['A', 'B', 'C']
```

#### 6.3 列表运算
```python
# 拼接 +
[1,2] + [3,4]    # [1, 2, 3, 4]

# 重复 *
[1, 2] * 3       # [1, 2, 1, 2, 1, 2]

# 成员判断 in
3 in [1,2,3]     # True

# 长度 len()
len([1,2,3])     # 3

# 比较（按顺序逐个比较）
[1, 2, 3] < [1, 2, 4]  # True
```

#### 6.4 列表方法大全

##### ➕ 添加元素
```python
lst = [1, 2, 3]

# append：末尾添加一个元素
lst.append(4)
print(lst)  # [1, 2, 3, 4]

# extend：末尾添加多个元素（把另一个列表拆开加进去）
lst.extend([5, 6])
print(lst)  # [1, 2, 3, 4, 5, 6]

# insert：指定位置插入
lst.insert(0, 0)  # 在索引0处插入0
print(lst)  # [0, 1, 2, 3, 4, 5, 6]
```

##### ➖ 删除元素
```python
lst = ["a", "b", "c", "d", "e"]

# pop：删除并返回指定位置的元素（默认最后一个）
lst.pop()      # 'e'（删除最后一个）
print(lst)     # ['a', 'b', 'c', 'd']

lst.pop(0)     # 'a'（删除第一个）
print(lst)     # ['b', 'c', 'd']

# remove：删除第一个匹配的元素（不返回）
lst.remove("c")
print(lst)     # ['b', 'd']

# del：删除指定位置或切片（关键字，不是方法）
del lst[0]
print(lst)     # ['d']

del lst[:]     # 清空整个列表

# clear：清空列表
lst.clear()
print(lst)     # []
```

##### 🔍 查找与统计
```python
lst = ["a", "b", "c", "a", "b", "a"]

# index：查找元素的索引（找不到报错）
lst.index("b")     # 1（第一个b的位置）
lst.index("b", 2)  # 4（从索引2开始找）

# count：统计出现次数
lst.count("a")     # 3

# in：判断是否存在
"c" in lst         # True
"z" in lst         # False
```

##### 🔄 排序与反转
```python
lst = [3, 1, 4, 1, 5, 9, 2, 6]

# sort：原地排序（修改原列表）
lst.sort()
print(lst)  # [1, 1, 2, 3, 4, 5, 6, 9]

# 降序排序
lst.sort(reverse=True)
print(lst)  # [9, 6, 5, 4, 3, 2, 1, 1]

# 按自定义规则排序（按长度）
words = ["apple", "hi", "banana"]
words.sort(key=len)
print(words)  # ['hi', 'apple', 'banana']

# sorted：返回新的排序后的列表（不修改原列表）
lst = [3, 1, 4]
new_lst = sorted(lst)
print(lst)      # [3, 1, 4]（原列表不变）
print(new_lst)  # [1, 3, 4]

# reverse：原地反转
lst = [1, 2, 3]
lst.reverse()
print(lst)  # [3, 2, 1]

# 切片反转（不修改原列表）
lst = [1, 2, 3]
new_lst = lst[::-1]
print(lst)      # [1, 2, 3]
print(new_lst)  # [3, 2, 1]
```

##### 📋 复制
```python
lst = [1, 2, 3]

# copy：浅拷贝
lst2 = lst.copy()

# 切片拷贝
lst3 = lst[:]

# list() 构造
lst4 = list(lst)
```

#### 6.5 列表遍历
```python
lst = ["a", "b", "c"]

# 方式1：遍历元素
for item in lst:
    print(item)

# 方式2：带索引遍历
for i, item in enumerate(lst):
    print(i, item)

# 方式3：按索引遍历
for i in range(len(lst)):
    print(lst[i])
```

#### 6.6 列表推导式
非常实用的语法，用一行代码生成列表：
```python
# 基本格式：[表达式 for 变量 in 可迭代对象]

# 生成1-10的平方
squares = [x**2 for x in range(1, 11)]
# [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# 带条件：只保留偶数的平方
evens_square = [x**2 for x in range(10) if x % 2 == 0]
# [0, 4, 16, 36, 64]

# 多个循环
pairs = [(x, y) for x in [1,2] for y in [3,4]]
# [(1, 3), (1, 4), (2, 3), (2, 4)]

# 字符串处理
words = ["hello", "world", "python"]
lengths = [len(w) for w in words]  # [5, 5, 6]
upper_words = [w.upper() for w in words]  # ['HELLO', 'WORLD', 'PYTHON']
```

#### 6.7 嵌套列表（二维列表）
```python
# 3行3列的矩阵
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# 取元素
matrix[0][0]   # 1（第一行第一列）
matrix[1][2]   # 6（第二行第三列）

# 遍历二维列表
for row in matrix:
    for item in row:
        print(item)

# 列表推导式生成二维列表
matrix = [[i*j for j in range(1,4)] for i in range(1,4)]
```

#### 6.8 其他常用操作
```python
lst = [3, 1, 4, 1, 5, 9, 2, 6]

# 求和
sum(lst)        # 31

# 最大值、最小值
max(lst)        # 9
min(lst)        # 1

# 平均值
sum(lst) / len(lst)  # 3.875

# 列表拼接（不修改原列表）
lst1 = [1, 2]
lst2 = [3, 4]
lst3 = lst1 + lst2  # [1, 2, 3, 4]

# 重复
[0] * 5        # [0, 0, 0, 0, 0]
```

**我的笔记：**
> 

---

### 七、元组 tuple 详解

#### 7.1 元组定义
元组是**有序、不可变**的容器，类似只读列表。
```python
# 空元组
t = ()
t = tuple()

# 有元素的元组
t = (1, 2, 3)
t = ("a", "b", "c")

# 单个元素的元组（注意逗号！）
t = (1,)   # ✅ 是元组
t = (1)    # ❌ 不是元组，就是整数1
```

#### 7.2 元组的特点
- 不可变：不能增删改元素
- 访问速度比列表快
- 可以作为字典的key（列表不行）
- 解包赋值很方便

#### 7.3 元组支持的操作
```python
t = (1, 2, 3, 4, 5)

# 索引和切片（和列表一样）
t[0]       # 1
t[1:4]     # (2, 3, 4)

# 拼接、重复
t + (6, 7)  # (1, 2, 3, 4, 5, 6, 7)
t * 2       # (1, 2, 3, 4, 5, 1, 2, 3, 4, 5)

# 成员判断
3 in t      # True

# 长度
len(t)      # 5

# 统计、查找
t.count(2)  # 1
t.index(3)  # 2

# 遍历
for item in t:
    print(item)
```

#### 7.4 元组的不可变性
```python
t = (1, 2, [3, 4])

# t[0] = 10  # ❌ 报错，元组元素不能改

# 但如果元素本身是可变对象（如列表），可以修改那个对象的内容
t[2].append(5)
print(t)  # (1, 2, [3, 4, 5])
# 注意：元组存的是列表的引用，引用没变，列表本身变了
```

#### 7.5 元组解包
```python
# 多变量赋值
a, b, c = (1, 2, 3)
print(a, b, c)  # 1 2 3

# 交换两个变量
a, b = b, a

# 用*号收集多余元素
first, *rest = (1, 2, 3, 4, 5)
print(first)  # 1
print(rest)   # [2, 3, 4, 5]

*rest, last = (1, 2, 3, 4, 5)
print(rest)   # [1, 2, 3, 4]
print(last)   # 5

first, *middle, last = (1, 2, 3, 4, 5)
print(first)   # 1
print(middle)  # [2, 3, 4]
print(last)    # 5
```

#### 7.6 元组和列表的区别

| 特性 | 列表 list | 元组 tuple |
|------|-----------|------------|
| 可变性 | 可变（增删改） | 不可变 |
| 语法 | `[]` | `()` |
| 速度 | 较慢 | 较快 |
| 内存 | 占用多 | 占用少 |
| 能否当字典key | 不能 | 能 |
| 方法数量 | 多 | 少（只有count和index） |

**什么时候用元组？**
- 数据不应该被修改时（保护数据）
- 需要作为字典的key时
- 函数返回多个值时（默认返回元组）

**我的笔记：**
> 

---

### 八、字典 dict 详解

#### 8.1 字典定义
字典是**键值对**的集合，**无序**（Python 3.7+有序），**key必须唯一且不可变**。
```python
# 空字典
d = {}
d = dict()

# 有数据的字典
d = {"name": "Tom", "age": 18, "gender": "男"}

# key可以是不同的不可变类型
d = {1: "one", "two": 2, (1,2): "tuple"}
```

#### 8.2 字典的特点
- key 必须是**不可变类型**（字符串、数字、元组）
- key **不能重复**，重复会覆盖
- value 可以是任意类型
- 查询速度非常快（O(1)）

#### 8.3 字典的增删改查

##### 查
```python
d = {"name": "Tom", "age": 18}

# 方式1：[] 取值（key不存在会报错）
d["name"]    # 'Tom'
# d["height"]  # ❌ KeyError

# 方式2：get() 取值（key不存在返回None或默认值）
d.get("age")       # 18
d.get("height")    # None（不报错）
d.get("height", 0) # 0（指定默认值）

# 方式3：setdefault() 取值（key不存在就添加）
d.setdefault("age", 20)   # 18（key存在，返回原值）
d.setdefault("height", 175) # 175（key不存在，添加并返回）
print(d)  # {'name': 'Tom', 'age': 18, 'height': 175}
```

##### 增/改
```python
d = {"name": "Tom"}

# key存在就是修改，不存在就是新增
d["age"] = 18     # 新增
d["name"] = "Jerry"  # 修改
print(d)  # {'name': 'Jerry', 'age': 18}

# update：批量添加/修改
d.update({"gender": "男", "age": 20})
print(d)  # {'name': 'Jerry', 'age': 20, 'gender': '男'}
```

##### 删
```python
d = {"name": "Tom", "age": 18, "gender": "男"}

# pop：删除指定key并返回value
d.pop("age")     # 18
print(d)         # {'name': 'Tom', 'gender': '男'}

# popitem：删除最后一个键值对并返回（Python 3.7+）
d.popitem()      # ('gender', '男')
print(d)         # {'name': 'Tom'}

# del：删除指定key
del d["name"]

# clear：清空字典
d.clear()
print(d)         # {}
```

#### 8.4 字典方法大全

##### 🔑 keys / values / items
```python
d = {"name": "Tom", "age": 18}

# 获取所有key
d.keys()    # dict_keys(['name', 'age'])
list(d.keys())  # ['name', 'age']

# 获取所有value
d.values()  # dict_values(['Tom', 18])

# 获取所有键值对
d.items()   # dict_items([('name', 'Tom'), ('age', 18)])
```

##### 📋 复制
```python
d = {"a": 1, "b": 2}

# copy：浅拷贝
d2 = d.copy()

# dict() 构造
d3 = dict(d)
```

##### 🔍 判断
```python
d = {"name": "Tom", "age": 18}

# 判断key是否存在
"name" in d        # True
"height" in d      # False

# 长度
len(d)             # 2
```

#### 8.5 字典遍历
```python
d = {"name": "Tom", "age": 18, "gender": "男"}

# 遍历key
for key in d:
    print(key, d[key])

# 遍历key（更明确）
for key in d.keys():
    print(key)

# 遍历value
for value in d.values():
    print(value)

# 遍历键值对（最常用）
for key, value in d.items():
    print(key, value)
```

#### 8.6 字典推导式
```python
# 基本格式：{key: value for 变量 in 可迭代对象}

# 字典推导式
squares = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# 带条件
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
# {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}

# 键值互换
d = {"a": 1, "b": 2, "c": 3}
new_d = {v: k for k, v in d.items()}
# {1: 'a', 2: 'b', 3: 'c'}

# 两个列表合成字典
keys = ["a", "b", "c"]
values = [1, 2, 3]
d = {k: v for k, v in zip(keys, values)}
# {'a': 1, 'b': 2, 'c': 3}
```

#### 8.7 其他创建字典的方式
```python
# 方式1：{}
d1 = {"name": "Tom", "age": 18}

# 方式2：dict() 关键字参数
d2 = dict(name="Tom", age=18)

# 方式3：dict() 二元组列表
d3 = dict([("name", "Tom"), ("age", 18)])

# 方式4：dict.fromkeys() 批量创建（value相同）
d4 = dict.fromkeys(["a", "b", "c"], 0)
# {'a': 0, 'b': 0, 'c': 0}

# 方式5：zip() 两个列表
keys = ["a", "b", "c"]
values = [1, 2, 3]
d5 = dict(zip(keys, values))
```

#### 8.8 嵌套字典
```python
# 字典套字典
students = {
    "001": {"name": "张三", "age": 18, "score": 90},
    "002": {"name": "李四", "age": 19, "score": 85},
    "003": {"name": "王五", "age": 18, "score": 95}
}

# 取值
students["001"]["name"]   # '张三'
students["002"]["score"]  # 85

# 遍历
for id, info in students.items():
    print(f"学号{id}：{info['name']}，{info['age']}岁")
```

**我的笔记：**
> 

---

### 九、集合 set 详解

#### 9.1 集合定义
集合是**无序、元素不重复**的容器，类似只有key没有value的字典。
```python
# 空集合（注意：不能用{}，那是空字典）
s = set()

# 有元素的集合
s = {1, 2, 3, 3, 3}
print(s)  # {1, 2, 3}（自动去重）

# 从列表创建（去重）
lst = [1, 2, 2, 3, 3, 3]
s = set(lst)  # {1, 2, 3}
```

#### 9.2 集合的特点
- 元素**不重复**（自动去重）
- **无序**（不能用索引访问）
- 元素必须是**不可变类型**
- 集合运算（交集、并集、差集等）非常方便

#### 9.3 集合的增删改查

##### 增
```python
s = {1, 2, 3}

# add：添加一个元素
s.add(4)
print(s)  # {1, 2, 3, 4}

# update：添加多个元素
s.update([5, 6, 7])
print(s)  # {1, 2, 3, 4, 5, 6, 7}
```

##### 删
```python
s = {1, 2, 3, 4, 5}

# remove：删除指定元素（不存在会报错）
s.remove(3)
print(s)  # {1, 2, 4, 5}

# discard：删除指定元素（不存在不报错）
s.discard(100)  # 不报错

# pop：随机删除一个元素并返回
s.pop()

# clear：清空集合
s.clear()
print(s)  # set()
```

##### 查
```python
s = {1, 2, 3}

# 判断元素是否存在
2 in s     # True
10 in s    # False

# 长度
len(s)     # 3

# 遍历
for item in s:
    print(item)
```

#### 9.4 集合运算

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

# 交集（两个集合都有的元素）
a & b              # {3, 4}
a.intersection(b)  # {3, 4}

# 并集（两个集合所有元素，去重）
a | b              # {1, 2, 3, 4, 5, 6}
a.union(b)         # {1, 2, 3, 4, 5, 6}

# 差集（a有b没有的元素）
a - b              # {1, 2}
a.difference(b)    # {1, 2}

# 对称差集（不同时在两个集合里的元素）
a ^ b              # {1, 2, 5, 6}
a.symmetric_difference(b)  # {1, 2, 5, 6}
```

#### 9.5 集合关系判断
```python
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}

# 子集：a的所有元素都在b里
a.issubset(b)   # True
a <= b          # True

# 真子集
a < b           # True

# 超集：b包含a的所有元素
b.issuperset(a) # True
b >= a          # True

# 真超集
b > a           # True

# 是否不相交（没有公共元素）
a = {1, 2}
b = {3, 4}
a.isdisjoint(b)  # True
```

#### 9.6 集合推导式
```python
# 基本格式：{表达式 for 变量 in 可迭代对象}

s = {x**2 for x in range(10)}
# {0, 1, 4, 9, 16, 25, 36, 49, 64, 81}

# 带条件
s = {x for x in range(20) if x % 3 == 0}
# {0, 3, 6, 9, 12, 15, 18}
```

#### 9.7 集合的典型应用场景
```python
# 1. 列表去重
lst = [1, 2, 2, 3, 3, 3]
unique_lst = list(set(lst))  # [1, 2, 3]（注意：顺序可能变）

# 2. 找共同元素
list1 = [1, 2, 3, 4]
list2 = [3, 4, 5, 6]
common = set(list1) & set(list2)  # {3, 4}

# 3. 找不同元素
diff = set(list1) - set(list2)  # {1, 2}
```

**我的笔记：**
> 

---

---

## 第三篇：运算符与流程控制

---

### 十、运算符大全

#### 10.1 算术运算符

| 运算符 | 说明 | 示例 | 结果 |
|--------|------|------|------|
| `+` | 加 | `5 + 3` | 8 |
| `-` | 减 | `5 - 3` | 2 |
| `*` | 乘 | `5 * 3` | 15 |
| `/` | 除（结果总是float） | `7 / 2` | 3.5 |
| `//` | 整除（向下取整） | `7 // 2` | 3 |
| `%` | 取模（余数） | `7 % 2` | 1 |
| `**` | 幂运算 | `2 ** 3` | 8 |

**⚠️ Python 取模规则：余数符号与除数一致**
```python
-10 % 3   # 2（除数3为正，结果为正）
10 % -3   # -2（除数-3为负，结果为负）
-7 // 3   # -3（向下取整，不是-2）
```

**公式：** `a % b = a - b * (a // b)`

#### 10.2 比较运算符

| 运算符 | 说明 | 示例 | 结果 |
|--------|------|------|------|
| `==` | 等于 | `5 == 5` | True |
| `!=` | 不等于 | `5 != 3` | True |
| `>` | 大于 | `5 > 3` | True |
| `<` | 小于 | `5 < 3` | False |
| `>=` | 大于等于 | `5 >= 5` | True |
| `<=` | 小于等于 | `5 <= 3` | False |

**连续比较（Python特有）：**
```python
x = 5
1 < x < 10    # True（等价于 1<x and x<10）
10 > x > 1    # True
```

#### 10.3 赋值运算符

| 运算符 | 说明 | 示例 | 等价于 |
|--------|------|------|--------|
| `=` | 简单赋值 | `a = 10` | |
| `+=` | 加后赋值 | `a += 5` | `a = a + 5` |
| `-=` | 减后赋值 | `a -= 5` | `a = a - 5` |
| `*=` | 乘后赋值 | `a *= 5` | `a = a * 5` |
| `/=` | 除后赋值 | `a /= 5` | `a = a / 5` |
| `//=` | 整除后赋值 | `a //= 5` | `a = a // 5` |
| `%=` | 取模后赋值 | `a %= 5` | `a = a % 5` |
| `**=` | 幂后赋值 | `a **= 2` | `a = a ** 2` |

#### 10.4 逻辑运算符

| 运算符 | 说明 | 示例 | 结果 |
|--------|------|------|------|
| `and` | 与（两边都True才True） | `True and False` | False |
| `or` | 或（一边True就True） | `True or False` | True |
| `not` | 非（取反） | `not True` | False |

**短路求值：**
```python
# and：左边为False，右边不执行
10 > 20 and print("不会执行")

# or：左边为True，右边不执行
10 < 20 or print("不会执行")
```

**返回值不是只有布尔值：**
```python
# and：返回第一个假值，都真返回最后一个
3 and 0 and 5     # 0
3 and 4 and 5     # 5

# or：返回第一个真值，都假返回最后一个
0 or "" or 5      # 5
0 or "" or []     # []
```

#### 10.5 成员运算符

| 运算符 | 说明 | 示例 | 结果 |
|--------|------|------|------|
| `in` | 元素在序列中 | `'a' in 'abc'` | True |
| `not in` | 元素不在序列中 | `'d' not in 'abc'` | True |

```python
# 字符串
"P" in "Python"     # True

# 列表
3 in [1,2,3]        # True

# 字典（判断的是key）
"name" in {"name": "Tom"}  # True
"Tom" in {"name": "Tom"}   # False（判断的是key不是value）
```

#### 10.6 身份运算符

| 运算符 | 说明 |
|--------|------|
| `is` | 是否同一对象（id相同） |
| `is not` | 是否不同对象 |

```python
a = 2
b = 2
a is b     # True（小整数池，同一个对象）
a == b     # True（值相等）

a = [1, 2, 3]
b = [1, 2, 3]
a == b     # True（值相等）
a is b     # False（不是同一个对象，id不同）
```

**`==` 和 `is` 的区别：**
- `==`：比较**值**是否相等
- `is`：比较**身份（内存地址）**是否相同，即是否同一个对象

#### 10.7 位运算符（了解）

| 运算符 | 说明 | 示例 |
|--------|------|------|
| `&` | 按位与 | `5 & 3` → 1 |
| `\|` | 按位或 | `5 \| 3` → 7 |
| `^` | 按位异或 | `5 ^ 3` → 6 |
| `~` | 按位取反 | `~5` → -6 |
| `<<` | 左移 | `5 << 1` → 10 |
| `>>` | 右移 | `5 >> 1` → 2 |

#### 10.8 运算符优先级
从高到低（不用死记，不确定就加括号）：
1. `()` 括号
2. `**` 幂运算
3. `~` 按位取反
4. `*` `/` `//` `%`
5. `+` `-`
6. `<<` `>>` 位移
7. `&`
8. `^` `|`
9. `==` `!=` `>` `<` `>=` `<=`
10. `=` `+=` 等赋值
11. `is` `is not`
12. `in` `not in`
13. `not`
14. `and`
15. `or`

**我的笔记：**
> 

---

### 十一、条件判断 if/elif/else

#### 11.1 基本 if 语句
```python
age = 18
if age >= 18:
    print("成年了")
```

#### 11.2 if-else 语句
```python
age = 16
if age >= 18:
    print("成年了")
else:
    print("未成年")
```

#### 11.3 if-elif-else 多分支
```python
score = 85

if score >= 90:
    print("优秀")
elif score >= 80:
    print("良好")
elif score >= 60:
    print("及格")
else:
    print("不及格")
```

#### 11.4 嵌套 if
```python
age = 20
has_id = True

if age >= 18:
    if has_id:
        print("可以进入")
    else:
        print("请出示身份证")
else:
    print("未成年禁止入内")
```

#### 11.5 三元表达式（一行if-else）
```python
# 格式：值1 if 条件 else 值2

age = 18
status = "成年" if age >= 18 else "未成年"
print(status)  # '成年'

# 等价于
if age >= 18:
    status = "成年"
else:
    status = "未成年"
```

#### 11.6 常见判断条件
```python
# 判断空
if not s:       # 空字符串、空列表等为False
    print("空")

# 判断None
if x is None:   # 用is，不要用==
    print("是None")

# 判断数字
if x > 0:
    print("正数")

# 判断字符串包含
if "abc" in s:
    print("包含abc")
```

**我的笔记：**
> 

---

### 十二、循环 for/while

#### 12.1 for 循环
用于遍历可迭代对象（列表、字符串、字典、range等）。

```python
# 遍历列表
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(fruit)

# 遍历字符串
for char in "Python":
    print(char)

# 带索引遍历
for i, fruit in enumerate(fruits):
    print(i, fruit)
```

#### 12.2 range() 函数
生成整数序列，常用于循环次数。

```python
# range(n)：0到n-1
for i in range(5):
    print(i)  # 0,1,2,3,4

# range(start, end)：start到end-1
for i in range(2, 6):
    print(i)  # 2,3,4,5

# range(start, end, step)：指定步长
for i in range(0, 10, 2):
    print(i)  # 0,2,4,6,8

# 倒序
for i in range(5, 0, -1):
    print(i)  # 5,4,3,2,1
```

#### 12.3 while 循环
条件为True就一直循环。

```python
# 打印1-5
count = 1
while count <= 5:
    print(count)
    count += 1
```

#### 12.4 while True 无限循环
```python
while True:
    answer = input("输入q退出：")
    if answer == "q":
        break
    print("你输入了：", answer)
```

#### 12.5 循环中的 else
循环正常结束（不是被break打断）时执行：
```python
# for循环的else
for i in range(5):
    if i == 10:
        break
else:
    print("循环正常结束了")  # 会执行

# while循环的else
n = 0
while n < 5:
    n += 1
else:
    print("while正常结束")
```

#### 12.6 嵌套循环
```python
# 打印九九乘法表
for i in range(1, 10):
    for j in range(1, i+1):
        print(f"{j}×{i}={i*j}", end="\t")
    print()  # 换行
```

**我的笔记：**
> 

---

### 十三、break/continue/pass

#### 13.1 break：跳出整个循环
```python
# 找到第一个偶数就停止
for i in range(1, 10):
    if i % 2 == 0:
        print("找到第一个偶数：", i)
        break
```

#### 13.2 continue：跳过本次循环，继续下一次
```python
# 打印1-10中的奇数
for i in range(1, 11):
    if i % 2 == 0:
        continue  # 偶数跳过
    print(i)
```

#### 13.3 pass：空语句，占位用
什么都不做，只是为了语法不报错：
```python
if True:
    pass  # 还没想好写什么，先占个位置

def func():
    pass  # 函数还没实现，先占位

class MyClass:
    pass  # 类还没实现，先占位
```

#### 13.4 对比总结

| 关键字 | 作用 |
|--------|------|
| `break` | 跳出**整个**循环，不再执行 |
| `continue` | 跳过**本次**循环，继续下一次 |
| `pass` | 什么都不做，占位符 |

**我的笔记：**
> 

---

---

## 第四篇：函数与模块

---

### 十四、函数详解

#### 14.1 什么是函数
函数就是**一段可重复使用的代码块**，给它起个名字，用的时候调用就行。

#### 14.2 定义函数
```python
def 函数名(参数1, 参数2, ...):
    """函数文档字符串（说明函数用途）"""
    函数体
    return 返回值
```

```python
# 示例：打招呼函数
def greet(name):
    """向指定的人打招呼"""
    print(f"Hello, {name}!")

# 调用函数
greet("Tom")
greet("Jerry")
```

#### 14.3 函数的返回值 return
```python
# 有返回值的函数
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # 8

# 返回多个值（本质是返回元组）
def calc(a, b):
    return a+b, a-b, a*b

sum_val, diff, product = calc(10, 5)
print(sum_val, diff, product)  # 15 5 50

# 没有return的函数，默认返回None
def say_hi():
    print("hi")

result = say_hi()
print(result)  # None
```

#### 14.4 函数参数

##### 位置参数
按顺序传递：
```python
def info(name, age):
    print(f"{name}，{age}岁")

info("Tom", 18)  # 按位置传
```

##### 关键字参数
按参数名传递，顺序可以任意：
```python
info(age=18, name="Tom")  # 按名字传，顺序无所谓
```

##### 默认参数
参数有默认值，调用时可以不传：
```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Tom")          # Hello, Tom!（用默认值）
greet("Tom", "Hi")    # Hi, Tom!（传了就用传的）
```

**⚠️ 注意：默认参数必须放在位置参数后面**
```python
# ✅ 正确
def func(a, b=10, c=20):
    pass

# ❌ 错误
# def func(a=10, b):
#     pass
```

**⚠️ 默认参数不要用可变对象（坑！）**
```python
# ❌ 错误写法
def add_item(item, lst=[]):
    lst.append(item)
    return lst

print(add_item(1))  # [1]
print(add_item(2))  # [1, 2]（不是[2]！因为默认列表被复用了）
print(add_item(3))  # [1, 2, 3]

# ✅ 正确写法
def add_item(item, lst=None):
    if lst is None:
        lst = []
    lst.append(item)
    return lst
```

##### 可变参数 *args
接收任意数量的位置参数，变成**元组**：
```python
def sum_all(*args):
    print(args)  # 是个元组
    return sum(args)

print(sum_all(1, 2, 3))       # 6
print(sum_all(1, 2, 3, 4, 5)) # 15
```

##### 关键字可变参数 **kwargs
接收任意数量的关键字参数，变成**字典**：
```python
def print_info(**kwargs):
    print(kwargs)  # 是个字典
    for k, v in kwargs.items():
        print(f"{k}: {v}")

print_info(name="Tom", age=18, gender="男")
```

##### 参数组合顺序
参数定义的顺序必须是：
1. 位置参数
2. 默认参数
3. *args
4. 命名关键字参数
5. **kwargs

```python
def func(a, b, c=0, *args, d=10, **kwargs):
    print(a, b, c, args, d, kwargs)
```

#### 14.5 解包传参
```python
# * 解包列表/元组，变成位置参数
def add(a, b, c):
    return a + b + c

nums = [1, 2, 3]
print(add(*nums))  # 等价于 add(1, 2, 3)

# ** 解包字典，变成关键字参数
info = {"name": "Tom", "age": 18}
def print_info(name, age):
    print(name, age)

print_info(**info)  # 等价于 print_info(name="Tom", age=18)
```

#### 14.6 匿名函数 lambda
一行的小函数，适合简单逻辑：
```python
# 格式：lambda 参数: 返回值

# 普通函数
def add(a, b):
    return a + b

# 等价 lambda
add = lambda a, b: a + b

print(add(3, 5))  # 8
```

**常用场景：作为 sorted、max、min 等的 key 参数**
```python
# 按第二个元素排序
pairs = [(1, 3), (2, 1), (3, 2)]
pairs.sort(key=lambda x: x[1])
print(pairs)  # [(2, 1), (3, 2), (1, 3)]

# 按value找最大的key
d = {"a": 3, "b": 1, "c": 2}
max_key = max(d, key=lambda k: d[k])
print(max_key)  # 'a'
```

#### 14.7 作用域
```python
# 全局变量
x = 100

def func():
    # 局部变量
    x = 200
    print("函数内：", x)  # 200

func()
print("函数外：", x)  # 100
```

**global 关键字：在函数内修改全局变量**
```python
x = 100

def func():
    global x  # 声明x是全局变量
    x = 200

func()
print(x)  # 200
```

**nonlocal 关键字：修改外层嵌套函数的变量**
```python
def outer():
    x = 100
    def inner():
        nonlocal x  # 声明x是外层函数的变量
        x = 200
    inner()
    print(x)  # 200

outer()
```

#### 14.8 递归函数
函数自己调用自己：
```python
# 阶乘
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n-1)

print(factorial(5))  # 120

# 斐波那契数列
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)

print(fib(10))  # 55
```

**递归三要素：**
1. 明确函数要做什么
2. 找到递归结束条件（base case）
3. 找到递归关系式（怎么把大问题拆成小问题）

#### 14.9 高阶函数
接收函数作为参数，或者返回函数的函数。

```python
# map：对每个元素做处理
nums = [1, 2, 3, 4, 5]
result = map(lambda x: x**2, nums)
print(list(result))  # [1, 4, 9, 16, 25]

# filter：筛选满足条件的元素
result = filter(lambda x: x % 2 == 0, nums)
print(list(result))  # [2, 4]

# reduce：累积运算（需要导入）
from functools import reduce
result = reduce(lambda a, b: a + b, nums)
print(result)  # 15
```

#### 14.10 闭包
内层函数引用外层函数的变量，外层函数返回内层函数：
```python
def outer(x):
    def inner(y):
        return x + y
    return inner

add5 = outer(5)
print(add5(3))   # 8
print(add5(10))  # 15
```

**我的笔记：**
> 

---

### 十五、模块与包

#### 15.1 什么是模块
一个 `.py` 文件就是一个模块，里面可以定义函数、类、变量。

#### 15.2 导入模块

```python
# 方式1：导入整个模块
import math
print(math.sqrt(16))  # 4.0

# 方式2：导入模块的指定内容
from math import sqrt, pi
print(sqrt(16))  # 4.0
print(pi)        # 3.14159...

# 方式3：导入所有内容（不推荐，容易命名冲突）
from math import *

# 方式4：给模块起别名
import math as m
print(m.sqrt(16))  # 4.0

# 方式5：给导入的内容起别名
from math import sqrt as square_root
print(square_root(16))  # 4.0
```

#### 15.3 自定义模块
创建 `my_module.py`：
```python
# my_module.py
name = "我的模块"

def add(a, b):
    return a + b

def say_hello():
    print("Hello from my_module!")
```

在另一个文件中使用：
```python
import my_module

print(my_module.name)
my_module.say_hello()
print(my_module.add(3, 5))
```

#### 15.4 `__name__ == "__main__"` 的作用
```python
# my_module.py
def add(a, b):
    return a + b

# 只有直接运行这个文件时才执行下面的代码
# 被其他文件import时不执行
if __name__ == "__main__":
    print("测试代码")
    print(add(3, 5))
```

#### 15.5 什么是包（Package）
包含多个模块的文件夹，必须有 `__init__.py` 文件（可以是空的）。

```
my_package/
    __init__.py
    module1.py
    module2.py
```

**导入包中的模块：**
```python
from my_package import module1
from my_package.module2 import func
```

#### 15.6 常用标准库

| 模块 | 用途 |
|------|------|
| `math` | 数学运算 |
| `random` | 随机数 |
| `time` | 时间相关 |
| `datetime` | 日期时间 |
| `os` | 操作系统接口 |
| `sys` | 系统相关 |
| `json` | JSON 处理 |
| `re` | 正则表达式 |
| `collections` | 扩展数据类型 |
| `itertools` | 迭代器工具 |
| `functools` | 函数工具 |
| `pathlib` | 路径处理 |

#### 15.7 random 模块常用
```python
import random

# 随机整数（包含两端）
random.randint(1, 10)   # 1到10之间的随机整数

# 随机浮点数（0到1之间）
random.random()          # 0.0到1.0之间

# 随机浮点数（指定范围）
random.uniform(1, 10)    # 1到10之间的随机小数

# 从序列中随机选一个
random.choice(["a", "b", "c"])

# 从序列中随机选多个（不重复）
random.sample([1,2,3,4,5], 3)  # 随机选3个

# 打乱列表顺序（原地打乱）
lst = [1, 2, 3, 4, 5]
random.shuffle(lst)
```

#### 15.8 time 模块常用
```python
import time

# 当前时间戳（秒）
time.time()

# 休眠n秒
time.sleep(1)  # 暂停1秒

# 格式化时间
time.strftime("%Y-%m-%d %H:%M:%S")
```

**我的笔记：**
> 

---

---

## 第五篇：进阶内容

---

### 十六、文件操作

#### 16.1 打开文件 open()
```python
# 基本格式
f = open("文件路径", "打开模式", encoding="utf-8")
# 操作文件
f.close()  # 一定要关闭！
```

**打开模式：**

| 模式 | 说明 |
|------|------|
| `r` | 只读（默认），文件不存在报错 |
| `w` | 只写，文件不存在就创建，存在就覆盖 |
| `a` | 追加，文件不存在就创建，存在就追加到末尾 |
| `r+` | 读写，文件不存在报错 |
| `w+` | 读写，文件不存在就创建，存在就覆盖 |
| `a+` | 读写追加 |
| `rb` | 二进制只读 |
| `wb` | 二进制只写 |
| `ab` | 二进制追加 |

#### 16.2 with 语句（推荐）
自动关闭文件，不用手动 `close()`：
```python
with open("test.txt", "r", encoding="utf-8") as f:
    content = f.read()
    print(content)
# 离开with块自动关闭文件
```

#### 16.3 读取文件
```python
with open("test.txt", "r", encoding="utf-8") as f:
    # 读取全部内容
    content = f.read()
    
    # 读取一行
    line = f.readline()
    
    # 读取所有行，返回列表
    lines = f.readlines()
```

**逐行读取（大文件推荐，省内存）：**
```python
with open("test.txt", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip())  # strip去掉换行符
```

#### 16.4 写入文件
```python
# 覆盖写入
with open("test.txt", "w", encoding="utf-8") as f:
    f.write("Hello World\n")
    f.write("第二行\n")
    
    # 写入多行
    lines = ["第一行\n", "第二行\n", "第三行\n"]
    f.writelines(lines)

# 追加写入
with open("test.txt", "a", encoding="utf-8") as f:
    f.write("追加的内容\n")
```

#### 16.5 文件指针
```python
with open("test.txt", "r", encoding="utf-8") as f:
    # 当前指针位置
    print(f.tell())
    
    # 移动指针：offset偏移量，whence起始位置（0=开头，1=当前，2=末尾）
    f.seek(5)  # 移动到第5个字节处
    print(f.read())
```

#### 16.6 os 模块操作文件和目录
```python
import os

# 获取当前工作目录
os.getcwd()

# 切换目录
os.chdir("/path/to/dir")

# 列出目录内容
os.listdir(".")

# 创建目录
os.mkdir("test_dir")       # 创建单级目录
os.makedirs("a/b/c")       # 创建多级目录

# 删除文件
os.remove("test.txt")

# 删除空目录
os.rmdir("test_dir")

# 重命名文件/目录
os.rename("old.txt", "new.txt")

# 判断是否存在
os.path.exists("test.txt")

# 判断是否是文件
os.path.isfile("test.txt")

# 判断是否是目录
os.path.isdir("test_dir")

# 获取文件大小（字节）
os.path.getsize("test.txt")

# 路径拼接
os.path.join("a", "b", "c.txt")  # 'a/b/c.txt'

# 获取文件名
os.path.basename("/a/b/c.txt")   # 'c.txt'

# 获取目录名
os.path.dirname("/a/b/c.txt")    # '/a/b'

# 分割文件名和扩展名
os.path.splitext("c.txt")        # ('c', '.txt')
```

#### 16.7 pathlib 模块（面向对象的路径处理，推荐）
```python
from pathlib import Path

# 创建路径对象
p = Path(".")

# 路径拼接
p = Path("a") / "b" / "c.txt"

# 判断
p.exists()
p.is_file()
p.is_dir()

# 获取文件名
p.name          # 'c.txt'
p.stem          # 'c'（不含扩展名）
p.suffix        # '.txt'

# 父目录
p.parent        # 'a/b'

# 遍历目录
for item in Path(".").iterdir():
    print(item)

# 递归遍历
for item in Path(".").rglob("*.py"):
    print(item)

# 读取文件
content = Path("test.txt").read_text(encoding="utf-8")

# 写入文件
Path("test.txt").write_text("Hello", encoding="utf-8")

# 创建目录
Path("a/b/c").mkdir(parents=True, exist_ok=True)
```

**我的笔记：**
> 

---

### 十七、异常处理

#### 17.1 什么是异常
程序运行时出错，就会抛出异常。如果不处理，程序就会崩溃。

```python
# 例子：除零错误
print(10 / 0)  # ZeroDivisionError: division by zero
```

#### 17.2 try-except 捕获异常
```python
try:
    # 可能出错的代码
    result = 10 / 0
except ZeroDivisionError:
    # 出错了怎么办
    print("除数不能为零！")
```

#### 17.3 捕获多个异常
```python
try:
    num = int(input("请输入数字："))
    result = 10 / num
    print(result)
except ValueError:
    print("输入的不是数字！")
except ZeroDivisionError:
    print("不能输入0！")
except:
    print("其他错误")
```

#### 17.4 获取异常信息
```python
try:
    10 / 0
except ZeroDivisionError as e:
    print(f"出错了：{e}")
```

#### 17.5 try-except-else
没有异常时执行 else：
```python
try:
    result = 10 / 2
except ZeroDivisionError:
    print("出错了")
else:
    print("没有出错，结果是：", result)
```

#### 17.6 try-except-finally
不管有没有异常，finally 都会执行：
```python
try:
    f = open("test.txt", "r")
    content = f.read()
except FileNotFoundError:
    print("文件不存在")
finally:
    f.close()  # 不管有没有异常，都关闭文件
```

#### 17.7 主动抛出异常 raise
```python
def divide(a, b):
    if b == 0:
        raise ValueError("除数不能为零")  # 主动抛出异常
    return a / b

try:
    divide(10, 0)
except ValueError as e:
    print(e)
```

#### 17.8 自定义异常
```python
class MyError(Exception):
    """自定义异常类"""
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

# 使用
try:
    raise MyError("这是自定义异常")
except MyError as e:
    print(e)
```

#### 17.9 常见异常类型

| 异常类型 | 说明 |
|----------|------|
| `SyntaxError` | 语法错误 |
| `IndentationError` | 缩进错误 |
| `NameError` | 变量未定义 |
| `TypeError` | 类型错误 |
| `ValueError` | 值错误 |
| `IndexError` | 索引越界 |
| `KeyError` | 字典key不存在 |
| `AttributeError` | 属性不存在 |
| `ZeroDivisionError` | 除零错误 |
| `FileNotFoundError` | 文件不存在 |
| `IOError` | IO错误 |
| `ImportError` | 导入错误 |

**我的笔记：**
> 

---

### 十八、面向对象编程

#### 18.1 什么是面向对象
- 面向过程：一步步做，关注怎么做
- 面向对象：找对象，关注谁来做

#### 18.2 类和对象
- **类（Class）**：模板，比如「人类」
- **对象（Object/Instance）**：根据模板创建的具体实例，比如「张三」

#### 18.3 定义类
```python
class 类名:
    """类的文档字符串"""
    
    # 构造方法，创建对象时自动调用
    def __init__(self, 参数1, 参数2, ...):
        self.属性1 = 参数1
        self.属性2 = 参数2
    
    # 方法
    def 方法名(self, 参数1, ...):
        方法体
```

```python
# 示例：定义一个人类
class Person:
    """人类"""
    
    def __init__(self, name, age):
        # 属性
        self.name = name
        self.age = age
    
    # 方法
    def say_hello(self):
        print(f"大家好，我叫{self.name}，今年{self.age}岁")
    
    def grow_up(self, years=1):
        self.age += years
        print(f"{self.name}长大了{years}岁，现在{self.age}岁")
```

#### 18.4 创建对象
```python
# 创建对象
p1 = Person("张三", 18)
p2 = Person("李四", 20)

# 访问属性
print(p1.name)  # 张三
print(p2.age)   # 20

# 调用方法
p1.say_hello()  # 大家好，我叫张三，今年18岁
p1.grow_up()    # 张三长大了1岁，现在19岁
```

#### 18.5 self 是什么
- `self` 就是对象本身
- 类的方法第一个参数必须是 `self`
- 调用方法时不用传 `self`，Python 自动传

#### 18.6 属性访问

##### 实例属性
每个对象自己的属性，各不相同：
```python
p1 = Person("张三", 18)
p2 = Person("李四", 20)
# p1.name 和 p2.name 不一样
```

##### 类属性
所有对象共享的属性，定义在类里面，方法外面：
```python
class Person:
    # 类属性
    species = "人类"
    
    def __init__(self, name):
        self.name = name  # 实例属性

p1 = Person("张三")
p2 = Person("李四")

print(p1.species)  # 人类
print(p2.species)  # 人类（共享同一个）
print(Person.species)  # 人类
```

#### 18.7 方法类型

##### 实例方法
最常用，第一个参数是 `self`，访问实例属性：
```python
class Person:
    def __init__(self, name):
        self.name = name
    
    def say_hello(self):  # 实例方法
        print(f"我是{self.name}")
```

##### 类方法
用 `@classmethod` 装饰，第一个参数是 `cls`（类本身），访问类属性：
```python
class Person:
    species = "人类"
    
    @classmethod
    def get_species(cls):
        return cls.species

print(Person.get_species())  # 人类
```

##### 静态方法
用 `@staticmethod` 装饰，不需要 `self` 或 `cls`，和类关系不大：
```python
class Calculator:
    @staticmethod
    def add(a, b):
        return a + b

print(Calculator.add(3, 5))  # 8
```

#### 18.8 继承
子类继承父类的属性和方法，还可以扩展。

```python
# 父类（基类）
class Animal:
    def __init__(self, name):
        self.name = name
    
    def eat(self):
        print(f"{self.name}在吃东西")

# 子类（派生类）继承Animal
class Dog(Animal):
    def bark(self):
        print(f"{self.name}在汪汪叫")

# 使用
dog = Dog("旺财")
dog.eat()    # 旺财在吃东西（继承来的方法）
dog.bark()   # 旺财在汪汪叫（自己的方法）
```

#### 18.9 方法重写
子类可以重写父类的方法：
```python
class Animal:
    def speak(self):
        print("动物叫")

class Dog(Animal):
    def speak(self):  # 重写父类方法
        print("汪汪汪")

class Cat(Animal):
    def speak(self):  # 重写父类方法
        print("喵喵喵")

Dog().speak()  # 汪汪汪
Cat().speak()  # 喵喵喵
```

#### 18.10 super() 调用父类方法
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def say_hello(self):
        print(f"我叫{self.name}，{self.age}岁")

class Student(Person):
    def __init__(self, name, age, grade):
        # 调用父类的__init__
        super().__init__(name, age)
        self.grade = grade
    
    def say_hello(self):
        # 调用父类的say_hello
        super().say_hello()
        print(f"我上{self.grade}年级")

s = Student("小明", 10, 4)
s.say_hello()
```

#### 18.11 多继承
一个类可以继承多个父类：
```python
class A:
    def method_a(self):
        print("A的方法")

class B:
    def method_b(self):
        print("B的方法")

class C(A, B):  # 同时继承A和B
    pass

c = C()
c.method_a()  # A的方法
c.method_b()  # B的方法
```

#### 18.12 私有属性和方法
Python 没有真正的私有，用下划线开头表示约定俗成的私有：
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self._age = age       # 单下划线：约定私有，外部尽量不要直接访问
        self.__password = "123456"  # 双下划线：名称修饰，外部不能直接访问
    
    def get_age(self):
        return self._age

p = Person("张三", 18)
print(p._age)          # 18（能访问，但不建议）
# print(p.__password)  # 报错，访问不到
print(p._Person__password)  # 其实可以这样访问（名称修饰）
```

#### 18.13 魔术方法（特殊方法）
前后都有双下划线的方法，有特殊含义。

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    # __str__：print时显示的内容
    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"
    
    # __repr__：调试时显示的内容
    def __repr__(self):
        return f"Person('{self.name}', {self.age})"
    
    # __len__：len()时调用
    def __len__(self):
        return self.age
    
    # __eq__：== 比较时调用
    def __eq__(self, other):
        return self.name == other.name and self.age == other.age
    
    # __add__：+ 运算时调用
    def __add__(self, other):
        return Person(self.name + other.name, self.age + other.age)

p = Person("张三", 18)
print(p)              # Person(name=张三, age=18)
print(len(p))         # 18
print(p == Person("张三", 18))  # True
```

#### 18.14 @property 装饰器
把方法变成属性一样调用：
```python
class Person:
    def __init__(self, name, birth_year):
        self.name = name
        self.birth_year = birth_year
    
    @property
    def age(self):
        return 2024 - self.birth_year

p = Person("张三", 2000)
print(p.age)  # 24（像属性一样访问，不用加括号）
```

**我的笔记：**
> 

---

### 十九、迭代器与生成器

#### 19.1 可迭代对象
可以用 `for` 循环遍历的都是可迭代对象，如列表、字符串、字典等。

```python
# 判断是否可迭代
from collections.abc import Iterable

isinstance([1,2,3], Iterable)  # True
isinstance("abc", Iterable)    # True
isinstance(123, Iterable)      # False
```

#### 19.2 迭代器
有 `__next__()` 方法的对象，能一个个取数据。

```python
lst = [1, 2, 3]

# iter() 获取迭代器
it = iter(lst)

# next() 取下一个值
print(next(it))  # 1
print(next(it))  # 2
print(next(it))  # 3
# print(next(it))  # StopIteration（取完了）
```

#### 19.3 生成器
一种特殊的迭代器，用 `yield` 关键字，惰性计算，省内存。

```python
# 生成器函数
def countdown(n):
    while n > 0:
        yield n  # 遇到yield暂停，返回值，下次继续
        n -= 1

# 创建生成器对象
gen = countdown(5)

print(next(gen))  # 5
print(next(gen))  # 4
print(next(gen))  # 3

# 也可以用for遍历
for num in countdown(5):
    print(num)
```

#### 19.4 生成器表达式
类似列表推导式，用 `()` 而不是 `[]`：
```python
# 列表推导式（一次性生成所有，占内存）
lst = [x**2 for x in range(10)]

# 生成器表达式（惰性计算，省内存）
gen = (x**2 for x in range(10))

print(next(gen))  # 0
print(next(gen))  # 1
```

**什么时候用生成器？**
- 数据量很大，不想一次性全加载到内存
- 只需要遍历一次
- 无限序列

**我的笔记：**
> 

---

### 二十、装饰器

#### 20.1 什么是装饰器
在不修改原函数代码的情况下，给函数增加新功能。

#### 20.2 简单装饰器
```python
import time

# 装饰器函数
def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} 执行耗时：{end-start:.4f}秒")
        return result
    return wrapper

# 使用装饰器
@timer
def slow_func():
    time.sleep(1)
    print("函数执行完了")

slow_func()
# 等价于：slow_func = timer(slow_func)
```

#### 20.3 带参数的装饰器
```python
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def say_hello():
    print("Hello!")

say_hello()  # 打印3次Hello!
```

#### 20.4 多个装饰器
```python
def decorator1(func):
    def wrapper():
        print("装饰器1开始")
        func()
        print("装饰器1结束")
    return wrapper

def decorator2(func):
    def wrapper():
        print("装饰器2开始")
        func()
        print("装饰器2结束")
    return wrapper

@decorator1
@decorator2
def func():
    print("原函数")

func()
# 输出：
# 装饰器1开始
# 装饰器2开始
# 原函数
# 装饰器2结束
# 装饰器1结束
```

**我的笔记：**
> 

---

---

## 第六篇：实用工具

---

### 二十一、Python 内置函数大全

### 数学相关
| 函数 | 说明 | 示例 | 结果 |
|------|------|------|------|
| `abs(x)` | 绝对值 | `abs(-10)` | 10 |
| `round(x, n)` | 四舍五入 | `round(3.14159, 2)` | 3.14 |
| `max(...)` | 最大值 | `max(3, 1, 4)` | 4 |
| `min(...)` | 最小值 | `min(3, 1, 4)` | 1 |
| `sum(iterable)` | 求和 | `sum([1,2,3])` | 6 |
| `pow(a, b)` | 幂运算 | `pow(2, 3)` | 8 |
| `divmod(a, b)` | 商和余数 | `divmod(7, 3)` | (2, 1) |

### 类型转换
| 函数 | 说明 |
|------|------|
| `int(x)` | 转整数 |
| `float(x)` | 转浮点数 |
| `str(x)` | 转字符串 |
| `bool(x)` | 转布尔值 |
| `list(x)` | 转列表 |
| `tuple(x)` | 转元组 |
| `dict(x)` | 转字典 |
| `set(x)` | 转集合 |
| `bytes(x)` | 转字节 |
| `chr(x)` | 数字转字符 |
| `ord(x)` | 字符转数字 |
| `bin(x)` | 转二进制字符串 |
| `oct(x)` | 转八进制字符串 |
| `hex(x)` | 转十六进制字符串 |

### 序列相关
| 函数 | 说明 |
|------|------|
| `len(x)` | 长度 |
| `sorted(iterable)` | 排序（返回新列表） |
| `reversed(seq)` | 反转（返回迭代器） |
| `enumerate(iterable)` | 带索引遍历 |
| `zip(*iterables)` | 打包多个序列 |
| `range(start, stop, step)` | 生成整数序列 |
| `iter(iterable)` | 获取迭代器 |
| `next(iterator)` | 取下一个值 |

### 对象相关
| 函数 | 说明 |
|------|------|
| `type(x)` | 查看类型 |
| `isinstance(x, type)` | 判断类型 |
| `id(x)` | 查看内存地址 |
| `hasattr(obj, name)` | 是否有属性 |
| `getattr(obj, name)` | 获取属性 |
| `setattr(obj, name, value)` | 设置属性 |
| `delattr(obj, name)` | 删除属性 |
| `dir(obj)` | 列出所有属性和方法 |

### 输入输出
| 函数 | 说明 |
|------|------|
| `print(...)` | 打印输出 |
| `input(prompt)` | 输入 |
| `open(file, mode)` | 打开文件 |

### 其他常用
| 函数 | 说明 |
|------|------|
| `help(obj)` | 查看帮助 |
| `eval(expr)` | 执行字符串表达式 |
| `exec(code)` | 执行字符串代码 |
| `map(func, iterable)` | 映射 |
| `filter(func, iterable)` | 过滤 |
| `reduce(func, iterable)` | 归约（functools） |
| `lambda` | 匿名函数 |
| `all(iterable)` | 所有都为True才True |
| `any(iterable)` | 有一个为True就True |
| `callable(obj)` | 是否可调用 |
| `hash(obj)` | 哈希值 |
| `globals()` | 全局变量字典 |
| `locals()` | 局部变量字典 |

**我的笔记：**
> 

---

### 二十二、字符串方法大全

### 查找与判断
- `find(sub)` → 查找子串，找不到返回-1
- `rfind(sub)` → 从右边找
- `index(sub)` → 查找子串，找不到报错
- `rindex(sub)` → 从右边找
- `count(sub)` → 统计出现次数
- `startswith(prefix)` → 是否以...开头
- `endswith(suffix)` → 是否以...结尾
- `isalpha()` → 是否全是字母
- `isdigit()` → 是否全是数字
- `isalnum()` → 是否全是字母或数字
- `isspace()` → 是否全是空白
- `isupper()` → 是否全大写
- `islower()` → 是否全小写
- `istitle()` → 是否每个单词首字母大写
- `isdecimal()` → 是否全是十进制数字
- `isnumeric()` → 是否全是数字字符

### 大小写转换
- `upper()` → 全大写
- `lower()` → 全小写
- `swapcase()` → 大小写互换
- `title()` → 每个单词首字母大写
- `capitalize()` → 首字母大写，其余小写
- `casefold()` → 更彻底的小写转换

### 去除空白
- `strip(chars)` → 去掉两边空白/指定字符
- `lstrip(chars)` → 去掉左边
- `rstrip(chars)` → 去掉右边

### 分割与拼接
- `split(sep, maxsplit)` → 分割成列表
- `rsplit(sep, maxsplit)` → 从右边分割
- `splitlines(keepends)` → 按行分割
- `partition(sep)` → 分成三部分
- `rpartition(sep)` → 从右边分
- `join(iterable)` → 用字符串连接序列

### 替换
- `replace(old, new, count)` → 替换
- `translate(table)` → 按转换表替换
- `maketrans(x, y, z)` → 创建转换表

### 对齐填充
- `center(width, fillchar)` → 居中
- `ljust(width, fillchar)` → 左对齐
- `rjust(width, fillchar)` → 右对齐
- `zfill(width)` → 左边补0

### 编码
- `encode(encoding)` → 转字节
- `expandtabs(tabsize)` → 制表符转空格

### 格式化
- `format(*args, **kwargs)` → 格式化
- `format_map(mapping)` → 用字典格式化

**我的笔记：**
> 

---

### 二十三、列表方法大全

### 添加元素
- `append(item)` → 末尾添加一个
- `extend(iterable)` → 末尾添加多个
- `insert(index, item)` → 指定位置插入

### 删除元素
- `pop(index)` → 删除并返回指定位置（默认最后）
- `remove(item)` → 删除第一个匹配的元素
- `clear()` → 清空

### 查找与统计
- `index(item, start, end)` → 查找元素索引
- `count(item)` → 统计出现次数

### 排序与反转
- `sort(key, reverse)` → 原地排序
- `reverse()` → 原地反转

### 复制
- `copy()` → 浅拷贝

### 其他
- `len(lst)` → 长度（内置函数）
- `sorted(lst)` → 排序返回新列表（内置函数）
- `reversed(lst)` → 反转返回迭代器（内置函数）

**我的笔记：**
> 

---

### 二十四、字典方法大全

### 获取
- `get(key, default)` → 获取value，key不存在返回默认值
- `setdefault(key, default)` → 获取，不存在就添加

### 添加/修改
- `update(dict)` → 批量添加/修改

### 删除
- `pop(key, default)` → 删除指定key并返回value
- `popitem()` → 删除最后一个键值对
- `clear()` → 清空

### 遍历
- `keys()` → 所有key
- `values()` → 所有value
- `items()` → 所有键值对

### 复制
- `copy()` → 浅拷贝

### 其他
- `fromkeys(seq, value)` → 从序列创建字典（类方法）

**我的笔记：**
> 

---

### 二十五、常用代码片段 100+

#### 1. 数字相关
```python
# 1. 判断奇偶
def is_even(n):
    return n % 2 == 0

# 2. 反转数字
def reverse_num(n):
    return int(str(n)[::-1])

# 3. 数字转列表
def num_to_list(n):
    return [int(d) for d in str(n)]

# 4. 列表转数字
def list_to_num(lst):
    return int(''.join(map(str, lst)))

# 5. 斐波那契数列
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a

# 6. 阶乘
def factorial(n):
    result = 1
    for i in range(1, n+1):
        result *= i
    return result

# 7. 最大公约数
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

# 8. 最小公倍数
def lcm(a, b):
    return a * b // gcd(a, b)

# 9. 判断质数
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# 10. 生成质数列表
def primes(n):
    sieve = [True] * (n+1)
    sieve[0] = sieve[1] = False
    for i in range(2, int(n**0.5)+1):
        if sieve[i]:
            sieve[i*i : n+1 : i] = [False]*len(sieve[i*i : n+1 : i])
    return [i for i, is_p in enumerate(sieve) if is_p]
```

#### 2. 字符串相关
```python
# 11. 反转字符串
s[::-1]

# 12. 判断回文
def is_palindrome(s):
    return s == s[::-1]

# 13. 统计字符出现次数
from collections import Counter
counts = Counter("hello world")

# 14. 去重保持顺序
def unique_chars(s):
    seen = set()
    result = []
    for c in s:
        if c not in seen:
            seen.add(c)
            result.append(c)
    return ''.join(result)

# 15. 字符串转列表
list("abc")  # ['a', 'b', 'c']

# 16. 列表转字符串
''.join(['a', 'b', 'c'])  # 'abc'

# 17. 首字母大写
s.title()

# 18. 驼峰转下划线
import re
def camel_to_snake(s):
    return re.sub(r'(?<!^)(?=[A-Z])', '_', s).lower()

# 19. 下划线转驼峰
def snake_to_camel(s):
    parts = s.split('_')
    return parts[0] + ''.join(p.title() for p in parts[1:])

# 20. 去除标点
import string
def remove_punctuation(s):
    return s.translate(str.maketrans('', '', string.punctuation))
```

#### 3. 列表相关
```python
# 21. 列表去重（保持顺序）
def unique(lst):
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

# 22. 列表去重（不保持顺序，简单快速）
list(set(lst))

# 23. 列表展开（扁平化）
def flatten(lst):
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

# 24. 列表分组
def group(lst, size):
    return [lst[i:i+size] for i in range(0, len(lst), size)]

# 25. 找出列表中出现次数最多的元素
from collections import Counter
def most_common(lst):
    return Counter(lst).most_common(1)[0][0]

# 26. 两个列表找共同元素
list(set(list1) & set(list2))

# 27. 两个列表找不同元素
list(set(list1) - set(list2))

# 28. 列表随机打乱
import random
random.shuffle(lst)

# 29. 列表随机取样
import random
random.sample(lst, 3)  # 随机选3个

# 30. 列表元素位置互换
lst[i], lst[j] = lst[j], lst[i]

# 31. 列表复制（深拷贝）
import copy
new_lst = copy.deepcopy(lst)

# 32. 列表合并
list1 + list2

# 33. 列表元素求和
sum(lst)

# 34. 列表元素平均值
sum(lst) / len(lst)

# 35. 列表中位数
def median(lst):
    sorted_lst = sorted(lst)
    n = len(sorted_lst)
    mid = n // 2
    if n % 2 == 0:
        return (sorted_lst[mid-1] + sorted_lst[mid]) / 2
    else:
        return sorted_lst[mid]
```

#### 4. 字典相关
```python
# 36. 字典键值互换
{v: k for k, v in d.items()}

# 37. 字典按key排序
sorted(d.items())

# 38. 字典按value排序
sorted(d.items(), key=lambda x: x[1])

# 39. 字典value最大的key
max(d, key=d.get)

# 40. 字典value最小的key
min(d, key=d.get)

# 41. 合并两个字典
{**d1, **d2}  # Python 3.5+
d1.update(d2)  # 原地合并

# 42. 字典推导式
squares = {x: x**2 for x in range(10)}

# 43. 两个列表合成字典
dict(zip(keys, values))

# 44. 字典默认值
from collections import defaultdict
d = defaultdict(int)  # 默认值为0
d['a'] += 1

# 45. 统计词频
from collections import Counter
counts = Counter(words)

# 46. 有序字典
from collections import OrderedDict
d = OrderedDict()

# 47. 字典获取带默认值
d.get('key', default_value)

# 48. 字典批量设置默认值
d.setdefault('key', value)

# 49. 字典删除指定key并返回值
d.pop('key', default_value)
```

#### 5. 文件操作
```python
# 50. 读取整个文件
with open('file.txt', 'r', encoding='utf-8') as f:
    content = f.read()

# 51. 逐行读取文件
with open('file.txt', 'r', encoding='utf-8') as f:
    for line in f:
        print(line.strip())

# 52. 读取所有行到列表
with open('file.txt', 'r', encoding='utf-8') as f:
    lines = f.readlines()

# 53. 写入文件
with open('file.txt', 'w', encoding='utf-8') as f:
    f.write('hello\n')

# 54. 追加写入
with open('file.txt', 'a', encoding='utf-8') as f:
    f.write('world\n')

# 55. 写入多行
with open('file.txt', 'w', encoding='utf-8') as f:
    f.writelines(lines)

# 56. 复制文件
import shutil
shutil.copy('src.txt', 'dst.txt')

# 57. 移动/重命名文件
import shutil
shutil.move('old.txt', 'new.txt')

# 58. 删除文件
import os
os.remove('file.txt')

# 59. 判断文件是否存在
import os
os.path.exists('file.txt')

# 60. 获取文件大小
import os
os.path.getsize('file.txt')
```

#### 6. 日期时间
```python
from datetime import datetime, date, timedelta

# 61. 当前时间
now = datetime.now()

# 62. 当前日期
today = date.today()

# 63. 格式化时间
now.strftime("%Y-%m-%d %H:%M:%S")

# 64. 字符串转时间
datetime.strptime("2024-01-01", "%Y-%m-%d")

# 65. 时间加减
tomorrow = today + timedelta(days=1)
yesterday = today - timedelta(days=1)

# 66. 时间差
diff = date2 - date1
diff.days  # 相差天数

# 67. 获取时间戳
import time
timestamp = time.time()

# 68. 时间戳转日期
datetime.fromtimestamp(timestamp)

# 69. 本周第一天
today - timedelta(days=today.weekday())

# 70. 本月第一天
today.replace(day=1)
```

#### 7. 正则表达式
```python
import re

# 71. 匹配数字
re.findall(r'\d+', text)

# 72. 匹配邮箱
re.findall(r'[\w.-]+@[\w.-]+\.\w+', text)

# 73. 匹配手机号
re.findall(r'1[3-9]\d{9}', text)

# 74. 匹配URL
re.findall(r'https?://[\w.-]+(?:/[\w.-]*)*', text)

# 75. 替换
re.sub(r'\d+', 'X', text)

# 76. 分割
re.split(r'[,;]', text)

# 77. 判断是否匹配
re.match(r'^\d+$', text)

# 78. 提取分组
match = re.search(r'(\d{4})-(\d{2})-(\d{2})', text)
if match:
    year, month, day = match.groups()
```

#### 8. 其他常用
```python
# 79. 计时
import time
start = time.time()
# ... 代码 ...
end = time.time()
print(f"耗时：{end-start:.4f}秒")

# 80. 生成随机字符串
import random
import string
def random_string(length):
    return ''.join(random.choices(string.ascii_letters + string.digits, k=length))

# 81. 暂停
import time
time.sleep(1)  # 暂停1秒

# 82. 命令行参数
import sys
args = sys.argv

# 83. 退出程序
import sys
sys.exit()

# 84. 获取环境变量
import os
os.environ.get('PATH')

# 85. 执行系统命令
import os
os.system('ls')

# 86. 获取当前目录
import os
os.getcwd()

# 87. 遍历目录
import os
for root, dirs, files in os.walk('.'):
    for f in files:
        print(os.path.join(root, f))

# 88. 打印进度条
for i in range(101):
    print(f"\r进度：{i}%", end='')
    time.sleep(0.1)

# 89. 异常捕获
try:
    pass
except Exception as e:
    print(f"出错了：{e}")

# 90. 断言
assert x > 0, "x必须大于0"
```

#### 9. 进阶技巧
```python
# 91. 列表推导式
[x**2 for x in range(10)]

# 92. 字典推导式
{ x: x**2 for x in range(10) }

# 93. 集合推导式
{ x**2 for x in range(10) }

# 94. 生成器表达式
(x**2 for x in range(10))

# 95. 三元表达式
x if condition else y

# 96. 解包赋值
a, b, c = [1, 2, 3]
a, *rest = [1, 2, 3, 4, 5]

# 97. 交换变量
a, b = b, a

# 98. 链式比较
1 < x < 10

# 99. 海象运算符（Python 3.8+）
if (n := len(s)) > 10:
    print(f"字符串太长，有{n}个字符")

# 100. 装饰器模板
import functools
def decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        # 前置操作
        result = func(*args, **kwargs)
        # 后置操作
        return result
    return wrapper
```

**我的代码收藏：**
> 

---

### 二十六、易错点与坑点汇总

#### 1. 基础语法
1. **缩进错误**：Python 靠缩进区分代码块，必须统一用4个空格，不要混用Tab和空格
2. **= 和 == 混淆**：`=` 是赋值，`==` 是比较
3. **忘记冒号**：if/for/while/def/class 后面都要加 `:`
4. **变量未定义就使用**：会报 `NameError`
5. **关键字做变量名**：比如 `list = [1,2,3]`，会覆盖内置函数

#### 2. 数据类型
6. **整数除法**：`/` 结果是 float，`//` 才是整除
7. **浮点数精度问题**：`0.1 + 0.2 != 0.3`
8. **字符串不可变**：不能直接 `s[0] = 'A'`，要重新赋值
9. **列表是可变对象**：函数传参时会修改原列表
10. **列表复制的坑**：`lst2 = lst` 不是复制，是引用；要用 `lst.copy()` 或 `lst[:]`
11. **字典 key 必须是不可变类型**：列表不能当 key
12. **字典 key 不存在会报错**：用 `get()` 更安全
13. **空集合不能用 {}**：`{}` 是空字典，空集合是 `set()`
14. **元组单个元素要加逗号**：`(1)` 是整数，`(1,)` 才是元组

#### 3. 循环与判断
15. **range 含头不含尾**：`range(5)` 是 0-4，不包含5
16. **for 循环中修改列表**：遍历列表时删除元素会出问题，用倒序或列表推导式
17. **while 循环忘记更新条件**：容易变成死循环
18. **is 和 == 混淆**：`is` 比较身份（内存地址），`==` 比较值
19. **小整数池的迷惑**：`a = 256; b = 256; a is b` 是True，但 `a = 257` 就不一定了

#### 4. 函数
20. **默认参数用可变对象**：`def func(lst=[])` 是大坑，默认值会被复用
21. **默认参数必须在位置参数后面**
22. **函数没有 return 时返回 None**
23. **全局变量在函数内修改要加 global**
24. **递归深度有限制**：默认递归深度约1000层，太深会栈溢出

#### 5. 文件操作
25. **忘记关闭文件**：一定要用 `with` 语句
26. **文件编码问题**：Windows 默认 GBK，最好指定 `encoding='utf-8'`
27. **路径分隔符**：Windows 是 `\`，Linux 是 `/`，用 `os.path.join()` 或 `pathlib`
28. **文件不存在就打开会报错**：先判断是否存在

#### 6. 异常处理
29. **裸 except 捕获所有异常**：不推荐，会隐藏问题，最好指定具体异常类型
30. **except 顺序写反**：要先写具体的，再写宽泛的

#### 7. 面向对象
31. **方法第一个参数忘记写 self**
32. **实例方法调用时传 self**：调用时不用传，Python 自动传
33. **类属性和实例属性混淆**
34. **继承时忘记调用 super().__init__()**

#### 8. 其他
35. **索引从0开始**：不是从1开始
36. **切片含头不含尾**：`s[1:4]` 包含索引1，不包含4
37. **负索引**：`s[-1]` 是最后一个元素
38. **Python 区分大小写**：`Name` 和 `name` 是两个变量
39. **字符串和数字不能直接拼接**：要先转类型
40. **列表 + 和 append 的区别**：`+` 是拼接返回新列表，`append` 是原地添加

**我的错题本：**

| 题目/场景 | 错误原因 | 正确写法 |
|-----------|----------|----------|
| | | |
| | | |
| | | |
| | | |
| | | |

---

### 二十七、实战小项目

### 项目1：猜数字游戏
```python
import random

def guess_number():
    target = random.randint(1, 100)
    count = 0
    
    print("欢迎来到猜数字游戏！")
    print("我想了一个1-100之间的数字，你来猜猜看")
    
    while True:
        try:
            guess = int(input("请输入你的猜测："))
            count += 1
            
            if guess < target:
                print("太小了，再大一点！")
            elif guess > target:
                print("太大了，再小一点！")
            else:
                print(f"恭喜你，猜对了！答案就是{target}")
                print(f"你一共猜了{count}次")
                break
        except ValueError:
            print("请输入一个整数！")

if __name__ == "__main__":
    guess_number()
```

### 项目2：简易计算器
```python
def calculator():
    print("简易计算器")
    print("支持：+ - * /")
    
    while True:
        expression = input("请输入算式（输入q退出）：")
        if expression.lower() == 'q':
            print("再见！")
            break
        
        try:
            result = eval(expression)
            print(f"结果：{result}")
        except Exception as e:
            print(f"输入有误：{e}")

if __name__ == "__main__":
    calculator()
```

### 项目3：待办事项管理
```python
def todo_manager():
    todos = []
    
    while True:
        print("\n===== 待办事项 =====")
        print("1. 查看所有待办")
        print("2. 添加待办")
        print("3. 删除待办")
        print("4. 标记完成")
        print("5. 退出")
        
        choice = input("请选择操作：")
        
        if choice == '1':
            if not todos:
                print("暂无待办事项")
            else:
                for i, todo in enumerate(todos, 1):
                    status = "✓" if todo['done'] else " "
                    print(f"{i}. [{status}] {todo['text']}")
        
        elif choice == '2':
            text = input("请输入待办内容：")
            todos.append({"text": text, "done": False})
            print("添加成功！")
        
        elif choice == '3':
            idx = int(input("请输入要删除的序号：")) - 1
            if 0 <= idx < len(todos):
                todos.pop(idx)
                print("删除成功！")
            else:
                print("序号不存在")
        
        elif choice == '4':
            idx = int(input("请输入要完成的序号：")) - 1
            if 0 <= idx < len(todos):
                todos[idx]['done'] = True
                print("已标记完成！")
            else:
                print("序号不存在")
        
        elif choice == '5':
            print("再见！")
            break
        
        else:
            print("无效选择，请重新输入")

if __name__ == "__main__":
    todo_manager()
```

### 项目4：词频统计
```python
from collections import Counter
import string

def word_count(filename):
    with open(filename, 'r', encoding='utf-8') as f:
        text = f.read()
    
    # 转小写，去标点
    text = text.lower()
    text = text.translate(str.maketrans('', '', string.punctuation))
    
    # 分词
    words = text.split()
    
    # 统计
    counts = Counter(words)
    
    # 输出前10个
    print("出现次数最多的10个单词：")
    for word, count in counts.most_common(10):
        print(f"{word}: {count}次")

if __name__ == "__main__":
    word_count("test.txt")
```

### 项目5：石头剪刀布
```python
import random

def rock_paper_scissors():
    choices = ["石头", "剪刀", "布"]
    win_map = {"石头": "剪刀", "剪刀": "布", "布": "石头"}
    
    print("欢迎来到石头剪刀布！")
    
    while True:
        player = input("请出拳（石头/剪刀/布，输入q退出）：")
        if player.lower() == 'q':
            print("再见！")
            break
        
        if player not in choices:
            print("请输入石头、剪刀或布！")
            continue
        
        computer = random.choice(choices)
        print(f"电脑出了：{computer}")
        
        if player == computer:
            print("平局！")
        elif win_map[player] == computer:
            print("你赢了！")
        else:
            print("你输了！")

if __name__ == "__main__":
    rock_paper_scissors()
```

**我的项目记录：**
> 

---

## 📝 学习进度追踪

### 基础入门
- [ ] Python 简介与环境搭建
- [ ] 基础语法规则
- [ ] 变量与数据类型

### 数据类型
- [ ] 数值类型 int/float/bool
- [ ] 字符串 str 详解
- [ ] 列表 list 详解
- [ ] 元组 tuple 详解
- [ ] 字典 dict 详解
- [ ] 集合 set 详解

### 运算符与流程控制
- [ ] 运算符大全
- [ ] 条件判断 if/elif/else
- [ ] 循环 for/while
- [ ] break/continue/pass

### 函数与模块
- [ ] 函数详解
- [ ] 模块与包

### 进阶内容
- [ ] 文件操作
- [ ] 异常处理
- [ ] 面向对象编程
- [ ] 迭代器与生成器
- [ ] 装饰器

### 实战项目
- [ ] 猜数字游戏
- [ ] 简易计算器
- [ ] 待办事项管理
- [ ] 词频统计
- [ ] 石头剪刀布

---

> 💡 **使用建议**：
> 1. 每学完一节，在「我的笔记」里补充自己的理解和代码
> 2. 做错的题目及时记录到「错题本」
> 3. 常用代码片段收藏到「代码片段」章节
> 4. 定期复习错题本和易错点
> 5. 学完基础就开始做小项目，边练边学
> 6. 遇到问题先查官方文档，再搜索，最后提问
