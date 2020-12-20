# Partial Differential Equations (PDEs) for Image Denoising

Image Denoising can be cast as an inverse problem to which we exploit PDEs to solve. There are several
approaches dealing with Inverse Problem, resumed in the figure below.

![Alt](images/ci.png)

__Author: Khoa NGUYEN__

## Background
In theory, we are looking for a solution <img src="svgs/9a816d3409cff0a970fc73cfd9ea3e75.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=22.831056599999986pt/> by minimizing the following cost:

<img src="svgs/2101f41ba7f16ddcc28beb79496af43b.svg?invert_in_darkmode" align=middle width=165.32312444999997pt height=24.65753399999998pt/>

with <img src="svgs/86f67b02b0fa6adbc14c3ec7e5a136b5.svg?invert_in_darkmode" align=middle width=215.14490909999998pt height=24.65753399999998pt/>

where <img src="svgs/e06ba62f2bfed5cf8a0fae61c45d4ac8.svg?invert_in_darkmode" align=middle width=11.92007189999999pt height=22.465723500000017pt/> is a pixel-value range, corresponding {0,...,255} for RGB images.

The first term represents consistency between the observation <img src="svgs/6c4adbc36120d62b98deef2a20d5d303.svg?invert_in_darkmode" align=middle width=8.55786029999999pt height=14.15524440000002pt/> and and the solution <img src="svgs/6dbb78540bd76da3f1625782d42d6d16.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=14.15524440000002pt/>, while the second
term is the regulator which depicts an expected property for the solution. In the project, we will expect to study the impact different
regulation terms.

The variational cost over an image by integrating through its spatial information <img src="svgs/9432d83304c1eb0dcb05f092d30a767f.svg?invert_in_darkmode" align=middle width=11.87217899999999pt height=22.465723500000017pt/>:

<img src="svgs/aa24f20cae0b4a011f08286e9cb0c719.svg?invert_in_darkmode" align=middle width=297.64800284999995pt height=26.76175259999998pt/>

**Data Term**

<img src="svgs/0a990797d46f540e7d0ecd54ee24c64c.svg?invert_in_darkmode" align=middle width=208.31631314999998pt height=26.76175259999998pt/>

The data term considered here is the norm of difference between the solution <img src="svgs/6dbb78540bd76da3f1625782d42d6d16.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=14.15524440000002pt/> and the observation <img src="svgs/6c4adbc36120d62b98deef2a20d5d303.svg?invert_in_darkmode" align=middle width=8.55786029999999pt height=14.15524440000002pt/>,
which is integrated through the image's spatial information <img src="svgs/9432d83304c1eb0dcb05f092d30a767f.svg?invert_in_darkmode" align=middle width=11.87217899999999pt height=22.465723500000017pt/>.

**Regulation Term**

    1. Heat Equation (HE)

Considering the prior term (or regularization) as the diffusion term in Heat Equation.

<img src="svgs/c5d840bcd826ed7386598ceb615b22b9.svg?invert_in_darkmode" align=middle width=195.41848094999997pt height=26.76175259999998pt/>

Minimizing the total energy E(u,v) by applying the gradient descent algorithm:

<img src="svgs/719da8e883ea00219c8d8a993d846329.svg?invert_in_darkmode" align=middle width=322.0031694pt height=29.190975000000005pt/>

where <img src="svgs/c745b9b57c145ec5577b82542b2df546.svg?invert_in_darkmode" align=middle width=10.57650494999999pt height=14.15524440000002pt/> is the weighting factor, <img src="svgs/fd8be73b54f5436a5cd2e73ba9b6bfa9.svg?invert_in_darkmode" align=middle width=9.58908224999999pt height=22.831056599999986pt/> is the gradient step.

    2. Total Variation (TV)

<img src="svgs/9767362167f47753d06b01fac7903cb1.svg?invert_in_darkmode" align=middle width=203.38664114999997pt height=26.76175259999998pt/>

Recall the <img src="svgs/546dd4be76e9c449f1c24292d8388015.svg?invert_in_darkmode" align=middle width=126.79641974999997pt height=26.76175259999998pt/>, the the diffusion equation will be:

<p align="center"><img src="svgs/8e1c61591bc91255742b6f3255157ce5.svg?invert_in_darkmode" align=middle width=243.70668464999997pt height=39.452455349999994pt/></p>

    3. Perona-Malik Diffusion (PM)

<p align="center"><img src="svgs/b256480742a6d10c9112211bef7db882.svg?invert_in_darkmode" align=middle width=205.91056529999997pt height=33.81208709999999pt/></p>
with different choices for function <img src="svgs/477e79c3356910b8ee9c9018d1997781.svg?invert_in_darkmode" align=middle width=19.89923759999999pt height=24.65753399999998pt/>: <img src="svgs/20d2fef0b644c4bd823daa990b5a2634.svg?invert_in_darkmode" align=middle width=186.13214234999998pt height=26.76175259999998pt/>, <img src="svgs/73ad69e230c2448ab1acecb7f5c5f63a.svg?invert_in_darkmode" align=middle width=179.05452674999998pt height=37.07785289999999pt/>, <img src="svgs/e1dc96fcd0a1c8910ac940a0c31af604.svg?invert_in_darkmode" align=middle width=165.76678634999996pt height=34.64863050000001pt/>.



