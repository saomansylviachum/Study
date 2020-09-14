# Python Challenge3 词频统计

给了一大段字符，需要找出这一大段字符中出现频率最低的。

## 解决问题

1. 将这一大段字存在文件夹中
2. 读取文件夹 open readline
3. 记得将\n进行替换
4. 记得考虑dict中是否有键值 key in dic.keys() or dic.haskey(key)



```python
def count(str,dic):
    for i in str:
        dic[i]=dic[i]+1 if i in dic.keys() else 1
    return dic

file=open("./source_3.txt",'r')
dic=dict()
for line in file:
    line.strip()
    dic=count(line,dic)
dic
```

5. 排序

   sorted(iterable,key,reverse)

   ```python
   sorted(dic.keys())
   sorted(dic.items(),key=lambda item:item[1])
   ```

   