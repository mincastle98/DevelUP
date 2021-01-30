# **zip & enumerate**

### for문에서 유용하게 사용되는 내장함수 2가지

1. zip()
2. enumerate()

#

## 1. zip()

: 동일한 개수로 이루어진 자료형을 묶어주는 역할을 하는 함수이다.

```python
aList = ['a', 'b', 'c']
bList = ['1', '2', '3']

print( zip(aList, bList) )
print( list(zip(aList, bList)) )
```

> <zip object at 0x7ff2917845f0>  
> [('a', '1'), ('b', '2'), ('c', '3')]

`zip()`은 zip 객체를 return하기 때문에 확인이 필요한 경우에는 list 혹은 set과 같은 sequence 객체로 변환하는 과정이 필요하다.

---

```python
aList = ['a', 'b', 'c']
bList = ['1', '2', '3', '4']

print( list(zip(aList, bList)) )
```

> [('a', '1'), ('b', '2'), ('c', '3')]

서로 다른 길이의 객체를 주어졌을 때는 가장 짧은 길이의 객체를 기준으로 zip 객체가 만들어진다.

---

```python
print( list(zip()) )
```

> []

아무런 parameter도 주어지지 않은 경우에는 빈 list를 return한다.

---

`zip(*)`을 이용하면 이중 list를 풀어 원소들이 모여잇는 tuple로 변환할 수 있다.

```python
li = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

print( list(zip(*li)) )
print( list(zip(li[0], li[1], li[2])) )
```

> [(1, 4, 7), (2, 5, 8), (3, 6, 9)]  
> [(1, 4, 7), (2, 5, 8), (3, 6, 9)]

`zip(*...)`을 사용하면 `li` 내의 list들을 나열하여 `zip(...)`을 실행시킨 것과 동일한 결과를 얻는 것을 볼 수 있다.

---

```python
aList = [1, 2, 3]
bList = [4, 5, 6]
sum = []

for a, b in zip(aList, bList):
    sum.append(a + b)

print( sum )
```

> [5, 7, 9]

동시에 여러 list의 값들을 돌며 for문을 진행하고 싶을 때 다음과 같이 `zip()`을 활용할 수 있다.

#

## 2. enumerate()

: 순서가 있는 자료형(list, tuple, str)을 입력받아 index와 value를 묶어주는 역할을 하는 함수이다.

```python
li = ['a', 'b', 'c']

print( enumerate(li) )
print( list(enumerate(li)) )
```

> <enumerate object at 0x7f800bf845f0>  
> [(0, 'a'), (1, 'b'), (2, 'c')]

`enumerate()` 역시 enumerate 객체를 return하기 때문에 확인이 필요한 경우 `zip()`과 동일하게 list 혹은 set과 같은 sequence 객체로 변환하는 과정이 필요하다.

`enumerate()`는 index, value 순으로 값이 묶여서 return된다.

---

`enumerate()`는 for문에서 주로 사용된다.

```python
li = ['a', 'b', 'c']

li_ = []
for idx, val in enumerate(li):
    li_.append((idx, val))
print(li_)

li_ = []
for idx in range(len(li)):
    li_.append((idx, li[idx]))
print(li_)
```

> [(0, 'a'), (1, 'b'), (2, 'c')]  
> [(0, 'a'), (1, 'b'), (2, 'c')]

`enumerate()`를 이용하여 `idx`와 `val`을 간편하게 얻은 경우와 `range()`를 이용하여 `idx`와 이를 이용해서 값을 참조한 경우가 같은 것을 확인할 수 있다.

## Refer

https://wikidocs.net/32  
https://velog.io/@rosewwross
