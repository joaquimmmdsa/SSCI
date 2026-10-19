1 

_Tema 1: Modular Arithmetic Tools_ 

# **1 Modular Arithmetic Tools** 

## **1.1 Divisibility in** Z 

- **1.1** Let _a, b ∈_ Z be integers such that mcd( _a, b_ ) = 1. Show that the greatest common divisor of _a_ + _b_ and _a − b_ is either 1 or 2. 

- **1.2** Show that, for every _a, b, m ∈_ Z, mcd( _ma, mb_ ) = _m ·_ mcd( _a, b_ ). 

- **1.3** Is it true that, for _a, b ∈_ Z, mcd(3 _a − b, b −_ 2 _a_ ) = mcd( _a, b_ )? Explain why. 

- **1.4** Compute mcd(28 _n −_ 5 _,_ 35 _n −_ 8), for _n_ ⩾ 1. 

- **1.5** Find the greatest common divisor and the B´ezout coefficients for each of the following pairs of integers (check its validity): a) 1492 _,_ 1776; b) 7469 _,_ 2464; 

   - c) 500 _,_ 11312. 

- **1.6** Compute the least common multiple of each pair of integers from the previous exercise. 

- **1.7** Show that the fraction<sup><u>4</u></sup> 2<sup>_<u>n</u>_</sup> _n_<sup><u>+5</u></sup> +3<sup>isirreducibleforevery</sup><sup>_n_⩾1.</sup> 

- **1.8** Solve the following Diophantine equations: a) 93 _x −_ 81 _y_ = 3; b) 71 _x −_ 50 _y_ = 1; c) 42 _x_ + 18 _y_ = 34; 

   - d) 283 _x −_ 1722 _y_ = 31. 

- **1.9** a) Using the Euclidean algorithm, compute the greatest common divisor mcd(1911 _,_ 65). b) Justify whether the Diophantine equation 3822 _x_ + 65 _y_ = 26 has solution or not, in the positive case, describe them all (Indication: you can use the previous item). 

- **1.10** Ask somebody to multiply his/her day of birthday by 12, multiply his/her month of birthday by 31, add the two results, and tell you only this final sum. Can you guess, just with this information, when is his/her birthday? 

- **1.11** Show that if _ab_ is a perfect square and mcd( _m, n_ ) = 1, then _a_ and _b_ are both perfect squares as well. 

- **1.12** Show that if _a_ and _b_ are integers and _a_<sup>2</sup> _|b_<sup>2</sup> , then _a|b_ . 

- **1.13** Find the smallest natural number _n_ such that _n/_ 2 is a perfect square, _n/_ 3 is a perfect cube, and _n/_ 5 is a perfect fifth power. 

_Seguretat i Secret en la Codificaci´o de la Informaci´o (EPSEM) curs 26–27–Q1._ 

2 

- **1.14** Find the decomposition of the six integers involved in Exercise 1.5, as product of primes. Check the formulas relating these decompositions with their respective greatest common divisor and least common multiple (computed before). 

## **1.2 Congruences** 

- **1.15** Do the following calculations in the indicated modular arithmetic: a) 8 _·_ (7<sup>2</sup> _−_ 2) + 6 a Z _/_ 12Z; 

   - b) (8<sup>3</sup> _−_ 1)<sup>4</sup> a Z _/_ 6Z; c) ((4<sup>3</sup> )<sup>5</sup> _−_ 1)<sup>4</sup> + 2<sup>4</sup> _·_ (3<sup>4</sup> _−_ 1) a Z _/_ 10Z. 

- **1.16** Prove that if _a ≡ b_ (mod _m_ ) then, for every value of _k_ , _ka ≡ kb_ (mod _m_ ). Is it true that if there exists _k_ such that _ka ≡ kb_ (mod _m_ ), then _a ≡ b_ (mod _m_ )? And what if _k_ is a prime number? 

- **1.17** Prove that if _a ≡ b_ (mod _m_ ) then, for every value of _n_ , _a_<sup>_n_</sup> _≡ b_<sup>_n_</sup> (mod _m_ ). Is it true that if there exist _n_ such that _a_<sup>_n_</sup> _≡ b_<sup>_n_</sup> (mod _m_ ), then _a ≡ b_ (mod _m_ )? 

- **1.18** Prove that every even prime _p_ which can be written as the sum of two squares must be _p ≡_ 1 (mod 4). 

- **1.19** Make a complete list of the invertible elements modulo 2, 3, 4, 5, 6, 7, 8, 9, and 10. 

- **1.20** Are the elements 29, 234, and 512 invertible modulo 1170? In the affirmative case find their inverses. 

