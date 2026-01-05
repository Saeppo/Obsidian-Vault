# Competitive Analysis
Competitive analysis is one way to measure the quality of an online algorithm.
## Idea
OPT = Optimal Offline Algorithm.
Offline means getting the entire input before having to compute.
En optimal algoritme, er en der kender fremtiden.

## Notation
ALG = Results of running an algorithm.
ALG(I) denote the result of running an algorithm ALG on the input sequence I. Thus, OPT(I) is the result of running OPT on I.

Kigger på forskellen mellem vores ALG over OPT, som giver en garanti for alle vores sekvenser, bestemt også den værste. 
An Algorithm, ALG, is c-competitive if
$$
\forall I : \frac{ALG(I)}{OPT(I)} \leq c
$$
ALG has competitive ratio c if
	c is the best (smallest) c for which ALG is c-competitive

Technically, the definition of being c-competitive is that ∃b ∀I : Alg(I ) ≤ c Opt(I ) + b, but the additive term, b, does not become relevant for what we consider. Also not relevant today, a best c does not necessarily exist, so the competitive ratio is inf {c | Alg is c-competitive}.

## A simplest online problem
We have a very simple request sequence with very simple responses.![[Pasted image 20251120102356.png]]
### OPT example
![[Pasted image 20251120102511.png]]
På dag 10 køber vi skiene, indtil da lejer vi dem bare.  
Vi kender ikke d, men sådan vil den optimale algoritme se ud. Hvis vi bliver kaldt hjem før dag 10, så køre vi otimalt, da omkostningerne d < 10, men hvis vi bliver kaldt hjem dag 10 eller senere, er det worst case, da vi skulle have købt dem dag et.
Vi klare os maksimalt dobbelt så dårligt i det her eksempel, hvor vi tager hjem efter 19 dage$$\frac{ALG}{OPT} = \frac{19}{10}<2$$
![[Pasted image 20251120102910.png]]
2-competitive, man gre det aldrig bedre end 2 gange OPT.
Competitive ratio, er hvad svaret er lige præcist.
Den er 2-competitive, men den er ikke competitive ratio 2, da competitive ratio 2 er det den er lige præcist.

# Online problemer
Input kommer en af gangen.
Hver gang vi får en forespørgelse, skal vi tage en beslutning. Vi kan ikke lave beslutningen om når den er taget.
Vi vil minimere omkostningerne.

## example
Ski problem, er det samme som ens pc der skal reguelere strøm. Luk ned koster meget energi, så den skal vurdere når man stopper med at taste, om den skal blive ved med at køre, eller om den skal køre med mindre kraft.

# Machine Scheduling
$m \geq 1$ machines
n jobs of varying sizes arriving one at a time to be assigned to a machine. 
The goal is to minimize makespan, i.e., finish all jobs as early as possible. 
Algorithm List Scheduling (Ls): place next job on the least loaded machine.

Makesspan = Tidspunkt hvor alle jobs er færdige.
Minimize makespan = Så kort tid som muligt, hvor alle jobs er færdige.
LS= Algorithm List Scheduling

## List Scheduling example
![[Pasted image 20251120103500.png]]
Hvordan jobs (øverst) bliver tildelt ud på maskiner M. 
OPT er ikke en online algortihm. Men det er en naturlig reference point, det er drømmen, men kan ikke opnås, men vi kan sammenlign hvor godt vi køre iforhold til OPT.
As input sequences I get harder, OPT(I) typically grows, so a comparison to OPT remains somewhat reasonable.
![[Pasted image 20251120103918.png]]
Vi har vist vores competitive ratio, er mindst $\frac{10}{7}$, en nedregrænse, eller negativt resultat, er nedre grænse for hvor godt det kan gå
![[Pasted image 20251120104158.png]]
Hvis man har m maskiner, så vil det se ud som overstående. Variable af en rektangle. Længden M maskiner, og højden af (m-1)+m
# Machine Scheduling - Proof Techniques
![[Pasted image 20251120104723.png]]
Lower bound proof vist tidligere. Upper bound prrof vises under.
![[Pasted image 20251120104756.png]]
t her, er det der giver os det makespan, som er resultat for hvor lang tid jobbet køre.
T er den samlede længde af alle jobs.
l er længden af jobenheder op til 0, den stiblede linje, som er der hvor vores makespan starter. De der hak der er, kan de ikke komme under. List schedual algortihm, placere den på den mindst belastede maskiner, så derfor sættes t der og skaber vores l-grænser
Vi kan sige OPT $\geq$ T/m og OPT $\geq$ t, OPT tager mindst t at blive færdig.

