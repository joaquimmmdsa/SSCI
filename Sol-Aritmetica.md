# Solutions — Modular Arithmetic Tools

**Course:** *Seguretat i Secret en la Codificació de la Informació* (EPSEM), curs 26–27–Q1
**Problem sheet:** `Prob-Aritmetica` (Tema 1)

---

## Notes on this document

- **Restored statements.** The markdown file `Prob-Aritmetica.md` lost the formulas of exercises
  **1.22, 1.23, 1.25** and **1.27**. They have been recovered from the original
  `Prob-Aritmetica.pdf` and are restated below.
- **Notation.** $\gcd$ = greatest common divisor (mcd), $\operatorname{lcm}$ = least common
  multiple (mcm); $[a]_m$ is the class of $a$ modulo $m$. Ring units are listed as residue classes.
- **Typo in 1.11.** The statement says $\gcd(m,n)=1$; the hypothesis that makes sense (and the
  one solved here) is $\gcd(a,b)=1$.
- **Typo in 1.18.** Read literally the statement is false for the even prime $p=2$ (indeed
  $2=1^2+1^2$ but $2\equiv 2 \pmod 4$). What is true — and is proved below — is the intended
  statement: **every odd prime** that is a sum of two squares satisfies $p\equiv 1\pmod 4$.
- **Items 1.38 (u) and (v).** As written they are false (counterexamples below); the standard
  true statements obtained by swapping the roles of $\gcd$ and $\operatorname{lcm}$ are recorded
  next to each answer.
- Every numerical result in this document was independently checked by computer.

---

## 1.1 Divisibility in $\mathbb{Z}$

### 1.1
*Let $a,b\in\mathbb Z$ with $\gcd(a,b)=1$. Show that $\gcd(a+b,\,a-b)\in\{1,2\}$.*

**Solution.** Let $d=\gcd(a+b,\,a-b)$. Then $d\mid a+b$ and $d\mid a-b$, hence
$$d\mid (a+b)+(a-b)=2a \qquad\text{and}\qquad d\mid (a+b)-(a-b)=2b.$$
So $d$ is a common divisor of $2a$ and $2b$:
$$d\mid \gcd(2a,2b)=2\gcd(a,b)=2.$$
As $d>0$, we get $d\in\{1,2\}$. Both cases really occur:
$a=2,\,b=1$ gives $\gcd(3,1)=1$, while $a=3,\,b=1$ gives $\gcd(4,2)=2$. $\blacksquare$

### 1.2
*Show that $\gcd(ma,mb)=m\cdot\gcd(a,b)$ for all $a,b,m\in\mathbb Z$.*

**Solution.** If $m=0$ both sides are $0$. Assume first $m>0$. For every prime $p$, let $v_p(x)$
be the exponent of $p$ in $x$ (with $v_p(0)=+\infty$, which also covers $a=0$ or $b=0$). Using
$\min(\alpha+t,\beta+t)=t+\min(\alpha,\beta)$:
$$v_p\bigl(\gcd(ma,mb)\bigr)=\min\bigl(v_p(m)+v_p(a),\,v_p(m)+v_p(b)\bigr)
=v_p(m)+\min\bigl(v_p(a),v_p(b)\bigr)=v_p\bigl(m\gcd(a,b)\bigr).$$
Two nonnegative integers with the same valuation at every prime are equal, so
$\gcd(ma,mb)=m\gcd(a,b)$ for $m>0$.

*Sign convention (small remark).* With the standard convention that gcds are nonnegative, for
$m<0$ the general identity reads $\gcd(ma,mb)=|m|\cdot\gcd(a,b)$ (gcds only see $|ma|,|mb|$);
the formula $m\,\gcd(a,b)$ is then correct as an identity "up to sign", and is literally true
whenever $m\ge 0$ or when one declares gcds up to sign. $\blacksquare$

*Bézout alternative.* Write $\gcd(a,b)=ax+by$. Then $m\gcd(a,b)=(ma)x+(mb)y$, which shows
$m\gcd(a,b)$ is a common divisor of $ma,mb$ (both positive multiples), and the converse
divisibility follows by the same computation with the roles of $(a,b)$ and $(ma,mb)$ swapped;
the valuation proof avoids all case distinctions.

### 1.3
*Is $\gcd(3a-b,\,b-2a)=\gcd(a,b)$ for all $a,b\in\mathbb Z$?*

**Solution.** **Yes, it is true.** Let $d=\gcd(a,b)$ and $g=\gcd(3a-b,\,b-2a)$.

- Since $d\mid a$ and $d\mid b$, we have $d\mid 3a-b$ and $d\mid b-2a$, so $d$ is a common divisor
  of the two numbers and therefore $d\mid g$.
- Conversely, $g$ divides
  $$(3a-b)+(b-2a)=a \qquad\text{and}\qquad 2(3a-b)+3(b-2a)=(6a-2b)+(3b-6a)=b,$$
  so $g\mid a$ and $g\mid b$, hence $g\mid d$.

Therefore $d=g$ (both are positive). Equivalently, the change of pair
$(a,b)\mapsto(3a-b,\,b-2a)$ is given by the matrix
$\begin{pmatrix}3&-1\\-2&1\end{pmatrix}$ of determinant $3\cdot 1-(-1)(-2)=1$, i.e. it is
unimodular, and unimodular transformations preserve the gcd. $\blacksquare$

### 1.4
*Compute $\gcd(28n-5,\,35n-8)$ for $n\ge 1$.*

**Solution.** Form the combination that cancels $n$:
$$5(28n-5)-4(35n-8)=140n-25-140n+32=7.$$
Hence $\gcd(28n-5,35n-8)\mid 7$, so the gcd is $1$ or $7$. But
$$28n-5\equiv -5\equiv 2 \pmod 7,$$
so $7\nmid 28n-5$; therefore the gcd cannot be $7$.

**Answer:** $\gcd(28n-5,\,35n-8)=1$ for every $n\ge 1$.

### 1.5
*Find the gcd and Bézout coefficients of each pair (and check).*

**Solution.**

**a) $1492,\,1776$.** Euclidean algorithm:
$$1776=1\cdot 1492+284,\quad 1492=5\cdot 284+72,\quad 284=3\cdot 72+68,\quad 72=1\cdot 68+4,\quad 68=17\cdot 4+0.$$
So $\gcd=4$. Back-substitution:
$$4=72-68=72-(284-3\cdot72)=4\cdot72-284=4(1492-5\cdot284)-284=4\cdot1492-21\cdot284$$
$$=4\cdot1492-21(1776-1492)=25\cdot1492-21\cdot1776.$$
**Answer:** $\gcd(1492,1776)=4$ and $25\cdot 1492+(-21)\cdot 1776=4$.
*Check:* $25\cdot1492=37300$, $21\cdot1776=37296$, difference $4$. ✔

**b) $7469,\,2464$.**
$$7469=3\cdot2464+77,\qquad 2464=32\cdot 77+0 .$$
So $\gcd=77$. Reading the first identity backwards:
$$77=1\cdot 7469-3\cdot 2464.$$
**Answer:** $\gcd(7469,2464)=77$ and $1\cdot7469+(-3)\cdot2464=77$.
*Check:* $7469-7392=77$. ✔

**c) $500,\,11312$.**
$$11312=22\cdot500+312,\quad 500=312+188,\quad 312=188+124,\quad 188=124+64,$$
$$124=64+60,\quad 64=60+4,\quad 60=15\cdot4+0 .$$
So $\gcd=4$. Back-substitution:
$$4=64-60=2\cdot64-124=2\cdot188-3\cdot124=5\cdot188-3\cdot312=5\cdot500-8\cdot312$$
$$=5\cdot500-8(11312-22\cdot500)=181\cdot500-8\cdot11312.$$
**Answer:** $\gcd(500,11312)=4$ and $181\cdot500+(-8)\cdot11312=4$.
*Check:* $90500-90496=4$. ✔

### 1.6
*Compute the least common multiple of each pair from 1.5.*

**Solution.** Use $\operatorname{lcm}(a,b)=\dfrac{|ab|}{\gcd(a,b)}$.

- $\operatorname{lcm}(1492,1776)=\dfrac{1492\cdot1776}{4}=373\cdot1776=662448.$
- $\operatorname{lcm}(7469,2464)=\dfrac{7469\cdot2464}{77}=97\cdot2464=239008.$
- $\operatorname{lcm}(500,11312)=\dfrac{500\cdot11312}{4}=125\cdot11312=1414000.$

### 1.7
*Show that $\dfrac{4n+5}{2n+3}$ is irreducible for every $n\ge 1$.*

**Solution.** Any common divisor $d$ of numerator and denominator must divide
$$(4n+5)-2(2n+3)=(4n+5)-(4n+6)=-1 .$$
Hence $d=\pm1$ and the fraction is irreducible (it is already in lowest terms, since
$2n+3>0$). $\blacksquare$

### 1.8
*Solve the Diophantine equations.*

**Solution.** Recall: $ax+by=c$ has integer solutions iff $\gcd(a,b)\mid c$; if $(x_0,y_0)$ is one
solution, all are $x=x_0+\frac{b}{g}t,\; y=y_0-\frac{a}{g}t$ ($g=\gcd(a,b)$, $t\in\mathbb Z$).

