# [[2^j ,2^j - j - 2, 3]] Gottesman's Code

This is a homegrown implementation of the family of **[[2^j, 2^j - j - 2, 3]] Gottesman codes**, also known as **[[2^j, 2^j - j - 2, 3]]** **quantum Hamming codes**, as described in Gottesman's 1997 PhD thesis on '_Stabilizer Codes and Quantum Error Correction_' [1].

Key details for the [[8, 3, 3]] code when j = 3 using Stabilizer Formalism:
- [2] utilizes an explicit construction method for the stabilizer generators. The remaining m generators, apart from Mx and Mz, are constructed using the check matrix [Hm|AmHm], where Hm = [c0, c1, ..., c^2m − 1]. Each column ck (for k = 0, 1, ..., 2^m − 1) represents a binary vector corresponding to the integer k. Also, Am refers to any invertible m × m matrix devoid of fixed points such that Am​.s ≠ 0 and Am.s ≠ s for all s ∈ F₂ᵐ.
- [3] introduces alternative stabilizer generators for the [[8, 3, 3]] code. It identifies permutations effective for all stabilizer generators except for X^⊗8 and Z^⊗8. However, these can be replaced with XXYZIYZI and ZZIXYIXY, respectively. The stabilizer generators are permuted to achieve desired properties, reflecting an alternative approach to constructing the stabilizer code.

# Notes:
- This implementation adopts the Gottesman Notation for the [[8, 3, 3]] stabilizer code as depicted in Table 3.3 on Page 22 on the Gottesman's PhD thesis. Additionally, for j = 4, our [[16, 10, 3]] stabilizer code stemming from Gottesman(4) can be cross-verified from **Table 8.1 on Page 91 **as well [1]
- The differences between [1], [2], and [3] primarily lie in the choice of stabilizer generators and their permutations for the [[8, 3, 3]] stabilizer code.
"""

# Requirements

- QuantumClifford.ECC: AbstractECC parity_checks

# How to Install?
To successfull run Gottesman.jl, follow these steps:
- **Download:** Download the QuantumClifford.jl source file.
- **Place in src folder:** Move the downloaded source file into the src folder of your Julia environment.
- **Include:** Include the file in your Julia code. For example, if you want to include it in a file named ECC.jl, add the following line at the end of ECC.jl:
```
 include("codes/gottesmencode.jl")
```
- **Package Development:** Develop the package using Pkg.develop(). Navigate to the root directory of your Julia environment and run:
```
using Pkg
Pkg.develop(path="path_to_QuantumClifford.jl")
```
- **Usage:** Once the package is successfully installed, you can use it in your Julia code. Import the necessary functions or modules from QuantumClifford.jl using:
```
using QuantumClifford.ECC: Gottesman, Parity_checks
parity_checks(Gottesman(4))
```
**Exploration**:  Play around with the code. Experiment with different values of js and see the symmetries in the Stabilizer Code


# Results 

**Stabilizer of [[8,3,3]] Code when j==3**
```
julia> parity_checks(Gottesman(4))
+ XXXXXXXXXXXXXXXX
+ ZZZZZZZZZZZZZZZZ
+ _X_X_X_XZYZYZYZY
+ _X_XZYZYX_X_YZYZ
+ _XZYX_YZ_XZYX_YZ
+ _YXZ_YXZ_YXZ_YXZ
```
**Stabilizer of [[16, 10, 3]] when j==4 Code**
```
parity_checks(Gottesman(4))
+ XXXXXXXXXXXXXXXX
+ ZZZZZZZZZZZZZZZZ
+ _X_X_X_XZYZYZYZY
+ _X_XZYZYX_X_YZYZ
+ _XZYX_YZ_XZYX_YZ
+ _YXZ_YXZ_YXZ_YXZ
```

**Stabilizer of [[32, 27, 3]] when j==5 Code**

```
parity_checks(Gottesman(5))
+ XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
+ ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
+ _X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZY
+ _X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ
+ _X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ
+ _XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ
+ _YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y

```

**Stabilizer of [[1032, 1012, 3]] when j==10 Code**


```
julia> parity_checks(Gottesman(10))
+ XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX⋯XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
+ ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ⋯ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯ZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZY
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZ⋯X_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X⋯ZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZ_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZ_X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZ
+ _X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZ⋯X_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ
+ _X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZY⋯_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ
+ _XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_Y⋯_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ
+ _YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YX⋯_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ_YXZ
```

 **Stabilizer of [[32768, 32751, 3]] when j==15 Code**

```
julia> parity_checks(Gottesman(15))
+ XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX⋯XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
+ ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ⋯ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯ZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZY
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZ⋯X_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X⋯ZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZYZYZYZYZYZYZYZYZ
+ _X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZ_X_X_X_X_X_X_X_⋯YZYZYZYZYZYZYZYZ_X_X_X_X_X_X_X_XZYZYZYZYZYZYZYZYX_X_X_X_X_X_X_X_YZYZYZYZYZYZYZYZ
+ _X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZ⋯X_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ_X_X_X_XZYZYZYZYX_X_X_X_YZYZYZYZ
+ _X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZY⋯_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ_X_XZYZYX_X_YZYZ
+ _XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_Y⋯_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ_XZYX_YZ
+ _YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_⋯_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y_YXZXZ_Y
```

# Physical Qubits vs Logical Qubit Graphs
Gottesman(3), Gottesman(4), Gottesman(5) 
![image](https://github.com/Fe-r-oz/GottesmanCode/assets/93876775/2eef72b7-2f00-4b83-bbce-d787bd14b627)


# References
- Gottesman, D. (1997). Stabilizer Codes and Quantum Error Correction [quant-ph/9705052]. arXiv:quant-ph/9705052 [arxiv](https://arxiv.org/abs/quant-ph/9705052)
- Yu, S., Bierbrauer, J., Dong, Y., Chen, Q., & Oh, C.H. (2009). All the stabilizer codes of distance 3. [arxiv](https://arxiv.org/abs/0901.1968v3)
- Chao, R., & Reichardt, B. W. (2018). Quantum error correction with only two extra qubits. Physical Review Letters, 121(5), 050502. [doi](https://doi.org/10.1103/PhysRevLett.121.050502)
