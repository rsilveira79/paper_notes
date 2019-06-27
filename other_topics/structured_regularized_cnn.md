## Structured Regularized CNN

### Paper 1 - CNN biased towards texture (ICLR2019)
- recent studies -> important role of texture
- ImageNet trained towards texture, not shape
- Shape hypothesis $$ \rightarrow $$ each layer acquires complex knowledge representation of previous layers
- Other findings pointing towards texture $$ \rightarrow $$ local texture provides sufficient information about object class
- Texture hypothesis $$ \rightarrow $$ object texture is more important than shape for object recognition
- Confound $$ \rightarrow $$ CNN do not cope well with domain shift
- ImageNet can be solved to high accuracy using only local information
- Finding $$ \rightarrow $$ shape-based representation may be more beneficial than a texture-based one


### Paper 2 - Measuring the tendency of CNNs to Learn Surface Statistical Regularities (Bengio)



### Paper 3 - Discovering Causal Signals in Images (Bottou)



### Sources
1. [ImageNet-trained CNNs are biased towards texture; increasing shape bias improves accuracy and robustness](https://arxiv.org/pdf/1811.12231.pdf)  
2. [Measuring the tendency of CNNs to Learn Surface Statistical Regularities](https://arxiv.org/abs/1711.11561)  
3. [Image Kernels](http://setosa.io/ev/image-kernels/)
4. [Texture vs Shape repo](https://github.com/rgeirhos/texture-vs-shape)  
5. [Stylized-ImageNet](https://github.com/rgeirhos/Stylized-ImageNet)  
6. [Discovering Causal Signals in Images](https://leon.bottou.org/publications/pdf/cvpr-2017.pdf)  