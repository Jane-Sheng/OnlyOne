# Python笔记

## 第2章 变量和简单数据类型

### 2.4 数据类型转换

- str(x) 转为字符串函数

  ```python
  >>> year = 2000
  >>> str(2000)
  '2000'
  ```

- ord(x) ASCII字符转为十进制数

  ```python
  >>> ord('a')
  97
  ```

- chr(x) 十进制数转为ASCII字符

  ```python
  >>> chr(100)
  'd'
  ```

## 第3章 条件分支与循环

### 3.5 复杂条件及处理

身份运算符

```python
>>> i=t=1
>>> id(i)
1458624304
>>> id(t)
1458624304
```

~ 按位翻转

\>\> 右移运算符 << 左移运算符

^ 按位异或

## 第4章 列表与元组

### 4.1 接触列表 List

- 列表元素增加 append() insert()

  ```python
  >>> fruits = ['apple']
  >>> fruits.append('pear')
  >>> fruits
  ['apple', 'pear']
  >>> fruits.insert(1, 'banana')
  >>> fruits
  ['apple', 'banana', 'pear']
  ```

- 列表元素查找 index()、in成员运算、下标、切片

  ```python
  >>> list1=['Tom', 1, 2.3, 1]
  >>> list1.index('Tom')	# 返回元素下标
  0
  >>> list1.index(1)	# 默认返回第1次出现的下标
  1
  >>> list1.index(1,2)	# 返回第2次出现的下标
  3
  >>> list1.index('a')
  Error
  >>> 'a' in list1
  False
  >>> list1[0]
  'Tom'
  >>> list1[1:]
  [1, 2.3, 1]
  ```

- 列表元素修改

  ```python
  >>> list1=['Tom', 1, 2.3, 1]
  >>> list1[3]='元'
  >>> list1
  ['Tom', 1, 2.3, '元']
  ```

- 列表元素删除 clear() pop() remove() del函数

  ```python
  >>> listColor=['red', 'green', 'yellow']
  >>> len(listColor)
  3
  >>> listColor.clear()	 # 清空元素
  >>> listColor
  []
  ```

  ```python
  >>> listColor=['red', 'green', 'yellow']
  >>> one=listColor.pop()	 # 取出末尾元素并返回
  >>> one
  'yellow'
  >>> listColor
  ['red', 'green']
  >>> listColor.pop(1)	# 取出指定元素并返回
  'green'
  >>> listColor
  ['red']
  ```

  ```python
  >>> listpop=['球1', '球2', '球3', '球2']
  >>> listpop.remove('球2')	# 只删除第1处
  >>> listpop
  ['球1', '球3', '球2']
  ```

  ```python
  >>> del(listpop[2])	 # 删除指定下标元素
  >>> listpop
  ['球1', '球3']
  >>> del(listpop)	# 删除整个列表变量
  >>> listpop
  Error
  ```

- 列表元素合并 extend()、"+"

  ```python
  >>> team1 = ['张三', '李四', '王五']
  >>> team2 = ['Tom', 'Jack', 'John']
  >>> team1.extend(team2)	 # 在末尾添加
  >>> team1
  ['张三', '李四', '王五', 'Tom', 'Jack', 'John']
  ```

  ```python
  >>> id(team1)
  59887904
  >>> team1 = team1 + team2	 # 用“+”后是重建了一个新变量
  >>> id(team1)
  64513888
  >>> team1
  ['张三', '李四', '王五', 'Tom', 'Jack', 'John', 'Tom', 'Jack', 'John']
  ```

- 列表元素排序

  ```python
  >>> fruit = ['banana', 'pear', 'apple', 'peach']
  >>> fruit_1 = fruit.copy()	# 复制
  >>> fruit_1.sort()	# 正序排序
  >>> fruit_1
  ['apple', 'banana', 'peach', 'pear']
  >>> fruit.sort(reverse=True)	# 逆序排序
  >>> fruit
  ['pear', 'peach', 'banana', 'apple']
  ```