- **1.21** Find all the solutions to the following equations: a) 31 _x_ = 1 in Z _/_ 101Z; b) 4 _x_ = 0 in Z _/_ 18Z; c) 6 _x_ = 0 in Z _/_ 30Z. 

**1.22** Solve the following systems of linear equations over the indicated rings (try different methods for each one, and check the results agree): a) in Z _/_ 17Z; � _x−_ + 32 _x_ + 14 _y_ = 15 _y_ = 1 b) in Z _/_ 5Z and Z _/_ 25Z; � 23 _xx −_ + 24 _yy_ = 0= 2 c) in Z _/_ 5Z and Z _/_ 25Z; � 43 _xx −_ + 24 _yy_ = 0= 2  3 _x_ + 2 _y_ + _z_ = 0 d) _x − y −_ 4 _z_ = 2 in Z _/_ 2Z and Z _/_ 7Z.   _−x_ + 2 _y_ + 3 _z_ = 3 

_The Chinese reminder theorem_ 

_1.3_ 

3 

- **1.23** Decide which of the following matrices are invertible over the indicated rings; in case they are, find the inverse: 



## **1.3 The Chinese reminder theorem** 

- **1.24** (Sun Tsu Suan-Ching, s. IV) We have a collection of objects; when counted in groups of three there are two remaining, when counted in groups of five there are three remaining, and when counted in groups of seven there are two remaining. How many objects do we have? 

- **1.25** Solve the following systems of congruences: 



- **1.26** Let _m_ 1 _, . . . , mn >_ 1 be integers coprime to each other, and let _M_ = _m_ 1 _· · · mn_ . Prove that, for every _a, b ∈_ Z, _a ≡ b_ (mod _M_ ) if and only if _a ≡ b_ (mod _mi_ ), for every _i_ = 1 _, . . . , n_ . Is there any relation with the Chinese Remainder Theorem? 

- **1.27** Check, by hand, whether the maps 



are bijective or not. Does it match with a theorem you know about this? 

## **1.4 Fermat and Euler’s theorems** 

- **1.28** a) Find the inverse of 37 in Z _/_ 98Z. 

   - b) Compute the value of 37<sup>55</sup> _·_ 53<sup>13</sup> (mod 98). 

_Seguretat i Secret en la Codificaci´o de la Informaci´o (EPSEM) curs 26–27–Q1._ 

4 

- **1.29** Compute the values of (a) 513<sup>1017</sup> (mod 6); (b) 2<sup>154</sup> (mod 5); (c) 3<sup>178</sup> (mod 12). 

- **1.30** Compute the last two digits of the huge number 103<sup>1243</sup> . 

- **1.31** Find all the numbers _n_ for which 10<sup>_n_</sup> + 3 is multiple of 7. 

- **1.32** Find all the numbers _n_ for which 4<sup>_n_</sup> + 5 is multiple of 15. 

- **1.33** a) Solve the equation 2<sup>2021</sup> ( _x −_ 2<sup>2022</sup> ) = 4<sup>2023</sup> (mod 13). b) Deduce from it a description of all solutions to the equation 2<sup>2021</sup> (10 _·_ 3<sup>_n_</sup> _−_ 2<sup>2022</sup> ) = 4<sup>2023</sup> (mod 13). 

- **1.34** Compute 2022<sup>20222022</sup> (mod 19) and (mod 21). 

- **1.35** Compute the following values of the Euler phi function: _φ_ (128), _φ_ (1123), _φ_ (1125), _φ_ (29270241), and _φ_ (12648925575). 

- **1.36** Order the following rings by decreasing amount of invertible elements: Z, Z _/_ 11Z, Z _/_ 12Z, Z _/_ 18Z, and Q. 

- **1.37 The Mersenne numbers.** The _q_ -th Mersenne number is defined as _Mq_ = 2<sup>_q_</sup> _−_ 1. These numbers are not always prime, but were found and studied by the french mathematician Marin Mersenne as an important source of prime numbers. 

   - a) show that if _Mq_ is prime then _q_ is prime as well (hint: _x_<sup>_n_</sup> _−_ 1 = ( _x −_ 1)( _x_<sup>_n−_1</sup> + _x_<sup>_n−_2</sup> + _· · ·_ + _x_ + 1)); 

   - b) show that the converse is not true, by giving the smallest possible counterexample; 

   - c) in the cases where _q_ is primer and _Mq_ is not, the primes dividing _Mq_ are very limited: show that if _p, q_ are primes and _p|Mq_ then _p ≡_ 1 (mod _q_ ) (hint: use the previous item); d) Decide whether _M_ 13 or _M_ 17 are primes or not (you may use calculator or computer, but it is not about doing a big number of divisions: use the previous items to drastically reduce the computation). 

