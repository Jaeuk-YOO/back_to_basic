# 프로그래머스 알고리즘 연습 (18-05-02)
## level 2 이상한 문자만들기
### - 첫번째 풀이  
**문제** :  
string이 try hello world라면 첫 번째 단어는 TrY, 두 번째 단어는 HeLlO, 세 번째 단어는 WoRlD로 바꿔 TrY HeLlO WoRlD를 리턴하면 됩니다.  
**주의** 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단합니다.
```py
string = "try hello world"
#new_list = []
new_string = str()
for x in string.split():
    x_len = len(x)
    for index in range(0, x_len):
        print(index)
        if (index+1)%2!=0:
            result = x[index].upper()
            new_string = new_string+(x[index].upper())
            print(new_string)
            #new_list.append(result)
        else:
            new_string = new_string+(x[index])
            print(new_string)
            #new_list.append(x[index])
        if index == x_len:
            new_string = new_string+"%20"

print(new_string)
```
처음에는 list로 넣어서 하려다가 string을 더하면 된다는 아주 기초적인 사실을 떠올려서 string을 더하는 방식으로 해결  

### - 두번째 풀이
1. 에러가 났던 부분은 testcase의 ```string```이 소문자로만 들어오지 않았기에 ```s```값을 받아서 ```else``` 부분에 ```str.lower()```를 추가해서 일일이 ```lower()```된 값을 넘겼다.  
2. 하단의 if는 for문이 안 끝나는 경우 공백을 넣어주고 끝나는 경우는 공백을 넣어주지 않기 위함이다.
```py
def toWeirdCase(s):
    new_string = str()    
    
    for x in s.split():
        x_len = len(x)
        for index in range(0, x_len):
            print(index)
            if (index+1)%2!=0:
                result = x[index].upper()
                new_string = new_string+(x[index].upper())
                print(new_string)
            elif (index+1)%2==0:
                result = x[index].lower()
                new_string = new_string+(x[index].lower())
                print(new_string)
            if (index == x_len-1) and (s.split().index(x)+1 != len(s.split())):
                new_string = new_string+" "

    return new_string

# 아래는 테스트로 출력해 보기 위한 코드입니다.
print("결과 : {}".format(toWeirdCase("try hello world")));
```
축하합니다 정답입니다~ 다른사람의 코드를 볼까요??

```py
    # rhdudals0659님의 코드입니다.
    def toWeirdCase(s):
        return " ".join(map(lambda x: "".join([a.lower() if i % 2 else a.upper() for i, a in enumerate(x)]), s.split(" ")))
```
~~쉬펄...... 빡대가리라 슬포요...~~