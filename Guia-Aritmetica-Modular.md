# Guia d'estudi — Modular Arithmetic Tools

**Curs:** *Seguretat i Secret en la Codificació de la Informació* (EPSEM), curs 26–27–Q1  
**Tema:** Aritmètica modular, divisibilitat, congruències, CRT, Fermat/Euler i matrius mòdul $m$

> Aquesta guia recull la teoria, les demostracions principals, els algorismes i les estratègies de resolució necessàries per afrontar qualsevol exercici del tema. Les referències del tipus **exercici 1.3** remeten al full `Prob-Aritmetica.md`; les solucions desenvolupades són a `Sol-Aritmetica.md`.

**Notes sobre els enunciats.** En aquesta guia s'usen les versions matemàticament correctes d'alguns enunciats que tenen errates conegudes al full de problemes:

- **Exercici 1.11:** la hipòtesi correcta és $\operatorname{mcd}(a,b)=1$, no $\operatorname{mcd}(m,n)=1$.
- **Exercici 1.18:** cal llegir *primer senar*. El primer $2=1^2+1^2$ és l'excepció, i $2\equiv 2\pmod 4$.
- **Exercici 1.38 (u) i (v):** tal com estan escrits són falsos; a la secció 15 s'indiquen les versions correctes.

***

## Taula de continguts

