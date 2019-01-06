# Shell 通配符

## 符号

|字符|	含义|
|---|---|
|*	|匹配 0 或多个字符|
|?	|匹配任意一个字符|
|[list]	|匹配 list 中的任意单一字符|
|[!list]	|匹配 除list 中的任意单一字符以外的字符|
|[c1-c2]	|匹配 c1-c2 中的任意单一字符 如：[0-9] [a-z]|
|{string1,string2,...}	|匹配 sring1 或 string2 (或更多)其一字符串|
|{c2..c2}	|匹配 c1-c2 中全部字符 如{1..10}|

## 例子

```shell
touch love_{1..10}_linux.txt

ls *.txt
```

## 参考

<https://my.oschina.net/u/2435120/blog/632345>
