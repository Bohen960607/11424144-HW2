#### Step 1: 對微分方程兩邊進行拉普拉斯變換 (Laplace Transform)

設 $\mathcal{L}\{x(t)\}=X(s)$。根據拉普拉斯變換的微分性質：

* $\mathcal{L}\{\frac{dx}{dt}\} = sX(s) - x(0)$
* $\mathcal{L}\{\frac{d^2x}{dt^2}\} = s^2X(s) - sx(0) - x'(0)$

以及單位脈衝函數（狄拉克 $\delta$ 函數）的拉普拉斯變換：

$$\mathcal{L}\{\delta(t)\} = 1$$

將初始條件 $x(0)=0$ 與 $x'(0)=0$ 代入上述公式中，可簡化為：

* $\mathcal{L}\{\frac{dx}{dt}\} = sX(s)$
* $\mathcal{L}\{\frac{d^2x}{dt^2}\} = s^2X(s)$

將上述結果代回原微分方程，可得 $s$ 域的代數方程：

$$s^2X(s) - 3sX(s) + 2X(s) = 1$$

#### Step 2: 求解 $X(s)$ 的代數表達式

提出公因式 $X(s)$：

$$(s^2 - 3s + 2)X(s) = 1$$

將分母的多項式進行因式分解：

$$(s - 1)(s - 2)X(s) = 1$$

移項後得到 $X(s)$ 的標準形式：

$$X(s) = \frac{1}{(s - 1)(s - 2)}$$

#### Step 3: 部分分式拆解 (Partial Fraction Decomposition)

為了方便查表進行反變換，將 $X(s)$ 拆解為兩個部分分式：

$$\frac{1}{(s - 1)(s - 2)} = \frac{A}{s - 1} + \frac{B}{s - 2}$$

這裡利用 **Heaviside 蓋住法 (留數法)** 來快速求解未知係數 $A$ 與 $B$：

* **求 $A$：** 方程兩邊同乘 $(s-1)$ 並令 $s=1$
$$A = \left. \frac{1}{s - 2} \right|_{s=1} = \frac{1}{1 - 2} = -1$$

* **求 $B$：** 方程兩邊同乘 $(s-2)$ 並令 $s=2$

$$B = \left. \frac{1}{s - 1} \right|_{s=2} = \frac{1}{2 - 1} = 1$$

將 $A=-1, B=1$ 代回，得到：

$$X(s) = \frac{1}{s - 2} - \frac{1}{s - 1}$$

#### Step 4: 進行反拉普拉斯變換 (Inverse Laplace Transform)

對 $X(s)$ 取反變換 $\mathcal{L}^{-1}$ 以求得時域原函數 $x(t)$：

$$x(t) = \mathcal{L}^{-1}\{X(s)\} = \mathcal{L}^{-1}\left\{\frac{1}{s - 2}\right\} - \mathcal{L}^{-1}\left\{\frac{1}{s - 1}\right空间}$$

根據常用的基本拉普拉斯變換公式 $\mathcal{L}^{-1}\{\frac{1}{s - a}\} = e^{at}$，可直接查表導出時域解。

---

### Ans:

$$x(t) = e^{2t} - e^t \quad (t \ge 0)$$

