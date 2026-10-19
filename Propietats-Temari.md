# Propietats del temari

## 1. Anells i cossos

### 1.1 Anell

- **Anell:** \((R,+,\cdot)\) amb \((R,+)\) grup abelià, producte associatiu i distributiu respecte de la suma.
- **Anell commutatiu:** \(ab=ba\) per a tots \(a,b\in R\).
- **Anell amb unitat:** existeix \(1\ne0\) amb \(1a=a1=a\).
- **Domini d'integritat:** anell commutatiu amb unitat, \(1\ne0\), sense divisors de zero.
- **Cos:** anell commutatiu amb unitat, \(1\ne0\), on tot element no nul és invertible.
- **Divisor de zero:** \(a\ne0\) tal que existeix \(b\ne0\) amb \(ab=0\).
- **Unitat:** \(a\) tal que existeix \(b\) amb \(ab=ba=1\); s'escriu \(b=a^{-1}\).

### 1.2 Propietats bàsiques dels anells

- \(a0=0a=0\).
- \((-a)b=-(ab)\), \(a(-b)=-(ab)\), \((-a)(-b)=ab\).
- \(a(b-c)=ab-ac\), \((a-b)c=ac-bc\).
- Si \(a\) és unitat i \(ab=ac\), aleshores \(b=c\).
- En un domini, si \(a\ne0\) i \(ab=ac\), aleshores \(b=c\).
- \((a+b)^n=\sum_{k=0}^n\binom nk a^k b^{n-k}\) en un anell commutatiu.
- Si \(p\) és primer i \(\operatorname{char}(R)=p\), aleshores \((a+b)^p=a^p+b^p\) i \((a+b)^{p^k}=a^{p^k}+b^{p^k}\).
- \((a^{-1})^{-1}=a\).
- \((ab)^{-1}=b^{-1}a^{-1}\); en un anell commutatiu, \((ab)^{-1}=a^{-1}b^{-1}\).
- \(R^\times\) és un grup amb el producte.
- \(0\notin R^\times\) si \(1\ne0\).
- En un cos, \(R^\times=R\setminus\{0\}\).

## 2. Divisibilitat a \(\mathbb Z\)

- **Definició:** \(a\mid b\iff \exists c\in\mathbb Z:\ b=ac\).
- \(a\mid a\).
- \(a\mid b\) i \(b\mid c\Rightarrow a\mid c\).
- \(a\mid b\) i \(a\mid c\Rightarrow a\mid(ub+vc)\) per a tots \(u,v\in\mathbb Z\).
- \(a\mid b\Rightarrow a\mid bc\) per a tot \(c\in\mathbb Z\).
- \(a\mid b\) i \(c\mid d\Rightarrow ac\mid bd\).
- \(a\mid b\Rightarrow ac\mid bc\).
- \(a\mid b\Rightarrow a^n\mid b^n\) per a tot \(n\ge1\).
- \(a^n\mid b^n\Rightarrow a\mid b\) per a tot \(n\ge1\).
- \(a\mid b\) i \(b\mid a\iff b=\pm a\).
- Si \(a\mid b\) i \(b\ne0\), aleshores \(|a|\le|b|\).
- \(\pm1\mid a\) per a tot \(a\in\mathbb Z\).
- \(a\mid0\) per a tot \(a\in\mathbb Z\).
- \(0\mid b\iff b=0\).
- \(a\mid b\iff |a|\mid|b|\).
- \(a\mid b\) i \(a\mid c\Rightarrow a\mid(b+c)\) i \(a\mid(b-c)\).
- Si \(a\) és senar, \(a\mid(b+c)\) i \(a\mid(b-c)\Rightarrow a\mid b\) i \(a\mid c\).
- **Lema d'Euclides general:** si \(a\mid bc\) i \(\operatorname{mcd}(a,b)=1\), aleshores \(a\mid c\).
- Si \(d=\operatorname{mcd}(a,b)\), aleshores \(d\mid(ua+vb)\) per a tots \(u,v\in\mathbb Z\).

## 3. Màxim comú divisor i mínim comú múltiple

