## 8. Divisibilitat

Siguin \(a,b \in \mathbb{Z}\).

\[
a \mid b
\iff a \text{ divideix } b
\iff b \text{ és múltiple de } a
\iff b \text{ és divisible per } a
\iff \exists c \in \mathbb{Z} \text{ tal que } b = ac.
\]

**Explicació:**
La divisibilitat és un concepte fonamental que descriu quan un nombre cap dins d'un altre sense deixar residu. La notació \(a \mid b\) es llegeix "a divideix b". Fixa't que la condició principal és que existeixi un enter \(c\) que, multiplicat per \(a\), ens doni exactament \(b\). És a dir, \(b\) es pot construir com a múltiples de \(a\).

**Exemples:**

\[
2 \mid 6 \quad \text{perquè} \quad 6 = 2\cdot 3.
\]

\[
2 \nmid 5 \quad \text{perquè no existeix cap } c \in \mathbb{Z} \text{ tal que } 5 = 2c.
\]

## 9. Propietats de la divisibilitat

### 9.i) Transitivitat

Siguin \(a,b,c \in \mathbb{Z}\). Si \(a \mid b\) i \(b \mid c\), aleshores \(a \mid c\).

**Explicació:**
La transitivitat és com una cadena de dominó. Si \(a\) cap dins de \(b\) (és a dir, \(b\) és múltiple de \(a\)), i al seu torn \(b\) cap dins de \(c\), aleshores forçosament \(a\) també ha de cabre dins de \(c\). Això ens permet encadenar divisions i simplificar problemes.

**Demostració:**

Si \(a \mid b\), aleshores \(\exists k \in \mathbb{Z}\) tal que \(b = ak\).

Si \(b \mid c\), aleshores \(\exists m \in \mathbb{Z}\) tal que \(c = bm\).

Substituint \(b\):
\[
c = (ak)m = a(km).
\]
Com que \(km \in \mathbb{Z}\), tenim que \(a \mid c\).

**Exemple concret (només un cas):**

\(2 \mid 4\) i \(4 \mid 12\), per tant \(2 \mid 12\).

Comprovació: \(4 = 2\cdot 2\) i \(12 = 4\cdot 3 = 2\cdot 2\cdot 3 = 2\cdot 6\), així que \(2 \mid 12\).

### 9.ii) Linealitat (suma i resta)

Siguin \(a,b,c \in \mathbb{Z}\). Si \(a \mid b\) i \(a \mid c\), aleshores
\[
a \mid (b+c) \quad \text{i} \quad a \mid (b-c).
\]

**Explicació:**
Si un nombre divideix dos nombres diferents, també divideix qualsevol combinació lineal seva. Pensa-hi com a grups d'objectes: si pots agrupar \(b\) objectes en grups de mida \(a\), i també pots agrupar \(c\) objectes en grups de mida \(a\), aleshores si els ajuntes tots, o si en treus una part, la mida del grup \(a\) encara funciona perfectament. Aquesta propietat és la base per a moltes demostracions algebraiques.

**Demostració:**

Si \(a \mid b\), aleshores \(\exists k \in \mathbb{Z}\) tal que \(b = ak\).

Si \(a \mid c\), aleshores \(\exists m \in \mathbb{Z}\) tal que \(c = am\).

Aleshores:
\[
b+c = ak + am = a(k+m),
\]
\[
b-c = ak - am = a(k-m).
\]
Com que \(k+m \in \mathbb{Z}\) i \(k-m \in \mathbb{Z}\), tenim que
\[
a \mid (b+c) \quad \text{i} \quad a \mid (b-c).
\]

**Exemple concret (només un cas):**

\(2 \mid 6\) i \(2 \mid 10\), per tant \(2 \mid (6+10) = 16\) i \(2 \mid (10-6) = 4\).

Comprovació: \(6 = 2\cdot 3\), \(10 = 2\cdot 5\), així \(16 = 2\cdot 8\) i \(4 = 2\cdot 2\).

### 9.iii) Factor comú

Siguin \(a,b,c \in \mathbb{Z}\). Si \(a \mid b\), aleshores \(a \mid bc\).

**Explicació:**
Si \(a\) ja divideix \(b\), aleshores dividirà qualsevol múltiple de \(b\). És com dir: si 2 divideix 6, aleshores 2 també dividirà 6 multiplicat per qualsevol nombre (per exemple, 6×5=30, i 2 divideix 30). La divisibilitat es propaga cap amunt quan multipliquem.

**Demostració:**

Si \(a \mid b\), aleshores \(\exists k \in \mathbb{Z}\) tal que \(b = ak\).

