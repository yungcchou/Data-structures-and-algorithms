# Matrix

## **Definition of a Matrix**

- A matrix is a 2-dimensional array or a collection of elements arranged in rows and columns. It's commonly used to represent grids, tables, and many mathematical operations like linear transformations and graph representations.

## **Matrix Representation**

- Matrices can be represented as a list of lists (arrays of arrays) in programming languages such as Python. Each sub-list represents a row, and elements in that sub-list represent the values of the columns for that particular row.

## **Basic Matrix Operations**

- **Addition and Subtraction**: Matrices can be added or subtracted element-wise, provided the matrices have the same dimensions.
- **Multiplication**: Two matrices can be multiplied if the number of columns in the first matrix matches the number of rows in the second matrix.
- **Transpose**: Transposing a matrix involves swapping its rows and columns.

## **Sparse Matrix**

- A matrix with a large number of zero elements is called a sparse matrix. Special data structures like linked lists or dictionaries are used to store sparse matrices efficiently to save memory.

### Example

Let's take a 5x5 matrix as an example, where most of the elements are zeros:

#### Standard Matrix Representation

$$\begin{bmatrix}
0 & 0 & 3 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 \\
4 & 0 & 0 & 0 & 5 \\
0 & 7 & 0 & 0 & 0 \\
0 & 0 & 0 & 9 & 0 \\
\end{bmatrix}$$

#### Sparse Matrix Representation:
In a sparse matrix, only non-zero elements and their positions are stored to save memory.

There are different formats to store sparse matrices. One of the simplest is the **COO (Coordinate) format**, which stores the row index, column index, and value for each non-zero element.

#### Sparse Matrix in COO Format:
| Row | Column | Value |
|:-----:|:--------:|:-----:|
|  0  | 2      | 3     |
| 2   | 0      | 4     |
| 2   | 4      | 5     |
| 3   | 1      | 7     |
| 4   | 3      | 9     |

#### Explanation:
- Instead of storing all elements, we only store the non-zero elements with their respective row and column indices.
- This method is particularly memory-efficient when dealing with large matrices that have many zeros.

### Python Code Example (Sparse Matrix using `scipy`):

```python
import numpy as np
from scipy.sparse import coo_matrix

# Create a dense matrix (5x5 matrix)
dense_matrix = np.array([
    [0, 0, 3, 0, 0],
    [0, 0, 0, 0, 0],
    [4, 0, 0, 0, 5],
    [0, 7, 0, 0, 0],
    [0, 0, 0, 9, 0]
])

# Convert the dense matrix into a sparse matrix (COO format)
sparse_matrix = coo_matrix(dense_matrix)

# Print the sparse matrix data (row, column, and value)
print("Row Indices:", sparse_matrix.row)
print("Column Indices:", sparse_matrix.col)
print("Values:", sparse_matrix.data)
```

### Output:
```text
Row Indices: [0 2 2 3 4]
Column Indices: [2 0 4 1 3]
Values: [3 4 5 7 9]
```

This output shows the non-zero elements of the matrix, their row and column indices, and their values, just like the table in the sparse matrix representation.

## **Applications in Algorithms**

- **Graph Representation**: Matrices can be used to represent graphs through adjacency matrices, where the presence of an edge between two vertices is marked in the matrix.
- **Dynamic Programming**: Problems such as the shortest path, matrix chain multiplication, and others utilize matrices in their dynamic programming solutions.
- **Matrix Multiplication**: Strassen’s algorithm is a well-known divide-and-conquer approach for matrix multiplication that improves efficiency compared to the standard method.

## **Efficiency Considerations**

- Operations on large matrices can be computationally expensive. Optimizations such as blocking, Strassen's algorithm for multiplication, and using sparse matrix representations are important for improving performance.

## Matrix multiplication and dot product

Matrix multiplication and dot product are important operations in linear algebra and have distinct characteristics and uses. Let's look at each of them in detail:

### 1. **Matrix Multiplication**

Matrix multiplication is a way of combining two matrices to produce a third matrix. There are different types of matrix multiplication, but the most common form is **standard matrix multiplication**.

#### **Standard Matrix Multiplication (Dot Product for Matrices)**

