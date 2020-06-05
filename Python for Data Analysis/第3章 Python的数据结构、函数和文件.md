[toc]
Python最基础的数据结构：元组、列表、字典和集合
## 3.1 数据结构和列表
### 元组：固定长度，不可改变的Python序列对象
+ 元组中存储的对象可能是可变对象
  + 一旦创建了元组，元组中的对象就不能修改了
  + 如果元组中的某个对象是可变的，比如列表，可以在原位进行修改
  + 元组乘以一个整数，像列表一样，会将几个元组的复制串联起来，对象本身并没有复制，只是引用了它
#### 拆分元组
#### tuple方法
### 列表
与元组对比，列表的长度可变、内容可以被修改
#### 添加和删除元素
+ 添加
  + append：添加至列表末尾
  + insert：添加至指定位置
+ 删除
  + pop：删除列表末尾元素
  + remove：删除指定位置元素
+ 检查
  + in：检查列表是否包含某个值
  + not in：检查列表是否**不**包含某个值
**在列表中检查是否存在某个值*远*比字典和集合速度慢，因为Python是线性搜索列表的值**
#### 串联和组合列表
+ 串联
```python
[4, None, 'foo'] + [7, 8, (2, 3)]
>>> [4, None, 'foo', 7, 8, (2, 3)]
```
+ 追加
```python
x = [4, None, 'foo']
x.extend([7, 8, (2, 3)])
>>> [4, None, 'foo', 7, 8, (2, 3)]
```
+ append与extend区别
```python
x = [4, None, 'foo']
x.append([7, 8, (2, 3)])
>>> [4, None, 'foo', [7, 8, (2, 3)]]
```
#### 排序
使用sort函数将一个列表原地排序（**不创建新的对象**）
```python
a = [7, 2, 5, 1, 3]
a.sort()
>>> [1, 2, 3, 5, 7]
b = ['saw', 'small', 'He', 'foxes', 'six']
b.sort(key=len)
>>> ['He', 'saw', 'six', 'small', 'foxes']
```
#### 二分搜索和维护已排序的列表
bisect模块支持二分查找，和向已排序的列表插入值
+ bisect.bisect可以找到插入值后仍保证排序的位置
+ bisect.insort是向这个位置插入值
#### 切片
+ 切片包含起始元素，不包含结束元素
+ 负数表明从后向前切片
+ 第二个冒号后面的step表示切片步长
#### 序列函数
+ enumerate函数：返回（i,value）元组序列
+ sorted函数：从任意序列的元素返回一个新的排好序的列表
  + sorted函数可以接受和sort相同的参数
+ zip函数：将多个列表、元组或其他序列成对组合成一个元组列表
  + 可以处理任意多的序列，元素的个数取决于最短的序列
  + 同时迭代多个序列，可结合enumerate使用
  + 给出⼀个“被压缩的”序列，zip可以被⽤来解压序列。也可以当作把⾏的列表转换为列的列表。
```python
seq1 = ['foo', 'bar', 'baz']
seq2 = ['one', 'two', 'three']
zipped = zip(seq1, seq2)
list(zipped)
>>> [('foo', 'one'), ('bar', 'two'), ('baz', 'three')]
seq3 = [False, True]
list(zip(seq1, seq2, seq3))
>>> [('foo', 'one', False), ('bar', 'two', True)]
for i, (a, b) in enumerate(zip(seq1, seq2)):
    print('{0}: {1}, {2}'.format(i, a, b))
>>> 0: foo, one
    1: bar, two
    2: baz, three
pitchers = [('Nolan', 'Ryan'), ('Roger', 'Clemens'), ('Schilling', 'Curt')]
first_names, last_names = zip(*pitchers)
first_names, last_names
>>> (('Nolan', 'Roger', 'Schilling'), ('Ryan', 'Clemens', 'Curt'))
```
+ reversed函数
  + reversed是一个生成器，只有实例化（即列表或for循环）之后才能创建翻转的序列
### 字典
使用del关键字或pop方法（返回值的同时删除键）删除值
keys和values是字典键和值的迭代器方法。虽然键值对没有顺序，但可以用相同的顺序输出键和值
用update方法可以将一个字典和另一个融合
```python
# update方法是原地改变字典，任何传递给update的键的旧的值都会被舍弃
d1 = {'a': 'some value', 'b': [1, 2, 3, 4], 7: 'an integer'}
d1.update({'b': 'foo', 'c': 12})
d1
>>> {'a': 'some value', 'b': 'foo', 7: 'an integer', 'c': 12}
```

