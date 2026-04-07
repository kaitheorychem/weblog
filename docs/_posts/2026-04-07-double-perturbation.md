---
layout: post
title: "perturbation-equivarent"
date: 2026-04-08
---
## 初めに
「時間に依存しない摂動だから正確じゃない」、「時間に依存しない摂動だから厳密」みたいな言い方を耳にして気になるのでまとめ。

問題になるのは次のような文脈である。
H0とVが交換する時、Vによる摂動ではH0の固有状態間では本来遷移が起きえない。そのはずなのに、なぜか遷移が起きるのは他にWという相互作用があって、H=H0+W+Vという形になっており、より正確な固有状態H'=H_0+Wでは元の固有状態が混合しているからだ、というロジックである。

これに関して、別の捉え方もある。初めからW＋Vが摂動であると捉え、H0の固有状態の時間変化を時間に依存する摂動により追おうという立場である。

この二つの見方は摂動の次数を揃える限りは基本的に等価であり、どちらかを採用することで特定の項が落ちたり厳密性が損なわれるというわけではないが、数式や取り扱いの見掛け上の違い(Wについての摂動の後でVについての摂動取ってと二段階にすることで精度悪くならないか等)が気になることもあるのでここにまとめる。

## 前提 

$$
  H  =  H_0 + V + W
$$

であり、H_0はV,Wと可換、VとWの間で非可換.
$$
  [H_0,V]=0,[H_0,V]=0,[V,W]\neq0
$$

H0の固有状態を始状態として別の固有状態に遷移する過程を調べる。


## 時間に依存しない摂動(Wによる混合の後Vによる遷移)

Wによる摂動により定めた摂動固有状態から、Vによる時間に依存した摂動で時間発展させる。

### ステップ1: Wによる時間に依存しない摂動

まずH'=H_0+Wに対して摂動展開を行う。H_0の固有状態を$|n\rangle$とすると($H_0|n\rangle=E_n|n\rangle$)、H'の固有状態$|n'\rangle$は:

$$|n'\rangle = |n\rangle + \sum_{m\neq n}\frac{\langle m|W|n\rangle}{E_n-E_m}|m\rangle + \sum_{m\neq n}\sum_{k\neq n}\frac{\langle m|W|k\rangle\langle k|W|n\rangle}{(E_n-E_m)(E_n-E_k)} |m\rangle + \cdots$$

対応するエネルギーは:

$$E_n' = E_n + \langle n|W|n\rangle + \sum_{m\neq n}\frac{|\langle m|W|n\rangle|^2}{E_n-E_m} + \cdots$$

### ステップ2: Vによる時間に依存する摂動

次に、このH'の固有状態$|n'\rangle$からの初期状態に対して、時間に依存する摂動でVの効果を取り入れる。相互作用表現で、時間発展の振幅は:

$$c_m^{(1)}(t) = -\frac{i}{\hbar}\int_0^t dt' e^{i(E_m'-E_n')t'/\hbar}\langle m'|V|n'\rangle$$

$$c_m^{(2)}(t) = -\frac{i}{\hbar}\int_0^t dt' e^{i(E_m'-E_n')t'/\hbar}\langle m'|V|n'\rangle + \left(-\frac{i}{\hbar}\right)^2\sum_{k\neq m,n}\int_0^t dt'\int_0^{t'} dt'' e^{i(E_m'-E_k')t'/\hbar}e^{i(E_k'-E_n')t''/\hbar}\langle m'|V|k'\rangle\langle k'|V|n'\rangle$$

ここで$|m'\rangle, |n'\rangle$はH'=H_0+Wの固有状態である。



## 時間に依存する摂動

V+Wを摂動項として初めから全て時間による摂動によりH_0の固有状態の時間発展を記述する。

### 時間に依存する摂動でV+Wを扱う

相互作用表現で、ハミルトニアンH=H_0+V+Wの下では、H_0の固有状態$|n\rangle$から始まる時間発展について、状態$|\psi(t)\rangle$は以下のように展開される:

1次の摂動:
$$c_m^{(1)}(t) = -\frac{i}{\hbar}\int_0^t dt' e^{i(E_m-E_n)t'/\hbar}\langle m|V+W|n\rangle$$

2次の摂動:
$$c_m^{(2)}(t) = c_m^{(1)}(t) + \left(-\frac{i}{\hbar}\right)^2\sum_{k\neq m,n}\int_0^t dt'\int_0^{t'} dt'' e^{i(E_m-E_k)t'/\hbar}e^{i(E_k-E_n)t''/\hbar}\langle m|(V+W)|k\rangle\langle k|(V+W)|n\rangle$$

全体としての遷移確率は:
$$P_{n\to m}(t) = |c_m^{(2)}(t)|^2$$

ここで1次の項は$\langle m|V+W|n\rangle$の全体の寄与を含み、2次の項は中間状態$|k\rangle$を経由する経路を含む。