## Theorem
The algorithm Ls for minimizing makespan in machine scheduling with m ≥ 1 machines has competitive ratio $2- \frac{1}{m}$

# Bin Packing
Bin = container
Unbounded supply of bins of size 1. 
n items, each of size strictly between zero and one, to be placed in a bin. 
Obviously, the items placed in any given bin cannot be larger than 1 in total. 
The goal is to minimize the number of bins used. 
Algorithm First-Fit (FF): place next item in the first bin with enough space. The ordering of the bins is determined by the first time they receive an item.

Man kan ikke overfylde en Bin, og man vil gerne bruge så få som muligt.

## First Fit (FF) example
![[Pasted image 20251120110444.png]]
Bin kan mask være 1. Men vi kan optimere det her, OPT ville have 3 bins.

## Simple Lower Bound Against FF
![[Pasted image 20251120110945.png]]
Vi "driller" algortimen, ved at give den nogle inputs der er $\frac{1}{3}+ \frac{1}{1000}$, så der er ikke plads til 1/3+1/1000 inden for 1, så algortimen fordeler det dårligt.
1/2 er også $\frac{1}{2} + \frac{1}{1000}$
Så OPT lægger 1/3 og 1/2 sammen, hvor vores algortime lægger dem hver for sig.

Ff has been shown to be 1.7-competitive \[hard]. Thus, the competitiv e ratio is at most 1.7. 
We have just shown that the competitive ratio is at least 1.5. 
So, the competitive ratio of Ff is in the interval \[1.5, 1.7]. 
We’ll approach the precise value in the exercises.

Det ikke altid i online algortimer, at man kan sige at den competitive ratio ligger lige præcis der, men vi kan vide hvad den ligger imellem.

# Bevis for Competitive ratio

En boks A og en boks B, hvor man åbner en af dem. A boks har kost a og B boks har kost b. Inde i en af dem ligger præmien og man vil gerne åbne den.

$$\frac{a+b}{max\{a,b\}}$$
ex
$$a=b, CR\ på\ 2$$
Advisary lægger den i den boks, som vi ikke åbner, worst case.
Åbner A med sandsynligheden p. Hvilken omkostning vil man få? og hvad er en competitive ratio?

Min forventede competitive ratio (CR):
	Med sandsyngliheden p, finder man a.
	Præmien er gemt i A. Forventede competitive ratio (CR)$$\frac{pa+(1+p)(a+b)}{a}$$
	Præmien er gemt i B. Forventede competitive ratio (CR) $$\frac{p(a+b)+(1+p)b}{b}$$
$$\frac{pa+(1+p)(a+b)}{a}= \frac{p(a+b)+(1-p)b}{b}$$
$$pab+ab+b^{2}-pab-pb^{2}=pa^{2}+pab+ab-pab$$
$$b^{2}-pb^{2}=pa^{2}$$
$$b^{2}=pa^{2}+pb^{2}$$
$$p=\frac{b^{2}}{a^{2}+b^{2}}$$
Det her er sandsynligheden p, som er fundet for de to bokse., for man åbner den rigtige.
Vi har valgt vores Competitive Ratio (CR) er sat lig med hinanden, sp vi kan vælge en af dem.
$$\frac{b^{2}}{a^{2}+b^{2}}*a+(1- \frac{b^{2}}{a^{2}+b^{2}})(a+b)$$
1 kan vi omskrive til $a^{2}$ over $a^{2}$ +$b^{2}$
$$\frac{b^{2}}{a^{2}+b^{2}} + \frac{1}{a} \frac{a^{2}}{a^{2}+b^{2}} (a+b)$$
$$\frac{b^{2}+a(a+b)}{a^{2}+b^{2}}$$
$$
\frac{a^{2}+b^{2}+ab}{a^{2}+b^{2}}
$$
Hvis a=b, hvad sker der så, så kan vi læse dem alle sammen som a.
$$
a=b: \frac{3}{2}
$$
Vores forventede competitive ratio, er $\frac{3}{2}$
Hvis $a \neq b$

Fastholder a
$b \rightarrow O^{+} : 1$
$b \rightarrow \infty : 1$

Der hvor a = b, får vi $\frac{3}{2}$
Hvis værdierne er en smule anderledes, bliver det bedre, worst case er a = b.