1. [Introducció i notació](#sec1)
2. [Anells i cossos](#sec2)
3. [Divisibilitat a $\mathbb Z$](#sec3)
4. [Màxim comú divisor i mínim comú múltiple](#sec4)
5. [Algorisme d'Euclides i identitat de Bézout](#sec5)
6. [Equacions diofàntiques lineals](#sec6)
7. [Nombres primers i factorització](#sec7)
8. [Congruències i aritmètica modular](#sec8)
9. [L'anell $\mathbb Z/m\mathbb Z$](#sec9)
10. [Teorema xinès del residu](#sec10)
11. [Teoremes de Fermat i Euler](#sec11)
12. [Matrius mòdul $m$](#sec12)
13. [Consells i estratègies de resolució](#sec13)
14. [Resum de fórmules i propietats clau](#sec14)
15. [Exemples il·lustratius i connexions amb els exercicis](#sec15)
16. [Apèndix: taula ràpida de resultats](#sec16)

***

<a id="sec1"></a>
## 1. Introducció i notació

### 1.1 Conjunts i estructures bàsiques

| Símbol | Significat |
|---|---|
| $\mathbb N$ | Nombres naturals. En aquest curs, habitualment $\{0,1,2,\dots\}$; sovint ens interessen els positius. |
| $\mathbb Z$ | Nombres enters: $\{\dots,-2,-1,0,1,2,\dots\}$. |
| $\mathbb Q$ | Nombres racionals. |
| $\mathbb R$ | Nombres reals. |
| $\mathbb C$ | Nombres complexos. |
| $\mathbb Z/m\mathbb Z$ | Anell de les classes de residus mòdul $m$. També s'escriu $\mathbb Z_m$. |
| $\mathbb F_p$ | Cos finit $\mathbb Z/p\mathbb Z$, amb $p$ primer. |
| $M_n(R)$ | Matrius $n\times n$ amb entrades a l'anell $R$. |
| $GL_n(R)$ | Matrius invertibles $n\times n$ sobre $R$. |

### 1.2 Notació aritmètica

| Notació | Significat |
|---|---|
| $a\mid b$ | $a$ divideix $b$: existeix $c\in\mathbb Z$ amb $b=ac$. |
| $a\nmid b$ | $a$ no divideix $b$. |
| $\operatorname{mcd}(a,b)$ | Màxim comú divisor de $a$ i $b$. Sinònim: $\gcd(a,b)$. |
| $\operatorname{mcm}(a,b)$ | Mínim comú múltiple de $a$ i $b$. Sinònim: $\operatorname{lcm}(a,b)$. |
| $a\equiv b\pmod m$ | $a-b$ és múltiple de $m$; $a$ i $b$ tenen el mateix residu mòdul $m$. |
| $[a]_m$, $\overline a$ | Classe de residus de $a$ mòdul $m$: $[a]_m=a+m\mathbb Z$. |
| $\varphi(n)$ | Funció phi d'Euler: nombre d'enters $1\le k\le n$ amb $\operatorname{mcd}(k,n)=1$. |
| $U(m)$ | Grup d'unitats de $\mathbb Z/m\mathbb Z$; $|U(m)|=\varphi(m)$. |
| $R^\times$ | Grup d'unitats de l'anell $R$. |
| $\det A$ | Determinant de la matriu quadrada $A$. |
| $\operatorname{adj}A$ | Matriu adjunta de $A$. |
| $v_p(n)$ | Exponent de $p$ a la factorització de $n$; $v_p(0)=+\infty$ per conveni. |
| $\operatorname{ord}_m(a)$ | Ordre multiplicatiu de $a$ mòdul $m$: el menor $k>0$ amb $a^k\equiv1\pmod m$. |
| $a^{-1}\bmod m$ | Invers modular de $a$ mòdul $m$, si existeix. |

### 1.3 Convencions i casos límit

- Treballarem sempre amb **mòduls positius** $m>0$. Si apareix un mòdul negatiu, es treballa amb $|m|$.
- El **mcd** es pren **positiu**: $\operatorname{mcd}(a,b)\ge0$. Per conveni, $\operatorname{mcd}(0,0)$ no es defineix (o es pren $0$ en alguns contexts); en aquest curs evitarem aquest cas.
- El **mcm** de dos nombres no nuls es pren **positiu**. Si un dels dos és $0$, sovint es pren $\operatorname{mcm}(a,0)=0$.
- $\operatorname{mcd}(a,b)=\operatorname{mcd}(|a|,|b|)$.
- El residu mòdul $m$ que usarem normalment és el **residu no negatiu** $0\le r<m$.
- $a\bmod m$ denota aquest residu.
- Per a $m=1$, hi ha una sola classe de residus i $\mathbb Z/1\mathbb Z$ és l'anell zero; no és un cos.
- En un anell, **unitat** vol dir element invertible. No s'ha de confondre amb l'element neutre del producte, que també es diu *u* o *1*.

### 1.4 Full de ruta del tema

El fil conductor és:

$$
\text{divisibilitat}
\;\longrightarrow\;
\operatorname{mcd}/\operatorname{mcm}
\;\longrightarrow\;
\text{Bézout}
\;\longrightarrow\;
\text{congruències}
\;\longrightarrow\;
\mathbb Z/m\mathbb Z
\;\longrightarrow\;
\text{CRT, Fermat/Euler, matrius}.
$$

Les eines clau que cal dominar són:

1. **Algorisme d'Euclides** per calcular mcd i inversos.
2. **Identitat de Bézout** per resoldre equacions diofàntiques i trobar inversos modulars.
3. **Factorització en primers** per calcular mcd, mcm i $\varphi(n)$.
4. **Teorema xinès del residu** per descompondre problemes mòdul $m$ en problemes més petits.
5. **Fermat/Euler i exponenciació ràpida** per calcular potències grans.
6. **Determinant i adjunta** per invertir matrius i resoldre sistemes lineals mòdul $m$.

***

<a id="sec2"></a>
## 2. Anells i cossos

### 2.1 Definició d'anell

Un **anell** és un conjunt $R$ amb dues operacions, suma $+$ i producte $\cdot$, que compleixen:

1. $(R,+)$ és un **grup abelià**:
   - suma associativa: $(a+b)+c=a+(b+c)$;
   - suma commutativa: $a+b=b+a$;
   - element neutre $0$: $a+0=a$;
   - oposat: per a cada $a$ existeix $-a$ amb $a+(-a)=0$.
2. El producte és **associatiu**: $(ab)c=a(bc)$.
3. El producte és **distributiu** respecte de la suma:
   $$
   a(b+c)=ab+ac,\qquad (a+b)c=ac+bc.
   $$

No es demana que el producte sigui commutatiu ni que existeixi element neutre del producte.

### 2.2 Anell commutatiu, anell amb unitat, domini i cos

| Concepte | Definició |
|---|---|
| **Anell commutatiu** | Anell on $ab=ba$ per a tots $a,b$. |
| **Anell amb unitat** | Anell on existeix $1\ne0$ amb $1a=a1=a$ per a tot $a$. |
| **Domini d'integritat** | Anell commutatiu amb unitat, $1\ne0$, sense divisors de zero. |
| **Cos** | Anell commutatiu amb unitat, $1\ne0$, on tot element no nul és invertible. |
| **Divisor de zero** | Element $a\ne0$ tal que existeix $b\ne0$ amb $ab=0$ (o $ba=0$ en anells no commutatius). |
| **Unitat** | Element $a$ tal que existeix $b$ amb $ab=ba=1$. S'escriu $b=a^{-1}$. |

> **Conveni:** en aquesta guia, "anell" inclou la unitat llevat que es digui el contrari; "cos" sempre és commutatiu.

### 2.3 Exemples fonamentals

| Anell | Commutatiu? | Unitat? | Domini? | Cos? | Unitats |
|---|---|---|---|---|---|
| $\mathbb Z$ | Sí | Sí | Sí | No | $\{\pm1\}$ |
| $\mathbb Q$ | Sí | Sí | Sí | Sí | $\mathbb Q\setminus\{0\}$ |
| $\mathbb R$ | Sí | Sí | Sí | Sí | $\mathbb R\setminus\{0\}$ |
| $\mathbb C$ | Sí | Sí | Sí | Sí | $\mathbb C\setminus\{0\}$ |
| $M_n(\mathbb Z)$ | No, si $n\ge2$ | Sí, $I_n$ | No | No | $\det A=\pm1$ |
| $M_n(\mathbb Q)$ | No, si $n\ge2$ | Sí, $I_n$ | No | No | $\det A\ne0$ |
| $\mathbb Z/m\mathbb Z$ | Sí | Sí | Només si $m$ és primer | Només si $m$ és primer | $\operatorname{mcd}(a,m)=1$ |

**Exemples de divisors de zero.**

- A $M_2(\mathbb Z)$:
  $$
  A=\begin{pmatrix}1&0\\0&0\end{pmatrix},\qquad
  B=\begin{pmatrix}0&0\\1&0\end{pmatrix},\qquad
  AB=\begin{pmatrix}0&0\\0&0\end{pmatrix},
  $$
  amb $A\ne0$ i $B\ne0$.
- A $\mathbb Z/6\mathbb Z$: $[2][3]=[6]=[0]$, amb $[2]\ne[0]$ i $[3]\ne[0]$.

**Exemple de no commutativitat.** A $M_2(\mathbb Z)$,
$$
\begin{pmatrix}1&1\\0&0\end{pmatrix}
\begin{pmatrix}1&0\\0&1\end{pmatrix}
\ne
\begin{pmatrix}1&0\\0&1\end{pmatrix}
\begin{pmatrix}1&1\\0&0\end{pmatrix}
$$
en general; de fet, les matrius no commuten llevat de casos especials.

### 2.4 Propietats bàsiques

Sigui $R$ un anell i $a,b,c\in R$.

1. **El neutre és únic.** Si $0$ i $0'$ són neutres de la suma, $0=0+0'=0'$.
2. **L'oposat és únic.** Si $b$ i $b'$ són oposats de $a$, llavors $b=b+0=b+(a+b')=(b+a)+b'=0+b'=b'$.
3. **El producte per zero s'anul·la:**
   $$
   a0=0a=0.
   $$
   *Demostració:* $a0=a(0+0)=a0+a0$; restant $a0$ als dos costats, $0=a0$.
4. **Signes:**
   $$
   (-a)b=-(ab),\qquad a(-b)=-(ab),\qquad (-a)(-b)=ab.
   $$
5. **Distributivitat generalitzada:**
   $$
   a(b-c)=ab-ac,\qquad (a-b)c=ac-bc.
   $$
6. **Cancel·lació per unitats:** si $a$ és invertible i $ab=ac$, llavors $b=c$. Multiplicant per $a^{-1}$.
7. **En un domini**, es pot cancel·lar qualsevol element no nul: si $a\ne0$ i $ab=ac$, llavors $a(b-c)=0$, i com que no hi ha divisors de zero, $b=c$.
8. **Binomi de Newton** en un anell commutatiu:
   $$
   (a+b)^n=\sum_{k=0}^n\binom nk a^k b^{n-k}.
   $$
9. **Fet de característica $p$:** si $p$ és primer i $R$ és commutatiu amb $p\cdot1=0$, llavors
   $$
   (a+b)^p=a^p+b^p,
   $$
   perquè els coeficients binomials $\binom pk$ són divisibles per $p$ per a $1\le k\le p-1$. Aquest fet s'usa en algunes demostracions del teorema de Fermat.

### 2.5 Unitats i inversos

Un element $a\in R$ és una **unitat** si existeix $b\in R$ amb
$$
ab=ba=1.
$$
L'element $b$ és únic i s'escriu $a^{-1}$.

Propietats:

- $(a^{-1})^{-1}=a$.
- Si $a$ i $b$ són unitats, llavors $ab$ és unitat i
  $$
  (ab)^{-1}=b^{-1}a^{-1}.
  $$
  En un anell commutatiu, $(ab)^{-1}=a^{-1}b^{-1}$.
- El conjunt de les unitats $R^\times$ forma un grup amb el producte.
- $0$ no és unitat si $1\ne0$.
- En un cos, $R^\times=R\setminus\{0\}$.

**Exemples.**

- A $\mathbb Z$, les unitats són $\pm1$.
- A $\mathbb Q,\mathbb R,\mathbb C$, tot element no nul és unitat.
- A $M_n(\mathbb Q)$, les unitats són les matrius amb determinant no nul.
- A $M_n(\mathbb Z)$, les unitats són les matrius amb determinant $\pm1$.
- A $\mathbb Z/m\mathbb Z$, $[a]$ és unitat si i només si $\operatorname{mcd}(a,m)=1$ (ho demostrarem a la secció 9).

### 2.6 Per què ens interessa l'estructura d'anell?

Perquè $\mathbb Z/m\mathbb Z$ no és només un conjunt de residus: té suma i producte compatibles amb la congruència. Això permet:

- sumar, restar i multiplicar classes;
- parlar d'elements invertibles i de divisors de zero;
- resoldre equacions i sistemes;
- aplicar eines algebraiques (grups d'unitats, cossos, matrius).

El fet central és:

$$
\mathbb Z/m\mathbb Z \text{ és un cos} \iff m \text{ és primer}.
$$

Aquesta és la raó per la qual, quan $m$ és primer, l'àlgebra lineal mòdul $m$ funciona igual que sobre $\mathbb R$ o $\mathbb Q$; quan $m$ no és primer, apareixen complicacions.

### 2.7 Connexions amb els exercicis

- **Exercici 1.38 (a):** $M_2(\mathbb Z)$ té divisors de zero; per tant, no és un domini.
- **Exercici 1.38 (b):** en $M_2(\mathbb Q)$ no es pot cancel·lar una matriu no invertible; $AB=AC$ no implica $B=C$.
- **Exercici 1.38 (c):** en qualsevol anell, $0=-0$; a $\mathbb Z/2\mathbb Z$ també $1=-1$.
- **Exercici 1.38 (d):** en anells no commutatius, $(ab)^{-1}=b^{-1}a^{-1}$, no $a^{-1}b^{-1}$.
- **Exercici 1.38 (e):** hi ha anells amb $a^2=b^2=1$ però $(ab)^2\ne1$; per exemple, matrius de reflexió.

***
<a id="sec3"></a>
## 3. Divisibilitat a $\mathbb Z$

### 3.1 Definició

Siguin $a,b\in\mathbb Z$. Diem que **$a$ divideix $b$**, i escrivim $a\mid b$, si existeix $c\in\mathbb Z$ tal que
$$
b=ac.
$$
Equivalentment: $b$ és múltiple de $a$; $b$ és divisible per $a$; la divisió de $b$ per $a$ té residu zero.

**Exemples.**

- $2\mid6$ perquè $6=2\cdot3$.
- $2\nmid5$ perquè no existeix cap enter $c$ amb $5=2c$.
- $7\mid0$ perquè $0=7\cdot0$.
- $0\mid0$ perquè $0=0\cdot c$ per a qualsevol $c$; per conveni, però, sovint es prefereix dir que $0$ no és divisor de res o tractar aquest cas a part.
- $0\nmid b$ si $b\ne0$.

### 3.2 Propietats

| Propietat | Enunciat | Idea de demostració |
|---|---|---|
| **Reflexivitat** | $a\mid a$ | $a=a\cdot1$. |
| **Transitivitat** | $a\mid b$ i $b\mid c$ $\Rightarrow$ $a\mid c$ | $b=ak$, $c=bm$ $\Rightarrow$ $c=a(km)$. |
| **Linealitat** | $a\mid b$ i $a\mid c$ $\Rightarrow$ $a\mid (ub+vc)$ per a tots $u,v\in\mathbb Z$ | $b=ak$, $c=am$ $\Rightarrow$ $ub+vc=a(uk+vm)$. |
| **Factor comú** | $a\mid b$ $\Rightarrow$ $a\mid bc$ per a tot $c$ | $b=ak$ $\Rightarrow$ $bc=a(kc)$. |
| **Producte** | $a\mid b$ i $c\mid d$ $\Rightarrow$ $ac\mid bd$ | $b=ak$, $d=cm$ $\Rightarrow$ $bd=ac(km)$. |
| **Antisimetria (llevat de signe)** | $a\mid b$ i $b\mid a$ $\Rightarrow$ $a=\pm b$ | Si $a,b\ne0$, $b=ak$, $a=bm$ $\Rightarrow$ $1=km$, així que $k=\pm1$. |
| **Mida** | Si $a\mid b$ i $b\ne0$, llavors $|a|\le|b|$ | $|b|=|a||c|$ amb $|c|\ge1$. |
| **Associats** | $a\mid b$ i $b\mid a$ $\iff$ $b=\pm a$ | Conseqüència de l'antisimetria. |
| **Unitats** | $\pm1$ divideixen qualsevol enter | $b=(\pm1)(\pm b)$. |

**Demostració de la linealitat.** Si $a\mid b$ i $a\mid c$, existeixen $k,m\in\mathbb Z$ amb $b=ak$ i $c=am$. Aleshores, per a qualsevol $u,v\in\mathbb Z$,
$$
ub+vc=u(ak)+v(am)=a(uk+vm),
$$
i $uk+vm\in\mathbb Z$. Per tant, $a\mid ub+vc$.

**Demostració de l'antisimetria.** Si $a\mid b$ i $b\mid a$, existeixen $k,m$ amb $b=ak$ i $a=bm$. Substituint,
$$
a=(ak)m=a(km).
$$
Si $a\ne0$, llavors $1=km$. Com que $k,m\in\mathbb Z$, això obliga $k=m=\pm1$, d'on $b=\pm a$. Si $a=0$, llavors $a\mid b$ implica $b=0$, i també $a=\pm b=0$.

### 3.3 El contraexemple fonamental: $a\mid bc$ no implica $a\mid b$ ni $a\mid c$

En general,
$$
a\mid bc \;\not\Rightarrow\; a\mid b \ \text{o}\ a\mid c.
$$
**Contraexemple:**
$$
6\mid 2\cdot3=6,
\qquad\text{però}\qquad
6\nmid2 \quad\text{i}\quad 6\nmid3.
$$
La raó és que $6$ pot "repartir" els seus factors entre $2$ i $3$: un $2$ i un $3$ per separat, sense que cap dels dos contingui tot el $6$.

Aquesta és una de les trampes més freqüents. La situació canvia si $a$ i $b$ són coprimers:

> **Lema d'Euclides (cas general).** Si $a\mid bc$ i $\operatorname{mcd}(a,b)=1$, aleshores $a\mid c$.

**Demostració.** Com que $\operatorname{mcd}(a,b)=1$, per Bézout existeixen $\alpha,\beta\in\mathbb Z$ amb
$$
\alpha a+\beta b=1.
$$
Multiplicant per $c$:
$$
\alpha ac+\beta bc=c.
$$
Ara bé, $a\mid\alpha ac$ i, com que $a\mid bc$, també $a\mid\beta bc$. Per linealitat, $a\mid c$. $\blacksquare$

Aquest lema és la base de la unicitat de la factorització en primers i de la resolució de congruències.

### 3.4 Divisibilitat i combinacions lineals

Si $d=\operatorname{mcd}(a,b)$, llavors $d$ divideix qualsevol combinació lineal de $a$ i $b$:
$$
d\mid (ua+vb)\qquad\text{per a tots }u,v\in\mathbb Z.
$$
Recíprocament, el conjunt de les combinacions lineals de $a$ i $b$ és exactament el conjunt dels múltiples de $d$:
$$
\{ua+vb:u,v\in\mathbb Z\}=d\mathbb Z.
$$
Això és una conseqüència de Bézout i de la linealitat.

**Aplicació típica.** Per demostrar que $\operatorname{mcd}(A(n),B(n))=1$ per a tot $n$, de vegades n'hi ha prou de trobar una combinació lineal de $A(n)$ i $B(n)$ que sigui una constant $\pm1$:
$$
uA(n)+vB(n)=\pm1.
$$
Aleshores qualsevol divisor comú de $A(n)$ i $B(n)$ divideix $\pm1$, i per tant el mcd és $1$.

**Exemple (exercici 1.7).** Per a $A(n)=4n+5$ i $B(n)=2n+3$,
$$
1\cdot(4n+5)-2\cdot(2n+3)=4n+5-4n-6=-1.
$$
Per tant, $\operatorname{mcd}(4n+5,2n+3)\mid1$, i com que és positiu, és $1$. La fracció $\frac{4n+5}{2n+3}$ és irreductible per a tot $n\ge1$.

**Exemple (exercici 1.4).** Per a $A(n)=28n-5$ i $B(n)=35n-8$,
$$
5A(n)-4B(n)=5(28n-5)-4(35n-8)=140n-25-140n+32=7.
$$
Així, el mcd divideix $7$, de manera que només pot ser $1$ o $7$. Però
$$
28n-5\equiv -5\equiv2\pmod7,
$$
així que $7\nmid28n-5$. Per tant, el mcd no pot ser $7$ i és $1$.

### 3.5 Altres propietats útils

1. **Divisibilitat i suma/resta:**
   $$
   a\mid b \text{ i } a\mid c \iff a\mid (b+c) \text{ i } a\mid (b-c).
   $$
   La implicació $\Leftarrow$ surt de sumar i restar les dues divisibilitats:
   $$
   (b+c)+(b-c)=2b,\qquad (b+c)-(b-c)=2c.
   $$
   Si $a$ és **senar**, llavors $\operatorname{mcd}(a,2)=1$, i pel lema d'Euclides $a\mid b$ i $a\mid c$. Aquest és l'exercici 1.38 (h). Sense la condició "senar", és fals: $a=4$, $b=c=2$ dóna $4\mid4$ i $4\mid0$, però $4\nmid2$ (exercici 1.38 (g)).
2. **Divisibilitat i producte:**
   $$
   a\mid b \Rightarrow ac\mid bc.
   $$
3. **Divisibilitat i potències:**
   $$
   a\mid b \Rightarrow a^n\mid b^n.
   $$
   El recíproc també és cert: $a^n\mid b^n\Rightarrow a\mid b$ (exercici 1.12).
4. **Divisibilitat per descomposició:**
   Si $a=bc$ i $\operatorname{mcd}(b,c)=1$, llavors $b\mid a$ i $c\mid a$; però no es pot concloure res del tipus $b\mid c$ o $c\mid b$.
5. **Divisibilitat i valor absolut:**
   $$
   a\mid b \iff |a|\mid|b|.
   $$

### 3.6 Errors freqüents

- **Confondre $a\mid b$ amb $b\mid a$.** La divisibilitat no és simètrica.
- **Cancel·lar un factor sense invertibilitat.** A $\mathbb Z$ es pot cancel·lar un factor no nul perquè $\mathbb Z$ és un domini; però en $\mathbb Z/m\mathbb Z$ només es pot cancel·lar si el factor és invertible.
- **Concloure $a\mid b$ o $a\mid c$ de $a\mid bc$.** Cal la hipòtesi $\operatorname{mcd}(a,b)=1$ (o $\operatorname{mcd}(a,c)=1$).
- **Oblidar el signe.** Els divisors poden ser negatius; el mcd es pren positiu.
- **Tractar $0$ com un divisor qualsevol.** $0\mid b$ només si $b=0$.

***

<a id="sec4"></a>
## 4. Màxim comú divisor i mínim comú múltiple

### 4.1 Definició de màxim comú divisor

Siguin $a,b\in\mathbb Z$, no tots dos zero. El **màxim comú divisor** de $a$ i $b$, $\operatorname{mcd}(a,b)$, és l'enter positiu $d$ que compleix:

1. $d\mid a$ i $d\mid b$;
2. si $c\mid a$ i $c\mid b$ per a algun $c\in\mathbb Z$, llavors $c\mid d$.

La condició 2 diu que $d$ és el **més gran** en l'ordre de la divisibilitat: qualsevol altre divisor comú divideix $d$. Això és més fort que dir simplement que $d$ és el més gran en valor absolut.

**Unicitat.** Si $d$ i $d'$ compleixen les dues condicions, llavors $d\mid d'$ i $d'\mid d$; com que tots dos són positius, $d=d'$.

**Conveni.** $\operatorname{mcd}(a,b)=\operatorname{mcd}(|a|,|b|)$. Si $a=b=0$, el mcd no està definit (tot enter els divideix).

**Exemples.**

- $\operatorname{mcd}(12,18)=6$.
- $\operatorname{mcd}(240,46)=2$.
- $\operatorname{mcd}(a,0)=|a|$ si $a\ne0$.
- $\operatorname{mcd}(a,1)=1$.
- $\operatorname{mcd}(a,a)=|a|$.

### 4.2 Definició de mínim comú múltiple

Siguin $a,b\in\mathbb Z$ no nuls. El **mínim comú múltiple** $\operatorname{mcm}(a,b)$ és l'enter positiu $m$ que compleix:

1. $a\mid m$ i $b\mid m$;
2. si $a\mid n$ i $b\mid n$ per a algun $n\in\mathbb Z$, llavors $m\mid n$.

És a dir, $m$ és el múltiple comú més petit en l'ordre de la divisibilitat.

**Conveni.** $\operatorname{mcm}(a,b)=\operatorname{mcm}(|a|,|b|)$. Si un dels dos és $0$, es pren $\operatorname{mcm}(a,0)=0$ (l'únic múltiple comú de $0$ i $a$ és $0$).

### 4.3 Propietats fonamentals

| Propietat | Fórmula |
|---|---|
| Simetria | $\operatorname{mcd}(a,b)=\operatorname{mcd}(b,a)$, $\operatorname{mcm}(a,b)=\operatorname{mcm}(b,a)$. |
| Signe | $\operatorname{mcd}(a,b)=\operatorname{mcd}(|a|,|b|)$, $\operatorname{mcm}(a,b)=\operatorname{mcm}(|a|,|b|)$. |
| Zero | $\operatorname{mcd}(a,0)=|a|$; $\operatorname{mcm}(a,0)=0$. |
| Traslació | $\operatorname{mcd}(a,b)=\operatorname{mcd}(a\pm b,b)=\operatorname{mcd}(a,b\pm a)$. |
| Més general | $\operatorname{mcd}(a,b)=\operatorname{mcd}(a+kb,b)$ per a tot $k\in\mathbb Z$. |
| Homogeneïtat | $\operatorname{mcd}(ma,mb)=|m|\operatorname{mcd}(a,b)$. |
| Quocients coprimers | Si $d=\operatorname{mcd}(a,b)$, llavors $\operatorname{mcd}(a/d,b/d)=1$. |
| Producte | $\operatorname{mcd}(a,b)\operatorname{mcm}(a,b)=|ab|$, per a $a,b\ne0$. |
| MCM via MCD | $\operatorname{mcm}(a,b)=\dfrac{|ab|}{\operatorname{mcd}(a,b)}$. |
| Divisors comuns | Tot divisor comú de $a$ i $b$ divideix $\operatorname{mcd}(a,b)$. |
| Múltiples comuns | $\operatorname{mcm}(a,b)$ divideix tot múltiple comú de $a$ i $b$. |

**Demostració de la traslació.** Un enter $c$ divideix $a$ i $b$ si i només si divideix $a+kb$ i $b$:
- si $c\mid a$ i $c\mid b$, llavors $c\mid a+kb$;
- si $c\mid a+kb$ i $c\mid b$, llavors $c\mid(a+kb)-kb=a$.
Per tant, els conjunts de divisors comuns coincideixen, i el màxim és el mateix.

**Demostració de la homogeneïtat.** Per a $m>0$, usem valors $p$-àdics:
$$
v_p(\operatorname{mcd}(ma,mb))
=\min(v_p(m)+v_p(a),v_p(m)+v_p(b))
=v_p(m)+\min(v_p(a),v_p(b))
=v_p(m\operatorname{mcd}(a,b)).
$$
Com que dos nombres positius amb les mateixes valoracions a tots els primers són iguals, $\operatorname{mcd}(ma,mb)=m\operatorname{mcd}(a,b)$. Per a $m<0$, $\operatorname{mcd}(ma,mb)=|m|\operatorname{mcd}(a,b)$.

**Demostració de la relació producte.** Per a cada primer $p$,
$$
\min(r_p,s_p)+\max(r_p,s_p)=r_p+s_p,
$$
on $r_p=v_p(a)$ i $s_p=v_p(b)$. Per tant, els exponents de $p$ a $\operatorname{mcd}(a,b)\operatorname{mcm}(a,b)$ i a $|ab|$ coincideixen.

### 4.4 Càlcul per factorització

Siguin
$$
a=\prod_p p^{r_p},\qquad b=\prod_p p^{s_p},
$$
on els productes recorren tots els primers que apareixen a $a$ o $b$, i els exponents poden ser $0$. Aleshores
$$
\operatorname{mcd}(a,b)=\prod_p p^{\min(r_p,s_p)},
\qquad
\operatorname{mcm}(a,b)=\prod_p p^{\max(r_p,s_p)}.
$$

**Exemple.** $a=360=2^3\cdot3^2\cdot5$, $b=84=2^2\cdot3\cdot7$. Posem la mateixa llista de primers $2,3,5,7$:

| Primer | $r_p$ (a $360$) | $s_p$ (a $84$) | $\min$ | $\max$ |
|---|---:|---:|---:|---:|
| $2$ | $3$ | $2$ | $2$ | $3$ |
| $3$ | $2$ | $1$ | $1$ | $2$ |
| $5$ | $1$ | $0$ | $0$ | $1$ |
| $7$ | $0$ | $1$ | $0$ | $1$ |

Per tant,
$$
\operatorname{mcd}(360,84)=2^2\cdot3=12,
\qquad
\operatorname{mcm}(360,84)=2^3\cdot3^2\cdot5\cdot7=2520.
$$
Comprovació: $12\cdot2520=30240=360\cdot84$.

**Quan convé factoritzar.** Quan els nombres són petits, quan ja tenim la factorització, o quan necessitem els exponents per a una altra cosa (per exemple, $\varphi(n)$). Per a nombres grans sense factorització coneguda, l'algorisme d'Euclides és molt més eficient.

### 4.5 Càlcul per l'algorisme d'Euclides

Per a nombres grans, el mètode estàndard és:
$$
\operatorname{mcd}(a,b)=\operatorname{mcd}(b,r),
$$
on $r$ és el residu de dividir $a$ per $b$. Es repeteix fins que el residu és $0$; l'últim divisor no nul és el mcd. Aquest és l'algorisme d'Euclides, que desenvolupem a la secció 5.

**Exemple.** $\operatorname{mcd}(1492,1776)$:
$$
1776=1\cdot1492+284,\quad
1492=5\cdot284+72,\quad
284=3\cdot72+68,
$$
$$
72=1\cdot68+4,\quad
68=17\cdot4+0.
$$
L'últim residu no nul és $4$, així que $\operatorname{mcd}(1492,1776)=4$.

### 4.6 MCD i MCM de diversos nombres

Es defineixen de manera anàloga:
$$
\operatorname{mcd}(a_1,\dots,a_n),\qquad
\operatorname{mcm}(a_1,\dots,a_n).
$$
Propietats:

- Són associatius i commutatius:
  $$
  \operatorname{mcd}(a,b,c)=\operatorname{mcd}(\operatorname{mcd}(a,b),c),
  \qquad
  \operatorname{mcm}(a,b,c)=\operatorname{mcm}(\operatorname{mcm}(a,b),c).
  $$
- Per factorització, es prenen els exponents mínims (mcd) o màxims (mcm) per a cada primer.
- **Atenció:** en general,
  $$
  \operatorname{mcm}(a,b,c)\ne\frac{abc}{\operatorname{mcd}(a,b,c)}.
  $$
  La fórmula $ab/\operatorname{mcd}(a,b)$ és només per a dos nombres.
- Si els nombres són **coprimers dos a dos**, llavors
  $$
  \operatorname{mcm}(a_1,\dots,a_n)=a_1\cdots a_n.
  $$
  Aquesta és la situació del teorema xinès del residu.

### 4.7 Propietats distributives de mcd i mcm

En el reticle de divisibilitat es compleixen:
$$
\operatorname{mcd}(a,\operatorname{mcm}(b,c))
=
\operatorname{mcm}(\operatorname{mcd}(a,b),\operatorname{mcd}(a,c)),
$$
$$
\operatorname{mcm}(a,\operatorname{mcd}(b,c))
=
\operatorname{mcd}(\operatorname{mcm}(a,b),\operatorname{mcm}(a,c)).
$$
Es demostren primer amb valors $p$-àdics, usant les identitats
$$
\min(x,\max(y,z))=\max(\min(x,y),\min(x,z)),
$$
$$
\max(x,\min(y,z))=\min(\max(x,y),\max(x,z)).
$$
La primera és l'exercici 1.38 (l).

### 4.8 Consells pràctics

1. **Per calcular un mcd:** si els nombres són petits o ja estan factoritzats, factoritzeu; si són grans, useu Euclides.
2. **Per calcular un mcm:** useu
   $$
   \operatorname{mcm}(a,b)=\frac{|ab|}{\operatorname{mcd}(a,b)}
   $$
   o la factorització. No cal calcular el mcm directament amb Euclides.
3. **Per simplificar fraccions:** dividiu numerador i denominador pel mcd. Els quocients són coprimers.
4. **Per demostrar que un mcd és $1$:** busqueu una combinació lineal que valgui $\pm1$, o demostreu que cap primer divideix els dos nombres.
5. **Per a expressions en $n$:** elimineu la $n$ amb una combinació lineal; el mcd ha de dividir la constant resultant. Després comproveu quins divisors de la constant apareixen realment.
6. **Comproveu sempre** que el mcd divideix els dos nombres i que el mcm és múltiple dels dos. Si heu usat la fórmula producte, comproveu $\operatorname{mcd}\cdot\operatorname{mcm}=|ab|$.

### 4.9 Connexions amb els exercicis

- **Exercici 1.1:** $\operatorname{mcd}(a+b,a-b)\in\{1,2\}$ si $\operatorname{mcd}(a,b)=1$. Idea: $d\mid2a$ i $d\mid2b$, així que $d\mid2$.
- **Exercici 1.2:** $\operatorname{mcd}(ma,mb)=|m|\operatorname{mcd}(a,b)$.
- **Exercici 1.3:** $\operatorname{mcd}(3a-b,b-2a)=\operatorname{mcd}(a,b)$; la transformació és unimodular (determinant $1$).
- **Exercici 1.4:** $\operatorname{mcd}(28n-5,35n-8)=1$.
- **Exercici 1.6:** càlcul de mcm a partir del mcd.
- **Exercici 1.7:** fracció irreductible; combinació lineal constant $\pm1$.
- **Exercici 1.14:** verificació de les fórmules min/max amb factoritzacions.

***
<a id="sec5"></a>
## 5. Algorisme d'Euclides i identitat de Bézout

### 5.1 Divisió euclidiana

**Teorema (divisió euclidiana).** Siguin $a\in\mathbb Z$ i $b\in\mathbb Z$ amb $b>0$. Aleshores existeixen **únics** $q,r\in\mathbb Z$ tals que
$$
a=bq+r,\qquad 0\le r<b.
$$
$q$ és el **quocient** i $r$ el **residu**.

**Demostració de l'existència.** Considerem el conjunt
$$
S=\{a-bq:q\in\mathbb Z\}\cap\{0,1,\dots,b-1\}.
$$
Prenent $q$ prou petit (molt negatiu), $a-bq$ es fa positiu; i podem triar el representant de $a$ mòdul $b$ a l'interval $[0,b-1]$. Així $S$ no és buit i té un element $r=a-bq$ amb $0\le r<b$.

**Demostració de la unicitat.** Si $a=bq+r=bq'+r'$ amb $0\le r,r'<b$, llavors
$$
b(q-q')=r'-r.
$$
El valor absolut del costat dret és $<b$, mentre que el costat esquerre és múltiple de $b$. L'única possibilitat és $r'-r=0$, i llavors $q=q'$.

**Exemples.**

- $a=17$, $b=5$: $17=5\cdot3+2$, $q=3$, $r=2$.
- $a=-7$, $b=3$: $-7=3\cdot(-3)+2$, $q=-3$, $r=2$. El residu no negatiu és $2$, no $-1$.
- $a=7$, $b=-3$: normalment prenem $b>0$; si no, es treballa amb $|b|$ o s'adapta la condició $0\le r<|b|$.

### 5.2 Algorisme d'Euclides

Per calcular $\operatorname{mcd}(a,b)$ amb $a,b>0$:

$$
\begin{aligned}
a&=bq_1+r_1, & 0&\le r_1<b,\\
b&=r_1q_2+r_2, & 0&\le r_2<r_1,\\
r_1&=r_2q_3+r_3, & 0&\le r_3<r_2,\\
&\;\;\vdots\\
r_{n-2}&=r_{n-1}q_n+r_n, & 0&\le r_n<r_{n-1},\\
r_{n-1}&=r_nq_{n+1}+0.
\end{aligned}
$$

L'últim residu no nul $r_n$ és $\operatorname{mcd}(a,b)$.

**Pseudocodi.**

```text
euclides(a, b):
    a = |a|; b = |b|
    while b != 0:
        (a, b) = (b, a mod b)
    return a
```

**Exemple complet.** $\operatorname{mcd}(240,46)$:
$$
\begin{aligned}
240&=5\cdot46+10,\\
46&=4\cdot10+6,\\
10&=1\cdot6+4,\\
6&=1\cdot4+2,\\
4&=2\cdot2+0.
\end{aligned}
$$
L'últim residu no nul és $2$, així que $\operatorname{mcd}(240,46)=2$.

**Per què funciona.** A cada pas usem
$$
\operatorname{mcd}(a,b)=\operatorname{mcd}(b,r),
$$
perquè els divisors comuns de $a$ i $b$ són exactament els divisors comuns de $b$ i $r=a-bq$. Els residus disminueixen estrictament i no poden ser negatius, així que l'algorisme acaba. Quan arribem a $r=0$, tenim $\operatorname{mcd}(r_{n-1},0)=r_{n-1}$.

**Complexitat.** El nombre de divisions és $O(\log(\min(|a|,|b|)))$; el pitjor cas es dóna amb nombres de Fibonacci consecutius.

### 5.3 Identitat de Bézout

**Teorema (Bézout).** Siguin $a,b\in\mathbb Z$, no tots dos zero, i $d=\operatorname{mcd}(a,b)$. Aleshores existeixen $\alpha,\beta\in\mathbb Z$ tals que
$$
d=\alpha a+\beta b.
$$
A més, el conjunt de les combinacions lineals de $a$ i $b$ és exactament $d\mathbb Z$:
$$
\{ua+vb:u,v\in\mathbb Z\}=d\mathbb Z.
$$

**Demostració constructiva.** L'algorisme d'Euclides dóna els residus com a combinacions lineals de $a$ i $b$. El penúltim residu no nul és $d$, i expressant-lo cap enrere s'obté la combinació. Això demostra l'existència de manera efectiva.

**Demostració abstracta.** El conjunt $I=\{ua+vb:u,v\in\mathbb Z\}$ és un ideal no nul de $\mathbb Z$. Tot ideal de $\mathbb Z$ és principal, així que $I=(d')$ per a algun $d'>0$. Com que $a,b\in I$, $d'\mid a$ i $d'\mid b$. A més, $d'=ua+vb$ per a alguns $u,v$, i qualsevol divisor comú de $a$ i $b$ divideix $d'$. Per tant, $d'=\operatorname{mcd}(a,b)$.

**Corol·lari fonamental.**
$$
\operatorname{mcd}(a,b)=1
\iff
\exists\alpha,\beta\in\mathbb Z:\ \alpha a+\beta b=1.
$$

**Demostració.**

- $(\Rightarrow)$ És Bézout amb $d=1$.
- $(\Leftarrow)$ Si $\alpha a+\beta b=1$, qualsevol divisor comú $c$ de $a$ i $b$ divideix $\alpha a+\beta b=1$. Per tant, $c=\pm1$, i el mcd és $1$.

**El mcd és la combinació lineal positiva més petita.** Si $a,b$ no són tots dos zero, el menor enter positiu de la forma $ua+vb$ és exactament $\operatorname{mcd}(a,b)$. Això dóna una caracterització alternativa molt útil.

### 5.4 Coeficients de Bézout no únics

Si
$$
d=\alpha a+\beta b,
$$
llavors per a qualsevol $t\in\mathbb Z$,
$$
d=\left(\alpha+t\frac{b}{d}\right)a+
\left(\beta-t\frac{a}{d}\right)b.
$$
Així, els coeficients de Bézout formen una família infinita. Quan $\operatorname{mcd}(a,b)=1$,
$$
d=1,\qquad
\alpha'=\alpha+tb,\qquad
\beta'=\beta-ta.
$$

**Comprovació.** Els termes addicionals són
$$
t\frac{b}{d}a-t\frac{a}{d}b=0.
$$

### 5.5 Mètode de substitucions cap enrere

És el mètode més directe:

1. Apliqueu Euclides i guardeu les divisions.
2. Aïlleu el residu de l'última divisió no nul·la.
3. Substituïu cada residu per la seva expressió en la divisió anterior.
4. Repetiu fins a expressar el mcd com a combinació de $a$ i $b$.

**Exemple.** $\operatorname{mcd}(240,46)=2$:
$$
\begin{aligned}
2&=6-4,\\
4&=10-6 &&\Rightarrow 2=2\cdot6-10,\\
6&=46-4\cdot10 &&\Rightarrow 2=2\cdot46-9\cdot10,\\
10&=240-5\cdot46 &&\Rightarrow 2=47\cdot46-9\cdot240.
\end{aligned}
$$
Per tant,
$$
2=(-9)\cdot240+47\cdot46,
\qquad
\alpha=-9,\ \beta=47.
$$
Comprovació: $-9\cdot240+47\cdot46=-2160+2162=2$.

**Exemple.** $\operatorname{mcd}(31,12)=1$:
$$
\begin{aligned}
31&=2\cdot12+7,\\
12&=1\cdot7+5,\\
7&=1\cdot5+2,\\
5&=2\cdot2+1,\\
2&=2\cdot1+0.
\end{aligned}
$$
Cap enrere:
$$
1=5-2\cdot2=5-2(7-5)=3\cdot5-2\cdot7
=3(12-7)-2\cdot7=3\cdot12-5\cdot7
$$
$$
=3\cdot12-5(31-2\cdot12)=13\cdot12-5\cdot31.
$$
Així,
$$
1=(-5)\cdot31+13\cdot12,
\qquad
\alpha=-5,\ \beta=13.
$$

### 5.6 Mètode matricial $2\times2$

La identitat de Bézout es pot calcular de manera molt ordenada amb matrius. Representem la parella $(a,b)$ com un vector fila. Cada divisió
$$
a=bq+r
$$
es pot escriure com
$$
(a,b)
\begin{pmatrix}
0&1\\
1&-q
\end{pmatrix}
=
(b,\ a-qb)
=
(b,r).
$$
La matriu
$$
M_q=
\begin{pmatrix}
0&1\\
1&-q
\end{pmatrix}
$$
té determinant $-1$, així que és invertible sobre $\mathbb Z$ (unimodular). Això garanteix que les combinacions lineals enteres es conserven.

Si repetim el procés fins a obtenir $(d,0)$,
$$
(a,b)M=(d,0),
$$
on $M$ és el producte de les matrius $M_q$ en l'ordre de les divisions. Si
$$
M=
\begin{pmatrix}
m_{11}&m_{12}\\
m_{21}&m_{22}
\end{pmatrix},
$$
llavors
$$
(a,b)M=(a m_{11}+b m_{21},\ a m_{12}+b m_{22}).
$$
La primera component és $d$, així que
$$
\boxed{d=a\,m_{11}+b\,m_{21}}.
$$
Per tant, els coeficients de Bézout són la **primera columna** de $M$:
$$
\boxed{\alpha=m_{11},\qquad \beta=m_{21}}.
$$

**Algorisme.**

1. Inicialitzeu $M=I_2$.
2. Mentre la parella actual $(a,b)$ no tingui un component zero:
   - feu la divisió $a=bq+r$;
   - actualitzeu $(a,b)\leftarrow(b,r)$;
   - actualitzeu $M\leftarrow M M_q$.
3. Quan un component sigui zero, l'altre és $d=\operatorname{mcd}(a,b)$.
4. La primera columna de $M$ dóna $\alpha,\beta$.

**Exemple 1: $\operatorname{mcd}(240,46)$.** Quocients $5,4,1,1,2$:
$$
M=
\begin{pmatrix}
0&1\\
1&-5
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-4
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix}
=
\begin{pmatrix}
-9&23\\
47&-120
\end{pmatrix}.
$$
La primera columna és $(-9,47)$, així que
$$
2=(-9)\cdot240+47\cdot46.
$$

**Exemple 2: $\operatorname{mcd}(31,12)$.** Quocients $2,1,1,2,2$:
$$
M=
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix}
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix}
=
\begin{pmatrix}
-5&12\\
13&-31
\end{pmatrix}.
$$
La primera columna és $(-5,13)$, així que
$$
1=(-5)\cdot31+13\cdot12.
$$

**Justificació de la primera columna.** Si $(a,b)M=(d,0)$, la primera component és $a m_{11}+b m_{21}=d$. Com que $m_{11},m_{21}\in\mathbb Z$, aquests són els coeficients de Bézout. La matriu $M$ és un producte de matrius de determinant $-1$; per tant, $\det M=\pm1$, i les operacions preserven el mcd.

### 5.7 Mètode iteratiu (Euclides estès)

Una altra manera de calcular els coeficients, molt adequada per a programació, és mantenir tres parelles de valors:
$$
(r_0,r_1),\qquad (s_0,s_1),\qquad (t_0,t_1),
$$
amb la invariància
$$
r_i=s_i a+t_i b.
$$
Inicialment:
$$
r_0=a,\ r_1=b,\qquad s_0=1,\ s_1=0,\qquad t_0=0,\ t_1=1.
$$
A cada pas, amb $q=\lfloor r_0/r_1\rfloor$:
$$
r_2=r_0-q r_1,\qquad
s_2=s_0-q s_1,\qquad
t_2=t_0-q t_1.
$$
Es desplacen els valors i es repeteix fins que $r_1=0$. L'últim $r_0$ no nul és $d$, i els corresponents $s_0,t_0$ són $\alpha,\beta$.

**Exemple amb $240,46$.** Les files successives són:

| Residu | Expressió |
|---:|---|
| $240$ | $1\cdot240+0\cdot46$ |
| $46$ | $0\cdot240+1\cdot46$ |
| $10$ | $1\cdot240-5\cdot46$ |
| $6$ | $-4\cdot240+21\cdot46$ |
| $4$ | $5\cdot240-26\cdot46$ |
| $2$ | $-9\cdot240+47\cdot46$ |
| $0$ | $23\cdot240-120\cdot46$ |

El darrer residu no nul és $2$, amb coeficients $(-9,47)$.

### 5.8 Invers modular mitjançant Bézout

Si $\operatorname{mcd}(a,m)=1$, per Bézout existeixen $\alpha,\beta$ amb
$$
\alpha a+\beta m=1.
$$
Reduint mòdul $m$:
$$
\alpha a\equiv1\pmod m.
$$
Per tant,
$$
\boxed{a^{-1}\equiv\alpha\pmod m}.
$$
El coeficient $\beta$ no interessa per a l'invers, però apareix en la combinació.

**Exemple (exercici 1.20).** Invers de $29$ mòdul $1170$. Euclides:
$$
1170=40\cdot29+10,\quad
29=2\cdot10+9,\quad
10=1\cdot9+1.
$$
Cap enrere:
$$
1=10-9=3\cdot10-29=3(1170-40\cdot29)-29=3\cdot1170-121\cdot29.
$$
Així,
$$
29^{-1}\equiv-121\equiv1049\pmod{1170}.
$$
Comprovació: $29\cdot1049=30421=26\cdot1170+1$.

**Exemple (exercici 1.28).** Invers de $37$ mòdul $98$:
$$
1=17\cdot98-45\cdot37,
$$
així que
$$
37^{-1}\equiv-45\equiv53\pmod{98}.
$$
Comprovació: $37\cdot53=1961=20\cdot98+1$.

### 5.9 Errors freqüents

- **Perdre el signe** en les substitucions cap enrere. Comproveu sempre la combinació final.
- **Multiplicar les matrius en ordre incorrecte.** Si les divisions són $q_1,\dots,q_n$, el producte és $M_{q_1}M_{q_2}\cdots M_{q_n}$.
- **Usar la segona columna** de la matriu en lloc de la primera. La primera dóna $d$; la segona dóna la relació del zero.
- **Concloure que els coeficients són únics.** No ho són; difereixen per múltiples de $b/d$ i $-a/d$.
- **Aplicar Bézout amb $d\ne1$ per trobar un invers.** Només hi ha invers si $d=1$.
- **Oblidar reduir mòdul $m$.** L'invers és una classe; el representant pot ser negatiu, però normalment es dóna entre $0$ i $m-1$.

***

<a id="sec6"></a>
## 6. Equacions diofàntiques lineals

### 6.1 Equació i condició de solució

Una **equació diofàntica lineal** és una equació
$$
ax+by=c,
$$
on $a,b,c\in\mathbb Z$ i es busquen solucions $x,y\in\mathbb Z$ (només enters).

Sigui
$$
d=\operatorname{mcd}(a,b).
$$
Aleshores:
$$
\boxed{ax+by=c \text{ té solució entera} \iff d\mid c.}
$$

**Demostració.**

- $(\Rightarrow)$ Si $ax+by=c$, com que $d\mid a$ i $d\mid b$, per linealitat $d\mid ax+by=c$.
- $(\Leftarrow)$ Si $d\mid c$, escrivim $c=dc'$. Per Bézout, $d=\alpha a+\beta b$. Multiplicant per $c'$:
  $$
  c=dc'=\alpha c'a+\beta c'b.
  $$
  Per tant, $(x_0,y_0)=(\alpha c',\beta c')$ és una solució.

**Conseqüència important.** Si $d\nmid c$, l'equació no té cap solució entera. Per exemple, $2x+4y=7$ no té solució perquè $\operatorname{mcd}(2,4)=2\nmid7$.

### 6.2 Solució general

Si $(x_0,y_0)$ és una solució particular de $ax+by=c$, aleshores **totes** les solucions enteres són
$$
\boxed{x=x_0+\frac{b}{d}t,\qquad y=y_0-\frac{a}{d}t,\qquad t\in\mathbb Z,}
$$
on $d=\operatorname{mcd}(a,b)$.

**Demostració que són solucions.** Per a qualsevol $t$,
$$
a\left(x_0+\frac bd t\right)+b\left(y_0-\frac ad t\right)
=ax_0+by_0+t\frac{ab}{d}-t\frac{ab}{d}=c.
$$

**Demostració que són totes.** Si $(x,y)$ és una altra solució, restant $ax_0+by_0=c$:
$$
a(x-x_0)+b(y-y_0)=0.
$$
Escrivim $a=da'$, $b=db'$ amb $\operatorname{mcd}(a',b')=1$. Aleshores
$$
a'(x-x_0)=-b'(y-y_0).
$$
Com que $\operatorname{mcd}(a',b')=1$, pel lema d'Euclides $b'\mid(x-x_0)$. Així $x-x_0=b't$ per a algun $t\in\mathbb Z$, i substituint s'obté $y-y_0=-a't$. Per tant, totes les solucions tenen la forma indicada.

**Interpretació geomètrica.** Les solucions enteres són els punts de la recta $ax+by=c$ amb coordenades enteres. El vector
$$
\left(\frac bd,-\frac ad\right)
$$
és el pas mínim entre punts enters consecutius de la recta.

### 6.3 Algorisme de resolució

Per resoldre $ax+by=c$:

1. **Calculeu** $d=\operatorname{mcd}(a,b)$.
2. **Comproveu** si $d\mid c$. Si no, no hi ha solució.
3. **Dividiu** l'equació per $d$:
   $$
   a'x+b'y=c',\qquad a'=\frac ad,\ b'=\frac bd,\ c'=\frac cd.
   $$
   Ara $\operatorname{mcd}(a',b')=1$.
4. **Trobeu** una solució particular de $a'x+b'y=c'$:
   - trobeu $\alpha,\beta$ amb $\alpha a'+\beta b'=1$ (Bézout);
   - feu $x_0=\alpha c'$, $y_0=\beta c'$.
5. **Escriviu la solució general:**
   $$
   x=x_0+b't,\qquad y=y_0-a't.
   $$
6. **Comproveu** substituint a l'equació original.

**Consell.** Per mantenir els nombres petits, podem reduir $x_0$ mòdul $b'$ i ajustar $y_0$ corresponentment. Si canviem $x_0$ per $x_0+kb'$, aleshores $y_0$ canvia per $y_0-ka'$.

### 6.4 Exemples

**Exemple 1 (exercici 1.8a).** $93x-81y=3$.

Dividim per $3$:
$$
31x-27y=1.
$$
Euclides:
$$
31=1\cdot27+4,\quad
27=6\cdot4+3,\quad
4=1\cdot3+1.
$$
Cap enrere:
$$
1=4-3=4-(27-6\cdot4)=7\cdot4-27=7(31-27)-27=7\cdot31-8\cdot27.
$$
Així, $31\cdot7-27\cdot8=1$, i una solució particular és $(x_0,y_0)=(7,8)$. La solució general:
$$
x=7+27t,\qquad y=8+31t,\qquad t\in\mathbb Z.
$$
Comprovació: $93(7)-81(8)=651-648=3$.

**Exemple 2 (exercici 1.8b).** $71x-50y=1$.

Euclides dóna
$$
1=27\cdot50-19\cdot71.
$$
Així, $71\cdot(-19)-50\cdot(-27)=1$, i una solució particular és $(-19,-27)$. General:
$$
x=-19+50t,\qquad y=-27+71t.
$$

**Exemple 3 (exercici 1.8c).** $42x+18y=34$.

$\operatorname{mcd}(42,18)=6$, però $6\nmid34$. **No hi ha solució.**

**Exemple 4 (exercici 1.8d).** $283x-1722y=31$.

Euclides:
$$
1722=6\cdot283+24,\quad
283=11\cdot24+19,\quad
24=1\cdot19+5,\quad
19=3\cdot5+4,\quad
5=1\cdot4+1.
$$
Cap enrere:
$$
1=5-4=4\cdot5-19=4\cdot24-5\cdot19=59\cdot24-5\cdot283
=59\cdot1722-359\cdot283.
$$
Multiplicant per $31$:
$$
283\cdot(-11129)-1722\cdot(-1829)=31.
$$
Reduint la solució particular mòdul $1722$:
$$
x_0=-11129+7\cdot1722=925,\qquad
y_0=-1829+7\cdot283=152.
$$
General:
$$
x=925+1722t,\qquad y=152+283t.
$$
Comprovació: $283\cdot925-1722\cdot152=261775-261744=31$.

**Exemple 5 (exercici 1.9b).** $3822x+65y=26$.

Com que $3822=2\cdot1911$ i $\operatorname{mcd}(1911,65)=13$, tenim $\operatorname{mcd}(3822,65)=13$. Com que $13\mid26$, hi ha solució. De l'exercici 1.9a,
$$
13=(-2)\cdot1911+59\cdot65.
$$
Multiplicant per $2$:
$$
26=(-4)\cdot1911+118\cdot65=(-2)\cdot3822+118\cdot65.
$$
Així, $(x_0,y_0)=(-2,118)$. General:
$$
x=-2+5s,\qquad y=118-294s,\qquad s\in\mathbb Z.
$$

### 6.5 Solucions amb cotes: el joc de l'aniversari

**Exercici 1.10.** Una persona multiplica el dia del seu aniversari per $12$, el mes per $31$, suma els resultats i ens dóna només la suma $S$. Podem recuperar la data?

Siguin $d\in\{1,\dots,31\}$ el dia i $m\in\{1,\dots,12\}$ el mes. Aleshores
$$
S=12d+31m.
$$

**Unicitat.** Si $12d_1+31m_1=12d_2+31m_2$, llavors
$$
12(d_1-d_2)=31(m_2-m_1).
$$
Com que $\operatorname{mcd}(12,31)=1$, $12\mid(m_2-m_1)$. Però $|m_2-m_1|\le11<12$, així que $m_1=m_2$ i llavors $d_1=d_2$. Per tant, la data queda determinada per $S$.

**Recuperació.** Reduïm mòdul $12$:
$$
S\equiv31m\equiv7m\pmod{12}.
$$
Com que $7^{-1}\equiv7\pmod{12}$ (perquè $7\cdot7=49\equiv1$),
$$
m\equiv7S\pmod{12}.
$$
Prenem el representant de $m$ a $\{1,\dots,12\}$ (si el residu és $0$, llavors $m=12$). Després
$$
d=\frac{S-31m}{12}.
$$

**Exemple.** $S=353$:
$$
7\cdot353=2471\equiv11\pmod{12},
$$
així que $m=11$ (novembre) i
$$
d=\frac{353-31\cdot11}{12}=\frac{353-341}{12}=1.
$$
La data és l'**1 de novembre**.

**Un altre exemple.** $S=256$:
$$
7\cdot256=1792\equiv4\pmod{12},
$$
així que $m=4$ (abril) i
$$
d=\frac{256-31\cdot4}{12}=\frac{256-124}{12}=11.
$$
La data és l'**11 d'abril**.

> **Atenció amb l'ordre dels coeficients.** Al full de problemes, el dia es multiplica per $12$ i el mes per $31$. Si useu la convenció contrària, canvieu les fórmules en conseqüència.

### 6.6 Equació homogènia

L'equació
$$
ax+by=0
$$
sempre té la solució trivial $(0,0)$. Si $d=\operatorname{mcd}(a,b)$, totes les solucions són
$$
x=\frac bd t,\qquad y=-\frac ad t,\qquad t\in\mathbb Z.
$$
Això és la solució general del sistema homogeni associat; la solució general de $ax+by=c$ és una solució particular més la solució general de l'homogeni.

### 6.7 Errors freqüents

- **No comprovar $d\mid c$.** És la condició necessària i suficient; sense ella no hi ha solució.
- **No dividir per $d$.** Els passos de la solució general usen $a/d$ i $b/d$, no $a$ i $b$.
- **Confondre els signes.** Per a $ax-by=c$, tracteu-lo com $ax+(-b)y=c$, o adapteu la fórmula.
- **Donar només una solució.** L'equació té infinites solucions (si en té una); cal donar la família paramètrica.
- **Oblidar comprovar.** La substitució és ràpida i detecta errors de signe.
- **Pensar que la solució particular ha de ser positiva.** Pot ser negativa; les cotes o el context poden seleccionar la solució desitjada.

***
<a id="sec7"></a>
## 7. Nombres primers i factorització

### 7.1 Definició de nombre primer

Un enter $p>1$ és **primer** si els únics divisors positius de $p$ són $1$ i $p$.

- $1$ **no** és primer.
- $2$ és l'únic primer parell.
- Els primers positius comencen:
  $$
  2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97,\dots
  $$
- A $\mathbb Z$, els associats $-p$ també es comporten com a irreductibles, però normalment ens restringim als primers positius.

**Definició equivalent.** $p>1$ és primer si, per a tots $a,b\in\mathbb Z$,
$$
p\mid ab \implies p\mid a \text{ o } p\mid b.
$$
Aquesta propietat és la que distingeix els primers dels nombres compostos.

### 7.2 Lema d'Euclides

**Lema.** Si $p$ és primer i $p\mid ab$, aleshores $p\mid a$ o $p\mid b$.

**Demostració.** Si $p\mid a$, ja està. Si $p\nmid a$, com que els únics divisors positius de $p$ són $1$ i $p$, tenim $\operatorname{mcd}(p,a)=1$. Per Bézout existeixen $\alpha,\beta$ amb
$$
\alpha p+\beta a=1.
$$
Multiplicant per $b$:
$$
\alpha pb+\beta ab=b.
$$
Ara $p\mid\alpha pb$ i, per hipòtesi, $p\mid ab$, així que $p\mid\beta ab$. Per linealitat, $p\mid b$.

**Generalització.** Si $p$ és primer i $p\mid a_1a_2\cdots a_n$, llavors $p\mid a_i$ per a algun $i$. Es demostra per inducció usant el lema.

**Generalització a mòduls no primers.** Si $a\mid bc$ i $\operatorname{mcd}(a,b)=1$, llavors $a\mid c$. Aquesta és la versió general del lema d'Euclides (secció 3).

### 7.3 Teorema fonamental de l'aritmètica

**Teorema.** Tot enter $n\ne0,\pm1$ es pot escriure de manera única (llevat de l'ordre dels factors i del signe) com a producte de potències de primers:
$$
n=\pm p_1^{r_1}p_2^{r_2}\cdots p_k^{r_k},
$$
amb $p_1,\dots,p_k$ primers positius diferents i $r_1,\dots,r_k\ge1$.

**Existència.** Es demostra per inducció forta sobre $|n|$. Si $|n|$ és primer, ja està. Si no, $|n|=ab$ amb $1<a,b<|n|$; per hipòtesi d'inducció, $a$ i $b$ factoritzen en primers, i ajuntant les factoritzacions s'obté la de $|n|$. El signe es treu fora.

**Unicitat.** Suposem
$$
p_1p_2\cdots p_r=q_1q_2\cdots q_s,
$$
amb tots els $p_i,q_j$ primers. Com que $p_1$ divideix el producte de la dreta, pel lema d'Euclides $p_1$ divideix algun $q_j$. Com que $q_j$ és primer, $p_1=q_j$. Cancel·lem aquest factor i repetim. Així les dues llistes coincideixen llevat d'ordre. Agrupant factors repetits s'obté la forma amb exponents.

**Conseqüència.** La factorització és única. Per exemple,
$$
84=2^2\cdot3\cdot7,
\qquad
360=2^3\cdot3^2\cdot5.
$$
No hi ha cap altra factorització en primers llevat de reordenar els factors.

### 7.4 Valoracions $p$-àdiques

Per a un primer $p$ i un enter $n\ne0$, $v_p(n)$ és l'exponent de $p$ a la factorització de $n$. Per conveni, $v_p(0)=+\infty$.

Propietats:

1. $v_p(ab)=v_p(a)+v_p(b)$.
2. $v_p(a+b)\ge\min(v_p(a),v_p(b))$.
3. Si $v_p(a)\ne v_p(b)$, llavors
   $$
   v_p(a+b)=\min(v_p(a),v_p(b)).
   $$
4. $a\mid b\iff v_p(a)\le v_p(b)$ per a tot primer $p$.
5. $\operatorname{mcd}(a,b)=\prod_p p^{\min(v_p(a),v_p(b))}$.
6. $\operatorname{mcm}(a,b)=\prod_p p^{\max(v_p(a),v_p(b))}$.

Les valoracions són molt útils per demostrar propietats de divisibilitat sense fer cas per cas.

**Exemple (exercici 1.12).** Si $a^2\mid b^2$, llavors per a tot primer $p$,
$$
2v_p(a)=v_p(a^2)\le v_p(b^2)=2v_p(b),
$$
així que $v_p(a)\le v_p(b)$. Per tant, $a\mid b$.

**Exemple (exercici 1.11).** Si $ab$ és un quadrat perfecte i $\operatorname{mcd}(a,b)=1$, llavors per a cada primer $p$, com a molt un de $v_p(a),v_p(b)$ és positiu. Com que $v_p(a)+v_p(b)$ és parell, l'únic exponent positiu és parell. Per tant, $a$ i $b$ són quadrats perfectes.

### 7.5 Hi ha infinits nombres primers

**Teorema (Euclides).** Hi ha infinits nombres primers.

**Demostració.** Suposem que només n'hi hagués un nombre finit:
$$
p_1,p_2,\dots,p_n.
$$
Considerem
$$
N=p_1p_2\cdots p_n+1.
$$
Cap $p_i$ divideix $N$, perquè $N$ deixa residu $1$ en dividir per $p_i$. Per tant, $N$ o bé és primer, o bé té un factor primer que no és cap dels $p_i$. En tots dos casos hi ha un primer fora de la llista, contradicció.

### 7.6 Criteris de divisibilitat

| Divisor | Criteri |
|---|---|
| $2$ | L'última xifra és parell. |
| $3$ | La suma de les xifres és divisible per $3$. |
| $4$ | Les dues últimes xifres formen un nombre divisible per $4$. |
| $5$ | L'última xifra és $0$ o $5$. |
| $6$ | És divisible per $2$ i per $3$. |
| $8$ | Les tres últimes xifres formen un nombre divisible per $8$. |
| $9$ | La suma de les xifres és divisible per $9$. |
| $10$ | L'última xifra és $0$. |
| $11$ | La suma alternada de les xifres és divisible per $11$. |

**Per què funcionen.** En base $10$:
- $10\equiv1\pmod3$ i $10\equiv1\pmod9$, així que $n\equiv$ suma de xifres.
- $10\equiv-1\pmod{11}$, així que les potències de $10$ alternen signe.
- $10^2=100\equiv0\pmod4$, així que només compten les dues últimes xifres.
- $10^3=1000\equiv0\pmod8$, així que només compten les tres últimes xifres.

**Exemple.** $2347$: és senar, la suma de xifres és $2+3+4+7=16$ (no divisible per $3$), no acaba en $0$ ni $5$. Per provar que és primer, cal provar els primers $\le\sqrt{2347}\approx48.4$:
$$
2,3,5,7,11,13,17,19,23,29,31,37,41,43,47.
$$
Cap d'ells divideix $2347$, així que $2347$ és primer (exercici 1.38 (n)).

### 7.7 Test de primalitat i garbell d'Eratòstenes

**Test de primalitat per divisió.** Per saber si $n>1$ és primer, n'hi ha prou de provar si és divisible per algun primer $p\le\sqrt n$.

**Per què.** Si $n=ab$ amb $1<a\le b<n$, llavors $a\le\sqrt n$. Per tant, si no hi ha cap divisor $\le\sqrt n$, $n$ és primer.

**Garbell d'Eratòstenes.** Per llistar els primers fins a $N$:

1. Escriviu els nombres $2,3,\dots,N$.
2. Comenceu amb $p=2$.
3. Marqueu com a compostos tots els múltiples de $p$ més grans que $p$: $2p,3p,4p,\dots$
4. Agafeu el següent nombre no marcat; és primer.
5. Repetiu fins que $p^2>N$.
6. Els nombres no marcats són primers.

**Consell.** Per a nombres grans, no feu divisions fins a $n/2$; atureu-vos a $\sqrt n$. Per a $n$ de 6 xifres, això redueix moltíssim la feina.

### 7.8 Aplicacions de la factorització

**MCD i MCM.** Ja els hem vist: mínims i màxims exponents.

**Simplificació de fraccions.** Si $d=\operatorname{mcd}(a,b)$, aleshores
$$
\frac ab=\frac{a/d}{b/d}
$$
és irreductible.

**Perfectes quadrats, cubs, etc.** Perquè $n$ sigui un quadrat perfecte, tots els exponents de la seva factorització han de ser parells. Perquè sigui un cub, múltiples de $3$, etc.

**Exercici 1.13.** Volem el menor $n$ tal que $n/2$ sigui quadrat, $n/3$ cub i $n/5$ cinquena potència. Escrivim $n=\prod p^{e_p}$. Les condicions són, per a cada primer $p$:

| Primer | Condicions sobre $e_p$ | Mínim |
|---|---|---:|
| $2$ | $e_2\equiv1\pmod2$, $e_2\equiv0\pmod3$, $e_2\equiv0\pmod5$ | $15$ |
| $3$ | $e_3\equiv1\pmod3$, $e_3\equiv0\pmod2$, $e_3\equiv0\pmod5$ | $10$ |
| $5$ | $e_5\equiv1\pmod5$, $e_5\equiv0\pmod2$, $e_5\equiv0\pmod3$ | $6$ |
| $p\ne2,3,5$ | $e_p\equiv0\pmod{2,3,5}$ | $0$ |

Per tant,
$$
n=2^{15}\cdot3^{10}\cdot5^6=30\,233\,088\,000\,000.
$$

**Exercici 1.14.** Les factoritzacions dels nombres de l'exercici 1.5 són:
$$
1492=2^2\cdot373,\quad
1776=2^4\cdot3\cdot37,\quad
7469=7\cdot11\cdot97,
$$
$$
2464=2^5\cdot7\cdot11,\quad
500=2^2\cdot5^3,\quad
11312=2^4\cdot7\cdot101.
$$
Amb aquestes, es comprova que el mcd pren els mínims exponents i el mcm els màxims.

### 7.9 Nombres de Mersenne

El $q$-èssim **nombre de Mersenne** és
$$
M_q=2^q-1.
$$
No sempre és primer; per exemple, $M_{11}=2047=23\cdot89$.

**Propietat 1.** Si $M_q$ és primer, llavors $q$ és primer.

**Demostració.** Si $q=ab$ amb $1<a,b<q$, llavors
$$
2^q-1=(2^a)^b-1=(2^a-1)\left((2^a)^{b-1}+(2^a)^{b-2}+\cdots+2^a+1\right),
$$
i els dos factors són $>1$. Per tant, $M_q$ és compost. Contrapostiu: si $M_q$ és primer, $q$ és primer.

**Propietat 2 (exercici 1.37c).** Si $q$ és primer i $p$ és un primer que divideix $M_q$, llavors
$$
p\equiv1\pmod q.
$$

**Demostració.** Tenim $2^q\equiv1\pmod p$. Com que $p\ne2$, $2$ és invertible mòdul $p$. Sigui $r=\operatorname{ord}_p(2)$; llavors $r\mid q$. Com que $q$ és primer, $r=1$ o $r=q$. Si $r=1$, llavors $2\equiv1\pmod p$, impossible perquè $p\ne1$. Així $r=q$. Pel teorema de Fermat, $r\mid p-1$, així que $q\mid p-1$, és a dir, $p\equiv1\pmod q$. Com que $p$ i $q$ són senars, de fet $p\equiv1\pmod{2q}$.

**Exercici 1.37d.** Per decidir si $M_{13}=8191$ és primer, $\sqrt{8191}\approx90.5$. Els candidats $p\equiv1\pmod{26}$ fins a $90$ són $53$ i $79$. Cap divideix $8191$, així que $M_{13}$ és primer.

Per $M_{17}=131071$, $\sqrt{131071}\approx362$. Els candidats $p\equiv1\pmod{34}$ són $103,137,239,307$ (a més de $1$, que no és primer). Cap divideix $131071$, així que $M_{17}$ és primer.

**Moraleja.** La propietat $p\equiv1\pmod q$ redueix dràsticament el nombre de divisions necessàries per testar $M_q$.

### 7.10 Primers i sumes de dos quadrats

**Exercici 1.18.** Si un primer senar $p$ s'escriu com $p=a^2+b^2$, llavors $p\equiv1\pmod4$.

**Demostració.** Els quadrats mòdul $4$ són $0$ i $1$. Com que $p$ és senar, $a$ i $b$ tenen paritat diferent: un és parell i l'altre senar. Per tant,
$$
a^2+b^2\equiv0+1=1\pmod4.
$$
El primer $2=1^2+1^2$ és l'excepció, i $2\equiv2\pmod4$.

### 7.11 Errors freqüents

- **Considerar $1$ com a primer.** No ho és.
- **Oblidar que $2$ és primer.** És l'únic parell.
- **Factoritzar sense incloure tots els primers.** Cal la mateixa llista de primers per comparar exponents; els que no apareixen tenen exponent $0$.
- **Confondre factorització i divisors.** Un divisor pot tenir exponents menors o iguals, no cal que sigui primer.
- **Testar la primalitat fins a $n/2$.** N'hi ha prou fins a $\sqrt n$.
- **Pensar que $M_q$ primer implica $q$ primer i recíprocament.** El recíproc és fals: $M_{11}=23\cdot89$.
- **Oblidar el signe** en factoritzar nombres negatius.

***
<a id="sec8"></a>
## 8. Congruències i aritmètica modular

### 8.1 Definició

Sigui $m>0$. Diem que $a$ és **congruent** amb $b$ mòdul $m$, i escrivim
$$
a\equiv b\pmod m,
$$
si $a-b$ és múltiple de $m$, és a dir, si existeix $k\in\mathbb Z$ amb
$$
a-b=km.
$$
Equivalentment:

- $m\mid(a-b)$;
- $a$ i $b$ tenen el mateix residu en dividir per $m$;
- $a=b+km$ per a algun $k\in\mathbb Z$.

**Exemples amb $m=5$.**

- $7\equiv2\pmod5$, perquè $7-2=5$.
- $-3\equiv2\pmod5$, perquè $-3-2=-5$.
- $7\equiv-3\pmod5$, perquè $7-(-3)=10$.
- $7\not\equiv3\pmod5$, perquè $7-3=4$ no és múltiple de $5$.

**Interpretació de "calaixos".** Els residus $0,1,\dots,m-1$ són els calaixos. Dos nombres són congruents si són al mateix calaix.

### 8.2 La congruència és una relació d'equivalència

Per a $m>0$, la relació $\equiv\pmod m$ sobre $\mathbb Z$ és:

1. **Reflexiva:** $a\equiv a\pmod m$, perquè $a-a=0=m\cdot0$.
2. **Simètrica:** si $a\equiv b$, llavors $b-a=-(a-b)$ també és múltiple de $m$, així que $b\equiv a$.
3. **Transitiva:** si $a\equiv b$ i $b\equiv c$, llavors
   $$
   a-c=(a-b)+(b-c)
   $$
   és suma de múltiples de $m$, i per tant múltiple de $m$. Així $a\equiv c$.

Per tant, $\equiv\pmod m$ parteix $\mathbb Z$ en classes d'equivalència disjuntes.

### 8.3 Compatibilitat amb les operacions

Si $a\equiv a_0\pmod m$ i $b\equiv b_0\pmod m$, llavors:

$$
a+b\equiv a_0+b_0\pmod m,
$$
$$
a-b\equiv a_0-b_0\pmod m,
$$
$$
ab\equiv a_0b_0\pmod m.
$$

**Demostració de la suma.** $(a+b)-(a_0+b_0)=(a-a_0)+(b-b_0)$, suma de múltiples de $m$.

**Demostració del producte.**
$$
ab-a_0b_0=a(b-b_0)+b_0(a-a_0),
$$
i els dos termes són múltiples de $m$.

**Conseqüències.**

- Es poden reduir els operands mòdul $m$ abans de sumar, restar o multiplicar.
- Les potències també es conserven:
  $$
  a\equiv b\pmod m \implies a^n\equiv b^n\pmod m
  $$
  per a tot $n\ge0$.
- Si $f(x)$ és un polinomi amb coeficients enters, llavors
  $$
  a\equiv b\pmod m \implies f(a)\equiv f(b)\pmod m.
  $$

**Atenció.** La congruència **no** és compatible amb la divisió en general. De $ab\equiv ac\pmod m$ no es pot concloure $b\equiv c\pmod m$ llevat que $a$ sigui invertible mòdul $m$.

### 8.4 Classes d'equivalència

La classe de $a$ mòdul $m$ és
$$
[a]_m=\{b\in\mathbb Z:a\equiv b\pmod m\}=a+m\mathbb Z.
$$
És el conjunt de tots els enters que donen el mateix residu que $a$.

**Exemple amb $m=5$:**
$$
[0]_5=\{\dots,-10,-5,0,5,10,\dots\},
$$
$$
[1]_5=\{\dots,-9,-4,1,6,11,\dots\},
$$
i així successivament.

**Propietat fonamental.**
$$
[a]_m=[b]_m \iff a\equiv b\pmod m.
$$
Per tant, qualsevol element de la classe pot representar-la.

**Conjunt quocient.**
$$
\mathbb Z/m\mathbb Z=\{[0]_m,[1]_m,\dots,[m-1]_m\}.
$$
Té exactament $m$ elements. Cada classe és un conjunt infinit, però el quocient és finit.

**Partició.**
$$
\mathbb Z=[0]_m\sqcup[1]_m\sqcup\cdots\sqcup[m-1]_m.
$$
Cada enter pertany exactament a una classe.

**Sistema complet de residus.** Un conjunt de $m$ enters, un per cada classe, és un **sistema complet de residus** mòdul $m$. El més habitual és $\{0,1,\dots,m-1\}$, però també es pot usar $\{1,\dots,m\}$ o representants negatius.

### 8.5 Aritmètica de classes

A $\mathbb Z/m\mathbb Z$ es defineixen:
$$
[a]_m+[b]_m=[a+b]_m,
\qquad
[a]_m[b]_m=[ab]_m.
$$
Aquestes operacions estan **ben definides**: no depenen dels representants triats. Si $[a]=[a_0]$ i $[b]=[b_0]$, llavors $a\equiv a_0$ i $b\equiv b_0$, i per compatibilitat
$$
a+b\equiv a_0+b_0,\qquad ab\equiv a_0b_0.
$$
Per tant, $[a+b]=[a_0+b_0]$ i $[ab]=[a_0b_0]$.

Amb aquestes operacions, $\mathbb Z/m\mathbb Z$ és un anell commutatiu amb unitat. Ho veurem a la secció 9.

### 8.6 Equacions lineals de congruències

L'equació
$$
ax\equiv b\pmod m
$$
es resol així:

1. Calculeu $d=\operatorname{mcd}(a,m)$.
2. Si $d\nmid b$, **no hi ha solució**.
3. Si $d\mid b$, dividiu per $d$:
   $$
   a'x\equiv b'\pmod{m'},\qquad
   a'=\frac ad,\ b'=\frac bd,\ m'=\frac md.
   $$
   Ara $\operatorname{mcd}(a',m')=1$, així que $a'$ és invertible mòdul $m'$.
4. Trobeu l'invers $(a')^{-1}$ mòdul $m'$ i obteniu
   $$
   x\equiv x_0=(a')^{-1}b'\pmod{m'}.
   $$
5. Mòdul $m$, hi ha exactament $d$ solucions:
   $$
   x=x_0+km',\qquad k=0,1,\dots,d-1.
   $$

**Demostració de la condició.** Si $ax\equiv b\pmod m$, llavors $m\mid ax-b$. Com que $d\mid m$ i $d\mid a$, tenim $d\mid b$. Recíprocament, si $d\mid b$, la congruència reduïda té solució perquè $a'$ és invertible mòdul $m'$.

**Exemples.**

- $31x\equiv1\pmod{101}$: $\operatorname{mcd}(31,101)=1$; l'invers és $88$, així que $x\equiv88$.
- $4x\equiv0\pmod{18}$: $d=2$, $m'=9$; $2x\equiv0\pmod9$, així que $x\equiv0\pmod9$. Solucions mòdul $18$: $x=0,9$.
- $6x\equiv0\pmod{30}$: $d=6$, $m'=5$; $x\equiv0\pmod5$. Solucions mòdul $30$: $0,5,10,15,20,25$.
- $2x\equiv7\pmod{10}$: $d=2\nmid7$, no hi ha solució.
- $2x\equiv6\pmod{10}$: $d=2$, $x\equiv3\pmod5$, solucions $x=3,8$.

**Nombre de solucions.** Si $d\mid b$, hi ha exactament $d$ solucions mòdul $m$. Si $d\nmid b$, cap.

### 8.7 Sistemes de congruències i mcm

Si
$$
x\equiv a\pmod m
\qquad\text{i}\qquad
x\equiv b\pmod n,
$$
llavors $x-a$ és múltiple de $m$ i $x-b$ és múltiple de $n$. En particular, si hi ha solució, aleshores
$$
a\equiv b\pmod{\operatorname{mcd}(m,n)}.
$$
Aquesta és la **condició de compatibilitat**.

Si la condició es compleix, el sistema té solució única mòdul
$$
\operatorname{mcm}(m,n).
$$
No cal que $m$ i $n$ siguin coprimers; per exemple,
$$
x\equiv1\pmod4,\qquad x\equiv3\pmod6
$$
és compatible perquè $1\equiv3\pmod2$, i la solució és $x\equiv9\pmod{12}$.

**Demostració.** De $x\equiv a\pmod m$ i $x\equiv b\pmod n$ obtenim $a-b=(x-b)-(x-a)$, que és múltiple de $\operatorname{mcd}(m,n)$. Recíprocament, la condició és suficient (es pot demostrar reduint a potències de primers o amb el CRT general).

**Sistemes amb més de dues congruències.** La condició general és
$$
a_i\equiv a_j\pmod{\operatorname{mcd}(m_i,m_j)}
\qquad\text{per a tots }i,j.
$$
Si es compleix, hi ha solució única mòdul $\operatorname{mcm}(m_1,\dots,m_n)$.

### 8.8 Inclusions i interseccions de classes

Algunes propietats útils (exercici 1.38):

1. **Inclusió:**
   $$
   [a]_{2m}\subseteq[a]_m.
   $$
   Si $x\equiv a\pmod{2m}$, llavors $x-a=2mk=m(2k)$, així que $x\equiv a\pmod m$. La inclusió és estricta: $a+m\in[a]_m$, però $a+m\notin[a]_{2m}$.

2. **Intersecció:**
   $$
   [a]_m\cap[b]_m\ne\varnothing \iff a\equiv b\pmod m.
   $$
   Si hi ha un element comú $c$, llavors $c\equiv a$ i $c\equiv b$, així que $a\equiv b$.

3. **Intersecció amb mòduls diferents:** si
   $$
   [a]_m\cap[b]_{2m}\ne\varnothing,
   $$
   llavors $[b]_{2m}\subseteq[a]_m$, però no necessàriament $[a]_{2m}=[b]_{2m}$. Contraexemple: $m=3$, $a=0$, $b=3$; les classes $[0]_3$ i $[3]_6$ s'intersecten (per exemple a $3$), però no són iguals.

### 8.9 Errors freqüents

- **Cancel·lar sense invertibilitat.** De $2\cdot2\equiv2\cdot(-1)\pmod6$ no es pot concloure $2\equiv-1\pmod6$.
- **Dividir per un nombre no invertible.** A $\mathbb Z/6\mathbb Z$, no es pot dividir per $2$.
- **Pensar que $a\equiv b\pmod m$ implica $a=b$.** Només implica que difereixen en un múltiple de $m$.
- **Reduir l'exponent mòdul $m$.** L'exponent s'ha de reduir mòdul $\varphi(m)$ (si la base és coprimera amb $m$) o mòdul l'ordre, no mòdul $m$.
- **Oblidar que $m=1$ és un cas trivial.** Tots els enters són congruents mòdul $1$.
- **Confondre el residu amb el quocient.** $a\bmod m$ és el residu, no $a/m$.

***

<a id="sec9"></a>
## 9. L'anell $\mathbb Z/m\mathbb Z$

### 9.1 Operacions i estructura

A
$$
\mathbb Z/m\mathbb Z=\{[0],[1],\dots,[m-1]\}
$$
definim
$$
[a]+[b]=[a+b],\qquad [a][b]=[ab].
$$
Aquestes operacions estan ben definides (secció 8) i compleixen els axiomes d'anell commutatiu amb unitat:

- neutre de la suma: $[0]$;
- oposat de $[a]$: $[-a]$;
- neutre del producte: $[1]$;
- distributivitat, associativitat i commutativitat.

L'element $[0]$ és el zero i $[1]$ és la unitat. Si $m>1$, $[0]\ne[1]$.

**Característica.** $m[1]=[m]=[0]$, i $m$ és el menor enter positiu amb aquesta propietat. Així, $\mathbb Z/m\mathbb Z$ té característica $m$.

### 9.2 Unitats

**Proposició.** $[a]_m$ és invertible si i només si
$$
\operatorname{mcd}(a,m)=1.
$$

**Demostració.**

- $(\Rightarrow)$ Si $[a]$ és invertible, existeix $[x]$ amb $[a][x]=[1]$. Això vol dir $ax\equiv1\pmod m$, és a dir, $ax-1=km$ per a algun $k$. Així
  $$
  ax+(-k)m=1,
  $$
  i per Bézout $\operatorname{mcd}(a,m)=1$.
- $(\Leftarrow)$ Si $\operatorname{mcd}(a,m)=1$, per Bézout existeixen $\alpha,\beta$ amb $\alpha a+\beta m=1$. Reduint mòdul $m$, $\alpha a\equiv1$, així que $[a]^{-1}=[\alpha]$.

**Conseqüència.** El nombre d'unitats de $\mathbb Z/m\mathbb Z$ és $\varphi(m)$.

**Exemples.**

- A $\mathbb Z/5\mathbb Z$, tot element no nul és invertible: $1^{-1}=1$, $2^{-1}=3$, $3^{-1}=2$, $4^{-1}=4$.
- A $\mathbb Z/6\mathbb Z$, les unitats són $[1]$ i $[5]$; $[5]^{-1}=[5]$.
- A $\mathbb Z/8\mathbb Z$, les unitats són $[1],[3],[5],[7]$; cadascuna és el seu propi invers? $3\cdot3=9\equiv1$, $5\cdot5=25\equiv1$, $7\cdot7=49\equiv1$. Sí.

### 9.3 Divisors de zero

**Proposició.** Si $m>1$ i $[a]\ne[0]$ no és invertible, aleshores $[a]$ és un divisor de zero: existeix $[b]\ne[0]$ amb
$$
[a][b]=[0].
$$

**Demostració.** Si $[a]$ no és invertible, $\operatorname{mcd}(a,m)=d>1$. Escrivim $a=da'$ i $m=dn$ amb $n=m/d$. Com que $d>1$, tenim $0<n<m$ (si $d=m$, llavors $[a]=[0]$, cas que hem exclòs). Aleshores
$$
[a][n]=[an]=[da'n]=[a'm]=[0],
$$
i $[n]\ne[0]$ perquè $0<n<m$.

**Exemple amb $m=6$.**

- $[2][3]=[6]=[0]$, amb $[2],[3]\ne[0]$.
- $[3][2]=[0]$.
- $[4][3]=[12]=[0]$.

A $\mathbb Z/6\mathbb Z$, els elements no nuls no invertibles són $[2],[3],[4]$, i tots són divisors de zero.

**Atenció.** El zero $[0]$ no es considera divisor de zero en aquesta definició, tot i que $[0][b]=[0]$ per a tot $b$.

### 9.4 Quan $\mathbb Z/m\mathbb Z$ és un cos?

**Teorema.** Per a $m>1$,
$$
\mathbb Z/m\mathbb Z \text{ és un cos} \iff m \text{ és primer}.
$$

**Demostració.**

- $(\Rightarrow)$ Si $\mathbb Z/m\mathbb Z$ és un cos, tot element no nul és invertible. Si $m$ no fos primer, $m=dn$ amb $1<d<m$. Llavors $[d]\ne[0]$, però $\operatorname{mcd}(d,m)=d>1$, així que $[d]$ no seria invertible. Contradicció.
- $(\Leftarrow)$ Si $m$ és primer i $[a]\ne[0]$, llavors $m\nmid a$. Com que $m$ és primer, $\operatorname{mcd}(a,m)=1$, i per la proposició anterior $[a]$ és invertible. Per tant, tot element no nul té invers, i l'anell és un cos.

**Notació.** Quan $p$ és primer, escrivim
$$
\mathbb F_p=\mathbb Z/p\mathbb Z.
$$

**Exemples.**

- $\mathbb F_5$ és un cos.
- $\mathbb F_7$ és un cos.
- $\mathbb Z/6\mathbb Z$ no és un cos: $[2]$ no és invertible.
- $\mathbb Z/4\mathbb Z$ no és un cos: $[2]$ és divisor de zero i no invertible.

### 9.5 Llei de cancel·lació

**Proposició.**

1. Si $[a]$ és invertible, llavors
   $$
   [a][b]=[a][c]\implies[b]=[c].
   $$
2. Si $[a]$ no és invertible, la cancel·lació pot fallar.

**Demostració de (1).** Multiplicant per $[a]^{-1}$:
$$
[a]^{-1}[a][b]=[a]^{-1}[a][c]
\implies[1][b]=[1][c]
\implies[b]=[c].
$$

**Contraexemple de (2).** A $\mathbb Z/6\mathbb Z$:
$$
[2][0]=[0]=[2][3],
$$
però $[0]\ne[3]$. No podem cancel·lar $[2]$ perquè no és invertible.

**Conseqüència.** En $\mathbb Z/m\mathbb Z$, la cancel·lació per $[a]$ és vàlida si i només si $\operatorname{mcd}(a,m)=1$.

### 9.6 Taula d'unitats i divisors de zero

| $m$ | Unitats | $\varphi(m)$ | Cos? | Divisors de zero (representants no nuls) |
|---|---|---:|---|---|
| $2$ | $\{1\}$ | $1$ | Sí | cap |
| $3$ | $\{1,2\}$ | $2$ | Sí | cap |
| $4$ | $\{1,3\}$ | $2$ | No | $2$ |
| $5$ | $\{1,2,3,4\}$ | $4$ | Sí | cap |
| $6$ | $\{1,5\}$ | $2$ | No | $2,3,4$ |
| $7$ | $\{1,\dots,6\}$ | $6$ | Sí | cap |
| $8$ | $\{1,3,5,7\}$ | $4$ | No | $2,4,6$ |
| $9$ | $\{1,2,4,5,7,8\}$ | $6$ | No | $3,6$ |
| $10$ | $\{1,3,7,9\}$ | $4$ | No | $2,4,5,6,8$ |
| $11$ | $\{1,\dots,10\}$ | $10$ | Sí | cap |
| $12$ | $\{1,5,7,11\}$ | $4$ | No | $2,3,4,6,8,9,10$ |

Aquesta taula resumeix l'exercici 1.19 i ajuda a detectar errors.

### 9.7 Estructura via teorema xinès del residu

Si
$$
m=p_1^{e_1}p_2^{e_2}\cdots p_r^{e_r},
$$
amb $p_i$ primers diferents, llavors
$$
\mathbb Z/m\mathbb Z
\cong
\mathbb Z/p_1^{e_1}\mathbb Z\times\cdots\times\mathbb Z/p_r^{e_r}\mathbb Z.
$$
Aquesta descomposició és el teorema xinès del residu (secció 10). Permet:

- reduir operacions mòdul $m$ a operacions mòdul cada potència de primer;
- comptar unitats: $\varphi(m)=\prod\varphi(p_i^{e_i})$;
- analitzar divisors de zero i nilpotents;
- resoldre sistemes component a component.

**Nilpotents.** A $\mathbb Z/p^e\mathbb Z$, l'element $[p]$ és nilpotent:
$$
[p]^e=[p^e]=[0].
$$
Això no passa en un cos.

### 9.8 Errors freqüents

- **Cancel·lar un element no invertible.** És l'error més habitual.
- **Pensar que tot element no nul és invertible.** Només si $m$ és primer.
- **Pensar que $\mathbb Z/m\mathbb Z$ és un cos per a tot $m$ primer.** Sí, però per a $m$ compost no.
- **Confondre $[0]$ amb l'element neutre del producte.** $[0]$ és el zero; $[1]$ és la unitat.
- **Oblidar que $[a]=[b]$ si $a\equiv b$.** Les classes no són nombres; són conjunts.
- **Tractar $\mathbb Z/m\mathbb Z$ com un cos en resoldre sistemes.** Si $m$ no és primer, el determinant no nul no garanteix invertibilitat.

***
<a id="sec10"></a>
## 10. Teorema xinès del residu (CRT)

### 10.1 Motivació

El problema clàssic de Sun Tsu Suan-Ching (segle IV) diu:

> Tenim un conjunt d'objectes. Si els comptem de tres en tres, en sobren dos; si els comptem de cinc en cinc, en sobren tres; si els comptem de set en set, en sobren dos. Quants objectes hi ha?

En llenguatge modern:
$$
x\equiv2\pmod3,\qquad
x\equiv3\pmod5,\qquad
x\equiv2\pmod7.
$$
El teorema xinès del residu garanteix que hi ha una solució única mòdul $3\cdot5\cdot7=105$.

### 10.2 Enunciat

**Teorema (CRT).** Siguin $m_1,\dots,m_n>1$ enters **coprimers dos a dos**:
$$
\operatorname{mcd}(m_i,m_j)=1\qquad\text{per a }i\ne j.
$$
Siguin $a_1,\dots,a_n\in\mathbb Z$. Aleshores el sistema
$$
\begin{cases}
x\equiv a_1\pmod{m_1},\\
x\equiv a_2\pmod{m_2},\\
\quad\vdots\\
x\equiv a_n\pmod{m_n}
\end{cases}
$$
té una solució, i és **única mòdul**
$$
M=m_1m_2\cdots m_n.
$$
És a dir, totes les solucions són de la forma
$$
x=x_0+kM,\qquad k\in\mathbb Z.
$$

### 10.3 Demostració

**Existència (constructiva).** Per a cada $i$, definim
$$
M_i=\frac{M}{m_i}.
$$
Com que els $m_j$ són coprimers dos a dos, $\operatorname{mcd}(M_i,m_i)=1$. Per tant, $M_i$ té invers mòdul $m_i$; sigui $y_i$ amb
$$
M_i y_i\equiv1\pmod{m_i}.
$$
Definim
$$
x=\sum_{i=1}^n a_i M_i y_i.
$$
Aleshores, per a cada $j$:
- si $i=j$, el terme $a_jM_jy_j\equiv a_j\pmod{m_j}$;
- si $i\ne j$, llavors $m_j\mid M_i$ (perquè $M_i$ conté el factor $m_j$), així que el terme $a_iM_iy_i\equiv0\pmod{m_j}$.

Per tant,
$$
x\equiv a_j\pmod{m_j}
$$
per a tot $j$.

**Unicitat.** Si $x$ i $x'$ són dues solucions, llavors
$$
x\equiv x'\pmod{m_i}
$$
per a tot $i$. Així, cada $m_i$ divideix $x-x'$. Com que els $m_i$ són coprimers dos a dos, el seu producte $M$ també divideix $x-x'$ (per inducció: si $m_1\mid N$ i $m_2\mid N$ amb $\operatorname{mcd}(m_1,m_2)=1$, llavors $m_1m_2\mid N$). Per tant, $x\equiv x'\pmod M$.

### 10.4 Mètode de substitucions successives

És el mètode més pràctic per resoldre a mà.

1. Agafeu la primera congruència:
   $$
   x=a_1+m_1k.
   $$
2. Substituïu a la segona congruència i resoleu per a $k$:
   $$
   a_1+m_1k\equiv a_2\pmod{m_2}.
   $$
   Com que $\operatorname{mcd}(m_1,m_2)=1$, $m_1$ és invertible mòdul $m_2$.
3. Obteniu $k=k_0+m_2t$, i per tant
   $$
   x=a_1+m_1k_0+m_1m_2t.
   $$
4. Repetiu amb la tercera congruència, etc.
5. Al final obteniu
   $$
   x=x_0+M t.
   $$

**Exemple (Sun Tsu).** Resolem
$$
x\equiv2\pmod3,\qquad x\equiv3\pmod5,\qquad x\equiv2\pmod7.
$$

**Pas 1.** $x=2+3k$. Imposem mòdul $5$:
$$
2+3k\equiv3\pmod5
\implies3k\equiv1\pmod5.
$$
Com que $3^{-1}\equiv2\pmod5$,
$$
k\equiv2\pmod5.
$$
Així $k=2+5t$, i
$$
x=2+3(2+5t)=8+15t.
$$

**Pas 2.** Imposem mòdul $7$:
$$
8+15t\equiv2\pmod7.
$$
Com que $8\equiv1$ i $15\equiv1$,
$$
1+t\equiv2\pmod7
\implies t\equiv1\pmod7.
$$
Així $t=1+7s$, i
$$
x=8+15(1+7s)=23+105s.
$$
Per tant,
$$
\boxed{x\equiv23\pmod{105}}.
$$
Comprovació: $23\equiv2\pmod3$, $23\equiv3\pmod5$, $23\equiv2\pmod7$.

### 10.5 Fórmula directa

Amb la notació anterior:
$$
\boxed{x\equiv\sum_{i=1}^n a_iM_iy_i\pmod M,}
$$
on
$$
M=\prod_{i=1}^n m_i,\qquad
M_i=\frac{M}{m_i},\qquad
y_i\equiv M_i^{-1}\pmod{m_i}.
$$
Aquesta fórmula és útil quan hi ha poques congruències i els inversos són fàcils de calcular.

**Exemple.** Per al sistema anterior:
$$
M=105,\quad M_1=35,\quad M_2=21,\quad M_3=15.
$$
Inversos:
$$
35\equiv2\pmod3,\quad 2^{-1}\equiv2\pmod3,\quad y_1=2;
$$
$$
21\equiv1\pmod5,\quad y_2=1;
$$
$$
15\equiv1\pmod7,\quad y_3=1.
$$
Aleshores
$$
x\equiv2\cdot35\cdot2+3\cdot21\cdot1+2\cdot15\cdot1
=140+63+30=233\equiv23\pmod{105}.
$$

### 10.6 Unicitat i relació amb la bijecció

El CRT també es pot formular com una **bijecció**:
$$
\varphi:\mathbb Z/M\mathbb Z
\longrightarrow
\mathbb Z/m_1\mathbb Z\times\cdots\times\mathbb Z/m_n\mathbb Z,
$$
$$
[a]_M\longmapsto([a]_{m_1},\dots,[a]_{m_n}).
$$
Si els $m_i$ són coprimers dos a dos, $\varphi$ és un isomorfisme d'anells.

**Injectivitat.** Si $\varphi([a])=\varphi([b])$, llavors $a\equiv b\pmod{m_i}$ per a tot $i$. Com que els $m_i$ són coprimers dos a dos, $M\mid a-b$, així que $[a]_M=[b]_M$.

**Surjectivitat.** Donat $(a_1,\dots,a_n)$, el CRT proporciona un $x$ amb $x\equiv a_i\pmod{m_i}$; per tant, $\varphi([x])=(a_1,\dots,a_n)$.

**Conseqüència (exercici 1.26).** Si els $m_i$ són coprimers dos a dos i $M=\prod m_i$, llavors
$$
a\equiv b\pmod M
\iff
a\equiv b\pmod{m_i}\ \text{per a tot }i.
$$

**Quan els mòduls no són coprimers.** La mateixa aplicació pot ser injectiva però no exhaustiva. Si $M=\operatorname{mcm}(m_1,\dots,m_n)$, la imatge té $M$ elements, però el codomini pot tenir més. Per exemple, a l'exercici 1.27:
$$
f:\mathbb Z/18\mathbb Z\to\mathbb Z/2\mathbb Z\times\mathbb Z/6\mathbb Z\times\mathbb Z/9\mathbb Z
$$
és injectiva però no exhaustiva, perquè $2,6,9$ no són coprimers dos a dos i el codomini té $108$ elements. En canvi,
$$
g:\mathbb Z/18\mathbb Z\to\mathbb Z/2\mathbb Z\times\mathbb Z/9\mathbb Z
$$
és bijectiva perquè $2$ i $9$ són coprimers.

### 10.7 CRT general per a mòduls no coprimers

**Teorema (CRT general).** El sistema
$$
x\equiv a_i\pmod{m_i},\qquad i=1,\dots,n,
$$
té solució si i només si
$$
a_i\equiv a_j\pmod{\operatorname{mcd}(m_i,m_j)}
\qquad\text{per a tots }i,j.
$$
Si hi ha solució, és única mòdul
$$
M=\operatorname{mcm}(m_1,\dots,m_n).
$$

**Idea de demostració.** Es descompon cada $m_i$ en potències de primers. Per a cada primer $p$, les congruències que involucren $p$ han de ser compatibles; la condició $a_i\equiv a_j\pmod{\operatorname{mcd}(m_i,m_j)}$ és exactament la compatibilitat per a cada primer. Aleshores es combinen les solucions de cada primer amb el CRT.

**Exemple sense solució.**
$$
x\equiv0\pmod2,\qquad x\equiv1\pmod4.
$$
Aquí $\operatorname{mcd}(2,4)=2$, però $0\not\equiv1\pmod2$, així que no hi ha solució.

**Exemple amb solució.**
$$
x\equiv1\pmod4,\qquad x\equiv3\pmod6.
$$
$\operatorname{mcd}(4,6)=2$ i $1\equiv3\pmod2$, així que hi ha solució. La solució és $x\equiv9\pmod{12}$.

### 10.8 Cas homogeni

Si
$$
a_1=a_2=\cdots=a_n=0,
$$
el sistema és
$$
x\equiv0\pmod{m_i}\quad\text{per a tot }i.
$$
Això vol dir que $x$ és múltiple de cada $m_i$, i per tant múltiple de
$$
M=\operatorname{mcm}(m_1,\dots,m_n).
$$
La solució és
$$
x\equiv0\pmod M.
$$
Aquest sistema sempre té solució, independentment de si els mòduls són coprimers o no. La unicitat mòdul $M$ és la de l'observació general.

### 10.9 Aplicacions

1. **Resoldre sistemes de congruències.** És l'ús directe.
2. **Calcular mòdul un nombre compost.** Es descompon $m$ en potències de primers i es treballa component a component.
3. **Multiplicativitat de $\varphi$.** Si $\operatorname{mcd}(m,n)=1$, llavors
   $$
   \varphi(mn)=\varphi(m)\varphi(n),
   $$
   perquè $U(mn)\cong U(m)\times U(n)$ via CRT.
4. **Matrius mòdul $m$.** La invertibilitat i els sistemes es poden analitzar component a component mòdul cada potència de primer.
5. **Càlculs grans.** Per exemple, per calcular $2022^{20222022}\pmod{21}$, es calcula mòdul $3$ i mòdul $7$ i es recombina.

**Exemple (exercici 1.34).** Volem $2022^{20222022}\pmod{21}$.
- Mòdul $3$: $2022\equiv0$, així que el resultat és $0$.
- Mòdul $7$: $2022\equiv-1$, i l'exponent és parell, així que el resultat és $1$.

Resolem
$$
N\equiv0\pmod3,\qquad N\equiv1\pmod7.
$$
De $N=3k$: $3k\equiv1\pmod7$, i $3^{-1}\equiv5$, així que $k\equiv5\pmod7$. Per tant,
$$
N\equiv15\pmod{21}.
$$

### 10.10 Errors freqüents

- **No comprovar que els mòduls són coprimers dos a dos.** El CRT clàssic els necessita.
- **Confondre coprimers dos a dos amb coprimers en conjunt.** Per exemple, $6,10,15$ tenen $\operatorname{mcd}(6,10,15)=1$, però no són coprimers dos a dos: $\operatorname{mcd}(6,10)=2$. El CRT clàssic no s'aplica directament.
- **Usar $M=\prod m_i$ quan els mòduls no són coprimers.** Cal usar $M=\operatorname{mcm}(m_i)$.
- **Oblidar la condició de compatibilitat.** Si els mòduls no són coprimers, no n'hi ha prou que cada congruència tingui solució.
- **Pensar que la solució és única en $\mathbb Z$.** És única mòdul $M$; hi ha infinites solucions $x_0+kM$.
- **Equivocar els inversos $y_i$.** Comproveu que $M_iy_i\equiv1\pmod{m_i}$.

***

<a id="sec11"></a>
## 11. Teoremes de Fermat i Euler

### 11.1 Petit teorema de Fermat

**Teorema (Fermat).** Si $p$ és primer i $p\nmid a$, llavors
$$
\boxed{a^{p-1}\equiv1\pmod p.}
$$
Equivalentment, per a tot $a\in\mathbb Z$,
$$
\boxed{a^p\equiv a\pmod p.}
$$

**Demostració (permutació de residus).** Els residus no nuls mòdul $p$ són
$$
1,2,\dots,p-1.
$$
Multiplicar per $a$ (amb $p\nmid a$) dóna una permutació d'aquest conjunt, perquè si $ai\equiv aj\pmod p$, llavors $i\equiv j$ cancel·lant $a$ (invertible). Per tant,
$$
\prod_{i=1}^{p-1}(ai)\equiv\prod_{i=1}^{p-1}i\pmod p.
$$
El costat esquerre és $a^{p-1}(p-1)!$, i el dret és $(p-1)!$. Com que $(p-1)!$ és invertible mòdul $p$, podem cancel·lar:
$$
a^{p-1}\equiv1\pmod p.
$$
Multiplicant per $a$ s'obté $a^p\equiv a$.

**Cas $p\mid a$.** Si $p\mid a$, llavors $a\equiv0\pmod p$, i $a^p\equiv0\equiv a\pmod p$. La versió $a^p\equiv a$ val per a tot $a$; la versió $a^{p-1}\equiv1$ només si $p\nmid a$.

### 11.2 Funció $\varphi$ d'Euler

**Definició.**
$$
\varphi(n)=|\{1\le k\le n:\operatorname{mcd}(k,n)=1\}|.
$$
És el nombre d'enters positius fins a $n$ que són coprimers amb $n$. Equivalentment, és el nombre d'unitats de $\mathbb Z/n\mathbb Z$:
$$
\varphi(n)=|U(n)|.
$$

**Propietats.**

1. $\varphi(1)=1$.
2. Si $p$ és primer, $\varphi(p)=p-1$.
3. Si $p$ és primer i $e\ge1$,
   $$
   \varphi(p^e)=p^e-p^{e-1}=p^{e-1}(p-1).
   $$
4. Si $\operatorname{mcd}(m,n)=1$,
   $$
   \varphi(mn)=\varphi(m)\varphi(n).
   $$
5. En general,
   $$
   \varphi(n)=n\prod_{p\mid n}\left(1-\frac1p\right),
   $$
   on el producte recorre els primers que divideixen $n$.
6. $\varphi(n)$ és parell per a $n>2$.
7. $\sum_{d\mid n}\varphi(d)=n$.

**Demostració de la fórmula per a $p^e$.** Els nombres $1,\dots,p^e$ que **no** són coprimers amb $p^e$ són els múltiples de $p$:
$$
p,2p,\dots,p^{e-1}p=p^e.
$$
N'hi ha $p^{e-1}$. Per tant,
$$
\varphi(p^e)=p^e-p^{e-1}.
$$

**Demostració de la multiplicativitat.** Si $\operatorname{mcd}(m,n)=1$, el CRT dóna una bijecció
$$
U(mn)\cong U(m)\times U(n).
$$
Per tant, $|U(mn)|=|U(m)||U(n)|$, és a dir, $\varphi(mn)=\varphi(m)\varphi(n)$.

**Exemples (exercici 1.35).**

- $\varphi(128)=\varphi(2^7)=2^7-2^6=128-64=64$.
- $1123$ és primer, així que $\varphi(1123)=1122$.
- $1125=3^2\cdot5^3$:
  $$
  \varphi(1125)=\varphi(3^2)\varphi(5^3)=3\cdot2\cdot25\cdot4=600.
  $$
- $29270241=3^4\cdot7\cdot11\cdot13\cdot19^2$:
  $$
  \varphi(29270241)=54\cdot6\cdot10\cdot12\cdot342=13\,296\,960.
  $$
- $12648925575=3^4\cdot5^2\cdot11^3\cdot13\cdot19^2$:
  $$
  \varphi(12648925575)=54\cdot20\cdot1210\cdot12\cdot342
  =5\,363\,107\,200.
  $$

### 11.3 Teorema d'Euler

**Teorema (Euler).** Si $\operatorname{mcd}(a,m)=1$, llavors
$$
\boxed{a^{\varphi(m)}\equiv1\pmod m.}
$$

**Demostració (permutació d'unitats).** Sigui $U(m)$ el conjunt d'unitats mòdul $m$. Multiplicar per $a$ (que és unitat) dóna una bijecció de $U(m)$ en si mateix. Per tant, el producte de tots els elements de $U(m)$ és congruent amb el producte de tots els elements multiplicats per $a$:
$$
\prod_{u\in U(m)}(au)\equiv\prod_{u\in U(m)}u\pmod m.
$$
El costat esquerre és $a^{\varphi(m)}$ vegades el producte de les unitats. Com que aquest producte és invertible mòdul $m$, es cancel·la i s'obté
$$
a^{\varphi(m)}\equiv1\pmod m.
$$

**Demostració alternativa (Lagrange).** $U(m)$ és un grup finit d'ordre $\varphi(m)$. Per Lagrange, l'ordre de $a$ divideix $\varphi(m)$; per tant, $a^{\varphi(m)}=1$.

**Cas particular.** Si $m=p$ és primer, $\varphi(p)=p-1$, i recuperem Fermat.

### 11.4 Ordre d'un element

Si $\operatorname{mcd}(a,m)=1$, l'**ordre** de $a$ mòdul $m$ és el menor enter $k>0$ tal que
$$
a^k\equiv1\pmod m.
$$
S'escriu $\operatorname{ord}_m(a)$.

Propietats:

1. $\operatorname{ord}_m(a)$ existeix i divideix $\varphi(m)$.
2. $a^r\equiv a^s\pmod m$ si i només si
   $$
   r\equiv s\pmod{\operatorname{ord}_m(a)}.
   $$
3. En particular, si $r\equiv s\pmod{\varphi(m)}$, llavors $a^r\equiv a^s\pmod m$ (quan $\operatorname{mcd}(a,m)=1$).
4. L'ordre pot ser més petit que $\varphi(m)$. Per exemple, mòdul $8$, tots els elements senars tenen ordre $1$ o $2$, mentre que $\varphi(8)=4$.

**Com calcular l'ordre.** Es factoritza $\varphi(m)$ i es prova dividir l'exponent per cada factor primer; es busca el menor divisor $k$ de $\varphi(m)$ amb $a^k\equiv1$. En exercicis petits, sovint n'hi ha prou de calcular les potències successives fins que es repeteixi $1$.

**Exemple (exercici 1.37c).** Si $2^q\equiv1\pmod p$ i $q$ és primer, llavors $\operatorname{ord}_p(2)\mid q$, així que l'ordre és $1$ o $q$. Com que $1$ és impossible, l'ordre és $q$. Per Fermat, $q\mid p-1$.

### 11.5 Exponenciació ràpida

Per calcular $a^e\bmod m$ amb $e$ gran, no es fan $e$ multiplicacions. S'usa el mètode binari:

```text
potencia_mod(a, e, m):
    resultat = 1
    base = a mod m
    while e > 0:
        if e odd:
            resultat = (resultat * base) mod m
        base = (base * base) mod m
        e = e // 2
    return resultat
```

**Complexitat.** $O(\log e)$ multiplicacions mòdul $m$.

**Exemple.** $3^{1243}\bmod100$:
$$
3^{20}\equiv1\pmod{100},
\qquad
1243=20\cdot62+3,
$$
$$
3^{1243}\equiv(3^{20})^{62}\cdot3^3\equiv1\cdot27=27\pmod{100}.
$$
Els dos últims dígits de $103^{1243}$ són $27$.

**Exemple (exercici 1.29).**

- $513^{1017}\pmod6$: $513\equiv3$, i $3^n\equiv3\pmod6$ per a $n\ge1$. Resultat: $3$.
- $2^{154}\pmod5$: $2^4\equiv1$, $154=4\cdot38+2$, així que $2^{154}\equiv2^2=4$.
- $3^{178}\pmod{12}$: $3^2=9$, $3^3\equiv3$, $3^4\equiv9$; per a $n\ge2$, $3^n\equiv3$ si $n$ és senar i $9$ si $n$ és parell. $178$ és parell, així que $9$.

### 11.6 Advertència: reduir l'exponent

**Error greu:**
$$
r\equiv s\pmod m \;\not\Rightarrow\; a^r\equiv a^s\pmod m.
$$
**Contraexemple.** $m=5$, $a=2$, $r=1$, $s=6$:
$$
1\equiv6\pmod5,
$$
però
$$
2^1=2\not\equiv2^6=64\equiv4\pmod5.
$$

**Regla correcta.** Si $\operatorname{mcd}(a,m)=1$, es pot reduir l'exponent mòdul $\operatorname{ord}_m(a)$, i en particular mòdul $\varphi(m)$:
$$
a^r\equiv a^s\pmod m
\quad\text{si}\quad
r\equiv s\pmod{\varphi(m)}.
$$
Si no es coneix l'ordre, $\varphi(m)$ és una cota segura.

**Si $\operatorname{mcd}(a,m)\ne1$.** No es pot aplicar Euler. Per exemple, $2^{\varphi(4)}=2^2=4\equiv0\pmod4$, no $1$. En aquests casos:

- es pot calcular directament si l'exponent és petit;
- es pot usar el CRT i analitzar cada potència de primer;
- sovint la successió $a^n\bmod m$ esdevé periòdica després d'un prefix; es pot detectar el cicle.

**Exercici 1.38 (y).** La implicació
$$
r\equiv s\pmod p \implies a^{r-1}\equiv a^{s-1}\pmod p
$$
és falsa. Contraexemple: $p=5$, $a=2$, $r=1$, $s=6$; $1\equiv6\pmod5$, però $2^0=1$ i $2^5=32\equiv2$. La versió correcta és amb $r\equiv s\pmod{p-1}$ i $p\nmid a$.

### 11.7 Aplicacions

**Invers modular.**

- Si $p$ és primer i $p\nmid a$:
  $$
  a^{-1}\equiv a^{p-2}\pmod p.
  $$
- Si $\operatorname{mcd}(a,m)=1$:
  $$
  a^{-1}\equiv a^{\varphi(m)-1}\pmod m.
  $$
  Aquesta fórmula és més lenta que Bézout per a càlculs manuals, però útil en criptografia.

**Exercici 1.28.** $37^{55}\cdot53^{13}\pmod{98}$. Com que $53\equiv37^{-1}$,
$$
37^{55}\cdot53^{13}\equiv37^{55}\cdot37^{-13}=37^{42}\pmod{98}.
$$
$\varphi(98)=\varphi(2)\varphi(49)=1\cdot42=42$, i $\operatorname{mcd}(37,98)=1$, així que per Euler
$$
37^{42}\equiv1\pmod{98}.
$$
Resultat: $1$.

**Exercici 1.33.** Resoldre $2^{2021}(x-2^{2022})\equiv4^{2023}\pmod{13}$. Com que $\varphi(13)=12$, es redueixen els exponents mòdul $12$:
$$
2^{2021}\equiv2^5\equiv6,\qquad
2^{2022}\equiv2^6\equiv-1,\qquad
4^{2023}=2^{4046}\equiv2^2=4.
$$
L'equació queda $6(x+1)\equiv4\pmod{13}$, i $6^{-1}\equiv11$, així que
$$
x+1\equiv44\equiv5\pmod{13}
\implies x\equiv4\pmod{13}.
$$

**Exercici 1.34.** $2022^{20222022}\pmod{19}$. $2022\equiv8$, i
$$
8^2\equiv7,\qquad8^3\equiv-1\pmod{19},
$$
així que $8^6\equiv1$. Com que $20222022$ és múltiple de $6$, el resultat és $1$. Per a mòdul $21$, s'usa CRT com hem vist.

**Exercici 1.31.** $10^n+3$ múltiple de $7$. Com que $10\equiv3$,
$$
3^n+3\equiv0\pmod7
\implies3^n\equiv4\pmod7.
$$
Les potències de $3$ mòdul $7$ són $3,2,6,4,5,1$, amb període $6$. El valor $4$ apareix a $n\equiv4\pmod6$.

**Exercici 1.32.** $4^n+5$ múltiple de $15$. Mòdul $5$, $4^n\equiv(-1)^n\equiv\pm1$, així que $4^n+5\equiv\pm1\not\equiv0\pmod5$. No hi ha cap $n$.

### 11.8 Errors freqüents

- **Aplicar Euler sense $\operatorname{mcd}(a,m)=1$.** La conclusió pot ser falsa.
- **Reduir l'exponent mòdul $m$.** S'ha de reduir mòdul $\varphi(m)$ o mòdul l'ordre.
- **Pensar que l'ordre és sempre $\varphi(m)$.** No; pot ser un divisor propi.
- **Confondre $\varphi(p)=p-1$ amb $\varphi(p^e)=p^e-1$.** La fórmula correcta és $p^e-p^{e-1}$.
- **Oblidar que $\varphi$ és multiplicativa només per a factors coprimers.**
- **Calcular $a^{p-1}$ quan $p\mid a$.** Llavors no val $1$; val $0$ mòdul $p$.

***
<a id="sec12"></a>
## 12. Matrius mòdul $m$

### 12.1 Definicions bàsiques

Sigui $R=\mathbb Z/m\mathbb Z$. El conjunt de matrius $n\times n$ amb entrades a $R$ es denota
$$
M_n(R)=M_n(\mathbb Z/m\mathbb Z).
$$
La suma i el producte es defineixen igual que sobre $\mathbb Z$, reduint el resultat mòdul $m$:
$$
(A+B)_{ij}=a_{ij}+b_{ij},\qquad
(AB)_{ij}=\sum_{k=1}^n a_{ik}b_{kj}.
$$
La matriu identitat $I_n$ té $1$ a la diagonal i $0$ fora.

Una matriu $A\in M_n(R)$ és **invertible** si existeix $B\in M_n(R)$ amb
$$
AB=BA=I_n.
$$
En aquest cas $B=A^{-1}$. El conjunt de matrius invertibles forma el grup lineal
$$
GL_n(R)=\{A\in M_n(R):\det A\in R^\times\}.
$$
Aquesta igualtat és un teorema, que demostrarem a la secció 12.5.

### 12.2 Determinant

El determinant es defineix amb la mateixa fórmula que sobre $\mathbb Z$:
$$
\det(A)=\sum_{\sigma\in S_n}\operatorname{sgn}(\sigma)
\prod_{i=1}^n a_{i,\sigma(i)}\pmod m.
$$
Com que és un polinomi amb coeficients enters en les entrades, reduir les entrades mòdul $m$ abans o després del càlcul dóna el mateix resultat. Això és molt útil: podem treballar amb representants petits.

**Cas $2\times2$:**
$$
A=\begin{pmatrix}a&b\\c&d\end{pmatrix},
\qquad
\det A=ad-bc.
$$

**Cas $3\times3$:** regla de Sarrus o desenvolupament per files/columnes:
$$
\det\begin{pmatrix}
a&b&c\\
d&e&f\\
g&h&i
\end{pmatrix}
=aei+bfg+cdh-ceg-bdi-afh.
$$
També es pot desenvolupar per la primera fila:
$$
a\begin{vmatrix}e&f\\h&i\end{vmatrix}
-b\begin{vmatrix}d&f\\g&i\end{vmatrix}
+c\begin{vmatrix}d&e\\g&h\end{vmatrix}.
$$

**Exemple.**
$$
A=\begin{pmatrix}1&2&3\\0&1&4\\5&6&0\end{pmatrix}
\pmod5.
$$
Desenvolupant per la primera fila:
$$
\det A=1(1\cdot0-4\cdot6)-2(0\cdot0-4\cdot5)+3(0\cdot6-1\cdot5)
$$
$$
=(0-24)-2(0-20)+3(0-5)
=-24+40-15=1\pmod5.
$$
Com que $1$ és unitat, $A$ és invertible mòdul $5$ (exercici 1.23c).

### 12.3 Propietats del determinant

| Propietat | Fórmula |
|---|---|
| Determinant de la identitat | $\det I_n=1$. |
| Multiplicativitat | $\det(AB)=\det A\det B$. |
| Transposició | $\det(A^T)=\det A$. |
| Escalat | $\det(cA)=c^n\det A$. |
| Triangular | Si $A$ és triangular, $\det A=\prod_i a_{ii}$. |
| Multilinealitat | El determinant és lineal en cada fila/columna per separat. |
| Alternança | Si es permuten dues files, el determinant canvia de signe; si dues files coincideixen, val $0$. |
| Filera/columna zero | Si una fila o columna és zero, $\det A=0$. |
| Operacions elementals | Sumar a una fila un múltiple d'una altra no canvia el determinant; multiplicar una fila per $c$ multiplica el determinant per $c$. |
| Desenvolupament | Es pot desenvolupar per qualsevol fila o columna. |
| Adjunta | $A\operatorname{adj}(A)=\operatorname{adj}(A)A=\det(A)I_n$. |

**Atenció.** El determinant **no** és lineal respecte de la suma de matrius:
$$
\det(A+B)\ne\det A+\det B
$$
en general.

**Per què $\det(AB)=\det A\det B$.** És una identitat polinomial amb coeficients enters que val sobre $\mathbb Q$ (o $\mathbb R$). Com que els enters s'injecten a $\mathbb Q$, la identitat val sobre $\mathbb Z$, i reduint mòdul $m$ val sobre $\mathbb Z/m\mathbb Z$.

### 12.4 Matriu adjunta i fórmula de la inversa

Per a una matriu $A=(a_{ij})$, el **menor** $A_{ij}$ és la matriu $(n-1)\times(n-1)$ que s'obté eliminant la fila $i$ i la columna $j$. El **cofactor** és
$$
C_{ij}=(-1)^{i+j}\det(A_{ij}).
$$
La **matriu adjunta** és la transposada de la matriu de cofactors:
$$
\operatorname{adj}(A)=C^T,
\qquad
\operatorname{adj}(A)_{ij}=C_{ji}.
$$
Aleshores
$$
A\operatorname{adj}(A)=\operatorname{adj}(A)A=\det(A)I_n.
$$

**Cas $2\times2$:**
$$
A=\begin{pmatrix}a&b\\c&d\end{pmatrix},
\qquad
\operatorname{adj}(A)=
\begin{pmatrix}d&-b\\-c&a\end{pmatrix}.
$$
Si $\det A=ad-bc$ és una unitat,
$$
\boxed{
A^{-1}=\frac{1}{\det A}
\begin{pmatrix}d&-b\\-c&a\end{pmatrix}
=(\det A)^{-1}
\begin{pmatrix}d&-b\\-c&a\end{pmatrix}
\pmod m.
}
$$

**Cas general.** Si $\det A$ és una unitat mòdul $m$,
$$
\boxed{
A^{-1}=(\det A)^{-1}\operatorname{adj}(A)\pmod m.
}
$$
La divisió per $\det A$ es fa multiplicant pel seu invers modular, no dividint en $\mathbb Z/m\mathbb Z$.

**Exemple $2\times2$ mòdul $5$:**
$$
A=\begin{pmatrix}1&2\\3&4\end{pmatrix},
\qquad
\det A=4-6=-2\equiv3\pmod5.
$$
$3^{-1}\equiv2\pmod5$ perquè $3\cdot2=6\equiv1$. Així,
$$
\operatorname{adj}(A)=
\begin{pmatrix}4&-2\\-3&1\end{pmatrix}
\equiv
\begin{pmatrix}4&3\\2&1\end{pmatrix}\pmod5,
$$
$$
A^{-1}=2
\begin{pmatrix}4&3\\2&1\end{pmatrix}
=
\begin{pmatrix}8&6\\4&2\end{pmatrix}
\equiv
\begin{pmatrix}3&1\\4&2\end{pmatrix}\pmod5.
$$
Comprovació:
$$
\begin{pmatrix}1&2\\3&4\end{pmatrix}
\begin{pmatrix}3&1\\4&2\end{pmatrix}
=
\begin{pmatrix}11&5\\25&11\end{pmatrix}
\equiv
\begin{pmatrix}1&0\\0&1\end{pmatrix}\pmod5.
$$

**Exemple $2\times2$ mòdul $6$ amb determinant unitat:**
$$
A=\begin{pmatrix}1&2\\3&5\end{pmatrix},
\qquad
\det A=5-6=-1\equiv5\pmod6.
$$
$5^{-1}\equiv5\pmod6$, i
$$
\operatorname{adj}(A)=
\begin{pmatrix}5&-2\\-3&1\end{pmatrix}
\equiv
\begin{pmatrix}5&4\\3&1\end{pmatrix}\pmod6,
$$
$$
A^{-1}=5
\begin{pmatrix}5&4\\3&1\end{pmatrix}
=
\begin{pmatrix}25&20\\15&5\end{pmatrix}
\equiv
\begin{pmatrix}1&2\\3&5\end{pmatrix}=A\pmod6.
$$
Així, $A$ és la seva pròpia inversa: $A^2\equiv I_2\pmod6$.

### 12.5 Criteri d'invertibilitat

**Teorema.** Sigui $A\in M_n(\mathbb Z/m\mathbb Z)$. Aleshores
$$
\boxed{
A \text{ és invertible}
\iff
\det(A)\in(\mathbb Z/m\mathbb Z)^\times
\iff
\operatorname{mcd}(\det(A),m)=1.
}
$$

**Demostració.**

- $(\Rightarrow)$ Si $A$ és invertible, existeix $B$ amb $AB=I_n$. Prenent determinants:
  $$
  \det(A)\det(B)=\det(I_n)=1.
  $$
  Per tant, $\det(A)$ té invers $\det(B)$ a $\mathbb Z/m\mathbb Z$, i és una unitat.
- $(\Leftarrow)$ Si $d=\det(A)$ és una unitat, sigui $d^{-1}$ el seu invers. Definim
  $$
  B=d^{-1}\operatorname{adj}(A).
  $$
  Aleshores
  $$
  AB=d^{-1}A\operatorname{adj}(A)=d^{-1}dI_n=I_n,
  $$
  i igualment $BA=I_n$. Per tant, $A$ és invertible i $A^{-1}=B$.

**Conseqüències.**

- Si $m=p$ és primer, $A$ és invertible si i només si $\det A\ne0$ en $\mathbb F_p$.
- Si $m$ és compost, pot passar que $\det A\ne0$ però $\operatorname{mcd}(\det A,m)\ne1$; llavors $A$ **no** és invertible.
- Exemple: $A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$ mòdul $6$ té $\det A=4\ne0$, però $\operatorname{mcd}(4,6)=2$, així que no és invertible.

### 12.6 Exemples d'invertibilitat

**Exercici 1.23a.** $A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$ mòdul $3$:
$$
\det A=-2\equiv1\pmod3,
$$
que és unitat. A més,
$$
A\equiv\begin{pmatrix}1&2\\0&1\end{pmatrix}\pmod3,
\qquad
A^{-1}\equiv
\begin{pmatrix}1&1\\0&1\end{pmatrix}\pmod3.
$$

**Exercici 1.23b.** La mateixa $A$ mòdul $10$:
$$
\det A=-2,\qquad \operatorname{mcd}(2,10)=2\ne1,
$$
així que **no és invertible** mòdul $10$.

**Exercici 1.23c.**
$$
B=\begin{pmatrix}3&2&1\\1&-1&-4\\-1&2&3\end{pmatrix},
\qquad
\det B=18.
$$
- Mòdul $3$: $\det B\equiv0$, no invertible.
- Mòdul $5$: $\det B\equiv3$, unitat; invertible, amb inversa
  $$
  B^{-1}=
  \begin{pmatrix}
  0&2&1\\
  2&0&1\\
  2&4&0
  \end{pmatrix}
  \pmod5.
  $$
- Mòdul $10$: $\operatorname{mcd}(18,10)=2\ne1$, no invertible.

**Exercici 1.23d.**
$$
D=\begin{pmatrix}
1&2&0&0\\
3&-4&0&1\\
0&0&2&-1\\
0&3&2&5
\end{pmatrix},
\qquad
\det D=-126=-2\cdot3^2\cdot7.
$$
- No invertible mòdul $2,3,7,9$, perquè $\det D\equiv0$ mòdul aquests.
- Invertible mòdul $5$ i mòdul $55=5\cdot11$, perquè $\operatorname{mcd}(126,5)=1$ i $\operatorname{mcd}(126,55)=1$.
- Les inverses concretes són a les solucions de l'exercici 1.23; el punt important és el criteri del determinant.

**Exercici 1.23 (apartat 1c).** La matriu
$$
C=\begin{pmatrix}1&2&3\\0&1&4\\5&6&0\end{pmatrix}
$$
té $\det C=1$ mòdul $5$, així que és invertible mòdul $5$.

### 12.7 Sistemes lineals sobre un cos $\mathbb F_p$

Si $p$ és primer, $\mathbb F_p$ és un cos i tota l'àlgebra lineal estàndard funciona:

- vectors, combinacions lineals, subespais;
- independència lineal, bases i dimensió;
- eliminació de Gauss i Gauss-Jordan;
- rang;
- regla de Cramer;
- teorema de Rouché–Capelli.

**Sistema.** Un sistema lineal
$$
A\mathbf x=\mathbf b
$$
amb $A\in M_{m\times n}(\mathbb F_p)$ i $\mathbf b\in\mathbb F_p^m$.

**Rouché–Capelli.**

- El sistema és **compatible** si i només si
  $$
  \operatorname{rang}(A)=\operatorname{rang}(A\mid\mathbf b).
  $$
- Si és compatible i $\operatorname{rang}(A)=n$ (nombre d'incògnites), la solució és **única**.
- Si és compatible i $\operatorname{rang}(A)=r<n$, hi ha
  $$
  p^{n-r}
  $$
  solucions.

**Matriu quadrada.** Si $A$ és $n\times n$ i $\det A\ne0$, llavors $A$ és invertible i
$$
\mathbf x=A^{-1}\mathbf b
$$
és l'única solució.

**Regla de Cramer.** Si $\det A\ne0$, llavors
$$
x_i=\frac{\det A_i}{\det A},
$$
on $A_i$ és la matriu que s'obté substituint la columna $i$ de $A$ per $\mathbf b$.

**Exemple (exercici 1.22a).** A $\mathbb Z/17\mathbb Z$:
$$
\begin{cases}
x+3y=15,\\
-2x+14y=1.
\end{cases}
$$
$$
A=\begin{pmatrix}1&3\\-2&14\end{pmatrix},
\qquad
\det A=14+6=20\equiv3\pmod{17}.
$$
$3^{-1}\equiv6$, així que
$$
x=\frac{\det\begin{pmatrix}15&3\\1&14\end{pmatrix}}{3}
=\frac{207}{3}\equiv\frac{3}{3}\equiv1,
$$
$$
y=\frac{\det\begin{pmatrix}1&15\\-2&1\end{pmatrix}}{3}
=\frac{31}{3}\equiv14\cdot6=84\equiv16.
$$
Solució: $(x,y)=(1,16)$.

**Exemple (exercici 1.38t).** A $\mathbb Z/13\mathbb Z$:
$$
\begin{cases}
2x+3y=3,\\
x+2y=4,\\
5x-4y=2.
\end{cases}
$$
Les dues primeres equacions donen $x=7$, $y=5$; la tercera es compleix:
$$
5\cdot7-4\cdot5=35-20=15\equiv2\pmod{13}.
$$
El determinant de la matriu de les dues primeres és $2\cdot2-3\cdot1=1\ne0$, així que el sistema és compatible i determinat.

### 12.8 Sistemes sobre $\mathbb Z/m\mathbb Z$ amb $m$ compost

Quan $m$ no és primer, hi ha divisors de zero i les coses es compliquen.

**Cas 1: $\det A$ és una unitat.** Llavors $A$ és invertible i el sistema té **solució única**:
$$
\mathbf x=A^{-1}\mathbf b.
$$
També es pot usar Cramer, perquè la divisió per $\det A$ és multiplicació pel seu invers.

**Cas 2: $\det A$ no és una unitat.** Llavors $A$ no és invertible. El sistema pot:

- no tenir solució;
- tenir una solució;
- tenir diverses solucions.

No n'hi ha prou de mirar el determinant. Cal resoldre el sistema o analitzar-lo component a component.

**Mètode pràctic.**

1. Factoritzeu $m=\prod p_i^{e_i}$.
2. Resoleu el sistema mòdul cada $p_i^{e_i}$.
3. Combineu les solucions amb el CRT.

Aquest mètode és especialment útil perquè mòdul una potència de primer la informació és més manejable que mòdul un compost amb diversos factors.

**Exemple (apunts, mòdul $6$).**
$$
\begin{cases}
x+2y=1,\\
3x+4y=2
\end{cases}
\pmod6.
$$
La matriu és
$$
A=\begin{pmatrix}1&2\\3&4\end{pmatrix},
\qquad
\det A=4,
$$
que no és unitat mòdul $6$. De la primera equació, $x=1-2y$. Substituint:
$$
3(1-2y)+4y\equiv2
\implies3-2y\equiv2
\implies2y\equiv1\pmod6.
$$
Però $2y$ mòdul $6$ només pot valer $0,2,4$; mai $1$. Per tant, **no hi ha solució**.

**Exemple (apunts, mòdul $6$, homogeni).**
$$
\begin{cases}
x+2y=0,\\
3x+4y=0
\end{cases}
\pmod6.
$$
De la primera, $x=-2y$. Substituint:
$$
3(-2y)+4y=-6y+4y=4y\equiv0\pmod6.
$$
Això equival a $6\mid4y$, és a dir, $3\mid2y$, i com que $\operatorname{mcd}(3,2)=1$, $3\mid y$. Per tant, $y\equiv0$ o $3\pmod6$:
- $y=0\Rightarrow x=0$;
- $y=3\Rightarrow x=-6\equiv0$.
Solucions: $(0,0)$ i $(0,3)$. El sistema és compatible indeterminat, però amb un nombre finit de solucions.

**Exemple (exercici 1.22b).** Mòdul $5$ i mòdul $25$:
$$
\begin{cases}
3x+2y=0,\\
2x-4y=2.
\end{cases}
$$
El determinant és $-16$.
- Mòdul $5$: $-16\equiv4$, unitat; solució única $(4,4)$.
- Mòdul $25$: $-16\equiv9$, unitat; solució única $(19,9)$.

**Exemple (exercici 1.22c).** El mateix sistema amb la segona equació $4x-4y=2$ no té solució, ni mòdul $5$ ni mòdul $25$. Eliminant:
$$
4\cdot(3x+2y)=12x+8y\equiv0,
\qquad
3\cdot(4x-4y)=12x-12y\equiv6,
$$
restant:
$$
20y\equiv-6.
$$
Mòdul $5$, $20y\equiv0$ però $-6\equiv4$, contradicció. Mòdul $25$, $20y$ només pot valer $0,5,10,15,20$, mai $19$.

**Exemple (exercici 1.22d).** Mòdul $2$ no té solució; mòdul $7$ té solució única $(5,6,1)$.

### 12.9 Independència lineal i rang sobre anells

Sobre un cos, la independència lineal i el rang es comporten bé. Sobre $\mathbb Z/m\mathbb Z$ amb $m$ compost, no:

- Un vector no nul pot ser linealment dependent. Per exemple, a $(\mathbb Z/6\mathbb Z)^2$,
  $$
  v=(2,0),\qquad 3v=(6,0)=(0,0),
  $$
  amb $3\ne0$. Així $v$ és linealment dependent tot i ser no nul.
- Una matriu pot tenir determinant no nul i no ser invertible.
- Les nocions habituals de rang poden no coincidir amb les expectatives d'un cos; cal anar amb compte.
- Els sistemes poden tenir un nombre de solucions que no és una potència del mòdul.

**Què es pot fer.**

- Treballar mòdul cada potència de primer via CRT.
- Usar eliminació només amb operacions permeses: intercanviar files, sumar un múltiple d'una altra fila, multiplicar una fila per una **unitat**.
- No multiplicar files per elements no invertibles si es vol preservar l'equivalència del sistema (es poden introduir o perdre solucions).
- Per a problemes avançats, usar la forma normal de Smith sobre $\mathbb Z$ o tècniques de mòduls.

### 12.10 Errors freqüents

- **Concloure invertibilitat de $\det A\ne0$ quan $m$ no és primer.** Cal que $\det A$ sigui una unitat, és a dir, $\operatorname{mcd}(\det A,m)=1$.
- **Dividir per $\det A$ quan no és unitat.** En $\mathbb Z/m\mathbb Z$ no hi ha divisió general.
- **Usar Cramer amb determinant no unitat.** Cramer només és vàlid si $\det A$ és invertible.
- **Cancel·lar matrius no invertibles.** $AB=AC$ no implica $B=C$ si $A$ no és invertible.
- **Multiplicar files per elements no unitats en resoldre sistemes.** Pot canviar el conjunt de solucions.
- **Oblidar que $M_n(\mathbb Z)$ no és commutatiu.** $(AB)^{-1}=B^{-1}A^{-1}$.
- **Pensar que tota matriu no nul·la és invertible o que tot vector no nul és independent.** A $\mathbb Z/m\mathbb Z$ compost, no.

***
<a id="sec13"></a>
## 13. Consells i estratègies de resolució

### 13.1 Ruta general davant d'un problema

1. **Identifiqueu el tipus d'objecte:** enters, congruències, classes, matrius, sistema.
2. **Identifiqueu el mòdul $m$.** Factoritzeu-lo si no és primer:
   $$
   m=p_1^{e_1}\cdots p_r^{e_r}.
   $$
   Això us dirà si podeu dividir per qualsevol element no nul o no.
3. **Comproveu si els elements que voleu invertir són unitats:**
   $$
   \operatorname{mcd}(a,m)=1.
   $$
4. **Trieu l'eina:**
   - mcd/mcm: Euclides o factorització;
   - invers: Bézout;
   - equació diofàntica: Bézout + solució general;
   - sistema de congruències: CRT;
   - potència gran: Fermat/Euler + exponenciació ràpida;
   - matriu: determinant + adjunta/Gauss;
   - sistema lineal: determinant, rang, Cramer o eliminació.
5. **Comproveu el resultat** substituint o amb una identitat (mcd·mcm, $AA^{-1}=I$, etc.).

### 13.2 Per tipus d'exercici

#### Càlcul de mcd i mcm

- **Nombres petits o factoritzats:** factoritzeu i useu mínims/màxims exponents.
- **Nombres grans:** algorisme d'Euclides.
- **Expressions en $n$:** busqueu una combinació lineal que elimini $n$; el mcd divideix la constant resultant. Després comproveu quins divisors apareixen.
- **Diversos nombres:** calculeu el mcd per parelles o per factorització; per al mcm, useu
  $$
  \operatorname{mcm}(a,b)=\frac{|ab|}{\operatorname{mcd}(a,b)}
  $$
  i després combineu.
- **Comprovació:** el mcd ha de dividir tots els nombres; el mcm ha de ser múltiple de tots; per a dos nombres, $\operatorname{mcd}\cdot\operatorname{mcm}=|ab|$.

#### Trobar coeficients de Bézout

- **Mètode de substitucions:** bo per a càlculs manuals curts.
- **Mètode matricial:** bo per a moltes divisions o per evitar errors de signe.
- **Euclides estès iteratiu:** bo per a programació.
- **Comprovació:** substituïu $\alpha a+\beta b$ i comproveu que dóna $d$.
- **Recordeu:** els coeficients no són únics; si en trobeu uns, també valen
  $$
  \alpha+t\frac bd,\qquad \beta-t\frac ad.
  $$

#### Equacions diofàntiques

- **Pas 0:** calculeu $d=\operatorname{mcd}(a,b)$.
- **Pas 1:** si $d\nmid c$, no hi ha solució. Atureu-vos.
- **Pas 2:** dividiu per $d$ per treballar amb coeficients coprimers.
- **Pas 3:** trobeu una solució particular amb Bézout.
- **Pas 4:** escriviu la solució general amb pas $(b/d,-a/d)$.
- **Pas 5:** si hi ha cotes, imposeu-les i seleccioneu els $t$ vàlids.
- **Comprovació:** substituïu la solució general a l'equació original.

#### Sistemes de congruències

- **Comproveu la coprimalitat dos a dos** si voleu usar el CRT clàssic.
- **Mètode seqüencial:** substituïu una congruència dins de la següent; és el més pràctic a mà.
- **Fórmula directa:** útil si els inversos són fàcils.
- **Si els mòduls no són coprimers:** comproveu la condició
  $$
  a_i\equiv a_j\pmod{\operatorname{mcd}(m_i,m_j)}.
  $$
  Si no es compleix, no hi ha solució. Si es compleix, la solució és única mòdul $\operatorname{mcm}(m_i)$.
- **Comprovació:** substituïu la solució a cada congruència original.

#### Potències grans

- **Reduïu la base** mòdul $m$.
- **Si $\operatorname{mcd}(a,m)=1$:** useu Fermat/Euler per reduir l'exponent mòdul $\varphi(m)$ o, millor, mòdul l'ordre.
- **Si $\operatorname{mcd}(a,m)\ne1$:** no useu Euler; calculeu directament, detecteu el període o useu CRT.
- **Exponenciació ràpida:** implementeu el mètode binari; no calculeu $a^e$ sencer.
- **Comprovació:** per a exponents petits, compareu amb el càlcul directe.

#### Inversos modulars

- **Bézout:** si $\alpha a+\beta m=1$, llavors $a^{-1}\equiv\alpha\pmod m$.
- **Fermat:** si $m=p$ primer, $a^{-1}\equiv a^{p-2}\pmod p$.
- **Euler:** si $\operatorname{mcd}(a,m)=1$, $a^{-1}\equiv a^{\varphi(m)-1}\pmod m$.
- **Comprovació:** $a\cdot a^{-1}\equiv1\pmod m$.

#### Matrius

- **Pas 1:** calculeu $\det A$ mòdul $m$.
- **Pas 2:** comproveu $\operatorname{mcd}(\det A,m)=1$.
- **Si és unitat:** $A^{-1}=(\det A)^{-1}\operatorname{adj}(A)$; també podeu usar Gauss-Jordan amb operacions per unitats.
- **Si no és unitat:** no és invertible. No conclogueu res sobre sistemes sense analitzar-los.
- **Comprovació:** $AA^{-1}=I$ i $A^{-1}A=I$.

#### Sistemes lineals mòdul $m$

- **Si $m=p$ és primer:** useu àlgebra lineal estàndard (Gauss, rang, Cramer, Rouché–Capelli).
- **Si $m$ és compost:**
  - si $\det A$ és unitat, hi ha solució única via inversa/Cramer;
  - si $\det A$ no és unitat, el sistema pot no tenir solució, tenir-ne una o diverses;
  - resoleu per substitució/eliminació o descomponeu amb CRT;
  - no dividiu per elements no invertibles.
- **Comprovació:** substituïu la solució a totes les equacions.

#### Problemes de veritat/fals

- **Per demostrar que és fals:** un contraexemple és suficient. Trieu mòduls petits ($4,6,8$) o matrius $2\times2$ senzilles.
- **Per demostrar que és cert:** useu definicions, Bézout, CRT, Fermat/Euler o valoracions.
- **Comproveu les hipòtesis:** coprimalitat, primalitat, invertibilitat, $m>1$.

### 13.3 Errors comuns i com evitar-los

| Error | Per què és fals | Com evitar-lo |
|---|---|---|
| Cancel·lar $a$ de $ab\equiv ac\pmod m$ sense més | $a$ pot no ser invertible | Comproveu $\operatorname{mcd}(a,m)=1$. |
| Concloure $a\mid b$ o $a\mid c$ de $a\mid bc$ | Els factors poden repartir-se | Useu el lema d'Euclides amb $\operatorname{mcd}(a,b)=1$. |
| Confondre mcd i mcm | Són duals | mcd = mínims exponents; mcm = màxims. |
| Usar $ab/\operatorname{mcd}(a,b)$ per a tres nombres | La fórmula és per a dos | Useu factorització o $\operatorname{mcm}(\operatorname{mcm}(a,b),c)$. |
| Aplicar Fermat/Euler sense coprimalitat | La conclusió pot fallar | Comproveu $\operatorname{mcd}(a,m)=1$. |
| Reduir l'exponent mòdul $m$ | L'exponent viu mòdul $\varphi(m)$ o l'ordre | Reduïu mòdul $\varphi(m)$ o $\operatorname{ord}_m(a)$. |
| Usar CRT amb mòduls no coprimers dos a dos | Pot no ser bijectiu | Comproveu coprimalitat o useu el CRT general. |
| Pensar que $\det A\ne0$ implica invertibilitat mòdul $m$ compost | $\det A$ pot no ser unitat | Comproveu $\operatorname{mcd}(\det A,m)=1$. |
| Dividir per $\det A$ en $\mathbb Z/m\mathbb Z$ | No hi ha divisió general | Multipliqueu per $(\det A)^{-1}$ si existeix. |
| Oblidar la condició $d\mid c$ en diofàntiques | És necessària i suficient | Calculeu el mcd primer. |
| Donar una sola solució d'una diofàntica | N'hi ha infinites | Escriviu la família paramètrica. |
| Confondre $\varphi(p^e)$ amb $p^e-1$ | Cal excloure els múltiples de $p$ | $\varphi(p^e)=p^e-p^{e-1}$. |
| Pensar que $\varphi$ és multiplicativa per a qualsevol parella | Només si són coprimers | Comproveu $\operatorname{mcd}(m,n)=1$. |
| Oblidar que $1$ no és primer | Defineix la factorització | Comenceu els primers a $2$. |
| Testar primalitat fins a $n/2$ | N'hi ha prou fins a $\sqrt n$ | Atureu-vos a $\sqrt n$. |
| Concloure $a^n\equiv b^n\Rightarrow a\equiv b$ | Les potències poden coincidir sense les bases | Useu un contraexemple; no invertiu sense coprimalitat. |
| Pensar que $[a]_m\cap[b]_{2m}\ne\varnothing$ implica igualtat | Només hi ha inclusió | Recordeu $[b]_{2m}\subseteq[a]_m$. |
| Usar $(ab)^{-1}=a^{-1}b^{-1}$ en anells no commutatius | L'ordre s'inverteix | Useu $(ab)^{-1}=b^{-1}a^{-1}$. |

### 13.4 Checklist d'examen

- [ ] He identificat el mòdul i l'he factoritzat?
- [ ] He comprovat si els elements que vull invertir són coprimers amb el mòdul?
- [ ] He comprovat la condició de solució (per a diofàntiques o sistemes)?
- [ ] He aplicat correctament els signes en Bézout?
- [ ] He donat **totes** les solucions, no només una?
- [ ] He comprovat el resultat substituint?
- [ ] He evitat cancel·lar factors no invertibles?
- [ ] He distingit entre mòdul primer i compost?
- [ ] He comprovat que el determinant és una unitat abans d'invertir una matriu?
- [ ] He escrit la solució en la forma demanada (classe, família, matriu)?

### 13.5 Com verificar resultats

1. **mcd:** comproveu que divideix els dos nombres i que qualsevol altre divisor comú és més petit o divideix el resultat.
2. **mcm:** comproveu que és múltiple dels dos i que $\operatorname{mcd}\cdot\operatorname{mcm}=|ab|$ per a dos nombres.
3. **Bézout:** substituïu $\alpha a+\beta b$ i comproveu que dóna $d$.
4. **Diofàntica:** substituïu la solució general a l'equació; comproveu que el pas anul·la els termes.
5. **CRT:** substituïu la solució a cada congruència original.
6. **Potència:** per a exponents petits, compareu amb el càlcul directe; per a grans, comproveu amb un mòdul primer o amb una calculadora.
7. **Matriu inversa:** multipliqueu $AA^{-1}$ i comproveu que dóna $I$.
8. **Sistema:** substituïu la solució a totes les equacions.
9. **$\varphi$:** comproveu que el resultat és parell per a $n>2$ i que és menor que $n$.
10. **Classes:** comproveu que el representant triat és a l'interval correcte.

### 13.6 Consells de càlcul

- **Reduïu aviat:** passeu a residus petits abans de multiplicar.
- **Useu representants negatius** quan simplifiquen: per exemple, $p-1\equiv-1$.
- **Aprofiteu les potències conegudes:** $2^{10}=1024\equiv24\pmod{1000}$, $3^{20}\equiv1\pmod{100}$, etc.
- **Factoritzeu el mòdul** abans de res; sovint el problema es divideix en casos més petits.
- **Per a càlculs de potències,** busqueu primer l'ordre de la base; sovint és molt més petit que $\varphi(m)$.
- **Per a sistemes,** el mètode de substitució sol ser més segur que Cramer quan el mòdul és compost.
- **Per a matrius,** calcular el determinant primer estalvia molta feina: si no és unitat, no cal buscar la inversa.

***

<a id="sec14"></a>
## 14. Resum de fórmules i propietats clau

### 14.1 Divisibilitat, mcd i mcm

| Concepte | Fórmula |
|---|---|
| Divisibilitat | $a\mid b\iff\exists c\in\mathbb Z:\ b=ac$. |
| Linealitat | $a\mid b,\ a\mid c\Rightarrow a\mid(ub+vc)$. |
| Lema d'Euclides | $a\mid bc,\ \operatorname{mcd}(a,b)=1\Rightarrow a\mid c$. |
| MCD | $d=\operatorname{mcd}(a,b)$ si $d\mid a,b$ i tot divisor comú divideix $d$. |
| MCM | $m=\operatorname{mcm}(a,b)$ si $a,b\mid m$ i $m$ divideix tot múltiple comú. |
| Traslació | $\operatorname{mcd}(a,b)=\operatorname{mcd}(a+kb,b)$. |
| Homogeneïtat | $\operatorname{mcd}(ma,mb)=|m|\operatorname{mcd}(a,b)$. |
| Producte | $\operatorname{mcd}(a,b)\operatorname{mcm}(a,b)=|ab|$. |
| MCM via MCD | $\operatorname{mcm}(a,b)=|ab|/\operatorname{mcd}(a,b)$. |
| Factorització | $\operatorname{mcd}=\prod p^{\min}$; $\operatorname{mcm}=\prod p^{\max}$. |
| Quocients | $\operatorname{mcd}(a/d,b/d)=1$ si $d=\operatorname{mcd}(a,b)$. |

### 14.2 Bézout i diofàntiques

| Concepte | Fórmula |
|---|---|
| Bézout | $\exists\alpha,\beta:\ \alpha a+\beta b=\operatorname{mcd}(a,b)$. |
| Coprimers | $\operatorname{mcd}(a,b)=1\iff\exists\alpha,\beta:\ \alpha a+\beta b=1$. |
| Coeficients no únics | $\alpha'=\alpha+t\,b/d$, $\beta'=\beta-t\,a/d$. |
| Equació diofàntica | $ax+by=c$ té solució $\iff\operatorname{mcd}(a,b)\mid c$. |
| Solució general | $x=x_0+\frac bd t$, $y=y_0-\frac ad t$. |
| Homogènia | $x=\frac bd t$, $y=-\frac ad t$. |
| Invers modular | $\alpha a+\beta m=1\Rightarrow a^{-1}\equiv\alpha\pmod m$. |

### 14.3 Primers i factorització

| Concepte | Fórmula |
|---|---|
| Primer | $p>1$ amb únics divisors positius $1,p$. |
| Lema d'Euclides | $p\mid ab\Rightarrow p\mid a$ o $p\mid b$. |
| FTA | $n=\pm p_1^{r_1}\cdots p_k^{r_k}$, únic llevat d'ordre i signe. |
| Valoració | $v_p(ab)=v_p(a)+v_p(b)$. |
| Divisibilitat | $a\mid b\iff v_p(a)\le v_p(b)$ per a tot $p$. |
| Infinitura | Hi ha infinits primers (Euclides). |
| Test | N'hi ha prou de provar primers $\le\sqrt n$. |
| Mersenne | $M_q=2^q-1$; si $M_q$ primer, $q$ primer. |
| Factor de Mersenne | $p\mid M_q\Rightarrow p\equiv1\pmod q$ (amb $q$ primer). |

### 14.4 Congruències i $\mathbb Z/m\mathbb Z$

| Concepte | Fórmula |
|---|---|
| Congruència | $a\equiv b\pmod m\iff m\mid(a-b)$. |
| Compatibilitat | $a\equiv a_0,\ b\equiv b_0\Rightarrow a\pm b\equiv a_0\pm b_0$, $ab\equiv a_0b_0$. |
| Classes | $[a]_m=a+m\mathbb Z$. |
| Quocient | $\mathbb Z/m\mathbb Z=\{[0],\dots,[m-1]\}$. |
| Unitat | $[a]$ invertible $\iff\operatorname{mcd}(a,m)=1$. |
| Cos | $\mathbb Z/m\mathbb Z$ és cos $\iff m$ primer. |
| Divisor de zero | Si $[a]\ne[0]$ no és unitat, existeix $[b]\ne[0]$ amb $[a][b]=[0]$. |
| Cancel·lació | $[a]$ invertible i $[a][b]=[a][c]\Rightarrow[b]=[c]$. |
| Equació lineal | $ax\equiv b\pmod m$ té solució $\iff d=\operatorname{mcd}(a,m)\mid b$. |
| Nombre de solucions | Si $d\mid b$, hi ha exactament $d$ solucions mòdul $m$. |
| Solució lineal | $x\equiv(a/d)^{-1}(b/d)\pmod{m/d}$, més $k(m/d)$. |

### 14.5 CRT

| Concepte | Fórmula |
|---|---|
| CRT clàssic | $m_i$ coprimers dos a dos $\Rightarrow$ solució única mòdul $M=\prod m_i$. |
| Fórmula directa | $x=\sum a_iM_iy_i$, $M_i=M/m_i$, $y_i=M_i^{-1}\bmod m_i$. |
| Unicitat | $x\equiv x_0\pmod M$. |
| CRT general | Solució $\iff a_i\equiv a_j\pmod{\operatorname{mcd}(m_i,m_j)}$; única mòdul $\operatorname{mcm}(m_i)$. |
| Bijecció | $\mathbb Z/M\mathbb Z\cong\prod\mathbb Z/m_i\mathbb Z$ si coprimers dos a dos. |
| Equivalència | $a\equiv b\pmod M\iff a\equiv b\pmod{m_i}$ per a tot $i$ (si coprimers). |

### 14.6 Fermat, Euler i $\varphi$

| Concepte | Fórmula |
|---|---|
| Fermat | $p$ primer, $p\nmid a\Rightarrow a^{p-1}\equiv1\pmod p$. |
| Fermat (tot $a$) | $a^p\equiv a\pmod p$. |
| Euler | $\operatorname{mcd}(a,m)=1\Rightarrow a^{\varphi(m)}\equiv1\pmod m$. |
| $\varphi(p)$ | $p-1$. |
| $\varphi(p^e)$ | $p^e-p^{e-1}=p^{e-1}(p-1)$. |
| Multiplicativitat | $\operatorname{mcd}(m,n)=1\Rightarrow\varphi(mn)=\varphi(m)\varphi(n)$. |
| Fórmula general | $\varphi(n)=n\prod_{p\mid n}(1-1/p)$. |
| Ordre | $\operatorname{ord}_m(a)\mid\varphi(m)$. |
| Reducció d'exponent | $a^r\equiv a^s$ si $r\equiv s\pmod{\operatorname{ord}_m(a)}$; suficient mòdul $\varphi(m)$. |
| Invers per Fermat | $a^{-1}\equiv a^{p-2}\pmod p$. |
| Invers per Euler | $a^{-1}\equiv a^{\varphi(m)-1}\pmod m$. |

### 14.7 Matrius

| Concepte | Fórmula |
|---|---|
| Determinant $2\times2$ | $\det\begin{pmatrix}a&b\\c&d\end{pmatrix}=ad-bc$. |
| Multiplicativitat | $\det(AB)=\det A\det B$. |
| Adjunta | $A\operatorname{adj}(A)=\det(A)I$. |
| Inversa | $A^{-1}=(\det A)^{-1}\operatorname{adj}(A)$. |
| Invertibilitat | $A$ invertible $\iff\det A$ és unitat $\iff\operatorname{mcd}(\det A,m)=1$. |
| Cramer | $x_i=\det(A_i)/\det(A)$ si $\det A$ és unitat. |
| $2\times2$ inversa | $\frac1{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$. |
| Sistema únic | $\det A$ unitat $\Rightarrow$ solució única $A^{-1}b$. |

### 14.8 Equivalències notables

$$
\boxed{\operatorname{mcd}(a,b)=1 \iff \exists\alpha,\beta\in\mathbb Z:\ \alpha a+\beta b=1.}
$$

$$
\boxed{[a]_m \text{ invertible} \iff \operatorname{mcd}(a,m)=1.}
$$

$$
\boxed{\mathbb Z/m\mathbb Z \text{ és cos} \iff m \text{ és primer}.}
$$

$$
\boxed{ax+by=c \text{ té solució entera} \iff \operatorname{mcd}(a,b)\mid c.}
$$

$$
\boxed{A\in M_n(\mathbb Z/m\mathbb Z) \text{ invertible} \iff \operatorname{mcd}(\det A,m)=1.}
$$

$$
\boxed{a^{\varphi(m)}\equiv1\pmod m \quad\text{si }\operatorname{mcd}(a,m)=1.}
$$

$$
\boxed{\text{CRT: } m_i \text{ coprimers dos a dos} \Rightarrow \text{solució única mòdul } \prod m_i.}
$$

### 14.9 Taula de decisions ràpida

| Vull... | Eina |
|---|---|
| Calcular un mcd | Euclides (nombres grans) o factorització (nombres petits). |
| Calcular un mcm | $|ab|/\operatorname{mcd}(a,b)$ o factorització. |
| Trobar un invers | Bézout; Fermat/Euler si el mòdul és primer o hi ha coprimalitat. |
| Resoldre $ax+by=c$ | Comprovar $d\mid c$, Bézout, solució general. |
| Resoldre un sistema de congruències | CRT; substitucions successives. |
| Calcular $a^e\bmod m$ | Exponenciació ràpida; Fermat/Euler si $\operatorname{mcd}(a,m)=1$. |
| Calcular $\varphi(n)$ | Factoritzar $n$ i usar $p^{e-1}(p-1)$. |
| Decidir si una matriu és invertible | Calcular $\det A$ i comprovar $\operatorname{mcd}(\det A,m)=1$. |
| Resoldre un sistema lineal mòdul $p$ | Gauss, Cramer, Rouché–Capelli. |
| Resoldre un sistema lineal mòdul $m$ compost | Determinant unitat? Si sí, inversa; si no, substitució/CRT. |

***
<a id="sec15"></a>
## 15. Exemples il·lustratius i connexions amb els exercicis

### 15.1 Mapa d'exercicis per concepte

| Concepte | Exercicis | Què hi trobareu |
|---|---|---|
| Propietats del mcd | 1.1, 1.2, 1.3, 1.4, 1.7 | Traslació, homogeneïtat, combinacions lineals, fraccions irreductibles. |
| Euclides i Bézout | 1.5, 1.9, 1.20, 1.28 | Càlcul de mcd, coeficients, inversos modulars. |
| MCM | 1.6, 1.14 | Fórmula producte/mcd i verificació per factorització. |
| Diofàntiques | 1.8, 1.9b, 1.10 | Condició de solució, solució general, cotes. |
| Factorització | 1.11, 1.12, 1.13, 1.14 | Quadrats, cubs, potències, factoritzacions. |
| Congruències | 1.15–1.21 | Operacions, potències, inversos, equacions lineals. |
| Sistemes lineals | 1.22 | Mòdul primer i compost, diverses solucions. |
| Matrius | 1.23 | Determinant, inversa, criteris. |
| CRT | 1.24–1.27 | Sun Tsu, sistemes, bijeccions, no coprimalitat. |
| Fermat/Euler | 1.28–1.35 | Potències grans, $\varphi$, ordre, aplicacions. |
| Mersenne | 1.37 | Primalitat, ordre, factors. |
| Veritat/fals | 1.38 | Contraexemples, correccions, casos límit. |

### 15.2 Exemples treballats

#### Exemple 1: mcd de formes lineals (exercicis 1.1, 1.3, 1.4)

**1.1.** Si $\operatorname{mcd}(a,b)=1$, sigui $d=\operatorname{mcd}(a+b,a-b)$. Aleshores
$$
d\mid(a+b)+(a-b)=2a,\qquad
d\mid(a+b)-(a-b)=2b.
$$
Així $d\mid\operatorname{mcd}(2a,2b)=2\operatorname{mcd}(a,b)=2$. Com que $d>0$, $d\in\{1,2\}$.

A més, si $a,b$ són tots dos senars, $a+b$ i $a-b$ són parells, així que $d=2$. Si tenen paritat diferent, $a+b$ i $a-b$ són senars, així que $d=1$.

**1.3.** Volem veure
$$
\operatorname{mcd}(3a-b,b-2a)=\operatorname{mcd}(a,b).
$$
Si $d=\operatorname{mcd}(a,b)$, llavors $d\mid3a-b$ i $d\mid b-2a$. Recíprocament, si $g=\operatorname{mcd}(3a-b,b-2a)$, llavors
$$
g\mid(3a-b)+(b-2a)=a,
$$
i
$$
g\mid2(3a-b)+3(b-2a)=b.
$$
Per tant, $g\mid\operatorname{mcd}(a,b)$. Els dos mcd coincideixen. La transformació té matriu
$$
\begin{pmatrix}3&-1\\-2&1\end{pmatrix},
\qquad
\det=3\cdot1-(-1)(-2)=1,
$$
així que és unimodular i preserva el mcd.

**1.4.** Per a $A=28n-5$, $B=35n-8$,
$$
5A-4B=7.
$$
Així $\operatorname{mcd}(A,B)\mid7$. Com que $A\equiv2\pmod7$, cap $7$ no divideix $A$; per tant, el mcd és $1$.

#### Exemple 2: Bézout i invers modular (exercicis 1.5, 1.20)

**1.5a.** $\operatorname{mcd}(1492,1776)$:
$$
1776=1492+284,\quad
1492=5\cdot284+72,\quad
284=3\cdot72+68,
$$
$$
72=68+4,\quad
68=17\cdot4.
$$
Així $\operatorname{mcd}=4$. Cap enrere:
$$
4=72-68=4\cdot72-284=4(1492-5\cdot284)-284
=4\cdot1492-21\cdot284
$$
$$
=4\cdot1492-21(1776-1492)=25\cdot1492-21\cdot1776.
$$
Comprovació: $25\cdot1492-21\cdot1776=37300-37296=4$.

**1.20.** Invers de $29$ mòdul $1170$:
$$
1=3\cdot1170-121\cdot29,
$$
així que
$$
29^{-1}\equiv-121\equiv1049\pmod{1170}.
$$
Comprovació: $29\cdot1049=30421=26\cdot1170+1$.

#### Exemple 3: equació diofàntica (exercici 1.8a)

$$
93x-81y=3.
$$
Dividim per $3$:
$$
31x-27y=1.
$$
Euclides:
$$
31=27+4,\quad
27=6\cdot4+3,\quad
4=3+1.
$$
Cap enrere:
$$
1=4-3=7\cdot4-27=7\cdot31-8\cdot27.
$$
Així, $31\cdot7-27\cdot8=1$, i una solució particular és $(7,8)$. General:
$$
x=7+27t,\qquad y=8+31t.
$$
Comprovació: $93\cdot7-81\cdot8=651-648=3$.

#### Exemple 4: factorització i potències (exercici 1.13)

Volem el menor $n$ amb $n/2$ quadrat, $n/3$ cub i $n/5$ cinquena potència. Si $n=\prod p^{e_p}$, les condicions per a cada primer són:

| Primer | Condicions | Mínim |
|---|---|---:|
| $2$ | $e\equiv1\pmod2$, $e\equiv0\pmod3$, $e\equiv0\pmod5$ | $15$ |
| $3$ | $e\equiv1\pmod3$, $e\equiv0\pmod2$, $e\equiv0\pmod5$ | $10$ |
| $5$ | $e\equiv1\pmod5$, $e\equiv0\pmod2$, $e\equiv0\pmod3$ | $6$ |

Per tant,
$$
n=2^{15}3^{10}5^6=30\,233\,088\,000\,000.
$$
Comprovació:
$$
\frac n2=(2^7 3^5 5^3)^2,\qquad
\frac n3=(2^5 3^3 5^2)^3,\qquad
\frac n5=(2^3 3^2 5)^5.
$$

#### Exemple 5: CRT (exercicis 1.24, 1.25a)

**1.24.** Resolem
$$
x\equiv2\pmod3,\quad
x\equiv3\pmod5,\quad
x\equiv2\pmod7.
$$
De $x=2+3k$ i mòdul $5$:
$$
2+3k\equiv3\implies3k\equiv1\implies k\equiv2\pmod5.
$$
Així $x=8+15t$. Mòdul $7$:
$$
8+15t\equiv2\implies1+t\equiv2\implies t\equiv1\pmod7.
$$
Per tant,
$$
x=23+105s,
$$
és a dir, $x\equiv23\pmod{105}$.

**1.25a.** Sistema
$$
x\equiv10\pmod7,\quad
x\equiv6\pmod9,\quad
x\equiv1\pmod{10}.
$$
Els mòduls són coprimers dos a dos i $M=630$. De $x=1+10k$ i mòdul $9$:
$$
1+10k\equiv6\implies k\equiv5\pmod9,
$$
així $x=51+90m$. Mòdul $7$:
$$
51+90m\equiv3\implies2-m\equiv3\implies m\equiv6\pmod7.
$$
Per tant,
$$
x=51+90\cdot6+630s=591+630s.
$$

#### Exemple 6: Fermat/Euler (exercicis 1.28, 1.34)

**1.28.** $37^{55}\cdot53^{13}\pmod{98}$. Com que $53\equiv37^{-1}$,
$$
37^{55}\cdot53^{13}\equiv37^{55-13}=37^{42}.
$$
$\varphi(98)=42$, i $\operatorname{mcd}(37,98)=1$, així que Euler dóna $37^{42}\equiv1$.

**1.34.** $2022^{20222022}\pmod{19}$ i $\pmod{21}$.

Mòdul $19$: $2022\equiv8$, i $8^3\equiv-1$, així que $8^6\equiv1$. Com que $20222022$ és múltiple de $6$, el resultat és $1$.

Mòdul $21$: mòdul $3$ el resultat és $0$; mòdul $7$, $2022\equiv-1$ i l'exponent és parell, així que el resultat és $1$. Resolent
$$
N\equiv0\pmod3,\quad N\equiv1\pmod7
$$
s'obté $N\equiv15\pmod{21}$.

#### Exemple 7: matrius (exercicis 1.23a, 1.22b)

**1.23a.** $A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$ mòdul $3$:
$$
\det A=-2\equiv1\pmod3,
$$
així que és invertible. Com que $A\equiv\begin{pmatrix}1&2\\0&1\end{pmatrix}$,
$$
A^{-1}\equiv\begin{pmatrix}1&1\\0&1\end{pmatrix}\pmod3.
$$

**1.22b.** Sistema
$$
\begin{cases}
3x+2y=0,\\
2x-4y=2
\end{cases}
\pmod5.
$$
Matriu $A=\begin{pmatrix}3&2\\2&-4\end{pmatrix}$, $\det A=-16\equiv4\pmod5$, unitat. $4^{-1}=4$. Amb Cramer o substitució s'obté
$$
(x,y)=(4,4)\pmod5.
$$
Mòdul $25$, $\det A\equiv9$, $9^{-1}=14$, i la solució és
$$
(x,y)=(19,9)\pmod{25}.
$$

#### Exemple 8: sistema sobre anell compost (exercici 1.22c)

$$
\begin{cases}
3x+2y=0,\\
4x-4y=2
\end{cases}
$$
No té solució, ni mòdul $5$ ni mòdul $25$. Multiplicant la primera per $4$ i la segona per $3$:
$$
12x+8y\equiv0,\qquad
12x-12y\equiv6.
$$
Restant:
$$
20y\equiv-6.
$$
Mòdul $5$: $0\equiv4$, impossible. Mòdul $25$: $20y$ només pot valer $0,5,10,15,20$, mai $19$. Per tant, no hi ha solució.

#### Exemple 9: sistema homogeni sobre $\mathbb Z/6\mathbb Z$

$$
\begin{cases}
x+2y=0,\\
3x+4y=0
\end{cases}
\pmod6.
$$
De la primera, $x=-2y$. Substituint:
$$
3(-2y)+4y=4y\equiv0\pmod6.
$$
Això equival a $6\mid4y$, és a dir, $3\mid2y$, i com que $\operatorname{mcd}(3,2)=1$, $3\mid y$. Per tant, $y=0$ o $3$:
- $y=0\Rightarrow x=0$;
- $y=3\Rightarrow x=-6\equiv0$.

Solucions: $(0,0)$ i $(0,3)$.

#### Exemple 10: veritat/fals (exercici 1.38)

- **(g) Fals:** $a=4$, $b=c=2$: $4\mid4$ i $4\mid0$, però $4\nmid2$.
- **(h) Cert:** si $a$ és senar, $a\mid b+c$ i $a\mid b-c$ impliquen $a\mid2b$ i $a\mid2c$; com que $\operatorname{mcd}(a,2)=1$, $a\mid b$ i $a\mid c$.
- **(r) Fals:** a $\mathbb Z/6\mathbb Z$, $2\cdot2\equiv2\cdot(-1)$, però no es pot cancel·lar $2$ perquè no és invertible; de fet $2\not\equiv-1\pmod6$.
- **(u) Fals:** la versió correcta és $a+c\equiv b+d\pmod{\operatorname{mcd}(r,s)}$, no $a+b\equiv c+d\pmod{\operatorname{mcm}(r,s)}$.
- **(v) Fals:** la versió correcta és $ac\equiv bd\pmod{\operatorname{mcd}(r,s)}$.
- **(y) Fals:** $r\equiv s\pmod p$ no implica $a^{r-1}\equiv a^{s-1}$; cal reduir l'exponent mòdul $p-1$ (si $p\nmid a$) o mòdul l'ordre.

### 15.3 Comentaris sobre els exercicis de veritat/fals

L'exercici 1.38 és especialment útil per repassar casos límit. Resum de les afirmacions:

| Apartat | Valor | Idea clau |
|---|---|---|
| (a) | Cert | $M_2(\mathbb Z)$ té divisors de zero. |
| (b) | Fals | No es pot cancel·lar una matriu no invertible. |
| (c) | Cert | $0=-0$; a $\mathbb Z/2\mathbb Z$, $1=-1$. |
| (d) | Fals | En anells no commutatius, $(ab)^{-1}=b^{-1}a^{-1}$. |
| (e) | Cert | Hi ha matrius $a^2=b^2=I$ amb $(ab)^2\ne I$. |
| (f) | Cert | $\operatorname{mcd}(249018,34650)=462$. |
| (g) | Fals | $a=4$, $b=c=2$. |
| (h) | Cert | Cal $a$ senar. |
| (i) | Fals | Cal $d=\operatorname{mcd}(a,b)$, no un divisor qualsevol. |
| (j) | Fals | $\operatorname{mcd}(13,23)=1\mid4$; hi ha solucions. |
| (k) | Cert | La família $x=16+3\lambda$, $y=4+\lambda$ és correcta. |
| (l) | Cert | Identitat distributiva de mcd i mcm. |
| (m) | Fals | Hi ha exactament $25$ primers $\le100$, no menys d'una quarta part. |
| (n) | Cert | $2347$ és primer. |
| (o) | Cert | Si les classes s'intersecten, $m\mid(a-b)$. |
| (p) | Cert | $[a]_{2m}\subseteq[a]_m$, i la inclusió és estricta. |
| (q) | Fals | Contraexemple $m=3$, $a=0$, $b=3$. |
| (r) | Fals | Cancel·lació il·legal de $2$ mòdul $6$. |
| (s) | Cert | $2x\equiv7\pmod{10}$ no té solució; $2x\equiv6$ en té dues. |
| (t) | Cert | El sistema és compatible i determinat mòdul $13$. |
| (u) | Fals | La versió correcta usa $\operatorname{mcd}(r,s)$ i $a+c\equiv b+d$. |
| (v) | Fals | La versió correcta usa $\operatorname{mcd}(r,s)$ i $ac\equiv bd$. |
| (w) | Cert | $11^{11111}\equiv6\pmod{13}$. |
| (x) | Fals | $22^{2222}\equiv15\not\equiv16\equiv33^{3333}\pmod{17}$. |
| (y) | Fals | Cal reduir l'exponent mòdul $p-1$, no mòdul $p$. |
| (z) | Cert | Euler amb $\varphi(pq)=(p-1)(q-1)$. |

### 15.4 Notes sobre alguns resultats

- **Exercici 1.36.** Per ordenar els anells pel nombre d'unitats, compteu:
  $$
  |\mathbb Q^\times|=\infty,\quad
  |\mathbb Z^\times|=2,\quad
  |(\mathbb Z/11\mathbb Z)^\times|=10,
  $$
  $$
  |(\mathbb Z/18\mathbb Z)^\times|=6,\quad
  |(\mathbb Z/12\mathbb Z)^\times|=4.
  $$
  Per tant, l'ordre **estrictament decreixent** és
  $$
  \mathbb Q \succ \mathbb Z/11\mathbb Z \succ \mathbb Z/18\mathbb Z
  \succ \mathbb Z/12\mathbb Z \succ \mathbb Z.
  $$
  Compteu unitats, no la cardinalitat del conjunt: $\mathbb Z$ és infinit, però només té $\pm1$ com a unitats.

- **Exercici 1.37.** $M_{11}=2047=23\cdot89$ és el contraexemple més petit al recíproc de "si $M_q$ és primer, $q$ és primer". $M_{13}=8191$ i $M_{17}=131071$ són primers.

- **Exercici 1.38 (m).** Els primers $\le100$ són exactament $25$; per tant, no és cert que n'hi hagi menys d'una quarta part.

- **Exercici 1.38 (t).** El sistema té tres equacions i dues incògnites; el fet que el determinant de les dues primeres sigui no nul i que la tercera es compleixi mostra que és compatible i determinat.

### 15.5 Estratègia d'estudi

1. **Primer pas:** domineu les definicions de divisibilitat, mcd, congruència i classe.
2. **Segon pas:** practiqueu Euclides i Bézout fins que siguin automàtics.
3. **Tercer pas:** resolteu diofàntiques i sistemes de congruències amb el mètode seqüencial.
4. **Quart pas:** interioritzeu Fermat/Euler i la reducció d'exponents.
5. **Cinquè pas:** practiqueu matrius mòdul $m$, especialment el criteri del determinant.
6. **Sisè pas:** feu els veritat/fals; són els que detecten més errors conceptuals.
7. **Setè pas:** proveu de resoldre els exercicis sense mirar les solucions i comproveu amb les taules d'aquesta guia.

***
<a id="sec16"></a>
## 16. Apèndix: taula ràpida de resultats

Aquesta taula resumeix les respostes dels exercicis del full `Prob-Aritmetica.md`. Els desenvolupaments complets són a `Sol-Aritmetica.md`.

| Exercici | Resultat clau |
|---|---|
| **1.1** | $\operatorname{mcd}(a+b,a-b)\in\{1,2\}$. És $2$ si $a,b$ són tots dos senars; és $1$ si tenen paritat diferent. |
| **1.2** | $\operatorname{mcd}(ma,mb)=\lvert m\rvert\operatorname{mcd}(a,b)$; per a $m\ge0$, $\operatorname{mcd}(ma,mb)=m\operatorname{mcd}(a,b)$. |
| **1.3** | Sí: $\operatorname{mcd}(3a-b,b-2a)=\operatorname{mcd}(a,b)$. |
| **1.4** | $\operatorname{mcd}(28n-5,35n-8)=1$ per a tot $n\ge1$. |
| **1.5** | a) $\operatorname{mcd}=4$, $25\cdot1492-21\cdot1776=4$. b) $\operatorname{mcd}=77$, $7469-3\cdot2464=77$. c) $\operatorname{mcd}=4$, $181\cdot500-8\cdot11312=4$. |
| **1.6** | $\operatorname{mcm}(1492,1776)=662448$; $\operatorname{mcm}(7469,2464)=239008$; $\operatorname{mcm}(500,11312)=1414000$. |
| **1.7** | $\operatorname{mcd}(4n+5,2n+3)=1$; la fracció és irreductible. |
| **1.8** | a) $x=7+27t$, $y=8+31t$. b) $x=-19+50t$, $y=-27+71t$. c) Cap solució. d) $x=925+1722t$, $y=152+283t$. |
| **1.9** | a) $\operatorname{mcd}(1911,65)=13$, $(-2)\cdot1911+59\cdot65=13$. b) $x=-2+5s$, $y=118-294s$. |
| **1.10** | $m\equiv7S\pmod{12}$ (representant a $1,\dots,12$), $d=(S-31m)/12$. Exemple $S=353$: 1 de novembre. |
| **1.11** | Si $ab$ és quadrat i $\operatorname{mcd}(a,b)=1$, aleshores $a$ i $b$ són quadrats. |
| **1.12** | Si $a^2\mid b^2$, aleshores $a\mid b$. |
| **1.13** | $n=2^{15}3^{10}5^6=30\,233\,088\,000\,000$. |
| **1.14** | $1492=2^2\cdot373$, $1776=2^4\cdot3\cdot37$, $7469=7\cdot11\cdot97$, $2464=2^5\cdot7\cdot11$, $500=2^2\cdot5^3$, $11312=2^4\cdot7\cdot101$. |
| **1.15** | a) $10$; b) $1$; c) $1$. |
| **1.16** | $a\equiv b\Rightarrow ka\equiv kb$ és cert. El recíproc és fals en general; és cert si $\operatorname{mcd}(k,m)=1$. Que $k$ sigui primer no n'hi ha prou. |
| **1.17** | $a\equiv b\Rightarrow a^n\equiv b^n$ és cert per a $n\ge0$. El recíproc és fals. |
| **1.18** | Tot primer senar suma de dos quadrats compleix $p\equiv1\pmod4$. El $2$ és l'excepció. |
| **1.19** | Unitats: $m=2$: $\{1\}$; $3$: $\{1,2\}$; $4$: $\{1,3\}$; $5$: $\{1,2,3,4\}$; $6$: $\{1,5\}$; $7$: $\{1,\dots,6\}$; $8$: $\{1,3,5,7\}$; $9$: $\{1,2,4,5,7,8\}$; $10$: $\{1,3,7,9\}$. |
| **1.20** | $29$ invertible, $29^{-1}\equiv1049\pmod{1170}$. $234$ i $512$ no són invertibles. |
| **1.21** | a) $x\equiv88\pmod{101}$. b) $x\equiv0,9\pmod{18}$. c) $x\equiv0\pmod5$, és a dir, $0,5,10,15,20,25\pmod{30}$. |
| **1.22** | a) $(1,16)$ mòdul $17$. b) $(4,4)$ mòdul $5$; $(19,9)$ mòdul $25$. c) Cap solució. d) Cap solució mòdul $2$; $(5,6,1)$ mòdul $7$. |
| **1.23** | a) Invertible mòdul $3$, $A^{-1}=\begin{pmatrix}1&1\\0&1\end{pmatrix}$. b) No invertible mòdul $10$. c) Invertible només mòdul $5$; inversa a les solucions. d) Invertible només mòdul $5$ i $55$. |
| **1.24** | $x\equiv23\pmod{105}$. |
| **1.25** | a) $x\equiv591\pmod{630}$. b) $x\equiv331\pmod{420}$. c) $x\equiv118\pmod{420}$. |
| **1.26** | $a\equiv b\pmod M\iff a\equiv b\pmod{m_i}$ per a tot $i$. És la injectivitat de la bijecció CRT. |
| **1.27** | $f$ és injectiva però no exhaustiva; $g$ és bijectiva. |
| **1.28** | a) $37^{-1}\equiv53\pmod{98}$. b) $37^{55}\cdot53^{13}\equiv1\pmod{98}$. |
| **1.29** | a) $3$; b) $4$; c) $9$. |
| **1.30** | Els dos últims dígits de $103^{1243}$ són $27$. |
| **1.31** | $n\equiv4\pmod6$. |
| **1.32** | Cap $n$; $4^n+5$ mai és múltiple de $15$. |
| **1.33** | a) $x\equiv4\pmod{13}$. b) $n\equiv1\pmod3$. |
| **1.34** | $2022^{20222022}\equiv1\pmod{19}$ i $\equiv15\pmod{21}$. |
| **1.35** | $\varphi(128)=64$; $\varphi(1123)=1122$; $\varphi(1125)=600$; $\varphi(29270241)=13\,296\,960$; $\varphi(12648925575)=5\,363\,107\,200$. |
| **1.36** | Ordre decreixent: $\mathbb Q\succ\mathbb Z/11\mathbb Z\succ\mathbb Z/18\mathbb Z\succ\mathbb Z/12\mathbb Z\succ\mathbb Z$ (unitats $\infty,10,6,4,2$). |
| **1.37** | a) $M_q$ primer $\Rightarrow q$ primer. b) $M_{11}=2047=23\cdot89$. c) $p\mid M_q\Rightarrow p\equiv1\pmod q$. d) $M_{13}=8191$ i $M_{17}=131071$ són primers. |
| **1.38** | Cert: a, c, e, f, h, k, l, n, o, p, s, t, w, z. Fals: b, d, g, i, j, m, q, r, u, v, x, y. |

