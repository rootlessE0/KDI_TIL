# 파이썬 기초(5)

> 튜플(tuple), 집합(set), 딕셔너리(dictionary)

## 0.튜플 

* 리스트와 유사한 집합적 자료형, 그러나 원소 추가, 수정, 삭제 불가 > 원소 변경시 에러 발생
* 소괄호 `()` 사용 또는 `변수 = 값,`하여 선언
* 원소는 0부터 시작하는 인덱스로 구분

* 실수로 요소가 추가되거나 삭제되지 않도록 내용을 변경할 수 없게 하기 위해 사용

* 인덱스를 이용하여 접근

  

#### 튜플 생성

```python
# 튜플 생성
t1=(1,2,3)
print(t1)

t2=4,5,6
print(t2)

t3=t1,(7,8,9)

t4=[1,2],[3,4]

# 원소 1개를 튜플로 생성
t5=(4)
t6=4    # 일반 정수형 변수
t7=4,   # 튜플

# 리스트를 튜플로 변환 후 반환하는 함수 : tuple()
t8=tuple([5,6,7,8])
print(t5)
print(type(t8))

# 튜플을 리스트로 변환 후 반환하는 함수 : list()
to_list1=list(t1)
print(to_list1)

# 튜플내의 튜플 원소는 그대로 유지
to_list2=list(t3)
print(to_list2) # [(1,2,3),(7,8,9)]

# 튜플 변경시 에러
# 추가/수정/삭제 불가
t=(1,2,3)
# t[0]=5 TypeError: 'tuple' object does not support item assignment

>>>
(1, 2, 3)
(4, 5, 6)
4
<class 'tuple'>
[1, 2, 3]
[(1, 2, 3), (7, 8, 9)]
```



## 1. 집합

* 순서가 없음  > 입력되는 순서와 출력되는 순서가 다를 수 있음 > 인덱스로 접근 불가 > 이미 포함되어있는 요소(값) 변경 불가
* 중괄호 `{}` 사용하여 선언
* 동일한 요소(값)이 중복될 수 없음
* 요소 추가, 삭제 가능
* 집합 안에 변경 가능한 항목 포함할 수 없음 > 리스트 포함 불가능, 튜플 포함 가능

### 집합 생성, 추가, 삭제

```python
# 집합 생성
s1={1,2,3,4,5}
print(s1)
print(type(s1)) # <class 'set'>

# 리스트를 집합으로 변환 후 반환 : set()
s2=set([1,2,3])
print(s2)
print(type(s2)) # <class 'set'>

# 동일한 요소(값)이 중복될 수 없음
s4={1,2,2,3,4} # 에러는 없음
print(s4) # 중복 값 제거하고 집합 생성

# s5={1,2,[3,4]} TypeError: unhashable type: 'list'

# print(s4[0]) TypeError: 'set' object is not subscriptable

# 집합에 요소 추가 : add(), update()
s={1,2,3}

s.add(4) # 1개 추가시
print(s)

s.update([5,6]) # 여러개 추가시
print(s)

# 집합에서 요소 삭제 : remove(), discard(5)
s.remove(3)
s.discard(5)
print(s)

# 없는 요소 삭제시
# s.remove(10) # KeyError: 10
s.discard(10) # 에러 없음(없을 시 아무 작업하지 않음)

# 집합 전체 요소 삭제 : clear()
s.clear() # 요소만 삭제, set의 구조는 존재
print(s) # set()

# 집합 요소, 구조 삭제 : del
del s
# print(s) NameError: name 's' is not defined

>>>
{1, 2, 3, 4, 5}
<class 'set'>
{1, 2, 3}
<class 'set'>
{1, 2, 3, 4}
{1, 2, 3, 4}
{1, 2, 3, 4, 5, 6}
{1, 2, 4, 6}
set()
```



### 집합 연산

```python
A={1,2,3}
B={3,4,5}

# 합집합
C=A|B
print(C)
C=A.union(B)
print(C)

# 교집합
C=A&B
print(C)
C=A.intersection(B)
print(C)

# 차집합
C=A-B
print(C)
C=A.difference(B)
print(C)

>>>
{1, 2, 3, 4, 5}
{1, 2, 3, 4, 5}
{3}
{3}
{1, 2}
{1, 2}
```



#### 예제) 합집합, 교집합, 차집합 출력 

```
A={'Park','Kim','Lee'}
B={'Park','길동','몽룡'}

print('파티에 참석한 모든 사람\n',A|B) # A.union(B)
print('----------------------------------')
print('2개의 파티에 모두 참석한 사람\n',A&B) # A.intersection(B)
print('----------------------------------')
print('파티 A에만 참석한 사람\n',A-B) # A.difference(B)
print('----------------------------------')
print('파티 B에만 참석한 사람\n',B-A) # B.difference(A)
```



### 집합 에러

#### TypeError : unhashable type

```python
s5={1,2,[3,4]} 
>>>
TypeError: unhashable type: 'list'
```

집합은 해싱을 이용해서 저장, 관리되므로 변경 가능한  타입은 저장이 불가

해시에 해당하는 값을 변경 > 해시코드 변경 > 논리에 어긋남



#### TypeError : 'set' object is not subscriptable

```python
print(s4[0]) 
>>>
TypeError: 'set' object is not subscriptable
```

집합은 순서가 없으므로 인덱스로 접근할 수 없음



## 2. 딕셔너리

