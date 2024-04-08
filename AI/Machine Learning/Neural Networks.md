
## Neural Network
##### Tools Used
1. [Python](/python/python)
2. [Numpy](/python/numpy.md)
### Contents
1. [Simple Examples](#simple%20examples)
	- [Dot Product](#dot%20product)

#### Simple examples
##### Example 1
*Simple code containing only one neuron*

```python
inputs = [1,2,3]
weights = [2,4,5]
bias = 2
output = inputs[0]*weights[0] + inputs[1]*weights[1]+inputs[2]*weights[2] +bias
# Todo: Findout why bias is adding insted of multiplying
print(output)
```

$$Y =( \sum_{k=1}^n inputs[k]  \  * \ weights[k]  \ )+ bias$$

##### Example 2
2. *Simple code containing 3 neuron*
```python
inputs = [ 1, 2, 3]
weights_1 = [ 2, 4, 5]
weights_2 = [ 3, 4, 5]
weights_3 = [ .1, .2, .3]

bias_1 = 2
bias_2 = -1
bias_3 = -2

output = [
		inputs[0]*weights_1[0] + inputs[1]*weights_1[1]+inputs[2]*weights_1[2] +bias_1,
		inputs[0]*weights_2[0] + inputs[1]*weights_2[1]+inputs[2]*weights_2[2] +bias_2,
		inputs[0]*weights_3[0] + inputs[1]*weights_3[1]+inputs[2]*weights_3[2] +bias_3
]
print(output)


```

$$Y[i] =( \sum_{k=1}^K inputs[i][k]  \  * \ weights[i][k]  \ )+ bias)$$
$$ Where \ Y = 1:\infty$$


![[Neural Network With 3 Weights.canvas|Neural Network With 3 Weights]]


##### Simplified Example 2

```python
inputs = [1, 2, 3]
weights = [[2, 4, 5], [3, 4, 5], [0.1, 0.2, 0.3]]
biases = [2, -1, -2]

output = []

for neuron_weights, neuron_bias in zip(weights, biases):
    neuron_output = 0
    for n_input, weight in zip(inputs, neuron_weights):
        neuron_output = n_input * weight
    neuron_output += neuron_bias
    output.append(neuron_output)


print(output)
```
###### Explanation
- [zip](/python/python#zip)
```python
output= []

for neuron_weights, neuron_bias in zip(weights, biases):
    neuron_output = 0
    for n_input, weight in zip(inputs, neuron_weights):
        neuron_output = n_input * weight
    neuron_output += neuron_bias
    output.append(neuron_output)

print(output)

```


> [!Note] Note
> - `for neuron_weights, neuron_bias in zip(weights, biases):` Used to loop through weights and biases and implementing 
$$Y =( \sum_{k=1}^n inputs[k]  \  * \ weights[k]  \ )+ bias$$
> - `neuron_output = 0` used to store he result tuple
> - `neuron_output = n_input * weight` multiplies the input with corresponding weight 
> - after looping through first tuples `neuron_output += neuron_bias` adds to get the final result of 1 neuron


```python
inputs = [1, 2, 3]
weights = [2, 4, 5]
bias = 2
output = 0
for neuron_weights , neuron_inputs in zip(weights,inputs):
    output = neuron_weights * neuron_inputs 
output = output + bias
print(output)
```
- This process is repeated to get the output corresponds to each weight and biases 


---
##### Dot Product

```python
import numpy as np
inputs = [1,2,3,2.5]
weights = [0.2,0.8,-0.5,1.0]
bias = 2
print(np.dot(inputs,weights) + bias)
print(np.dot(weights,inputs) + bias)

```
*position of the inputs,weight does not matter it gives the same result*


> [!NOTE] Dot Product
> 
 $$ \overrightarrow a.\overrightarrow b = (a_1 \hat i + a_2 \hat j + a_3 \hat k)(b_1 \hat i + b_2 \hat j + b_3 \hat k)$$
> $$Where
> \begin{aligned}
> \ \ \ \overrightarrow a &= a_1\hat i + a_2 \hat j + a_3 \hat k \\
> \overrightarrow b &= b_1 \hat i + b_2 \hat j + b_3\hat k
> \end{aligned}
> $$ 
> Dot product of 2 vector produces `scalar single value`




```python
import numpy as np
inputs = [1,2,3,4]
weights = [[1,2,1,3],
		   [1,2,3,4],
		   [1,2,3,5]]
biases = [2,2,3]
print(np.dot(inputs,weights[1]) + biases[1])

print(np.dot(weights[1],inputs) + biases[2])
# weight should be the first arguiment to np.dot()
print(np.dot(weights,inputs) + biases[2])
```

> [!INFO] np.dot() order
> - The `weight` should be the first arguments to the np.dot() otherwise it will throw an shape error
> - It is a dot product rule and `numpy` treats `inputs` as a column vector even if it is a row vector
$$
\begin{aligned}
\mathbf{A}_{m \times n} \cdot \mathbf{B}_{n \times p} &= \mathbf{C}_{m \times p} \\
& \mathbf{A}_{m \times n}\ \  is\  \ an\ \ (m \times n)\  matrix. \\
&\mathbf{B}_{n \times p}\ \ is\ \ an\ (n \times p) \  matrix. \\
 & \mathbf{C}_{m \times p}\ \ is\  \ the\  resulting \ (m \times p )\ \ \  matrix.
\end{aligned}
$$




##### Multiple Inputs

```python
import numpy as np
inputs_1 = [1,2,3,4]
inputs_2 = [1,3,45,5]
inputs_3 = [1.1,2.2,3,4]

weights_1 = [1,33,34,5]
weights_2 = [0.2,3,3,3]
weights_3 = [1.123,3.2,3,3]
biases = [1,2,3]

output = []

output[0] = np.dot(inputs_1,weights_1) + biases[0]
print(output)
```