**a) $93x-81y=3$.** Dividing by $3$: $31x-27y=1$. Euclidean algorithm:
$$31=1\cdot27+4,\quad 27=6\cdot4+3,\quad 4=1\cdot3+1 .$$
Back-substitution: $1=4-3=4-(27-6\cdot4)=7\cdot4-27=7(31-27)-27=7\cdot31-8\cdot27$.
So $(x_0,y_0)=(7,8)$. From $31(x-7)=27(y-8)$ and $\gcd(31,27)=1$ we get $x-7=27t$:
$$\boxed{x=7+27t,\qquad y=8+31t,\qquad t\in\mathbb Z.}$$
*Check:* $93(7)-81(8)=651-648=3$. ✔

**b) $71x-50y=1$.** Euclid:
$$71=1\cdot50+21,\quad 50=2\cdot21+8,\quad 21=2\cdot8+5,\quad 8=1\cdot5+3,\quad 5=1\cdot3+2,\quad 3=1\cdot2+1 .$$
Back-substitution:
$$1=3-2=2\cdot3-5=2\cdot8-3\cdot5=8\cdot8-3\cdot21=8\cdot50-19\cdot21=27\cdot50-19\cdot71 .$$
So $71\cdot(-19)-50\cdot(-27)=1$, i.e. $(x_0,y_0)=(-19,-27)$:
$$\boxed{x=-19+50t,\qquad y=-27+71t,\qquad t\in\mathbb Z.}$$
*Check:* $71(-19)-50(-27)=-1349+1350=1$. ✔

**c) $42x+18y=34$.** $\gcd(42,18)=6$, but $6\nmid 34$. **No integer solutions.** $\blacksquare$

**d) $283x-1722y=31$.** Euclid:
$$1722=6\cdot283+24,\quad 283=11\cdot24+19,\quad 24=1\cdot19+5,\quad 19=3\cdot5+4,\quad 5=1\cdot4+1 .$$
Back-substitution:
$$1=5-4=4\cdot5-19=4\cdot24-5\cdot19=59\cdot24-5\cdot283=59\cdot1722-359\cdot283 .$$
So $1=(-359)\cdot283+59\cdot1722$, i.e. $283\cdot(-359)-1722\cdot(-59)=1$. Multiplying by $31$:
$$283\cdot(-11129)-1722\cdot(-1829)=31 .$$
Reducing the particular solution modulo $1722$: $-11129+7\cdot1722=925$, and correspondingly
$y=-1829+7\cdot283=152$:
$$\boxed{x=925+1722t,\qquad y=152+283t,\qquad t\in\mathbb Z.}$$
*Check:* $283\cdot925-1722\cdot152=261775-261744=31$. ✔

### 1.9
*a) Compute $\gcd(1911,65)$ by the Euclidean algorithm. b) Decide whether $3822x+65y=26$ has solutions and, if so, describe them all.*

**Solution.**

**a)** $1911=29\cdot65+26$; $\quad 65=2\cdot26+13$; $\quad 26=2\cdot13+0$. Hence
$$\gcd(1911,65)=13 .$$
Bézout coefficients: $13=65-2\cdot26=65-2(1911-29\cdot65)=59\cdot65-2\cdot1911$, that is
$$(-2)\cdot1911+59\cdot65=13 .$$

**b)** $3822=2\cdot1911$. Since $\gcd(2,65)=1$,
$$\gcd(3822,65)=\gcd(2\cdot1911,65)=\gcd(1911,65)=13 .$$
Because $13\mid 26$, **there are solutions.** Multiplying the Bézout identity of (a) by $2$:
$$26=(-4)\cdot1911+118\cdot65=(-2)\cdot3822+118\cdot65 .$$
So $(x_0,y_0)=(-2,118)$ is a particular solution. From $3822(x+2)=-65(y-118)$ and
$3822=13\cdot294,\ 65=13\cdot5$, we get $294(x+2)=-5(y-118)$; since $\gcd(294,5)=1$, $x+2=5s$:
$$\boxed{x=-2+5s,\qquad y=118-294s,\qquad s\in\mathbb Z.}$$
*Check for $s=1$:* $(x,y)=(3,-176)$, and $3822\cdot3+65\cdot(-176)=11466-11440=26$. ✔

### 1.10
*The birthday game: day times 12, month times 31, and only the sum $S$ is told. Guess the birthday.*

**Solution.** Let $d\in\{1,\dots,31\}$ be the day and $m\in\{1,\dots,12\}$ the month. We know only
$$S=12d+31m .$$

*Uniqueness:* if $12d_1+31m_1=12d_2+31m_2$, then $12(d_1-d_2)=31(m_2-m_1)$. Thus
$12\mid 31(m_2-m_1)$, and since $\gcd(12,31)=1$, $12\mid m_2-m_1$. But
$|m_2-m_1|\le 11<12$, so $m_1=m_2$, and then $d_1=d_2$. So the pair $(d,m)$ is uniquely
determined by $S$ (indeed no two birthdays give the same sum).

*Recovering the date:* reduce the equation modulo $12$: $S\equiv 31m\equiv 7m \pmod{12}$.
Since $7\cdot7=49\equiv1\pmod{12}$,
$$m\equiv 7S \pmod{12},$$
and $m$ is the representative of this class in $\{1,\dots,12\}$ (take $12$ if the residue is $0$).
Then
$$d=\frac{S-31m}{12},$$
which is an integer between $1$ and $31$ automatically (the possible sums are $43\le S\le744$).

*Example.* For $S=353$: $7\cdot353=2471\equiv 11 \pmod{12}$, so $m=11$ (November) and
$d=(353-341)/12=1$, i.e. the birthday is **November 1st**. ✔

### 1.11
*Show that if $ab$ is a perfect square and $\gcd(a,b)=1$ (the sheet writes $\gcd(m,n)=1$, a typo), then $a$ and $b$ are both perfect squares.*

**Solution.** If $a=0$ (then $b=\pm1$) or $b=0$, the claim is immediate; assume $ab\ne0$. Write
$a=\prod_p p^{\alpha_p}$, $b=\prod_p p^{\beta_p}$. Two facts:

1. $\gcd(a,b)=1$ means that for each prime $p$, at most one of $\alpha_p,\beta_p$ is positive.
2. $ab=c^2$ means $\alpha_p+\beta_p=v_p(c^2)$ is **even** for every $p$.

By (1), for each prime $p$ one of $\alpha_p,\beta_p$ is $0$, so by (2) the other one equals the
even number $\alpha_p+\beta_p$ (up to sign, i.e. both exponents are even). Hence
$a=\prod_p p^{\alpha_p}$ and $b=\prod_p p^{\beta_p}$ are products of primes with even exponents:
$$a=\Bigl(\prod_p p^{\alpha_p/2}\Bigr)^2,\qquad b=\Bigl(\prod_p p^{\beta_p/2}\Bigr)^2$$
are both perfect squares. $\blacksquare$

### 1.12
*Show that if $a^2\mid b^2$ then $a\mid b$.*

**Solution.** Let $g=\gcd(a,b)$, and write $a=ga'$, $b=gb'$ with $\gcd(a',b')=1$. Then
$a^2\mid b^2$ becomes $g^2a'^2\mid g^2b'^2$, hence (cancelling $g^2\ne0$)
$$a'^2\mid b'^2 .$$
If $|a'|>1$, take a prime $p\mid a'$. Then $p\mid a'^2\mid b'^2$, so $p\mid b'$, contradicting
$\gcd(a',b')=1$. Therefore $a'=\pm1$, i.e. $a=\pm g$, and so $a\mid b$. $\blacksquare$

*Valuation alternative:* $a^2\mid b^2 \Rightarrow 2v_p(a)\le 2v_p(b) \Rightarrow v_p(a)\le v_p(b)$
for all $p$, i.e. $a\mid b$.

### 1.13
*Find the smallest $n$ such that $n/2$ is a square, $n/3$ is a cube and $n/5$ is a fifth power.*

**Solution.** Write $n=\prod_p p^{e_p}$. The three conditions say, for every prime $p$:

- $n/2$ square: $e_2-1$ even and $e_p$ even for $p\ne2$;
- $n/3$ cube: $e_3-1$ divisible by $3$ and $e_p$ divisible by $3$ for $p\ne3$;
- $n/5$ fifth power: $e_5-1$ divisible by $5$ and $e_p$ divisible by $5$ for $p\ne5$.

So, by CRT-type reasoning on each exponent (the smallest nonnegative solution of a congruence):

| prime | conditions | smallest $e_p$ |
|-------|-----------|----------------|
| $2$ | $e\equiv1\pmod2,\; e\equiv0\pmod3,\; e\equiv0\pmod5$ | $15$ |
| $3$ | $e\equiv1\pmod3,\; e\equiv0\pmod2,\; e\equiv0\pmod5$ | $10$ |
| $5$ | $e\equiv1\pmod5,\; e\equiv0\pmod2,\; e\equiv0\pmod3$ | $6$ |
| $p\ne2,3,5$ | $e\equiv0\pmod{2,3,5}$ | $0$ |

Hence
$$\boxed{n=2^{15}\cdot3^{10}\cdot5^{6}=30233088000000 .}$$

*Check:*
$$\frac n2=2^{14}3^{10}5^6=(2^7\,3^5\,5^3)^2=3888000^2,\qquad
\frac n3=2^{15}3^{9}5^6=(2^5\,3^3\,5^2)^3=21600^3,$$
$$\frac n5=2^{15}3^{10}5^{5}=(2^3\,3^2\,5)^5=360^5. \;✔$$

### 1.14
*Prime decompositions of the six integers of 1.5, and check of the gcd/lcm formulas.*