- **Operation**: If you have two matrices, $A$and $B$, where $A$is of size $m \times n$ and $B$is of size $n \times p$, the result will be a matrix $C$of size $m \times p$.
- **Formula**: The element $C[i][j]$ in the resulting matrix is computed as the dot product of the $i$-th row of matrix $A$and the $j$-th column of matrix $B$.
  
$$C[i][j] = \sum_{k=1}^{n} A[i][k] \times B[k][j]$$

- **Conditions**: For standard matrix multiplication, the number of columns in the first matrix $A$must equal the number of rows in the second matrix $B$.

- **Complexity**: The time complexity of multiplying two $n \times n$matrices is $O(n^3)$, though this can be improved using more advanced algorithms (like Strassen’s Algorithm) to approximately $O(n^{2.81})$.

#### **Strassen’s Matrix Multiplication**

- **Strassen's algorithm** improves on the classical $O(n^3)$matrix multiplication by reducing the number of recursive multiplications needed.
- Instead of dividing matrices directly into submatrices and multiplying them, Strassen's method uses a more complex combination of the submatrices to reduce the number of multiplications.
- **Time complexity**: $O(n^{2.81})$, which is faster than the traditional method but still not optimal for all cases.

#### **Element-wise Multiplication (Hadamard Product)**

- **Operation**: In contrast to standard matrix multiplication, element-wise multiplication multiplies corresponding elements of two matrices.

$$C[i][j] = A[i][j] \times B[i][j]$$

- **Conditions**: Both matrices must have the same dimensions.
- **Complexity**: $O(n^2)$for two $n \times n$ matrices.

### 2. **Dot Product** (Specific to Vectors)

The dot product (also called scalar product) is a specialized form of matrix multiplication that applies to vectors. It results in a scalar value rather than a matrix or another vector.

#### **Dot Product Definition**

- **Operation**: Given two vectors $\mathbf{a}$and $\mathbf{b}$ of the same length, the dot product is computed as:
  
$$\mathbf{a} \cdot \mathbf{b} = \sum_{i=1}^{n} a_i \times b_i$$

  Where $a_i$and $b_i$ are the individual components of the vectors $\mathbf{a}$ and $\mathbf{b}$.
  
- **Result**: The result of a dot product is a scalar value.
- **Example**: If $\mathbf{a} = [1, 2, 3]$and $\mathbf{b} = [4, 5, 6]$, then the dot product is:
  
$$\mathbf{a} \cdot \mathbf{b} = (1 \times 4) + (2 \times 5) + (3 \times 6) = 32$$

- **Geometric Interpretation**: The dot product measures how much one vector extends in the direction of another. It is related to the cosine of the angle between two vectors, such that:
  
$$\mathbf{a} \cdot \mathbf{b} = |\mathbf{a}| |\mathbf{b}| \cos(\theta)$$
  where $\theta$ is the angle between $\mathbf{a}$ and $\mathbf{b}$.

### Key Differences Between Matrix Multiplication and Dot Product

| Feature                    | Matrix Multiplication                                | Dot Product (for Vectors)                 |
|----------------------------|------------------------------------------------------|-------------------------------------------|
| **Type of Output**          | Matrix                                               | Scalar (Single number)                    |
| **Dimensions**              | For matrices $A(m \times n)$ and $B(n \times p)$, results in $C(m \times p)$matrix | Applies to vectors of the same length     |
| **Conditions**              | Number of columns in the first matrix = Number of rows in the second matrix | Both vectors must have the same length    |
| **Complexity**              | $O(n^3)$ for $n \times n$ matrices (can be reduced with optimizations) | $O(n)$for vectors of length $n$ |
| **Use Case**                | Commonly used for transformations, solving systems of equations, graphics, etc. | Used to calculate projection, similarity  |

### Summary

- **Matrix Multiplication** refers to multiplying two matrices to produce another matrix, with applications in graphics, engineering, and algorithm design.
- **Dot Product** is a specific case of vector multiplication resulting in a scalar and is widely used in physics, machine learning, and statistics for measuring vector similarity.

Each of these operations is essential in various domains like computer graphics, machine learning, physics simulations, and algorithms.

[[ Python Demo ]](02_matrix.ipynb)