* 키(key)와 값(value)의 한 쌍을 요소로 갖는 자료형
* 중괄호 `{}` 또는 `변수 = dict()`사용하여 선언
* 순서가 없음 > 인덱스로 접근 불가
* key를 통해서만 접근, key는 숫자, 문자 다 가능
* key:value 한 쌍을 item 이라고 함
* 쉼표 `,` 로 item 구분

```python
dict명['key']=value # 대괄호 안의 값이 인덱스가 아님에 주의
```

```python
# key : value - item으로 이루어짐
d={1:'a'}
print(d)
print(type(d))

# 두 번째 요소 추가
# dict명['key']=value
d[2]='b' # 대괄호 안의 값이 인덱스가 아님에 주의
print(d) # {1:'a', 2:'b'}

print('-----------------------------')
d['삼']='c'
print(d) # # {1:'a', 2:'b', 3: 'c'}

# 회원정보 저장
member={'name':'홍길동','phone':'01012341234'}
print(member)

# 주소 정보 추가
member['address']='서울'
print(member)

# 길면 여러 줄로 입력해도 됨
naver = {
    'name':'naver',
    'url':'www.naver.com',
    'userid':'nv',
    'password':'1234'
}
google = {
    'name':'google',
    'url':'www.google.com',
    'userid':'gg',
    'password':'1234'
}
print(naver)
print(google)
# {'name': 'naver', 'url': 'www.naver.com', 'userid': 'nv', 'password': '1234'}
# {'name': 'google', 'url': 'www.google.com', 'userid': 'gg', 'password': '1234'}

print('----------------------------')
# keys(), values(), items() : 딕셔너리 값을 리스트를 포함하는 형태로 반환
print(naver.keys())
print(naver.values())
print(naver.items())
# naver.keys()[0] TypeError: 'dict_keys' object is not subscriptable
# 리스트 형태지만 리스트와 같이 바로 인덱스로 접근하면 사용 불가능
print(type(naver.keys())) # <class 'dict_keys'

# 키 리스트나 값 리스트를 함수를 이용해서 반환 받으면 List 형식으로 형 변환 후 접근 가능
# list() 함수를 이용해 리스트로 변환
to_list=list(naver.keys())
print(to_list)
print(type(to_list)) # <class 'list'>
print(to_list[0]) # 인덱스로 접근 가능

# tople() 함수를 이용해 튜플로 반환
to_tople=tuple(naver.keys())
print(to_tople)
print(type(to_tople)) # <class 'list'>
print(to_tople[0]) # 인덱스로 접근 가능

print()


# for문 이용하여 각 요소 출력
for key in naver.keys():
    print(key, end=' ')
print()
for val in naver.values():
    print(val, end=' ')
print()
for item in naver.items():
    print(item, end=' ')


# key로 value 반환받기
print(naver['userid']) # 직접 접근
print(naver.get('password')) # get() 사용하여 간접 접근

# 직접 접근시 key 존재하지 않으면 KeyError 발생
# print(naver['Link'])

# get()을 통한 간접 접근시, 없을 경우 출력값 설정 가능
print(naver.get('Link'))
print(naver.get('Link','없음'))

# if 문에서 get() 사용
insert_key='Link'
if naver.get(insert_key) is None:
    print(insert_key + '에 대한 data가 없습니다.')

# key 존재 여부만 확인 : in, not in
print('link' in google) # google 딕셔너리에 link 키가 존재하는지 여부
print('link' not in google)# google 딕셔너리에 link 키가 존재하지 않는지 여부
```



#### 예제) 메뉴 딕셔너리 아이템 추가, 수정하기

```python
# 딕셔너리 선언
dictionary ={
    'name' : '버섯불고기덮밥',
    'type' : '덮밥',
    'ingredient' : ['소고기','버섯','양파','간장','설탕'],
    'origin' : '한국'
}

# 딕셔너리 내용 출력
print('요리명 :', dictionary['name'])
print('종류 : ', dictionary['type'])
print('재료 : ', dictionary['ingredient'])
print('원산지 : ', dictionary['origin'])

# dictionary[name] 키 value를 한우버섯불고기덮밥으로 변경
dictionary['name']='한우버섯불고기덮밥'
# 딕셔너리[키]=값
# 해당 키 값이 존재하면 값 변경, 없으면 item을 추가
print('요리명 :', dictionary['name'])

# 사용자로부터 5개의 item 입력받아 dict 구성
# 같은 이름의 키를 가질 수 없다.(키 중복 불가)
user_dict={} # 빈 딕셔너리 할당 후 작업
for i in range(5):
    key=input('key를 입력하세요 : ')
    val=input('key에 대응하는 값을 입력하세요 : ')
    user_dict[key]=val
print(user_dict)
```



#### 예제) 인자 전달받아 딕셔너리로 반환

```python
def show_info(name,grade,age,phone):
    return {'name':name,'grade':grade,'age':age,'phone':phone}

print(show_info('홍길동','4','10','1234'))
```



## 5. 자료구조별 변경가능여부

> 변경 가능(Mutable)/불가능(Immutable)

|  자료형  | 변경가능여부 | 인덱스사용 |
| :------: | :----------: | :--------: |
|  수치형  |  Immutable   |            |
|  문자열  |  Immutable   |    사용    |
|  리스트  |   Mutable    |    사용    |
|   튜플   |  Immutable   |    사용    |
| 딕셔너리 |   Mutable    |            |

