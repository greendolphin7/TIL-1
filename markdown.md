# 20210113 Python

## 설치

### Python 3.8.7

- 버전 통일을 위해 사용

### VSCode

- python 확장 프로그램 설치

### Git

- 버전 관리를 위해 설치(현재는 사용하지 않고 있음)

### Typora

- markdown을 통한 정리

## Python의 기본 3요소

### 변수

- 값을 저장함

- list

  `_list = ['김밥','국수','귤']`

- dictionary(dict)

  `_dict = { '김밥':'010-1122-1123','국수:010-4456-4124'}`

### 조건

- if ~ elif ~ else

  ```python
  if ~~ :
    해당 조건에 해당하는 내용문
  elif ~~ :
    첫 조건에 해당이 안 되고 두 번째에 해당되는 경우의 조건문
  else :
    그 밖의 나머지 조건문
  ```

  ![스크린샷 2021-01-13 오후 5.35.35](markdown.assets/스크린샷 2021-01-13 오후 5.35.35.png)

### 반복

- while
- for
  - range(n)
    - 0부터 n-1 이하까지 반복(n은 포함하지 않음)

# 20210114 Python

## types

- 대개 number(int, float), string, boolean의 3요소
- 형변환
  - num = 4
  - str(num) => '4' : 문자열로 변환
- type 표시
  - type(num) 처럼 사용

## f-string / string interpolation

```python
name='김종백'

print(f'내 이름은 {name}입니다.')
## 내 이름은 김종백입니다.
```

- Python 3.6 이상 버전에서 가능
- 이전의 .format()에 비해 속도 측면에서 큰 향상

## list

```python
my_list = ['Java','Python']
print(my_list[0])
## Java
my_list[0]='C++'
print(my_list[0])
## C++
len(my_list)
##2
```

- len( ) : 리스트 또는 문자열의 길이 정수형으로 반환
- 리스트는 수정이 자유롭다.

## dictionary

```python
my_home = {
    'location':'대전', #key : value
    'area-code' : '042', #뒤에 오는 게 없어도 comma 사용가능
}

print(my_home['location'])
## 대전
print(my_home.get('location'))
## 대전, 없는 key값이 있는 경우 None 반환
```

- key : value의 형태로 사용됨
- 없는 키값에 접근하려 하면 KeyError 발생
- key값을 입력하면 그 key에 1:1 대응되는 value값 반환

- None : 아무 것도 없다는 의미

## operators

### 계산 연산자

| 연산자 |   의미   |
| :----: | :------: |
|   +    |  더하기  |
|   -    |   빼기   |
|   *    |  곱하기  |
|   /    |  나누기  |
|   //   |   몫만   |
|   %    | 나머지만 |
|   **   |   제곱   |

### 비교 연산자

|    연산자    |    의미    |
| :----------: | :--------: |
|      ==      |   같다.    |
|      !=      | 같지 않다. |
| >, <, >=, <= |  대소비교  |

### 연산자의 우선순위

- 각 연산자에는 우선순위가 있으나 외우기 귀찮다면 ( )로 우선순위를 지정하자.

## Condition

```python
n=10
#1. 주어진 수 n이 홀수인지?
if n%2==0:
    print('짝수')
else:
    print('홀수')
#2. 주어진 수가 음수/0/양수 중 어느 쪽인지?
if n<0:
    print('음수')
elif n==0:
    print('0')
else:
    print('양수')
```

```python
numbers = [i for i in range(1, 8)]
for num in numbers:
    if num % 2 == 1:
        print(num)
```

## function

- 복잡하고 긴 과정을 간단하게 여러 번 쓸 수 있도록 이름을 붙인 것
- 내장함수 : 별 조치 없이도 파이썬 내에서 사용할 수 있는 함수
- 외장함수 : 별 조치를 해야 파이썬 내에서 사용할 수 있는 함수
  - import 등으로 해당 함수을 파이썬 내에서 사용하겠다고 선언한 이후에 사용할 수 있음

