# 파이썬 기초(9)

> 오류 예외처리

## 예외처리

오류에 대처하기 위한 오류

예외는 주로 실행중에 발생

오류 발생시 프로그램이 중단되고 에러마세지가 출력되지 않도록 예외 처리 메세지를 발생시킴



### 에러 종류

```python
# 에러 종류 확인

# ZeroDivisionError
# print(10/0)

# TypeError
# print('나이: '+23)

# NameError
# print(b)

# ValueError
# c=100
# print('%d%'%c)

# SyntaxError
# if x > 10
#     print('홍길동')

# UnboundLocalError
# def add():
#     a=a+1
# print(add())

# ModuleNotFoundError
# import myModule

# FileNotFoundError
# f=open('exception.txt','r')

# OSError
# f=open('c:\file\exception.txt','w')
```



### 예외 처리 방법 

```python
#에러가 발생하기만 하면 except 블록 수행

# 1
try:
    print(10/0) # ZeroDivisionError
except: # 에러 종류 명시X. 에러 종류와 상관 없이 수행
    print('0으로 나눌 수 없습니다.')

# 2 : Exception
try:
    print(10/0)
except Exception: # Exception : 최상위 에러(모든 에러를 전부 포함하는 에러 집합)
    print('오류 발생')

# 3
try:
    # print('나이 : '+23) # 예외처리 명시되어있지 않아 TypeError 발생
    print(10/0)
except ZeroDivisionError: # 0으로 나누는 에러의 경우만 처리 함
    print('오류 발생')

# 4 : 에러종류 명시
# 숫자를 입력하지 않은 경우 ValueError
try:
    num=int(input('숫자를 입력하세요 : '))
except ValueError:
    print('숫자가 아닙니다.')

# 5 : 에러 종류 명시 as 에러 메세지 변수 : 시스템에서 확인한 에러 메세지를 그대로 출력 가능
try:
    print(10/0)
except ZeroDivisionError as e:
    print('오류발생 : ',e)

# 6-1 : 여러개의 예외처리, 에러 명시
# 그러나 첫번째 에러에 대해서만 처리하고 프로그램 종료
# except 구문을 여러번 반복해서 명시
a=[1,2,3]
try:
    print(10/0) # 첫번째 오류발생
    print(a[4]) # 인덱스 범위가 벗어남 - 두번째 오류발생
except ZeroDivisionError as e:
    print('0으로 나눌 수 없습니다.', e)
except IndexError as e:
    print('인덱스 범위를 벗어났습니다. : ',e)

# 6-2 : 여러개의 예외처리
# 첫번째 에러에 대해서만 처리하고 프로그램 종료
try:
    print(10/0)
    print(a[4])
except(ZeroDivisionError,IndexError) as e:
    print('오류가 발생했습니다.',e)

```



#### 예제) 예외처리

```python
# try:
#     오류 가능성이 있는 코드
# except:
#     오류 발생시 처리 구문
# else:
#     오류가 없을 시 진행되는 구문
# finally:
#     print('종료')

try:
    num=int(input('숫자 입력 : '))
except ValueError:
    print('숫자가 아닙니다.') # 에러 발생시 실행
else:
    print(num) # 정상 진행시 실행

# 오류 발생시 아무것도 하지 않고 넘어가기
# 파일 읽어오기를 수행할 때
# 파일이 없어서 오류가 나면 그냥 pass 하고
# 파일이 있으면 읽고 출력하기

try:
    f=open('exception.txt','r')
except FileNotFoundError:
    pass
else : # 생략 가능
    data=f.read()
    print(data)
    f.close()
finally: # 생략 가능
    print('종료')

# 기능별로 필요시에는 문장마다 try except 처리를 해 줘야 함
# 예외처리는 프로그램 내부에서의 문제보다 외부와 연결되는 코드에서 예외처리를 해주게 됨
# ex. 사용자 입력, 파일 입출력, 메모리 관리 등
# finally 문 : 예외 발생 여부에 상관 없이 항상 수행되는 문
```