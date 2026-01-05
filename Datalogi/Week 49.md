### 1. Identify Variables

- **Number of Vertices ($n$):** $n = 200,000 = 2 \times 10^5$ users3.
    
- **Matrix Size ($n^2$):** $(2 \times 10^5)^2$.
    
- **Storage per Entry:** 4 bytes4.
    
- **Available RAM:** 64 GB (Gigabytes)5.
    

### 2. Calculate Total Required Storage

The total storage $S$ (in bytes) is:

$$S = n^2 \times 4 \text{ bytes}$$

$$S = (200,000)^2 \times 4 \text{ bytes}$$

$$S = (40,000,000,000) \times 4 \text{ bytes}$$

$$S = 160,000,000,000 \text{ bytes}$$

### 3. Convert to Gigabytes (GB) and Compare

To compare this to the available RAM, we convert the required storage from bytes to Gigabytes (GB). We use the standard binary conversion where $1 \text{ GB} = 2^{30} \text{ bytes} = 1,073,741,824 \text{ bytes}$.

$$S \approx \frac{160,000,000,000 \text{ bytes}}{1,073,741,824 \text{ bytes/GB}} \approx 0.149 \text{ GB}$$

Since $1 \text{ GB} = 1024 \text{ MB}$, we can also express this in Megabytes (MB):

$$S \approx 0.149 \text{ GB} \times 1024 \text{ MB/GB} \approx \mathbf{152.6 \text{ MB}}$$