```python
print(random.sample(lotto, 6))
```



## Crawling

- HTML+CSS+JS = 내 브라우저(크롬)를 꾸며 화면에 보여준다.
- Python으로 해당 페이지의 정보를 요청할 경우, 우리는 HTML+CSS+JS에 해당하는 정보를 가져온다.

- requests와 BeautifulSoup를 사용

  ```python
  import requests
  from bs4 import BeautifulSoup
  
  # 네이버의 주식정보 페이지의 현재 코스피 지수를 가져온다.
  url = 'https://finance.naver.com/sise/'
  
  # 요청을 보낸다. -> Requests
  response = requests.get(url).text
  # 받은 결과를 해석한다.(html) -> bs4의 BeautifulSoup
  # 복잡한 텍스트 중 내가 원하는 정보를 가져오기 쉽게 가공
  data = BeautifulSoup(response, 'html.parser')
  # 원하는 결과를 찾아서 출력한다.
  # 찾을 때는 크롬 > 검사 > 찾을 요소 선택 > Copy path > Copy Selector
  kospi_point = data.select_one('@@')
  ```
  


## API(Application Programming Interface)

- 정의 : 응용 프로그램에서 사용할 수 있도록 운영 체제나 프로그래밍 언어가 제공하는 기능을 제공할 수 있게 만든 인터페이스
- 프로그램과 프로그램이 서로 소통하기 위한 수단
- 소통하기 위한 규칙 > API 문서

```python
import requests

url = f'https://api.agify.io/?name={name}'
response = requests.get(url + name).json()
```

```python
key = 'hidden'
sido = '서울'
url = f'http://apis.data.go.kr/B552584/ArpltnInforInqireSvc/getCtprvnRltmMesureDnsty?serviceKey={key}&returnType=json&numOfRows=5&pageNo=1&sidoName={sido}&ver=1.0'

response = dict(requests.get(url).json())
```

## Git

- 코드에서 버전 관리를 위해 필요

### 주요 명령어

- 맨 처음 어떤 폴더를 git이 관리할지 여부를 결정

```bash
$ git init
```

- 대상이 되는 폴더를 git으로 관리하기 시작하겠다는 의미(1번만 하면 됨. 이후 내용은 상시 시행)

- 만약 git status등으로 master가 보이면, init 하지 말 것. 이미 했었음.

```bash
$ git status 
```

- 어떤 변경사항이 있는지 알아보기 위한 명령어

```bash
$ git add **
```

- stage에 파일을 올림

```bash
$ git config --global user.name @@
$ git config --global user.email @@
```

- "@@"라는 사람이 commit한다는 것을 알려야 함
- "@@"의 이메일을 가진 사람이 commit한다는 것을 알려야 함
- commit 단계를 거쳐야 기록이 남음

```bash
$ git commit -m 'first commit'
```

- -m : 메시지와 같이
- angular 메시지 작성 체계 : 
  - **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
  - **ci**: Changes to our CI configuration files and scripts (example scopes: Circle, BrowserStack, SauceLabs)
  - **docs**: Documentation only changes
  - **feat**: A new feature
  - **fix**: A bug fix
  - **perf**: A code change that improves performance
  - **refactor**: A code change that neither fixes a bug nor adds a feature
  - **test**: Adding missing tests or correcting existing tests
- 현재는 local로 진행하는 듯.

# 20210115 Python

## 원격(Remote 저장소)

- github
  - 무료 서비스 가능 / 유료 버전도 있음
- gitlab
  - SSAFY 서비스 중
  - 유료(회사에서 많이 씀)
- and so on....

```bash
$ git remote add origin "address"
```

- 내 컴퓨터의 저장소에서 원격 저장소(origin이라고 명명)를 지정하고, 그 주소는 "address"에 있는 주소로 하겠다는 의미

```bash
$ git push origin master
```

