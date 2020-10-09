---
layout: post
title: Floating Point Operations Rounding Errors
subtitle: Numerical Analysis
gh-repo: phuonggtrann/math446
gh-badge: [follow]

comments: true
---

## How do floating point operation rounding errors can reduce the accuracy of linear equation (y = Ax + b). It is possible to lose all correct digits ?<br/>

The goal is to solved for unknown x with the smallest possible relative foward erroe (RFE). It is done with 3 differents size (n) and 3 different nxn matrices for 1 ≤ i, j ≤ n:<br/>
- A1(i, j) = (i + 1/ sin(i + j))/(j + cos(i + j) + 1)
- A2(i, j) = (i + sin(i + j))/(i + j + 1)
- A3(i, j) = (i + sin(i + j))/(j + cos(i + j) + 1)

### A1(i, j) = (i + 1/ sin(i + j))/(j + cos(i + j) + 1)<br/>
| size | Relative Backward Error (RBE) |Relative Foward Error (RFE) | Error Magnification Factor (EMF) | Condition Number (COND)
| :------ |:--- | :--- | :--- | :--- |
| 6 | 1.377811512381070 | 8.992806499463768e-15 | 6.526877166182781e-15 | 59.051023822469567 
| 12 | 1.426836226818009 | 1.887379141862766e-14 | 1.322772092822324e-14 | 7.219563930906002e+03
| 18 | 1.007589946234150 | 1.472155730652958e-13 | 1.461066315870969e-13 | 57.582507993251738


**MATLAB CODE:**

```
GausseLim.m
%% Elimination
for i = 1:n-1
    for j = i+1:n
        m = a(j,i)/a(i,i);
        for k = i:n
            a(j,k) = a(j,k)-m*a(i,k);
        end
        b(j) = b(j) - m*b(i);
    end
end
 
%% Back Sub
x = zeros(n,1);
for i = n:-1:1
    for j = i+1:n
        b(i) = b(i) - a(i,j)*x(j);
    end
    x(i) = b(i)/a(i,i);
end
x; % This is solution

GL_run.m
n = 6 ; % n might be 6, 12, 18
aorig = zeros(n,n);
for i = 1:n
    for j = 1:n
        % This depend on function A1, A2, or A3
        aorig(i,j) =  (i + 1/ sin(i + j))/(j + cos(i + j) + 1));
    end
end
c = ones(n,1);
b = aorig*c;
a = aorig;
GausseLim
 
% Calculate RBE, RFE, EMF, condition number
%% Not sure why RBE and COND is different when I use a instead of aorig
% Decide to go with aorig because original always better(no rounding)
RBE = norm(aorig*x - b, inf)/norm(b, inf)
RFE = norm(c-x, inf)/norm(c,inf)
EMF = RBE/RFE
COND = cond(aorig,inf)
A1(i,j)=  ((i+1)/(sin⁡(i+j)))⁄(j+cos⁡(i+j)+1)
```

**MATLAB SESSION:**

```
>> gl_run
n =
     6
RBE =
   1.377811512381070
RFE =
     8.992806499463768e-15
EMF =
     6.526877166182781e-15
COND =
  59.051023822469567
>> gl_run
n =
    12
RBE =
   1.426836226818009
RFE =
     1.887379141862766e-14
EMF =
     1.322772092822324e-14
COND =
     7.219563930906002e+03
>> gl_run
n =
    18
RBE =
   1.007589946234150
RFE =
     1.472155730652958e-13
EMF =
     1.461066315870969e-13
COND =
  57.582507993251738
A2(i,j)=  (i+sin⁡(i+j))⁄(j+j+1)
>> gl_run
n =
     6
RBE =
   2.370433142701478
RFE =
     3.889324418082651e-10
EMF =
     1.640765288005617e-10
COND =
     2.259665789391311e+06
>> gl_run
n =
    12
RBE =
   4.347366764479971
RFE =
     2.415508971687075e-04
EMF =
     5.556257621102775e-05
COND =
     5.146361740838818e+12
>> gl_run
n =
    18
RBE =
   6.745749826083214
RFE =
  22.666835057243510
EMF =
   3.360165384372779
Warning: Matrix is close to singular or badly scaled. Results may
be inaccurate. RCOND =  3.177575e-18. 
> In cond (line 46)
  In gl_run (line 19)
COND =
     2.663035149379290e+17
A3(i,j)=  (i+sin⁡(i+j))⁄(j+cos⁡(i+j)+1)
>> gl_run
n =
     6
RBE =
   8.319901808803753
RFE =
     4.485301019485632e-14
EMF =
     5.391050426508021e-15
COND =
     8.829339368344521e+02
>> gl_run
n =
    12
RBE =
  21.312719339396107
RFE =
     2.722400083143839e-11
EMF =
     1.277359326977830e-12
COND =
     1.852023667474059e+06
>> gl_run
n =
    18
RBE =
  36.687933440269994
RFE =
     9.979205684018666e-09
EMF =
     2.720023928375625e-10
COND =
     4.549076021914460e+08
```
