# 5.01 학교 파이썬수업 퀴즈 5회차 리뷰 (18-04-25)
이번에 풀지 못했던 피보나치 관련된 퀴즈.  

피보나치 수열에 대해 입출력을 받아 해당 입출력에 대한 조건으로 피보나치 수열을 ```print```한다.

15분 안에 풀지 못해 0점을 받은 스스로를 반성하면서.

조건 1) 시작하는 피보나치 수열의 수   
조건 2) 조건 1에 대응하여 다음에 나타나야 하는 피보나치 수열의 수를 입력받는다. ~~이 조건을 주는데도 제시간에 풀지못한 나는 킹빠가맨입니다.~~  
조건 3) 조건 2에 대응하여 조건 2 이후 나타나야 하는 숫자의 갯수를 입력받습니다.
```py
첫번째 input()으로 2, 두번째 input()으로 3, 세번째 input()으로 2 
를 입력 받았다면,
[0,1,1,2,3,5,8,13,21,34,55 ...]에서
[2,3] 다음인 [5]부터 2개를 받아 [5,8]을 print해주면 됩니다.
```
```py
a = input("initial:")
b = input("next:")
n = input("length:")
the_list = []

def fib(a,b,n):
    end=-1 #초기값을 음수로 설정하여 input값과의 동일 가능성을 제거한다.
    i=0

    while end!=0:
        if i==0:
            the_list.append(int(a)+int(b))
            i+=1 #인덱스의 역할을 하게 된다.
            end=int(n)-1 #앞으로 몇 번 반복하게 하는지를 결정한다.
                
        elif i==1:
            the_list.append(the_list[0]+int(b))
            i+=1
            end=end-1
                
        else:
            the_list.append(the_list[i-2]+the_list[i-1])
                #여기서부터는 i가 2부터 시작하기 때문에 2를 빼서 list의 index로 활용한다.
            i+=1
            end=end-1
    print(the_list)

fib(a,b,n)
```