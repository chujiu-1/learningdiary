用Python编写函数：输⼊变量n，输出形如{1:1, … ,n: n*n} 的字典。

例如当n=8时，输出{1: 1，2: 4, 3: 9, 4: 16, 5:25, 6: 36, 7: 49, 8: 64}

```python
def input_dict(n):
    list = range(1,n+1)  # 创建一个从1到n的list
    d = {}               # 创建一个字典
    n = 1
    for n in list :
        d[n] = n**2      # 对应key值为n方
    return d

print(input_dict(8))
```