- 列标其他操作方法

  用.copy()复制后新变量id不同，用“=”赋值（或初始化）操作后新变量id相同

  ```python
  >>> vegetable = ['白菜', '萝卜', '青菜', '芹菜', '花菜', '白菜']
  >>> id(vegetable)
  53664104
  >>> new_vege = vegetable.copy()
  >>> id(new_vege)
  58214800
  >>> same_list = vegetable
  >>> id(same_list)
  53664104
  ```

  元素在列表中出现次数计数

  ```python
  >>> vegetable.count('白菜')
  2
  ```

  元素倒置

  ```python
  >>> ltom = [9, 8, 7, 6, 5, 4, 2, 1]
  >>> ltom.reverse()
  >>> ltom
  [1, 2, 4, 5, 6, 7, 8, 9]
  >>> vegetable.reverse()
  >>> vegetable
  ['白菜', '花菜', '芹菜', '青菜', '萝卜', '白菜']
  ```

  列表的另一种定义方式

  ```python
  >>> Nums = [i ** 2 for i in range(11) if i > 0]
  >>> Nums
  [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
  ```

### 4.2 基于列表算法

- 冒泡排序

  ```python
  fish_records = [18, 8, 7, 2, 3, 6, 1, 1]
  i = 0	 # 循环控制变量
  compare = 0
  fish_len = len(fish_records)
  while i < fish_len:
      j = 1	 # 循环控制变量
      while j < fish_len - i:
          if fish_records[j-1] > fish_records[j]:
              compare = fish_records[j-1]
        			fish_records[j-1] = fish_records[j]
        			fish_records[j] = compare
              # fish_records[j-1], fish_records[j] = fish_records[j], fish_records[j-1]
      		j += 1
      i += 1
  print(fish_records)
  ```

  ```python
  [1, 1, 2, 3, 6, 7, 8, 18]
  ```

### 4.3  元组 Tuple

- 元组基本知识

  1. 元组只有一个元素时，默认为int、char等原类型；或者说，int、char等基本类型也是特殊的一元元组。元组内元素不可变。

     ```python
     >>> test3 = (1)
     >>> type(test3)
     <class 'int'>
     ```

  2. 用(1,)新建变量，得到元组类型的变量。

     ```python
     >>> type(1,)
     >>> type(test3)
     <class 'tuple'>
     
     >>> name, age = 'tom', 19
     >>> name, age
     ('tom', 19)
     ```

  3. 可用下标调用元组内指定变量。元组内变量可以重复。

     ```python
     >>> test2 = (1, 2, 2, '1', 'a')
     >>> test2[1]
     2
     ```

## 第5章 字典 Dict

### 5.1 接触字典

{键Key:值Value, ...}

字典是可变的序列，键具有唯一性、不可变性。

- 字典的建立、读取、修改、删除

  ```python
  >>> d1 = {1:'Tom', 2:'Jerry', 3:'Jim'}
  >>> d1[1]	 # 读取
  'Tom'
  
  >>> del(d1)	 # 删除元组
  >>> id(d1)
  Error
  
  >>> d2 = {'Tom':20, 'Jack':18, 'Kate':30}
  >>> d2.setdefault('Alice', 12)	# 添加1
  12
  >>> d2
  {'Tom':20, 'Jack':18, 'Kate':30, 'Alice':12}
  >>> d2['Mike'] = 40	 # 添加2
  >>> d2
  {'Tom':20, 'Jack':18, 'Kate':30, 'Alice':12, 'Mike':40}
  
  >>> d2['Mike'] = 39	 # 修改
  >>> d2
  {'Tom':20, 'Jack':18, 'Kate':30, 'Alice':12, 'Mike':39}
  
  >>> del(d2['Mike'])	 # 删除元素
  >>> d2
  {'Tom':20, 'Jack':18, 'Kate':30, 'Alice':12}
  ```

- 遍历字典值、判断字典值、清除字典元素

  ```python
  >>> d2 = {'Tom':20, 'Jack':18, 'Kate':30, 'Alice':12}
  >>> for get in d2.items():	# 遍历字典值
    			print(get)
  ('Tom', 20)
  ('Jack', 18)
  ('Kate', 30)
  ('Alice', 12)
  
  >>> if 'Jack' in d2.keys():	 #判断字典值
    			print(d2['Jack'])
  18
  
  >>> d2.clear()	# 清除字典元素
  >>> d2
  {}
  ```

## 第6章 函数 Function

### 6.1 函数基本知识

