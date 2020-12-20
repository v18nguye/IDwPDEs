[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#theoretical-background">Theoretical Background</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

The project aims to exploit Partial Differential Equations (PDEs) to solve Inverse Problem in Image Denoising. There are other
approaches dealing with Inverse Problem, resumed in Figure below.

![Alt](images/ci.png)

### Theoretical Background
In theory, we are looking for a solution <img src="svgs/9a816d3409cff0a970fc73cfd9ea3e75.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=22.831056599999986pt/> by minimizing the following cost:

<img src="svgs/2101f41ba7f16ddcc28beb79496af43b.svg?invert_in_darkmode" align=middle width=165.32312444999997pt height=24.65753399999998pt/>

with <img src="svgs/0ba7c2f345c9d47ed4fce8b4b568f1e4.svg?invert_in_darkmode" align=middle width=224.90869169999996pt height=24.65753399999998pt/>

where <img src="svgs/e06ba62f2bfed5cf8a0fae61c45d4ac8.svg?invert_in_darkmode" align=middle width=11.92007189999999pt height=22.465723500000017pt/> is a set of possible solutions whose element values corresponding {0,...,255} for RGB images.

The <img src="svgs/a073111060fab93e704125a7248622dc.svg?invert_in_darkmode" align=middle width=77.08567184999998pt height=24.65753399999998pt/> term represents the consistency between the observation <img src="svgs/6c4adbc36120d62b98deef2a20d5d303.svg?invert_in_darkmode" align=middle width=8.55786029999999pt height=14.15524440000002pt/> and and the solution <img src="svgs/6dbb78540bd76da3f1625782d42d6d16.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=14.15524440000002pt/>, while the <img src="svgs/e301f098c314cbae7c79e4621a1d8732.svg?invert_in_darkmode" align=middle width=54.67258994999999pt height=24.65753399999998pt/>
term is the regulator which depicts an expected property for the solution. In the project, we will expect to study the impact of different
regularization terms.

**Data Term**

<img src="svgs/3006af981807a1b114110bc539ed06d2.svg?invert_in_darkmode" align=middle width=214.04469075000003pt height=26.76175259999998pt/>

The data term considered here is the norm 2 of difference between the solution <img src="svgs/6dbb78540bd76da3f1625782d42d6d16.svg?invert_in_darkmode" align=middle width=9.41027339999999pt height=14.15524440000002pt/> and the observation <img src="svgs/6c4adbc36120d62b98deef2a20d5d303.svg?invert_in_darkmode" align=middle width=8.55786029999999pt height=14.15524440000002pt/>,
which is integrated through the image's spatial information <img src="svgs/9432d83304c1eb0dcb05f092d30a767f.svg?invert_in_darkmode" align=middle width=11.87217899999999pt height=22.465723500000017pt/>.

**Regulation Term**

    1. Heat Equation (HE)

Considering the prior term (or regularization) as the diffusion term in Heat Equation.

<img src="svgs/c5d840bcd826ed7386598ceb615b22b9.svg?invert_in_darkmode" align=middle width=195.41848094999997pt height=26.76175259999998pt/>

Minimizing the total energy E(u,v) by applying the gradient descent algorithm:

<img src="svgs/5f5d5a71b9cfc51ccae3a428a0d02fb4.svg?invert_in_darkmode" align=middle width=276.09008789999996pt height=27.91243950000002pt/>

*Diffusion Equation* <p align="center"><img src="svgs/b0961e021c3aae53bcabdc16e5ebb0ad.svg?invert_in_darkmode" align=middle width=225.3818193pt height=33.81208709999999pt/></p>

where <img src="svgs/c745b9b57c145ec5577b82542b2df546.svg?invert_in_darkmode" align=middle width=10.57650494999999pt height=14.15524440000002pt/> is the weighting factor, <img src="svgs/fd8be73b54f5436a5cd2e73ba9b6bfa9.svg?invert_in_darkmode" align=middle width=9.58908224999999pt height=22.831056599999986pt/> is the gradient step.

    2. Total Variation (TV)

<img src="svgs/dac99e99e78beb5f0231d3dc11827977.svg?invert_in_darkmode" align=middle width=225.30423464999998pt height=29.424786600000015pt/>

Recall the <img src="svgs/546dd4be76e9c449f1c24292d8388015.svg?invert_in_darkmode" align=middle width=126.79641974999997pt height=26.76175259999998pt/>, the the diffusion equation will be:

<p align="center"><img src="svgs/8e1c61591bc91255742b6f3255157ce5.svg?invert_in_darkmode" align=middle width=243.70668464999997pt height=39.452455349999994pt/></p>

    3. Perona-Malik Diffusion (PM)

<p align="center"><img src="svgs/b256480742a6d10c9112211bef7db882.svg?invert_in_darkmode" align=middle width=205.91056529999997pt height=33.81208709999999pt/></p>

with different choices for function <img src="svgs/477e79c3356910b8ee9c9018d1997781.svg?invert_in_darkmode" align=middle width=19.89923759999999pt height=24.65753399999998pt/>: <img src="svgs/33b73b6041552a7e586557a60994802c.svg?invert_in_darkmode" align=middle width=185.28739349999998pt height=26.76175259999998pt/>, <img src="svgs/6461a38730e2d704ff15d39e298d4f90.svg?invert_in_darkmode" align=middle width=178.20977789999998pt height=37.07785289999999pt/>, <img src="svgs/d858960f01b8c92886cb25f5eb2e7b92.svg?invert_in_darkmode" align=middle width=164.92203585pt height=34.64863050000001pt/>.

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

### Installation

<!-- USAGE EXAMPLES -->
## Usage

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<!-- CONTACT -->
## Contact

Khoa NGUYEN - [@v18nguyen](https://twitter.com/v18nguyen) - khoa.v18nguyen@gmail.com

Project Link: [https://github.com/v18nguye/IDwPDEs](https://github.com/v18nguye/IDwPDEs)

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [Cool README Template](https://github.com/othneildrew/Best-README-Template#built-with)

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/v18nguye/IDwPDEs.svg?style=for-the-badge
[contributors-url]: https://github.com/v18nguye/IDwPDEs/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/v18nguye/IDwPDEs.svg?style=for-the-badge
[forks-url]: https://github.com/v18nguye/IDwPDEs/network/members
[stars-shield]: https://img.shields.io/github/stars/v18nguye/IDwPDEs.svg?style=for-the-badge
[stars-url]: https://github.com/v18nguye/IDwPDEs/stargazers
[issues-shield]: https://img.shields.io/github/issues/v18nguye/IDwPDEs.svg?style=for-the-badge
[issues-url]: https://github.com/v18nguye/IDwPDEs/issues
[license-shield]: https://img.shields.io/github/license/v18nguye/IDwPDEs.svg?style=for-the-badge
[license-url]: https://github.com/v18nguye/IDwPDEs/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/khoa-nguyen-139b9b15b/