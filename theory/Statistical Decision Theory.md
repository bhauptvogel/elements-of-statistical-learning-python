# Statistical Decision Theory

# Quantitative Variables

- $X \in \mathbb{R}^p$ real valued random input vector
- $Y \in \mathbb{R}$ real valued random output variable

- $\mathrm{Pr}(X,Y)$ joint distribution probability

- $f(X)$ (seeked) function for predicting $Y$ given values of the input $X$

- $L(Y,f(X))$ ************loss function************ for penalizing errors in prediction:

- $\mathrm{EPE}(f)$ expected prediction error

- Example for with *squared error loss*: $L(Y, f(X))=(Y-f(X))^2$*
    
    $$
    \mathrm{EPE}(f)=\mathrm{E}(Y-f(X))^2\\=\int [y-f(x)]^2\mathrm{Pr}(dx,dy)
    $$
    
    → conditioning on $X$:
    
    $$
    \mathrm{EPE}(f)=\mathrm{E}_X\mathrm{E}_{Y|X}([Y-f(X)]^2|X)
    $$
    
    → it suffices to minimize $\mathrm{EPE}$ pointwise: 
    
    $$
    f(x)=\mathrm{argmin}_c\mathrm{E}_{Y|X}([Y-c]^2|X=x)
    $$
    
    Solution: 
    
    $$
    f(x)=\mathrm{E}(Y|X=x)
    $$
    
- Example for Nearest Neighbor
    
    $$
    \hat{f}(x)=\mathrm{Ave}(y_i|x_i\in N_k(x))
    $$
    
    → $\mathrm{Ave}$ denotes average
    
    → $N_k(x)$ neighborhood containing $k$ points in $\mathcal{T}$ closest to $x$
    
    > As $k$ gets larger the average will get more stable!
    > 

# Qualitative Variables

- $G$ categoriacal output variable

- $\mathbf{L}$ loss function represented by a $K\times K$ matrix (where $K=\mathrm{card}(G)$)
    - $L(k,l)$ is price paid for classifying an observation belonging to class $\mathcal{G}_k$ as $\mathcal{G}_l$
    - Most often *********zero-one********* loss functions used (misclassifications charged a single unit)
    
- Example for ********zero-one******** loss function
    
    $$
    \mathrm{EPE}(f)=\mathrm{E}[L(G,\hat{G}(X))]
    $$
    
    → conditioning on $X$:
    
    $$
    \mathrm{EPE}(f)=\mathrm{E}_X\sum\limits_{k=1}^{K}L[\mathcal{G}_k,\hat{G}(X)]\mathrm{Pr}(\mathcal{G}_k|X)
    $$
    
    → it suffices to minimize $\mathrm{EPE}$ pointwise: 
    
    $$
    \hat{G}(x)=\mathrm{argmin}_{g\in\mathcal{G}}\sum\limits_{k=1}^{K}L(\mathcal{G}_k,g)\mathrm{Pr}(\mathcal{G}_k|X=x)
    $$
    
    → simplify with 0-1 loss function: 
    
    $$
    \hat{G}(x)=\mathrm{argmin}_{g\in\mathcal{G}}[1-\mathrm{Pr}(g|X=x)]\\ \hat{G}(x) =\mathcal{G}_k \text{ if }\mathrm{Pr}(\mathcal{G}_k|X=x)=\max\limits_{g\in\mathcal{G}}\mathrm{Pr}(g|X=x)
    $$
    

## Bayes Classifier

> Optimal decision boundary
> 
- error rate is called **********bayes rate**********
- $k$-nearest neighbor directly approximates bayes classifier