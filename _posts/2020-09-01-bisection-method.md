---
layout: post
title: Bisection Method
subtitle: Numerical Analysis
gh-repo: phuonggtrann/math446
gh-badge: [follow]

comments: true
---

## Solving Equation by Bisection Method

According to given information, each of the functions has exactly one root between -1 and 1. Therefore, f(-1)*f(1) < 0 and my starting interval is [-1, 1].

**Function (A): f(x) = (432x4 + 72x2 + 16x + 1)e − 8e6x**   

> Interval [-1, 1 ]: root = -0.183516

> Interval [-0.2, 1]: root = -0.183516 

> Interval [-0.2, 0.2]: root = -0.183517 

> Interval [-0.2, 0]: root = -0.183517 

> Interval [-0.19, 0]: root = -0.183517 

> Interval [-0.19, -0.17]: root = -0.183517 

> After trunking down the interval from [-1,1] to [-0.19, -0.17] and since the results of the last 4 intervals are consistent (-0.183517 for the last 4 intervals and -0.183516 for the first 2 trials), I am confident that the root is close to -0.183517. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is 7.64, in which, extremely close to 0. 

**MATLAB SESSION:** 
```
>> format long
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 1)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)

xc =

  -0.183516979217529

>> xc = bisect(f,-0.2,1,0.0000005)

xc =

  -0.183516788482666

>> xc = bisect(f,-0.2,0.2,0.0000005)

xc =

  -0.183517074584961

>> xc = bisect(f,-0.2,0,0.0000005)

xc =

  -0.183517074584961

>> xc = bisect(f,-0.19,0,0.0000005)

xc =

  -0.183517093658447

>> xc = bisect(f,-0.19,-0.17,0.0000005)

xc =

  -0.183517150878906

>> f(xc)

ans =

     7.641771270883169e-06
```
**Function (B): f(x) = (432x4 + 72x2 + 16x + 2)e − 8e6x**  

> Interval [-1, 1]: root = -0.135866

> Interval [-1, 0]: root = -0.135866

> Interval [-0.5, 0]: root = -0.135866

> Interval [-0.2, -0.1]: root = -0.135866

> Interval [-0.14, -0.13]: root = -0.135866

> Interval [-0.136, -0.13]: root = -0.135866
	
> After trunking down the interval from [-1,1] to [-0.136, -0.13] and since the results of all tested intervals are consistent (-0.135866), I am confident that the root is close to -0.135866. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is -8.75, in which, extremely close to 0. 

**MATLAB SESSION:**
```
>> format long
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 2)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)

xc =

  -0.135866641998291

>> xc = bisect(f,-1,0,0.0000005)

xc =

  -0.135866641998291

>> xc = bisect(f,-0.5,0,0.0000005)

xc =

  -0.135866641998291

>> xc = bisect(f,-0.2,-0.1,0.0000005)

xc =

  -0.135866165161133

>> xc = bisect(f,-0.14,-0.13,0.0000005)

xc =

  -0.135866394042969

>> xc = bisect(f,-0.136,-0.13,0.0000005)

xc =

  -0.135866333007813

>> f(xc)

ans =

    -8.754228302265687e-06
```

**Function (C): f(x) = (432x4 + 72x2 + 16x + 3)e − 8e6x**  

> Interval [-1, 1]: root = 0.166992

> Interval [0,1]: root = 0.166992

> Interval [0, 0.5]: root = 0.166992

> Interval [0, 0.2]: root = 0.166796

> Interval [0.1, 0.2]: root = 0.166796

> Interval [0.10, 0.18]: root = 0.166992

> Interval [0.1, 0.17]: root = 0.166958

> Interval [0.15, 0.17]: root = 0.166992

> Interval [0.16, 0.17]: root = 0.166992


> After trunking down the interval from [-1,1] to [0.16, 0.17] and since the results of all tested intervals are fluctuating, I am not confident that I got the first 6 digits of the root correct. However, my best guess is that the root is somewhere close to 0.166992 since it happens 6 out of 9 tested intervals. Additionally, I also try to plug my best root in the equation to see and surprisingly, I get 0 therefore I have more confidence to state that the actual root is 0.166992 and that I got my first 6 digits of the root correctly. 

**MATLAB SESSION:**
```
>> format long
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 3)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)

xc =

   0.166992187500000

>> xc = bisect(f,0,1,0.0000005)

xc =

   0.166992187500000

>> xc = bisect(f,0,0.5,0.0000005)

xc =

   0.166992187500000

>> xc = bisect(f,0,0.2,0.0000005)

xc =

   0.166796875000000

>> xc = bisect(f,0.1,0.2,0.0000005)

xc =

   0.166796875000000

>> xc = bisect(f,0.10,0.18,0.0000005)

xc =

   0.166992187500000

>> xc = bisect(f,0.10,0.17,0.0000005)

xc =

   0.166958007812500

>> xc = bisect(f,0.15,0.17,0.0000005)

xc =

   0.166992187500000

>> xc = bisect(f,0.16,0.17,0.0000005)

xc =

   0.166992187500000

>> f(xc)

ans =

     0
```

**Function (D): f(x) = (432x4 + 72x2 + 16x + 4)e − 8e6x**
> Interval [-1, 1]: root = 0.436535

> Interval [0,1]: root = 0.436535

> Interval [0,0.8]: root = 0.436535

> Interval [0, 0.5]: root = 0.436535

> Interval [0.4, 0.5]: root = 0.436535

> After trunking down the interval from [-1,1] to [-0.136, -0.13] and since the results of all tested intervals are consistent (0.436535), I am confident that the root is close to 0.436535. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is 1.18, in which, extremely close to 0. 

**MATLAB SESSION:**
```
>> format long
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 4)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)

xc =

   0.436535358428955

>> xc = bisect(f,0,1,0.0000005)

xc =

   0.436535358428955

>> xc = bisect(f,0,0.8,0.0000005)

xc =

   0.436535263061523

>> xc = bisect(f,0,0.5,0.0000005)

xc =

   0.436535358428955

>> xc = bisect(f,0.4,0.5,0.0000005)

xc =

   0.436535263061523

>> f(xc)

ans =

     1.181522007698277e-05
```
### Final conclusion:
> For (A): f(x)=(432x4 + 72x2 + 16x + 1)e − 8e6x, root = -0.183517 <br/>
> For (B): f(x)=(432x4 + 72x2 + 16x + 2)e − 8e6x, root = -0.135866<br/>
> For (C): f(x)=(432x4 + 72x2 + 16x + 3)e − 8e6x, root = 0.166992<br/>
> For (D): f(x)=(432x4 + 72x2 + 16x + 4)e − 8e6x, root = 0.436535<br/>

**MATLAB CODE:**
```
%Program 1.1 Bisection Method
%Computes approximate solution of f(x)=0
%Input: function handle f; a,b such that f(a)*f(b)<0,
% and tolerance tol
%Output: Approximate solution xc
function xc = bisect(f,a,b,tol)
if sign(f(a)) * sign(f(b)) >= 0
    error("f(a)f(b)<0 not satisfied!") %ceases execution
end
fa = f(a);
fb = f(b);
while (b - a) / 2 > tol
    c = (a + b) / 2;
    fc = f(c);
    if fc == 0 %c is a solution, done
        break
    end     
    if sign(fc) * sign(fa)<0 %a and c make the new interval
            b = c; fb = fc;
    else %c and b make the new interval
            a = c; fa = fc;
    end
end
xc = (a + b) / 2; %new midpoint is best estimate
```