**Solution.** The prime factorizations are
$$1492=2^2\cdot373,\qquad 1776=2^4\cdot3\cdot37,\qquad 7469=7\cdot11\cdot97,$$
$$2464=2^5\cdot7\cdot11,\qquad 500=2^2\cdot5^3,\qquad 11312=2^4\cdot7\cdot101 .$$
(Indeed $373$, $37$, $97$, $101$ are prime.) The formulas read
$\gcd=\prod p^{\min(\alpha_p,\beta_p)}$, $\operatorname{lcm}=\prod p^{\max(\alpha_p,\beta_p)}$.

- **$1492,1776$:** $\gcd=2^{\min(2,4)}=2^2=4$ and
  $\operatorname{lcm}=2^{\max(2,4)}\cdot3\cdot37\cdot373=2^4\cdot3\cdot37\cdot373=1776\cdot373=662448$. ✔
- **$7469,2464$:** $\gcd=7\cdot11=77$ and
  $\operatorname{lcm}=2^5\cdot7\cdot11\cdot97=2464\cdot97=239008$. ✔
- **$500,11312$:** $\gcd=2^2=4$ and
  $\operatorname{lcm}=2^4\cdot5^3\cdot7\cdot101 = 2000\cdot707=1414000$. ✔

All values agree with exercises 1.5 and 1.6.

## 1.2 Congruences

### 1.15
*Compute in the indicated modular arithmetic.*

**Solution.**

**a) $8\cdot(7^2-2)+6$ in $\mathbb Z/12\mathbb Z$:** $7^2=49\equiv1$, so $7^2-2\equiv-1\equiv11$ and
$$8\cdot11+6=88+6=94\equiv 94-84=10 \pmod{12}. \qquad \boxed{10}$$

**b) $(8^3-1)^4$ in $\mathbb Z/6\mathbb Z$:** $8\equiv2$, $8^3\equiv2^3=8\equiv2$, so $8^3-1\equiv1$
and
$$(8^3-1)^4\equiv 1^4=1 \pmod 6. \qquad \boxed{1}$$

**c) $\bigl((4^3)^5-1\bigr)^4+2^4(3^4-1)$ in $\mathbb Z/10\mathbb Z$:** $4^2\equiv6$, $4^3\equiv4$,
$4^4\equiv6$, $4^5\equiv4$, so $(4^3)^5\equiv4$ and $(4^3)^5-1\equiv3$, giving
$3^4=81\equiv1$. Also $3^4\equiv1$ yields $2^4(3^4-1)\equiv16\cdot 0=0$. Total:
$$1+0=1 \pmod{10}. \qquad \boxed{1}$$

### 1.16
*Prove: $a\equiv b \pmod m\Rightarrow ka\equiv kb\pmod m$ for every $k$. Is the converse true? What if $k$ is prime?*

**Solution.** If $m\mid a-b$, then $m\mid k(a-b)=ka-kb$, so $ka\equiv kb\pmod m$.

**The converse is false in general.** Counterexample: $k=2$, $m=6$, $a=1$, $b=4$:
$$2\cdot1=2\equiv 2\cdot4=8 \pmod 6,\qquad\text{but}\qquad 1\not\equiv 4 \pmod 6 .$$
The cancellation is only valid when $\gcd(k,m)=1$ (then $k$ is a unit mod $m$). By Bézout,
$ku+mv=1$, so $a\equiv kua\equiv kub\equiv b\pmod m$.

**Being prime is not enough.** Take $k=2$ (prime), $m=4$, $a=1$, $b=3$:
$2\equiv 6\equiv 2\pmod 4$ but $1\not\equiv3\pmod4$. The correct hypothesis is
$\gcd(k,m)=1$, not primeness of $k$. $\blacksquare$

### 1.17
*Prove: $a\equiv b \pmod m\Rightarrow a^n\equiv b^n\pmod m$ for every $n$. Is the converse true?*

**Solution.** For $n\ge0$ use induction on $n$: $n=0$ is $1\equiv1$; if $a^n\equiv b^n$, then
multiplying by $a\equiv b$ (exercise 1.16) gives $a^{n+1}=a\cdot a^n\equiv b\cdot b^n=b^{n+1}$.
(For negative exponents one first needs $a$ invertible; the statement is meant for $n\ge0$.)

**The converse is false.** Counterexample: $m=3$, $a=1$, $b=2$ (taking $n=2$):
$$1^2=1\equiv4=2^2 \pmod 3,\qquad\text{but}\qquad 1\not\equiv2\pmod3 . \qquad\blacksquare$$

### 1.18
*Prove that every odd prime that is a sum of two squares satisfies $p\equiv1\pmod4$.*

**Solution.** *Preliminary note.* Stated literally with "even prime" it is false: the only even
prime is $2=1^2+1^2$, and $2\equiv2\not\equiv1\pmod4$. The true statement (proved here) is for
**odd** primes, with $2=1^2+1^2$ the single exceptional prime representable as a sum of two
squares.

Squares modulo $4$ are $0^2\equiv0$ and $1^2\equiv1$. Hence a sum of two squares is congruent to
$$0,\;1 \text{ or } 2 \pmod 4 .$$
Let $p$ be an odd prime with $p=a^2+b^2$. Since $p$ is odd, $a$ and $b$ have opposite parity;
the square of the even one is $\equiv0$ and of the odd one is $\equiv1\pmod4$. Therefore
$$p=a^2+b^2\equiv1\pmod4 . \qquad\blacksquare$$
(Equivalently: no prime $p\equiv3\pmod4$ is a sum of two squares.) $\blacksquare$

### 1.19
*Complete list of invertible elements modulo $2,3,4,5,6,7,8,9,10$.*

**Solution.** An element $[a]_m$ is invertible iff $\gcd(a,m)=1$:

| $m$ | invertible elements |
|-----|---------------------|
| $2$ | $\{1\}$ |
| $3$ | $\{1,2\}$ |
| $4$ | $\{1,3\}$ |
| $5$ | $\{1,2,3,4\}$ |
| $6$ | $\{1,5\}$ |
| $7$ | $\{1,2,3,4,5,6\}$ |
| $8$ | $\{1,3,5,7\}$ |
| $9$ | $\{1,2,4,5,7,8\}$ |
| $10$ | $\{1,3,7,9\}$ |

The counts are the Euler values $\varphi(2),\dots,\varphi(10)=1,2,2,4,2,6,4,6,4$.

### 1.20
*Are $29$, $234$, $512$ invertible modulo $1170$? Find the inverses when possible.*

**Solution.** $1170=2\cdot3^2\cdot5\cdot13$ (so $\gcd(a,1170)=1$ iff $a$ is coprime to $2,3,5,13$).

- **$29$:** $29$ is prime, $29\ne2,3,5,13$, so $\gcd(29,1170)=1$: **invertible.**
  Euclid: $1170=40\cdot29+10$; $29=2\cdot10+9$; $10=1\cdot9+1$. Back-substitution:
  $$1=10-9=3\cdot10-29=3(1170-40\cdot29)-29=3\cdot1170-121\cdot29 .$$
  So $29^{-1}\equiv-121\equiv 1049\pmod{1170}$. *Check:* $29\cdot1049=30421=26\cdot1170+1$. ✔
- **$234$:** $234=2\cdot3^2\cdot13$ and $1170=5\cdot234$, so $\gcd(234,1170)=234\ne1$:
  **not invertible.**
- **$512$:** $512=2^9$, so $\gcd(512,1170)=2\ne1$: **not invertible.**

### 1.21
*Find all solutions.*

**Solution.**

**a) $31x=1$ in $\mathbb Z/101\mathbb Z$.** Euclid: $101=3\cdot31+8$; $31=3\cdot8+7$;
$8=1\cdot7+1$. Back-substitution:
$$1=8-7=8-(31-3\cdot8)=4\cdot8-31=4(101-3\cdot31)-31=4\cdot101-13\cdot31 .$$
Hence $-13\cdot31\equiv1$, i.e. $x\equiv-13\equiv88\pmod{101}$.
*Check:* $31\cdot88=2728=27\cdot101+1$. ✔ $\;\boxed{x\equiv88\pmod{101}}$

**b) $4x\equiv0 \pmod{18}$.** $18\mid4x\iff9\mid x$ (cancel $2$, coprime to $9$). In
$\mathbb Z/18\mathbb Z$: $x\in\{0,9\}$. $\;\boxed{x\equiv0 \text{ or } 9 \pmod{18}}$

**c) $6x\equiv0 \pmod{30}$.** $30\mid6x\iff5\mid x$. In $\mathbb Z/30\mathbb Z$:
$$x\in\{0,5,10,15,20,25\}. \qquad \boxed{x\equiv0 \bmod 5}$$

### 1.22
*Solve the systems over the indicated rings (the systems were lost in the .md; restored from the PDF).*

> **a)** in $\mathbb Z/17\mathbb Z$: $\begin{cases} x+3y=15\\ -2x+14y=1\end{cases}$
> **b)** in $\mathbb Z/5\mathbb Z$ and $\mathbb Z/25\mathbb Z$: $\begin{cases} 3x+2y=0\\ 2x-4y=2\end{cases}$
> **c)** in $\mathbb Z/5\mathbb Z$ and $\mathbb Z/25\mathbb Z$: $\begin{cases} 3x+2y=0\\ 4x-4y=2\end{cases}$
> **d)** in $\mathbb Z/2\mathbb Z$ and $\mathbb Z/7\mathbb Z$: $\begin{cases}3x+2y+z=0\\ x-y-4z=2\\ -x+2y+3z=3\end{cases}$

**Solution.**

