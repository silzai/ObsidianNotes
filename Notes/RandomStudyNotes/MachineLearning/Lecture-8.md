# Neural Networks
- will use `pytorch` (not tensorflow because has the playground.tensorflow website)
- forward pass produces output
- backward propagation reduces error by adjusting the weights
- Developers role is find the following hyper-parameters:
	- number of layers, 
	- number of neurons per layer
# neuron:
- The following happens inside a neuron:
	- do linear combination (dot product) of incoming weights and biases
	- and then passing it through an activation function (such as sigmoid):
		- we do this to convert the linear combination to non-linear (doing non-linear transformation)
# To build NN using pytorch:
- Pick the structure
- pick the loss function
- pick the gradient function