### 16.1 Equivalències per memoritzar

$$
\begin{aligned}
&\operatorname{mcd}(a,b)=1 &&\iff \exists\alpha,\beta:\alpha a+\beta b=1,\\
&[a]_m\text{ invertible} &&\iff \operatorname{mcd}(a,m)=1,\\
&\mathbb Z/m\mathbb Z\text{ és cos} &&\iff m\text{ és primer},\\
&ax+by=c\text{ té solució} &&\iff \operatorname{mcd}(a,b)\mid c,\\
&A\in M_n(\mathbb Z/m\mathbb Z)\text{ invertible} &&\iff \operatorname{mcd}(\det A,m)=1.
\end{aligned}
$$

### 16.2 Tres regles d'or

1. **No dividiu mai per un element que no sigui unitat.** En $\mathbb Z/m\mathbb Z$, comproveu $\operatorname{mcd}(a,m)=1$ abans de cancel·lar o invertir.
2. **Reduïu l'exponent correctament.** Si $\operatorname{mcd}(a,m)=1$, l'exponent es redueix mòdul $\varphi(m)$ o, millor, mòdul l'ordre; mai mòdul $m$.
3. **Comproveu sempre.** Una substitució, un producte de matrius o una congruència poden detectar la majoria d'errors.

***

*Fi de la guia.*
