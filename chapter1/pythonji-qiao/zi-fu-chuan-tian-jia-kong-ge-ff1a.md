##字符串添加空格
####Word break II 
```
Input："lintcode"，["de","ding","co","code","lint"]
Output：["lint code", "lint co de"]
Explanation：
insert a space is "lint code"，insert two spaces is "lint co de".

```



```py
results.append(' '.join(word) ) 

```
效果是把每个 element 之间加空格



