##逆序遍历
```py
a = [1,3,6,8,9]

print("通过下标逆序遍历1：")
for i in a[::-1]:
    print(i, end=" ")
    
print("\n通过下标逆序遍历2：")
for i in range(len(a)-1,-1,-1):
    print(a[i], end=" ")
    
print("\n通过reversed逆序遍历：")
for i in reversed(a):
    print(i, end=" ")
```
运行结果

```py
通过下标逆序遍历1：
9 8 6 3 1 
通过下标逆序遍历2：
9 8 6 3 1 
通过reversed逆序遍历：
9 8 6 3 1 
```

如果你需要遍历数字序列，可以使用内置range()函数。它会生成数列。



range()语法：

range(start,end,step=1):顾头不顾尾



正序遍历：

range(10):默认step＝1，start＝0,生成可迭代对象，包含[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
range(1,10):指定start＝1，end＝10，默认step＝1，生成可迭代对象，包含[1, 2, 3, 4, 5, 6, 7, 8, 9]
range(1,10,2):指定start＝1，end＝10，step＝2，生成可迭代对象，包含[1, 3, 5, 7, 9]
逆序遍历：
range(9,-1,-1):step＝-1，start＝9,生成可迭代对象，包含[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

```py
for i in range(9, -1, -1):
    print(i)
```