**a)** Determinant $\Delta=1\cdot14-3\cdot(-2)=20\equiv3\pmod{17}$, a unit ($3^{-1}=6$). Cramer:
$$x=\frac{\begin{vmatrix}15&3\\1&14\end{vmatrix}}{\Delta}=\frac{207}{3}\equiv \frac{3}{3}\equiv 3\cdot6=18\equiv1,
\qquad
y=\frac{\begin{vmatrix}1&15\\-2&1\end{vmatrix}}{\Delta}=\frac{31}{3}\equiv 14\cdot6=84\equiv16 .$$
*Substitution method (check):* $x=15-3y\Rightarrow -2(15-3y)+14y=1\Rightarrow 20y\equiv31\equiv14$, and
$20\equiv3$, $y\equiv 14\cdot6=84\equiv16$, $x=15-48=-33\equiv1$.
*Check:* $1+3\cdot16=49\equiv15$; $-2+14\cdot16=222\equiv1$.
$$\boxed{(x,y)=(1,16)\ \text{in }\mathbb Z/17\mathbb Z}$$

**b)** Determinant $\Delta=3\cdot(-4)-2\cdot2=-16$.
In $\mathbb Z/5\mathbb Z$: $\Delta\equiv-16\equiv4$ (unit, $4^{-1}=4$). From $2x=2+4y$:
$x=1+2y$ ($2^{-1}=3$). Substituting in the first equation: $3(1+2y)+2y=0\Rightarrow 8y\equiv-3\equiv2
\Rightarrow 3y\equiv2\Rightarrow y\equiv4$, $x\equiv1+8\equiv4$.
*Cramer check:* $x=\frac{-4}{-16}=\frac{1}{4}\equiv4$, $y=\frac{6}{-16}=\frac{1}{4}\equiv4$.
$$\boxed{(x,y)=(4,4)\ \text{in }\mathbb Z/5\mathbb Z}$$

In $\mathbb Z/25\mathbb Z$: $\Delta\equiv9$, $9^{-1}=14$. Substitution: $x=1+2y$ ($2^{-1}=13$),
$3(1+2y)+2y=0\Rightarrow 8y\equiv-3\equiv22\Rightarrow y\equiv22\cdot22=484\equiv9$
($8^{-1}=22$), hence $x\equiv1+18=19$.
*Cramer check:* $x=\frac{-4}{9}=-4\cdot14=-56\equiv19$, $y=\frac{6}{9}=6\cdot14=84\equiv9$.
$$\boxed{(x,y)=(19,9)\ \text{in }\mathbb Z/25\mathbb Z}$$

**c)** **No solutions, in either ring.** Add the two equations: $(3x+2y)+(4x-4y)\equiv0+2$, i.e.
$7x-2y\equiv2$; a cleaner elimination: multiply the first equation by $4$ and the second by $3$:
$$12x+8y\equiv0,\qquad 12x-12y\equiv6 .$$
Subtracting: $20y\equiv-6$.

- Modulo $5$: $20y\equiv0$ but $-6\equiv4$, so $0\equiv4$: contradiction (equivalently,
  modulo $5$ the two left-hand sides become proportional, $2x+3y$, with right sides $0$ and $1$).
- Modulo $25$: the values of $20y$ are $0,5,10,15,20$, never $-6\equiv19$: contradiction.

**d)** In $\mathbb Z/2\mathbb Z$ (where $3\equiv1$, $2\equiv0$, $-1\equiv1$, $-4\equiv0$) the system
becomes
$$x+z=0,\qquad x+y=0,\qquad x+z=1,$$
and the first and third equations contradict each other: **no solutions.**

In $\mathbb Z/7\mathbb Z$: from $x-y-4z=2$ we get $x=2+y+4z$. Substituting into the first equation:
$$3(2+y+4z)+2y+z=6+5y+13z\equiv0 \;\Rightarrow\; 5y+13z\equiv1 .$$
Substituting into the third: $-(2+y+4z)+2y+3z=-2+y-z\equiv3\Rightarrow y-z\equiv5\Rightarrow y=5+z$.
Then
$$5(5+z)+13z=25+18z\equiv1 \Rightarrow 18z\equiv-24\Rightarrow 4z\equiv4 \Rightarrow z=1,$$
so $y=6$ and $x=2+6+4=12\equiv5$.
*Check:* $3\cdot5+2\cdot6+1=28\equiv0$; $5-6-4=-5\equiv2$; $-5+12+3=10\equiv3$. ✔
$$\boxed{(x,y,z)=(5,6,1)\ \text{in }\mathbb Z/7\mathbb Z}$$

### 1.23
*Which matrices are invertible over the indicated rings? Find the inverses (matrices restored from the PDF).*

> **a)** $A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$ in $\mathbb Z/3\mathbb Z$;
> **b)** $A$ in $\mathbb Z/10\mathbb Z$;
> **c)** $B=\begin{pmatrix}3&2&1\\1&-1&-4\\-1&2&3\end{pmatrix}$ in $\mathbb Z/3\mathbb Z$, $\mathbb Z/5\mathbb Z$, $\mathbb Z/10\mathbb Z$;
> **d)** $D=\begin{pmatrix}1&2&0&0\\3&-4&0&1\\0&0&2&-1\\0&3&2&5\end{pmatrix}$ in $\mathbb Z/2\mathbb Z,\mathbb Z/3\mathbb Z,\mathbb Z/5\mathbb Z,\mathbb Z/7\mathbb Z,\mathbb Z/9\mathbb Z,\mathbb Z/55\mathbb Z$.

**Solution.** *Criterion:* a square matrix over $\mathbb Z/n\mathbb Z$ is invertible iff $\det A$ is
a unit modulo $n$, i.e. $\gcd(\det A,n)=1$ (if $\det A$ is a unit, $A^{-1}=(\det A)^{-1}\operatorname{adj}A$;
if $A$ is invertible, $1=\det(AA^{-1})=\det A\det A^{-1}$ shows $\det A$ is a unit).

**a)** $\det A=1\cdot4-2\cdot3=-2\equiv1\pmod3$: a unit, so $A$ is invertible in
$\mathbb Z/3\mathbb Z$. Moreover $A\equiv\begin{pmatrix}1&2\\0&1\end{pmatrix}$ and
$$\begin{pmatrix}1&2\\0&1\end{pmatrix}^{-1}=\begin{pmatrix}1&-2\\0&1\end{pmatrix}
\equiv\begin{pmatrix}1&1\\0&1\end{pmatrix}\pmod3 .$$
$$\boxed{A^{-1}=\begin{pmatrix}1&1\\0&1\end{pmatrix}\ \text{in }\mathbb Z/3\mathbb Z}$$
*Check:* $\begin{pmatrix}1&2\\0&1\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix}
=\begin{pmatrix}1&3\\0&1\end{pmatrix}\equiv I$. ✔

**b)** $\det A=-2$, and $\gcd(2,10)=2\ne1$: **not invertible in $\mathbb Z/10\mathbb Z$.**
(Indeed over $\mathbb Z/2\mathbb Z$ both rows coincide: $A\equiv\begin{pmatrix}1&0\\1&0\end{pmatrix}$.)

**c)** $\det B=3\bigl((-1)\cdot3-(-4)\cdot2\bigr)-2\bigl(1\cdot3-(-4)\cdot(-1)\bigr)
+1\bigl(1\cdot2-(-1)\cdot(-1)\bigr)=3\cdot5-2\cdot(-1)+1\cdot1=18 .$

- In $\mathbb Z/3\mathbb Z$: $\det B\equiv0$: **not invertible.**
- In $\mathbb Z/5\mathbb Z$: $\det B\equiv3$, a unit ($3^{-1}=2$). Gauss–Jordan elimination (or
  $B^{-1}=2\cdot\operatorname{adj}B$) gives
  $$\boxed{B^{-1}=\begin{pmatrix}0&2&1\\2&0&1\\2&4&0\end{pmatrix}\ \text{in }\mathbb Z/5\mathbb Z}$$
  *Check* (products mod 5): row 1 of $B$ times columns: $3\cdot0+2\cdot2+1\cdot2=6\equiv1$,
  $3\cdot2+2\cdot0+1\cdot4=10\equiv0$, $3\cdot1+2\cdot1+1\cdot0=5\equiv0$; row 2:
  $1\cdot0-1\cdot2-4\cdot2=-10\equiv0$, $1\cdot2-1\cdot0-4\cdot4=-14\equiv1$,
  $1\cdot1-1\cdot1-4\cdot0=0$; row 3: $-1\cdot0+2\cdot2+3\cdot2=10\equiv0$,
  $-1\cdot2+2\cdot0+3\cdot4=10\equiv0$, $-1\cdot1+2\cdot1+3\cdot0=1$. Thus $B\,B^{-1}=I$. ✔
- In $\mathbb Z/10\mathbb Z$: $\det B=18$, $\gcd(18,10)=2\ne1$: **not invertible.**

**d)** Expanding $\det D$ along the first row:
$$\det D=1\cdot\begin{vmatrix}-4&0&1\\0&2&-1\\3&2&5\end{vmatrix}
-2\cdot\begin{vmatrix}3&0&1\\0&2&-1\\0&2&5\end{vmatrix}
=\bigl(-4\cdot12-6\bigr)-2\cdot(3\cdot12)=-54-72=-126 .$$
So $\det D=-126=-2\cdot3^2\cdot7$.

- $\mathbb Z/2\mathbb Z,\ \mathbb Z/3\mathbb Z,\ \mathbb Z/7\mathbb Z,\ \mathbb Z/9\mathbb Z$:
  $\det D\equiv0$ modulo each of $2,3,7,9$: **not invertible** in any of these rings.
