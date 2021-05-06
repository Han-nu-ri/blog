생계통 HW#3
학번: 2021-21051
이름: 한누리

1.1)
X가 T 보다 큰 경우 Penalty cost가 발생하고, X가 T 이하인 경우 Fixed cost가 발생합니다.  f와 P는 각각 X의 pdf, cdf이므로 아래와 같은 cost 식이 성립합니다:
$$
g(T)=(1-F(T))K + F(T)pT
$$
1.2)
위 g(T)의 일계 도함수, 이계 도함수를 구하여 g가 볼록인지 확인합니다.
g(T)의 일계 도함수:
$$
g'(T)=-f(T)K+f(T)pT+F(T)p 
$$
g(T)의 이계 도함수:
$$
g''(T)=-f'(T)K+f'(T)pT+f(T)p+f(T)p \\
= f'(T)(pT-K) + 2f(T)p
$$
T < E[X]이므로, g''(T)는 양수이고 g는 볼록입니다. 따라서 다음을 만족하는 T*이 optimal입니다.
$$
g'(T^*)=-f(T^*)K+f(T^*)pT^*+F(T^*)p=0
$$

2.1)
![image](https://user-images.githubusercontent.com/11609881/117333081-86eddc80-aed3-11eb-9b9a-944cc60b4321.png)

```
import scipy.stats  
import numpy as np  
import scipy.integrate as integrate  
  
  
def compute_likelihood_normal(data, d_mean, d_std):  
    return scipy.stats.norm(d_mean, d_std).pdf(data)  
  
  
def compute_inverse_F(input, d_mean, d_std):  
    return scipy.stats.norm.ppf(input, loc=d_mean, scale=d_std)  
  
  
def compute_s_optimal(X, each_t, costs, c, p, h, d_mean, d_std):  
    discretized_expectation = 0  
  for each_x_index in range(0, 6):  
        discretized_expectation += costs[each_x_index, each_t + 1] * compute_likelihood_normal(X[each_x_index], d_mean, d_std)  
  
    return compute_inverse_F(((-c + -discretized_expectation + p) / (h + p)), d_mean, d_std), discretized_expectation  
  
def compute_theta_plus_one(h, p, x):  
    return h * max(0, x) + p * max(0, -x)  
  
  
def compute_theta(y, c, x, r, discretized_expectation, d_mean, d_std):  
    return c*(y-x) + h*integrate.quad(lambda d: (y - d)*scipy.stats.norm(d_mean, d_std).pdf(d), 0.0, y)[0] + p*integrate.quad(lambda d: (d - y)*scipy.stats.norm(d_mean, d_std).pdf(d), y, np.inf)[0] + r*discretized_expectation  
  
  
if __name__ == "__main__":  
    T = 10  
  c = 1  
  h = 0.5  
  p = 10  
  r = 0.98  
  d_mean = 20  
  d_std = 5  
  X = [-10, 0, 10, 20, 30, 40]  
    costs = np.zeros(shape=(6, 11))  
    s_optimal = np.zeros(shape=(10,))  
    for each_t in range(10, -1, -1):  
        if each_t < 10:  
            s_optimal[each_t], discretized_expectation = compute_s_optimal(X, each_t, costs, c, p, h, d_mean, d_std)  
        for each_x_index in range(0, 6):  
            if each_t == 10:  
                costs[each_x_index, each_t] = compute_theta_plus_one(h, p, X[each_x_index])  
            else:  
                if X[each_x_index] < s_optimal[each_t]:  
                    y = s_optimal[each_t]  
                else:  
                    y = X[each_x_index]  
                costs[each_x_index, each_t] = compute_theta(y, c, X[each_x_index], r, discretized_expectation, d_mean, d_std)  
    print(s_optimal)  
    print(costs)
```
2.2)
![image](https://user-images.githubusercontent.com/11609881/117335218-dd5c1a80-aed5-11eb-9ff8-8c4df0824668.png)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgwMjI3MjI4MiwtMzkwMTk5MzM4LDc3MT
g0MDQ5NCwxMTE3NjgzNzg3LC0yMjM1Mjk3NDksLTEzMDU5Nzk1
NTUsNDAzNDU1MDkzLDE4ODI5OTY4MDRdfQ==
-->