```
def 函数名 ([参数]):
		函数体
		[return 返回值]
```

### 6.2 自定义函数第一步

- 求10的因数

  ```python
  def factor_no_para():	 # 不带参数的求因数的自定义函数
  		i = 1
      nums = 10
      print('%d的因数是：' % (nums))
      while i <= nums:
        	if nums % i == 0:
          		print('%d' % (i))
          i += 1
  factor_no_para()	# 调用自定义函数
  tt = type(factor_no_para)	 # 检查是否是函数类型
  print(tt)	 # 打印tt类型
  ```

- 求任意数字的因数

  ```python
  def find_factor(nums):	# 带参数的求因数的自定义函数
    	i = 1
    	str1 = ''
    	print('%d的因数是：' % (nums))
    	while i <= nums:
      		if nums % i == 0:
        			str1 = str1 + ' ' + str(i)
      		i += 1
    	print(str1)
  num2_L = [10, 15, 18, 25]
  i = 0
  num_len = len(num2_L)
  while i < num_len:
    	find_factor(num2_L[i])
      i += 1
  ```

### 6.3 自定义函数第二步

1. 位置参数 positional argument

   ```python
   def test1(name, age):
   		print('姓名%s,年龄%s' % (name, str(age)))
   test1('Tom', 11)
   ```

2. 关键字参数 keyword argument

   ```python
   test1(name='John', age=20)
   test1('John', age=20)
   ```

   传递参数时，关键字参数必须放在位置参数后面；且不能重复对同一个参数赋值。

3. 默认值

   ```python
   def test1(name='', age=20):
   		print('姓名%s,年龄%s' % (name, str(age)))
   test1('Tom', 11)
   test1(18)
   ```

   默认值参数必须放在非默认值参数后面。

4. 不定长参数*、**

   ```python
   def watermelon(name, *attributes):
   		print(name)
   		print(type(attributes))
   		description = ''
   		for get_t in attributes:
   				description += '' + get_t
   		print(description)
   watermelon('西瓜', '甜', '圆形', '绿色')
   print('--------------------------')
   watermelon('西瓜', '甜', '圆形', '绿皮', '红瓤', '无籽')
   ```

   ```
   西瓜
   <class 'tuple'>
    甜 圆形 绿色
   --------------------------
   西瓜
   <class 'tuple'>
    甜 圆形 绿皮 红瓤 无籽
   ```

   - 不定长参数前加*、**表示。

   - *用于接收位置参数的剩余值，类型是元组；**用于接收关键字参数的默认值，类型是字典。

   - 在函数定义中，可以有\*没有\*\*，也可以有\*没有\**；当都出现时，**类参数要放在\*类型参数的后面。

   ```python
   def test1(mame, *other1, **other2):
     	print(name, other1, other2)
   test1('kan', 1,2,3,4, a='a')
   ```

   ```
   kan (1, 2, 3, 4) {'a': 'a'}
   ```

## 第7章 类

### 7.1 初识类

```python
class Box():
  	'''求立方体的类'''
  	def __init__(self, length1, width1, height1):	# 默认传递类参数额保留函数__init__；self代表实例对象,在实例调用时传递实例对象
    		self.length = length1
        self.width = width1
        self.height = height1
        
    def volume(self):	 # 求立方体体积的函数volume
      	return self.length * self.width * self.height
      
my_box = Box(10, 10, 10)
print(my_box.volume)
```

### 7.2 属性使用

属性初始化的两种方法

1. 在\_\_init\_\_里直接初始化

   ```python
   class Box():
     	'''求立方体的类'''
     	def __init__(self):	# 默认传递类参数额保留函数__init__
       		self.length = 0
           self.width = 0
           self.height = 0
           
       def volume(self):	 # 求立方体体积的函数volume
         	return self.length * self.width * self.height
         
   my_box = Box()
   my_box.length = 10
   my_box.width = 10
   my_box.height = 10
   print(my_box.volume)
   ```

   可以通过对象直接访问和修改它的参数（即length width height等）。即，默认公有。

2. 传递参数初始化

   此方式例程见7.1。

   可以通过对象直接新建类定义中没有的新参数，并通过此对象调用。

   ```python
   my_box.haha = 6
   print(my_box.haha)
   ```

### 7.3 类改造问题

