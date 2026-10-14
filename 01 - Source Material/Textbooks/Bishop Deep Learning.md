
## Chapter 1


### Summary Notes:
- 

### Active Notes:
- Examples of deep learning (pgs. 1-6)
	- Medical diagnosis (e.g., skin lesions)
		- An example of supervised learning (given labels) and classification (each input is assigned a discrete set of classes)
		- When outputs consist of one or more continuous variables --> regression problem
		- Transfer learning --> takes a large model (trained on general images) and applies it to a specialized problem (skin images)
	- Protein structure
		- Take amino acids as input --> generate 3D structure as output
	- Image synthesis
		- Unsupervised  --> images are unlabeled 
		- Generative model --> generate new output examples that differ from those used to train the model
			- But share the same statistical properties
	- Large language models
		- LLM --> build rich internal representations to capture the semantics of language
		- Autoregressive LLM --> a form of gen. AI that can generate language as output
		- Loop: take sequence of words as input --> generate next word --> generate next word
- Basic example (pgs. 6 - 12)
	- Problem setup
		- Input variable $x$, target variable $t$
			- Both variables are continuous on the real axis
		- $N = 10$ data points evenly spaced out and generated with the function $\sin(2\pi x)$ 
		- Random noise (Gaussian) was then added to each point to generate the corresponding variable $t$
		- We wish to predict a value for $t_{n}$ given a $x_{n}$
	- The randomness is present in a lot of real-world datasets
	- To start with, the book considers a simple approach based on curve fitting, using the polynomial function of the form:
	$$
y(x, w) = w_{0}+w_{1}x+w_{2}x^2+\dots+w_{M}x^M = \sum_{j=0}^Mw_{j}x^j 
$$
	- While the polynomial function $y(x, w)$ is a nonlinear function of x, it is a linear function of the coefficients w
	- Determine coefficient values --> fit polynomial to training data --> minimize an error function that measures the misfit
	- Misfit measure --> sum of the squares of the differences between the predictions $y(x_{n}, w)$ for each data point $x_{n}$ and the corresponding target $t_{n}$ given by
	- 
$$
E(w) = \frac{1}{2}\sum_{n=1}^N(y(x_{n}, w)-t_{n})^2
$$
- cont.
	- Book tested different parameters on $M$
		- 0 and 1 order polynomials --> very poor fitting
		- 3 --> overall very good
		- 9 --> fits through all the points perfectly, but is an example of *overfitting*
		- Overfitting --> good training accuracy but actually fits to the function $\sin(2\pi x)$ poorly
	- In the worked example, the coefficients have become very finely tuned to the data --> exhibiting both large negative/positive values
	- Larger datasets can also help with reducing the overfitting problem (large data set, we can afford to fit a more complex model)
- Regularization and more (pgs. 12 - 13 )
	- Simple penalty term added to the coefficients to discourage large magnitudes
	- $$
E(w) = \frac{1}{2}\sum_{n=1}^N(y(x_{n}, w)-t_{n})^2 + \frac{\lambda}{2}
||w||^2$$
	- where the coefficient $\lambda$ governs the relative importance of the regularization term compared with the sum-of-squares error
		- E.g., with $\ln \lambda$ equal to -18, the 9-th degree polynomial fits well, but with $\ln\lambda$ equal to 0 the function becomes flat
- Model selection (pgs. 14-15)
	- The quantity $\lambda$ is an example of a *hyperparameter* since we can't just simply minimize w.r.t. w and $\lambda$ since the model will just become overfit
		- Degree of polynomial ($M$) is also a hyperparameter, since minimizing will just, again, result in 0 training error and an extremely overfit model
	- Simple solution --> use a training set and a separate validation set, then select the model with the lowest error on the validation set
		- Might overfit on validation --> test set may become necessary
	- **Cross-validation** --> simple way to make use of all available data
		- ![[Figure_11.pdf]]
		- Illustrated here, each partition is used for validation and then the performance scores from the $S$ runs are then averaged
- Brief history of Machine Learning (pgs. 16-18)
	- Neural networks --> based on the neurons in the brains of humans and other mammals
	- Basic idea behind artifical neural networks:
		1. Describe the properties of a single neuron by forming a linear combination of the outputs of other neurons
		2. Transform it using a nonlinear function
	- $$
\begin{gather}
a = \sum_{t=1}^Mw_{i}x_{i} \\
y = f(a) \\
\end{gather}
$$
		- where $x_{1}, \dots, x_{M}$ represent $M$ inputs corresponding to the activities of other neurons that send connections to this neuron
		- and $w_{1}, \dots , w_{M}$ are continuous variables called weights, which represent the strengths of the associated synapses
	- Terminology:
		- quantity $a$ --> called the pre-activation
		- non-linear function $f(.)$ --> activation function
		- output y --> activation 
	- Single-layer neural network --> perceptron 
- Backpropagation (pgs.19-20)
	- Problem --> training multi-layer neural networks
	- Solution --> application of gradient based optimization methods
	- New training process for feed-forward (or multi-layer) neural networks:
		1. Initialize all parameters using a random number generator
		2. Iteratively update them using gradient-based optimization techniques
		3. Compute derivatives of the error function, done in a process known as *error backpropagation 
	- While there exist many optimization algorithms, the most common is known as stochastic gradient descent
- Deep networks (pgs. 20-22)
	- Networks with many layers of weights --> called deep neural networks
	- Massive models (parameters in the trillions) --> necessitate large datasets for good parameters values =  lots of computation
		- Of course, solution is GPUs