Multiplicant per \(c\):
\[
bc = (ak)c = a(kc).
\]
Com que \(kc \in \mathbb{Z}\), tenim que \(a \mid bc\).

**Exemple concret:**

\(2 \mid 6\), per tant \(2 \mid 6\cdot 5 = 30\).

Comprovació: \(6 = 2\cdot 3\), així \(30 = 6\cdot 5 = 2\cdot 3\cdot 5 = 2\cdot 15\).

### 9.iv) Contraexemple: \(a \mid bc \nRightarrow a \mid b\) o \(a \mid c\)

En general, que \(a\) divideixi un producte \(bc\) **no** implica que divideixi cap dels factors.

**Explicació:**
Aquesta és una trampa molt comuna. El fet que un nombre divideixi un producte **no vol dir** que divideixi necessàriament cadascun dels factors per separat. El nombre pot estar format per la combinació de parts dels dos factors. Cal anar amb compte i no assumir aquesta propietat sense demostració, perquè és falsa en general.

**Contraexemple:**

\[
6 \mid 2\cdot 3 = 6,
\]
però
\[
6 \nmid 2 \quad \text{i} \quad 6 \nmid 3.
\]

Per tant, \(a \mid bc\) no implica \(a \mid b\) ni \(a \mid c\).

### 9.v) Antisimetria (llevat de signe)

Siguin \(a,b \in \mathbb{Z}\). Si \(a \mid b\) i \(b \mid a\), aleshores
\[
a = \pm b.
\]

**Explicació:**
Si dos nombres es divideixen mútuament, vol dir que tenen exactament la mateixa "grandària" en valor absolut. L'únic que pot canviar és el signe (positiu o negatiu). Per exemple, 2 i -2 es divideixen mútuament, però no podria ser que 2 dividís 4 i 4 dividís 2 alhora (llevat que fossin iguals o oposats). Això ens ajuda a classificar nombres segons la seva divisibilitat.

**Demostració:**

Si \(a \mid b\), aleshores \(\exists k \in \mathbb{Z}\) tal que \(b = ak\).

Si \(b \mid a\), aleshores \(\exists m \in \mathbb{Z}\) tal que \(a = bm\).

Substituint \(b\):
\[
a = (ak)m = a(km).
\]

Si \(a \neq 0\), aleshores \(1 = km\), i per tant \(k = \pm 1\) i \(m = \pm 1\). Així:
\[
b = a(\pm 1) = \pm a.
\]

Si \(a = 0\), aleshores \(a \mid b\) implica \(b = 0\), i també es compleix \(a = \pm b = 0\).

**Exemple concret:**

\(2 \mid -2\) i \(-2 \mid 2\), per tant \(2 = -(-2)\).

## 10. Definició: màxim comú divisor

Siguin \(a,b \in \mathbb{Z}\), no tots dos zero. El màxim comú divisor de \(a\) i \(b\) es denota
\[
\operatorname{mcd}(a,b).
\]

**Explicació:**
El màxim comú divisor (mcd) és el nombre més gran possible que divideix alhora tant \(a\) com \(b\) sense deixar residu. És una eina fonamental per simplificar fraccions i resoldre equacions diofàntiques. Per definició, sempre és un nombre positiu, i com a mínim sempre existeix l'1 (que divideix tots els enters). La condició "no tots dos zero" és perquè si tots dos fossin zero, qualsevol nombre els dividiria i no tindria sentit parlar d'un "màxim".

## 11. Teorema (divisió euclidiana) "divisió normal"

Siguin \(a \in \mathbb{Z}\) i \(b \in \mathbb{Z}\) amb \(b > 0\). Aleshores existeixen únics \(q,r \in \mathbb{Z}\) tals que
\[
a = bq + r,
\]
i
\[
0 \le r < b.
\]

**Explicació:**
Aquest és el teorema que aprenem a primària quan fem divisions amb residu. Diu que si dividim un nombre enter \(a\) (dividend) per un nombre positiu \(b\) (divisor), obtenim un quocient \(q\) i un residu \(r\). La clau és que el residu sempre ha de ser més petit que el divisor (\(r < b\)) i no pot ser negatiu (\(r \ge 0\)). Els valors de \(q\) i \(r\) són únics per a cada parella \(a\) i \(b\).

## 12. Observació

\[
\operatorname{mcd}(a,b) = \operatorname{mcd}(a \pm b, b).
\]
Per tant,
\[
\operatorname{mcd}(a,b) = \operatorname{mcd}(b,r),
\]
on \(r\) és el residu de la divisió euclidiana de \(a\) per \(b\).