继承、重写方法

**继承**inheritance 继承原有类功能的基础上，增加新的功能（属性或方法），形成新的**子类**。被继承的叫**父类**。

```python
class Box1():	# 定义父类
  	'''求立方体的类'''
  	def __init__(self, length1, width1, height1):
    		self.length = length1
        self.width = width1
        self.height = height1
      
    def volume(self):	 # 求立方体体积的函数volume
      	return self.length * self.width * self.height
      
      
class Box2(Box1):	# 继承Box1定义子类Box2
  	def __init__(self, length1, width1, height1):	 # 此处的属性（参数）至少要包括父类的
      	super().__init__(length1, width1, height1)	 # 因为父类的构造函数已经被覆盖，故用super()显式地调用父类的构造函数
    		self.color='white'
        self.material='paper'
        self.type='fish'
      
    def area(self):
      	return self.length * self.width * self.height  
      
my_box = Box(10, 10, 10)
print(my_box.volume())
```

子类的子函数会完全覆盖父类的同名函数。只要函数名相同，即使两者参数不同，也不会出现重载。

在子类的定义中可以显式地调用父类。

### 7.4 私有

欲将**变量**或**函数**变成私有，可在前面加**双下划线**__

```python
class Box():
  	'''求立方体的类'''
  	def __init__(self, length1, width1, height1):
    		self.length = length1
        self.width = width1
        self.height = height1
      
    def volume(self):
      	return self.length * self.width * self.height
      
      
class Box1(Box):
  	def __init__(self, length1, width1, height1):
      	super().__init__(length1, width1, height1)
    		self.__name = 'three cool cats'
      
    def volume(self, num=1):
      	self.__showName()
      	return self.length * self.width * self.height
      
    def __showName(self):
      	print(self.__name)
        
        
my_box = Box(10, 10, 10)
my_box1 = Box1(11, 12, 13)

my_box1.__name = 'fff'	# 不能直接访问私有变量，这里实际上是新建了一个新变量
# my_box1.__showName()  # Error 不能直接调用私有函数

print(my_box.volume())
print(my_box1.volume())
```

```
1000
three cool cats
1716
```

### 7.5 把类放到模块中

为了让类可以共享，把类放入模块中。两个好处：减少代码的重复；便于更新。

假设Box在Box.py文件中，可通过

```python
from Box import *
```

来调用它。

### 7.6 类回顾

**动态类**（Dynamic Class） 可以创建实例的类。

**静态类**（Static Class） 不支持实例的类。

定义变量时不需要使用self；也不需要有\_\_init\_\_构造函数。

```python
class StaticC():
  	name = 'Tom'				# 类局部变量
    age = 20
    address = 'China'
    call = 28380000
    
    def a():	# 没有self参量，不能叫方法，只能叫函数
      	i = 0
        i += 1
        print('第一个函数%d' % (i))
        
    def b(add=1):
      	print('第二个函数%d' % (add))
        
   	def c(add=1):
      	print('第三个函数%d' % (add))
        return add
      
     
StaticC.c()
```

静态类可以理解为一个工具类，将一系列的变量和函数封装成了一个工具包，

动态类可以创建实例，实例具有属性和方法。

## 第8章 标准库

### 8.1 python标准库知识

**Python语言标准库**（Stantard Library） 内置了大量的函数，是python解释器的核心功能之一。

打开Python手册（Tutorial）的方法：Python IDLE --> Help --> Python Docs --> The Python Standard Library --> Built-in Functions内置函数、常量、类型、基本类

### 8.2 datetime模块

创建日期和时间

```
datetime.now()								  获取当天的日期和时间
datetime.date(t)								获取当天的日期，t为datetime实例参数（下同）
datetime.time(t)								获取当天的时间
datetime.ctime(t)								获取“星期,月,日,时,分,秒,年”格式的字符串
datetime.utcnow()								获取当前的UTC日期和时间（北京是UTC+8）
datetime.timestamp(t)						获取当天的时间戳（Unix时间戳）
datetime.fromtimestamp(t_tamp)	根据时间戳返回UTC日期时间；t_tamp为时间戳浮点数
datetime.combine(date1, time1)	绑定日期、时间，生成新的datetime对象；date1为日期对象，time1为时间对象
datetime.strptime(dt_str, sf)		根据字符串和指定格式生成新的datetime对象；dt_str为字符串日期时间，sf为指定格式
datetime.timetuple(t)						把datetime对象所有属性转为时间元组对象
t.isocalendar()									获取ISO格式的日期（元组格式）
t.strftime(dt_str_format)				获取自定义格式的日期时间字符串，dt_str_format指定格式
```

