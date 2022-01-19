[toc]

# Python(in vscode)



## `__name__`

```python
if __name__ == '__main__':		# 1
    print('running in direct file')

if __name__ == 'mod.mod2':		# 2 (이 코드는 mod.mod2에 존재)
    print('activate mod.mod2.py')
```

1. 이 코드가 있는 파일을 직접 실행할 시 `__name__ = '__main__'`
2. 'mod.mod2' 모듈 파일을 import한 파일을 실행하면 `__name__ = 'mod.mod2'`



## import sys

#### sys.path.append

path: 환경 변수(시스템 변수)

```python
# mod파일에 있는 mod2 모듈 파일을 import
import sys
sys.path.append('C:\workspace\mod')
import mod2
```

또는 TERMINAL창에 `set PYTHONPATH='C:\workspace\mod'` 입력 후 import mod2



## 예외 처리

#### 사용자 정의 예외 처리(`__str__`의 사용)

```python
# 사용자 정의 예외 처리
class MyError(Exception):
    def __str__(self):
        return '영주는 바보가 아니다'

def say_nick(nick):
    if nick == '바보':
        raise MyError		# raise: 일부러 exception 발생

say_nick('바보')
```



## 데이터 저장

#### 파일(파일 복사, 임시 파일 만들기)

f.read(): 파일 전체 내용을 str로 읽음

f.readline(): 파일 내용 한 줄씩 str로 읽음(while문 활용)

f.readlines(): 파일 전체 내용을 list로 반환

f.write(data): 파일에 data 저장

```python
# 파일 복사
import shutil
shutil.copy('text1.txt', 'text2.txt')

# 임시 파일 만들기
import tempfile
f = tempfile.mkstemp()
print(f)
```



#### pickle 객체

```python
# pickle: 문자열 외의 데이터 저장 or 읽음
import pickle

class Multiple_:
    def __init__(self, multiplier):
        self.multiplier = multiplier
    def multiply(self, number):
        return number * self.multiplier
m = Multiple_(5)

with open('pickle_test.txt', 'wb') as f:	# wb: write binary
    data = {1: 'python', 2: 'javascript'}
    data1 = 'youngju'
    pickle.dump(data, f)
    pickle.dump(data1, f)
    pickle.dump(m, f)
    
lst = list()
with open('pickle_test.txt', 'rb') as f:
    while True:
        try:
            msg = pickle.load(f)
            if isinstance(msg, Multiple_):
                print(f'Multiple_객체를 만났습니다.\n연산의 결과는 {msg.multiply(2)}입니다.\n)
            lst.append(msg)
        except:
            break
                      
print(lst)
```

pickle.dump(data, f): 데이터를 f 파일에 저장

pickle.load(f): f 파일의 데이터를 하나씩 읽어옴



## 다양한 모듈들

```python
# webbrowser
import webbrowser
webbrowser.open('http://google.com')

# calendar
import calendar
print(calendar.calendar(2022))		# calendar.prcal(2022)
print(calendar.prmonth(2022, 1))
print(calendar.weekday(2022, 2, 3))
print(calendar.monthrange(2022, 2))	# (2월의 시작 요일, 며칠까지 있는지)

# os
import os
print(os.environ['path'])		# 환경 변수
os.chdir(os.getcwd() + '\lib')	# change dir, get current working dir

print(os.system('dir'))		# dir목록이 보이기는하나 실제 반환값이 아님
f = os.popen('dir')
print(f.read())				# 실제 반환값이 dir목록
f = os.popen('code')
print(f.read())				# vscode 실행

# time
import time
print(time.asctime(time.localtime(time.time())))	# 시간 변환
print(time.strftime('%c'))	# 시간 포맷
for i in range(5):
    print(time.ctime())
    time.sleep(2)
```



## random

random.random(): 실수형 난수

random.randint(a, b): a~b에서 정수형 난수

random.choice(list): list에서 무작위로 요소 선택

random.shuffle(list): list 섞기