**Explicació:**
Aquesta observació és la base de l'Algorisme d'Euclides. La primera part diu que si sumem o restem \(b\) a \(a\), el màxim comú divisor no canvia. Això és perquè qualsevol nombre que divideixi \(a\) i \(b\) també dividirà \(a+b\) i \(a-b\) (propietat 9.ii). La segona part és la conseqüència directa d'aplicar la divisió euclidiana: com que \(a = bq + r\), aleshores \(r = a - bq\), i per la propietat anterior, el mcd de \((a,b)\) és el mateix que el mcd de \((b,r)\). Això ens permet anar reduint el problema a nombres cada cop més petits fins que el residu sigui zero, moment en què el divisor actual és el mcd.

## 14. Teorema (Identitat de Bézout)

Siguin \(a, b \in \mathbb{Z}\) amb \(a, b > 0\), i sigui \(d = \operatorname{mcd}(a,b)\). Aleshores existeixen \(\alpha, \beta \in \mathbb{Z}\) tals que:
\[
d = \alpha a + \beta b.
\]

El màxim comú divisor de dos nombres sempre es pot escriure com una combinació lineal entera d’aquests dos nombres. És a dir, el mcd no és només un divisor comú, sinó que és la combinació lineal més petita possible (en valor absolut) que es pot formar amb \(a\) i \(b\).

Els coeficients \(\alpha\) i \(\beta\) poden ser positius, negatius o zero. No són únics: si en trobem uns, també en podem trobar infinits afegint múltiples de \(b/d\) i \(-a/d\).

**Explicació:**
La Identitat de Bézout ens assegura que el màxim comú divisor de dos nombres sempre es pot "fabricar" sumant i restant múltiples d'aquests dos nombres. És a dir, no és només un nombre que els divideix, sinó que és una combinació lineal d'ells. Això té aplicacions molt potents, com ara trobar l'invers modular d'un nombre, que és essencial en criptografia (com el sistema RSA). Els coeficients \(\alpha\) i \(\beta\) es poden trobar aplicant l'Algorisme d'Euclides "cap enrere", com veurem a l'exemple.

**Exemple pràctic:**

Volem trobar \(\alpha, \beta\) tals que:
\[
d = \operatorname{mcd}(240,46) = \alpha \cdot 240 + \beta \cdot 46.
\]

**Algorisme d’Euclides:**
\[
240 = 46 \cdot 5 + 10
\]
\[
46 = 10 \cdot 4 + 6
\]
\[
10 = 6 \cdot 1 + 4
\]
\[
6 = 4 \cdot 1 + 2
\]
\[
4 = 2 \cdot 2 + 0
\]

Per tant, \(d = 2\).

**Ara cap enrere:**
\[
2 = 6 - 4 \cdot 1
\]
\[
4 = 10 - 6 \cdot 1 \implies 2 = 6 - (10 - 6) = 2 \cdot 6 - 10
\]
\[
6 = 46 - 10 \cdot 4 \implies 2 = 2(46 - 10 \cdot 4) - 10 = 2 \cdot 46 - 9 \cdot 10
\]
\[
10 = 240 - 46 \cdot 5 \implies 2 = 2 \cdot 46 - 9(240 - 46 \cdot 5) = 47 \cdot 46 - 9 \cdot 240
\]

Per tant:
\[
2 = (-9) \cdot 240 + 47 \cdot 46.
\]

Així, \(\alpha = -9\) i \(\beta = 47\).

