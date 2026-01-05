# Graph
Grafer, er ikke kun en kurve, men også et netværk
![[Pasted image 20251125102006.png]]
Knude: $V$
Kanter: $E \subseteq V x V$

![[Pasted image 20251125102655.png]]
Vertices: P, Q, R, S, T
Edges: All the lines
Degree of a vertex: Number of edges that meet up at a vertex. So for P has 3 edges to it. R has 2, Q has 4 and so on.
Man kan kun skifte vej ved knuderne, da det er der kanterne mødes.

![[Pasted image 20251125103025.png]]
Det her er den samme graf, da kanterne føre til de samme knuder, men det ser bare anderledes ud med hvordan de er tegnet. 
$V_{vertices} = \{P,Q,R,T,S\}$
$E_{edges}=\{(T,Q), (Q,T), ...\}$

# Walks, Paths, and Cycles
En walk er at bevæge sig fra f.eks. P -> Q -> R. Hvis man siger Walk, må man gerne ramme sig selv.
En Sti (Path), når man ikke kommer forbi den samme knude.

# Connectedness
![[Pasted image 20251125103735.png]]
Disconneted Grah der er ikke en walk mellem hver bunke
Connected graph, der er en walk mellem hver bunke.
Man kan ikke komme fra den venstre til den højre og omvendt.

# Weighted Graphs
![[Pasted image 20251125103912.png]]
Hver kant har en pris for at tage. F.eks. i Minecraft hvor et mob skal bevæge sig 8 blocks, eller over ild. Ild kræver 10 blocks at tage det ene skridt, mens de 8 blocks tager 8 blocks at gå. Samme concept her.
## Pris for walk
C -> F -> I -> K
$9+2+2=13$

# Matrix Representations for Graphs
![[Pasted image 20251125110059.png]]
If G is a graph with vertices labelled {1, 2, ...}, its adjacency matrix A is the n x n matrix whose ij-th entry is the number of edges joining vertex i and vertex j. Two nodes i and j are adjacent if the ij-th entry in the adjcacency matrix is larger than 0. 

If, in addition to the vertices, the edges are labelled {1, 2,..., m}, its incidence matrix M is the n x m matrix whose ij-th entry is 1 if vertex i is incident to edge j and 0 otherwise. The figure above shows a labelled graph G with its adjacency and incidence matrices.
![[Pasted image 20251125110523.png]]

# Matrix-Matrix Multiplication
![[Pasted image 20251125110655.png]]
Længden af række og længden af søjle skal være lige lange for at man kan gange det sammen. Man ser dem som vektorer og tager prikproduktet.
Man har to valg af rækker og tre rækker af koloner i svaret, da det er det den er sat sammen af de matricer.

## Zero index
![[Pasted image 20251125111241.png]]
## One Index
![[Pasted image 20251125111258.png]]

# Powers of the Adjacency matrix
Square matricer bevare størrelsen
Vi kender
$4*4*4*4*4=4^{5}$
Vi kan her ved square matricer
$A\ x\ A\ x\ A\ x\ A\ x\ A = A^{5}$

Gange er associativ (Giver det samme på hver sin side af "=" tegnet):
$4*(4*4)= (4*4)*4$

Matrix MuH er også associativ.
$(A\ x\ B)\ x\ C= A\ x\ (B\ x\ C)$

## Theorem
If G is a graph with adjacency matrix A, and vertices with indices $1,...,n$ then for each positive integer k
the ij-th entry of $A^{k}$ is the number of different walks using exactly k edges from node i to node j
![[Pasted image 20251125114340.png]]
2 mulige stiger, fra 4 til 5. Man kan aflæse matricerne her, for fire skridt $A^{4}$ Hvor man går fra 4 til 5, er der 2 muligheder. Som vist, man tager rækker og koloner.

## Proof induktion på k
### Basis 
$$k=1\ \space \space \space(A^{k}=A)$$
Alle stiger med længden 1, er en kant.
Stiger med længe en er $(A^{k}=A)$

### Skridt
Antag sætning er OK for $A^{k}$ Vis den for $A^{k+1}$
Vis den for $A^{k+1}=A\ x\ A^{k}$

Se på et givet par i, j
Enhver stig er længe k+1

![[Pasted image 20251125120037.png]]
Samlet valg = $\Sigma_{j} a_{iL}*b_{Lj}=c$

# Algorithm for All-Pairs Shortest Path
![[Pasted image 20251127101800.png]]

$$\Sigma^{n_{k=1}a_k=a_{1,}a_{2},...,}a_{n}$$
Ny notation:
$$Sum\{a_{1},a_{2},..., a_{n}\}$$
Tage minimum af et tal, notation: 
$$min\{a_{1}, a_{2},..., a_{n}\}$$
```` python
def min(x1, x2):
	#Something recursive that chooses the Min
	"""if x1 > x2:
		min(x2, x.next)
		else:
			x2 > x1
			min(x1, x.next)"""
