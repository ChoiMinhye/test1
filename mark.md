# Week4 Assignment4 CodeReview
## 20141944 정보보안암호수학과 최민혜

> **week4 과제는 다음과 같다.**
> 1. 재귀함수로 Factorial 함수 작성하기
> 2. Factorial 함수를 적용하여 Combination 함수 작성하기
> 3. 재귀함수를 이용하여 Combination 함수 작성하기


### 1번
재귀함수로 Factorial함수를 작성하기 위하여

1부터 n-1까지를 곱한값에 n을 곱하는 방식으로 실행하였다.


이때 종료 조건은 n이 1이거나 0일경우 1을반환하고 종료하도록하였다.
```python
#Recursive Factorial Function
def Factorial(n):
    return 1 if n == 1 or n == 0 else Factorial(n - 1)*n

#Combination Function1(Factorial 이용)
def Combination(n,r):
    return Factorial(n)/(Factorial(r)*Factorial(n-r))

#Combination Function2(Recursive Algorithm 이용)
def recursive_Combination(n,r):
    if n == r or r == 0:    #nCn == 1, nC0 == 1 이므로 1을 반환한다.
        return 1
    else:    #nCr == (n-1)C(r-1)+(n-1)C(r)을 이용한다.
        return recursive_Combination(n-1,r-1)+recursive_Combination(n-1,r)


print('<Factorial calculation>')
number = int(input('Enter a number: '))    #수 입력
while number >= 0:    #음수값이 입력될 때까지 Factorial계산
    print('%d! = %d' %(number,Factorial(number)))
    number = int(input('Enter a number: '))
else:
    print('Incorrect form')
print()

print('<Combination nCr>')
n = int(input('Enter a number n: '))    #n 입력
r = int(input('Enter a number r: '))    #r 입력

while n >= r and r >= 0:    #n이 r보다 크거나 같고, r이 0 이상일 동안 계속 실행한다.
    print('%dC%d = %d (Factorial is used.)' %(n,r,Combination(n,r)))
    print('%dC%d = %d (Recursive Algorithm is used.)' %(n,r,recursive_Combination(n,r)))

    print()
    n = int(input('Enter a number n: '))  # n 입력
    r = int(input('Enter a number r: '))  # r 입력
else:
print("Incorrect form")```
