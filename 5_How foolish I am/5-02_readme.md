# 프로그래머스 알고리즘 연습 (18-05-02)
### level 2 이상한 문자만들기

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
            
print(new_string)
```
처음에는 list로 넣어서 하려다가 string을 더하면 된다는 아주 기초적인 사실을 떠올려서 string을 더하는 방식으로 해결