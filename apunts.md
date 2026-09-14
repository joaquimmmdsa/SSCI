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
