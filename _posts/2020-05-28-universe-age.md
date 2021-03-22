---
layout: post
title: Accepted Age of the Universe 
subtitle: Can it be trusted?
gh-repo: phuonggtrann/DS-Unit-1-Build
gh-badge: [follow]

comments: true
---

I was wondering if the accepted age of the universe is trust-worthy. I decided to take it upon myself to explore the validity of this value. The universe we live in isn’t static and it continues to expand. Because of its expanding nature, light from other galaxies observed from Earth appear to be redshifted the further away they are from us. The universe contains billions of galaxies, with each galaxy containing millions of stars. By calculating their distance away from us, I was able to find out the constant rate that causes the expansion of the universe. Once I knew this constant, I could essentially turn back time to the point of the Big Bang to determine the age of the universe. I started by collecting valuable data/information. In order to calculate the age of the universe, I was able to collect data from approximately 4320 galaxies:

| Galaxy Name | Modulus Distance | Recession Velocity | Actual Distance |
| :------ |:--- | :--- | :--- |
| UGC12914 | 33.49 | 4522.0 | 49.888449 |
| PGC000143	 | 24.94 | -54.0 | 0.972747 |
| NGC7814 | 30.80	 | 1204.0 | 14.454398 |
| UGC00014 | 35.03 | 7428.0 | 101.391139 |

Using the above data, I created a graph with x as actual distance and y as recession velocity.

![Imgur](https://i.imgur.com/JfoJOMw.png)

Having the age range, I then tried to find a more specific number to represent the universe's age. I then use linear regression to find the slope, which, base on the Hubble's law, is the Hubble constant. 

![Imgur](https://i.imgur.com/vFeIKZh.png)

Since the Big Bang, the universe has expanded by the rate of the Hubble constant. So, in order to turn back time, I needed to take the Hubble constant out of the equation. I can do so by essentially multiplying the Hubble constant by its inverse.

~~~Python
new_hubble_const = model2[0]/(3.08*(1e19))
new_age = 1/(new_hubble_const)
~~~

Using the above code, the result for the age of the universe is in seconds. However, the accepted value is in billions of years. Therefore, to compare them, I needed to convert the seconds into billions of years. At the end of it all, based on the data set and algorithms, the age of the universe is 13.825 billion years. The accepted value for the age of the universe is 13.9 billion years. Therefore with a margin error of 0.5%, I can positively say that I can trust the accepted value.

Check out my work [here](https://colab.research.google.com/drive/1bF9nHEGGYvuFaLh7_4esDXt5HfO8d1yn?authuser=3#scrollTo=IAuq9LhvXRUU)