- $\mathbb Z/5\mathbb Z$: $\det D\equiv-126\equiv4$, a unit: **invertible**, and
  $$\boxed{D^{-1}=\begin{pmatrix}4&4&4&1\\1&3&3&2\\1&3&3&0\\2&1&0&0\end{pmatrix}\ \text{in }\mathbb Z/5\mathbb Z}$$
- $\mathbb Z/55\mathbb Z$ ($55=5\cdot11$): $\gcd(126,55)=1$, so $D$ is **invertible**, and
  $$\boxed{D^{-1}=\begin{pmatrix}24&29&14&41\\16&13&48&7\\51&38&48&35\\47&21&40&15\end{pmatrix}\ \text{in }\mathbb Z/55\mathbb Z}$$

In both cases the inverse was obtained by Gauss–Jordan elimination and verified by direct
multiplication $D\,D^{-1}=D^{-1}D=I$ (mod $5$ and mod $55$ respectively). ✔

## 1.3 The Chinese remainder theorem

### 1.24
*(Sun Tsu Suan-Ching) Counted in threes, two remain; in fives, three remain; in sevens, two remain. How many objects?*

**Solution.** We must solve
$$x\equiv2\ (\mathrm{mod}\ 3),\qquad x\equiv3\ (\mathrm{mod}\ 5),\qquad x\equiv2\ (\mathrm{mod}\ 7).$$
The moduli $3,5,7$ are pairwise coprime, so the solution is unique modulo $3\cdot5\cdot7=105$.
Sequential substitution: $x=2+3k$; then $2+3k\equiv3\pmod5\Rightarrow 3k\equiv1\Rightarrow k\equiv2$
($3^{-1}=2$), so $k=2+5m$ and $x=8+15m$. Then $8+15m\equiv2\pmod7\Rightarrow 1+m\equiv2\Rightarrow m\equiv1$,
so $x=23+105t$.
*Check:* $23=3\cdot7+2$, $23=5\cdot4+3$, $23=7\cdot3+2$. ✔
$$\boxed{x\equiv23\pmod{105}}$$
(The smallest positive answer is the classical **23**.)

### 1.25
*Solve the systems of congruences (restored from the PDF).*

> **a)** $x\equiv10\pmod7,\ x\equiv6\pmod9,\ x\equiv1\pmod{10}$.
> **b)** $x\equiv3\pmod4,\ x\equiv1\pmod{15},\ x\equiv2\pmod7$.
> **c)** $3x\equiv2\pmod4,\ 4x\equiv7\pmod{15},\ 8x\equiv-1\pmod7$.

**Solution.**

**a)** Moduli $7,9,10$ pairwise coprime, $M=630$. Solve $x\equiv6\pmod9$, $x\equiv1\pmod{10}$ first:
$x=1+10k$; $1+10k\equiv6\pmod9\Rightarrow k\equiv5\pmod9$ (as $10\equiv1$), so $x=51+90m$.
Impose $x\equiv10\equiv3\pmod7$: $51+90m\equiv3\Rightarrow 2-m\equiv3\Rightarrow m\equiv6\pmod7$
($90\equiv-1$), so $x=51+90\cdot6+630t=591+630t$.
*Check:* $591\equiv3\pmod7$, $\equiv6\pmod9$ ($9\cdot65=585$), $\equiv1\pmod{10}$. ✔
$$\boxed{x\equiv591\pmod{630}}$$

**b)** Moduli $4,15,7$ pairwise coprime, $M=420$. Start from $x\equiv2\pmod7$: $x=2+7k$. Then
$2+7k\equiv1\pmod{15}\Rightarrow 7k\equiv-1\equiv14\Rightarrow k\equiv14\cdot13=182\equiv2\pmod{15}$
($7^{-1}=13$), so $x=16+105m$. Impose $x\equiv3\pmod4$: $16+105m\equiv m\equiv3\pmod4$, so
$x=16+315+420t=331+420t$.
*Check:* $331\equiv3\pmod4$, $\equiv1\pmod{15}$, $\equiv2\pmod7$ ($7\cdot47=329$). ✔
$$\boxed{x\equiv331\pmod{420}}$$

**c)** Simplify each congruence (multiply by the inverse of the coefficient):
$$3x\equiv2\ (4)\Rightarrow x\equiv2\cdot3\equiv2;\qquad 4x\equiv7\ (15)\Rightarrow x\equiv7\cdot4=28\equiv13;$$
$$8x\equiv-1\equiv6\ (7)\Rightarrow x\equiv6\quad(8\equiv1).$$
So $x\equiv2\pmod4$, $x\equiv13\pmod{15}$, $x\equiv6\pmod7$ (moduli coprime, $M=420$). From
$x=6+7k$: $6+7k\equiv13\pmod{15}\Rightarrow 7k\equiv7\Rightarrow k\equiv1$, so $x=13+105m$;
$x\equiv2\pmod4\Rightarrow 1+m\equiv2\Rightarrow m\equiv1$, so $x=118+420t$.
*Check against the original congruences:* $3\cdot118=354\equiv2\pmod4$;
$4\cdot118=472\equiv7\pmod{15}$; $8\cdot118=944\equiv-1\pmod7$ ($944=135\cdot7-1$). ✔
$$\boxed{x\equiv118\pmod{420}}$$

### 1.26
*Let $m_1,\dots,m_n>1$ be pairwise coprime and $M=m_1\cdots m_n$. Prove that $a\equiv b\pmod M$ iff $a\equiv b\pmod{m_i}$ for all $i$. Relation with CRT?*

**Solution.** *($\Rightarrow$)* If $M\mid a-b$, then since $m_i\mid M$ also $m_i\mid a-b$.

*($\Leftarrow$)* Suppose $m_i\mid a-b$ for every $i$. We show $M=m_1\cdots m_n\mid a-b$ by induction
on $n$. For $n=2$: $m_1\mid a-b$ and $m_2\mid a-b$ with $\gcd(m_1,m_2)=1$ imply
$m_1m_2\mid a-b$. Inductive step: if $m_1\cdots m_{n-1}\mid a-b$ and $m_n\mid a-b$, the two
factors are coprime, so their product $M$ divides $a-b$.

**Relation with CRT.** The map
$$\varphi:\mathbb Z/M\mathbb Z\longrightarrow \mathbb Z/m_1\mathbb Z\times\cdots\times\mathbb Z/m_n\mathbb Z,
\qquad [a]_M\mapsto([a]_{m_1},\dots,[a]_{m_n})$$
is well defined, and this exercise says exactly that $\varphi$ is **injective** (two classes with
the same image everywhere coincide, i.e. $\#\mathbb Z/M\mathbb Z=M=m_1\cdots m_n$). Since domain
and codomain both have $M$ elements, injectivity is equivalent to bijectivity — this is one of
the standard formulations of the **Chinese Remainder Theorem**: $\varphi$ is an isomorphism iff
the $m_i$ are pairwise coprime. $\blacksquare$

### 1.27
*Decide whether the maps (restored from the PDF) are bijective:*
$$f:\mathbb Z/18\mathbb Z\to\mathbb Z/2\mathbb Z\times\mathbb Z/6\mathbb Z\times\mathbb Z/9\mathbb Z,
\quad [x]_{18}\mapsto([x]_2,[x]_6,[x]_9);$$
$$g:\mathbb Z/18\mathbb Z\to\mathbb Z/2\mathbb Z\times\mathbb Z/9\mathbb Z,
\quad [x]_{18}\mapsto([x]_2,[x]_9).$$

**Solution.**

**$g$ is bijective.** Indeed $g([x])=g([y])$ means $x\equiv y\pmod2$ and $x\equiv y\pmod9$, and since
$\gcd(2,9)=1$ this is equivalent (exercise 1.26) to $x\equiv y\pmod{18}$. So $g$ is injective,
and both sets have $18$ elements, hence $g$ is bijective. This matches the CRT: $2$ and $9$ are
coprime, and $2\cdot9=18$.

**$f$ is not bijective.** It is injective: $f([x])=f([y])$ means $x\equiv y$ modulo $2$, $6$ and
$9$, which is equivalent to $x\equiv y$ modulo their least common multiple
$\operatorname{lcm}(2,6,9)=18$; hence $[x]_{18}=[y]_{18}$.
However $f$ is **not surjective**: the codomain has $2\cdot6\cdot9=108$ elements while the domain
has $18$. Explicitly, the triple $(0,1,0)$ is not in the image: $x\equiv1\pmod6$ forces $x$ odd,
while $x\equiv0\pmod2$ forces $x$ even.

This mismatch is exactly what CRT warns about: the theorem needs the moduli to be **pairwise
coprime**, and here $\gcd(2,6)=2\ne1$, so there is no reason for $f$ to be onto (and indeed it
is not). The projection $([x]_2,[x]_6)$ alone would be injective into a $12$-element set, and
for $f$ the "surplus" is the redundancy: once $[x]_6$ is known, $[x]_2$ is determined.

## 1.4 Fermat and Euler's theorems

### 1.28
*a) Find the inverse of $37$ in $\mathbb Z/98\mathbb Z$. b) Compute $37^{55}\cdot53^{13}\pmod{98}$.*

**Solution.**

**a)** Euclid: $98=2\cdot37+24$; $37=1\cdot24+13$; $24=1\cdot13+11$; $13=1\cdot11+2$; $11=5\cdot2+1$.
Back-substitution:
$$1=11-5\cdot2=11-5(13-11)=6\cdot11-5\cdot13=6(24-13)-5\cdot13=6\cdot24-11\cdot13$$
$$=6(37-24)-11\cdot13=17\cdot24-11\cdot37=17(98-2\cdot37)-11\cdot37=17\cdot98-45\cdot37 .$$
So $-45\cdot37\equiv1$, i.e.
$$\boxed{37^{-1}\equiv-45\equiv53\pmod{98}}$$
*Check:* $37\cdot53=1961=20\cdot98+1$. ✔

