# Week4 Assignment4 CodeReview
## 20141944 정보보안암호수학과 최민혜

>  **week4 과제는 다음과 같다.**
>1. 재귀적으로 Factorial 함수 작성하기
>2. Factorial 함수를 적용하여 Combination 함수 작성하기
>3. 재귀함수를 이용하여 Combination 함수 작성하기
---
### _1. 재귀적으로 Factorial 함수 작성하기_
 * 초기 코드에는 '재귀적'으로 Facotorial 함수를 작성하기 위해 'n==1 이거나 0이 아닌 경우 '1부터 n-1까지를 재귀적으로 곱한 값에 n을 곱하도록하고 n==1 이나 0일 경우 1을 반환하고 종료하도록' 코드를 작성하였다.  
 * 코드리뷰를 통하여 종료조건이 n==0인 경우에만 설정해도 무방하므로, 프로그램 속도를 빠르게 하기 위해서는 수정하는 것이 좋겠다는 의견을 듣고 이를 수정하였다. 또한, 코딩 스타일 가이드라인에 맞추었을 때 함수이름은 '소문자'로 작성하는 것이 권장되어 이 부분도 수정하였다.

**>초기 코드**
```python
def Factorial(n):
    return 1 if n == 1 or n == 0 else Factorial(n – 1)*n
```
   **>코드 리뷰 후 수정한 코드**
   ```python
   def factorial(n):
       return 1 if n == 0 else factorial(n – 1)*n
   ```
---
### _2.Factorial 함수를 적용하여 Combination 함수 작성하기_
 * 초기에 Factorial 함수를 적용하여 'Combination 함수'를 작성하기 위해 다음 공식을 이용하였다.
 ```python
 nCr=Factorial(n)/(Factorial(r)*Facorial(n-r))
 ```
 * 코드 리뷰를 통하여 공백과 함수 이름 작성에 스타일 가이드라인에 맞지 않는 부분이 있었고 이를 수정하였다.  
  **>초기 코드**
 ```python
 def Combination(n,r):
     return Factorial(n)/(Factorial(r)*Factorial(n-r))
 ```

**>코드리뷰 후 수정한 코드**
```python
def combination(n,r):
    return factorial(n)/(factorial(r)*factorial(n – r))
```
---
### _3.재귀함수를 이용하여 Combination 함수 작성하기_
* 초기에는 재귀함수를 이용하여 Combination 함수를 작성하기 위해 다음의 공식을 이용하였다.
```python
nCr=(n-1)C(r-1)+(n-1)Cr
```
* 이때 nCn = 1이고 nC0 = 1 이므로 n = r일때나 r = 0일 경우 1을 반환하고 종료하도록 하였고  
그 외의 경우에는 (n-1)C(r-1)+(n-1)Cr 을 반환하도록 하였다.  
* 코드리뷰를 통해서 함수 이름의 길이를 줄이고 소문자로 바꾸게 되었고,  
또한 해당 실행문이 시작되기 전에 주석을 작성하는 것이 보기에 좋을 것 같다는 의견을 수렴하여 수정하였다,

**>초기 코드**
```python
def recursive_Combination(n,r):
    if n == r or r == 0:    #nCn == 1, nC0 == 1 이므로 1을 반환한다.
        return 1
    else:    #nCr == (n-1)C(r-1)+(n-1)C(r)을 이용한다.
        return recursive_Combination(n-1,r-1)+recursive_Combination(n-1,r)
```
**>코드리뷰 후 수정한 코드**
```python
def recursive_comb(n,r):
    #nCn == 1, nC0 == 1 이므로 1을 반환한다.
    if n == r or r == 0:
        return 1
        
    #nCr == (n-1)C(r-1)+(n-1)C(r)을 이용한다.
    else:
        return recursive_comb(n-1,r-1)+recursive_comb(n-1,r)
```
