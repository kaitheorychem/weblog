---
layout: post
title: "perturbation-equivarent"
date: 2026-04-08
---
# 時間に依存する摂動と時間に依存しない摂動の等価性

## 初めに
「時間に依存しない摂動だから正確じゃない」、「時間に依存しない摂動だから厳密」みたいな言い方を耳にして気になるのでまとめ。


## 前提
以下、
$$
H=H_0+\epsilon V
$$
を考える。$\epsilon$は摂動の次数を数えるための形式パラメータ（最後に$\epsilon=1$としてよい）。

$H_0$の固有値問題を
$$
H_0\lvert n^{(0)}\rangle=E_n^{(0)}\lvert n^{(0)}\rangle,
\qquad
\langle m^{(0)}\vert n^{(0)}\rangle=\delta_{mn}
$$
とする。以下では縮退なしを仮定する。

## 時間に依存しない摂動論
### 1. 時間に依存しない摂動で $H$ の固有状態を求める

$H$の固有値・固有状態を
$$
H\lvert n\rangle=E_n\lvert n\rangle,
$$
$$
E_n=E_n^{(0)}+\epsilon E_n^{(1)}+\epsilon^2E_n^{(2)}+\cdots,
$$
$$
\lvert n\rangle=\lvert n^{(0)}\rangle+\epsilon\lvert n^{(1)}\rangle+\epsilon^2\lvert n^{(2)}\rangle+\cdots
$$
と展開する。標準規格化条件
$$
\langle n^{(0)}\vert n\rangle=1
$$
を採用すると、

1次補正:
$$
E_n^{(1)}=V_{nn},\qquad V_{mn}:=\langle m^{(0)}\vert V\vert n^{(0)}\rangle,
$$
$$
\lvert n^{(1)}\rangle=\sum_{m\neq n}\frac{V_{mn}}{E_n^{(0)}-E_m^{(0)}}\lvert m^{(0)}\rangle.
$$

2次のエネルギー補正:
$$
E_n^{(2)}=\sum_{m\neq n}\frac{|V_{mn}|^2}{E_n^{(0)}-E_m^{(0)}}.
$$

（必要なら2次の状態補正も同様に導出できる。）

### 2. $H_0$ の固有状態を 1 で求めた固有状態で展開

1で求めた$\lvert n\rangle$は$H$の完全系なので、任意の$H_0$固有状態は
$$
\lvert k^{(0)}\rangle=\sum_n c_n^{(k)}\lvert n\rangle,
\qquad c_n^{(k)}=\langle n\vert k^{(0)}\rangle
$$
と書ける。1次まで使うと係数は
$$
c_k^{(k)}=1+\mathcal{O}(\epsilon^2),
$$
$$
c_n^{(k)}=-\epsilon\frac{V_{nk}}{E_k^{(0)}-E_n^{(0)}}+\mathcal{O}(\epsilon^2)\quad(n\neq k)
$$
なので、
$$
\lvert k^{(0)}\rangle
=\lvert k\rangle
-\epsilon\sum_{n\neq k}\frac{V_{nk}}{E_k^{(0)}-E_n^{(0)}}\lvert n\rangle
+\mathcal{O}(\epsilon^2).
$$

### 3. それぞれの状態の時間発展（時間に依存しない摂動）

$H$固有状態は単純位相で発展する:
$$
\lvert n,t\rangle=e^{-\frac{i}{\hbar}E_nt}\lvert n\rangle.
$$

初期状態を$\lvert\psi(0)\rangle=\lvert k^{(0)}\rangle$とすると、2の展開を使って
$$
\lvert\psi(t)\rangle
=\sum_n c_n^{(k)}e^{-\frac{i}{\hbar}E_nt}\lvert n\rangle.
$$

1次まで書くと
$$
\lvert\psi(t)\rangle
\approx e^{-\frac{i}{\hbar}E_kt}\lvert k\rangle
-\epsilon\sum_{n\neq k}\frac{V_{nk}}{E_k^{(0)}-E_n^{(0)}}e^{-\frac{i}{\hbar}E_nt}\lvert n\rangle.
$$

ここで$E_n$を$E_n^{(0)}+\epsilon E_n^{(1)}+\cdots$に戻せば、位相の中も次数ごとに展開できる。

#### 第一励起状態 $\lvert 1^{(0)}\rangle$ を初期状態にした具体式

$k=1$とすると、1次まで
$$
\lvert 1\rangle
=\lvert 1^{(0)}\rangle
+\epsilon\sum_{m\neq 1}\frac{V_{m1}}{E_1^{(0)}-E_m^{(0)}}\lvert m^{(0)}\rangle,
$$
$$
E_1=E_1^{(0)}+\epsilon V_{11}+\epsilon^2\sum_{m\neq 1}\frac{|V_{m1}|^2}{E_1^{(0)}-E_m^{(0)}}+\cdots.
$$