- **Definició de mcd:** \(d=\operatorname{mcd}(a,b)\) si \(d\mid a\), \(d\mid b\) i tot divisor comú de \(a\) i \(b\) divideix \(d\).
- **Definició de mcm:** \(m=\operatorname{mcm}(a,b)\) si \(a\mid m\), \(b\mid m\) i \(m\) divideix tot múltiple comú de \(a\) i \(b\).
- \(\operatorname{mcd}(a,b)=\operatorname{mcd}(|a|,|b|)\).
- \(\operatorname{mcm}(a,b)=\operatorname{mcm}(|a|,|b|)\).
- \(\operatorname{mcd}(a,0)=|a|\) si \(a\ne0\).
- \(\operatorname{mcm}(a,0)=0\).
- \(\operatorname{mcd}(a,a)=|a|\), \(\operatorname{mcm}(a,a)=|a|\).
- \(\operatorname{mcd}(a,1)=1\).
- \(\operatorname{mcd}(a,b)=\operatorname{mcd}(b,a)\), \(\operatorname{mcm}(a,b)=\operatorname{mcm}(b,a)\).
- \(\operatorname{mcd}(a,b)=\operatorname{mcd}(a+kb,b)\) per a tot \(k\in\mathbb Z\).
- \(\operatorname{mcd}(ma,mb)=|m|\operatorname{mcd}(a,b)\).
- \(\operatorname{mcm}(ma,mb)=|m|\operatorname{mcm}(a,b)\) si \(m\ne0\).
- Si \(d=\operatorname{mcd}(a,b)\), aleshores \(\operatorname{mcd}(a/d,b/d)=1\).
- \(\operatorname{mcd}(a,b)\operatorname{mcm}(a,b)=|ab|\) si \(a,b\ne0\).
- \(\operatorname{mcm}(a,b)=\dfrac{|ab|}{\operatorname{mcd}(a,b)}\) si \(a,b\ne0\).
- Tot divisor comú de \(a\) i \(b\) divideix \(\operatorname{mcd}(a,b)\).
- \(\operatorname{mcm}(a,b)\) divideix tot múltiple comú de \(a\) i \(b\).
- \(\operatorname{mcd}(a,b,c)=\operatorname{mcd}(\operatorname{mcd}(a,b),c)\).
- \(\operatorname{mcm}(a,b,c)=\operatorname{mcm}(\operatorname{mcm}(a,b),c)\).
- Si \(a_1,\dots,a_n\) són coprimers dos a dos, aleshores \(\operatorname{mcm}(a_1,\dots,a_n)=a_1\cdots a_n\).
- \(\operatorname{mcd}(a,\operatorname{mcm}(b,c))=\operatorname{mcm}(\operatorname{mcd}(a,b),\operatorname{mcd}(a,c))\).
- \(\operatorname{mcm}(a,\operatorname{mcd}(b,c))=\operatorname{mcd}(\operatorname{mcm}(a,b),\operatorname{mcm}(a,c))\).
- Si \(a=\prod_p p^{r_p}\) i \(b=\prod_p p^{s_p}\), aleshores
  \[
  \operatorname{mcd}(a,b)=\prod_p p^{\min(r_p,s_p)},\qquad
  \operatorname{mcm}(a,b)=\prod_p p^{\max(r_p,s_p)}.
  \]

## 4. Divisió euclidiana, algorisme d'Euclides i Bézout

- **Divisió euclidiana:** per a \(a\in\mathbb Z\) i \(b>0\), existeixen únics \(q,r\in\mathbb Z\) amb \(a=bq+r\) i \(0\le r<b\).
- \(\operatorname{mcd}(a,b)=\operatorname{mcd}(b,a\bmod b)\) si \(b\ne0\).
- **Algorisme d'Euclides:** l'últim residu no nul de les divisions successives és \(\operatorname{mcd}(a,b)\).
- **Identitat de Bézout:** si \(d=\operatorname{mcd}(a,b)\), existeixen \(\alpha,\beta\in\mathbb Z\) amb \(d=\alpha a+\beta b\).
- \(\{ua+vb:u,v\in\mathbb Z\}=d\mathbb Z\), on \(d=\operatorname{mcd}(a,b)\).
- \(\operatorname{mcd}(a,b)\) és el menor enter positiu de la forma \(ua+vb\).
- \(\operatorname{mcd}(a,b)=1\iff \exists\alpha,\beta\in\mathbb Z:\ \alpha a+\beta b=1\).
- Si \(d=\alpha a+\beta b\), aleshores per a tot \(t\in\mathbb Z\),
  \[
  d=\left(\alpha+t\frac bd\right)a+\left(\beta-t\frac ad\right)b.
  \]