```python
from datetime import datetime,date,time

print(datetime.now())		# 返回当天的日期和时间
today = datetime.now()
print(datetimr.date(today))		# 返回当天的日期
print(datetime.time(today))		# 返回当天的时间

print(datetime.ctime(today))	# 返回“星期,月,日,时,分,秒,年”格式的字符串
print(datetime.utcnow())			# 返回当前的UTC日期和时间
print(datetime.timestamp(today))	# 返回当天的时间戳
print(datetime.fromtimestamp(datetime.timestamp(today)))	# 根据时间戳返回 UTC datetime

date1 = date(2018, 2, 12)
time1 = time(20, 53, 48)
print(datetime.combine(date1, time1))	 # 绑定日期，时间，生成新的datetime对象

newDatetime = datetime.strptime("12/2/18 20:59", '%d/%m/%y %H:%M')	# 用字符串和指定格式生成新的datetime对象
print(newDatetime)

for tv in datetime.timetuple(today):
  	print(tv)
print(today.isocalendar())	# ISO格式的日期
print(today.strftime("%Y年%m月%d日 %H:%M:%S %p"))
```

```
2019-08-03 14:38:51.615660
2019-08-03
14:38:51.635642
Sat Aug  3 14:38:51 2019
2019-08-03 06:38:51.679616
1564814331.635642
2019-08-03 14:38:51.635642
2018-02-12 20:59:00
2019
8
3
14
38
51
5
215
-1
(2019, 31, 6)
2019年08月03日 14:38:51 PM
```

### 8.3 math模块

```python
>>> import math
>>> math.log2(2)
1.0
>>> math.log(9, 3)
2.0
>>> math.sin(30)
-0.9880316240928618
>>> math.pi
3.141592653589793
>>> math.sin(math.pi/2)
1.0
>>> math.sqrt(4)
2.0
>>> math.fbas(-10)	# 绝对值
10.0
>>> math.ceil(0.15)	# 向上取整
1
>>> math.floor(0.15)	# 向下取整
0
```

### 8.4 random模块

随机函数，用于生成一系列随机数计算均值、正态（高斯）分布、对数正态分布、伽玛（Gamma）分布和贝塔（Beta）分布。

```python
>>> import random
>>> random.random()	# 在0-1之间随机产生一个实数（随后不再改变）
0.7480237362897358
>>> random.uniform(-10, -1)	 # 在给定[a, b)区间内随机产生一个实数
-1.6864730982183342
>>> import math
>>> math.floor(random.uniform(0,9))	 # 叠加取整函数，在给定[a, b)区间内随机产生一个整数
0
>>> random.randint(0, 9)	# 在给定[a, b]区间内随机产生一个整数
9
>>> random.choice("abc")	# 在给定的可迭代的区间内随机选择一个元素
'a'
>>> random.choice([1, 2, 3])
2
>>> random.triangular()
0.7529027373677091
>>> random.triangular(0, 10)
4.473775632796311
```

### 8.5 os模块

os模块为多操作系统的访问提供了相关功能支持，便于忽略操作系统的区别而使用相同方法。

```python
>>> import os	 # 以我的MacBook Air(MacOS11)为例
>>> os.cpu_count()	# cpu个数
4
>>> os.curdir	 # 当前所在目录
'.'
>>> os.defpath	# 可执行文件的默认搜索路径
'/bin:/usr/bin'
>>> os.urandom(10)	# 返回一个随机字符，随机生成一个加密的数字，用于设备加密（此处老师口胡，不清楚）
b'6\xd3|q\xe5\x9f\xe0\xf0<\xed'
>>> os.path.abspath(os.curdir)	# 返回给定path规范化的绝对路径
'/Users/shengjie'
>>> d = os.path.abspath(os.curdir)
>>> os.path.dirname(d)	# 返回路径的目录
'/Users'
>>> os.path.basename(d)	# 返回路径的最后的文件名
'shengjie'
```