**Explicació de l'exemple:**
Primer hem aplicat l'Algorisme d'Euclides per trobar el mcd (que és 2). Després, hem anat "cap enrere" aïllant els residus de cada divisió (començant per l'última divisió no nul·la, que és \(6 = 4 \cdot 1 + 2\)). En cada pas, substituïm el residu anterior per la seva expressió en funció dels nombres originals. Aquest procés de substitucions successives ens permet expressar el 2 final com una combinació de 240 i 46. Els coeficients que acompanyen 240 i 46 són \(\alpha = -9\) i \(\beta = 47\), respectivament.

## 14.1. Mètode matricial \(2\times 2\) per trobar \(\alpha\) i \(\beta\)

La Identitat de Bézout diu que, per a \(a,b\in\mathbb Z\) no tots dos zero, existeixen \(\alpha,\beta\in\mathbb Z\) tals que
\[
d=\operatorname{mcd}(a,b)=\alpha a+\beta b.
\]
Aquests coeficients es poden trobar de manera molt ordenada fent servir matrius \(2\times 2\).

### Idea

Representem la parella \((a,b)\) com un vector fila. Cada divisió euclidiana
\[
a=bq+r,\qquad 0\le r<b,
\]
es pot escriure com
\[
(a,b)
\begin{pmatrix}
0 & 1\\
1 & -q
\end{pmatrix}
=
(b,\ a-qb)
=
(b,r).
\]
Per tant, la matriu
\[
M_q=
\begin{pmatrix}
0 & 1\\
1 & -q
\end{pmatrix}
\]
transforma la parella \((a,b)\) en la parella \((b,r)\).

Si repetim aquest procés fins que el segon component sigui \(0\), obtindrem
\[
(a,b)\,M=(d,0),
\]
on \(d=\operatorname{mcd}(a,b)\) i \(M\) és el producte de totes les matrius \(M_q\) utilitzades.

Com que
\[
(a,b)
\begin{pmatrix}
m_{11} & m_{12}\\
m_{21} & m_{22}
\end{pmatrix}
=
(a m_{11}+b m_{21},\ a m_{12}+b m_{22}),
\]
la primera component de \((d,0)\) és
\[
d=a\,m_{11}+b\,m_{21}.
\]
Per tant, els coeficients de Bézout són
\[
\boxed{\alpha=m_{11},\qquad \beta=m_{21}}.
\]
És a dir, la **primera columna** de la matriu total \(M\) dona els coeficients \(\alpha\) i \(\beta\).

---

### Algorisme

1. Inicialitzem
   \[
   M=I_2=\begin{pmatrix}1&0\\0&1\end{pmatrix}.
   \]

2. Mentre els dos components de la parella actual \((a,b)\) siguin no nuls:
   - Fem la divisió euclidiana \(a=bq+r\).
   - Actualitzem la parella:
     \[
     (a,b)\leftarrow (b,r).
     \]
   - Actualitzem la matriu:
     \[
     M\leftarrow M
     \begin{pmatrix}
     0&1\\
     1&-q
     \end{pmatrix}.
     \]

3. Quan un component sigui \(0\), l’altre és \(d=\operatorname{mcd}(a,b)\).

4. La primera columna de \(M\) dona \(\alpha\) i \(\beta\):
   \[
   d=\alpha a+\beta b.
   \]

---

### Exemple 1: \(\operatorname{mcd}(240,46)\)

Volem
\[
2=\alpha\cdot 240+\beta\cdot 46.
\]

#### Divisions euclidianes

\[
240=5\cdot 46+10
\]
\[
46=4\cdot 10+6
\]
\[
10=1\cdot 6+4
\]
\[
6=1\cdot 4+2
\]
\[
4=2\cdot 2+0
\]

Els quocients són:
\[
q_1=5,\quad q_2=4,\quad q_3=1,\quad q_4=1,\quad q_5=2.
\]

#### Matrius associades

\[
M_1=
\begin{pmatrix}
0&1\\
1&-5
\end{pmatrix},
\quad
M_2=
\begin{pmatrix}
0&1\\
1&-4
\end{pmatrix},
\quad
M_3=
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix},
\quad
M_4=
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix},
\quad
M_5=
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix}.
\]

#### Producte total

\[
M=M_1M_2M_3M_4M_5
=
\begin{pmatrix}
-9 & 23\\
47 & -120
\end{pmatrix}.
\]

La primera columna és \((-9,47)\). Per tant:
\[
\boxed{2=(-9)\cdot 240+47\cdot 46}.
\]
Així,
\[
\boxed{\alpha=-9,\qquad \beta=47}.
\]

Comprovació:
\[
(-9)\cdot 240+47\cdot 46=-2160+2162=2.
\]

---

### Exemple 2: \(\operatorname{mcd}(31,12)\)

Aquest és l’exemple que apareix a la pissarra.

Volem
\[
1=\alpha\cdot 31+\beta\cdot 12.
\]

#### Divisions euclidianes

\[
31=2\cdot 12+7
\]
\[
12=1\cdot 7+5
\]
\[
7=1\cdot 5+2
\]
\[
5=2\cdot 2+1
\]
\[
2=2\cdot 1+0
\]

Els quocients són:
\[
q_1=2,\quad q_2=1,\quad q_3=1,\quad q_4=2,\quad q_5=2.
\]

#### Matrius associades

\[
M_1=
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix},
\quad
M_2=
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix},
\quad
M_3=
\begin{pmatrix}
0&1\\
1&-1
\end{pmatrix},
\quad
M_4=
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix},
\quad
M_5=
\begin{pmatrix}
0&1\\
1&-2
\end{pmatrix}.
\]

#### Producte total

\[
M=M_1M_2M_3M_4M_5
=
\begin{pmatrix}
-5 & 12\\
13 & -31
\end{pmatrix}.
\]

