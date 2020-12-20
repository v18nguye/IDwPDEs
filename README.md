# Partial Differential Equations (PDEs) for Image Denoising

Image Denoising can be cast as an inverse problem to which we exploit PDEs to solve. There are several
approaches dealing with Inverse Problem, resumed in the figure below.

![Alt](images/ci.png)

__Author: Khoa NGUYEN__

## Background
In theory, we are looking for a solution <img src="svgs/9a816d3409cff0a970fc73cfd9ea3e75.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=22.831056599999986pt/> by minimizing the following cost:

<img src="svgs/2101f41ba7f16ddcc28beb79496af43b.svg?invert_in_darkmode" align=middle width=165.32312444999997pt height=24.65753399999998pt/>

with <img src="svgs/b53168d28010bd4c02d259734142b0c2.svg?invert_in_darkmode" align=middle width=212.12325915pt height=24.65753399999998pt/>

where <img src="svgs/e06ba62f2bfed5cf8a0fae61c45d4ac8.svg?invert_in_darkmode" align=middle width=11.92007189999999pt height=22.465723500000017pt/> is a set of possible solutions whose element values corresponding {0,...,255} for RGB images.

The <img src="svgs/a073111060fab93e704125a7248622dc.svg?invert_in_darkmode" align=middle width=77.08567184999998pt height=24.65753399999998pt/> term represents consistency between the observation <img src="svgs/6c4adbc36120d62b98deef2a20d5d303.svg?invert_in_darkmode" align=middle width=8.55786029999999pt height=14.15524440000002pt/> and and the solution <img src="svgs/6dbb78540bd76da3f1625782d42d6d16.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=14.15524440000002pt/>, while the <img src="svgs/80277ffb5e68aa9cae04225225d5faa4.svg?invert_in_darkmode" align=middle width=41.88715739999999pt height=22.465723500000017pt/>
term is the regulator which depicts an expected property for the solution. In the project, we will expect to study the impact of different
regularization terms.

**Data Term**

<img src="svgs/3006af981807a1b114110bc539ed06d2.svg?invert_in_darkmode" align=middle width=214.04469075000003pt height=26.76175259999998pt/>

The data term considered here is the norm of difference between the solution <img src="svgs/6dbb78540bd76da3f1625782d42d6d16.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=14.15524440000002pt/> and the observation <img src="svgs/6c4adbc36120d62b98deef2a20d5d303.svg?invert_in_darkmode" align=middle width=8.55786029999999pt height=14.15524440000002pt/>,
which is integrated through the image's spatial information <img src="svgs/9432d83304c1eb0dcb05f092d30a767f.svg?invert_in_darkmode" align=middle width=11.87217899999999pt height=22.465723500000017pt/>.

**Regulation Term**

    1. Heat Equation (HE)

Considering the prior term (or regularization) as the diffusion term in Heat Equation.

<img src="svgs/c5d840bcd826ed7386598ceb615b22b9.svg?invert_in_darkmode" align=middle width=195.41848094999997pt height=26.76175259999998pt/>

Minimizing the total energy E(u,v) by applying the gradient descent algorithm:

<img src="svgs/5f5d5a71b9cfc51ccae3a428a0d02fb4.svg?invert_in_darkmode" align=middle width=276.09008789999996pt height=27.91243950000002pt/>

or <p align="center"><img src="svgs/b0961e021c3aae53bcabdc16e5ebb0ad.svg?invert_in_darkmode" align=middle width=225.3818193pt height=33.81208709999999pt/></p> *Diffusion Equation*

where <img src="svgs/c745b9b57c145ec5577b82542b2df546.svg?invert_in_darkmode" align=middle width=10.57650494999999pt height=14.15524440000002pt/> is the weighting factor, <img src="svgs/fd8be73b54f5436a5cd2e73ba9b6bfa9.svg?invert_in_darkmode" align=middle width=9.58908224999999pt height=22.831056599999986pt/> is the gradient step.

    2. Total Variation (TV)

<img src="svgs/9767362167f47753d06b01fac7903cb1.svg?invert_in_darkmode" align=middle width=203.38664114999997pt height=26.76175259999998pt/>

Recall the <img src="svgs/546dd4be76e9c449f1c24292d8388015.svg?invert_in_darkmode" align=middle width=126.79641974999997pt height=26.76175259999998pt/>, the the diffusion equation will be:

<p align="center"><img src="svgs/8e1c61591bc91255742b6f3255157ce5.svg?invert_in_darkmode" align=middle width=243.70668464999997pt height=39.452455349999994pt/></p>

    3. Perona-Malik Diffusion (PM)

<p align="center"><img src="svgs/b256480742a6d10c9112211bef7db882.svg?invert_in_darkmode" align=middle width=205.91056529999997pt height=33.81208709999999pt/></p>

with different choices for function <img src="svgs/477e79c3356910b8ee9c9018d1997781.svg?invert_in_darkmode" align=middle width=19.89923759999999pt height=24.65753399999998pt/>: <img src="svgs/20d2fef0b644c4bd823daa990b5a2634.svg?invert_in_darkmode" align=middle width=186.13214234999998pt height=26.76175259999998pt/>, <img src="svgs/73ad69e230c2448ab1acecb7f5c5f63a.svg?invert_in_darkmode" align=middle width=179.05452674999998pt height=37.07785289999999pt/>, <img src="svgs/e1dc96fcd0a1c8910ac940a0c31af604.svg?invert_in_darkmode" align=middle width=165.76678634999996pt height=34.64863050000001pt/>.