### 8.6 sys模块

sys模块提供了跟Python解释器紧密相关的一些变量和函数。

```python
>>> import sys	# 以我的MacBook Air(MacOS11)为例
>>> sys.path
['', '/Users/shengjie/opt/anaconda3/lib/python38.zip', '/Users/shengjie/opt/anaconda3/lib/python3.8', '/Users/shengjie/opt/anaconda3/lib/python3.8/lib-dynload', '/Users/shengjie/opt/anaconda3/lib/python3.8/site-packages', '/Users/shengjie/opt/anaconda3/lib/python3.8/site-packages/aeosa']
>>> sys.api_version
1013
>>> sys.copyright
'Copyright (c) 2001-2020 Python Software Foundation.\nAll Rights Reserved.\n\nCopyright (c) 2000 BeOpen.com.\nAll Rights Reserved.\n\nCopyright (c) 1995-2001 Corporation for National Research Initiatives.\nAll Rights Reserved.\n\nCopyright (c) 1991-1995 Stichting Mathematisch Centrum, Amsterdam.\nAll Rights Reserved.'
>>> sys.prefix
'/Users/shengjie/opt/anaconda3'
>>> sys.platform
'darwin'
>>> sys.exit()	# 在命令行退出python
```

### 8.7 time模块

```python
>>> import time
>>> time.sleep(5)	 # 休眠模块
>>> time.clock()
0.0
>>> time.strftime('上午%H时：%M分：%S秒')
'上午10时：27分：29秒'
>>> time.time()	 # 返回时间戳
1627266467.595265
>>> type(time.time())
<class 'float'>

>>> import datetime
>>> tt1=datetime.datetime.timestamp(datetime.datetime.now())
>>> tt1
1627266660.676132
>>> type(tt1)
<class 'float'>	 # 使用datetime模块和time模块返回的时间戳类型相同
```

### 8.8 再论模块

**模块**：标准库模块、自定义模块（函数模块、主程序模块、类模块）

**包**：将模块组成分类的汇总/集合

引入包的三种方法：

1. 直接将包复制到源目录下

   ```python
   >>> import sys
   >>> sys.path
   ['', '/Users/shengjie/opt/anaconda3/lib/python38.zip', '/Users/shengjie/opt/anaconda3/lib/python3.8', '/Users/shengjie/opt/anaconda3/lib/python3.8/lib-dynload', '/Users/shengjie/opt/anaconda3/lib/python3.8/site-packages', '/Users/shengjie/opt/anaconda3/lib/python3.8/site-packages/aeosa']
   # 将对应的包复制到路径下
   >>> exit()
   
   >>> import package.Cat.Cat_Main
   OK
   Go!
   ```

2. 将包所在路径添加到path

   可避免复制文件对原路径文件夹的破坏。

   ```python
   >>> import sys
   >>> sys.path
   ['', '/Users/shengjie/opt/anaconda3/lib/python38.zip', '/Users/shengjie/opt/anaconda3/lib/python3.8', '/Users/shengjie/opt/anaconda3/lib/python3.8/lib-dynload', '/Users/shengjie/opt/anaconda3/lib/python3.8/site-packages', '/Users/shengjie/opt/anaconda3/lib/python3.8/site-packages/aeosa']
   >>> sys.path.append('(你的路径)')
   ```

3. 修改path的第0号地址为包所在路径

   ```python
   >>> import sys
   >>> sys.path[0] = '(你的路径)'
   ```

### 8.9 窥探标准库源码

## 第9章 异常

### 9.1 程序中的问题

1. 低级错误，代码语法出错

   低级错误指纯语法错误，代码主要在编写、调试阶段就报错。

2. 中级错误，代码存在隐性错误

   隐形错误主要指代码编写存在逻辑错误或缺陷，当程序满足特定数据处理条件时，报错或给出错误答案。（比较致命）

3. 高级错误，软件面对不确定性的异常错误

   高级错误指不确定性的异常错误，主要指软件的代码本身没有问题。所输入的数据也能得到控制或保证，而是在运行过程中环境所带来的不确定性异常。（考验鲁棒性 异常监控）

### 9.2 捕捉异常