- origin이라고 한 저장소에 master라는 branch를 설정하여 원격 저장소에 commit된 파일을 업로드한다.
- branch는 수업 대부분 과정에서는 쓸 일이 없을 것

```bash
$ git clone 'address'
```

- 원격 저장소의 address 주소에 저장된 프로젝트를 내 로컬 컴퓨터로 다운로드 가능

## Telegram Chatbot

### bot 만들기

- botfather 검색
- botfather를 통해 봇을 만들고, api key 획득

### bot 추가

- telegram 계정으로 bot을 등록한다.
- bot의 사용에 대한 자세한 설명은 https://core.telegram.org/bots/api#available-methods 에서 확인가능

### 메시지 전송 실습

```python
import requests

## TELEGRAM 챗봇 메시지 전송

KEY = 'hidden'
BASE_URL = 'https://api.telegram.org/bot'
CHAT_ID = 'hidden'
MESSAGE = '배가 고프다.'
URL = f'{BASE_URL}{KEY}/sendMessage?chat_id={CHAT_ID}&text={MESSAGE}'

response = dict(requests.get(URL).json())
```

## PythonAnywhere

- files > my_bot directory 생성 > naver_shopping 업로드

  - 무료서비스인 경우 24시간에 한 번 원하는 파일을 실행 가능(Scheduling)

- Tasks로 가면 UTC시간대로 되어 있다.

  - 한국은 UTC+9니까, 설정할 때는 한국 시각-9시 를 해야 한다.

  - 파일 설정은 위의 업로드된 파일의 PythonAnywhere 상의 주소를 말함

  - python version은 3.6으로

  - 작성예시

    ```python
    python3.6 /home/bellhundred/my_bot/naver_shopping.py	
    ```

  - 다 작성했으면 Create

## Naver API

- 네이버 API 신청
  - client-id, client-secret 코드 모두 받기
  - 신청할 API 목록 적기
  - WEB 주소는 http://localhost 로 

### Papago(ko->en)

- 요청 형식이 POST로 고정
- POST인 경우에는 조건 설정을 따로 dict 형태로 분리
- 네이버 API는 headers dict를 따로 만들어 그 안에 CLIENT ID / SECRET을 보관
- requests.post(URL, data=data, headers=headers)의 형태로 네이버 서버에 API 요청
- 전달받은 JSON을 깔끔하게 보기 위해 pprint 활용

```python
CLIENT_ID = 'hidden'
CLIENT_SECRET = 'hidden'
...
headers = {
    'X-Naver-Client-Id': CLIENT_ID,
    'X-Naver-Client-Secret': CLIENT_SECRET,
}
data = {
    'source': SOURCE,
    'target': TARGET,
    'text': text,
}
URL = f'https://openapi.naver.com/v1/papago/n2mt'
response = requests.post(URL, data=data, headers=headers).json()
```

### Search(Shopping)

- GET 방식이므로 Parameter는 URL 뒤에 &로 묶어서 표현

```python
URL = f'https://openapi.naver.com/v1/search/shop.json?query={QUERY}&display=100&start=1000&sort=asc'

headers = {
    'X-Naver-Client-Id': CLIENT_ID,
    'X-Naver-Client-Secret': CLIENT_SECRET,
}

```

## Function

- 목적 : 함수 덩어리를 하나의 코드로 -> 편하게 코딩하려고.

```python
def get_age():
    print("나이는 몇 살입니까?")
```



- 함수를 호출할 때마다 변하는 값을 쓰고 싶다면 > 매개변수

```python
def get_age(age):
    print(f'나이는 {age}살입니다.')
```

- 함수값 반환을 위해서는 return

```python
def get_age(age):
    return f'나이는 {age}살입니다.'

result = get_age(18)
print(result)
```

## Python Server - Flask

### installation

```bash
pip install flask
```

### 3rd party library

- 내장/외장함수 이외에 제 3자가 제공하는 모듈

- 대체로 pip install 모듈이름 의 형태로 설치하게 됨

### 실행

