![[Pasted image 20251119123420.png]]
$N = 1517, e =13$
$m = 43$
$(43,(1517,13)) = 43^{13} \space mod \space 1517 = c$
Svar B

$43^{13} \space mod \space 1517$ (ODD)
$43^{12} \space mod \space n$ (EVEN)
$(43^{6}* \space mod \space n)^{2} \space mod \space n$ (EVEN)
$(43^{3}* \space mod \space n)^{2}$ (ODD)
$k=2$ (EVEN)
$k=1$ (BASE)

3 EVEN 
2 ODDS

![[Pasted image 20251119125925.png]]
212 er svaret (212\*49) % 221

![[Pasted image 20251119130106.png]]
![[Pasted image 20251119130114.png]]
a)
$PK=(N=91,e=37);SK=(N=91,d=23)$
$Encrypt(m,PK)=m^{37} \space mod \space 91$
$p=7$
$q=13$
$N'=(p-1)*(q-1)$
$N'=6*12=72$
$gcd(N',e)=gcd(72,37) = 1$
$72=37+35$
$37=35+2$
$35=2*17+1$

$e*d \space mod \space N' = 1$
$37*23 \space mod \space 72 \neq 1$

b)
$N=11*13=143$
$N'=10*12=120$
$gcd(120,77) = 1$

$77*53 \space mod \space 120 = 1$
Svaret er B

Out: d, fordi N er et primtal

![[Pasted image 20251119132152.png]]
6 Lists in total
$2,3,5,7,11,13$

![[Pasted image 20251119132616.png]]
$N=1517=37*41$
$N'=1476=36*41$
$e*d \space mod \space N'=1$

a)
Find (p-1)(q-1)
$(37-1)(41-1)=36*40=1440$
Find d such that $e*d \equiv 1 (mod \space N)$
Extended Euclidean Algorithm
	Normal Euclidean Algorithm
Så skal man backsubstitude to express 1 as a combination of 17 and 1440

Så
$$17*593 \equiv 1 (mod \space 1440), d=593$$
b)
$m=423$
$N=1517$
$e=17$

To encrypt $c=E(m, PK)=m^{c}(mod \space N')$
$c=562$
1 Odd
4 Even

c)
To decrypt $r=D(c,SK)=c^{d}(mod \space N')$
$r=562^{593}\ (mod\ 1517)=423$
3 Odd, 9 Even
![[Pasted image 20251119135002.png]]
Hash functions, for size reduction. Cryptographically secure, so its improbable to change the message without changing the hash.![[Pasted image 20251119135114.png]]
It will always give an Even, and 2 is simple. Then the second prime is easily found.
![[Pasted image 20251119135221.png]]
In Modulus, if numbers are negative, the encrypted message, would just encrypt to the same.
![[Pasted image 20251119135407.png]]
a)
$N=1517$
$e=13$
$m=43$



$43^{13}(mod\ 1517)=43*1185(mod\ 1517)=894$
Så $c=894$

b)
$p=37$
$q=41$
$e=13$

$13d \equiv 1 (mod\ 1440)$
$gcd(1440,13)$

Step 1: Forward division table

Step 2: Backward substitution

$d=-433$
$d=1440-433=997$