1. 基本异常捕捉语句语法

   ```python
   try:
   		代码模块1
   except:
   		代码模块2
   ```

   若代码模块1执行中出错，则代码模块1后续代码不再执行，转入except处理。except捕捉异常信息，提示出错信息或处理出错后事项，异常处理结束。

   例：

   ```python
   def print_D(dic):
     	i = 0
       try:
         	len1 = len(dic)
           while i < len1:
             	print(dic.popitem())
               i += 1
       except:
         	print("传递值类型出错，必须为字典型！")
           
   print_D({1:'a', 2:'b'})	 # 正常字典对象
   print_D([1, 2, 3])	 		 # 错误字典对象
   ```

   ```
   (2, 'b')
   (1, 'a')
   传递值类型出错，必须为字典型！
   ```

2. 进阶异常捕捉语句语法

   ```python
   try:
   		# 主代码块
   		pass
   except KeyError as e:
     	# 如果发生异常，异常时，执行该块
       pass
   else:	 # 如果没有异常
     	# 主代码块执行完，执行该块
       pass
   finally:
     	# 无论异常与否，最终执行该块
   pass
   ```

   修改上例；

   ```python
   def print_D(dic):
     	i = 0
       try:
         	len1 = len(dic)
           while i < len1:
             	print(dic.popitem())
               i += 1
       except:
         	print("传递值类型出错，必须为字典型！")
       else:
         	print("No Error")
       finally:
         	print("Must be executed")
           
   print_D({1:'a', 2:'b'})	 # 正常字典对象
   print_D([1, 2, 3])	 		 # 错误字典对象
   ```

   一些异常

   ```python
   Exception					万能异常
   AttributeError		试图访问一个对象没有的属性，比如foo.x，但是foo没有属性x
   IOError						输入/输出异常：基本上是无法打开文件
   ImportError				无法引入模块或包：基本上是路径问题或名称错误
   IndentationError	语法错误（的子类）：代码没有正确对齐
   IndexError				下标索引超出序列边界，比如当x只有三个元素，却试图访问x[5]
   KeyError					试图访问字典里不存在的键
   KeyboardInterrupt	Ctrl+C被按下
   NameError					使用一个还未被赋予对象的变量
   SyntaxError				Python代码非法，代码不能编译（可能是语法错误，写错了）
   TypeError					传入对象类型与要求的不符合
   UnboundLocalError	试图访问一个还未被设置的局部变量，基本上是由于另有一个同名的全局变量，导致你以为正在访问它
   ValueError				传入一个调用者不期望的值，即使值的类型是正确的
   ```

### 9.3 抛出异常

```python
>>> i = '1'
>>> if type(i) != int:
...			raise TypeError('i类型出错！')
    
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
TypeError: i类型出错！
```

```python
class HelloException(Exception):
  	def __init__(self.msg):
      	self.message = msg
        
    def __str__(self):
      	return self.message
      
try:
  	raise HelloException('我的异常')
except HelloException as e:
  	print(e)
```

```
我的异常
```

## 第10章 文件处理

### 10.1 文本文件

- 建立文件

  ```python
  newfile = r'd:\t1.txt'	# 打开文件
  b_new_file = open(newfile, 'w')	# ‘w’表示只写 如果文件不存在，则新建；若存在，则清空原有内容
  b_new_file.close()	# 关闭文件
  print("%s成功建立！" % (newfile))
  ```

  文件的打开模式：w, r, a（只写，追加方式，append）

  ```python
  f.tell()	# r模式下，返回当前“光标”所在位置数
  num = f.read()	# 读光标到末尾的内容（流输入输出）
  f.seek(2)	 # 移动光标至指定位置
  ```

- 基本的读写文件

  ```python
  # 往文件里写内容
  newfile = r'd:\t1.txt'					# 定义需要建立的文本名称和路径
  b_new_file = open(newfile, 'w')	# 用open函数建立一个新的文本文件
  t_n = b_new_file.write('I like python!')	# 用文件对象write()方法写字符串
  b_new_file.close()							# 用close()方法关闭新建的文件
  print("往文件里写入%d字节内容" % (t_n))	 # 提示写文本文件内容成功
  # 往文件里读内容
  b_new_file = open(newfile, 'r')
  ```

  
