# 59 Specific Ways to Write Better Python

* [Pythonic Thinking](#pythonic-thinking)
    * [1. 明确Python版本](#item1)
    * [2. 遵循PEP8风格指引](#item2)
    * [3. 明确bytes，str和unicode的区别](#item3)
    * [4. 写辅助函数代替复杂表达式]
    * [5. 知道如何切割序列]
    * [6. 避免在单个切割中使用start，end和stride]
    * [7. 用列表推导代替map和filter](#item7)
    * [8. 避免多于两个表达式的列表推导]
    * [9. 大型推导考虑使用生成器]
    * [10. 用enumerate代替range]
    * [11. 用zip并行处理迭代](#item11)
    * [12. 避免在for和while循环后使用else]
    * [13. 利用好try/except/else/finally的每一块]
* [函数]
    * [14. 用异常代替返回None]
    * [15. 知道必包与变量作用域的相互作用]
    * [16. 考虑用生成器代替返回列表]
    * [17. 小心处理参数的迭代]
    * [18. 减少关键词参数的视觉干扰]
    * [19. 用关键词参数提供可选的特性]
    * [20. 用None和Docstrings指定动态默认参数]
    * [21. 只用关键词参数增加清晰度]
* [类与继承]
    * [22. 用辅助类代替用字典和元组记账](#item22)
    * [23. 简单的接口接受函数而不是类](#item23)
    * [24. 用@classmethod的多态性来通用地构造对象](#item24)
    * [25. 用super初始化父类]
    * [26. 只将多继承用在Mix-in功能类]
    * [27. 优先选择公有属性]
    * [28. 继承collecions.abc来实现自定义的容器]
* [Metaclasses和属性]
    * [29. 直接用属性替代Get和Set方法]
    * [30. 考虑用@property代替重构属性]
    * [31. 对可重复使用的@property方法使用修饰器]
    * [32. 对惰性属性使用__getattr__，__getattribute__和__setattr__]
    * [33. 用metaclass验证子类](#item33)
    * [34. 用metaclass注册类的存在]
    * [35. 用metaclass注释类的属性]
* [并发与并行]
    * [36. 用subprocess管理子进程]
    * [37. 用线程处理阻塞式I/O而不是并行计算]
    * [38. 用Lock避免线程间的数据竞争]
    * [39. 用Queue来解决线程间的合作]
    * [40. 考虑用协程来并行多个函数]
    * [41. 考虑用concurrent.futures来做真正的并行]
* [內建模块]
    * [42. 用functools.wraps来定义函数装饰器]
    * [43. 考虑用contextlib和with表达式完成try/finally的复用]
    * [44. 用copyreg使pickle变得可靠]
    * [45. 本地时钟用datetime替代time]
    * [46. 用内建的算法和数据结构]
    * [47. 当精确度很重要时使用decimal]
    * [48. 知道去哪里找社区提供的模块]
* [合作]
    * [49. 为每个函数、类和模块写Docstring]
    * [50. 用包来组织模块和提供稳定的API]
    * [51. 定义一个根异常来隔离API调用者]
    * [52. 知道怎样打破循环依赖]
    * [53. 用虚拟环境支持依赖的隔离和复用]
* [生产]
    * [54. 考虑用模块范围的代码来配置部署环境]
    * [55. 用repr字符串来调试输出]
    * [56. 用unittest来测试所有东西]
    * [57. 考虑用pdb做交互式调试]
    * [58. 先profile后优化]
    * [59. 用tracemalloc来理解内存使用和泄露]

# Pythonic Thinking
一门编程语言的使用风格是它的用户定义的。这么多年来，Python社区用*Pythonic*来形容符合特定风格的代码。Pythonic并不是编译器强制要求的，它是在长时间的使用这门语言和与其他人合作的过程积累出来的。Python程序喜欢清晰，简单而不是复杂，最大化可读性（试试 `import this`)。

熟悉其他语言的程序员可能把Python写得像C++、Java或他们最熟悉的某种语言。新手程序员可能还在适应大量的Python概念。所以很重要的一件事是：让大家了解最好的（最Pythonic）的方式去写Python。这些模式会影响到你写的每一个程序。

<a name="item1"></a>
## 1. 明确Python版本
本书里的大部分代码样例是Python3.4（2014.5.17版本）的语法，另外还有一部分是Python2.7（2010.7.3版本）语法用来对比两个版本间重要的区别。本书绝大多数建议适用于所有Python runtime：Cpython，Jython，IronPython，PyPy等。

很多电脑预装了多个版本的标准CPython。然而，命令行中的`python`指令可能并不清晰.`python`通常是`python2.7`的别名(alias)，但是有时候也是更老的版本的别名比如`python2.6`或`python2.5`。要搞清楚你用的是哪个版本的Python，你可以用`--version`参数。
```bash
$python --version
Python 2.7.10
```
Python3通常是用指令`python3`
```bash
$python3 --version
Python 3.4.2
```
你也可以在runtime里面用內建模块`sys`来搞清楚Python版本
```python
>>> import sys
>>> print(sys.version_info)
sys.version_info(major=2, minor=7, micro=10, releaselevel='final', serial=0)
>>> print(sys.version)
2.7.10 (default, Oct 23 2015, 19:19:21) 
[GCC 4.2.1 Compatible Apple LLVM 7.0.0 (clang-700.0.59.5)]
```

目前Python社区在同时维护Python2和Python3两个版本。Python2的发展目前主要是bug修复、安全性提升和反向移植（简化Python2到Python3的过渡）。一些有用的工具像`2to3`和`six`可以帮你更轻松的过渡到Python3开发。

Python3正在持续地添加新特效和新改进，Python2并不会。写这本书的时候，大多数最常用的Python开源库已经兼容了Python3。所以我强烈推荐使用Python3写你的下一个Python项目。

### 要点
*   现在有两个活跃的Python版本：Python2和Python3
*   现在有多个常用的Python runtime：CPython，Jython，IronPython，PyPy等
*   要确定`python`命令是你想要用的版本
*   选择Python3写你的下个项目，因为Python社区更专注于维护Python3

<a name="item2"></a>
## 2. 遵循PEP8风格指引
PEP8，Python第8号提升建议，是一个风格指引指导你如何去格式化Python代码。你可以随心所欲的写Python代码，只要语法正确。但是持续遵循一种风格会让你的代码更加易读，更加容易被接受。在大型社区中共享一种通用的风格也会让项目中的合作更加方便。另外即使你的代码只有你自己一个人会读，遵循风格指引也会让以后维护代码更加轻松。

PEP8包含很多细节告诉你如何写清晰的Python代码。随着Python语言的发展，它也在持续地更新。直接在线读一读[PEP8](https://www.python.org/dev/peps/pep-0008/)很有意义。这里列出了一些你务必要遵守的规则：

#### 空格
Python语法中空格很重要，Python程序员也对空格特别敏感，它对代码的清晰程度有很大影响。

*   缩进用空格代替tab
*   每层缩进用4个空格
*   一行不超过79个字符
*   太长的一行换行之后需要在常规缩进后再加4个空格
*   文件中函数和类之间都要用2个空行隔开
*   类里面的方法要用1个空行隔开
*   列表索引、函数调用、关键词参数都不要用空格
*   变量赋值等号前后有且只有一个空格


#### 命名
PEP8建议对语言中的不同部分用不同的命名风格。这样在读代码的时候可以清楚的分辨各个命名对应哪种类型。

*   函数、变量、属性用`lowercase_underscore`（小写+下划线）
*   受保护的实例属性用`_leading_underscore`（一个下划线开头）
*   私有的实例属性用`__double_leading_underscore`（两个下划线开头）
*   类和异常用`CapitalizedWord`（大写字母开头）
*   模块级别的常量用`ALL_CAPS`（全大写字母）
*   类的实例方法用`self`作为一个参数，指向对象本身
*   类方法用`cls`作为第一个参数，指向类本身


#### 表达式和语句
Python之禅说道：要解决一个问题，有且只有一种最明显的方式。PEP8尝试为表达式和语句明确这种风格。

*   用（`if a is not b`）代替（`if not a is b`）
*   不要用长度（`if len(somelist) == 0`）检查空值（比如`[]`，`''`）。用`if not somelist`，空值在`if`语句中等价于`False`
*   同理，非空的值（比如`[1]`, `'hi'`）在`if`语句中等价为`True`
*   避免单行`if/for/while/except`语句，分行更加清晰
*   总是在文件开头使用`import`语句
*   总是使用模块的绝对名字来`import`，而不是相对于当前模块路径的名字。比如说，要`import bar`包里面的`foo`模块，要用`from bar imort foo`，而不是`import foo`
*   如果你必须要用相对`import`，显示地写明`from . import foo`
*   import的分段顺序：标准模块，第三方模块，你自己的模块。每个子分段用字母表顺序

> *注解*
[Pylint](https://www.pylint.org)是一个常用python源代码的静态分析工具。Pylint提供了自动化执行PEP8规范的功能，还可以检测出Python程序中的很多其他常见错误。

### 要点
*   写Python代码的时候总是遵循PEP8风格指引
*   在大型Python社区中共享通用的代码风格可以方便合作
*   遵循一种风格让你以后维护自己的代码更轻松

<a name="item3"></a>
## 3. 明确bytes，str和unicode的区别
在Python3中，有两种类型表示字符的序列：`bytes`和`str`。`bytes`的实例包含原始的8位字符。`str`的实例包含Unicode字符

在Python2中，有两种类型表示字符的序列：`str`和`unicode`。不同于Python3，`str`的实例包含原始的8位字符。`unicode`的实例包含Unicode字符

有很多种方式将Unicode字符表示为二进制数据（原始8位字符），最常用的编码方式是UTF-8。要注意，Python3中的`str`实例和Python2中的`unicode`实例没有一个关联的二进制编码。要将Unicode字符转换为二进制数据，你必须使用`encode`方法。要将二进制数据转换为Unicode字符，你必须使用`decode`方法。

当你写Python程序的时候，在你的接口的最外层做编码和解码。你的程序的核心要用Unicode字符类型（Python3中的`str`，Python3中的`unicode`），而不要考虑任何编码相关的事情。这种方法让你可以接受各种编码（比如`Latin-1`,   `ShiftJIS`,`Big5`），同时严格控制你的输出编码（最好是`UTF-8`）。

Python代码中区分两种字符类型导致两种常见的情况：

*   你想操作UTF-8编码（或其他编码）的原始8位字符
*   你想操作没有具体编码的Unicode字符

你会经常需要两个辅助函数来转换这两种情况，来保证输入数据的类型符合预期。
Python3中，你会需要一个方法输入`str`或`bytes`，然后总是输出`str`
```
def to_str(bytes_or_str):
    if isinstance(bytes_or_str, bytes):
        value = bytes_or_str.decode('utf-8')
    else:
        value = bytes_or_str
    return value  # Instance of str
```

你需要另一个方法输入`str`或`bytes`，然后总是输出`bytes`
```
def to_bytes(bytes_or_str):
    if isinstance(bytes_or_str, str):
        value = bytes_or_str.encode('utf-8')
    else:
        value = bytes_or_str
    return value  # Instance of bytes
```

Python2中，你会需要一个方法输入`str`或`unicode`，然后总是输出`unicode`
```
# Python2
def to_unicode(unicode_or_str):
    if isinstance(unicode_or_str, str):
        value = unicode_or_str.decode('utf-8')
    else:
        value = unicode_or_str
    return value  # Instance of unicode
```

你需要另一个方法输入`str`或`unicode`，然后总是输出`str`
```
# Python2
def to_str(unicode_or_str):
    if isinstance(unicode_or_str, unicode):
        value = unicode_or_str.encode('utf-8')
    else:
        value = unicode_or_str
    return value  # Instance of str
```

当你在Python中处理原始8位字符和Unicode字符，还有两个重要的问题需要注意。

第一个问题是在Python2中，当只包含7位的ASCII字符时，`unicode`和`str`的实例看起来是相同的类型。

*   你可以用`+`合并`str`和`unicode`
*   你可以用等号和不等号比较`str`和`unicode`
*   你可以用`%s`来格式化`unicode`

所有这些表现意味着你通常在传参数时不用区分`str`和`unicode`实例（只要你只处理7位ASCII字符）。在Python3中，`bytes`和`str`实例永远不会相等——即使是空字符串——所以你需要更加注意你传的字符串类型。

第二个问题是在Python3中，与文件句柄（內建函数`open`返回的）相关的操作默认UTF-8编码。在Python2中，文件操作默认用二进制编码。这会造成意外的失败，特别是对于习惯Python2的程序员。

比如说，你要写一些随机二进制数据到一个文件。在Python2中这样可以，但是Python3中这样不行。
```
with open('/tmp/random.bin', 'w') as f:
    f.write(os.urandom(10))
>>>
TypeError: must be str, not bytes
```
造成这个异常的原因是，Python3中`open`函数新增了`encoding`参数，这个参数默认值是'utf-8'。这让文件的`read`和`write`操作接受包含Unicode字符的`str`实例，而不是包含二进制数据的`bytes`实例。

为了修正这个问题，你必须指定用二进制写模式（`'wb'`）打开，而不是写模式（`'w'`）。下面这种写法在Python2和Python3都可以正常运行：
```
with open('/tmp/random.bin', 'wb') as f:
    f.write(os.urandom(10))
```
这个问题同样存在于从文件中读取数据。解决方法一样：打开文件时指定二进制模式，用`'rb'`代替`'r'`。

### 要点
*   在Python3中，`bytes`包含8位字符的序列，`str`包含Unicode字符的序列。`bytes`和`str`实例之间不能使用操作符（比如`>`或`+`）
*   在Python2中，`str`包含8位字符的序列，`unicode`包含Unicode字符的序列。当`str`只包含7位的ASCII字符时，`str`和`unicode`实例之间可以使用操作符（比如`>`或`+`）
*   用辅助函数来保证你的输入字符串类型符合你的语气
*   当你想要

<a name="item7"></a>
## 7. 用列表推导代替map和filter

<a name="item11"></a>
## 11. 用zip并行处理迭代
在Python中你会经常用到很多list关联到相同的一批对象。列表推导让你很方便地对源列表应用一个表达式生成新的列表(看[7. 用列表推导代替map和filter](#7-mapfilter))。
```
names = ['Cecilia', 'Lise', 'Marie']
letters = [len(n) for n in names]
```

新列表的每一项与源列表的每一项索引是一一对应的。要想迭代并行迭代两个列表，你可以用源列表`names`的长度来迭代
```
longest_name = None
max_letters = 0
for i in range(len(names)):
    count = letters[i]
    if count > max_letters:
        longest_name = names[i]
        max_letters = count
print(longest_name)
```

这样的问题是整个循环看起来很杂乱，`names`和`letters`的索引让代码很难读。列表要进行两次索引。使用enumerate可以稍微好一点，但仍然不理想。
```
for i, name in enumerate(names):
    count = letters[i]
    if count > max_letters:
        max_letters = count
```

为了让这段代码更清晰，Python提供了內建函数`zip`。在Python3中，zip将两个或更多的迭代器包装成一个生成器。`zip`生成器yeild包含了每个迭代器下一个元素的元组。这样代码就清晰很多了。
```
for name, count in zip(names, letters):
    if count > max_letters:
        longest_name = name
        max_letters = count
```

內建函数`zip`还有两个问题。
首先Python2里的`zip`不是一个生成器，它会遍历每个迭代器然后返回一个元组的列表。这可能会耗掉很多内存，导致程序崩溃。如果你想在Python2中`zip`很大的迭代器，你应该用內建模块`itertools`提供的`izip`函数（看[46. 使用內建算法和数据结构]()）
第二个问题是如果输入的迭代器长度不一样，`zip`的表现会很奇怪。比如，你在`name`列表中加了一个名字而没有更新`letters`列表，使用`zip`会有意外的结果。
```
names.append("Rosalind")
for name, count in zip(names, letters):
    print(name)
>>>
Cecilia
Lise
Marie
```
新加的项`Rosalind`没有显示出来，这就是zip的工作方式。它一直输出元组，直到某一个输入的迭代器耗尽。通常情况下当你知道输入迭代器的长度相同，这种工作方式没问题。但是其他情况下，这种截断的行为会造成意外。如果你不确定输入列表的长度相同，考虑用內建模块`itertools`里的`zip_longest`函数（Python2中的`izip_longest`）

###  要点
*   內建函数`zip`可以用来并行迭代多个迭代器
*   Python3中的`zip`是一个生成元组的生成器，Python2中的`zip`返回所有元组的列表
*   如果你输入的迭代器长度不同，zip会截断输出
*   內建模块`itertools`的`zip_longest`函数并行迭代多个迭代器，不管长度是否相等（看[46. 使用內建算法和数据结构]()）

<a name="item22"></a>
## 22. 用辅助类代替用字典和元组记账
Python內建的字典类型在管理对象动态内部状态时非常好用。动态，是指你要记录一系列非预设的标识。比如说你要记录一系列学生的分数，而学生的名字事先不知道。你可以定义一个类，把名字存在字典里，而不是每个学生定义一个属性。
```
class SimpleGradeBook(object):
    def __init__(self):
        self._grades = {}

    def add_student(self, name):
        self._grades[name] = []

    def report_grade(self, name, score):
        self._grades[name].append(score)

    def average_grade(self, name):
        grades = self._grades[name]
        return sum(grades) / len(grades)
```
这个类的用法很简单
```
book = SimpleGradeBook()
book.add_student('Isaac Newton')
book.report_grade('Isaac Newton', 90)

print(book.average_grade('Isaac Newton'))
>>>
90.0
```
字典如此好用，以至于阻碍了我们写出更好的代码。比如说你想扩展`SimpleGradeBook`类来根据学科记录成绩，而不是全部记到一起。你可以修改`_grades`字典，将学生名字（键）映射到另外一个字典（值）。里层的字典将学科（键）映射到分数（值）。
```
class BySubjectGradeBook(object):
    def __init__(self):
        self._grades = {}

    def add_student(self, name):
        self._grades[name] = {}
```
这种改动方法看起来很明显。要处理多级字典，`report_grade`和`average_grade`方法会更加一些复杂度，但是还是可以搞定的。
```
    def report_grade(self, name, subject, grade):
        by_subject = self._grades[name]
        grade_list = by_subject.setdefault(subject, [])
        grade_list.append(grade)

    def average_grade(self, name):
        by_subject = self._grades[name]
        total, count = 0, 0
        for grades in by_subject.values():
            total += sum(grades)
            count += len(grades)
        return total / count
```
这个类的用法还是比较简单
```
book = BySubjectGradeBook()
book.add_student('Albert Einstein')
book.report_grade('Albert Einstein', 'Math', 75)
book.report_grade('Albert Einstein', 'Math', 65)
book.report_grade('Albert Einstein', 'Gym', 90)
book.report_grade('Albert Einstein', 'Gym', 95)
```
现在，假设你的需求再一次发生变化。你想记录每个分数相对于一门课总分的权重，这样期中期末考试就会比小测试更重要。要添加这种特性，可以改变里层的字典；不是学科（键）映射到成绩（值），而是映射到成绩和权重的元组`(score, weight)`。
```
class WeightedGradeBook(object):
    # ...
    def report_grade(self, name, subject, score, weight):
        by_subject = self._grades(name)
        grade_list = by_subject.setdefault(subject, [])
        grade_list.append((score, weight))
```
虽然`report_grade`的改动看起来简单——只是把值改成了一个元组——`average_grade`方法现在需要循环套循环，而且很难看明白。
```
    def average_grade(self, name):
        by_subject = self._grades(name)
        score_sum, score_count = 0, 0
        for subject, scores in by_subject.items():
            subject_avg, total_weight = 0, 0
            for score, weight in scores:
                #...
        return score_sum / score_count
```
这个类的用法也变得更复杂，位置参数中的多个数字意义不够清晰。
```
book.report_grade('Albert Einstein', 'Math', 80, 0.10)
```
当事情到了这种复杂程度，就是时候从字典和元组升级到多层级的类了。

最初，你不知道你需要支持分数权重，所以额外的辅助类的复杂程度看起来不可预估的。Python的內建字典和元组类型简单好用，让我们记账似的一层层地增加内部结构。其实你应该避免多与一层的嵌套（避免字典里包含字典）。它会让其他程序员很难读懂你的代码，维护起来像噩梦一般。

一旦你意识到记账变得复杂，分解成多个类。这样可以提供更好的接口，来封装你的数据。同事，这也让你在接口和具体实现之间创建一个抽象层。

### 重构成多个类
你可以从树型结构依赖的最底层来开始重构：单个分数。对于这么简单的信息，一个类似乎过于重度。一个元组，似乎很合适，因为分数是不可变的。这里，我用元组`(score, weight)`来将分数记录在一个列表中。
```
grades = []
grades.append((95, 0.45))
# ...
total = sum(score * weight for score, weight in grades)
total_weight = sum(weight for _, weight in grades)
average_grade = total / total_weight
```
问题是元组是按位置来排的。当你想关联更多信息到成绩上，比如老师的评语，你就需要重写所有2值元组的用法，因为变成了3值元组。这里，我用`_`（下划线作为变量名，表示Python惯例中没有用到的变量）来忽略元组中的第三个值。
```
grades = []
grades.append((95, 0.45, 'Great job'))
# ...
total = sum(score * weight for score, weight, _ in grades)
total_weight = sum(weight for _, weight, _ in grades)
average_grade = total / total_weight
```
这种方法让元组越来越长，其实跟增加字典的层次很像。当你发现你要用到2值以上的元组时，就应该考虑另外的方法了。

`collections`模块中的`namedtuple`正好是你需要的。它让你很方便的定义微型的、不可变的数据类。
```
import collections
Grade = collections.namedtuple('Grade', ('score', 'weight'))
```
这样的类可以由位置或者关键词参数来构造。字段可以由属性名来获取。当以后需求再次改变时，比如说要添加一些方法，有属性名就可以让你很轻松地从`namedtuple`升级到自定义的类。

>#####`namedtuple`的局限性
虽然`namedtuple`在很多情况下很有用，你更需要了解什么时候它会造成麻烦。

>*   你无法指定参数的默认值。当你有很多可选属性时，这会很麻烦。如果你发现你要的不只是少量的属性，定义你自己的类会是更好的选择。
*   实例的属性依然可以用数字索引来获取，也可以迭代。特别是面向外部的API，这可能会导致不恰当的用法，以后迁移到自定义的类就会很麻烦。如果你无法控制`namedtuple`的所有实例的用法，最好还是定义你自己的类吧。

接下来，你可以写一个类来代表包含一系列分数的单个学科。
```
class Subject(object):
    def __init__(self):
        self._grades = []

    def report_grade(self, score, weight):
        self._grades.append(Grade(score, weight))

    def average_grade(self):
        total, total_weight = 0, 0
        for grade in self._grades:
            total += grade.score * grade.weight
            total_weight += grade.weight
        return total / total_weight
```
然后你可以写一个类来表示一个学生正在学习的所有学科。
```
class Student(object):
    def __init__(self):
        self._subjects = {}

    def subject(self, name):
        if name not in self._subjects:
            self._subjects[name] = Subject()
        return self._subjects[name]

    def average_grade(self):
        total, count = 0, 0
        for subject in self._subjects.values():
            total += subject.average_grade()
            count += 1
        return total / count
```
最后，写一个包含所有学生并以名字为键的容器。
```
class Gradebook(object):
    def __init__(self):
        self._students = {}

    def student(self, name):
        if name not in self._students:
            self._students[name] = Student()
        return self._students[name]
```
这些类的代码行数几乎是之前的实现的两倍，但是代码易读很多。这些类的使用同样也更加清晰，更加易扩展。
```
book = Gradebook()
albert = book.student('Albert Einstein')
math = albert.subject('Math')
math.report_grade(80, 0.10)
# ...
print(albert.average_grade())

>>>
81.5
```
如果有必要，你可以写一些向后兼容的方法来将旧的API用法迁移到新的对象层级。

### 要点
*   字典里的值不要包含其他字典或者长元组
*   用`namedtuple`作轻量、不可变的数据容器，仅在你需要更灵活的完整类之前
*   用辅助类代替记账式的代码，当你的内部状态字典变得过于复杂时。

<a name="item23"></a>
## 23. 简单的接口接受函数而不是类
Python很多內建的API允许你传入一个函数来自定义某些行为。这些钩子（`hook`）在API执行的时候回调你的函数。比如，列表类型（`list`）的排序（`sort`）方法接收一个`key`参数，用来决定值的排序方法。这里，我按名字长度来排序一个名字的列表，将一个`lambda`表达式作为`key`的钩子：
```
names = ['Socrates', 'Archimedes', 'Plato', 'Aristotle']
names.sort(key=lambda x: len(x))
print(names)

>>>
['Plato', 'Socrates', 'Aristotle', 'Archimedes']
```
在其他语言中，你可能会用一个抽象类来定义一个钩子。在Python中，很多钩子是无状态的函数，有定义好的参数和返回值。函数作为钩子，因为函数在Python是一等公民：函数和方法可以被传递和引用，就像其他值一样。
比如说，你想自定义`defaultdict`类的行为（看[46. 使用內建的算法和数据结构](#46)）。这个数据结构让你提供一个函数，在每次有不存在的键被访问的时候调用。这个函数必须返回这个不存在的键在字典所对应的默认值。这里我定义了一个钩子，当每次访问不存在的键时，记录log并且返回默认值0：
```
def log_missing():
    print('Key added')
    return 0
```
给定以下的初始字典和增长列表，我们会调用两次`log_missing`函数，并且打印两次：
```
current = {'green': 12, 'blue': 3}
increments = [
    ('red', 5),
    ('blue', 17),
    ('orange', 9),
]
result = defaultdict(log_missing, current)
print('Before', dict(result))
for key, amount in increments:
    result[key] += amount
print('After', dict(result))

>>>
['Plato', 'Socrates', 'Aristotle', 'Archimedes']
('Before', {'blue': 3, 'green': 12})
Key added
Key added
('After', {'blue': 20, 'orange': 9, 'green': 12, 'red': 5})
```
提供`log_missing`这样的函数会让API变得很容易构造和测试，因为这样将决定性的行为与副作用区分开了。比如说，你现在想让`defaultdict`的默认值钩子计算所有不存在的键的总数。一种实现方法是用带状态的必包（看[15. 知道必包与变量作用域的相互作用](#15)）。这里，我定义一个辅助函数用这样的必包作为默认值的钩子。
```
def increment_with_report(current, increments):
    added_count = 0

    def missing():
        nonlocal added_count  # Stateful closure
        added_count += 1
        return 0

    result = defaultdict(missing, current)
    for key, amount in increments:
        result[key] += amount

    return result, added_count
```
运行这个函数会返回`2`，即使`defaultdict`完全不知道`missing`这个钩子包含状态。这是另一个接口接受函数的优点。在必包中隐藏状态让以后增加功能变得更容易。
```
result, count = increment_with_report(current, increments)
assert count == 2
```
为带状态的钩子定义必包的问题是，它比无状态的函数难读。另一种方法是定义一个小型的类来封装你想要追踪的状态。
```
class CountMissing(object):
    def __init__(self):
        self.added = 0

    def missing(self):
        self.added += 1
        return 0
```
在其他语言中，你现在可能要修改`defaultdict`来适应`CountMissing`的接口。但是在Python中，因为有一等公民函数，你可以像对象一样直接引用`CountMissing`方法，作为默认值的钩子传入`defaultdict`。用一个方法来满足一个函数接口是很轻松的。
```
counter = CountMissing()
result = defaultdict(counter.missing, current)  # Method ref
for key, amount in increments:
    result[key] += amount
assert counter.added == 2
```
像这样使用一个辅助类来替代带状态的必包，比起上面的`increment_with_report`函数更加清晰。然而，我们单独来看`CountMissing`类的目的，并不是很清楚。谁构造了`CountMissing`对象？谁调用了`missing`方法？这个类以后会不会添加其他的公有方法？在你看到`defaultdict`之前，这个类的用处一直是个谜。

为了让这种情况更清晰，Python允许类定义一个特殊的方法`__call__`。`__call__`让一个对象可以像函数一样被调用。它同样使对这个实例调用內建函数`callable`返回`True`。
```
class BetterCountMissing(object):
    def __init__(self):
        self.added = 0

    def __call__(self):
        self.added += 1
        return 0

counter = BetterCountMissing()
counter()
assert callable(counter)
```
这里，我用`BetterCountMissing`的实例作为`defaultdict`的默认值钩子来追踪被添加的不存在的键的总数。
```
counter = BetterCountMissing()
result = defaultdict(counter, current)  # Relies on __call__
for key, amount in increments:
    result[key] += amount
assert counter.added == 2
```
这个例子就比`CountMissing.missing`清晰多了。`__call__`方法说明一个类的实例将会被用作一个接受函数的参数（比如API钩子）。它将代码的读者引导到这个类的使用入口。它也说明这个类的目的是作为一个带状态的必包。

最重要的一点是，`defaultdict`完全不知道当你调用`__call__`的时候发生了说明。`defaultdict`只是需要一个函数作为默认值钩子而已。Python提供了很多不同的方式来满足一个简单的函数接口，按你的需求来实现吧。

### 要点
*   Python中，函数通常可以作为组件之间的简单接口，而不用定义和初始化一个类。
*   Python中，函数和方法的引用是一等公民，它们可以像其他类型一样在表达式中使用。
*   特殊方法`__call__`可以让一个类的实例像普通Python函数一样被调用。
*   当你需要一个函数来记录状态，考虑定义一个提供`__call__`方法的类，而不是定义一个带状态的必包（看[15. 知道必包与变量作用域的相互作用](#15)）。



<a name="item24"></a>
## 24. 用@classmethod的多态性来通用地构造对象
在Python中，不仅对象支持多态，类也支持。这意味着什么？这又有什么好处？

多态让一个层级结构的多个类对于同一个方法有自己独特的实现。这让很多类可以提供统一接口或者抽象基类，同时提供不同的功能（以[28. 继承collections.abc来实现自定义的容器类型](#28)为例）。

比如说，你正在写一个MapReduce的实现，你需要一个通用的类来表示输入数据。这里，我们定义了一个带有`read`方法的类，这个方法必须在子类中定义。
```
class InputData(object):
    def read(self):
        raise NotImplementedError
```
这里，我有一个具体的子类继承自`InputData`，从硬盘中的文件读取数据。
```
class PathInputData(InputData):
    def __init__(self, path):
        super().__init__()
        self.path = path

    def read(self):
        return open(self.path).read()
```
你可以有很多个`InputData`的子类，像`PathInputData`一样，各自实现标准的`read`接口返回要处理的数据。其他的`InputData`子类可以从网络中读取数据、解压数据、等等。

你还需要一个类似的抽象接口用一种标准的方法来接收输入数据。
```
class Worker(object):
    def __init__(self, input_data):
        self.input_data = input_data
        self.result = None

    def map(self):
        raise NotImplementedError

    def reduce(self):
        raise NotImplementedError
```
这里，我定了一个具体的`Worker`的子类来实现我需要的MapReduce函数：一个简单的行数计数器：
```
class LineCountWorker(Worker):
    def map(self):
        data = self.input_data.read()
        self.result = data.count("\n")
        print self.input_data, self.result

    def reduce(self, other):
        self.result += other.result
```
这种实现看起来不错，但我遇到了一个很大的障碍。这几个代码片段之间的联系是什么？我有一系列类，它们都有合理的接口和抽象——仅当一次构造一个对象。但是怎样构造大量的对象用于MapReduce呢？

最简单的办法是手动构造和连接大量对象和辅助函数。这里，我列出了一个目录下的内容，每个文件构造一个`PathInputData`实例。
```
def generate_inputs(data_dir):
    for name in os.listdir(data_dir):
        yield PathInputData(os.path.join(data_dir, name))
```
接下来，我用`generate_inputs`返回的`InputData`构造`LineCountWorker`实例。
```
def create_workers(input_list):
    workers = []
    for input_data in input_list:
        workers.append(LineCountWorker(input_data))
    return workers
```
我将这些`Worker`实例的`map`步骤分配到多个线程中执行（看[37. 阻塞式I/O使用线程，避免并行](#37)）。然后我循环调用`reduce`来计算最终的结果。
```
def execute(workers):
    threads = [Thread(target=w.map) for w in workers]
    for thread in threads: thread.start()
    for thread in threads: thread.join()
    first ,rest = workers[0], workers[1:]
    for worker in rest:
        first.reduce(worker)
    return first.result
```
最后，我将所有代码片段在一个函数里面连接起来运行。
```
def mapreduce(data_dir):
    inputs = generate_inputs(data_dir)
    workers = create_workers(inputs)
    return execute(workers)
```
这个函数在一系列测试文件上运行良好。
```
from tempfile import TemporaryDirectory

def write_test_files(tmpdir):
    # ...

with TemporaryDirectory() as tmpdir:
    write_test_files(tmpdir)
    result = mapreduce(tmpdir)

print('There are', result, 'lines')

>>>
There are 4360 lines
```
问题是什么？一个很大的问题是`mapreduce`函数根本不通用。如果你要写另一个`InputData`或者`Worker`的子类，你又要重新写对应的`generate_inputs`，`create_workers`和`mapreduce`函数。

这个问题归结于需要一个通用的方法来构造多个的对象。其他语言中，你可以用构造器的多态性来解决这个问题，每个`InputData`的子类提供一个特殊的构造器被辅助函数调用做MapReduce。问题是Python只允许有一个构造函数`__init__`。要求每个`InputData`的子类写一个对应的构造器很不合理。

这个问题的最好的解决办法是利用`@classmethod`的多态性。这就像我利用实例方法的多态性来写`InputData.read`，不同点是它只用于类本身而不是类构造的对象。

那么我们将这个办法应用在MapReduce的类上。这里我扩展了`InputData`类，加了一个类方法来负责用一个通用接口来生成多个新的`InputData`实例
```
class GenericInputData(object):
    def read(self):
        raise NotImplementedError

    @classmethod
    def generate_input(cls, config):
        raise NotImplementedError
```
`generate_input`接受一个字典参数，提供一系列配置参数给具体的`InputData`子类解析。这里，我用`config`来表示输入文件的目录路径。
```
class PathInputData(GenericInputData):
    def __init__(self, path):
        # super().__init__()
        self.path = path

    def read(self):
        return open(self.path).read()

    @classmethod
    def generate_inputs(cls, config):
        data_dir = config['data_dir']
        for name in os.listdir(data_dir):
            yield cls(os.path.join(data_dir, name))
```
类似的，我将`create_workers`作为辅助部分加入到`GenericWorker`类。这里，我用`input_class`参数来生成必需的输入，这个参数必须是`GenericInputData`的子类。然后用`cls()`作通用的构造器来构造`GenericWorker`的子类的实例。
```
class GenericWorker(object):
    def __init__(self, input_data):
        self.input_data = input_data
        self.result = None

    def map(self):
        raise NotImplementedError

    def reduce(self):
        raise NotImplementedError

    @classmethod
    def create_workers(cls, input_class, config):
        workers = []
        for input_data in input_class.generate_inputs(config):
            workers.append(cls(input_data))
        return workers
```
注意，`input_class.generate_inputs`的调用就是我想展示的类的多态性。你还可以看看`create_workers`调用`cls`来构造`GenericWorker`对象，而不是直接调用`__init__`方法。

对于`GenericWorker`的子类影响很小，就是改一下父类。
```
class LineCountWorker(GenericWorker):
    # ...
```
最终，我可以重写出一个完全通用的`mapreduce`函数。
```
def mapreduce(worker_class, input_class, config):
    workers = worker_class.create_workers(input_class, config)
    return execute(workers)
```
在新的代码上运行测试文件会生成同样的结果。区别在于`mapreduce`函数变得通用了，所以需要多传几个参数。
```
with TemporaryDirectory() as tmpdir:
    write_test_files(tmpdir)
    config = {'data_dir': tmpdir}
    result = mapreduce(LineCountWorker, PathInputData, config)
```
现在你就可以随意写其他`GenericInputData`和`GenericWorker`子类，而完全不需要重写任何胶水代码。

### 要点
*   Python的一个类只支持一个构造器，`__init__`方法
*   用`@classmethod`来定义其他的构造器
*   用类方法的多态性提供通用方法来构造和连接具体的子类。








<a name="item33"></a>
## 33. 用metaclass验证子类
Metaclass最简单的应用就是验证一个类定义的正确性。当你构造多层级的类时，你可能需要限定类型、强制重载方法或者严格限制类属性间的关系。Metaclass提供了一种可靠的方法，让你可以在定义一个子类时就运行验证代码。

通常一个类的验证代码在__init__方法中运行，一个类的类型被构造时（看[28. 继承collecions.abc来实现自定义的容器](#item28)）。用metaclass来验证可以更简单地抛出异常。










