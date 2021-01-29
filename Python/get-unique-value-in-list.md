# **list에서 중복 제거하기**

1. set 이용
2. for문 이용

#

## 1. set 이용

- set(집합) : 순서가 없고 유일한 값들을 가진다.
- 중복을 허용하지 않는다는 set의 특징을 이용하면 list에서 중복되는 값을 제거할 수 있다.

```python
li = ['a', 'a', 'b', 'b', 'c', 'd', 'd']
print( li )
print( set(li) )
```

> ['a', 'a', 'b', 'b', 'c', 'd', 'd']  
> {'c', 'd', 'b', 'a'}

---

list `li`를 set으로 변환 시켜주면 중복된 값이 제거된 것을 확인할 수 있다. 하지만 실행 결과는 set이기 때문에 list에서 가능한 indexing 작업을 할 수 없다.

```python
print( set(li)[0] )
```

> TypeError: 'set' object is not subscriptable

그렇기 때문에 이를 다시 list로 변환시켜주는 작업을 거치면 list에서 중복된 값만 제거된 값을 얻을 수 있다.

```python
print( list(set(li)) )
print( list(set(li))[0] )
```

> ['a', 'c', 'd', 'b']  
> a

이 때, 주의해야 할 것은 set은 순서가 없기 때문에 초기의 list와 index는 달라질 수 있으므로 원소의 index가 중요한 경우에는 사용을 피해야 한다. 이와 같은 경우에는 for문을 이용해야 한다.

#

## 2. for문 이용

- if문을 이용하여 원소를 직접 비교한다.

```python
li = ['a', 'a', 'b', 'b', 'c', 'd', 'd']

new_li = []
for i in li:
    if i not in new_li:
        new_li.append(i)

print( li )
print( new_li )
```

> ['a', 'c', 'd', 'b']  
> a

빈 list `new_li`를 선언한 후 모든 원소를 돌며 해당 원소가 `new_li`에 존재하는 지 확인하고 존재하지 않는 경우에만 `new_li`에 추가한다. 이럴 경우 동일한 원소 중 가장 먼저 존재하는 원소들만 남고 다른 원소들은 삭제된다.

## Refer

https://velog.io/@daybreak
