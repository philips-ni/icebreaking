BIT_TIPS
---

### clear the lowermost set bit of x
 - x &= (x - 1)
 
### extract the lowermost set bit
 - n = x & ~(x - 1)

