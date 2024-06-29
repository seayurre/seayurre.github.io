---
layout: post
title: "[Introduction to algorithms] Asymptotic Analysis"
subtitle: 
categories: [Introduction to algorithms]
tags: []
use_math : true
---
*based on KAIST CS300 course, CLRS textbook

### Running Time of an Algorithm

알고리즘의 실행 시간을 분석할 때 사용하는 Asymptotic Analysis(점근적 분석)에 대해서 알아보자.

알고리즘의 실행 시간은 실행하는 컴퓨터의 성능, Input의 종류(정렬 알고리즘을 예로 들면 input이 이미 sorted이냐 아니냐에 따라 실행시간이 달라질 수 있다), Input size $n$ 등 다양한 요인에 의해 결정된다. 이 중에서도 가장 결정적인 요인이 Input size $n$으로, 알고리즘의 실행 시간은 이 $n$을 변수로 하는 함수 $T(n)$으로 표기한다.

### Kinds of Analysis
- Worst Case(usually)
어떤 input size $n$에 대해서 실행 시간 $T(n)$이 최대가 되는 경우이다.  

- Average Case(sometimes)
어떤 input size $n$에 대해서 $T(n)$의 기댓값을 Average case running time이라 한다. 
Input이 어떠한 통계적인 분포를 따른다고 가정하고, 이를 이용해서 분석한다.  

- Best Case(bogus)
몇몇 테스트케이스에만 엄청나게 빠르게 작동하는 코드를 짜면 그걸 Best case라고 할 수도 있기 때문에, Best Case는 잘 논하지 않는다.


알고리즘의 실행 시간을 분석할 때에는 보통 **Worst Case Running Time을 고려한다.**
Worst Case Running Time은 어떤 알고리즘의 실행 시간 $T(n)$의 상한(upper bound)을 제공해 주기 때문에 **'이 알고리즘이 적어도 이 시간 안에는 작동된다'** 를 알 수가 있다. 
또한 Worst Case Running Time이 Average Case Running Time과 거의 유사하거나, Worst Case가 자주 발생하는 알고리즘도 있기 때문에 여러모로 알고리즘의 실행 시간을 분석할 때에는 Worst Case Running Time을 보는 것이 적절하다. 

### Asymptotic Analysis
상술하였듯 알고리즘의 실행 시간은 input size $n$에 대한 아주 깔끔한 식으로 딱 정해지는게 아니라, 컴퓨터의 성능을 비롯한 다양한 요인에 의해 영향을 받는다. 
그래서 어떤 알고리즘의 실행시간을 표현할 때 Asymptotic Analysis(점근적 분석)이라는 것을 사용하며, 이걸 간단히 표현하면 '$n$이 점점 증가함에 따라 $T(n)$이 어떻게 증가하는가를 살펴보는 것' 이라고 할 수 있을 것 같다. 

Asymptotic Analysis를 통해 알고리즘의 실행 시간 $T(n)$을 분석할 때는 다양한 표기법(Asymptotic Notation)을 사용한다.

#### O-notation(Big-O notation)
>어떤 함수 $g(n)$에 대해서, 모든  $n \geq n_0$ 인  $n$ 에 대해  $0\leq f(n) \leq cg(n)$를 만족하는 어떤 양의 상수  $c, n_0$ 가 존재하면 $f \in O(g) $로 표기한다.

이 때 $g(n)$은 $f(n)$의 **Asymptotic Upper Bound**라고 한다. 

조금 더 쉬운 말로 풀어쓰자면, 양수 n이 점점 커지다가 특정 상수를 넘어가면 그 뒤로는 g(n)의 양의 상수배가 f(n)보다 반드시 크거나 같아지는 경우이다. 
(엄밀하진 않지만) 직관적으로는 'g(n)이 f(n)보다 크거나 같다' 정도로 받아들일 수 있다. 

#### Ω-notation(Big-Omega notation)
>어떤 함수  $g(n)$에 대해서, 모든  $n \geq n_0$인 $n$에 대해  $0\leq cg(n) \leq f(n)$를 만족하는 어떤 양의 상수  $c, n_0$ 가 존재하면 $f \in Ω(g) $로 표기한다.

이 때 g(n)은 f(n)의 **Asymptotic Lower Bound**라고 한다. 
O-notation에서와는 다르게 이번에는 g(n)의 상수배가 어느 시점부터 f(n)보다 항상 작거나 같아지는 경우이다.

#### o-notation(Small-O notation)
>어떤 함수  $g(n)$에 대해서, 어떠한 양의 상수  $c, n_0$에 대해서도  $n \geq n_0$일 때  $0\leq f(n) < cg(n)$ 이면  $f \in o(g) $로 표기한다.

즉 모든 양의 상수 $c, n_0$에 대해서 저 관계가 성립해야 하는 것이다.
직관적으로는 'f(n)이 g(n)보다 확실히 작다!!' 라고 생각할 수 있다. 

이 때는 '**f(n) is asymptotic smaller than g(n)**'이라고 표현한다. 

#### ⍵-notation(Small-Omega notation)
>어떤 함수  $g(n)$에 대해서, 어떠한 양의 상수  $c, n_0$에 대해서도  $n \geq n_0$일 때  $0\leq cg(n) < f(n)$ 이면  $f \in \omega(g) $로 표기한다.

이 경우 역시 직관적으로 'f(n)이 g(n)보다는 확실히 크다!!' 라고 생각할 수 있고, '**f(n) is asymptotic larger than g(n)**'이라고 표현한다. 


Big-O와 Small-O, Big-Omega와 Small-Omega의 정의에서 그냥 등호 하나만 사라지는 게 차이점이 아님을 주의해야 한다. 
  
    
#### Θ-notation(Big-Theta notation)
>어떤 함수 $g(n)$에 대해서, 모든  $n \geq n_0$인  $n$에 대해  $c_1 g(n)\leq f(n) \leq c_2 g(n)$를 만족하는 어떤 양의 상수  $c_1, c_2, n_0$ 가 존재하면 $f \in \theta(g) $로 표기한다.

g(n)을 f(n)에 대한 **asymptotic tight bound**라고 한다. 

그리고 Θ-notation에 대한 유용한 Theorem이 존재한다.
>$f(n) = \theta (g(n))$ if and only if $f(n) = O(g(n))$ and $f(n)= \Omega(g(n))$


  
  
#### 예시 
1. 다항식 $f(n) = n^3 + 3n^2+1234$는 $\theta(n^3)$이다.
2. Insertion Sort(삽입정렬)의 Worst Case Running Time은 $O(n^2)$이다.