初期条件$\lvert\psi(0)\rangle=\lvert 1^{(0)}\rangle$を$H$固有状態で書くと
$$
\lvert\psi(0)\rangle
=\lvert 1\rangle
-\epsilon\sum_{n\neq 1}\frac{V_{n1}}{E_1^{(0)}-E_n^{(0)}}\lvert n\rangle+\mathcal{O}(\epsilon^2),
$$
よって時間発展は
$$
\lvert\psi(t)\rangle
\approx e^{-\frac{i}{\hbar}E_1 t}\lvert 1\rangle
-\epsilon\sum_{n\neq 1}\frac{V_{n1}}{E_1^{(0)}-E_n^{(0)}}e^{-\frac{i}{\hbar}E_n t}\lvert n\rangle.
$$

観測基底を$\{\lvert n^{(0)}\rangle\}$に戻したいときは、さらに$\lvert n\rangle=\lvert n^{(0)}\rangle+\mathcal{O}(\epsilon)$を代入して同じ次数で整理すればよい。

### 比較用: $H_0$ 基底での係数と確率 $P_{1\to n}(t)$

比較したい量を
$$
a_n^{\mathrm{(TI)}}(t):=\langle n^{(0)}\vert\psi(t)\rangle,
\qquad
P_{1\to n}^{\mathrm{(TI)}}(t):=\left|a_n^{\mathrm{(TI)}}(t)\right|^2
$$
とおく（TI = time-independent）。初期状態$\lvert\psi(0)\rangle=\lvert1^{(0)}\rangle$で、1次の状態補正まで使うと、$n\neq1$について
$$
a_n^{\mathrm{(TI)}}(t)
=\epsilon\frac{V_{n1}}{E_1^{(0)}-E_n^{(0)}}
\left(e^{-\frac{i}{\hbar}E_1^{(0)}t}-e^{-\frac{i}{\hbar}E_n^{(0)}t}\right)
+\mathcal{O}(\epsilon^2).
$$

したがって遷移確率は
$$
P_{1\to n}^{\mathrm{(TI)}}(t)
=4\epsilon^2\frac{|V_{n1}|^2}{\left(E_n^{(0)}-E_1^{(0)}\right)^2}
\sin^2\!\left(\frac{(E_n^{(0)}-E_1^{(0)})t}{2\hbar}\right)
+\mathcal{O}(\epsilon^3),\quad(n\neq1).
$$

$n=1$は規格化から
$$
P_{1\to1}^{\mathrm{(TI)}}(t)=1-\sum_{n\neq1}P_{1\to n}^{\mathrm{(TI)}}(t)+\mathcal{O}(\epsilon^3).
$$

## 時間に依存する摂動（標準的なやり方）

次は
$$
H(t)=H_0+\epsilon V(t)
$$
を相互作用表示で扱う。相互作用表示状態を
$$
\lvert\psi_I(t)\rangle=e^{\frac{i}{\hbar}H_0t}\lvert\psi_S(t)\rangle
$$
とすると
$$
i\hbar\frac{d}{dt}\lvert\psi_I(t)\rangle=\epsilon V_I(t)\lvert\psi_I(t)\rangle,
\qquad
V_I(t)=e^{\frac{i}{\hbar}H_0t}V(t)e^{-\frac{i}{\hbar}H_0t}.
$$

### 第1章: 1次摂動

時間発展演算子を$U_I(t,0)$とすると
$$
U_I(t,0)=1-\frac{i\epsilon}{\hbar}\int_0^t dt_1\,V_I(t_1)+\mathcal{O}(\epsilon^2).
$$

初期状態$\lvert i\rangle=\lvert i^{(0)}\rangle$から$\lvert f\rangle=\lvert f^{(0)}\rangle$への遷移振幅は
$$
A_{fi}^{(1)}(t)
=-\frac{i\epsilon}{\hbar}\int_0^t dt_1\,\langle f\vert V_I(t_1)\vert i\rangle.
$$

$\langle f\vert V_I(t)\vert i\rangle=e^{i\omega_{fi}t}V_{fi}(t)$（$\omega_{fi}=(E_f^{(0)}-E_i^{(0)})/\hbar$）より
$$
A_{fi}^{(1)}(t)
=-\frac{i\epsilon}{\hbar}\int_0^t dt_1\,e^{i\omega_{fi}t_1}V_{fi}(t_1).
$$