**b)** Since $53\equiv37^{-1}\pmod{98}$,
$$37^{55}\cdot53^{13}\equiv37^{55}\cdot37^{-13}=37^{42}\pmod{98}.$$
Now $\varphi(98)=\varphi(2)\varphi(49)=1\cdot42=42$ and $\gcd(37,98)=1$, so by **Euler's theorem**
$37^{42}\equiv1\pmod{98}$:
$$\boxed{37^{55}\cdot53^{13}\equiv1\pmod{98}}$$

### 1.29
*Compute (a) $513^{1017}\pmod6$; (b) $2^{154}\pmod5$; (c) $3^{178}\pmod{12}$.*

**Solution.**

**a)** $513\equiv3\pmod6$, and $3^n\equiv3\pmod6$ for all $n\ge1$ ( $3\cdot3=9\equiv3$; by induction).
$$\boxed{513^{1017}\equiv3\pmod6}$$

**b)** $2^4=16\equiv1\pmod5$, and $154=4\cdot38+2$:
$$2^{154}=(2^4)^{38}\cdot2^2\equiv1\cdot4=4\pmod5 .\qquad \boxed{4}$$

**c)** $3^2=9$, $3^3=27\equiv3$, $3^4=81\equiv9 \pmod{12}$: for $n\ge2$, $3^n\equiv3$ if $n$ is
odd and $\equiv9$ if $n$ is even. Since $178$ is even,
$$\boxed{3^{178}\equiv9\pmod{12}}$$

### 1.30
*Last two digits of $103^{1243}$.*

**Solution.** The last two digits are the residue mod $100$. As $103\equiv3\pmod{100}$, compute
$3^{1243}\bmod100$. We have
$$3^{10}=59049\equiv49,\qquad 3^{20}\equiv49^2=2401\equiv1\pmod{100}.$$
Since $1243=20\cdot62+3$:
$$3^{1243}\equiv (3^{20})^{62}\cdot3^3\equiv1\cdot27=27\pmod{100}.$$
$$\boxed{\text{The last two digits are }27}$$

### 1.31
*Find all $n$ with $10^n+3$ a multiple of $7$.*

**Solution.** Modulo $7$, $10\equiv3$, so the condition is $3^n+3\equiv0$, i.e.
$$3^n\equiv4\pmod7 .$$
The powers of $3$ modulo $7$ are
$$3^1=3,\quad 3^2=2,\quad 3^3=6,\quad 3^4=4,\quad 3^5=5,\quad 3^6=1,$$
and the sequence is periodic of period $6$ (by Fermat, $3^6\equiv1$). The value $4$ appears exactly
at the exponent $4$:
$$\boxed{n\equiv4\pmod6}$$

### 1.32
*Find all $n$ with $4^n+5$ a multiple of $15$.*

**Solution.** A multiple of $15$ must in particular be a multiple of $5$. But modulo $5$,
$$4^n\equiv(-1)^n\equiv\pm1,\qquad\text{so}\qquad 4^n+5\equiv4^n\equiv\pm1\not\equiv0\pmod5 .$$
Hence **there is no such $n$.** (Indeed $4^n\bmod15$ equals $4$ or $1$ for every $n$, never the
needed $10\equiv-5$.) $\blacksquare$

### 1.33
*a) Solve $2^{2021}(x-2^{2022})=4^{2023}\pmod{13}$. b) Deduce a description of all solutions of $2^{2021}(10\cdot3^n-2^{2022})=4^{2023}\pmod{13}$.*

**Solution.**

**a)** Fermat: $2^{12}\equiv1\pmod{13}$. Reduce the exponents modulo $12$:
$$2021=12\cdot168+5\;\Rightarrow\;2^{2021}\equiv2^5=32\equiv6,$$
$$2022=12\cdot168+6\;\Rightarrow\;2^{2022}\equiv2^6=64\equiv12\equiv-1,$$
$$4046=12\cdot337+2\;\Rightarrow\;4^{2023}=2^{4046}\equiv2^2=4 .$$
The equation becomes $6\,(x+1)\equiv4\pmod{13}$. Since $6^{-1}=11$ ($6\cdot11=66\equiv1$),
$$x+1\equiv4\cdot11=44\equiv5\pmod{13}\;\Longrightarrow\; \boxed{x\equiv4\pmod{13}}$$
*Check:* $2^{2021}(4-2^{2022})\equiv6\,(4+1)=30\equiv4\equiv4^{2023}$. ✔

**b)** By part (a), the congruence holds iff $10\cdot3^n\equiv4\pmod{13}$. As $10^{-1}=4$
($10\cdot4=40\equiv1$):
$$3^n\equiv4\cdot4=16\equiv3\pmod{13}.$$
The powers of $3$ modulo $13$ are $3^1=3,\ 3^2=9,\ 3^3=27\equiv1$, so $3$ has order $3$ and
$3^n\equiv3$ iff $n\equiv1\pmod3$:
$$\boxed{n\equiv1\pmod3\qquad(n=1,4,7,10,\dots)}$$

### 1.34
*Compute $2022^{20222022}\pmod{19}$ and $\pmod{21}$.*

**Solution.** **Modulo 19.** $2022=19\cdot106+8$, so $2022\equiv8$. Compute the order of $8$:
$$8^1=8,\quad 8^2=64\equiv7,\quad 8^3=7\cdot8=56\equiv-1\pmod{19},$$
so $8^6\equiv1$. Since
$$20222022=6\cdot3370337,$$
the exponent is a multiple of $6$, hence
$$2022^{20222022}\equiv8^{20222022}\equiv(8^6)^{3370337}\equiv1\pmod{19}. \qquad \boxed{1}$$

**Modulo 21.** $21=3\cdot7$, with $\gcd(3,7)=1$.
- Modulo $3$: $2022\equiv0$, so $2022^{20222022}\equiv0\pmod3$.
- Modulo $7$: $2022=7\cdot288+6\equiv-1$, and the exponent $20222022$ is even, so
  $2022^{20222022}\equiv(-1)^{\text{even}}=1\pmod7$.

Solve $N\equiv0\pmod3$, $N\equiv1\pmod7$: $N=3k$ with $3k\equiv1\pmod7$, i.e. $k\equiv5$ ($3^{-1}=5$),
so $N\equiv15\pmod{21}$.
$$\boxed{2022^{20222022}\equiv15\pmod{21}}$$

### 1.35
*Compute $\varphi(128)$, $\varphi(1123)$, $\varphi(1125)$, $\varphi(29270241)$, $\varphi(12648925575)$.*

**Solution.** Use the formulas $\varphi(p^e)=p^{e-1}(p-1)$ and multiplicativity on coprime factors
(equivalently $\varphi(n)=n\prod_{p\mid n}(1-\tfrac1p)$).

- $\varphi(128)=\varphi(2^7)=2^7-2^6=128-64=\boxed{64}$.
- $1123$ is prime (no prime $\le\sqrt{1123}\approx33.5$ divides it), so
  $\varphi(1123)=\boxed{1122}$.
- $1125=3^2\cdot5^3$:
  $$\varphi(1125)=\varphi(3^2)\varphi(5^3)=3\cdot(3-1)\cdot5^2\cdot(5-1)=6\cdot100=\boxed{600}.$$
- $29270241=3^4\cdot7\cdot11\cdot13\cdot19^2$. Indeed $29270241=81\cdot361361$,
  $361361=7\cdot51623=7\cdot11\cdot4693=7\cdot11\cdot13\cdot361$, $361=19^2$. Then
  $$\varphi(29270241)=\prod \varphi(p^{e}):
  \underbrace{54}_{3^3(3-1)}\cdot 6\cdot 10\cdot 12\cdot \underbrace{342}_{19\cdot18}
  =\boxed{13\,296\,960}.$$
- $12648925575=3^4\cdot5^2\cdot11^3\cdot13\cdot19^2$
  ($=81\cdot25\cdot1331\cdot13\cdot361$). Then
  $$\varphi(12648925575)=54\cdot20\cdot(11^2\cdot10)\cdot12\cdot342
  =\boxed{5\,363\,107\,200}.$$

### 1.36
*Order $\mathbb Z$, $\mathbb Z/11\mathbb Z$, $\mathbb Z/12\mathbb Z$, $\mathbb Z/18\mathbb Z$, $\mathbb Q$ by decreasing number of invertible elements.*

**Solution.** The invertible elements are the units:
$\mathbb Q^\times=\mathbb Q\setminus\{0\}$ (infinitely many); $\mathbb Z^\times=\{\pm1\}$ ($2$ elements);
and for the finite rings the count is $\varphi(m)$:
$$\varphi(11)=10,\qquad \varphi(18)=\varphi(2)\varphi(9)=6,\qquad \varphi(12)=\varphi(4)\varphi(3)=2\cdot2=4 .$$
Hence, in decreasing order:
$$\boxed{\mathbb Q\ \succ\ \mathbb Z\ \succ\ \mathbb Z/11\mathbb Z\ \succ\ \mathbb Z/18\mathbb Z\ \succ\ \mathbb Z/12\mathbb Z}$$
(with counts $\infty,\ 2,\ 10,\ 6,\ 4$). Note $\mathbb Z/11\mathbb Z$ is a field, so all its nonzero
elements are invertible.