- Si \(\operatorname{mcd}(a,b)=1\) i \(1=\alpha a+\beta b\), aleshores \(\alpha'=\alpha+tb\), \(\beta'=\beta-ta\) també compleixen \(1=\alpha'a+\beta'b\).
- Si \(\operatorname{mcd}(a,m)=1\) i \(\alpha a+\beta m=1\), aleshores \(a^{-1}\equiv\alpha\pmod m\).
- El nombre de divisions de l'algorisme d'Euclides és \(O(\log(\min(|a|,|b|)))\).

## 5. Equacions diofàntiques lineals

- **Equació:** \(ax+by=c\), amb \(a,b,c\in\mathbb Z\) i \(x,y\in\mathbb Z\).
- \(ax+by=c\) té solució entera \(\iff \operatorname{mcd}(a,b)\mid c\).
- Si \((x_0,y_0)\) és una solució particular de \(ax+by=c\) i \(d=\operatorname{mcd}(a,b)\), aleshores totes les solucions són
  \[
  x=x_0+\frac bd t,\qquad y=y_0-\frac ad t,\qquad t\in\mathbb Z.
  \]
- Les solucions de \(ax+by=0\) són
  \[
  x=\frac bd t,\qquad y=-\frac ad t,\qquad t\in\mathbb Z.
  \]
- La solució general de \(ax+by=c\) és una solució particular més la solució general de l'equació homogènia \(ax+by=0\).

## 6. Nombres primers i factorització

- **Primer:** \(p>1\) amb únics divisors positius \(1\) i \(p\).
- \(p\) és primer \(\iff\) per a tots \(a,b\in\mathbb Z\), \(p\mid ab\Rightarrow p\mid a\) o \(p\mid b\).
- \(1\) no és primer.
- \(2\) és l'únic primer parell.
- **Lema d'Euclides:** si \(p\) és primer i \(p\mid ab\), aleshores \(p\mid a\) o \(p\mid b\).
- Si \(p\) és primer i \(p\mid a_1a_2\cdots a_n\), aleshores \(p\mid a_i\) per a algun \(i\).
- **Teorema fonamental de l'aritmètica:** tot \(n\ne0,\pm1\) s'escriu de manera única, llevat de l'ordre i el signe, com
  \[
  n=\pm p_1^{r_1}p_2^{r_2}\cdots p_k^{r_k},
  \]
  amb \(p_i\) primers positius diferents i \(r_i\ge1\).
- \(v_p(ab)=v_p(a)+v_p(b)\).
- \(v_p(a+b)\ge\min(v_p(a),v_p(b))\).
- Si \(v_p(a)\ne v_p(b)\), aleshores \(v_p(a+b)=\min(v_p(a),v_p(b))\).
- \(a\mid b\iff v_p(a)\le v_p(b)\) per a tot primer \(p\).
- \(\operatorname{mcd}(a,b)=\prod_p p^{\min(v_p(a),v_p(b))}\).
- \(\operatorname{mcm}(a,b)=\prod_p p^{\max(v_p(a),v_p(b))}\).
- \(a^2\mid b^2\Rightarrow a\mid b\).
- Hi ha infinits nombres primers.
- Si \(n>1\) no és divisible per cap primer \(p\le\sqrt n\), aleshores \(n\) és primer.
- **Criteris de divisibilitat:**
  - \(2\mid n\iff\) l'última xifra és parell.
  - \(3\mid n\iff\) la suma de les xifres és divisible per \(3\).
  - \(4\mid n\iff\) les dues últimes xifres formen un múltiple de \(4\).
  - \(5\mid n\iff\) l'última xifra és \(0\) o \(5\).
  - \(6\mid n\iff 2\mid n\) i \(3\mid n\).
  - \(8\mid n\iff\) les tres últimes xifres formen un múltiple de \(8\).
  - \(9\mid n\iff\) la suma de les xifres és divisible per \(9\).
  - \(10\mid n\iff\) l'última xifra és \(0\).
  - \(11\mid n\iff\) la suma alternada de les xifres és divisible per \(11\).