## **1.5 True/false problems** 

- **1.38** Decide whether the following assertions are true or false, justifying conveniently your answers with an argument or a counterexample: 

   - a) In the ring _M_ 2(Z) there are two elements _A, B̸_ = 0 such that _AB_ = 0. 

   - b) In the ring _M_ 2(Q) it is true that _AB_ = _AC ⇒ B_ = _C_ . 

   - c) There is a ring containing elements opposed to themselves. 

   - d) In a ring _R_ , if two elements _a, b ∈ R_ are invertible, then so is _ab_ and ( _ab_ )<sup>_−_1</sup> = _a_<sup>_−_1</sup> _b_<sup>_−_1</sup> . 

   - e) There is a ring _R_ containing two elements _a, b ∈ R_ such that _a_<sup>2</sup> = 1, _b_<sup>2</sup> = 1, but ( _ab_ )<sup>2</sup><sup>_̸_</sup> = 1. 

_1.5 True/false problems_ 

5 

- f) In Z, mcd(249018 _,_ 34650) = 462. 

- g) In Z, if _a̸_ = 2, _a|_ ( _b_ + _c_ ) and _a|_ ( _b − c_ ), then _a|b_ and _a|c_ . 

- h) In Z, if _a_ ´es odd, _a|_ ( _b_ + _c_ ) and _a|_ ( _b − c_ ), then _a|b_ and _a|c_ . 

- i) In Z, if _d|a_ , _d|b_ and we write _a_ = _da_<sup>_′_</sup> and _b_ = _db_<sup>_′_</sup> , then _a_<sup>_′_</sup> and _b_<sup>_′_</sup> are coprimer. 

- j) The Diophantine equation 13 _x_ + 23 _y_ = 4 has no integer solutions. 

- k) All the integral solutions to the equation 2 _x −_ 6 _y_ = 8 are of the form _x_ = 16 + 3 _λ_ , _y_ = 4 + _λ_ , _λ ∈_ Z. 

- l) In Z, mcd( _a,_ mcm( _b, c_ )) = mcm(mcd( _a, b_ ) _,_ mcd( _a, c_ )). 

- m) Less than a fourth of the numbers between 1 _,_ 2 _, . . . ,_ 100 are primers. 

- n) The integer 2347 is prime. 

- o) If [ _a_ ] _m ∩_ [ _b_ ] _m̸_ = _∅_ then _m|_ ( _a − b_ ). 

- p) For every _a ∈_ Z and _m_ ⩾ 2, we have that [ _a_ ]2 _m ⊆_ [ _a_ ] _m_ , but they are not equal. 

- q) If [ _a_ ] _m ∩_ [ _b_ ]2 _m̸_ = _∅_ then [ _a_ ]2 _m_ = [ _b_ ]2 _m_ . 

- r) In Z _/_ 6Z we have that 3 = 0 because “2 _·_ 2 = 2 _·_ ( _−_ 1) _⇒_ 2 = _−_ 1 _⇒_ 3 = 0”. s) The equation 2 _x_ = 7 (mod 10) has no solution, while the equation 2 _x_ = 6 (mod 10) has two. 

2 _x_ + 3 _y_ = 3  t) The system of equations _x_ + 2 _y_ = 4  5 _x −_ 4 _y_ = 2 <sup>iscompatibleanddeterminedinZ</sup><sup>_/_13Z.</sup> 

- u) If _a ≡ b_ (mod _r_ ) and _c ≡ d_ (mod _s_ ), then _a_ + _b ≡ c_ + _d_ (mod _t_ ) where _t_ = mcm( _r, s_ ). 

- v) If _a ≡ b_ (mod _r_ ) and _c ≡ d_ (mod _s_ ), then _ab ≡ cd_ (mod _t_ ) where _t_ = mcd( _r, s_ ). 

- w) 11<sup>11111</sup> _≡_ 6 (mod 13). 

- x) 22<sup>2222</sup> _≡_ 33<sup>3333</sup> (mod 17). 

- y) If _r ≡ s_ (mod _p_ ), then _a_<sup>_r−_1</sup> _≡ a_<sup>_s−_1</sup> (mod _p_ ). 

- z) If _p_ and _q_ are different primes and _a ∈_ Z satisfies _p̸ |a_ and _q̸ |a_ , then _a_<sup>(</sup><sup>_p−_1)(</sup><sup>_q−_1)</sup> _≡_ 1 (mod _pq_ ). 

