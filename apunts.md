Apunts SSCI Divisibilitat i mcd Apunts: Matrius mòdul _m_ , determinants i invertibilitat 

Apunts 

October 16, 2026 

Contents 

|1<br>8.|Divisi|bilitat<br>8|
|---|---|---|
|1.1|Expli|cació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>9|
|1.2|Exem|ples<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>9|
|2<br>9.|Propie|tats de la divisibilitat<br>9|
|2.1|9.i) T|ransitivitat<br>. . . . . . . . . . . . . . . . . . . . . . . . .<br>9|
||2.1.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . .<br>9|
||2.1.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . .<br>9|
||2.1.3|Exemple concret (només un cas)<br>. . . . . . . . . . . .<br>10|
|2.2|9.ii)|Linealitat (suma i resta)<br>. . . . . . . . . . . . . . . . . .<br>10|
||2.2.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . .<br>10|
||2.2.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . .<br>10|
||2.2.3|Exemple concret (només un cas)<br>. . . . . . . . . . . .<br>10|
|2.3|9.iii)|Factor comú . . . . . . . . . . . . . . . . . . . . . . . . .<br>10|
||2.3.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . .<br>11|
||2.3.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . .<br>11|
||2.3.3|Exemple concret<br>. . . . . . . . . . . . . . . . . . . . .<br>11|
|2.4|9.iv)|Contraexemple: _a | bc_⇏_a | b_ o _a | c_<br>. . . . . . . . . . .<br>11|
||2.4.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . .<br>11|
||2.4.2|Contraexemple . . . . . . . . . . . . . . . . . . . . . .<br>11|
|2.5|9.v)|Antisimetria (llevat de signe) . . . . . . . . . . . . . . . .<br>12|
||2.5.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . .<br>12|
||2.5.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . .<br>12|
||2.5.3|Exemple concret<br>. . . . . . . . . . . . . . . . . . . . .<br>12|



1 

|3|10.|Denició: màxim comú divisor|12|
|---|---|---|---|
||3.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|12|
|4|11.|Teorema (divisió euclidiana) "divisió normal"|13|
||4.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|13|
|5|12.|Observació|13|
||5.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|13|
|6|14.|Teorema (Identitat de Bézout)|13|
||6.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|14|
||6.2|Exemple pràctic . . . . . . . . . . . . . . . . . . . . . . . . . .|14|
||6.3|Algorisme d'Euclides . . . . . . . . . . . . . . . . . . . . . . .|14|
||6.4|Ara cap enrere<br>. . . . . . . . . . . . . . . . . . . . . . . . . .|14|
||6.5|Explicació de l'exemple . . . . . . . . . . . . . . . . . . . . . .|15|
|7|14.1|. Mètode matricial 2_×_2 per trobar _α_ i _β_|15|
||7.1|Idea<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|15|
||7.2|Algorisme . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|16|
||7.3|Exemple 1: mcd(240_,_46) . . . . . . . . . . . . . . . . . . . . .|16|
|||7.3.1<br>Divisions euclidianes . . . . . . . . . . . . . . . . . . .|17|
|||7.3.2<br>Matrius associades . . . . . . . . . . . . . . . . . . . .|17|
|||7.3.3<br>Producte total<br>. . . . . . . . . . . . . . . . . . . . . .|17|
||7.4|Exemple 2: mcd(31_,_12)<br>. . . . . . . . . . . . . . . . . . . . .|17|
|||7.4.1<br>Divisions euclidianes . . . . . . . . . . . . . . . . . . .|18|
|||7.4.2<br>Matrius associades . . . . . . . . . . . . . . . . . . . .|18|
|||7.4.3<br>Producte total<br>. . . . . . . . . . . . . . . . . . . . . .|18|
||7.5|Justicació del mètode . . . . . . . . . . . . . . . . . . . . . .|19|
||7.6|Observació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|19|
||7.7|Resum . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|19|
|8|15.|Corol·lari (Caracterització del màxim comú divisor)|20|
||8.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|20|
||8.2|Exemple concret<br>. . . . . . . . . . . . . . . . . . . . . . . . .|20|
|9|16.|Denició: nombres coprimers|21|
||9.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|21|
||9.2|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|21|
||9.3|Per què és equivalent a l'existència de _α, β_? . . . . . . . . . .|21|
|||9.3.1<br>(_⇒_) Si mcd(_a, b_) = 1, aleshores existeixen _α, β ∈_Z||
|||tals que _αa_+_βb_= 1. . . . . . . . . . . . . . . . . . . .|22|



2 

||9.3.2<br>(_⇐_) Si existeixen _α, β ∈_Z tals que _αa_ + _βb_ = 1,||
|---|---|---|
||aleshores mcd(_a, b_) = 1.<br>. . . . . . . . . . . . . . . . .|22|
|9.4|Exemples<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . .|22|
|10 17.|Corol·lari: després de dividir pel mcd, els quocients són||
|copr|imers|23|
|10.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|23|
|10.2|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|23|
|10.3|Demostració . . . . . . . . . . . . . . . . . . . . . . . . . . . .|24|
|10.4|Importància . . . . . . . . . . . . . . . . . . . . . . . . . . . .|24|
|11 18.|Corol·lari: lema d'Euclides|25|
|11.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|25|
|11.2|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|25|
|11.3|Demostració . . . . . . . . . . . . . . . . . . . . . . . . . . . .|25|
|11.4|Exemple correcte . . . . . . . . . . . . . . . . . . . . . . . . .|26|
|11.5|Contraexemple si no són coprimers . . . . . . . . . . . . . . .|26|
|11.6|Importància . . . . . . . . . . . . . . . . . . . . . . . . . . . .|27|
|11.7|Resum . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|27|
|12 Exe|rcici: MCD de _a_+_b_ i _a −b_|27|
|12.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|27|
|12.2|Solució . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|27|
|12.3|Observació sobre la paritat<br>. . . . . . . . . . . . . . . . . . .|28|
|12.4|Exemples<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . .|29|
|12.5|Nota . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|29|
|12.6|Resum . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|30|
|13 Apu|nts: Exercicis de divisibilitat i mcd|30|
|13.1|Recordatori: propietat fonamental del mcd (apartat 12)<br>. . .|30|
|13.2|Exercici 1.3: És cert que mcd(3_a −b, b −_2_a_) = mcd(_a, b_)? . .|30|
|13.3|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|30|
|13.4|Solució pas a pas . . . . . . . . . . . . . . . . . . . . . . . . .|30|
|13.5 <br>|Explicació alternativa amb divisors comuns<br>. . . . . . . . . .<br>|31|
|13.6|Exercici 1.7: Demostra que la fracció <sup>4</sup><sup>_n_ + 5</sup><br>2_n_+ 3 <sup>és irreductible</sup>||
||<br>per a tot _n ≥_1. . . . . . . . . . . . . . . . . . . . . . . . . . .|31|
|13.7|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|31|
|13.8|Solució pas a pas . . . . . . . . . . . . . . . . . . . . . . . . .|32|
|13.9|Exemples<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . .|32|
|13.10|Nota . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|32|



3 