### 1.37
*Mersenne numbers $M_q=2^q-1$. (a) $M_q$ prime $\Rightarrow q$ prime. (b) Smallest counterexample to the converse. (c) If $q$ prime and $p\mid M_q$ ($p$ prime) then $p\equiv1\pmod q$. (d) Decide whether $M_{13}$, $M_{17}$ are prime.*

**Solution.**

**a)** If $q$ is not prime, write $q=ab$ with $1<a,b<q$ (and $a>1$). Using the hint with $x=2^a$:
$$M_q=2^{ab}-1=(2^a)^b-1=(2^a-1)\bigl((2^a)^{b-1}+(2^a)^{b-2}+\cdots+2^a+1\bigr).$$
Both factors are $>1$, so $M_q$ is composite. Taking the contrapositive:
$$M_q\text{ prime}\;\Longrightarrow\;q\text{ prime}. \qquad\blacksquare$$

**b)** The first primes give $M_2=3$, $M_3=7$, $M_5=31$, $M_7=127$, all prime, but
$$\boxed{M_{11}=2^{11}-1=2047=23\cdot89}$$
is composite: the converse of (a) fails, with $q=11$ the smallest possible counterexample.
(Note $23\equiv1\pmod{11}$, as predicted by (c).)

**c)** Let $p$ be a prime with $p\mid 2^q-1$, i.e. $2^q\equiv1\pmod p$. Then $p\ne2$ (as $M_q$ is
odd), so $\gcd(2,p)=1$ and the multiplicative order $\operatorname{ord}_p(2)$ of $2$ modulo $p$
is defined, and it divides $q$. As $q$ is prime, $\operatorname{ord}_p(2)\in\{1,q\}$. The value
$1$ would mean $2\equiv1\pmod p$, i.e. $p=1$, impossible. Hence
$$\operatorname{ord}_p(2)=q .$$
By Fermat's little theorem $\operatorname{ord}_p(2)\mid p-1$, so $q\mid p-1$:
$$\boxed{p\equiv1\pmod q}$$
(Moreover $p$ is odd and $q$ is odd, so in fact $p\equiv1\pmod{2q}$.)

**d)** Any prime divisor of $M_q$ is $\le\sqrt{M_q}$ and $\equiv1\pmod q$ (and odd, hence
$\equiv1\pmod{2q}$), which leaves very few candidates.

- $M_{13}=8191$, $\sqrt{8191}\approx90.5$. Candidates $p\equiv1\pmod{26}$ below $90.5$:
  $p=53,\ 79$. Check: $8191=53\cdot154+29$, so $53\nmid8191$; $8191=79\cdot103+54$, so
  $79\nmid8191$. Therefore $M_{13}=8191$ **is prime**.
- $M_{17}=131071$, $\sqrt{131071}\approx362$. Candidates $p\equiv1\pmod{34}$ below $362$:
  $p=103,\ 137,\ 239,\ 307$ (note $341=11\cdot31$, not prime). Check:
  $$131071=103\cdot1272+55,\quad =137\cdot956+99,\quad =239\cdot548+99,\quad =307\cdot426+289,$$
  so none divides $M_{17}$. Therefore $M_{17}=131071$ **is prime**.

## 1.5 True/false problems

### 1.38
*True or false, with justification.*

**a) TRUE.** E.g. $A=\begin{pmatrix}1&0\\0&0\end{pmatrix}$, $B=\begin{pmatrix}0&0\\0&1\end{pmatrix}$:
$AB=\begin{pmatrix}0&0\\0&0\end{pmatrix}$ with $A,B\ne0$ (zero divisors exist in $M_2(\mathbb Z)$,
which is therefore not a domain).

**b) FALSE.** Cancellation fails for non-invertible $A$: take
$A=\begin{pmatrix}1&0\\0&0\end{pmatrix}$, $B=\begin{pmatrix}0&0\\1&0\end{pmatrix}$, $C=0$.
Then $AB=0=AC$ but $B\ne C$. (The implication is true when $A$ is invertible.)

**c) TRUE.** In every ring $0=-0$, so $0$ is opposed to itself. (In $\mathbb Z/2\mathbb Z$ also
$1=-1$.)

**d) FALSE as stated for a general ring.** The correct identity is
$(ab)^{-1}=b^{-1}a^{-1}$, and the given one fails in non-commutative rings. In $M_2(\mathbb Q)$,
take $a=\begin{pmatrix}0&1\\1&0\end{pmatrix}$ ($a^{-1}=a$) and
$b=\begin{pmatrix}1&0\\0&2\end{pmatrix}$ ($b^{-1}=\begin{pmatrix}1&0\\0&\frac12\end{pmatrix}$).
Then $ab=\begin{pmatrix}0&2\\1&0\end{pmatrix}$, $(ab)^{-1}=\begin{pmatrix}0&1\\\frac12&0\end{pmatrix}$,
and $a^{-1}b^{-1}=\begin{pmatrix}0&\frac12\\1&0\end{pmatrix}\ne(ab)^{-1}$. In a **commutative**
ring the statement is true, as $ab\cdot a^{-1}b^{-1}=aa^{-1}bb^{-1}=1$.

**e) TRUE.** In $M_2(\mathbb Q)$ take $a=\begin{pmatrix}0&1\\1&0\end{pmatrix}$ and
$b=\begin{pmatrix}1&0\\0&-1\end{pmatrix}$: $a^2=I$, $b^2=I$, but
$ab=\begin{pmatrix}0&-1\\1&0\end{pmatrix}$ and $(ab)^2=\begin{pmatrix}-1&0\\0&-1\end{pmatrix}=-I\ne I$.

**f) TRUE.** Euclidean algorithm for $\gcd(249018,34650)$:
$$249018=7\cdot34650+6468,\quad 34650=5\cdot6468+2310,\quad 6468=2\cdot2310+1848,$$
$$2310=1\cdot1848+462,\quad 1848=4\cdot462+0 .$$
So the gcd is $462$ (and indeed $249018=539\cdot462$, $34650=75\cdot462$). ✔

**g) FALSE.** $a=4$, $b=c=2$: $4\mid(b+c)=4$ and $4\mid(b-c)=0$, but $4\nmid2$. (The condition
$a\ne2$ is not enough; the statement becomes true for **odd** $a$, see (h).)

**h) TRUE.** If $a\mid b+c$ and $a\mid b-c$, then $a$ divides their sum $2b$ and their difference
$2c$. As $a$ is odd, $\gcd(a,2)=1$, so $a\mid b$ and $a\mid c$.

**i) FALSE.** The claim is that $a'=a/d$ and $b'=b/d$ are always coprime; not so:
$a=12$, $b=8$, $d=2$ gives $a'=6$, $b'=4$ with $\gcd(6,4)=2$. (It is true when
$d=\gcd(a,b)$ — that is precisely the definition of the gcd.)

**j) FALSE.** $\gcd(13,23)=1$ divides $4$, so there are solutions. One of them is
$(x,y)=(-28,16)$: $13\cdot(-28)+23\cdot16=-364+368=4$. All of them:
$$x=-28+23t,\qquad y=16-13t,\quad t\in\mathbb Z .$$

**k) TRUE.** Plug in: $2(16+3\lambda)-6(4+\lambda)=32+6\lambda-24-6\lambda=8$ for every $\lambda$.
Conversely every integer solution has the form $x=4+3s,\ y=s$ (from $x-3y=4$); writing
$s=4+\lambda$ recovers $x=16+3\lambda,\ y=4+\lambda$. So exactly the stated family.

**l) TRUE.** This is the distributive law relating gcd and lcm,
$\gcd(a,\operatorname{lcm}(b,c))=\operatorname{lcm}(\gcd(a,b),\gcd(a,c))$, valid in any lattice
of divisibility. Proof with valuations: for each prime $p$,
$$\min\bigl(v_p(a),\max(v_p(b),v_p(c))\bigr)=\max\bigl(\min(v_p(a),v_p(b)),\min(v_p(a),v_p(c))\bigr),$$
which is the elementary identity $\min(x,\max(y,z))=\max(\min(x,y),\min(x,z))$.

**m) FALSE.** A fourth of $100$ is $25$, and the primes $\le100$ number exactly $25$
($2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97$). So the amount of
primes is *equal to* a fourth, not less.

**n) TRUE.** $2347$ is prime. Indeed $\sqrt{2347}\approx48.4$, so it suffices to test primes
$\le47$; the remainders are
$$2347=7\cdot335+2=11\cdot213+4=13\cdot180+7=17\cdot138+1=19\cdot123+10=23\cdot102+1$$
$$=29\cdot80+27=31\cdot75+22=37\cdot63+16=41\cdot57+10=43\cdot54+25=47\cdot49+44,$$
and $2347$ is odd with digit sum $16$, so $2,3,5$ do not divide it either. No prime $\le\sqrt{2347}$
divides it: it is prime.

**o) TRUE.** If $[a]_m\cap[b]_m\ne\emptyset$ there is $c$ with $c\equiv a$ and $c\equiv b\pmod m$;
then $m\mid c-a$ and $m\mid c-b$, hence $m\mid (c-a)-(c-b)=b-a$, i.e. $m\mid(a-b)$.

**p) TRUE.** If $x\in[a]_{2m}$, then $x-a=2mk$ for some $k$, so $x-a=m(2k)$ and $x\in[a]_m$;
thus $[a]_{2m}\subseteq[a]_m$. The inclusion is strict: $a+m\in[a]_m$ but
$(a+m)-a=m\notin 2m\mathbb Z$, so $a+m\notin[a]_{2m}$.

