![[supervisedLearningAndClustering.pdf]]
![[Pasted image 20251202194321.png]]
![[Pasted image 20251202194310.png]]
a: slobe
b: intercept

Function that finds the minimized loss:
$$L(a,b,S) = \frac{1}{3}\sum_{i=1}^{3} (ax_i + b - y_i)^2$$
Calculating the average of our coordinates
$$\overline{x} = \frac{x_1 + x_2 + x_3}{3}$$

$$\overline{y} = \frac{y_1 + y_2 + y_3}{3}$$
Calculating the best intercept:
$$b_{best} = \overline{y} - a \overline{x} \text{ [cite: 244]}$$
And the best slope:
$$a_{best} = \frac{\sum_{i=1}^{3}(y_{i}-\overline{y})(x_{i}-\overline{x})}{\sum_{i=1}^{3}(x_{i}-\overline{x})^{2}} \text{ [cite: 254]}$$
Sæt svaret ind i
$$y =a_{best}x + b_{best}$$
![[Pasted image 20251202200106.png]]
The learning rate $\alpha$
- If $\alpha$ is **large**, the model takes large steps. This makes training fast, but the model might overshoot the exact minimum and bounce around forever.
    
- If $\alpha$ is **small**, the model takes small steps. This is slow, but it guarantees a smooth path toward the minimum.

![[Pasted image 20251202200544.png]]
Choose a learning rate α > 0. 
Initialize θ to an arbitrary value Repeated
	θ ← θ − αL0 θ (θ, S) until θ no longer changes
The - (minus) before $\alpha$ adjust the learning curve up or down, depending on the slope of the curve. It will be smaller and smaller the number $\alpha$. So if the function goes up, the $\alpha$ will be minus to compensate and move it down, and vise versa. Until $\theta$ is 0.
![[Pasted image 20251202200935.png]]
![[Pasted image 20251202202135.png]]
![[Pasted image 20251202202212.png]]
$$||x-y||_2 = \sqrt{\sum_{i=1}^{d}(x_i-y_i)^2}$$
# Cluster Representative: The Centroid
$$\mu_{C_i} = \frac{1}{|C_i|} \cdot \sum_{o \in C_i} o$$
- **Note:** $|C_i|$ is the number of objects in cluster $C_i$.
## Cluster Quality Metrics
The clustering criterion minimized the distances within each cluster, optimizing for cohesion (small within-cluster distances).
- Total Squared Distance ($TD^2$) or Sum of Squares (SSQ): The measure of compactness for a single cluster, C10101010:
    
    $$TD^2(C) = \sum_{p \in C} ||p - \mu_C||_2^2$$
    
- Total Compactness for a Clustering: The measure of compactness for the entire clustering, which is the sum of the $TD^2$ of all $k$ clusters11:
    
    $$TD^2(C_1, C_2, \dots, C_k) = \sum_{i=1}^{k} TD^2(C_i)$$
# *k*-means Clustering - MacQueen algorithm
![[Pasted image 20251205152733.png]]
![[Pasted image 20251205152850.png]]
# Kvadratiske afstand
$$d^{2}(A,B) = (x_{A}-x_{B})^{2}+(y_{A}-y_{B})^{2}$$
Så skal man tage $\sqrt(svar)$
Og så får man distancen

Så for at finde det næste centriod, skal vi tage minimum afstanden mellem $C_{1}og C_{2}$
Så vi regner afstanden ud fra vores Centroid $C_{1}$ og så vores afstand til $C_{2}$, så vi har et $min(C_{1}, C_{2})$ der er så tæt på hinanden som muligt, f.eks. 46 og 40. Samme gør man for flere, så man konstant regner ud hvordan det ligger iforhold til de andre centroider.
## example
$d^{2}(P6, C_{1}=P3) = 49$
$d^{2}(P6, C_{2}=P9 = 26)$
$C_{3}=P11(2,10)$
$P6(9,3)\ og\ P11(2,10)$
det vil sige afstand fra P6 til P11 er
$(9-2)^{2}+(3-10)^{2}=49+49=\sqrt{98}$
 
Så tager man 
$$min(49,26,98)  Min\ er\ 26$$

Gør man for alle punkter