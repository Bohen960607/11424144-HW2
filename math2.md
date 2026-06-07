#### Step 1: 分析函數對稱性 (Symmetry Analysis)

傅立葉級數的通用展開式為：

$$f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} [a_n \cos(nx) + b_n \sin(nx)]$$

首先觀察給定函數 $f(x) = x^2$。因為 $f(-x) = (-x)^2 = x^2 = f(x)$，所以 $f(x)$ 為**偶函數 (Even function)**。
根據正交性質，偶函數在對稱區間 $[-\pi, \pi]$ 內的特性如下：
* 正弦項係數直接為零：$b_n = 0$
* 餘弦項與常數項係數可簡化為正半區間積分的兩倍。

因此，我們只需要計算 $a_0$ 與 $a_n$ 即可。

#### Step 2: 計算常數項（直流分量）$a_0$

根據公式，利用偶函數性質將積分區間從 $[-\pi, \pi]$ 縮小至 $[0, \pi]$ 並乘以 2：

$$a_0 = \frac{1}{\pi} \int_{-\pi}^{\pi} x^2 dx = \frac{2}{\pi} \int_{0}^{\pi} x^2 dx$$

進行積分計算：

$$a_0 = \frac{2}{\pi} \left[ \frac{x^3}{3} \right]_{0}^{\pi} = \frac{2}{\pi} \left( \frac{\pi^3}{3} - 0 \right) = \frac{2}{3}\pi^2$$

#### Step 3: 計算餘弦項係數 $a_n$

根據公式，同理利用偶函數性質簡化積分：

$$a_n = \frac{1}{\pi} \int_{-\pi}^{\pi} x^2 \cos(nx) dx = \frac{2}{\pi} \int_{0}^{\pi} x^2 \cos(nx) dx$$

此處必須使用**分部積分法 (Integration by parts)** 兩次。我們採用工程數學常用的**連鎖積分法（表格法）**來快速推導：

* **微分項 $u(x)$ 連續微分：** $x^2 \rightarrow 2x \rightarrow 2 \rightarrow 0$
* **積分項 $v(x)$ 連續積分：** $\cos(nx) \rightarrow \frac{\sin(nx)}{n} \rightarrow -\frac{\cos(nx)}{n^2} \rightarrow -\frac{\sin(nx)}{n^3}$

將對應項正負相乘（$+ - +$）交叉相加後，可得：

$$\int x^2 \cos(nx) dx = x^2 \left( \frac{\sin(nx)}{n} \right) - 2x \left( -\frac{\cos(nx)}{n^2} \right) + 2 \left( -\frac{\sin(nx)}{n^3} \right)$$

將上式代回定積分，並填入上下限 $[0, \pi]$：

$$a_n = \frac{2}{\pi} \left[ \frac{x^2 \sin(nx)}{n} + \frac{2x \cos(nx)}{n^2} - \frac{2 \sin(nx)}{n^3} \right]_{0}^{\pi}$$

由於 $n$ 為正整數，我們已知 $\sin(n\pi) = 0$ 且 $\sin(0) = 0$，因此所有包含 $\sin$ 的項在代入上下限後全部變為 0。上式可大幅簡化為：

$$a_n = \frac{2}{\pi} \left[ \frac{2\pi \cos(n\pi)}{n^2} - 0 \right]$$

再將 $\cos(n\pi) = (-1)^n$ 代入，約掉分子分母的 $\pi$：

$$a_n = \frac{2}{\pi} \cdot \frac{2\pi (-1)^n}{n^2} = \frac{4(-1)^n}{n^2}$$

#### Step 4: 組合寫出最終傅立葉級數

將求得的係數 $a_0 = \frac{2}{3}\pi^2$ 與 $a_n = \frac{4(-1)^n}{n^2}$ 代回原展開式（注意第一項是 $a_0 / 2$）：

$$\frac{a_0}{2} = \frac{\frac{2}{3}\pi^2}{2} = \frac{\pi^2}{3}$$

---

### Ans:

$$x^2 = \frac{\pi^2}{3} + \sum_{n=1}^{\infty} \frac{4(-1)^n}{n^2} \cos(nx)$$
