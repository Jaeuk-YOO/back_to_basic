# 5.01 학교 파이썬수업 퀴즈 5회차 리뷰 (18-05-02)
이번에도 풀지 못했던 파이썬 퀴즈~
A에서 미끄러지는 소리가 여기까지~~~

퀴즈 목표 : txt파일 3개를 불러와서 header와 comment와 계산해야하는 data내용을 조건에 맞게 분리한 후 data 내용만 받아 각각 element의 value값을 더해주는게 이번 퀴즈의 목표였다.

```py 
file_path1 = "./data.txt"
file_path2 = "./data2.txt"
file_path3 = "./data3.txt"

file1_open = open(file_path1)
file2_open = open(file_path2)
file3_open = open(file_path3)

new_list = []

for line in file1_open:
    if not line.endswith(".\n"):
        new_list.append(line.strip())

for line in file2_open:
    if not line.endswith(".\n"):
        new_list.append(line.strip())

for line in file3_open:
    if not line.endswith(".\n"):
        new_list.append(line.strip())

print(new_list)

goose_count = 0
jaeger_count = 0
fulmar_count = 0

for x in new_list:
    splitted_element = x.split()
    if splitted_element[0].count("goose") == 1:
        goose_count = goose_count + int(splitted_element[1])
    elif splitted_element[0].count("jaeger")==1:
        jaeger_count = jaeger_count + int(splitted_element[1])
    elif splitted_element[0].count("fulmar")==1:
        fulmar_count = fulmar_count + int(splitted_element[1])

print(goose_count)
print(jaeger_count)
print(fulmar_count)
```

퀴즈 하면서 막혔던 부분은 문장분류였다. header와 comment에는 마침표가 찍혀있었고, 이를 미루어 header와 comment를 분리해내기 위해 ```str in "."```으로 for문 안에서 헛짓거리를 했다는 것. 멍청함을 feedback 해보자.

> 1) ```string in "."```은 반대다ㅋㅋㅋ ```string```이 ```"."```에 있냐고 물으니까 당연히 ```False```가 나오지 ...  
```"." in string```이 되어야 ```"."```이 ```string```에 있냐고 묻는 것이다. **똥멍청이**였네ㅎㅎ
> 2) ```string.count(".")```은 ```1```이 나온다.
> 3) ```string.split()```을 하는 순간 ```string```은 ```list```가 된다. 마찬가지로 ```list in item```가 아니라 ```item in list ```이 되어야 ```True```든 ```False```든 결과가 나오는 것이다.
> 4) ```string.split()```은 빈칸 단위로 ```list```로 끊어줘서 ```in```으로 그 존재를 묻는 경우 하나의 ```element```를 완벽하게 일치하는 경우에만 ```True```처리를 한다.

~~그건 그렇고 파일 오픈해서 검증하는거 잘쓰지도 않는데 15분 솔직히 너무 빡센거 아니냐..~~ 