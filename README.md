# Fermat's Little Theorem proof using multinomial theorem

Ahhh these mathematicians...<br>
We need to prove $a^{p} \equiv a \mod p$ with $p$ prime and $p > a$.

## Multinomial theorem
<p>
  Since this is quite difficult to understand I'm simplifying as much as possible (it's almost the same as Wiki by the way).
  For any positive integer $m$ and non-negative integer $n$ this theorem describes how a sum of $m$ terms expands when raised to the nth power:

  $(x_{1} + x_{2} + \dots + x_{m})^{n} = \sum_{k_{1} + \dots + k_{m} = n} (\frac{n!}{k_{1}! \dots k_{m}!}) x_{1}^{k_{1}} x_{2}^{k_{2}} \dots x_{m}^{k_{m}}$

  This is a strange summation because of: $k_{1} + \dots + k_{m} = n$. There's no need to explain the meaning but it's somehow strange because it builds a combination of $k_{1} \dots k_{m}$ implicitly, see below.<br>

</p>

## Lightning fast example

<p>
  $(a + b + c)^{3} = a^{3} + b^{3} + c^{3} + 3a^{2}b + 3a^{2}c + 3b^{2}a + 3b^{2}c + 3c^{2}a + 3c^{2}b + 6abc$

The implicit combination is:<br>

  1. $(3, 0, 0)$
  2. $(0, 3, 0)$
  3. $(0, 0, 3)$
  4. $(2, 1, 0)$
  5. $(2, 0, 1)$
  6. $(1, 2, 0)$
  7. $(0, 2, 1)$
  8. $(1, 0, 2)$
  9. $(0, 1, 2)$
  10. $(1, 1, 1)$

Combinations are not an easy topic, here the quest. is: how many sets of $3$ elements can we build with 4 elements ($0, 1, 2, 3$) without breaking $k_{1} + \dots + k_{m} = n$ ? Not so easy. Since $3$ is enough to saturate it we'll have $n$ sets with it, and $1$ set with $1s$. Then $(2, 1, 0)$ form: <br>

$3! = 6$ combinations of 3 elements and <br>
$6 + n + 1 = 10$ solutions.

But there's another better formed solution for sure.

Now what's actually crazy about this theorem is that it correlates these combinations with powers and coeffs of every term of any power (ahhh these mathematicians...).<br>

$(\frac{n!}{k_{1}! \dots k_{m}!})$ 

This is the coeff. of every term, if you try to calculate it you will find that is correct. Now for this example is quite fast to check, but it actually works for every power and any number of $xs \dots$

</p>

## Back to Fermat

<p>
  We can represent $a^{p}$ as $(1 + 1 + \dots + 1)^{p}$ and apply the multinomial theorem, this will build some sets with $a$ $k_{1} \dots k_{a}$.<br>
  We can immediately notice $a$ sets of $(p_{1}, 0_{2}, 0_{3}, \dots, 0_{a})$ like terms (for which the coeff. will be $1$).<br>
  All other terms will need to 'produce' $p$ too as sum of $k_{1} \dots k_{a}$, then:
  $(\frac{n!}{k_{1}! \dots k_{m}!})$ will have $k_{1}! \dots k_{m}!$ composed only by factors which are coprime with $p$ since it's prime and $p > k_{1 \dots m}!$. This means: <br>
  $(\frac{n!}{k_{1}! \dots k_{m}!}) \equiv 0 \mod p$

  and:

  $(\frac{n!}{k_{1}! \dots k_{m}!}) \equiv 1 \mod p$ 

  in every other case.

  Since 'every other case' are the cases mentioned initially and there are $a$ of those. We will end up having something like:<br>

  calling $C_{1 \dots nCombs}$ the coeffs of the multinomial theorem, and $z_{1 \dots nCombs}$ the products of $x_{1 \dots a}^{k_1 \dots a} = 1$:

  $a^{p} = C_{1}z_{1} + C_{2}z_{2} + \dots + C_{nCombs}z_{nCombs}$

  will have $a$ $C_{?}z_{?} \equiv 1 \mod p$ and $nCombs - a$ $C_{?}z_{?} \equiv 0 \mod p$ then:<br>

  $a^{p} = (C_{1}z_{1} + C_{2}z_{2} + \dots + C_{nCombs}z_{nCombs}) \equiv a \mod p$
  
  which proves the theorem.

</p>

## $a^{p - 1} \equiv 1 \mod p$ case proof background

### Cancellation law
<p>
  If $u, x, y$ are integers and $u$ is coprime with a prime $p$ then if:<br>

  $ux \equiv uy \mod p$
  
  -> $x \equiv y \mod p$

  because if:

   $ux \equiv uy \mod p$ -> $p | u(x - y)$

   and since $u$ is coprime with $p$:

   $p | (x - y)$ -> $x \equiv y \mod p$

   Note the first 'if' statement: $ux \equiv uy \mod p$ is the starting point; the viceversa is not true. Infact this congruence forces $u$ to be big enough to restart the 'cycle' of $p$ otherwise it clearly wouldn't make sense. Also I guess that there's some rule on how many 'cycles', because even here is quite clear that if $x > y$, $u$ will make $x$ to restart the 'cycle' more often. There must be some 'overlapping' rule which I guess it coincides with the Fermat's Little Theorem but for the moment we are good with this result.

</p>

### Rearrangement property

