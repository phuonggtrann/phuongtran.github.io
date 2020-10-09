---
layout: post
title: Convergence of Newton’s Method and Multiplicity of Roots
subtitle: Numerical Analysis
gh-repo: phuonggtrann/math446
gh-badge: [follow]

comments: true
---



	f(x)=(432x^4+72x^2+16x+1)e-8e^6x

	Root: -0.183517046673394
	8 steps,x_0= -0.15 
	M=  (f''(x))/(2f'(x))= 5.2517146174653 
	lim┬(i→ ∞ )⁡〖e_(i+1)/(e_i^2 )= 5.251627863404252〗
	Fast converge, took 6 times to find the actual root. Convergence rate is matched to the  3rd decimal place.
	MATLAB Code:

g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 1)*exp(1)-8*exp(6*x))/(16*exp(1)*(108*x^3+9*x+1)-48*exp(6*x));
numSteps = 8;
x = zeros(numSteps, 1);
x(1) = -0.15;
for i = 1:numSteps
    x(i + 1) = g(x(i));
end
r = x


g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 1)*exp(1) -8*exp(6*x)) / (16*exp(1)*(108*x^3+9*x +1)-48*exp(6*x));
numSteps = 8;
x = zeros(numSteps, 1);
x(1) = -0.15;
for i = 1:numSteps
x(i + 1) = g(x(i));
end
r = x(numSteps + 1); %best guess at the root
e = abs(x - r); % array of errors
ratio = zeros(numSteps + 1, 1);
for i = 1:numSteps
ratio(i) = e(i+1)/e(i)^2;
end
ratio(numSteps + 1) = 0;
ratio


	MATLAB Session:

>> newtonMed

r =
  -0.150000000000000
  -0.190719842751033
  -0.183779024018000
  -0.183517406588275
  -0.183517046674075
  -0.183517046673394
  -0.183517046673394
  -0.183517046673394
  -0.183517046673394
>> convrat

ratio =

   6.411647403089624
   5.049652553062774
   5.244116501504337
   5.251627863404252
                   0
                 NaN
                 NaN
                 NaN
                   0
	f(x)=(432x^4+72x^2+16x+2)e-8e^6x

	Root:   -0.135866537960991
	8 steps,x_0= -0.2 
	M=  (f''(x))/(2f'(x))= 6.1351327123367 
	lim┬(i→ ∞ )⁡〖e_(i+1)/(e_i^2 )=  6.134429454118887〗
	Fast converge, took 5 times to find the actual root. Convergence rate is matched to the 2nd  decimal place. I tried to keep the same initial guess and steps with A but the convergence rate doesn’t match with calculated M. Therefore, I changed my initial guess around to find the most accurate convergent rate. 
	MATLAB Code:

g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 2)*exp(1)-8*exp(6*x))/(16*exp(1)*(108*x^3+9*x+1)-48*exp(6*x));
numSteps = 8;
x = zeros(numSteps, 1);
x(1) = -0.2;
for i = 1:numSteps
    x(i + 1) = g(x(i));
end
r = x


g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 2)*exp(1) -8*exp(6*x)) / (16*exp(1)*(108*x^3+9*x +1)-48*exp(6*x));
numSteps = 8;
x = zeros(numSteps, 1);
x(1) = -0.2;
for i = 1:numSteps
x(i + 1) = g(x(i));
end
r = x(numSteps + 1); %best guess at the root
e = abs(x - r); % array of errors
ratio = zeros(numSteps + 1, 1);
for i = 1:numSteps
ratio(i) = e(i+1)/e(i)^2;
end
ratio(numSteps + 1) = 0;
ratio

	MATLAB Session:
>> newtonMed

r =

  -0.200000000000000
  -0.153517341018035
  -0.137580929788627
  -0.135884373201961
  -0.135866539912327
  -0.135866537960991
  -0.135866537960991
  -0.135866537960991
  -0.135866537960991
>> convrat

ratio =

   4.291361495443495
   5.502767318939148
   6.068184905509152
   6.134429454118887
                   0
                 NaN
                 NaN
                 NaN
                   0

	f(x)=(432x^4+72x^2+16x+3)e-8e^6x

Root:      0.166437598042732
	
	50 steps,x_0= -0.2 
	m/(m-1)= 0.80 
	lim┬(i→ ∞ )⁡〖e_(i+1)/e_i = 0.797294409762213〗
	Slower convergence than the first 2 therefore I suggest this is linear convergence. I tried to do it on paper and got m=5. The convergent rate, however, is hard to find. My closest is 0.7929
	MATLAB Code:

g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 3)*exp(1)-8*exp(6*x))/(16*exp(1)*(108*x^3+9*x+1)-48*exp(6*x));
numSteps = 50;
x = zeros(numSteps, 1);
x(1) = -0.2;
for i = 1:numSteps
    x(i + 1) = g(x(i));
end
r = x


