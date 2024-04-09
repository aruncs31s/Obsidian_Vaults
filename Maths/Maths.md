### Contents
- [Matrices](#Matrices)
	- [Multiplication](#matrix%20multiplication)

### Matrix
#### Matrix Product
The product AB between matrices 
$$
A \in R_m\times_l\  and B \in R_l \times _n
then \ C \in R_m \times _n
$$

$$
c_ij = \sum_{k=1}^l a_ik \ b_kj 
$$
#rules

> [!NOTE] Rows and Columns
> The this notation
>$$ R_m \times _l $$
> The `m` represents the rows and `l` represents the columns
> To perform **multiplication of two matrices**, we should make sure that the number of columns in the 1st matrix is equal to the rows in the 2nd matrix.





![](https://www.mathsisfun.com/algebra/images/matrix-multiply-a.svg)


```rust
use ndarray::arr2; 
fn main() { 
let a = arr2(&[[1, 2, 3], [4, 5, 6]]);
90let b = arr2(&[[6, 3], [5, 2], [4, 1]]); println!("{}", a.dot(&b)); }
```


#### Reduced row echelon form

[[Gauss–Jordan elimination]]

 
##### Matrix Multiplication

[Source](https://youtu.be/aAFP5wsmH2k?si=6OVmgu5MlKmEk48q)