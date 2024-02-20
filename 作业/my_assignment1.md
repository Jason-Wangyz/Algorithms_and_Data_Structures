# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2024 spring, Complied by Wang Yuzhe from the School of Physics



**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

==（请改为同学的操作系统、编程环境等）==

操作系统：Windows 11

Python编程环境：Pycharm Community Edition 2022.3



## 1. 题目

### 20742: 泰波拿契數

http://cs101.openjudge.cn/practice/20742/



思路：



##### 代码

```python
from functools import lru_cache


@lru_cache(maxsize=None)
def t(m):
    if m == 0:
        return 0
    if m == 1 or m == 2:
        return 1
    else:
        return t(m-1) + t(m-2) + t(m-3)


n = int(input())
print(t(n))
```



代码运行截图 

![image-20240220151807956](C:\Users\王宇哲\AppData\Roaming\Typora\typora-user-images\image-20240220151807956.png)



### 58A. Chat room

greedy/strings, 1000, http://codeforces.com/problemset/problem/58/A



思路：



##### 代码

```python
s = input()
lst = ['h', 'e', 'l', 'l', 'o']
index = 0
for i in range(len(s)):
    if index > 4:
        break
    if s[i] == lst[index]:
        index += 1
if index == 5:
    print("YES")
else:
    print("NO")
```



代码运行截图 

![image-20240220152820122](C:\Users\王宇哲\AppData\Roaming\Typora\typora-user-images\image-20240220152820122.png)



### 118A. String Task

implementation/strings, 1000, http://codeforces.com/problemset/problem/118/A



思路：



##### 代码

```python
s = input().lower()
vowels = {'a', 'o', 'y', 'e', 'u', 'i'}
rest = []
for i in range(len(s)):
    if s[i] not in vowels:
        rest.append(s[i])
for i in range(len(rest)):
    print(f".{rest[i]}", end='')
```



代码运行截图

![image-20240220153741470](C:\Users\王宇哲\AppData\Roaming\Typora\typora-user-images\image-20240220153741470.png)



### 22359: Goldbach Conjecture

http://cs101.openjudge.cn/practice/22359/



思路：



##### 代码

```python
n = int(input())
is_prime = [True] * (n+1)
prime = set()


def eratosthenes(m):
    is_prime[0] = is_prime[1] = False
    for i in range(2, m+1):
        if is_prime[i]:
            prime.add(i)
            if i * i > m:
                continue
            for j in range(i*i, m+1, i):
                is_prime[j] = False


eratosthenes(n)
for i in range(1, n//2):
    if i in prime and n - i in prime:
        print(i, n - i)
        break
```



代码运行截图 

![image-20240220155224613](C:\Users\王宇哲\AppData\Roaming\Typora\typora-user-images\image-20240220155224613.png)



### 23563: 多项式时间复杂度

http://cs101.openjudge.cn/practice/23563/



思路：



##### 代码

```python
polynomial = list(input().split('+'))
ma = 0
for i in range(len(polynomial)):
    para, exp = polynomial[i].split('n^')
    if para != '0' and int(exp) > ma:
        ma = int(exp)
print(f"n^{ma}")
```



代码运行截图

![image-20240220160238954](C:\Users\王宇哲\AppData\Roaming\Typora\typora-user-images\image-20240220160238954.png)



### 24684: 直播计票

http://cs101.openjudge.cn/practice/24684/



思路：



##### 代码

```python
from collections import defaultdict
s = list(map(int, input().split()))
vote = defaultdict(int)
for i in range(len(s)):
    vote[s[i]] += 1
vote_list = []
for k, v in vote.items():
    vote_list.append((v, k))
vote_list.sort(reverse=True)
ans = []
i = 0
while i < len(vote_list) and vote_list[i][0] == vote_list[0][0]:
    ans.append(vote_list[i][1])
    i += 1
print(' '.join(map(str, sorted(ans))))
```



代码运行截图 

![image-20240220162513983](C:\Users\王宇哲\AppData\Roaming\Typora\typora-user-images\image-20240220162513983.png)



## 2. 学习总结和收获

这次作业里的题目在上学期和寒假都做过，这次又重新写了一遍，完成的比较快。本学期要在数算上多投入些时间，尽量紧跟群内大佬进度，希望能有更大收获。





