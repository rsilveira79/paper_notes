## Lottery Trick - Paper Review

**[Initial Paper]** The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks

**Approach**:  

1. Train the network
2. Set all weights **_w_** smaller then some threshold to zero (prune)  
3. Rewind all rest of weights to their initial configuration  
4. Retrain the network keeping pruned weights frozen (not trainable)  



**[Uber Paper]** Deconstructing Lottery Tickets: Zeros, Signs, and the Supermask



### Sources
1. [The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks](https://arxiv.org/abs/1803.03635)
2. [Deconstructing Lottery Tickets: Zeros, Signs, and the Supermask](https://arxiv.org/abs/1905.01067)