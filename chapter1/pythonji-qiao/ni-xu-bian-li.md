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