- 실행 파일의 이름은 무조건 app.py
- flask run을 bash창에서 실행
- 성공하면 Hello, World!가 담긴 인터넷 창의 링크가 bash 창에 출력됨
- 서버 구축 가능

### 작성

```python
@app.route('/ssafy')
def ssafy():
    return 'SSAFY로 온 걸 환영합니다.'
```

### 수정

```python
if __name__ == '__main__':
    app.run(debug=True)
```

### Variable Routing

- 게시글 번호를 동적으로 할당해주는 기능

```python
@app.route('/post/<string:post_id>')
def post1(post_id):
    return post_id
```

## Jupyter Notebook

```bash
pip install notebook
```

# 20210118 Python

## 단축평가

### AND

- T1 and T2 = T2
- T1 and F1 = F1
- F1 and T1 = F1
- F1 and F2 = F1

### OR

- T1 or T2 = T1
- T1 or F1 = T1
- F1 or T1 = T1
- F1 or F2 = F2

## is와 ==

### ==

- 값이 같다.
- a = [], b=[] 이면, a==b

### is

- 객체 / OOP에서 사용

# 20210119 Python

## enumerate

```python
for idx, menu in enumerate(lunch, start=1):
    print(idx, menu)
```

- 튜플 형태로 반환

## for ~ else

```python
for num in numbers:
    if num==4:
        print(True)
        break
else:
    print(False)
```

# 20210120 Python

## funtion

### 매개변수

- 함수 선언 시 사용하는 변수

### 전달인자

- 함수 실행 시 사용하는 변수

### 키워드 인자

- 직접 변수의 이름으로 특정 인자 전달

```python
def greeting(age, name='john'):
    return f'{name}은 {age}살입니다.'
```

### print vs return

- print : 값을 출력 -> 반환하면 None
- return : 값을 반환

### 가변인자

```python
*args = 리스트 형태로 값 전달
def func(a, b, *args):
    pass
```

### 키워드 가변인자

```python
**kwargs = dict 형태로 값 전달
def func(**kwargs):
    pass
```

## 이름 검색(resolution) 규칙

파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있습니다.

이것을, `LEGB Rule` 이라고 부르며, 아래와 같은 순서로 이름을 찾아나갑니다.

- `L`ocal scope: 정의된 함수

- `E`nclosed scope: 상위 함수

- `G`lobal scope: 함수 밖의 변수 혹은 import된 모듈

- `B`uilt-in scope: 파이썬안에 내장되어 있는 함수 또는 속성

## 예외처리

```python
try:
    ~
except:
    ~
else:
    ~
finally:
    ~
```

## raise

- 에러 발생시 사용

## Recursion

- 반복문과 유사
- 자기 자신을 호출
- 탈출 루트가 없으면 무한루프에 빠지게 됨

# 20210121 Python

## type complex

- real : 복소수의 실수부
- imag : 복소수의 허수부

## 회문

```python
str(A)과 str(A[::-1])을 비교
```

## ASCII CODE

```python
# ord()는 문자를 아스키 코드번호로 변환할때 사용합니다
print(ord("a"))         #  문자 a를 아스키 코드 번호로 변환
print(hex(ord("a")))    # 문자 a를 아스키 코드 번호로 변환(16진수)
print(type(ord("a")))   # 변환후 타입은 'int'
 
 
#chr()은 아스키 코드 번호를 문자열로 변경할때 사용합니다
print(chr(97))          # 아스키 코드 번호를 문자열로 변환
print(chr(0x61))        # 아스키 코드 번호(16진수)를 문자열로 변환
print(type(chr(97)))    # 변환후 타입은 'str'
```

## 에라토스테네스의 체

```python
number = int(input())

# 아래에 코드를 작성하시오.

sqrt_number = number**0.5
for i in range(2, round(sqrt_number//2)+1):
    if sqrt_number%i==0:
        print("N")
        break
else:
    print("Y")
```

- 일단 코드만.