La primera columna és \((-5,13)\). Per tant:
\[
\boxed{1=(-5)\cdot 31+13\cdot 12}.
\]
Així,
\[
\boxed{\alpha=-5,\qquad \beta=13}.
\]

Comprovació:
\[
(-5)\cdot 31+13\cdot 12=-155+156=1.
\]

---

### Justificació del mètode

Cada matriu
\[
\begin{pmatrix}
0&1\\
1&-q
\end{pmatrix}
\]
té determinant
\[
0\cdot(-q)-1\cdot 1=-1.
\]
Per tant, és invertible sobre els enters. Això garanteix que totes les operacions conserven les combinacions lineals enteres.

Si després d’aplicar totes les matrius obtenim
\[
(a,b)M=(d,0),
\]
aleshores
\[
d=a\,m_{11}+b\,m_{21},
\]
on \(m_{11}\) i \(m_{21}\) són els elements de la primera columna de \(M\). Per tant:
\[
\boxed{d=\alpha a+\beta b}
\]
amb
\[
\boxed{\alpha=m_{11},\qquad \beta=m_{21}}.
\]

---

### Observació

Els coeficients \(\alpha\) i \(\beta\) no són únics. Si
\[
d=\alpha a+\beta b,
\]
aleshores per a qualsevol \(t\in\mathbb Z\) també tenim
\[
d=\left(\alpha+t\frac{b}{d}\right)a+
\left(\beta-t\frac{a}{d}\right)b.
\]
Això dona infinites parelles de coeficients de Bézout per al mateix mcd.

---

### Resum

Per trobar \(\alpha,\beta\) amb matrius \(2\times 2\):

1. Escriu cada divisió euclidiana \(a=bq+r\) com la matriu
   \[
   \begin{pmatrix}
   0&1\\
   1&-q
   \end{pmatrix}.
   \]
2. Multiplica totes aquestes matrius en ordre.
3. Quan la parella inicial \((a,b)\) es transformi en \((d,0)\), la primera columna de la matriu producte dona els coeficients:
   \[
   d=\alpha a+\beta b.
   \]

Aquest mètode és equivalent a l’Algorisme d’Euclides estès, però amb un format matricial molt net i fàcil de comprovar.

## 15. Corol·lari (Caracterització del màxim comú divisor)

Siguin \(a, b, d \in \mathbb{Z}\) amb \(a, b, d > 0\). Aleshores:
\[
d = \operatorname{mcd}(a,b) \iff
\begin{cases}
(1)\ d \mid a, \\
(2)\ d \mid b, \\
(3)\ \forall c \in \mathbb{Z},\ c \mid a \text{ i } c \mid b \implies c \mid d.
\end{cases}
\]

**Explicació:**
Aquest corol·lari ens dona la **definició formal i rigorosa** del màxim comú divisor. No només diu que \(d\) és un divisor comú (condicions 1 i 2), sinó que a més és el **més gran** possible (condició 3). 

La clau és la condició (3): si qualsevol altre nombre \(c\) també divideix tant \(a\) com \(b\), aleshores forçosament \(c\) ha de dividir \(d\). Això vol dir que \(d\) és un múltiple de *tots* els divisors comuns de \(a\) i \(b\), la qual cosa el converteix automàticament en el més gran de tots ells.

Aquesta caracterització és molt útil perquè ens permet demostrar propietats del mcd sense necessitat de calcular-lo explícitament. També és la definició que s'utilitza en àlgebra abstracta per generalitzar el concepte de mcd a altres estructures algebraiques (com els anells d'ideals principals).

**Exemple concret:**

Siguin \(a = 12\) i \(b = 18\). Sabem que \(d = \operatorname{mcd}(12,18) = 6\).

Comprovem les condicions:
1. \(6 \mid 12\) (cert, \(12 = 6 \cdot 2\)).
2. \(6 \mid 18\) (cert, \(18 = 6 \cdot 3\)).
3. Si prenem qualsevol \(c\) que divideixi 12 i 18 (per exemple, \(c = 2\) o \(c = 3\)), comprovem que també divideix 6:
   - \(2 \mid 12\) i \(2 \mid 18 \implies 2 \mid 6\) (cert).
   - \(3 \mid 12\) i \(3 \mid 18 \implies 3 \mid 6\) (cert).

Per tant, es compleix la definició i \(6 = \operatorname{mcd}(12,18)\).







d=mcd(a,b) -->
d|a
d|b
c|a, c|b --> c <= d llavors c|d?
compte!




d=mcd(a,b) <-- evident perque c|d -> c <= d


