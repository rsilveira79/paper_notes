# Lottery Trick - Paper Review

## **[Initial Paper]** The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks

**Approach**:  

1. Train the network
2. Set all weights **_w_** smaller then some threshold to zero (prune)  
3. Rewind all rest of weights to their initial configuration  
4. Retrain the network keeping pruned weights frozen (not trainable)  



##**[Uber Paper]** Deconstructing Lottery Tickets: Zeros, Signs, and the Supermask

Three key points:

1. Setting Zero weights  
2. Keep sign to re-initialize network train
3. Masking behave like training

- Supermask $$ \rightarrow $$ mask that are trainable, when applied to randomly initialized model can have far better performance than chance

- Neural nets are overparameterized, enabling compression of each layer $$ \rightarrow $$ 
- LT Paper $$ \rightarrow $$ sparse sub-networks are trainable. Steps:
	1. 	Set all weights smaller than some threshold _t_ to 0
	2. Prune these weights
	3. Re-wind the rest of the weights to the initial configuration
	4. Retrain the network from start but w/ zero weights frozen (not trained)

Questions:

- Why masks and initial set of weights are tighly coupled?
- Why selecting large weights is effective for choosing a mask? What other criterias are effective

$$ w_{i} \rightarrow $$ initial weights before training  
$$ w_{f} \rightarrow $$ final weights after training

**Weights w/ mask value 1** $$\rightarrow $$ reset to initial values and mark for training in the next round

**Weights w/ mask value 0** $$\rightarrow $$ weights were pruned: set to 0 and frozen during training

Variables in training:

#### Mask Criteria: 

Functions that decide which weight to keep vs prune:

_large final_ = $$ M(w_{i},w_{f}) = |w_{f}|$$  
_small final_ = $$ M(w_{i},w_{f}) = -|w_{f}|$$  
_large init_ = $$ M(w_{i},w_{f}) = |w_{i}|$$  
_small init_ = $$ M(w_{i},w_{f}) = -|w_{i}|$$  
_large init, large final_ = $$ M(w_{i},w_{f}) = min(\alpha |w_{f}|, |w_{i}|)$$  
_small init, small final_ = $$ M(w_{i},w_{f}) = -max(\alpha |w_{f}|, |w_{i}|)$$  
_magnitude increase_ = $$ M(w_{i},w_{f}) = |w_{f}|-|w_{i}|$$  
_movement_ = $$ M(w_{i},w_{f}) = |w_{f}-w_{i}|$$  
_random_ = $$ M(w_{i},w_{f}) = 0$$  

#### Mask-1 Action  

_reinit_ = reinitialize kept weights based on the original initialization distribution
_reshuffle_ = same as above but reshufle kept weights init values
_constant_ = every weight on a layer becomes one of three values: -$$\alpha$$, 0, or $$\alpha$$

ORIGINAL LT Network ("rewind, large final")
Finding $$\rightarrow $$ as long as you keep the sign, reinitialization is not a deal breaker (even set to constant works well)

#### Mask-0 Action  

Finding $$\rightarrow $$ setting the value to zero actually matters
Usually on pruning $$\rightarrow $$ set weights to zero and freeze them in subsequent training

#### Supermasks

- Mask is training $$\rightarrow $$ _the masking operation tends to move weights in the direction they would have moved udring training_
- Masks using _large final_ criteria (nearly 40% at classifying digits on MNIST(

**Best Supermask**- _large final, same sign_
$$ M(w_{i},w_{f}) = max(0,\frac{w_{i}.w_{f}}{|w_{i}|}) $$ 

Supermaks and compression $$\rightarrow $$ only saves a binary mask and a random seed to reconstruct initial weights

--
### Sources
1. [The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks](https://arxiv.org/abs/1803.03635)
2. [Deconstructing Lottery Tickets: Zeros, Signs, and the Supermask](https://arxiv.org/abs/1905.01067)