- Si \(M_q=2^q-1\) és primer, aleshores \(q\) és primer.
- Si \(q\) és primer i \(p\) és un primer que divideix \(2^q-1\), aleshores \(p\equiv1\pmod q\); si \(p,q\) són senars, \(p\equiv1\pmod{2q}\).
- Si \(p\) és primer senar i \(p=a^2+b^2\), aleshores \(p\equiv1\pmod4\).

## 7. Congruències

- **Definició:** \(a\equiv b\pmod m\iff m\mid(a-b)\iff \exists k\in\mathbb Z:\ a=b+km\iff a\bmod m=b\bmod m\).
- \(a\equiv b\pmod1\) per a tots \(a,b\in\mathbb Z\).
- **Reflexiva:** \(a\equiv a\pmod m\).
- **Simètrica:** \(a\equiv b\pmod m\Rightarrow b\equiv a\pmod m\).
- **Transitiva:** \(a\equiv b\pmod m\) i \(b\equiv c\pmod m\Rightarrow a\equiv c\pmod m\).
- **Suma:** \(a\equiv a_0\pmod m\) i \(b\equiv b_0\pmod m\Rightarrow a+b\equiv a_0+b_0\pmod m\).
- **Resta:** \(a\equiv a_0\pmod m\) i \(b\equiv b_0\pmod m\Rightarrow a-b\equiv a_0-b_0\pmod m\).
- **Producte:** \(a\equiv a_0\pmod m\) i \(b\equiv b_0\pmod m\Rightarrow ab\equiv a_0b_0\pmod m\).
- \(a\equiv b\pmod m\Rightarrow a^n\equiv b^n\pmod m\) per a tot \(n\ge0\).
- \(a\equiv b\pmod m\Rightarrow f(a)\equiv f(b)\pmod m\) per a tot \(f\in\mathbb Z[x]\).
- \(a\equiv b\pmod m\Rightarrow ac\equiv bc\pmod m\).
- \(ac\equiv bc\pmod m\iff a\equiv b\pmod{\dfrac{m}{\operatorname{mcd}(c,m)}}\).
- Si \(\operatorname{mcd}(c,m)=1\), aleshores \(ac\equiv bc\pmod m\Rightarrow a\equiv b\pmod m\).
- Si \(d\mid m\), aleshores \(a\equiv b\pmod m\Rightarrow a\equiv b\pmod d\).
- \(a\equiv b\pmod m\) i \(a\equiv b\pmod n\iff a\equiv b\pmod{\operatorname{mcm}(m,n)}\).
- Si \(\operatorname{mcd}(m,n)=1\), aleshores \(a\equiv b\pmod m\) i \(a\equiv b\pmod n\iff a\equiv b\pmod{mn}\).
- \(a\equiv b\pmod m\Rightarrow \operatorname{mcd}(a,m)=\operatorname{mcd}(b,m)\).
- **Equació lineal:** \(ax\equiv b\pmod m\) té solució \(\iff d=\operatorname{mcd}(a,m)\mid b\).
- Si \(d=\operatorname{mcd}(a,m)\mid b\), aleshores
  \[
  x\equiv x_0\pmod{\frac md},\qquad
  x_0\equiv\left(\frac ad\right)^{-1}\frac bd\pmod{\frac md}.
  \]
- Si \(d=\operatorname{mcd}(a,m)\mid b\), hi ha exactament \(d\) solucions mòdul \(m\):
  \[
  x=x_0+k\frac md,\qquad k=0,1,\dots,d-1.
  \]
- \(ax\equiv1\pmod m\) té solució \(\iff \operatorname{mcd}(a,m)=1\).
- **Classe de residus:** \([a]_m=\{b\in\mathbb Z:a\equiv b\pmod m\}=a+m\mathbb Z\).
- \([a]_m=[b]_m\iff a\equiv b\pmod m\).
- \(\mathbb Z=\bigsqcup_{r=0}^{m-1}[r]_m\).
- \(|\mathbb Z/m\mathbb Z|=m\).
- \([a]_{km}\subseteq[a]_m\) per a tot \(k\ge1\).
- \([a]_m\cap[b]_n\ne\varnothing\iff a\equiv b\pmod{\operatorname{mcd}(m,n)}\).
- Si \([a]_m\cap[b]_n\ne\varnothing\), aleshores \([a]_m\cap[b]_n=[c]_{\operatorname{mcm}(m,n)}\) per a qualsevol \(c\in[a]_m\cap[b]_n\).