oversættes til
min(a_1, min(a_2, min(a_3, min(a_(k-1), a_n)))
`````

# Matix Multiplication
$$A\ x\ B = C$$
$$A= \begin{matrix}
a_{1,1} & a_{1,2}, ... & a_{1n} \\ a_{2,1} & ... & a_{2n} \\ a_{n,1} & ... & a_{nn}
\end{matrix}$$
$$c_{ij} = \Sigma^{n}_{k=1} a_{ik}*b_{k}$$
Noteret på den ny måde:
$$Sum\{a_{i,1}*b_{1j},a_{i2}*b_{2j}, ..., a_{in}*b_{nj}\}$$
## Variant Matrix mult
$$A \odot B = C$$
$$C_{ij}=min \{a_{ij}+b_{1j}, a_{i2}+b_{2j},..., a_{in}+b_{nj}\}$$
Dvs.
Plus (+, altså sum) er blevet til minimum
Og gange er blevet til plus
\+ (sum) -> minimum
   \*        ->     +
Som vist i eksemplet, så tager man 3+3 = 6, 2+1 = 3 og 2 + 5 = 7, her er det mindste 3, så derfor er minnimum = 3
![[Pasted image 20251127103849.png]]

Extended Real Number system
Alle kommatal union uendelig.
$R \cup \{\infty, - \infty\}$
Hvis man lægger noget til uendelig, er det uendelig, hvis man trækker noget fra uendelig, er det stadig uendelig. 

# The Edge Weight Matrix W
![[Pasted image 20251127105923.png]]
Diagonal står der altid 0, om man har 100 kanter eller ej.
Hvis kanterne i,j eksistere i vores figur, set på højre hånd, skriver vi det op. Hvis de er lig med hinanden, skriver vi 0, ellers skriver vi $\infty$ 

## Theorem
If G is a weighted graph with edge weight matrix W, and vertices with indices 1,...,n then for each positive integer k
the ij-th entry of
$$W^{k} = W\odot W \odot ... \odot W$$
Vi laver $W \odot W \odot ... \odot W$, k antal gange
is the length of the shortest path from i to j using maximally k edges
![[Pasted image 20251127110452.png]]
Vist i eksemplet, så er en Walk på 4 $W^{4}$ , der kan man gå fra 4 til 1, for 7 eller fra 5 til 3 for 5, når den vælger den mindste antal for Walk. Vi har lov til at tage 4 walks, men hvis man kan gøre det på 1 eller 2, stopper den bare der, ses ved 2 til 1.
Lægge dem sammen og tage minimim.
Så vi lægger 
Udregning af $W^{2}$ for række (3,5)
$$sum(\infty + 2) = \infty$$
$$sum(4+2)=6$$
$$sum(0, \infty) = \infty$$
$$sum(\infty, 6) = \infty$$
$$sum(\infty, 2) = \infty$$
$$sum(3, \infty) = \infty$$
$$min(\infty, 6, \infty, \infty, \infty, \infty) = 6$$

# Antag: der findes ikke negativ kredse
Findes ikke$$(Vægt < 0)$$
F.eks.: alle kant-vægte $\geq 0$
![[Pasted image 20251127111516.png]]
Vi kan bare tage det første punkt hvor de mødes og strege de andre ud, da de bare er længere, altså højere vægt.
Der findes altid korteste veje uden gentagelser.
	Sti uden gentagelse: $\leq n\ kanter$
	$\leq n-1\ kanter$
Har man rørt ved 2 knuder, har man 1 kant
Har man rørt ved 3 knuder, har man 2 kanter.
Har man rørt ved 4 knuder, har man 3 kanter.
Så vi skal kun holde står på antal knuder - 1, som giver kanter.

Vi når til et tidspunkt, hvor vi ganger noget på og så blvier de lig med hinanden. Så fra 5 og opefter kan vi stoppe, for k=6. Når vores matrice er længden 6. Vi skal nå til der hvor vi får en gentagelse, for at vise at v kunne have været stoppet en før, så vi skal udregne $W^{5}$ for at vide $W^{4}$ er den samme som $W^{5}$

Så vi kan sige $n-2$ er der den stopper med at udvikle sig.
![[Pasted image 20251127111748.png]]

x tager $O(n^{3})$ tid (for n x n matrice)
$\odot\ tager\ O(n^{3}) -|--------$
Gentag n-1 gange
$$n^{3}*(n-1)\approx n^{4}=O(n^{4})$$
### Nemmere måde at skrive det på (Repeated Squaring)
$$W \rightarrow W^{2}$$
$W^{2}=W \odot W$
$W^{4}= W^{2} \odot W^{2}$
$W^{8}=W^{4} \odot W^{4}$
Vi lander nok et sted alt for langt ude, hvor det ikke ændre sig, men det er fint, da det er det samme som n-2, hvor man burde stoppe, men matricen er det samme. So all good.

Efter *i* skridt: $W^{2^{i}}$
Vi kan stoppe så snart vi har at $2^{i} \geq n-1$
Det betyder at vi kan tage $log_{2}$ på begge sider som giver.
$$i \geqq log_{2}(n-1)$$
Vi er interreseret i første *i* hvor $log_{2}(n-1)$

Samlet tid for denne variant af algortime:
$\approx O(n^{3}*log(n))$
![[Pasted image 20251127114234.png]]
## Lemma
![[Pasted image 20251127111828.png]]