<p>
$a$ and $p$ are coprimes, $p$ is prime:
  
  $a, 2a, 3a, \dots, (p - 1)a \mod p$

  becomes a 'rearrangement' of:
  
  $1, 2, 3, \dots, (p - 1)$

  This one could look exactly like the former but it's not. This property does not care at all about congruences equalities; it just states that the first formula will be 'mapped' into that sequence of values. 'rearrangement' means that we don't care about which congruence will be mapped into which value, we just want to prove that all those values will be mapped. Nonetheless we will use the 'cancellation law' to prove it (:'D).
The fact that no congruence will 'produce' $0$ is trivial. Why all those values will be distinct is the real question.
<br>
We take the sequence of congruences:

$a, 2a, 3a, \dots, (p - 1)a \mod p$

and represent each pair as:

$ka \equiv ma \mod p$

From the 'cancellation law' we know that since $a$ is coprime with $p$:

$ka \equiv ma \mod p$

-> $k \equiv m \mod p$

but this is true only if $k = m$, and since this is not true then every $ka \equiv ma \mod p$ pair must produce a different remainder, and since the result set is: $\\{1, 2, 3 \dots, (p - 1)\\}$ then the property is proved. Here should be noted that the 'rearrangement property' works if and only if we consider the whole $\\{1, 2, 3, \dots, (p - 1)\\}$ set. If we operate a removal of any element the property doesn't hold (for the Euler's Theorem proof it holds because it considers every coprime of $n$).
  
</p>

## $a^{p - 1} \equiv 1 \mod p$ proof

<p>
  This proof has been discovered by James Ivory and Dirichlet.<br>
  Having proved the former properties this will be easily understandable. <br>

  We take the 'rearrangement property' and state that if it holds, then, this holds:

  $a * 2a * 3a * \dots * (p - 1)a \equiv 1 * 2 * 3 * \dots * (p - 1) (\mod p)$

  which is quite obvious at this point.<br>
  Now we can collect every term:

  $a^{p - 1}(p - 1)! \equiv (p - 1)! (\mod p)$

  We can think at this formula as:

  $a^{p - 1}(Z) \equiv 1(Z) (\mod p)$

  where $Z$ is coprime with $p$, then, applying the 'cancellation law':

  $a^{p - 1} \equiv 1 (\mod p)$

  which proves $a^{p - 1} \equiv 1 \mod p$.
</p>

## Using the same reasoning to prove Euler's Theorem: $a^{\phi(n)} \equiv 1 \mod n$

<p>
  We call $z_{1} \dots z_{\phi(n)}$ the integers which are coprime with $n$, then using the 'rearrangement property' (which holds because $a$ and $n$ are coprimes and because $z_{1} \dots z_{\phi(n)}$ are coprimes with $n$ [result set: $\{z_{1}, z_{2}, \dots, z_{\phi(n)}\}$]):

  $z_{1}a * z_{2}a * z_{3}a * \dots * z_{\phi(n)}a \equiv z_{1} * z_{2} * z_{3} * \dots * z_{\phi(n)} (\mod n)$

  collecting the terms
  
  $a^{\phi(n)} Z \equiv (1)Z (\mod n)$

  and using the 'cancellation law' (holds since $z_{1} \dots z_{\phi(n)}$ are coprimes with $n$):

  $a^{\phi(n)} \equiv 1 (\mod n)$

  To prove the result set mentioned initially, it's actually quite trivial that:<br>

  $a * z_{?} \equiv z_{?} \mod n$  
  
</p>

## Proof of $a^{p - 1} \equiv 1 \mod p$ using elements of the group theory

<p>
  This could seem unnecessary at this point, but it could be useful to understand some basic (while important) group theory elements.
  
  $G = \\{1, 2, \dots, p - 1\\}$

  with the operation of multiplication:

  $\\{G, *\\} = \\{z_{x \mod p} * z_{y \mod p} \mod p\\}$

  where $x, y$ are positive integers; forms a multiplicative group, i.e. a set with a binary operation which produces from $2$ elements of the set, $1$ element of the same set; where exists an identity element ($1$) and where each element has an inverse.<br>
  Since all these requirements are quite obvious, the only one which needs a more detailed analysis is the inverse existence for every element which is anyway quite easy to prove: calling $z$ any element of G, since $z$ is coprime with $p$, the Bezout's Identity ensures that:

  $zk + (-x)p = 1$

  exists for every $z$, proving this statement. The problem now is to prove that $k < p$ and that every solution is unique, i.e. for every:

  $z_{1}, z_{2} \in G$ -> $k_{1} \neq k_{2}$ where $k_{1}, k_{2} < p$

  Given the omomorphism (which proves $k_{1}, k_{2} < p$):

  $\varphi(a - b) = \varphi(a) - \varphi(b)$
  
  -> $(a - b) \mod p = a \mod p (-b) \mod p$
  
  -> $a + p - b \mod p = a \mod p + p - b \mod p$
  
  -> $a - b \mod p = a \mod p - b \mod p$

  we can rewrite the Bezout's Indentity as:

  $zk \equiv 1 \mod p$

  Now we can reuse the almighty 'cancellation law' and state that if:

  $z_{1}k_{1} \equiv z_{2}k_{1} \mod p$
  
  it's true, then $z_{1}, z_{2}$ should be the same number since $z_{1}, z_{2} < p$ and $k_{1} < p$ (this means it's coprime, otherwise we couldn't use the law). Since the hypothesis is that they are not the same number $k_{1_{1}}, k_{1_{2}}$ are forced to be different. This proves the uniqueness of the inverses and the Wilson's Theorem since this proof was requested to complete the proof.<br>

  Now, since we just proved that $G$ is a multiplicative group (we can write it like: $G_{p}^{*}$):<br>

  let $a$ be an element of $G_{p}^{*}$, let $k$ be the order of $a$, i.e. the smallest $k$ such that $a^{k} \equiv 1 \mod p$, then:<br>

  $1, a, a^{2}, \dots, a^{k - 1} (\mod p)$ 

  form a subgroup of $G_{p}^{*}$
  
  
</p>
