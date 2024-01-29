# Encode game state
Reasons to record encoded states over moves
* Gameplay can be replayed from any states, backward and forward. By using move sequence to reach certain state in the gameplay, moves need to be aggregated from start. Viewing gameplays in Counter Strike: Global Offensive suffers from long delay when jumping between rounds, which is caused by replaying from start everytime on jumping. In our case, the gameplay of m, n, k game could be long if k is large enough.
* In case errors can happen while recording, faults only remain in the state rather than whole gameplay, comparing to using moves.

A disadvantages is that it may take more spaces to store, comparing to 4 bytes at most per move.  

Some ideas on designing encoding: Since later states contain earlier states, we may have the code partial ordered. This may make states search-able. Puffer code for encoding a tree is designed to proved the count of all possible trees. This can be a reference. Or just compress the raw array data by compression algorithm like LZ4, which kernel already provides. Perfect hash functions may be considered if the count of possible game states is not too large.
