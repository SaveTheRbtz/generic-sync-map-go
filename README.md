Note that this is a PoC and you probably do not want to depend on this in production.

# Generic implementation of sync.Map

PoC of a 3x faster `sync.Map` in 1.18.
```
benchstat old generic
name                              old time/op  new time/op  delta
LoadMostlyHits/*sync.Map-8        18.0ns ± 3%   6.2ns ±20%  -65.44%  (p=0.000 n=10+10)
LoadMostlyMisses/*sync.Map-8      12.2ns ± 1%   4.1ns ± 3%  -66.37%  (p=0.000 n=8+10)
LoadOrStoreBalanced/*sync.Map-8    340ns ± 3%   199ns ± 3%  -41.63%  (p=0.000 n=10+9)
LoadOrStoreUnique/*sync.Map-8      696ns ± 4%   346ns ± 3%  -50.23%  (p=0.000 n=10+9)
LoadOrStoreCollision/*sync.Map-8  8.86ns ± 2%  3.56ns ± 8%  -59.85%  (p=0.000 n=9+10)
Range/*sync.Map-8                 4.96µs ± 2%  4.97µs ± 7%     ~     (p=0.549 n=10+9)
AdversarialAlloc/*sync.Map-8       274ns ±11%   179ns ± 3%  -34.78%  (p=0.000 n=9+7)
AdversarialDelete/*sync.Map-8      106ns ±16%    88ns ±10%  -17.20%  (p=0.000 n=10+10)
```
