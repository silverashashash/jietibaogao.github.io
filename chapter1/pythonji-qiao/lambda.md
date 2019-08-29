## python3 中用lambda函数的自定义排序

[https://blog.csdn.net/u010758410/article/details/79737498](https://blog.csdn.net/u010758410/article/details/79737498)

* 相关题目见 two-sum-difference-equals-to-target
* [https://www.jiuzhang.com/solution/two-sum-difference-equals-to-target\#tag-highlight-lang-python](https://www.jiuzhang.com/solution/two-sum-difference-equals-to-target#tag-highlight-lang-python)

当待排序列表的元素由多字段构成时，我们可以通过sorted\(iterable，key，reverse\)的参数key来制定我们根据那个字段对列表元素进行排序。

`key=lambda 元素: 元素[字段索引]`

例如：想对元素第二个字段排序，则

`key=lambda y: y[1] 备注：这里y可以是任意字母，等同key=lambda x: x[1]`

看几个简单的例子。

```py
listA = [3, 6, 1, 0, 10, 8, 9]
print(sorted(listA))
listB = ['g', 'e', 't', 'b', 'a']
print(sorted(listB))
print(sorted(listB, key=lambda y: y[0]))
listC = [('e', 4), ('o', 2), ('!', 5), ('v', 3), ('l', 1)]
print(sorted(listC, key=lambda x: x[1]))
```

```py
#结果一
[0, 1, 3, 6, 8, 9, 10]
#结果二
['a', 'b', 'e', 'g', 't']
['a', 'b', 'e', 'g', 't']
#结果三
[('l', 1), ('o', 2), ('v', 3), ('e', 4), ('!', 5)]
```



