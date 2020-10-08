Phuong Tran MTH446 – Project 1 09/01/2020

**Final conclusion:**

For (A): f(x)=(432x4 + 72x2 + 16x + 1)e − 8e6x, root = -0.183517

For (B): f(x)=(432x4 + 72x2 + 16x + 2)e − 8e6x, root = -0.135866

For (C): f(x)=(432x4 + 72x2 + 16x + 3)e − 8e6x, root = 0.166992

For (D): f(x)=(432x4 + 72x2 + 16x + 4)e − 8e6x, root = 0.436535

According to given information, each of the functions has exactly one root between -1 and 1. Therefore, f(-1)\*f(1) \&lt; 0 and my starting interval is [-1, 1].

**Function (A): f(x) = (432x****4 **** + 72x ****2** **+ 16x + 1)e − 8e****6x  ****  **

[-1, 1]: root = -0.183516

[-0.2, 1]: root = -0.183516

[-0.2, 0.2]: root = -0.183517

[-0.2, 0]: root = -0.183517

[-0.19, 0]: root = -0.183517

[-0.19, -0.17]: root = -0.183517

CONCLUSION:

After trunking down the interval from [-1,1] to [-0.19, -0.17] and since the results of the last 4 intervals are consistent (-0.183517 for the last 4 intervals and -0.183516 for the first 2 trials), I am confident that the root is close to -0.183517. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is 7.64e-6, in which, extremely close to 0.

MATLAB SESSION:

\&gt;\&gt; format long

\&gt;\&gt; f = @(x) (432\*x^4 + 72\*x^2 + 16\*x + 1)\*exp(1) - 8\*exp(6\*x);

\&gt;\&gt; xc = bisect(f,-1,1,0.0000005)

xc =

  -0.183516979217529

\&gt;\&gt; xc = bisect(f,-0.2,1,0.0000005)

xc =

  -0.183516788482666

\&gt;\&gt; xc = bisect(f,-0.2,0.2,0.0000005)

xc =

  -0.183517074584961

\&gt;\&gt; xc = bisect(f,-0.2,0,0.0000005)

xc =

  -0.183517074584961

\&gt;\&gt; xc = bisect(f,-0.19,0,0.0000005)

xc =

  -0.183517093658447

\&gt;\&gt; xc = bisect(f,-0.19,-0.17,0.0000005)

xc =

  -0.183517150878906

\&gt;\&gt; f(xc)

ans =

     7.641771270883169e-06

**Function (B): f(x) = (432x****4 **** + 72x ****2** **+ 16x + 2)e − 8e****6x  ****  **

[-1, 1]: root = -0.135866

[-1, 0]: root = -0.135866

[-0.5, 0]: root = -0.135866

[-0.2, -0.1]: root = -0.135866

[-0.14, -0.13]: root = -0.135866

[-0.136, -0.13]: root = -0.135866

CONCLUSION:

After trunking down the interval from [-1,1] to [-0.136, -0.13] and since the results of all tested intervals are consistent (-0.135866), I am confident that the root is close to -0.135866. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is -8.75e-6, in which, extremely close to 0.

MATLAB SESSION:

\&gt;\&gt; format long

\&gt;\&gt; f = @(x) (432\*x^4 + 72\*x^2 + 16\*x + 2)\*exp(1) - 8\*exp(6\*x);

\&gt;\&gt; xc = bisect(f,-1,1,0.0000005)

xc =

  -0.135866641998291

\&gt;\&gt; xc = bisect(f,-1,0,0.0000005)

xc =

  -0.135866641998291

\&gt;\&gt; xc = bisect(f,-0.5,0,0.0000005)

xc =

  -0.135866641998291

\&gt;\&gt; xc = bisect(f,-0.2,-0.1,0.0000005)

xc =

  -0.135866165161133

\&gt;\&gt; xc = bisect(f,-0.14,-0.13,0.0000005)

xc =

  -0.135866394042969

\&gt;\&gt; xc = bisect(f,-0.136,-0.13,0.0000005)

xc =

  -0.135866333007813

\&gt;\&gt; f(xc)

ans =

    -8.754228302265687e-06

**Function (C): f(x) = (432x****4 **** + 72x ****2** **+ 16x + 3)e − 8e****6x  ****  **

[-1, 1]: root = 0.166992

[0,1]: root = 0.166992

[0, 0.5]: root = 0.166992