g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 3)*exp(1) -8*exp(6*x)) / (16*exp(1)*(108*x^3+9*x +1)-48*exp(6*x));
numSteps = 50;
x = zeros(numSteps, 1);
x(1) = -0.2;
for i = 1:numSteps
x(i + 1) = g(x(i));
end
r = x(numSteps + 1); %best guess at the root
e = abs(x - r); % array of errors
ratio = zeros(numSteps + 1, 1);
for i = 1:numSteps
ratio(i) = e(i+1)/e(i);
end
ratio(numSteps + 1) = 0;
ratio

	MATLAB Session:
>> newtonMed

r =

  -0.200000000000000
  -0.122211138167402
  -0.061558670972538
  -0.014061336088604
   0.023274500122043
   0.052716753589336
   0.075996477796207
   0.094444340499453
   0.109089824713748
   0.120733920823678
   0.130002889453997
   0.137388408563619
   0.143277835872193
   0.147977221676006
   0.151728948747622
   0.154725349416518
   0.157119281765137
   0.159032387017940
   0.160561565128306
   0.161784071658871
   0.162761542474919
   0.163543178937582
   0.164168273613448
   0.164668227195491
   0.165068077928025
   0.165387961553820
   0.165643911299269
   0.165849234759850
   0.166013150654040
   0.166145949839538
   0.166255755483548
   0.166344244794039
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732
   0.166437598042732

>> convrat

ratio =

   0.787715937862012
   0.789874475145079
   0.791674946747691
   0.793152040535153
   0.794344674745697
   0.795290614321712
   0.796023505094132
   0.796571446909581
   0.796956439038507
   0.797194247939962
   0.797294409762213
   0.797260184735660
   0.797088339283947
   0.796768657524322
   0.796283084273980
   0.795604377517985
   0.794694106122693
   0.793499725362865
   0.791950360324902
   0.789950515927600
   0.787370879399192
   0.784034497715567
   0.779690565354201
   0.774015304277703
   0.766426485920017
   0.756153917902189
   0.741304157751835
   0.721403597133945
   0.687124508157959
   0.623499672525338
   0.513374036923966
                   0
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                 NaN
                   0

	f(x)=(432x^4+72x^2+16x+4)e-8e^6x

	Root:   0.436535483161814
	15 steps,x_0= 0.3 
	M=  (f''(x))/(2f'(x))= 8.159357331388
	lim┬(i→ ∞ )⁡〖e_(i+1)/(e_i^2 )=  8.159628955325694〗
	Fast converge, took 14 times to find the actual root (Maybe my initial guess is far from the actual root?). Convergence rate is matched to the 3rd decimal place. 
	MATLAB Code:

g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 2)*exp(1)-8*exp(6*x))/(16*exp(1)*(108*x^3+9*x+1)-48*exp(6*x));
numSteps = 8;
x = zeros(numSteps, 1);
x(1) = -0.2;
for i = 1:numSteps
    x(i + 1) = g(x(i));
end
r = x


g = @(x) x - ((432*x^4 + 72*x^2 + 16*x + 2)*exp(1) -8*exp(6*x)) / (16*exp(1)*(108*x^3+9*x +1)-48*exp(6*x));
numSteps = 8;
x = zeros(numSteps, 1);
x(1) = -0.2;
for i = 1:numSteps
x(i + 1) = g(x(i));
end
r = x(numSteps + 1); %best guess at the root
e = abs(x - r); % array of errors
ratio = zeros(numSteps + 1, 1);
for i = 1:numSteps
ratio(i) = e(i+1)/e(i)^2;
end
ratio(numSteps + 1) = 0;
ratio

	MATLAB Session:
>> newtonMed

r =

   0.300000000000000
   1.305059983205165
   1.156385412877226
   1.016784876471364
   0.888532141110720
   0.773445973920808
   0.672757072883677
   0.587375176400075
   0.518674086442343
   0.469578354405758
   0.443608494275333
   0.436922633928443
   0.436536702528404
   0.436535483173946
   0.436535483161814
   0.436535483161814
   0.436535483161814
   0.436535483161814
   0.436535483161814
   0.436535483161814
   0.436535483161814

>> convrat

ratio =

  46.589817672663180
   0.954284387871134
   1.119774986150105
   1.342473846065110
   1.649088970316637
   2.081088356005699
   2.703189331216577
   3.610073404650149
   4.897598179094880
   6.478116952784676
   7.738761148001843
   8.135308834856726
   8.159628955325694
                   0
                 Inf
                   0
                 Inf
                   0
                 Inf
                   0

### Conclusion: <br/>
**Function roots:** <br/>
	(A) -0.183517046673394<br/>
	(B) -0.135866537960991<br/>
	(C) 0.166437598042732<br/>
	(D) 0.436535483161814<br/>
- Function A and B is the easiest to find as they are fast convergent (less than 10 steps needed) therefore it’s quadratic convergence.
- Function D is harder to find but after changing my initial guess around, the actual root was found in about 15 steps, in which, I considered it to be a quadratic convergence too. 
- Function C is the hardest. Finding its actual root is easy (I keep increase the steps and changing my initial guess). However, it took more than 40 steps to get the actual root. To double check, I use quadratic formula to find the convergence rate first then I tried the linear convergent second. As a result, I am confident that function C’s actual root is linear convergent. 