## 8. Anell \(\mathbb Z/m\mathbb Z\)

- \([a]_m+[b]_m=[a+b]_m\), \([a]_m[b]_m=[ab]_m\).
- Les operacions de suma i producte estan ben definides.
- \(\mathbb Z/m\mathbb Z\) és un anell commutatiu amb unitat.
- \(\operatorname{char}(\mathbb Z/m\mathbb Z)=m\).
- \([a]_m\) és invertible \(\iff \operatorname{mcd}(a,m)=1\).
- El nombre d'elements invertibles de \(\mathbb Z/m\mathbb Z\) és \(\varphi(m)\).
- \(\mathbb Z/m\mathbb Z\) és un cos \(\iff m\) és primer.
- \(\mathbb Z/m\mathbb Z\) és un domini \(\iff m\) és primer.
- Si \(m>1\) i \([a]_m\ne[0]_m\) no és invertible, aleshores \([a]_m\) és un divisor de zero.
- La cancel·lació per \([a]_m\) és vàlida \(\iff \operatorname{mcd}(a,m)=1\).
- Si \(m=1\), \(\mathbb Z/1\mathbb Z\) és l'anell zero i no és un cos.
- Si \(m=p_1^{e_1}\cdots p_r^{e_r}\) amb \(p_i\) primers diferents, aleshores
  \[
  \mathbb Z/m\mathbb Z\cong \mathbb Z/p_1^{e_1}\mathbb Z\times\cdots\times\mathbb Z/p_r^{e_r}\mathbb Z.
  \]
- A \(\mathbb Z/p^e\mathbb Z\), \([p]^e=[0]\).

## 9. Teorema xinès del residu

- \(x\equiv a\pmod m\) i \(x\equiv b\pmod n\) tenen solució \(\iff a\equiv b\pmod{\operatorname{mcd}(m,n)}\).
- Si el sistema anterior té solució, aquesta és única mòdul \(\operatorname{mcm}(m,n)\).
- \(x\equiv a_i\pmod{m_i}\), \(i=1,\dots,r\), té solució \(\iff a_i\equiv a_j\pmod{\operatorname{mcd}(m_i,m_j)}\) per a tots \(i,j\).
- Si el sistema anterior té solució, aquesta és única mòdul \(\operatorname{mcm}(m_1,\dots,m_r)\).
- Si \(\operatorname{mcd}(m_i,m_j)=1\) per a \(i\ne j\), aleshores el sistema té solució única mòdul \(m_1m_2\cdots m_r\).
- **Fórmula directa:** si \(M=m_1\cdots m_r\), \(M_i=M/m_i\) i \(y_iM_i\equiv1\pmod{m_i}\), aleshores
  \[
  x\equiv\sum_{i=1}^r a_iM_iy_i\pmod M.
  \]
- Si \(\operatorname{mcd}(m_i,m_j)=1\) per a \(i\ne j\), aleshores
  \[
  \mathbb Z/(m_1\cdots m_r)\mathbb Z\cong
  \mathbb Z/m_1\mathbb Z\times\cdots\times\mathbb Z/m_r\mathbb Z.
  \]

## 10. Fermat, Euler i ordre

- **Funció \(\varphi\):** \(\varphi(n)=|\{1\le k\le n:\operatorname{mcd}(k,n)=1\}|\).
- \(\varphi(1)=1\).
- \(\varphi(p)=p-1\) si \(p\) és primer.
- \(\varphi(p^e)=p^e-p^{e-1}=p^{e-1}(p-1)\) si \(p\) és primer i \(e\ge1\).
- \(\varphi(mn)=\varphi(m)\varphi(n)\) si \(\operatorname{mcd}(m,n)=1\).
- \(\varphi(n)=n\prod_{p\mid n}\left(1-\dfrac1p\right)\).
- \(\varphi(n)\) és parell per a \(n>2\).
- \(\sum_{d\mid n}\varphi(d)=n\).
- **Petit teorema de Fermat:** si \(p\) és primer i \(p\nmid a\), aleshores \(a^{p-1}\equiv1\pmod p\).
- Si \(p\) és primer, aleshores \(a^p\equiv a\pmod p\) per a tot \(a\in\mathbb Z\).
- **Teorema d'Euler:** si \(\operatorname{mcd}(a,m)=1\), aleshores \(a^{\varphi(m)}\equiv1\pmod m\).
- **Ordre:** \(\operatorname{ord}_m(a)\) és el menor \(k>0\) amb \(a^k\equiv1\pmod m\), si \(\operatorname{mcd}(a,m)=1\).
- \(\operatorname{ord}_m(a)\mid\varphi(m)\) si \(\operatorname{mcd}(a,m)=1\).
- Si \(\operatorname{mcd}(a,m)=1\), aleshores
  \[
  a^r\equiv a^s\pmod m\iff r\equiv s\pmod{\operatorname{ord}_m(a)}.
  \]
