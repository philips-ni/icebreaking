BIT_TIPS
---

### clear the lowermost set bit of x
 - x &= (x - 1)
 
### extract the lowermost set bit
 - t = x & ~(x - 1)

### get the Nth bit of x
 - t = (x >> n) & 1
 
### swap the i_th and j_th  bit of x
 - bit_mask = (1 << i ) | (1 << j)
 - x ^= bit_mask
 
