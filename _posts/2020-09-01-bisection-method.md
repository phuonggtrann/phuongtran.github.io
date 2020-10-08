<!-- Copy and paste the converted output. -->

<!-----
NEW: Check the "Suppress top comment" option to remove this info from the output.

Conversion time: 0.637 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β29
* Thu Oct 08 2020 16:17:06 GMT-0700 (PDT)
* Source doc: Math 446 - Project1

WARNING:
You have some equations: look for ">>>>>  gd2md-html alert:  equation..." in output.

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 1; ALERTS: 3.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



```
Final conclusion:
For (A): f(x)=(432x4 + 72x2 + 16x + 1)e − 8e6x, root = -0.183517
For (B): f(x)=(432x4 + 72x2 + 16x + 2)e − 8e6x, root = -0.135866
For (C): f(x)=(432x4 + 72x2 + 16x + 3)e − 8e6x, root = 0.166992
For (D): f(x)=(432x4 + 72x2 + 16x + 4)e − 8e6x, root = 0.436535

According to given information, each of the functions has exactly one root between -1 and 1. Therefore, f(-1)*f(1) < 0 and my starting interval is [-1, 1].

Function (A): f(x) = (432x4 + 72x2 + 16x + 1)e − 8e6x   
	[-1, 1]: root = -0.183516
	[-0.2, 1]: root = -0.183516
	[-0.2, 0.2]: root = -0.183517
	[-0.2, 0]: root = -0.183517
	[-0.19, 0]: root = -0.183517
	[-0.19, -0.17]: root = -0.183517
CONCLUSION:
After trunking down the interval from [-1,1] to [-0.19, -0.17] and since the results of the last 4 intervals are consistent (-0.183517 for the last 4 intervals and -0.183516 for the first 2 trials), I am confident that the root is close to -0.183517. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is 7.64


<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: equation: use MathJax/LaTeX if your publishing platform supports it. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

, in which, extremely close to 0. 
MATLAB SESSION: 
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

Function (B): f(x) = (432x4 + 72x2 + 16x + 2)e − 8e6x   
	[-1, 1]: root = -0.135866
	[-1, 0]: root = -0.135866
	[-0.5, 0]: root = -0.135866
	[-0.2, -0.1]: root = -0.135866
	[-0.14, -0.13]: root = -0.135866
	[-0.136, -0.13]: root = -0.135866
CONCLUSION:
After trunking down the interval from [-1,1] to [-0.136, -0.13] and since the results of all tested intervals are consistent (-0.135866), I am confident that the root is close to -0.135866. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is -8.75


<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: equation: use MathJax/LaTeX if your publishing platform supports it. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

, in which, extremely close to 0. 
MATLAB SESSION: 
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

Function (C): f(x) = (432x4 + 72x2 + 16x + 3)e − 8e6x   
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

Function (D): f(x) = (432x4 + 72x2 + 16x + 4)e − 8e6x   
[-1, 1]: root = 0.436535
[0,1]: root = 0.436535
[0,0.8]: root = 0.436535
[0, 0.5]: root = 0.436535
[0.4, 0.5]: root = 0.436535
CONCLUSION:
After trunking down the interval from [-1,1] to [-0.136, -0.13] and since the results of all tested intervals are consistent (0.436535), I am confident that the root is close to 0.436535. Therefore, I am sure that my first 6 digits of the root is correct because of the consistency that I stated above. To double check my work, I tried f(xc) where xc is my final guess and the results is 1.18


<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: equation: use MathJax/LaTeX if your publishing platform supports it. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

, in which, extremely close to 0. 
MATLAB SESSION:
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