- Si \(\operatorname{mcd}(a,m)=1\) i \(r\equiv s\pmod{\varphi(m)}\), aleshores \(a^r\equiv a^s\pmod m\).
- Si \(p\) és primer i \(p\nmid a\), aleshores \(a^{-1}\equiv a^{p-2}\pmod p\).
- Si \(\operatorname{mcd}(a,m)=1\), aleshores \(a^{-1}\equiv a^{\varphi(m)-1}\pmod m\).

## 11. Matrius mòdul \(m\)

- \(M_n(\mathbb Z/m\mathbb Z)\) és l'anell de matrius \(n\times n\) amb entrades mòdul \(m\).
- \(GL_n(\mathbb Z/m\mathbb Z)=\{A\in M_n(\mathbb Z/m\mathbb Z):\det A\in(\mathbb Z/m\mathbb Z)^\times\}\).
- \(\det I_n=1\).
- \(\det(AB)=\det A\det B\).
- \(\det(A^T)=\det A\).
- \(\det(cA)=c^n\det A\).
- Si \(A\) és triangular, \(\det A=\prod_i a_{ii}\).
- El determinant és multilineal en cada fila o columna.
- Si es permuten dues files, el determinant canvia de signe.
- Si dues files o columnes coincideixen, \(\det A=0\).
- Si una fila o columna és zero, \(\det A=0\).
- Sumar a una fila un múltiple d'una altra no canvia el determinant.
- Multiplicar una fila per \(c\) multiplica el determinant per \(c\).
- Es pot desenvolupar el determinant per qualsevol fila o columna.
- \(A\operatorname{adj}(A)=\operatorname{adj}(A)A=\det(A)I_n\).
- Si \(\det A\) és una unitat, aleshores
  \[
  A^{-1}=(\det A)^{-1}\operatorname{adj}(A).
  \]
- Per a \(A=\begin{pmatrix}a&b\\c&d\end{pmatrix}\) amb \(\det A=ad-bc\) unitat,
  \[
  A^{-1}=(\det A)^{-1}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}.
  \]
- \(A\) és invertible \(\iff \det A\) és una unitat \(\iff \operatorname{mcd}(\det A,m)=1\).
- Si \(m=p\) és primer, \(A\) és invertible \(\iff \det A\ne0\) en \(\mathbb F_p\).
- **Sistemes sobre un cos \(\mathbb F_p\):** \(A\mathbf x=\mathbf b\) és compatible \(\iff \operatorname{rang}(A)=\operatorname{rang}(A\mid\mathbf b)\).
- Si \(A\mathbf x=\mathbf b\) és compatible i \(\operatorname{rang}(A)=n\), la solució és única.
- Si \(A\mathbf x=\mathbf b\) és compatible i \(\operatorname{rang}(A)=r<n\), hi ha \(p^{n-r}\) solucions.
- Si \(A\) és quadrada i \(\det A\ne0\), aleshores \(\mathbf x=A^{-1}\mathbf b\) és l'única solució.
- **Regla de Cramer:** si \(\det A\ne0\), aleshores
  \[
  x_i=\frac{\det A_i}{\det A},
  \]
  on \(A_i\) és la matriu que resulta de substituir la columna \(i\) de \(A\) per \(\mathbf b\).
- Si \(\det A\) és una unitat mòdul \(m\), el sistema \(A\mathbf x=\mathbf b\) té solució única \(\mathbf x=A^{-1}\mathbf b\).
- Si \(\det A\) no és una unitat mòdul \(m\), el sistema pot tenir cap, una o diverses solucions.
- Per resoldre un sistema mòdul \(m\) compost: es resol mòdul cada \(p_i^{e_i}\) i es combinen les solucions amb el teorema xinès del residu.