初期状態を$\lvert i\rangle=\lvert1^{(0)}\rangle$に固定すると、比較したい係数は
$$
a_n^{\mathrm{(TD)}}(t):=\langle n^{(0)}\vert\psi_S(t)\rangle
$$
（TD = time-dependent）で、$n\neq1$の1次振幅は
$$
a_n^{\mathrm{(TD)},(1)}(t)
=-\frac{i\epsilon}{\hbar}\int_0^t dt'\,e^{i\omega_{n1}t'}V_{n1}(t').
$$
ゆえに1次摂動での遷移確率は
$$
P_{1\to n}^{\mathrm{(TD)}}(t)
=\left|a_n^{\mathrm{(TD)},(1)}(t)\right|^2
=\frac{\epsilon^2}{\hbar^2}
\left|\int_0^t dt'\,e^{i\omega_{n1}t'}V_{n1}(t')\right|^2,
\quad(n\neq1).
$$

### 直接比較（静的摂動 $V(t)=V$）

時間依存計算の式に$V_{n1}(t')=V_{n1}$を入れると
$$
a_n^{\mathrm{(TD)},(1)}(t)
=\epsilon\frac{V_{n1}}{E_1^{(0)}-E_n^{(0)}}
\left(e^{-\frac{i}{\hbar}E_1^{(0)}t}-e^{-\frac{i}{\hbar}E_n^{(0)}t}\right),
$$
となり、上の$ a_n^{\mathrm{(TI)}}(t)$と一致する。したがって
$$
P_{1\to n}^{\mathrm{(TD)}}(t)=P_{1\to n}^{\mathrm{(TI)}}(t)
$$
が1次の遷移確率のレベルで同じ形で比較できる。

### 第2章: 2次摂動

Dyson展開の2次項:
$$
U_I^{(2)}(t,0)=\left(-\frac{i\epsilon}{\hbar}\right)^2\int_0^t dt_1\int_0^{t_1}dt_2\,V_I(t_1)V_I(t_2).
$$

したがって
$$
A_{fi}^{(2)}(t)
=\left(-\frac{i\epsilon}{\hbar}\right)^2
\sum_m\int_0^t dt_1\int_0^{t_1}dt_2\,
\langle f\vert V_I(t_1)\vert m\rangle
\langle m\vert V_I(t_2)\vert i\rangle.
$$

具体的には
$$
A_{fi}^{(2)}(t)
=\left(-\frac{i\epsilon}{\hbar}\right)^2
\sum_m\int_0^t dt_1\int_0^{t_1}dt_2\,
e^{i\omega_{fm}t_1}V_{fm}(t_1)
e^{i\omega_{mi}t_2}V_{mi}(t_2).
$$

### 第3章: 一般の $n$ 次摂動

一般$n$次のDyson項は
$$
U_I^{(n)}(t,0)=\left(-\frac{i\epsilon}{\hbar}\right)^n
\int_0^t dt_1\int_0^{t_1}dt_2\cdots\int_0^{t_{n-1}}dt_n
\,V_I(t_1)V_I(t_2)\cdots V_I(t_n).
$$

遷移振幅は中間状態を挿入して
$$
A_{fi}^{(n)}(t)
=\left(-\frac{i\epsilon}{\hbar}\right)^n
\sum_{m_1,\dots,m_{n-1}}
\int_0^t dt_1\int_0^{t_1}dt_2\cdots\int_0^{t_{n-1}}dt_n
\prod_{j=1}^{n}
\langle \alpha_j\vert V_I(t_j)\vert \alpha_{j-1}\rangle
$$
（$\alpha_0=i,\alpha_n=f,\alpha_j=m_j$）となる。

## まとめ

比較の観点を「初期状態$\lvert 1^{(0)}\rangle$から、時刻$t$で$\lvert n^{(0)}\rangle$にいる確率
$P_{1\to n}(t)$」にそろえると、時間非依存摂動と時間依存摂動は直接比較できる。

特に静的摂動$V(t)=V$では、1次振幅の式が一致し、
$$
P_{1\to n}^{\mathrm{(TI)}}(t)=P_{1\to n}^{\mathrm{(TD)}}(t)
$$
となる。つまり両者の違いは「何を展開するか」（固有値問題か、時間発展演算子か）であって、
同じ次数まで展開したときに得られる物理量（遷移確率）は整合する。

書いてて思ったが、序章で述べたような「時間に依存しない摂動は不正確〜」みたいな主張は、励起状態の時間発展を$\exp\left(-i(E-\frac i\tau)t\right)$みたいに書く部分の不正確さの話をしてる気がしてきた。(でもやっぱり摂動論に由来する不正確さじゃないよね)


### 
H0とVが交換する時Vによる摂動では遷移が起きえない。
そのはずなのに、なぜか遷移が起きるのは他にWという相互作用があって、H=H0+W+V


H=H0+V1+V2と書かれてる