[0, 0.2]: root = 0.166796

[0.1, 0.2]: root = 0.166796

[0.10, 0.18]: root = 0.166992

[0.1, 0.17]: root = 0.166958

[0.15, 0.17]: root = 0.166992

[0.16, 0.17]: root = 0.166992

CONCLUSION:

After trunking down the interval from [-1,1] to [0.16, 0.17] and since the results of all tested intervals are fluctuating, I am not confident that I got the first 6 digits of the root correct. However, my best guess is that the root is somewhere close to 0.166992 since it happens 6 out of 9 tested intervals. Additionally, I also try to plug my best root in the equation to see and surprisingly, I get 0 therefore I have more confidence to state that the actual root is 0.166992 and that I got my first 6 digits of the root correctly.

MATLAB SESSION:

\&gt;\&gt; format long

\&gt;\&gt; f = @(x) (432\*x^4 + 72\*x^2 + 16\*x + 3)\*exp(1) - 8\*exp(6\*x);

\&gt;\&gt; xc = bisect(f,-1,1,0.0000005)

xc =

   0.166992187500000

\&gt;\&gt; xc = bisect(f,0,1,0.0000005)

xc =

   0.166992187500000

\&gt;\&gt; xc = bisect(f,0,0.5,0.0000005)

xc =

   0.166992187500000

\&gt;\&gt; xc = bisect(f,0,0.2,0.0000005)

xc =

   0.166796875000000

\&gt;\&gt; xc = bisect(f,0.1,0.2,0.0000005)

xc =

   0.166796875000000

\&gt;\&gt; xc = bisect(f,0.10,0.18,0.0000005)

xc =

   0.166992187500000

\&gt;\&gt; xc = bisect(f,0.10,0.17,0.0000005)

xc =

   0.166958007812500

\&gt;\&gt; xc = bisect(f,0.15,0.17,0.0000005)

xc =

   0.166992187500000

\&gt;\&gt; xc = bisect(f,0.16,0.17,0.0000005)

xc =

   0.166992187500000

\&gt;\&gt; f(xc)

ans =

     0

**Function (D): f(x) = (432x****4 **** + 72x ****2** **+ 16x + 4)e − 8e****6x  ****  **

[-1, 1]: root = 0.436535

[0,1]: root = 0.436535

[0,0.8]: root = 0.436535

[0, 0.5]: root = 0.436535

[0.4, 0.5]: root = 0.436535

CONCLUSION:

After trunking down the interval from [-1,1] to [-0.136, -0.13] and since the results of all tested intervals are consistent (0.436535), I am confident that the root is close to 0.436535. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is 1.18e-5, in which, extremely close to 0.

MATLAB SESSION:

\&gt;\&gt; format long

\&gt;\&gt; f = @(x) (432\*x^4 + 72\*x^2 + 16\*x + 4)\*exp(1) - 8\*exp(6\*x);

\&gt;\&gt; xc = bisect(f,-1,1,0.0000005)

xc =

   0.436535358428955

\&gt;\&gt; xc = bisect(f,0,1,0.0000005)

xc =

   0.436535358428955

\&gt;\&gt; xc = bisect(f,0,0.8,0.0000005)

xc =

   0.436535263061523

\&gt;\&gt; xc = bisect(f,0,0.5,0.0000005)

xc =

   0.436535358428955

\&gt;\&gt; xc = bisect(f,0.4,0.5,0.0000005)

xc =

   0.436535263061523

\&gt;\&gt; f(xc)

ans =

     1.181522007698277e-05

MATLAB CODE:

%Program 1.1 Bisection Method

%Computes approximate solution of f(x)=0

%Input: function handle f; a,b such that f(a)\*f(b)\&lt;0,

% and tolerance tol

%Output: Approximate solution xc

function xc = bisect(f,a,b,tol)

if sign(f(a)) \* sign(f(b)) \&gt;= 0

error(&quot;f(a)f(b)\&lt;0 not satisfied!&quot;) %ceases execution

end

fa = f(a);

fb = f(b);

while (b - a) / 2 \&gt; tol

c = (a + b) / 2;

fc = f(c);

if fc == 0 %c is a solution, done

break

end

if sign(fc) \* sign(fa)\&lt;0 %a and c make the new interval

b = c; fb = fc;

else%c and b make the new interval

a = c; fa = fc;

end

end

xc = (a + b) / 2; %new midpoint is best estimate