**q) FALSE.** Take $m=3$, $a=0$, $b=3$: the classes $[0]_3$ (multiples of $3$) and $[3]_6$
(numbers $\equiv3\pmod6$) intersect (e.g. $3$), but $[0]_6\ne[3]_6$ (multiples of $6$ vs. odd
multiples of $3$). What is true: if they intersect then $[b]_{2m}\subseteq[a]_m$.

**r) FALSE.** In $\mathbb Z/6\mathbb Z$, $2\cdot2=4$ and $2\cdot(-1)=-2\equiv4$ are indeed equal,
but the step "$2=(-1)$" is an illegal cancellation: $2$ is not invertible modulo $6$
($\gcd(2,6)=2\ne1$). And in fact $2\not\equiv-1\pmod6$, so $3\ne0$. (The correct conclusion
would be $2\mid 2\cdot 3$ in $\mathbb Z$, i.e. nothing about $3\equiv0$.)

**s) TRUE.** $2x\equiv7\pmod{10}$: the left side is always even modulo $10$ (values $0,2,4,6,8$),
so it can never equal $7$: no solutions. $2x\equiv6\pmod{10}\iff5\mid x-3\iff x\equiv3\pmod5$,
i.e. $x=3,8$: exactly two solutions.

**t) TRUE.** The coefficient determinant is $1\cdot2-3\cdot1=-1\equiv12\not\equiv0\pmod{13}$,
so Cramer applies and the solution is unique (determined) if it exists. From $x=4-2y$ and
$2x+3y=3$: $2(4-2y)+3y=3\Rightarrow8-y=3\Rightarrow y=5$, $x=4-10=-6\equiv7$. Check in the third
equation: $5\cdot7-4\cdot5=15\equiv2$. So $(x,y)=(7,5)$ works, and the system is compatible and
determined.

**u) FALSE.** Counterexample: $r=2$, $s=3$, $a=b=0$, $c=d=1$. Then $a\equiv b\pmod2$ and
$c\equiv d\pmod3$, and $t=\operatorname{lcm}(2,3)=6$, but $a+b=0\not\equiv2=c+d\pmod6$.
(Corrected version, which is true: $a+c\equiv b+d\pmod{\gcd(r,s)}$, since $a\equiv b$ and
$c\equiv d$ both hold modulo $t=\gcd(r,s)$.)

**v) FALSE.** Counterexample: $r=10$, $s=15$, $a=b=2$, $c=d=1$; then $t=\gcd(10,15)=5$, but
$ab=4\not\equiv1=cd\pmod5$. (Corrected version, true: $ac\equiv bd\pmod{\gcd(r,s)}$.)

**w) TRUE.** $11\equiv-2\pmod{13}$, and $11111=12\cdot925+11$ with $2^{12}\equiv1$ (Fermat), so
$$11^{11111}\equiv(-2)^{11111}=-2^{11111}\equiv-2^{11}=-2048 .$$
Now $2048=13\cdot157+7$, so $-2048\equiv-7\equiv6\pmod{13}$. Hence $11^{11111}\equiv6\pmod{13}$. ✔

**x) FALSE.** $22\equiv5$ and $33\equiv-1\pmod{17}$. Since $2222=16\cdot138+14$,
$$22^{2222}\equiv5^{14}=5^8\cdot5^4\cdot5^2\equiv(-1)\cdot13\cdot8=-104\equiv-2\equiv15\pmod{17},$$
where $5^2\equiv8$, $5^4\equiv13$, $5^8\equiv-1$. On the other side
$33^{3333}\equiv(-1)^{3333}=-1\equiv16\pmod{17}$. Since $15\ne16$, the claimed congruence fails.

**y) FALSE.** Take $p=5$, $a=2$, $r=1$, $s=6$: then $r\equiv s\pmod5$, but
$a^{r-1}=2^0=1$ while $a^{s-1}=2^5=32\equiv2\pmod5$, and $1\not\equiv2$. The correct statement:
if $r\equiv s\pmod{p-1}$ and $p\nmid a$ then $a^{r-1}\equiv a^{s-1}\pmod p$ (the exponent lives
modulo the order of $a$, which divides $p-1$, not modulo $p$).

**z) TRUE.** Since $p\ne q$, $\gcd(a,pq)=1$, and $\varphi(pq)=(p-1)(q-1)$. By **Euler's theorem**
$a^{\varphi(pq)}=a^{(p-1)(q-1)}\equiv1\pmod{pq}$. $\blacksquare$

---

## Summary of final answers

| # | Answer |
|---|--------|
| 1.1 | $\gcd(a+b,a-b)\in\{1,2\}$ (both values occur) |
| 1.2 | $\gcd(ma,mb)=m\gcd(a,b)$ for $m\ge0$; in general $\gcd(ma,mb)=\lvert m\rvert\gcd(a,b)$ (proved) |
| 1.3 | Yes: $\gcd(3a-b,b-2a)=\gcd(a,b)$ |
| 1.4 | $\gcd(28n-5,35n-8)=1$ |
| 1.5 | a) $4$, $\;25\cdot1492-21\cdot1776$; b) $77$, $\;7469-3\cdot2464$; c) $4$, $\;181\cdot500-8\cdot11312$ |
| 1.6 | $662448$; $239008$; $1414000$ |
| 1.7 | Irreducible, since $\gcd(4n+5,2n+3)\mid1$ |
| 1.8 | a) $x=7+27t,\ y=8+31t$; b) $x=-19+50t,\ y=-27+71t$; c) none; d) $x=925+1722t,\ y=152+283t$ |
| 1.9 | a) $\gcd=13$; b) $x=-2+5s,\ y=118-294s$ |
| 1.10 | $m\equiv7S\pmod{12}\in\{1,\dots,12\}$, then $d=(S-31m)/12$ (unique) |
| 1.11 | Both are squares (with $\gcd(a,b)=1$) |
| 1.12 | $a^2\mid b^2\Rightarrow a\mid b$ (proved) |
| 1.13 | $n=2^{15}3^{10}5^{6}=30\,233\,088\,000\,000$ |
| 1.14 | $2^2\!\cdot\!373$, $2^4\!\cdot\!3\!\cdot\!37$, $7\!\cdot\!11\!\cdot\!97$, $2^5\!\cdot\!7\!\cdot\!11$, $2^2\!\cdot\!5^3$, $2^4\!\cdot\!7\!\cdot\!101$; min/max formulas verified |
| 1.15 | a) $10$; b) $1$; c) $1$ |
| 1.16 | Direct implication true; converse false (true iff $\gcd(k,m)=1$; primeness insufficient) |
| 1.17 | Direct implication true; converse false |
| 1.18 | Odd primes that are sums of two squares: $p\equiv1\pmod4$; $2=1^2+1^2$ is the exception |
| 1.19 | $\{1\};\{1,2\};\{1,3\};\{1,2,3,4\};\{1,5\};\{1,\dots,6\};\{1,3,5,7\};\{1,2,4,5,7,8\};\{1,3,7,9\}$ |
| 1.20 | $29$ invertible with inverse $1049$; $234$, $512$ not invertible |
| 1.21 | a) $x\equiv88$; b) $x\equiv0,9$; c) $x\equiv0\pmod5$ ($6$ classes) |
| 1.22 | a) $(1,16)$; b) $(4,4)$ mod 5 and $(19,9)$ mod 25; c) no solution; d) no solution mod 2, $(5,6,1)$ mod 7 |
| 1.23 | a) invertible, $\left(\begin{smallmatrix}1&1\\0&1\end{smallmatrix}\right)$; b) no; c) invertible only mod 5, $\left(\begin{smallmatrix}0&2&1\\2&0&1\\2&4&0\end{smallmatrix}\right)$; d) invertible only mod 5 and mod 55 (inverses in §1.23) |
| 1.24 | $x\equiv23\pmod{105}$ (smallest: $23$) |
| 1.25 | a) $x\equiv591\pmod{630}$; b) $x\equiv331\pmod{420}$; c) $x\equiv118\pmod{420}$ |
| 1.26 | Equivalence proved; it is the injectivity half of the CRT isomorphism |
| 1.27 | $f$ injective but not surjective (not bijective); $g$ bijective; CRT needs pairwise coprime moduli |
| 1.28 | a) $37^{-1}\equiv53$; b) $37^{55}53^{13}\equiv1\pmod{98}$ |
| 1.29 | a) $3$; b) $4$; c) $9$ |
| 1.30 | Last two digits: $27$ |
| 1.31 | $n\equiv4\pmod6$ |
| 1.32 | No such $n$ |
| 1.33 | a) $x\equiv4\pmod{13}$; b) $n\equiv1\pmod3$ |
| 1.34 | $\equiv1\pmod{19}$ and $\equiv15\pmod{21}$ |
| 1.35 | $64$, $1122$, $600$, $13\,296\,960$, $5\,363\,107\,200$ |
| 1.36 | $\mathbb Q\succ\mathbb Z\succ\mathbb Z/11\mathbb Z\succ\mathbb Z/18\mathbb Z\succ\mathbb Z/12\mathbb Z$ |
| 1.37 | a) proved; b) $M_{11}=2047=23\cdot89$; c) $p\equiv1\pmod q$; d) $M_{13}=8191$ and $M_{17}=131071$ are both prime |
| 1.38 | T: a, c, e, f, h, k, l, n, o, p, s, t, w, z — F: b, d, g, i, j, m, q, r, u, v, x, y |

*All computations were verified independently (Python + exact integer arithmetic).*
