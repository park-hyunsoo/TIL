# Numpy
> 넘파이의 연산은 C로 구현된 내부 반복문을 사용하기 때문에 파이썬 반복문에 비해 속도가 빠르며 벡터화 연산을 이용하여 간단한 코드로 선형 대수 연산을 수행할 수 있다

1. 벡터
```
import numpy as np

a = np.array([1,2,3])
b = np.array([4,5,6])

print(2 * a + b) # [ 6  9 12]
print(a == 2) # [False  True False]
print(b > 5) # [False False  True]
print((a == 2) & (b > 4)) # [False False False]
```
numpy의 array() 함수를 사용해 ndarray 클래스 객체, 배열을 만들 수 있다.

1차원 배열의 경우 벡터라고 한다.(행 벡터)

numpy는 벡터화 연산을 지원하고 각 원소에 대한 연산을 쉽게 할 수 있다.



