



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

- 常见的几种函数：

  ```python
  ().real //检测负数实部
  ().imag //检测负数虚部
  bin()   //将十进制数转换为二进制数
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

### 6.3 自定义函数第一步

1. 位置参数

   ```python
   def test1(name, age):
   		print('姓名%s,年龄%s' % (name, str(age)))
   test1('Tom', 11)
   ```

2. 关键字参数

   ```python
   test1(name='John', age=20)
   test1('John', age=20)
   ```

3. 默认值

   ```python
   def test1(name='', age=20):
   		print('姓名%s,年龄%s' % (name, str(age)))
   test1('Tom', 11)
   test1(18)
   ```

4. 不定长参数*、**