|14 19. Equaci|ons diofàntiques (Diofant d'Alexandria)<br>33|
|---|---|
|14.1 Enunci|at . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>33|
|14.2 Explic|ació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>33|
|14.3 Demos|tració . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>33|
|14.3.1|(_⇒_) Si hi ha solució, aleshores _d | c_.<br>. . . . . . . . . .<br>33|
|14.3.2|(_⇐_) Si _d | c_, aleshores hi ha solució.<br>. . . . . . . . . .<br>34|
|14.4 Exemp|le 1: equació sense solució . . . . . . . . . . . . . . . .<br>34|
|14.5 Exemp|le 2: equació amb solució . . . . . . . . . . . . . . . . .<br>35|
|14.5.1|Pas 1: calcular _d_ i comprovar que divideix _c_. . . . . . .<br>35|
|14.5.2|Pas 2: trobar coecients de Bézout. . . . . . . . . . . .<br>35|
|14.5.3|Pas 3: multiplicar per _c_<sup>_′_</sup>. . . . . . . . . . . . . . . . . .<br>35|
|14.5.4|Pas 4: comprovació.<br>. . . . . . . . . . . . . . . . . . .<br>35|
|14.6 Resum|. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>36|
|14.7 És l'ún|ica solució? Hi ha més solucions? . . . . . . . . . . . .<br>36|
|14.7.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . .<br>36|
|14.7.2|Explicació . . . . . . . . . . . . . . . . . . . . . . . . .<br>36|
|14.7.3|Demostració que són solucions<br>. . . . . . . . . . . . .<br>37|
|14.7.4|Exemple: 27_x_+ 13_y_ = 1250 . . . . . . . . . . . . . . .<br>37|
|14.7.5|Nota: són totes . . . . . . . . . . . . . . . . . . . . . .<br>38|
|14.7.6|Demostració que aquestes són totes les solucions<br>. . .<br>38|
|14.8 Exerci|ci: endevinar la data de naixement . . . . . . . . . . . .<br>40|
|14.8.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . .<br>40|
|14.8.2|Explicació . . . . . . . . . . . . . . . . . . . . . . . . .<br>40|
|14.8.3|Resolució pas a pas amb _c_= 256 . . . . . . . . . . . .<br>40|
|14.8.4|Comprovació<br>. . . . . . . . . . . . . . . . . . . . . . .<br>41|
|15 24. Lema|d'Euclides per a primers<br>42|
|15.1 Enunci|at . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>42|
|15.2 Explic|ació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>42|
|16 25. Teore|ma fonamental de l'aritmètica<br>42|
|16.1 Enunci|at . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>42|
|16.2 Demos|tració resumida . . . . . . . . . . . . . . . . . . . . . .<br>43|
|16.2.1|Existència . . . . . . . . . . . . . . . . . . . . . . . . .<br>43|
|16.2.2|Lema clau . . . . . . . . . . . . . . . . . . . . . . . . .<br>43|
|16.2.3|Unicitat . . . . . . . . . . . . . . . . . . . . . . . . . .<br>43|
|16.3 Exemp|les<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>43|
|16.4 Observ|acions sobre la unicitat . . . . . . . . . . . . . . . . . .<br>43|
|16.5 Import|ància . . . . . . . . . . . . . . . . . . . . . . . . . . . .<br>44|



4 

|17 26.|Hi ha|innits nombres primers|44|
|---|---|---|---|
|17.1|Enunci|at . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|44|
|17.2|Demos|tració (Euclides) . . . . . . . . . . . . . . . . . . . . . .|44|
|18 28.|Propo|sició: mcd i mcm mitjançant la factorització en||
|prim|ers||45|
|18.1|Enunci|at . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|45|
|18.2|Què só|n _ri_ i _si_? . . . . . . . . . . . . . . . . . . . . . . . . . .|45|
|18.3|Per qu|è funciona? . . . . . . . . . . . . . . . . . . . . . . . . .|45|
||18.3.1|Màxim comú divisor . . . . . . . . . . . . . . . . . . .|45|
||18.3.2|Mínim comú múltiple<br>. . . . . . . . . . . . . . . . . .|46|
|18.4|Exemp|le complet . . . . . . . . . . . . . . . . . . . . . . . . .|46|
||18.4.1|MCD<br>. . . . . . . . . . . . . . . . . . . . . . . . . . .|46|
||18.4.2|MCM<br>. . . . . . . . . . . . . . . . . . . . . . . . . . .|47|
|18.5|Propie|tat important<br>. . . . . . . . . . . . . . . . . . . . . . .|47|
|18.6|Observ|acions<br>. . . . . . . . . . . . . . . . . . . . . . . . . . .|47|
|19 29.|Aritm|ètica modular|48|
|19.1|Denic|ió . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|48|
|19.2|Explic|ació: per què equival a tenir el mateix residu?<br>. . . . .|48|
|19.3|Exemp|les amb _m_= 5 . . . . . . . . . . . . . . . . . . . . . . .|48|
||19.3.1|Exemple 1 . . . . . . . . . . . . . . . . . . . . . . . . .|48|
||19.3.2|Exemple 2 . . . . . . . . . . . . . . . . . . . . . . . . .|49|
|20 30.|La con|gruència mòdul _m_ és una relació d'equivalència|49|
|20.1|Record|atori: què vol dir _a ≡b_ (mod _m_) . . . . . . . . . . . .|49|
|20.2|Què és|una relació d'equivalència?<br>. . . . . . . . . . . . . . .|49|
|20.3|Propie|tat reexiva<br>. . . . . . . . . . . . . . . . . . . . . . . .|49|
||20.3.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . .|49|
||20.3.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . .|50|
||20.3.3|Exemple . . . . . . . . . . . . . . . . . . . . . . . . . .|50|
|20.4|Propie|tat simètrica . . . . . . . . . . . . . . . . . . . . . . . .|50|
||20.4.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . .|50|
||20.4.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . .|50|
||20.4.3|Exemple . . . . . . . . . . . . . . . . . . . . . . . . . .|50|
|20.5|Propie|tat transitiva . . . . . . . . . . . . . . . . . . . . . . . .|50|
||20.5.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . .|50|
||20.5.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . .|51|
||20.5.3|Exemple . . . . . . . . . . . . . . . . . . . . . . . . . .|51|
|20.6|Conseq|üència: classes de residus<br>. . . . . . . . . . . . . . . .|51|



5 

|20.7|Resum . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|52|
|---|---|---|
|21 31.|Denició: classes d'equivalència mòdul _m_|52|
|21.1|Denició . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|52|
|21.2|Formes equivalents . . . . . . . . . . . . . . . . . . . . . . . .|52|
|21.3|Exemple amb _m_= 5 . . . . . . . . . . . . . . . . . . . . . . .|52|
|21.4|Observació important<br>. . . . . . . . . . . . . . . . . . . . . .|53|
|22 32.|Observació: partició de Z en _m_ classes|53|
|22.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|53|
|22.2|Demostració . . . . . . . . . . . . . . . . . . . . . . . . . . . .|53|
||22.2.1 1. Existència<br>. . . . . . . . . . . . . . . . . . . . . . .|53|
||22.2.2 2. Unicitat<br>. . . . . . . . . . . . . . . . . . . . . . . .|54|
||22.2.3 3. Disjunció . . . . . . . . . . . . . . . . . . . . . . . .|54|
|22.3|El conjunt quocient Z_/m_Z . . . . . . . . . . . . . . . . . . . .|54|
||22.3.1 Exemple amb _m_= 5 . . . . . . . . . . . . . . . . . . .|54|
|22.4|Nota . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|54|
|23 33.|Observació:<br>compatibilitat de la congruència amb la||
|sum|a i el producte|55|
|23.1|Enunciat . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|55|
||23.1.1 (i) Compatibilitat amb la suma . . . . . . . . . . . . .|55|
||23.1.2 (ii) Compatibilitat amb el producte . . . . . . . . . . .|55|
|23.2|Demostració de (i) . . . . . . . . . . . . . . . . . . . . . . . .|55|
|23.3|Demostració de (ii) . . . . . . . . . . . . . . . . . . . . . . . .|56|
|23.4|Observació addicional: compatibilitat amb la resta<br>. . . . . .|56|
|23.5|Exemple amb _m_= 5 . . . . . . . . . . . . . . . . . . . . . . .|56|
|24 34.|Teorema: Z_/m_Z és un anell commutatiu|56|
|24.1|Idea<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|56|
|24.2|Denició de les operacions . . . . . . . . . . . . . . . . . . . .|57|
|24.3|Primer: les operacions estan ben denides . . . . . . . . . . .|57|
|24.4|Segon: Z_/m_Z amb aquestes operacions és un anell commutatiu|57|
||24.4.1 Suma<br>. . . . . . . . . . . . . . . . . . . . . . . . . . .|58|
||24.4.2 Producte<br>. . . . . . . . . . . . . . . . . . . . . . . . .|58|
||24.4.3 Distributivitat<br>. . . . . . . . . . . . . . . . . . . . . .|58|
|24.5|Conclusió<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . .|59|
|24.6|Exemple amb Z_/_5Z . . . . . . . . . . . . . . . . . . . . . . . .|59|
|24.7|Nota nal . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|59|



6 

|25 35. Proposició: invertibles, cossos i divisors de zero|59|
|---|---|
|25.1 Recordatori . . . . . . . . . . . . . . . . . . . . . . . . . . .|.<br>60|
|25.2 (i) [_a_]_m_ és invertible _⇐⇒a_ i _m_ són coprimers<br>. . . . . . .|.<br>60|
|25.2.1 Demostració . . . . . . . . . . . . . . . . . . . . . . .|.<br>60|
|25.2.2 Exemple amb _m_= 5 . . . . . . . . . . . . . . . . . .|.<br>60|
|25.2.3 Exemple amb _m_= 6 . . . . . . . . . . . . . . . . . .|.<br>60|
|25.3 (ii) Z_/m_Z és un cos _⇐⇒m_ és primer . . . . . . . . . . . .|.<br>61|
|25.3.1 Demostració . . . . . . . . . . . . . . . . . . . . . . .|.<br>61|
|25.3.2 Exemples<br>. . . . . . . . . . . . . . . . . . . . . . . .|.<br>61|
|25.4 (iii) Si [_a_]_m_ no és invertible, aleshores és un divisor de zero .|.<br>61|
|25.4.1 Enunciat . . . . . . . . . . . . . . . . . . . . . . . . .|.<br>61|
|25.4.2 Demostració . . . . . . . . . . . . . . . . . . . . . . .|.<br>61|
|25.4.3 Exemple amb _m_= 6 . . . . . . . . . . . . . . . . . .|.<br>62|
|25.4.4 Conseqüència . . . . . . . . . . . . . . . . . . . . . .|.<br>62|
|26 36. Observació: llei de cancel·lació|62|
|26.1 (i) Demostració de la cancel·lació per elements invertibles<br>.|.<br>63|
|26.1.1 Exemple amb _m_= 5 . . . . . . . . . . . . . . . . . .|.<br>63|
|26.2 (ii) Si [_a_]_m_ no és invertible, la cancel·lació pot fallar . . . . .|.<br>63|
|26.2.1 Exemple amb _m_= 6 . . . . . . . . . . . . . . . . . .|.<br>63|
|26.3 Conclusió<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . .|.<br>64|
|26.4 Resum nal . . . . . . . . . . . . . . . . . . . . . . . . . . .|.<br>64|
|27 Introducció|65|
|28 Anell Z_/m_Z|65|
|28.1 Denicions bàsiques<br>. . . . . . . . . . . . . . . . . . . . . .|.<br>65|
|28.2 Matrius _Mn_(Z_/m_Z)<br>. . . . . . . . . . . . . . . . . . . . . .|.<br>65|
|29 Determinants mòdul _m_|66|
|29.1 Denició . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|.<br>66|
|29.2 Propietats que es conserven . . . . . . . . . . . . . . . . . .|.<br>66|
|29.3 Exemple 1: determinant mòdul 6** . . . . . . . . . . . . . .|.<br>66|
|29.4 Exemple 2: determinant mòdul 5** . . . . . . . . . . . . . .|.<br>66|
|30 Invertibilitat de matrius mòdul _m_|67|
|30.1 Proposició . . . . . . . . . . . . . . . . . . . . . . . . . . . .|.<br>67|
|30.2 Demostració . . . . . . . . . . . . . . . . . . . . . . . . . . .|.<br>67|
|30.3 Fórmula clàssica de la inversa . . . . . . . . . . . . . . . . .|.<br>67|
|30.4 Exemple 3: inversa mòdul 5** . . . . . . . . . . . . . . . . .|.<br>68|



7 

|30.5 <br>30.6|Exemple 4: inversa mòdul 6 amb determinant unitat** . . . .<br> Exemple 5: determinant no unitat i matriu no invertible** . .|68<br>68|
|---|---|---|
|31 Àlge|bra lineal sobre Z_/p_Z amb _p_ primer|69|
|31.1|El cos F_p_<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . .|69|
|31.2|Què funciona exactament igual? . . . . . . . . . . . . . . . . .|69|
|31.3|Exemple 6: sistema sobre F5 per la inversa**<br>. . . . . . . . .|69|
|31.4|Exemple 7: regla de Cramer sobre F5 . . . . . . . . . . . . . .|70|
|31.5|Exemple 8: dependència lineal sobre F5<br>. . . . . . . . . . . .|70|
|32 Qua|n _m_ no és primer: complicacions|70|
|32.1|No és un cos . . . . . . . . . . . . . . . . . . . . . . . . . . . .|70|
|32.2|Conseqüències . . . . . . . . . . . . . . . . . . . . . . . . . . .|71|
|32.3|Exemple 9: sistema sobre Z_/_6Z sense solució** . . . . . . . .|71|
|32.4|Exemple 10: sistema sobre Z_/_6Z amb diverses solucions** . .|72|
|33 Res|um|72|
|34 Exe|rcicis proposats|73|
|35 Solu|cions breus|73|
|35.1|1a<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|73|
|35.2|1b<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|73|
|35.3|1c<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|74|
|35.4|2 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|74|
|35.5|3 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|74|
|35.6|4 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|74|
|35.7|5 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|74|
|36 40.|Teorema xinès del residu (Chinese remainder theorem)|75|
|36.1|Explicació . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|75|
|36.2|Resolució pas a pas . . . . . . . . . . . . . . . . . . . . . . . .|75|
||36.2.1 Pas 1: combinar les dues primeres congruències . . . .|75|
||36.2.2 Pas 2: imposar la tercera congruència<br>. . . . . . . . .|76|
|36.3|Solució general<br>. . . . . . . . . . . . . . . . . . . . . . . . . .|76|
|36.4|Comprovació<br>. . . . . . . . . . . . . . . . . . . . . . . . . . .|77|



# 1 8. Divisibilitat 

Siguin _a, b ∈_ Z . 

8 

_a | b ⇐⇒ a_ divideix _b ⇐⇒ b_ és múltiple de _a ⇐⇒ b_ és divisible per _a ⇐⇒∃c ∈_ Z tal que _b_ = _ac._ 

## 1.1 Explicació 

La divisibilitat és un concepte fonamental que descriu quan un nombre cap dins d'un altre sense deixar residu. La notació _a | b_ es llegeix "a divideix b". Fixa't que la condició principal és que existeixi un enter _c_ que, multiplicat per _a_ , ens doni exactament _b_ . És a dir, _b_ es pot construir com a múltiples de _a_ . 

## 1.2 Exemples 



2 ∤ 5 perquè no existeix cap _c ∈_ Z tal que 5 = 2 _c._ 

# 2 9. Propietats de la divisibilitat 

## 2.1 9.i) Transitivitat 

Siguin _a, b, c ∈_ Z . Si _a | b_ i _b | c_ , aleshores _a | c_ . 

### 2.1.1 Explicació 

La transitivitat és com una cadena de dominó. Si _a_ cap dins de _b_ (és a dir, _b_ és múltiple de _a_ ), i al seu torn _b_ cap dins de _c_ , aleshores forçosament _a_ també ha de cabre dins de _c_ . Això ens permet encadenar divisions i simplicar problemes. 

### 2.1.2 Demostració 

Si _a | b_ , aleshores _∃k ∈_ Z tal que _b_ = _ak_ . Si _b | c_ , aleshores _∃m ∈_ Z tal que _c_ = _bm_ . Substituint _b_ : 

_c_ = ( _ak_ ) _m_ = _a_ ( _km_ ) _._ 

Com que _km ∈_ Z , tenim que _a | c_ . 

9 

### 2.1.3 Exemple concret (només un cas) 



## 2.2 9.ii) Linealitat (suma i resta) 

Siguin _a, b, c ∈_ Z . Si _a | b_ i _a | c_ , aleshores 



### 2.2.1 Explicació 

Si un nombre divideix dos nombres diferents, també divideix qualsevol combinació lineal seva. Pensa-hi com a grups d'objectes: si pots agrupar _b_ objectes en grups de mida _a_ , i també pots agrupar _c_ objectes en grups de mida _a_ , aleshores si els ajuntes tots, o si en treus una part, la mida del grup _a_ encara funciona perfectament. Aquesta propietat és la base per a moltes demostracions algebraiques. 

### 2.2.2 Demostració 

Si _a | b_ , aleshores _∃k ∈_ Z tal que _b_ = _ak_ . Si _a | c_ , aleshores _∃m ∈_ Z tal que _c_ = _am_ . Aleshores: 



Com que _k_ + _m ∈_ Z i _k − m ∈_ Z , tenim que 



### 2.2.3 Exemple concret (només un cas) 



## 2.3 9.iii) Factor comú 

Siguin _a, b, c ∈_ Z . Si _a | b_ , aleshores _a | bc_ . 

10 

### 2.3.1 Explicació 

Si _a_ ja divideix _b_ , aleshores dividirà qualsevol múltiple de _b_ . És com dir: si 2 divideix 6, aleshores 2 també dividirà 6 multiplicat per qualsevol nombre (per exemple, 6Ö5=30, i 2 divideix 30). La divisibilitat es propaga cap amunt quan multipliquem. 

### 2.3.2 Demostració 

Si _a | b_ , aleshores _∃k ∈_ Z tal que _b_ = _ak_ . Multiplicant per _c_ : 



Com que _kc ∈_ Z , tenim que _a | bc_ . 

### 2.3.3 Exemple concret 

2 _|_ 6 , per tant 2 _|_ 6 _·_ 5 = 30 . Comprovació: 6 = 2 _·_ 3 , així 30 = 6 _·_ 5 = 2 _·_ 3 _·_ 5 = 2 _·_ 15 . 

## 2.4 9.iv) Contraexemple: _a | bc_ ⇏ _a | b_ o _a | c_ 

En general, que _a_ divideixi un producte _bc_ no implica que divideixi cap dels factors. 

### 2.4.1 Explicació 

Aquesta és una trampa molt comuna. El fet que un nombre divideixi un producte no vol dir que divideixi necessàriament cadascun dels factors per separat. El nombre pot estar format per la combinació de parts dels dos factors. Cal anar amb compte i no assumir aquesta propietat sense demostració, perquè és falsa en general. 

### 2.4.2 Contraexemple 



però 



Per tant, _a | bc_ no implica _a | b_ ni _a | c_ . 

11 

## 2.5 9.v) Antisimetria (llevat de signe) 

Siguin _a, b ∈_ Z . Si _a | b_ i _b | a_ , aleshores 



### 2.5.1 Explicació 

Si dos nombres es divideixen mútuament, vol dir que tenen exactament la mateixa "grandària" en valor absolut. L'únic que pot canviar és el signe (positiu o negatiu). Per exemple, 2 i -2 es divideixen mútuament, però no podria ser que 2 dividís 4 i 4 dividís 2 alhora (llevat que fossin iguals o oposats). Això ens ajuda a classicar nombres segons la seva divisibilitat. 

### 2.5.2 Demostració 

Si _a | b_ , aleshores _∃k ∈_ Z tal que _b_ = _ak_ . Si _b | a_ , aleshores _∃m ∈_ Z tal que _a_ = _bm_ . Substituint _b_ : 



Si _a̸_ = 0 , aleshores 1 = _km_ , i per tant _k_ = _±_ 1 i _m_ = _±_ 1 . Així: _b_ = _a_ ( _±_ 1) = _±a._ 

Si _a_ = 0 , aleshores _a | b_ implica _b_ = 0 , i també es compleix _a_ = _±b_ = 0 . 

### 2.5.3 Exemple concret 

2 _| −_ 2 i _−_ 2 _|_ 2 , per tant 2 = _−_ ( _−_ 2) . 

# 3 10. Denició: màxim comú divisor 

Siguin _a, b ∈_ Z , no tots dos zero. El màxim comú divisor de _a_ i _b_ es denota 



## 3.1 Explicació 

El màxim comú divisor (mcd) és el nombre més gran possible que divideix alhora tant _a_ com _b_ sense deixar residu. És una eina fonamental per simplicar fraccions i resoldre equacions diofàntiques. Per denició, sempre és un nombre positiu, i com a mínim sempre existeix l'1 (que divideix tots els enters). La condició "no tots dos zero" és perquè si tots dos fossin zero, qualsevol nombre els dividiria i no tindria sentit parlar d'un "màxim". 

12 

# 4 11. Teorema (divisió euclidiana) "divisió normal" 

Siguin _a ∈_ Z i _b ∈_ Z amb _b >_ 0 . Aleshores existeixen únics _q, r ∈_ Z tals que 



i 



## 4.1 Explicació 

Aquest és el teorema que aprenem a primària quan fem divisions amb residu. Diu que si dividim un nombre enter _a_ (dividend) per un nombre positiu _b_ (divisor), obtenim un quocient _q_ i un residu _r_ . La clau és que el residu sempre ha de ser més petit que el divisor ( _r < b_ ) i no pot ser negatiu ( _r ≥_ 0 ). Els valors de _q_ i _r_ són únics per a cada parella _a_ i _b_ . 

# 5 12. Observació 



Per tant, 



on _r_ és el residu de la divisió euclidiana de _a_ per _b_ . 

## 5.1 Explicació 

Aquesta observació és la base de l'Algorisme d'Euclides. La primera part diu que si sumem o restem _b_ a _a_ , el màxim comú divisor no canvia. Això és perquè qualsevol nombre que divideixi _a_ i _b_ també dividirà _a_ + _b_ i _a − b_ (propietat 9.ii). La segona part és la conseqüència directa d'aplicar la divisió euclidiana: com que _a_ = _bq_ + _r_ , aleshores _r_ = _a − bq_ , i per la propietat anterior, el mcd de ( _a, b_ ) és el mateix que el mcd de ( _b, r_ ) . Això ens permet anar reduint el problema a nombres cada cop més petits ns que el residu sigui zero, moment en què el divisor actual és el mcd. 

# 6 14. Teorema (Identitat de Bézout) 

Siguin _a, b ∈_ Z amb _a, b >_ 0 , i sigui _d_ = mcd( _a, b_ ) . Aleshores existeixen _α, β ∈_ Z tals que: 

_d_ = _αa_ + _βb._ 

13 

El màxim comú divisor de dos nombres sempre es pot escriure com una combinació lineal entera d'aquests dos nombres. És a dir, el mcd no és només un divisor comú, sinó que és la combinació lineal més petita possible (en valor absolut) que es pot formar amb _a_ i _b_ . 

Els coecients _α_ i _β_ poden ser positius, negatius o zero. No són únics: si en trobem uns, també en podem trobar innits afegint múltiples de _b/d_ i _−a/d_ . 

## 6.1 Explicació 

La Identitat de Bézout ens assegura que el màxim comú divisor de dos nombres sempre es pot "fabricar" sumant i restant múltiples d'aquests dos nombres. És a dir, no és només un nombre que els divideix, sinó que és una combinació lineal d'ells. Això té aplicacions molt potents, com ara trobar l'invers modular d'un nombre, que és essencial en criptograa (com el sistema RSA). Els coecients _α_ i _β_ es poden trobar aplicant l'Algorisme d'Euclides "cap enrere", com veurem a l'exemple. 

## 6.2 Exemple pràctic 

Volem trobar _α, β_ tals que: 



## 6.3 Algorisme d'Euclides 





Per tant, _d_ = 2 . 

## 6.4 Ara cap enrere 





14 

10 = 240 _−_ 46 _·_ 5 = _⇒_ 2 = 2 _·_ 46 _−_ 9(240 _−_ 46 _·_ 5) = 47 _·_ 46 _−_ 9 _·_ 240 Per tant: 

2 = ( _−_ 9) _·_ 240 + 47 _·_ 46 _._ 

Així, _α_ = _−_ 9 i _β_ = 47 . 

## 6.5 Explicació de l'exemple 

Primer hem aplicat l'Algorisme d'Euclides per trobar el mcd (que és 2). Després, hem anat "cap enrere" aïllant els residus de cada divisió (començant per l'última divisió no nul·la, que és 6 = 4 _·_ 1+2 ). En cada pas, substituïm el residu anterior per la seva expressió en funció dels nombres originals. Aquest procés de substitucions successives ens permet expressar el 2 nal com una combinació de 240 i 46. Els coecients que acompanyen 240 i 46 són _α_ = _−_ 9 i _β_ = 47 , respectivament. 

# 7 14.1. Mètode matricial 2 _×_ 2 per trobar _α_ i _β_ 

La Identitat de Bézout diu que, per a _a, b ∈_ Z no tots dos zero, existeixen _α, β ∈_ Z tals que 

_d_ = mcd( _a, b_ ) = _αa_ + _βb._ 

Aquests coecients es poden trobar de manera molt ordenada fent servir matrius 2 _×_ 2 . 

## 7.1 Idea 

Representem la parella ( _a, b_ ) com un vector la. Cada divisió euclidiana 



1 es pot escriure com _\_ [ (a,b) = (b, _\_ a-qb) = (b,r). _\_ ] Per tant, la �10 _−q_ � 1 matriu _\_ [ Mq= _\_ ] transforma la parella ( _a, b_ ) en la parella ( _b, r_ ) . �10 _−q_ � Si repetim aquest procés ns que el segon component sigui 0 , obtindrem 



on _d_ = mcd( _a, b_ ) i _M_ és el producte de totes les matrius _Mq_ utilitzades. 

15 



primera component de ( _d,_ 0) és 



Per tant, els coecients de Bézout són 



És a dir, la primera columna de la matriu total _M_ dona els coecients _α_ i _β_ . 

## 7.2 Algorisme 

1. Inicialitzem 



2. Mentre els dos components de la parella actual ( _a, b_ ) siguin no nuls: 

 Fem la divisió euclidiana _a_ = _bq_ + _r_ . 

 Actualitzem la parella: 



 Actualitzem la matriu: 



3. Quan un component sigui 0 , l'altre és _d_ = mcd( _a, b_ ) . 

4. La primera columna de _M_ dona _α_ i _β_ : 



7.3 Exemple 1: mcd(240 _,_ 46) 

Volem 



16 

### 7.3.1 Divisions euclidianes 



Els quocients són: 



7.3.2 Matrius associades 



7.3.3 Producte total 



La primera columna és ( _−_ 9 _,_ 47) . Per tant: 



Així, 



Comprovació: 



## 7.4 Exemple 2: mcd(31 _,_ 12) 

Aquest és l'exemple que apareix a la pissarra. Volem 



17 

### 7.4.1 Divisions euclidianes 



Els quocients són: 



7.4.2 Matrius associades 



7.4.3 Producte total 



La primera columna és ( _−_ 5 _,_ 13) . Per tant: 



Així, 



Comprovació: 



18 

## 7.5 Justicació del mètode 





Per tant, és invertible sobre els enters. Això garanteix que totes les operacions conserven les combinacions lineals enteres. 

Si després d'aplicar totes les matrius obtenim 



aleshores 



on _m_ 11 i _m_ 21 són els elements de la primera columna de _M_ . Per tant: 



amb 



## 7.6 Observació 

Els coecients _α_ i _β_ no són únics. Si 



aleshores per a qualsevol _t ∈_ Z també tenim 



Això dona innites parelles de coecients de Bézout per al mateix mcd. 

## 7.7 Resum 

Per trobar _α, β_ amb matrius 2 _×_ 2 : 

1. Escriu cada divisió euclidiana _a_ = _bq_ + _r_ com la matriu 



19 

2. Multiplica totes aquestes matrius en ordre. 

3. Quan la parella inicial ( _a, b_ ) es transformi en ( _d,_ 0) , la primera columna de la matriu producte dona els coecients: 

_d_ = _αa_ + _βb._ 

Aquest mètode és equivalent a l'Algorisme d'Euclides estès, però amb un format matricial molt net i fàcil de comprovar. 

# 8 15. Corol·lari (Caracterització del màxim comú divisor) 

Siguin _a, b, d ∈_ Z amb _a, b, d >_ 0 . Aleshores: _\_ [ d = mcd( _a, b_ ) _⇐⇒_ (1) _d | a,_ (2) _d | b, \_ ]  (3) _∀c ∈_ Z _, c | a_ i _c | b_ = _⇒ c | d._ 

## 8.1 Explicació 

Aquest corol·lari ens dona la denició formal i rigorosa del màxim comú divisor. No només diu que _d_ és un divisor comú (condicions 1 i 2), sinó que a més és el més gran possible (condició 3). 

La clau és la condició (3): si qualsevol altre nombre _c_ també divideix tant _a_ com _b_ , aleshores forçosament _c_ ha de dividir _d_ . Això vol dir que _d_ és un múltiple de tots els divisors comuns de _a_ i _b_ , la qual cosa el converteix automàticament en el més gran de tots ells. 

Aquesta caracterització és molt útil perquè ens permet demostrar propietats del mcd sense necessitat de calcular-lo explícitament. També és la denició que s'utilitza en àlgebra abstracta per generalitzar el concepte de mcd a altres estructures algebraiques (com els anells d'ideals principals). 

## 8.2 Exemple concret 

Siguin _a_ = 12 i _b_ = 18 . Sabem que _d_ = mcd(12 _,_ 18) = 6 . Comprovem les condicions: 

1. 6 _|_ 12 (cert, 12 = 6 _·_ 2 ). 

2. 6 _|_ 18 (cert, 18 = 6 _·_ 3 ). 

20 

3. Si prenem qualsevol _c_ que divideixi 12 i 18 (per exemple, _c_ = 2 o _c_ = 3 ), comprovem que també divideix 6: 

 2 _|_ 12 i 2 _|_ 18 = _⇒_ 2 _|_ 6 (cert).  3 _|_ 12 i 3 _|_ 18 = _⇒_ 3 _|_ 6 (cert). 

Per tant, es compleix la denició i 6 = mcd(12 _,_ 18) . 

# 9 16. Denició: nombres coprimers 

## 9.1 Enunciat 

Siguin _a, b >_ 0 enters. Es diu que _a_ i _b_ són coprimers (o primers entre si) si 

mcd( _a, b_ ) = 1 _._ 

Equivalentment, _a_ i _b_ són coprimers si existeixen _α, β ∈_ Z tals que 

_αa_ + _βb_ = 1 _._ 

## 9.2 Explicació 

Que dos nombres siguin coprimers vol dir que no tenen cap divisor positiu comú més gran que 1. És a dir, l'únic divisor positiu que comparteixen és l'1. 

No cal que els dos nombres siguin primers. Per exemple, 8 i 15 no són primers, però 

mcd(8 _,_ 15) = 1 _,_ 

per tant són coprimers. En canvi, 6 i 10 no són coprimers perquè 

mcd(6 _,_ 10) = 2 _̸_ = 1 _._ 

## 9.3 Per què és equivalent a l'existència de _α, β_ ? 

Aquesta equivalència és una conseqüència directa de la Identitat de Bézout. 

21 

- 9.3.1 ( _⇒_ ) Si mcd( _a, b_ ) = 1 , aleshores existeixen _α, β ∈_ Z tals que _αa_ + _βb_ = 1 . 

Això és exactament la Identitat de Bézout aplicada a _a_ i _b_ , amb _d_ = mcd( _a, b_ ) = 1 . 

- 9.3.2 ( _⇐_ ) Si existeixen _α, β ∈_ Z tals que _αa_ + _βb_ = 1 , aleshores mcd( _a, b_ ) = 1 . 

Demostració: sigui _d_ = mcd( _a, b_ ) . Com que _d | a_ i _d | b_ , tenim 



Per tant, _d |_ 1 . Com que _d >_ 0 , necessàriament _d_ = 1 . Així, doncs, les dues condicions són equivalents: 

mcd( _a, b_ ) = 1 _⇐⇒∃α, β ∈_ Z _, αa_ + _βb_ = 1 _._ 

## 9.4 Exemples 

1. 8 i 15 són coprimers: 



A més, podem trobar coecients de Bézout: 



Per tant, _α_ = 2 i _β_ = _−_ 1 . 

2. 31 i 12 són coprimers: 



I hem vist que 



3. 14 i 25 són coprimers: 



Per exemple, 9 _·_ 14 + ( _−_ 5) _·_ 25 = 126 _−_ 125 = 1 _._ 

4. 6 i 10 no són coprimers, perquè 



22 

# 10 17. Corol·lari: després de dividir pel mcd, els quocients són coprimers 

## 10.1 Enunciat 

Siguin _a, b >_ 0 , i sigui 



Escrivim 



amb _a_<sup>_′_</sup> _, b_<sup>_′_</sup> _∈_ Z . Aleshores 



És a dir, _a_<sup>_′_</sup> i _b_<sup>_′_</sup> són coprimers. 

## 10.2 Explicació 

Aquest corol·lari diu que si traiem de _a_ i _b_ tot el que tenen en comú, és a dir, si els dividim pel seu màxim comú divisor, els nombres que queden ja no tenen res en comú llevat de l'1. 

Per exemple: 



Aleshores 



I efectivament, 

mcd(2 _,_ 3) = 1 _._ 

Un altre exemple: 



Aleshores 



I 

mcd(120 _,_ 23) = 1 _._ 

23 

## 10.3 Demostració 

Siguin 



Volem veure que mcd( _a_<sup>_′_</sup> _, b_<sup>_′_</sup> ) = 1 . Sigui 



Aleshores _c | a_<sup>_′_</sup> i _c | b_<sup>_′_</sup> . Per tant, 



i 



Així, _dc_ és un divisor comú de _a_ i _b_ . 

Com que _d_ = mcd( _a, b_ ) , qualsevol divisor comú de _a_ i _b_ ha de dividir _d_ . Per tant, 



Com que _d >_ 0 , això implica 



Com que _c >_ 0 , necessàriament 



Per tant, 

mcd( _a_<sup>_′_</sup> _, b_<sup>_′_</sup> ) = 1 _._ 

## 10.4 Importància 

Aquest corol·lari és la base per simplicar fraccions: 



La fracció<sup>_<u>a</u>_</sup> _b_<sup>_<u>′′</u>_ésirreductible,perquè</sup><sup>_a′_i</sup><sup>_b′_sóncoprimers.</sup> 

24 

# 11 18. Corol·lari: lema d'Euclides 

## 11.1 Enunciat 

Si _a | bc_ i _a_ i _b_ són coprimers, aleshores 

_a | c._ 

És a dir: 



## 11.2 Explicació 

Aquest resultat es coneix com el lema d'Euclides. Diu que si un nombre _a_ divideix un producte _bc_ , i _a_ no comparteix cap factor amb _b_ , aleshores forçosament _a_ ha de dividir l'altre factor _c_ . 

Intuïtivament: com que _a_ i _b_ no tenen factors comuns, tots els factors de _a_ han d'estar dins de _c_ perquè _a_ pugui dividir _bc_ . 

## 11.3 Demostració 

Com que mcd( _a, b_ ) = 1 , per la Identitat de Bézout existeixen _α, β ∈_ Z tals que 

_αa_ + _βb_ = 1 _._ 

Multiplicant aquesta igualtat per _c_ : 

_αac_ + _βbc_ = _c._ 

Ara observem que: 

 _a | αac_ , perquè _αac_ = _a_ ( _αc_ ) . 



Com que _a_ divideix els dos sumands, també divideix la seva suma: 



Per tant, 



25 

## 11.4 Exemple correcte 

Siguin 



Com que 



i 



aleshores el lema d'Euclides ens assegura que 



I, efectivament, 10 = 5 _·_ 2 . Un altre exemple: 



Com que mcd(4 _,_ 3) = 1 i 



llavors 



Cert, 8 = 4 _·_ 2 . 

## 11.5 Contraexemple si no són coprimers 

La condició mcd( _a, b_ ) = 1 és essencial. Si no es compleix, el resultat pot ser fals. 

Per exemple: 



Tenim 



però 



Aquí mcd(6 _,_ 4) = 2 _̸_ = 1 , i per tant no podem aplicar el lema. Un altre cas: 





però 

6 ∤ 9 _._ 

De nou, mcd(6 _,_ 8) = 2 _̸_ = 1 . 

## 11.6 Importància 

Aquest corol·lari és fonamental per demostrar la unicitat de la factorització en primers. També s'utilitza per resoldre congruències, per simplicar equacions diofàntiques i en criptograa. 

A més, es pot combinar amb el corol·lari 17: si _d_ = mcd( _a, b_ ) , _a_ = _da_<sup>_′_</sup> , _b_ = _db_<sup>_′_</sup> , aleshores _a_<sup>_′_</sup> i _b_<sup>_′_</sup> són coprimers. Si _a | bc_ , aleshores _da_<sup>_′_</sup> _| db_<sup>_′_</sup> _c_ , és a dir, _a_<sup>_′_</sup> _| b_<sup>_′_</sup> _c_ . Com que mcd( _a_<sup>_′_</sup> _, b_<sup>_′_</sup> ) = 1 , pel lema d'Euclides _a_<sup>_′_</sup> _| c_ , i per tant _a_ = _da_<sup>_′_</sup> _| dc_ , és a dir, _a | c_ si _d | dc_ (sempre cert). Això dona una altra manera de veure la coherència entre 17 i 18. 

## 11.7 Resum 

-  16. _a_ i _b_ són coprimers si mcd( _a, b_ ) = 1 . Equivalentment, si existeixen _α, β ∈_ Z amb _αa_ + _βb_ = 1 . 

-  17. Si _d_ = mcd( _a, b_ ) i _a_ = _da_<sup>_′_</sup> , _b_ = _db_<sup>_′_</sup> , aleshores _a_<sup>_′_</sup> i _b_<sup>_′_</sup> són coprimers. 

-  18. Si _a | bc_ i mcd( _a, b_ ) = 1 , aleshores _a | c_ . Aquest és el lema d'Euclides. 

12 Exercici: MCD de _a_ + _b_ i _a − b_ 

## 12.1 Enunciat 

Siguin _a, b ∈_ Z amb mcd( _a, b_ ) = 1 . Aleshores 



És a dir, el màxim comú divisor de _a_ + _b_ i _a − b_ només pot ser 1 o 2 . 

## 12.2 Solució 

Sigui 



27 

Aleshores 



Per la propietat de linealitat del mcd: 





Per tant, 



Com que mcd( _a, b_ ) = 1 , tenim 



Com que _d >_ 0 , necessàriament 



Per tant, 



## 12.3 Observació sobre la paritat 

Com que mcd( _a, b_ ) = 1 , _a_ i _b_ no poden ser tots dos parells. Aleshores: 

 Si _a_ i _b_ són tots dos senars, _a_ + _b_ i _a − b_ són parells, i per tant 



 Si un és parell i l'altre senar, _a_ + _b_ i _a − b_ són senars, i per tant 





28 

## 12.4 Exemples 





Aleshores 









Aleshores 





Equivalentment, 







Aleshores 





## 12.5 Nota 

La condició mcd( _a, b_ ) = 1 és essencial. Si _a_ i _b_ no són coprimers, el mcd de _a_ + _b_ i _a − b_ pot ser més gran que 2 . Per exemple, amb _a_ = 6 i _b_ = 10 : 



i 



Per tant, la hipòtesi mcd( _a, b_ ) = 1 no es pot eliminar. 

29 

## 12.6 Resum 

Si _a_ i _b_ són coprimers, aleshores 



Més concretament: 



# 13 Apunts: Exercicis de divisibilitat i mcd 

## 13.1 Recordatori: propietat fonamental del mcd (apartat 12) 

Per a qualsevol _x, y ∈_ Z i _k ∈_ Z , 

mcd( _x, y_ ) = mcd( _x_ + _ky, y_ ) = mcd( _x, y_ + _kx_ ) _._ 

Això és cert perquè qualsevol divisor comú de _x_ i _y_ també divideix _x_ + _ky_ , i viceversa: si divideix _x_ + _ky_ i _y_ , aleshores divideix ( _x_ + _ky_ ) _− ky_ = _x_ . 

Aquesta propietat és la que ens permet eliminar termes i simplicar el càlcul del mcd. 

## 13.2 Exercici 1.3: És cert que mcd(3 _a − b, b −_ 2 _a_ ) = mcd( _a, b_ ) ? 13.3 Enunciat 

Per a _a, b ∈_ Z , volem veure si 

mcd(3 _a − b, b −_ 2 _a_ ) = mcd( _a, b_ ) _._ 

## 13.4 Solució pas a pas 

Apliquem la propietat del mcd. Primer sumem el segon component al primer: 



Calculem el primer component: 



30 

Per tant, 

mcd(3 _a − b, b −_ 2 _a_ ) = mcd( _a, b −_ 2 _a_ ) _._ 

Ara sumem 2 _a_ al segon component: 



Així doncs, 



Sí que és cert. 

## 13.5 Explicació alternativa amb divisors comuns 

Si _d_ és un divisor comú de 3 _a − b_ i _b −_ 2 _a_ , aleshores 



Per tant _d | a_ . Com que també _d | b −_ 2 _a_ , tenim 



Així _d | b_ . Per tant, tot divisor comú de 3 _a − b_ i _b −_ 2 _a_ també és divisor comú de _a_ i _b_ . 

Recíprocament, si _d | a_ i _d | b_ , aleshores 



Per tant, els conjunts de divisors comuns coincideixen, i en particular el seu màxim comú divisor és el mateix. 



## 13.7 Enunciat 

Volem veure que 

mcd(4 _n_ + 5 _,_ 2 _n_ + 3) = 1 

per a tot _n ≥_ 1 . Si el mcd és 1 , la fracció no es pot simplicar, és a dir, és irreductible. 

31 

## 13.8 Solució pas a pas 

Apliquem la propietat del mcd per eliminar la _n_ del primer component. Prenem _k_ = 2 i restem 2 _·_ (2 _n_ + 3) al primer component: 



Calculem: 



Per tant, 

mcd(4 _n_ + 5 _,_ 2 _n_ + 3) = mcd( _−_ 1 _,_ 2 _n_ + 3) _._ 

Ara bé, els únics divisors de _−_ 1 són 1 i _−_ 1 . Per tant, el màxim comú divisor de _−_ 1 amb qualsevol enter és 1 : 



Així, 



Com que el numerador i el denominador són coprimers, la fracció 



és irreductible per a tot _n ≥_ 1 . 

## 13.9 Exemples 



## 13.10 Nota 

El mateix mètode serveix per a fraccions de la forma 



sempre que _ad − bc_ = _±_ 1 . En aquest cas, _a_ = 4 , _b_ = 5 , _c_ = 2 , _d_ = 3 , i 



però el que importa és que la combinació 4 _n_ + 5 _−_ 2(2 _n_ + 3) = _−_ 1 , que és una constant no nul·la. Això garanteix que el mcd és 1 . 

32 

# 14 19. Equacions diofàntiques (Diofant d'Alexandria) 

## 14.1 Enunciat 

Siguin _a, b, c ∈_ Z , amb _a_ i _b_ no tots dos zero. Considerem l'equació 

_ax_ + _by_ = _c_ 

- on les incògnites _x, y_ es busquen només dins dels enters Z . Sigui _d_ = mcd( _a, b_ ) _._ 

Aleshores: 

l'equació _ax_ + _by_ = _c_ té solució entera _⇐⇒ d | c._ 

## 14.2 Explicació 

Els enters són més "fàcils" que els racionals en el sentit que no tenen denominadors, però això mateix fa que resoldre equacions només amb enters sigui més complicat: no sempre podem dividir. 

Sobre Q l'equació _ax_ + _by_ = _c_ (amb _a, b_ no nuls) sempre té solució. Sobre Z , en canvi, la paritat i la divisibilitat ho poden impedir. 

La idea clau és que tot el costat esquerre _ax_ + _by_ és forçosament un múltiple de _d_ = mcd( _a, b_ ) . Per tant, si _c_ no és múltiple de _d_ , l'equació és impossible. I si sí que ho és, la Identitat de Bézout ens permet construir una solució explícitament. 

## 14.3 Demostració 

Sigui _d_ = mcd( _a, b_ ) . 

14.3.1 ( _⇒_ ) Si hi ha solució, aleshores _d | c_ . 

Suposem que existeixen _x, y ∈_ Z tals que _ax_ + _by_ = _c_ . 

Com que _d | a_ , tenim _d | ax_ per a qualsevol _x ∈_ Z (propietat 9.iii). De la mateixa manera, com que _d | b_ , tenim _d | by_ . 

Per linealitat (propietat 9.ii), _d_ divideix la suma: 

_d | ax_ + _by_ = _c._ 

Per tant, _d | c_ . Això demostra que si _d_ ∤ _c_ , l'equació no té solució. 

33 

14.3.2 ( _⇐_ ) Si _d | c_ , aleshores hi ha solució. 

Suposem ara que _d | c_ . Aleshores existeix _c_<sup>_′_</sup> _∈_ Z tal que 



Per la Identitat de Bézout (apartat 14), existeixen _α, β ∈_ Z (que sabem calcular amb l'Algorisme d'Euclides) tals que 



Multiplicant aquesta igualtat per _c_<sup>_′_</sup> : 



És a dir, 



Per tant, prenent 



obtenim una solució entera de _ax_ + _by_ = _c_ . 

Així, _d | c_ és condició necessària i sucient. 

## 14.4 Exemple 1: equació sense solució 

Volem resoldre en enters: 



Aquí _a_ = 2 , _b_ = 4 , _c_ = 7 , i 



Com que 



el teorema ens diu que no hi ha cap solució entera. 

Intuïtivament: 2 _x_ sempre és parell, 4 _y_ sempre és parell, i la suma de dos parells sempre és parella. Però 7 és senar, així que mai podrem obtenir 7 sumant dos nombres parells. 

34 

## 14.5 Exemple 2: equació amb solució 

Volem resoldre en enters: 



14.5.1 Pas 1: calcular _d_ i comprovar que divideix _c_ . _d_ = mcd(27 _,_ 13) = 1 _._ 

Com que 1 _|_ 1250 , el teorema garanteix que sí que hi ha solució. 

14.5.2 Pas 2: trobar coecients de Bézout. 

Busquem _α, β ∈_ Z tals que 



Amb l'Algorisme d'Euclides: 



Aïllant l'1: 



Per tant, _α_ = 1 i _β_ = _−_ 2 . 

14.5.3 Pas 3: multiplicar per _c_<sup>_′_</sup> . 

Escrivim _c_ = _dc_<sup>_′_</sup> : 



és a dir, _c_<sup>_′_</sup> = 1250 . 

Aleshores una solució particular és: 



14.5.4 Pas 4: comprovació. 



Per tant: 



35 

## 14.6 Resum 

-  L'equació _ax_ + _by_ = _c_ en enters només pot tenir solució si _d_ = mcd( _a, b_ ) divideix _c_ . 

-  Si _d_ ∤ _c_ , és impossible (exemple: 2 _x_ + 4 _y_ = 7 ). 

-  Si _d | c_ , n'hi ha: es troba _αa_ + _βb_ = _d_ per Bézout, s'escriu _c_ = _dc_<sup>_′_</sup> , i _x_ 0 = _αc_<sup>_′_</sup> , _y_ 0 = _βc_<sup>_′_</sup> és solució. 

## 14.7 És l'única solució? Hi ha més solucions? 

### 14.7.1 Enunciat 

La solució _x_ 0 = _αc_<sup>_′_</sup> , _y_ 0 = _βc_<sup>_′_</sup> que hem construït no és única. De fet, si l'equació té una solució, en té innites. 

Sigui _d_ = mcd( _a, b_ ) i escrivim 



amb _a_<sup>_′_</sup> _, b_<sup>_′_</sup> _∈_ Z . Sabem pel corol·lari 17 que mcd( _a_<sup>_′_</sup> _, b_<sup>_′_</sup> ) = 1 . 

Si ( _x_ 0 _, y_ 0) és una solució particular de _ax_ + _by_ = _c_ , aleshores per a tot _λ ∈_ Z , 



també és solució. 

En el nostre cas, amb _x_ 0 = _αc_<sup>_′_</sup> i _y_ 0 = _βc_<sup>_′_</sup> : 



### 14.7.2 Explicació 

Un cop tenim una solució, en podem fabricar innites sumant i restant el mateix valor de manera que es compensi. La idea és sumar a _x_ 0 un múltiple de _b_<sup>_′_</sup> i restar de _y_ 0 el corresponent múltiple de _a_<sup>_′_</sup> , de manera que l'augment _a ·_ ( _λb_<sup>_′_</sup> ) quedi exactament anul·lat per la disminució _b ·_ ( _−λa_<sup>_′_</sup> ) . 

Per què funciona amb _a_<sup>_′_</sup> i _b_<sup>_′_</sup> i no amb _a_ i _b_ ? Perquè _ab_<sup>_′_</sup> = _ba_<sup>_′_</sup> (tots dos valen _da_<sup>_′_</sup> _b_<sup>_′_</sup> ), així que els dos termes extra se cancel·len. Si féssim servir _a_ i _b_ directament, el pas seria més gran del necessari; dividint pel _d_ obtenim el pas mínim que genera totes les solucions. 

36 

### 14.7.3 Demostració que són solucions 

Suposem que 



és a dir, _a_ ( _αc_<sup>_′_</sup> ) + _b_ ( _βc_<sup>_′_</sup> ) = _c_ . Prenem un altre candidat: 



amb _λ ∈_ Z arbitrari. Aleshores: 



Desenvolupant: 



Ara observem que 



Per tant, 



i queda 

_ax_ + _by_ = _c._ 

Així, ( _x, y_ ) també és solució per a qualsevol _λ ∈_ Z . Com que _λ_ pot ser qualsevol enter, hi ha innites solucions. 

14.7.4 Exemple: 27 _x_ + 13 _y_ = 1250 

Ja tenim la solució particular _x_ 0 = 1250 , _y_ 0 = _−_ 2500 . Aquí _d_ = 1 , així que 



La solució general és: 



Per exemple, amb _λ_ = 1 : 



i es comprova que 27 _·_ 1263 + 13 _·_ ( _−_ 2527) = 1250 . 

37 

### 14.7.5 Nota: són totes 

De fet, aquestes són totes les solucions: si ( _x, y_ ) és qualsevol altra solució, restant _ax_ 0 + _by_ 0 = _c_ s'obté _a_ ( _x − x_ 0) + _b_ ( _y − y_ 0) = 0 , és a dir, _a_<sup>_′_</sup> ( _x − x_ 0) = _−b_<sup>_′_</sup> ( _y − y_ 0) . Com que mcd( _a_<sup>_′_</sup> _, b_<sup>_′_</sup> ) = 1 , el lema d'Euclides obliga _b_<sup>_′_</sup> _|_ ( _x − x_ 0) , d'on _x_ = _x_ 0 + _λb_<sup>_′_</sup> per a algun _λ_ , i aleshores _y_ = _y_ 0 _− λa_<sup>_′_</sup> . 

### 14.7.6 Demostració que aquestes són totes les solucions 

Volem veure que no hi ha cap solució fora de la forma _x_ 0 + _λb_<sup>_′_</sup> , _y_ 0 _− λa_<sup>_′_</sup> . És a dir, que les innites solucions que hem construït són totes. 

Suposem que 



és una altra solució qualsevol en enters. Aleshores: 



Però també sabem que la solució particular compleix: 



Restant les dues igualtats: 



és a dir: 



Escrivim _a_ = _da_<sup>_′_</sup> i _b_ = _db_<sup>_′_</sup> amb _d_ = mcd( _a, b_ ) , i "tatxem" la _d_ dividint els dos costats per _d_ : 



El costat esquerre és clarament un múltiple de _a_<sup>_′_</sup> . Per tant, el costat dret també ho ha de ser: 



Però sabem que mcd( _a_<sup>_′_</sup> _, b_<sup>_′_</sup> ) = 1 (corol·lari 17). Pel lema d'Euclides (corol·lari 18), si _a_<sup>_′_</sup> divideix el producte _b_<sup>_′_</sup> ( _βc_<sup>_′_</sup> _− f_ ) i és coprimer amb _b_<sup>_′_</sup> , aleshores forçosament 



38 

Això vol dir que existeix un enter _λ ∈_ Z tal que 



Aïllant _f_ : 



Substituint això a l'equació _a_<sup>_′_</sup> ( _e − αc_<sup>_′_</sup> ) = _b_<sup>_′_</sup> ( _βc_<sup>_′_</sup> _− f_ ) : 



Simplicant _a_<sup>_′_</sup> (si _a_<sup>_′̸_</sup> = 0 ; el cas _a_<sup>_′_</sup> = 0 és anàleg): 



és a dir: 



Per tant, qualsevol solució ( _e, f_ ) és necessàriament de la forma 



per a alguna _λ ∈_ Z . Això demostra que les solucions paramètriques són totes les solucions. 

1. Complement: l'altra divisibilitat i unicitat del paràmetre _λ_ 

De la igualtat _a_<sup>_′_</sup> ( _e − αc_<sup>_′_</sup> ) = _b_<sup>_′_</sup> ( _βc_<sup>_′_</sup> _− f_ ) també es pot raonar simètricament: el costat dret és múltiple de _b_<sup>_′_</sup> , així que 



Com que mcd( _a_<sup>_′_</sup> _, b_<sup>_′_</sup> ) = 1 , pel lema d'Euclides _b_<sup>_′_</sup> és coprimer amb _a_<sup>_′_</sup> i per tant 



Això vol dir que existeix _λ ∈_ Z tal que 



és a dir: 



39 

Finalment, els dos paràmetres coincideixen: si escrivim _e − αc_<sup>_′_</sup> = _b_<sup>_′_</sup> _λ_ i _βc_<sup>_′_</sup> _− f_ = _a_<sup>_′_</sup> _µ_ , substituint a _a_<sup>_′_</sup> ( _e − αc_<sup>_′_</sup> ) = _b_<sup>_′_</sup> ( _βc_<sup>_′_</sup> _− f_ ) s'obté 







Per tant, una sola _λ ∈_ Z parametritza totes les solucions: _e_ = _αc_<sup>_′_</sup> + _λb_<sup>_′_</sup> , _f_ = _βc_<sup>_′_</sup> _− λa_<sup>_′_</sup> . 

## 14.8 Exercici: endevinar la data de naixement 

### 14.8.1 Enunciat 

Considerem l'equació 



on _x_ és el mes de naixement ( 1 _≤ x ≤_ 12 ) i _y_ és el dia de naixement ( 1 _≤ y ≤_ 31 ). 

Si només ens donen el valor de _c_ , és possible descobrir quin dia va néixer aquella persona? És a dir, podem recuperar ( _x, y_ ) a partir de _c_ ? 

### 14.8.2 Explicació 

Sense les cotes 1 _≤ x ≤_ 12 i 1 _≤ y ≤_ 31 , l'equació 12 _x_ + 31 _y_ = _c_ té innites solucions enteres (de la forma _x_ = _αc_<sup>_′_</sup> + _λb_<sup>_′_</sup> , _y_ = _βc_<sup>_′_</sup> _− λa_<sup>_′_</sup> ). Per tant, _c_ sol no determina ( _x, y_ ) . 

Però amb les cotes de mes i dia, d'entre les innites solucions només una cau dins dels intervals permesos. Així, les cotes seleccionen la solució "real" i permeten endevinar la data. 

### 14.8.3 Resolució pas a pas amb _c_ = 256 

Volem resoldre en enters 



1. Pas 1: existeix solució? 



Com que 1 _|_ 256 , el teorema garanteix que sí que hi ha solució. 

40 

2. Pas 2: coecients de Bézout. 

Busquem _α, β_ tals que 12 _α_ + 31 _β_ = 1 . Per Euclides: 



Per tant, _α_ = 13 i _β_ = _−_ 5 . 

3. Pas 3: solució particular. 

Com que _c_ = 256 = 1 _·_ 256 , tenim _c_<sup>_′_</sup> = 256 . Multiplicant Bézout per _c_<sup>_′_</sup> : 12 _·_ (13 _·_ 256) + 31 _·_ ( _−_ 5 _·_ 256) = 256 _._ 

És a dir, _x_ 0 = 3328 , _y_ 0 = _−_ 1280 és una solució particular (molt fora de rang, però vàlida). 

4. Pas 4: solució general. 

Aquí _a_<sup>_′_</sup> = 12 , _b_<sup>_′_</sup> = 31 (perquè _d_ = 1 ). Per tant: 



5. Pas 5: imposar les cotes. 

Busquem _λ_ tal que 



Provant amb _λ_ = _−_ 107 : 



Així, _x_ = 11 (novembre) i _y_ = 4 compleixen les cotes. 

### 14.8.4 Comprovació 



Per tant, la data recuperada és el 4 de novembre. 

41 

# 15 24. Lema d'Euclides per a primers 

## 15.1 Enunciat 

Sigui _p_ primer. Si _p | ab_ , aleshores _p | a_ o _p | b_ . És a dir: 

_p_ primer i _p | ab_ = _⇒ p | a_ o _p | b._ 

## 15.2 Explicació 

Aquest és el cas particular del lema d'Euclides (apartat 18) quan _a_ = _p_ és primer. 

Si _p_ no divideix _a_ , aleshores necessàriament mcd( _p, a_ ) = 1 (perquè els únics divisors positius de _p_ són 1 i _p_ ). Aleshores, com que _p | ab_ i mcd( _p, a_ ) = 1 , pel lema d'Euclides _p | b_ . 

# 16 25. Teorema fonamental de l'aritmètica 16.1 Enunciat 

Qualsevol nombre enter que no sigui 0 , 1 ni _−_ 1 es pot descompondre en producte de potències de nombres primers, tots diferents, i aquesta descomposició és única si no tenim en compte l'ordre dels factors ni el signe. És a dir: 



on: 

-  _a ∈_ Z , _a̸_ = 0 _, ±_ 1 . 

-  _p_ 1 _, . . . , pn_ són nombres primers, tots diferents entre si. 

-  _r_ 1 _, . . . , rn_ són nombres naturals _≥_ 1 , és a dir, els exponents. 

-  "únics llevat d'ordre i signe" vol dir que si escrius la factorització en un altre ordre, o amb algun signe canviat, en realitat és la mateixa factorització. 

42 

## 16.2 Demostració resumida 

### 16.2.1 Existència 

Per inducció forta en _n >_ 1 : si _n_ és primer, fet; si _n_ = _ab_ amb 1 _< a, b < n_ , per H.I. _a_ i _b_ factoritzen en primers i ajuntant-les s'obté la de _n_ . 

### 16.2.2 Lema clau 

Si _p_ és primer, _p | uv_ i _p_ ∤ _u_ , llavors mcd( _p, u_ ) = 1 . Per Bézout 1 = _px_ + _uy_ , d'on _v_ = _pxv_ + _uyv_ és múltiple de _p_ . Per tant _p | v_ . 

### 16.2.3 Unicitat 

Si _p_ 1 _· · · pr_ = _q_ 1 _· · · qs_ , llavors _p_ 1 _| qj_ per algun _j_ , i com que són primers _p_ 1 = _qj_ . Cancel·lem i repetim: les dues llistes coincideixen llevat d'ordre. Agrupant repetits, _a_ = _p_<sup>_r_</sup> 1<sup>1</sup><sup>_· · · p_</sup> _n_<sup>_rn_amb</sup><sup>_ri≥_1únics.Si</sup><sup>_a<_0,factoritzem</sup> _−a >_ 0 i hi afegim el signe. 

## 16.3 Exemples 

1. 84 = 2<sup>2</sup> _·_ 3 _·_ 7 

Aquí els primers són 2 _,_ 3 _,_ 7 , tots diferents, i els exponents són 2 _,_ 1 _,_ 1 . 

2. 360 = 2<sup>3</sup> _·_ 3<sup>2</sup> _·_ 5 

3. Si el nombre és negatiu, normalment es treu el signe fora i es factoritza la part positiva: 



O, si es permeten primers negatius, es pot repartir el signe entre els primers, però l'essència és la mateixa: els primers "de veritat" que apareixen, presos en valor absolut, i els seus exponents, són únics. 

## 16.4 Observacions sobre la unicitat 

Un exemple de no-unicitat només aparent seria: 



Són la mateixa factorització, només canvia l'ordre. 

43 

També cal que els primers siguin tots diferents. No escriuríem: 



amb _p_ 1 = 2 , _p_ 2 = 2 , perquè no serien diferents. Ho agrupem com: 



## 16.5 Importància 

Aquest teorema és fonamental perquè diu que els nombres primers són com els "àtoms" dels enters: qualsevol enter no nul ni _±_ 1 es construeix multiplicant primers d'una manera única. Serveix per calcular el mcd, el mcm, simplicar fraccions, estudiar divisibilitat, congruències, etc. 

# 17 26. Hi ha innits nombres primers 

## 17.1 Enunciat 

Hi ha innits nombres primers. 

## 17.2 Demostració (Euclides) 

Suposem que només hi hagués un nombre nit de primers: 



Mirem el nombre 



Aleshores _p_ 1 ∤ _a_ , perquè _a −_ 1 és múltiple de _p_ 1 però _a_ no ho és. En general, cap _pi_ divideix _a_ , perquè donaria residu 1 . 

Per tant, o bé _a_ és primer, o bé té un factor primer nou diferent de tots els _pi_ . En tots dos casos hi ha un primer fora de la llista, contradicció. 

Així doncs, no hi pot haver un nombre nit de primers: n'hi ha innits. 

44 

# 18 28. Proposició: mcd i mcm mitjançant la factorització en primers 

## 18.1 Enunciat 

Siguin 0 _< a_ i 0 _< b_ . Escrivim les seves factoritzacions en primers fent servir la mateixa llista de primers: 



amb _ri, si ≥_ 0 . Aleshores: 



i 



## 18.2 Què són _ri_ i _si_ ? 

-  _p_ 1 _, . . . , pn_ són tots els primers que apareixen en _a_ , en _b_ , o en tots dos. 

-  _ri_ és l'exponent del primer _pi_ dins de _a_ . 

-  _si_ és l'exponent del primer _pi_ dins de _b_ . 

-  Si un primer no apareix en un dels dos nombres, li posem exponent 0 . 

- Per tant, _ri, si ≥_ 0 . 

## 18.3 Per què funciona? 

### 18.3.1 Màxim comú divisor 

Un divisor comú de _a_ i _b_ només pot tenir els primers que apareixen en tots dos. A més, per a cada primer _pi_ : 

-  a _a_ , l'exponent és _ri_ ; 

-  a _b_ , l'exponent és _si_ . 

Perquè un nombre divideixi tant _a_ com _b_ , el seu exponent en _pi_ no pot superar ni _ri_ ni _si_ . Per tant, com a màxim pot ser 

min( _ri, si_ ) _._ 

45 

Per obtenir el màxim comú divisor, agafem precisament aquest exponent màxim permès: 



### 18.3.2 Mínim comú múltiple 

Un múltiple comú de _a_ i _b_ ha de ser divisible per _a_ i per _b_ . Per tant, per a cada primer _pi_ , el seu exponent ha de ser com a mínim _ri_ i com a mínim _si_ . És a dir, com a mínim 



Per obtenir el mínim comú múltiple, agafem exactament aquest exponent mínim obligatori: 



## 18.4 Exemple complet 

Siguin 



i 



Primer posem la mateixa llista de primers: 2 _,_ 3 _,_ 5 _,_ 7 . Els exponents són: 





### 18.4.1 MCD 

Agafem els mínims: 



46 

### 18.4.2 MCM 

Agafem els màxims: 



## 18.5 Propietat important 

Sempre es compleix: 



En l'exemple: 



i 



Aquesta propietat surt del fet que, per a cada primer _pi_ , 



## 18.6 Observacions 

-  Cal escriure els dos nombres amb la mateixa llista de primers. Si un primer no hi és, l'exponent és 0 . 

-  Els exponents _ri, si_ poden ser zero. 

-  El mètode és molt útil quan les factoritzacions són conegudes o fàcils de calcular. 

-  Per a nombres grans, normalment és més pràctic fer servir l'algorisme d'Euclides per al mcd, i després la propietat mcm( _a, b_ ) = _a·b/_ mcd( _a, b_ ) . 

-  La idea es pot generalitzar a més de dos nombres: el mcd pren els mínims exponents i el mcm pren els màxims exponents. 

47 

# 19 29. Aritmètica modular 

## 19.1 Denició 

Suposem que _m >_ 0 . Es diu que 



si _a − b_ és múltiple de _m_ , és a dir, si existeix _k ∈_ Z tal que 



Això equival a dir que _a_ i _b_ donen el mateix residu quan els dividim per 

_m_ . 

## 19.2 Explicació: per què equival a tenir el mateix residu? 

Si dividim _a_ i _b_ per _m_ : 



amb 0 _≤ r, r_<sup>_′_</sup> _< m_ . Llavors: 



Perquè _a − b_ sigui múltiple de _m_ , cal que _r − r_<sup>_′_</sup> també sigui múltiple de _m_ . Però com que _r_ i _r_<sup>_′_</sup> estan entre 0 i _m −_ 1 , l'única possibilitat és que 



és a dir, _r_ = _r_<sup>_′_</sup> . Per tant, _a_ i _b_ tenen el mateix residu. 

## 19.3 Exemples amb _m_ = 5 

### 19.3.1 Exemple 1 

7 _≡_ 2 (mod 5) 

perquè 7 _−_ 2 = 5 , que és múltiple de 5 . I, efectivament, tant 7 com 2 donen residu 2 en dividir per 5 . 

48 

### 19.3.2 Exemple 2 

_−_ 3 _≡_ 2 (mod 5) 

perquè _−_ 3 _−_ 2 = _−_ 5 , múltiple de 5 . I _−_ 3 es pot escriure com _−_ 1 _·_ 5 + 2 , així que també té residu 2 . 

Podem imaginar-ho com calaixos: cada residu possible ( 0 _,_ 1 _, . . . , m −_ 1 ) és un calaix, i dos nombres són congruents si són al mateix calaix. 

# 20 30. La congruència mòdul _m_ és una relació d'equivalència 

## 20.1 Recordatori: què vol dir _a ≡ b_ (mod _m_ ) 

Donats _a, b, m ∈_ Z amb _m >_ 0 , diem que 

_a ≡ b_ (mod _m_ ) 

si _a − b_ és múltiple de _m_ , és a dir, si existeix _k ∈_ Z tal que 



Això equival a dir que _a_ i _b_ donen el mateix residu en dividir per _m_ (vegeu apartat 29). 

## 20.2 Què és una relació d'equivalència? 

Una relació _∼_ sobre un conjunt és una relació d'equivalència si compleix tres propietats: 

1. Reexiva, 

2. Simètrica, 

3. Transitiva. 

Volem veure que _≡_ (mod _m_ ) les compleix totes tres. 

## 20.3 Propietat reexiva 

20.3.1 Enunciat 

_a ≡ a_ (mod _m_ ) per a tot _a ∈_ Z _._ 

49 

### 20.3.2 Demostració 

Cal veure que _a − a_ és múltiple de _m_ : 



Com que 0 és múltiple de _m_ , tenim _a ≡ a_ (mod _m_ ) . 

En paraules: tot nombre és al mateix calaix que ell mateix. 

### 20.3.3 Exemple 



ja que 7 _−_ 7 = 0 . 

## 20.4 Propietat simètrica 

### 20.4.1 Enunciat 

Si _a ≡ b_ (mod _m_ ) , llavors _b ≡ a_ (mod _m_ ) . 

### 20.4.2 Demostració 

Suposem que _a ≡ b_ (mod _m_ ) . Això vol dir que _a − b_ és múltiple de _m_ . Llavors: 



El negatiu d'un múltiple de _m_ també és múltiple de _m_ . Per tant, _b − a_ és múltiple de _m_ , i així 



En paraules: si dos nombres són al mateix calaix, l'ordre no importa. 

### 20.4.3 Exemple 

Com que 7 _≡_ 2 (mod 5) (perquè 7 _−_ 2 = 5 ), també 2 _≡_ 7 (mod 5) (perquè 2 _−_ 7 = _−_ 5 ). 

## 20.5 Propietat transitiva 

### 20.5.1 Enunciat 

Si _a ≡ b_ (mod _m_ ) i _b ≡ c_ (mod _m_ ) , llavors _a ≡ c_ (mod _m_ ) . 

50 

### 20.5.2 Demostració 

Suposem que _a − b_ és múltiple de _m_ i que _b − c_ també ho és. Sumem les dues expressions: 



Com que _a − b_ i _b − c_ són tots dos múltiples de _m_ , la seva suma també és múltiple de _m_ . Per tant, _a − c_ és múltiple de _m_ , és a dir, 



En paraules: si _a_ comparteix calaix amb _b_ , i _b_ comparteix calaix amb _c_ , llavors _a_ i _c_ són al mateix calaix. 

### 20.5.3 Exemple 

7 _≡_ 2 (mod 5) i 2 _≡−_ 3 (mod 5) . Llavors 7 _≡−_ 3 (mod 5) , ja que 7 _−_ ( _−_ 3) = 10 , que és múltiple de 5 . 

## 20.6 Conseqüència: classes de residus 

Com que _≡_ (mod _m_ ) és una relació d'equivalència, parteix Z en classes d'equivalència disjuntes, una per a cada residu possible. 

Per a _m_ = 5 : 

 Residu 0 : _. . . , −_ 10 _, −_ 5 _,_ 0 _,_ 5 _,_ 10 _, . . ._ 

-  Residu 1 : _. . . , −_ 9 _, −_ 4 _,_ 1 _,_ 6 _,_ 11 _, . . ._ 

-  Residu 2 : _. . . , −_ 8 _, −_ 3 _,_ 2 _,_ 7 _,_ 12 _, . . ._ 

-  Residu 3 : _. . . , −_ 7 _, −_ 2 _,_ 3 _,_ 8 _,_ 13 _, . . ._ 

-  Residu 4 : _. . . , −_ 6 _, −_ 1 _,_ 4 _,_ 9 _,_ 14 _, . . ._ 

El conjunt d'aquestes classes s'escriu Z _/m_ Z (o Z _m_ ) i té exactament _m_ elements. 

51 

## 20.7 Resum 

-  _≡_ (mod _m_ ) és una relació d'equivalència perquè compleix: 

   1. Reexiva: _a ≡ a_ (mod _m_ ) . 

   2. Simètrica: _a ≡ b_ (mod _m_ ) _⇒ b ≡ a_ (mod _m_ ) . 

   3. Transitiva: _a ≡ b_ (mod _m_ ) i _b ≡ c_ (mod _m_ ) _⇒ a ≡ c_ (mod _m_ ) . 

-  Les tres propietats es demostren directament a partir de la denició: " _a ≡ b_ (mod _m_ ) si _a − b_ és múltiple de _m_ ". 

-  Això permet agrupar els enters en classes de residus, que són la base de l'aritmètica modular. 

# 21 31. Denició: classes d'equivalència mòdul _m_ 

## 21.1 Denició 

Donat un enter _a ∈_ Z , la classe d'equivalència de _a_ mòdul _m_ es deneix com: 



És a dir, [ _a_ ] _m_ és el conjunt de tots els enters _b_ que són congruents amb _a_ mòdul _m_ . 

## 21.2 Formes equivalents 

La mateixa classe es pot escriure com: 



Intuïció: [ _a_ ] _m_ és el "calaix" del residu de _a_ . Conté tots els enters que donen el mateix residu que _a_ quan els dividim per _m_ . 

## 21.3 Exemple amb _m_ = 5 



52 



## 21.4 Observació important 





Per tant, una mateixa classe es pot representar amb qualsevol dels seus elements. 

# 22 32. Observació: partició de Z en _m_ classes 

## 22.1 Enunciat 

Les _m_ classes 



són totes diferents i cobreixen tots els enters. Escrivim: 



El símbol _⊔_ indica unió disjunta: cada enter pertany exactament a una d'aquestes classes. 

Això vol dir que tenim una partició de Z en _m_ classes. 

## 22.2 Demostració 

### 22.2.1 1. Existència 

Per a qualsevol _a ∈_ Z , dividim _a_ per _m_ : 



Llavors _a ≡ r_ (mod _m_ ) , així que _a ∈_ [ _r_ ] _m_ . Per tant, tot enter pertany com a mínim a una classe. 

53 

### 22.2.2 2. Unicitat 

Si _a ∈_ [ _r_ ] _m_ i _a ∈_ [ _s_ ] _m_ amb 0 _≤ r, s < m_ , llavors 

_r ≡ s_ (mod _m_ ) _,_ 

és a dir, _m_ divideix _r − s_ . Com que _|r − s| < m_ , l'única possibilitat és _r_ = _s_ . Per tant, cada enter pertany exactament a una classe. 

### 22.2.3 3. Disjunció 

Si [ _r_ ] _m ∩_ [ _s_ ] _m̸_ = ∅ , aleshores existeix algun _b_ que és congruent amb _r_ i amb _s_ . Per tant, _r ≡ s_ (mod _m_ ) , i com que 0 _≤ r, s < m_ , tenim _r_ = _s_ . Així, classes diferents no es tallen. 

## 22.3 El conjunt quocient Z _/m_ Z 

El conjunt de totes les classes d'equivalència mòdul _m_ s'escriu: 



Aquest conjunt té exactament _m_ elements. 

### 22.3.1 Exemple amb _m_ = 5 



Cada classe és un conjunt innit, però el conjunt de classes Z _/_ 5Z només té 5 elements. 

## 22.4 Nota 

-  Si _m_ = 1 , hi ha una sola classe: [0]1 = Z . 

-  Normalment prenem _m >_ 0 . Si _m_ fos negatiu, es treballa amb _|m|_ . 

-  La notació Z _/m_ Z també s'escriu de vegades com Z _m_ . 

Aquestes classes de residus són la base de l'aritmètica modular: més endavant es poden denir operacions com 





Però això ja seria el següent tema. 

54 

# 23 33. Observació: compatibilitat de la congruència amb la suma i el producte 

## 23.1 Enunciat 

Siguin _a, a_ 0 _, b, b_ 0 _∈_ Z i _m >_ 0 . Aleshores: 

23.1.1 (i) Compatibilitat amb la suma 

Si _a ≡ a_ 0 (mod _m_ ) i _b ≡ b_ 0 (mod _m_ ) , llavors 



### 23.1.2 (ii) Compatibilitat amb el producte 

Si _a ≡ a_ 0 (mod _m_ ) i _b ≡ b_ 0 (mod _m_ ) , llavors 



És a dir, la congruència és compatible amb la suma i amb el producte: podem substituir un nombre per qualsevol altre congruent sense alterar la congruència del resultat. 

## 23.2 Demostració de (i) 

Suposem que _a ≡ a_ 0 (mod _m_ ) i _b ≡ b_ 0 (mod _m_ ) . Això vol dir que 





Volem veure que ( _a_ + _b_ ) _−_ ( _a_ 0 + _b_ 0) és múltiple de _m_ . Però: 



Com que és suma de dos múltiples de _m_ , també és múltiple de _m_ . Per tant, 



55 

## 23.3 Demostració de (ii) 

Suposem igualment que _a ≡ a_ 0 (mod _m_ ) i _b ≡ b_ 0 (mod _m_ ) . Volem veure que 

_a · b − a_ 0 _· b_ 0 

és múltiple de _m_ . Fem una manipulació útil: 

- _a · b − a_ 0 _· b_ 0 = _a · b − a_ 0 _· b_ + _a_ 0 _· b − a_ 0 _· b_ 0 = ( _a − a_ 0) _· b_ + _a_ 0 _·_ ( _b − b_ 0) _._ Ara bé: 

-  ( _a − a_ 0) és múltiple de _m_ , així que ( _a − a_ 0) _· b_ també és múltiple de _m_ . 

 ( _b − b_ 0) és múltiple de _m_ , així que _a_ 0 _·_ ( _b − b_ 0) també és múltiple de _m_ . Per tant, la suma dels dos termes és múltiple de _m_ . Així, 

_a · b ≡ a_ 0 _· b_ 0 (mod _m_ ) _._ 

## 23.4 Observació addicional: compatibilitat amb la resta 

També es compleix: 

_a ≡ a_ 0 (mod _m_ ) _, b ≡ b_ 0 (mod _m_ ) _⇒ a − b ≡ a_ 0 _− b_ 0 (mod _m_ ) _._ 

Això surt de (i) aplicat a _b_ i _−b_ , o directament fent la diferència. 

## 23.5 Exemple amb _m_ = 5 

Tenim 7 _≡_ 2 (mod 5) i 8 _≡_ 3 (mod 5) . Llavors: 

-  Suma: 7 + 8 = 15 _≡_ 0 (mod 5) i 2 + 3 = 5 _≡_ 0 (mod 5) . 

-  Producte: 7 _·_ 8 = 56 _≡_ 1 (mod 5) i 2 _·_ 3 = 6 _≡_ 1 (mod 5) . 

Els resultats són congruents, com diu l'observació. 

# 24 34. Teorema: Z _/m_ Z és un anell commutatiu 

## 24.1 Idea 

A la secció anterior hem vist que la congruència respecta la suma i el producte. Això permet denir operacions sobre el conjunt de classes Z _/m_ Z . 

56 

## 24.2 Denició de les operacions 

A Z _/m_ Z denim: 



És a dir, sumem o multipliquem les classes sumant o multiplicant qualsevol representant i prenent després la classe del resultat. 

## 24.3 Primer: les operacions estan ben denides 

Que una operació estigui ben denida vol dir que el resultat no depèn dels representants triats. És a dir, si canviem _a_ per un altre _a_ 0 amb [ _a_ ] _m_ = [ _a_ 0] _m_ , i _b_ per un altre _b_ 0 amb [ _b_ ] _m_ = [ _b_ 0] _m_ , el resultat ha de ser el mateix. 

Suposem, doncs, que 



Això equival a dir: 



Per l'observació 33: 



Per tant: 



Així, les operacions no depenen dels representants. Estan ben denides. 

## 24.4 Segon: Z _/m_ Z amb aquestes operacions és un anell commutatiu 

Un anell commutatiu és un conjunt amb dues operacions, suma i producte, que compleixen les propietats habituals: associativitat, commutativitat, element neutre, element oposat per a la suma, i distributivitat del producte respecte de la suma. 

Comprovem-les per a Z _/m_ Z . 

57 

### 24.4.1 Suma 

1. Associativa: 

([ _a_ ] + [ _b_ ]) + [ _c_ ] = [ _a_ + _b_ ] + [ _c_ ] = [( _a_ + _b_ ) + _c_ ] = [ _a_ + ( _b_ + _c_ )] = [ _a_ ] + ([ _b_ ] + [ _c_ ]) _._ 

1. Commutativa: 



1. Element neutre: [0] _m_ . 



1. Element oposat: [ _−a_ ] _m_ . 



### 24.4.2 Producte 

1. Associatiu: 

([ _a_ ] _·_ [ _b_ ]) _·_ [ _c_ ] = [ _a · b_ ] _·_ [ _c_ ] = [( _a · b_ ) _· c_ ] = [ _a ·_ ( _b · c_ )] = [ _a_ ] _·_ ([ _b_ ] _·_ [ _c_ ]) _._ 

1. Commutatiu: 



1. Element neutre: [1] _m_ . 



### 24.4.3 Distributivitat 

El producte és distributiu respecte de la suma: 

[ _a_ ] _·_ ([ _b_ ]+[ _c_ ]) = [ _a_ ] _·_ [ _b_ + _c_ ] = [ _a·_ ( _b_ + _c_ )] = [ _a·b_ + _a·c_ ] = [ _a·b_ ]+[ _a·c_ ] = [ _a_ ] _·_ [ _b_ ]+[ _a_ ] _·_ [ _c_ ] _._ 

Igualment per l'altre costat, però com que el producte és commutatiu, ja queda cobert. 

58 

## 24.5 Conclusió 

Amb les operacions 



el conjunt Z _/m_ Z té estructura d'anell commutatiu amb unitat. L'element neutre de la suma és [0] _m_ i l'element neutre del producte és [1] _m_ . 

## 24.6 Exemple amb Z _/_ 5Z 

A Z _/_ 5Z : 



Comprovem la distributivitat: 



Coincideix. 

## 24.7 Nota nal 

Si _m_ és primer, aleshores Z _/m_ Z no només és un anell commutatiu, sinó que a més tot element no nul té invers multiplicatiu, i per tant és un cos. Per exemple, Z _/_ 5Z és un cos. En canvi, Z _/_ 6Z no és un cos, perquè, per exemple, [2] no té invers: no existeix cap [ _x_ ] tal que [2] _·_ [ _x_ ] = [1] . 

Però això ja correspondria a un tema posterior. 

# 25 35. Proposició: invertibles, cossos i divisors de zero 

Suposem _m >_ 1 i treballem a l'anell Z _/m_ Z . 

59 

## 25.1 Recordatori 

 [ _a_ ] _m_ és invertible (o una unitat) si existeix [ _x_ ] _m_ tal que 



 Dos enters _a_ i _m_ són coprimers (o primers entre si) si mcd( _a, m_ ) = 1 . 

25.2 (i) [ _a_ ] _m_ és invertible _⇐⇒ a_ i _m_ són coprimers 

### 25.2.1 Demostració 



_⇐⇒ a · x ≡_ 1 (mod _m_ ) 



_⇐⇒_ existeix un enter _y_ tal que _a · x −_ 1 = _y · m_ 

_⇐⇒_ existeix una combinació entera _a · x_ + _m ·_ ( _−y_ ) = 1 



L'últim pas és el teorema de Bézout: una combinació lineal entera de _a_ i _m_ val 1 si i només si mcd( _a, m_ ) = 1 . 

Per tant, [ _a_ ] _m_ té invers si i només si _a_ i _m_ són coprimers. 

### 25.2.2 Exemple amb _m_ = 5 

-  [2]5 és invertible perquè mcd(2 _,_ 5) = 1 . El seu invers és [3]5 , ja que 2 _·_ 3 = 6 _≡_ 1 (mod 5) . 

-  [4]5 és invertible perquè mcd(4 _,_ 5) = 1 . El seu invers és [4]5 , ja que 4 _·_ 4 = 16 _≡_ 1 (mod 5) . 

### 25.2.3 Exemple amb _m_ = 6 

-  [2]6 no és invertible perquè mcd(2 _,_ 6) = 2 _̸_ = 1 . 

-  [3]6 no és invertible perquè mcd(3 _,_ 6) = 3 _̸_ = 1 . 

-  [5]6 sí que és invertible perquè mcd(5 _,_ 6) = 1 . El seu invers és [5]6 , ja que 5 _·_ 5 = 25 _≡_ 1 (mod 6) . 

60 

## 25.3 (ii) Z _/m_ Z és un cos _⇐⇒ m_ és primer 

### 25.3.1 Demostració 

1. ( _⇒_ ) Si Z _/m_ Z és un cos, tot element no nul és invertible. Si _m_ no fos primer, podríem escriure _m_ = _d · n_ amb 1 _< d < m_ . Llavors [ _d_ ] _m̸_ = [0] _m_ , però mcd( _d, m_ ) = _d >_ 1 , així que per (i) [ _d_ ] _m_ no seria invertible. Contradicció. Per tant, _m_ ha de ser primer. 

2. ( _⇐_ ) Si _m_ és primer, prenem qualsevol [ _a_ ] _m̸_ = [0] _m_ . Això vol dir que _m_ no divideix _a_ . Com que _m_ és primer, mcd( _a, m_ ) = 1 . Per (i), [ _a_ ] _m_ és invertible. Per tant, tot element no nul té invers, i Z _/m_ Z és un cos. 

### 25.3.2 Exemples 

-  Z _/_ 5Z és un cos, perquè 5 és primer. 

-  Z _/_ 7Z és un cos, perquè 7 és primer. 

-  Z _/_ 6Z no és un cos, perquè 6 no és primer. Per exemple, [2]6 no té invers. 

## 25.4 (iii) Si [ _a_ ] _m_ no és invertible, aleshores és un divisor de zero 

### 25.4.1 Enunciat 

Si [ _a_ ] _m_ no és invertible, aleshores existeix [ _b_ ] _m̸_ = [0] _m_ tal que [ _a_ ] _m ·_ [ _b_ ] _m_ = [0] _m_ . 

És a dir, en Z _/m_ Z , tot element no invertible és un divisor de zero. 

### 25.4.2 Demostració 

Si [ _a_ ] _m_ no és invertible, per (i) tenim mcd( _a, m_ ) = _d >_ 1 . Escrivim: 

_a_ = _d · a_<sup>_′_</sup> _, m_ = _d · n_ 

amb _n_ = _m/d_ . Com que _d >_ 1 , tenim 0 _< n < m_ (excepte si _d_ = _m_ ; llavors _n_ = 1 , que també és diferent de 0 ). Aleshores: 

[ _a_ ] _m ·_ [ _n_ ] _m_ = [ _a · n_ ] _m_ = [ _d · a_<sup>_′_</sup> _· n_ ] _m_ = [ _a_<sup>_′_</sup> _· d · n_ ] _m_ = [ _a_<sup>_′_</sup> _· m_ ] _m_ = [0] _m._ 

61 

- I [ _n_ ] _m̸_ = [0] _m_ , perquè 0 _< n < m_ . Per tant, existeix [ _b_ ] _m_ = [ _n_ ] _m̸_ = [0] _m_ amb [ _a_ ] _m ·_ [ _b_ ] _m_ = [0] _m_ . 

- 25.4.3 Exemple amb _m_ = 6 

 [2]6 no és invertible. Prenem _n_ = 6 _/_ 2 = 3 . Llavors: 



I [3]6 _̸_ = [0]6 . 

 [3]6 no és invertible. Prenem _n_ = 6 _/_ 3 = 2 . Llavors: 



I [2]6 _̸_ = [0]6 . 

 [4]6 no és invertible. mcd(4 _,_ 6) = 2 , _n_ = 6 _/_ 2 = 3 . Llavors: 



I [3]6 _̸_ = [0]6 . 

### 25.4.4 Conseqüència 

A Z _/m_ Z , els elements invertibles són exactament les classes [ _a_ ] _m_ amb mcd( _a, m_ ) = 1 . Els elements no invertibles i no nuls són divisors de zero. 

# 26 36. Observació: llei de cancel·lació 

A l'anell Z _/m_ Z : 

-  (i) Si [ _a_ ] _m_ és invertible, aleshores 



 (ii) Si [ _a_ ] _m_ no és invertible, això no és cert en general. 

62 

## 26.1 (i) Demostració de la cancel·lació per elements invertibles 

Suposem que [ _a_ ] _m_ és invertible. Això vol dir que existeix [ _a_ ]<sup>_−_</sup> _m_<sup>1talque</sup> 



Suposem que 



Multipliquem els dos costats per l'invers [ _a_ ]<sup>_−_</sup> _m_<sup>1:</sup> 



Per associativitat: 







Per tant: 



Així, els elements invertibles es poden cancel·lar. 

### 26.1.1 Exemple amb _m_ = 5 

Com que [2]5 és invertible, si 



llavors necessàriament [ _b_ ]5 = [ _c_ ]5 . 

26.2 (ii) Si [ _a_ ] _m_ no és invertible, la cancel·lació pot fallar 

### 26.2.1 Exemple amb _m_ = 6 

Prenem [ _a_ ]6 = [2]6 , que no és invertible perquè mcd(2 _,_ 6) = 2 . 

Tenim: 





Per tant: 

però 



Així, no podem cancel·lar [2]6 . Un altre exemple: 

Llavors 

però 



## 26.3 Conclusió 

-  Si [ _a_ ] _m_ és invertible, podem cancel·lar-lo. 

-  Si [ _a_ ] _m_ no és invertible, no podem cancel·lar-lo en general, perquè pot passar que [ _a_ ] _·_ [ _b_ ] = [ _a_ ] _·_ [ _c_ ] amb [ _b_ ] _̸_ = [ _c_ ] . 

## 26.4 Resum nal 

A Z _/m_ Z , amb _m >_ 1 : 

-  [ _a_ ] _m_ és invertible _⇐⇒_ mcd( _a, m_ ) = 1 . 

-  Z _/m_ Z és un cos _⇐⇒ m_ és primer. 

-  Si [ _a_ ] _m_ no és invertible, aleshores és un divisor de zero: existeix [ _b_ ] _m̸_ = [0] _m_ amb [ _a_ ] _m ·_ [ _b_ ] _m_ = [0] _m_ . 

-  Si [ _a_ ] _m_ és invertible, es pot cancel·lar en igualtats: [ _a_ ] _·_ [ _b_ ] = [ _a_ ] _·_ [ _c_ ] _⇒_ [ _b_ ] = [ _c_ ] . 

-  Si [ _a_ ] _m_ no és invertible, la cancel·lació falla en general. 

64 

# 27 Introducció 

Estudiem matrius amb entrades a l'anell Z _/m_ Z . La idea central és que el determinant es deneix exactament igual que sobre Z , i moltes propietats es conserven. Quan _m_ és primer, Z _/m_ Z és un cos i tota l'àlgebra lineal estàndard funciona. Quan _m_ no és primer, apareixen divisors de zero i tot es complica. 

# 28 Anell Z _/m_ Z 

## 28.1 Denicions bàsiques 

Z _/m_ Z és el conjunt de classes de congruència mòdul _m_ : 



La suma i el producte es fan mòdul _m_ . 

-  Un element _a ∈_ Z _/m_ Z és una unitat si té invers multiplicatiu, és a dir, si existeix _b_ tal que 

_ab ≡_ 1 (mod _m_ ) _._ 

Això passa si i només si gcd( _a, m_ ) = 1 . 

-  Un element _a̸_ = 0 és un divisor de zero si existeix _b̸_ = 0 tal que 



Exemple: a Z _/_ 6Z , 2 _·_ 3 = 6 _≡_ 0 , però 2 _̸_ = 0 i 3 _̸_ = 0 . 

-  Z _/m_ Z és un cos si i només si _m_ és primer. En aquest cas l'escriurem F _p_ = Z _/p_ Z . 

## 28.2 Matrius _Mn_ (Z _/m_ Z) 

_Mn_ (Z _/m_ Z) és el conjunt de matrius _n × n_ amb entrades a Z _/m_ Z . La suma i el producte es deneixen igual que sobre Z , reduint el resultat mòdul _m_ . 

Una matriu _A ∈ Mn_ (Z _/m_ Z) és invertible si existeix _B ∈ Mn_ (Z _/m_ Z) tal que 



En aquest cas escrivim _A_<sup>_−_1</sup> = _B_ . El conjunt de matrius invertibles forma el grup lineal _GLn_ (Z _/m_ Z) . 

65 

# 29 Determinants mòdul _m_ 

## 29.1 Denició 

El determinant es deneix amb la mateixa fórmula que a Z : 



Com que el determinant és un polinomi amb coecients enters, reduir mòdul _m_ commuta amb el càlcul del determinant. 

## 29.2 Propietats que es conserven 





-  Multilinealitat i alternança per les i columnes. 

 Desenvolupament per menors i matriu adjunta. 



## 29.3 Exemple 1: determinant mòdul 6** 



det( _A_ ) = 1 _·_ 4 _−_ 2 _·_ 3 = 4 _−_ 6 = _−_ 2 _≡_ 4 (mod 6) _._ 

Com gcd(4 _,_ 6) = 2 , l'element 4 no és una unitat mòdul 6 . Per tant, _A_ no és invertible. 

## 29.4 Exemple 2: determinant mòdul 5** 



det( _A_ ) = 4 _−_ 6 = _−_ 2 _≡_ 3 (mod 5) _._ 

Com gcd(3 _,_ 5) = 1 , 3 és una unitat mòdul 5 . Per tant, _A_ és invertible. 

66 

# 30 Invertibilitat de matrius mòdul _m_ 

## 30.1 Proposició 

Sigui _A ∈ Mn_ (Z _/m_ Z) . Aleshores 

_A_ invertible _⇐⇒_ det( _A_ ) _∈_ (Z _/m_ Z)<sup>_∗_</sup> _._ 

Equivalentment, si representem det( _A_ ) per un enter, 

_A_ invertible _⇐⇒_ gcd(det( _A_ ) _, m_ ) = 1 _._ 

## 30.2 Demostració 

 ( _⇒_ ) Si _A_ és invertible, existeix _B_ amb _AB_ = _In_ . Prenent determinants: 



Per tant, det( _A_ ) té invers det( _B_ ) a Z _/m_ Z . Així det( _A_ ) és una unitat. 

-  ( _⇐_ ) Sigui _d_ = det( _A_ ) una unitat mòdul _m_ . Sigui _d_<sup>_−_1</sup> el seu invers. Denim 



Usant la propietat de la matriu adjunta: 



tenim 



## 30.3 Fórmula clàssica de la inversa 

Si det( _A_ ) és una unitat mòdul _m_ , 



Aquesta és la mateixa fórmula que sobre Q o R , però la divisió per det _A_ es fa multiplicant pel seu invers mòdul _m_ . 

67 

- 30.4 Exemple 3: inversa mòdul 5** 



Invers de 3 mòdul 5 : 3<sup>_−_1</sup> = 2 , perquè 3 _·_ 2 = 6 _≡_ 1 . 



30.5 Exemple 4: inversa mòdul 6 amb determinant unitat** 



det( _A_ ) = 1 _·_ 5 _−_ 2 _·_ 3 = 5 _−_ 6 = _−_ 1 _≡_ 5 (mod 6) _._ 

5 és unitat mòdul 6 , ja que 5 _·_ 5 = 25 _≡_ 1 . Així 5<sup>_−_1</sup> = 5 . 



Per tant, _A_ és la seva pròpia inversa mòdul 6 : 

_A_<sup>2</sup> _≡ I_ 2 (mod 6) _._ 

Comprovació: 



30.6 Exemple 5: determinant no unitat i matriu no invertible** 



gcd(3 _,_ 6) = 3 _̸_ = 1 , per tant 3 no és unitat. Així _A_ no és invertible. 

68 

# 31 Àlgebra lineal sobre Z _/p_ Z amb _p_ primer 

## 31.1 El cos F _p_ 

Si _p_ és primer, tot element no nul de Z _/p_ Z té invers multiplicatiu. Per tant, Z _/p_ Z és un cos, que denotem F _p_ . 

Això fa que tota l'àlgebra lineal estàndard funcioni exactament igual que sobre R o Q . 

## 31.2 Què funciona exactament igual? 

-  Vectors, combinacions lineals i subespais. 

-  Independència lineal, bases i dimensió. 

-  Sistemes d'equacions lineals: mètode de Gauss i eliminació. 

-  Rang d'una matriu. 

-  Determinants i invertibilitat. 

-  Regla de Cramer. 

-  Espais vectorials F<sup>_n_</sup> _p_ 

   - _p_<sup>.</sup> 

-  Teorema de RouchéCapelli: un sistema és compatible si i només si rang( _A_ ) = rang( _A|b_ ) . Si és compatible i el rang és igual al nombre d'incògnites, la solució és única. Si el rang és més petit, hi ha _p_<sup>_n−r_</sup> solucions. 

-  Una matriu és invertible si i només si det( _A_ ) _̸_ = 0 , si i només si les seves les/columnes són linealment independents, si i només si té rang _n_ . 

## 31.3 Exemple 6: sistema sobre F5 per la inversa** 





det( _A_ ) = 3 _̸_ = 0 a F5 , així que hi ha solució única. 







31.4 Exemple 7: regla de Cramer sobre F5 

Pel mateix sistema: 



31.5 Exemple 8: dependència lineal sobre F5 

Al cos F5 , els vectors 



són linealment independents? Mirem _av_ 1 + _bv_ 2 = 0 . _\_ [ a(1,2)+b(3,4)=(0,0) _a_ + 3 _b_ = 0 _⇐⇒ \_ ] El determinant de la matriu de coecients és 2 _a_ + 4 _b_ = 0 � 



Per tant, l'única solució és _a_ = _b_ = 0 . Són linealment independents. 

# 32 Quan _m_ no és primer: complicacions 

## 32.1 No és un cos 

Si _m_ no és primer, Z _/m_ Z no és un cos. Hi ha divisors de zero. Exemple _m_ = 6 : 

2 _·_ 3 = 6 _≡_ 0 (mod 6) _,_ 

però 2 _̸_ = 0 i 3 _̸_ = 0 . Ni 2 ni 3 són unitats. 

70 

## 32.2 Conseqüències 

-  No podem dividir per qualsevol element no nul. Només podem dividir per unitats. 

-  Una matriu pot tenir determinant no nul i, tot i així, no ser invertible. Exemple: 



det _A_ = 4 _̸_ = 0 , però 4 no és unitat mòdul 6 , així que _A_ no és invertible. 

-  El rang d'una matriu sobre un anell no és tan senzill com sobre un cos. 

-  La independència lineal canvia: un vector no nul pot ser linealment dependent. Exemple a Z _/_ 6Z : _v_ = (2 _,_ 0) . Tenim 



amb 3 _̸_ = 0 . Així _v_ és linealment dependent, tot i que _v̸_ = 0 . 

-  Els sistemes d'equacions poden tenir comportaments estranys: poden no tenir solució, tenir-ne una, o tenir-ne diverses. La regla de Cramer només s'aplica si el determinant és una unitat. 

-  La noció de base i dimensió sobre anells no és tan neta; cal parlar de mòduls lliures, torsió, etc. 

32.3 Exemple 9: sistema sobre Z _/_ 6Z sense solució** 





Com 4 no és unitat, no podem usar _A_<sup>_−_1</sup> . De fet, _A_ no és invertible. De la primera equació: 



Substituïm a la segona: 













Però 2 _y_ mòdul 6 només pot valer 0 _,_ 2 _,_ 4 . Mai 1 . Per tant, el sistema no té solució. 

- 32.4 Exemple 10: sistema sobre Z _/_ 6Z amb diverses solucions** 





Substituïm a la segona: 



Ara, 



Per tant, _y ≡_ 0 _,_ 3 (mod 6) . 

-  Si _y_ = 0 , aleshores _x_ = 0 . 



Solucions: (0 _,_ 0) i (0 _,_ 3) . El sistema és compatible indeterminat, però amb un nombre nit de solucions. 

# 33 Resum 

-  El determinant mòdul _m_ es calcula igual que a Z i compleix 



-  _A ∈ Mn_ (Z _/m_ Z) és invertible si i només si det( _A_ ) és una unitat mòdul _m_ , és a dir, gcd(det( _A_ ) _, m_ ) = 1 . 

-  Si det( _A_ ) és unitat, 



72 

-  Si _m_ = _p_ és primer, Z _/p_ Z és cos i tota l'àlgebra lineal estàndard funciona: vectors, independència lineal, sistemes, Cramer, rang, determinants, etc. 

-  Si _m_ no és primer, hi ha divisors de zero i l'àlgebra lineal és més complicada: cal anar amb compte amb divisions, rangs, independència i sistemes. 

# 34 Exercicis proposats 



2. Troba la inversa, si existeix, de 





4. Sobre Z _/_ 8Z , troba una matriu _A_ amb det _A_ = 4 i comprova que no és invertible. 

5. Sobre Z _/_ 6Z , dóna un exemple de vector no nul linealment dependent. 

# 35 Solucions breus 

35.1 1a 



35.2 1b 

det _B_ = 6 _−_ 5 = 1 (mod 8) _._ 

gcd(1 _,_ 8) = 1 , per tant és invertible. 

73 

## 35.3 1c 

det _C_ = 1(1 _·_ 0 _−_ 4 _·_ 6) _−_ 2(0 _·_ 0 _−_ 4 _·_ 5) + 3(0 _·_ 6 _−_ 1 _·_ 5) = 1(0 _−_ 24) _−_ 2(0 _−_ 20) + 3(0 _−_ 5) = _−_ 24 + 40 _−_ 15 = 1 (mod 5) _._ 

1 és unitat, per tant és invertible. 

35.4 2 det _A_ = 1 , així _A_<sup>_−_1</sup> = adj( _A_ ) . 



35.5 3 



= = _≡ \_ [ =A<sup>-1�</sup> 3 _\_ � �3 _·_ 3+6 _·_ 1 _\·_ 3+2 _·_ 1 � �15 _\_ � �1 _\_ � (mod 7) _.\_ ] Com� _xy_ � provació: 2 _·_ 1 + 1 = 3 _,_ 5 _·_ 1 + 3 _·_ 1 = 8 _≡_ 1 (mod 7) _._ 

35.6 4 



Com gcd(4 _,_ 8) = 4 _̸_ = 1 , 4 no és unitat mòdul 8 . Per tant, _A_ no és invertible. 

35.7 5 

A (Z _/_ 6Z)<sup>2</sup> , prenem 



Aleshores 



amb 3 _̸_ = 0 . Per tant, _v_ és linealment dependent tot i ser no nul. 

74 

# 36 40. Teorema xinès del residu (Chinese remainder theorem) 

## 36.1 Explicació 

El problema clàssic és el següent: Tenim un cert nombre d'objectes. Si els comptem de tres en tres, en sobren dos; si els comptem de cinc en cinc, en sobren tres; si els comptem de set en set, en sobren dos. Quants objectes hi ha? 

És a dir, busquem _x ∈_ Z tal que: 





Com trobar una d'aquestes solucions? Ho fem per substitució successiva. 

## 36.2 Resolució pas a pas 

36.2.1 Pas 1: combinar les dues primeres congruències 

Partim de: 



Això vol dir que: 



Imposem la segona congruència: 



Substituint: 



Ara necessitem l'invers de 3 mòdul 5 , que és 2 , perquè: 



Per tant: 



75 

Això vol dir que _k_ és de la forma: 



Substituint a _x_ : 



És a dir: 



36.2.2 Pas 2: imposar la tercera congruència 

Ara imposem: 



Amb l'expressió anterior: 



Reduïm mòdul 7 ( 8 _≡_ 1 , 15 _≡_ 1 ): 



Per tant: 



Substituint: 

_x_ = 8 + 15 _t_ = 8 + 15(1 + 7 _s_ ) = 8 + 15 + 105 _s_ = 23 + 105 _s._ És a dir: 



## 36.3 Solució general 

La solució és: 



on 105 = 3 _·_ 5 _·_ 7 . 

76 

## 36.4 Comprovació 



41 observacio: unicitat modul M = mcm(m1, . . . , mn) 

siguin m1, . . . , mn > 1 i a1, . . . , an dins dels enters. Si el sistema x=_ a1 mod(m1) . . . x=_ an mod(mn) te solucio, aleshores es unica modul M = mcm(m1, . . . , mn) 

Demostracio: suposem que x iy son dues solucions del sistema. Aleshores per a cada i = 1,. . . ,n x=_ ai mod(mi), y=ai mod(mi) per tant x=y mod (mi) aixo vol dir que mi|(x-y) per tot i = 1,. . . ,n per tant x-y es multiple comu de tots els mi com que M=mcm(m1,. . . ,mn) es el minim comu multiple, tenim M|(x-y) per tant x=y mod(m) la solucio no es unica x+kM=x mod(mi) 

42 corol·lari: cas homogeni el cas homogen es aquell en que es aquell en que a1=a2=. . . =an=0 el sistema queda x=_ 0 mod(m1) . . . x=0 mod(mn) aixo vol dir que x es multiple de cada mi per tant x es multiple de M = mcm(m1,. . . , mn) per tant la solucio es: x=0 mod(M) es a dir la classe solucio es [0]M Aquest sistema sempre te solucio independentment de si els moduls son copirmers o no. a mes la unicitat modul M es exactament la de l'observacio 41 

### 1. Teorema xines del residu: 

Siguin m1,. . . ,mn>1 entre coprimers dos a dos es a dir: mcd(mi,mj)=1 tal que i!=j aleshores per a qualsevol a1,. . . ,an dins dels enters el sistema x =_ a1 mod(m1) . . . x=_ an mod(mn) demostracio constructiva 

77 

