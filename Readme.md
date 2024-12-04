Here’s the updated **README.md** with attribution to the Udemy course:

---

# **Boltzmann Machines for Recommendation Systems**

## **Overview**
This project implements a **Restricted Boltzmann Machine (RBM)** for movie recommendation. The RBM learns hidden patterns in user-movie interaction data, enabling it to predict unseen user preferences.

> **Note**: This implementation is based on the course materials from the [Udemy Deep Learning A-Z™ Course](https://www.udemy.com/course/deeplearning/learn/lecture/8376018#overview).

---

## **Dataset**
The project uses the **MovieLens Dataset**:
- **`movies.dat`**: Contains movie details.
- **`users.dat`**: Contains user information.
- **`ratings.dat`**: Contains user ratings for movies.
- **Training and Test Splits**:
  - **`u1.base`**: Training dataset.
  - **`u1.test`**: Test dataset.

---

## **Preprocessing**
1. **Data Conversion**:
   - The user-movie interactions are converted into a matrix where:
     - **Rows**: Users.
     - **Columns**: Movies.
     - **Values**: Ratings (`1` to `5`) or `0` (not rated).
   - Ratings are then converted into binary values:
     - **`1`**: Liked (ratings `3`, `4`, or `5`).
     - **`0`**: Disliked (ratings `1` or `2`).
     - **`-1`**: Not rated.

2. **PyTorch Tensor Conversion**:
   - The data is converted into PyTorch tensors for model processing.

---

## **RBM Architecture**
The RBM consists of:
- **Visible Layer**:
  - Represents the input data (movie ratings).
  - One node per movie.
- **Hidden Layer**:
  - Represents latent features, such as user preferences.
  - Configured with 100 hidden nodes in this implementation.
- **Weights and Biases**:
  - **Weights (`W`)**: Connect visible and hidden layers.
  - **Biases**:
    - `a`: Hidden layer biases.
    - `b`: Visible layer biases.

### **RBM Methods**
1. **`sample_h`**:
   - Computes hidden probabilities given visible nodes.
   - Samples binary activations for the hidden layer.

2. **`sample_v`**:
   - Computes visible probabilities given hidden nodes.
   - Samples binary activations for the visible layer.

3. **`train`**:
   - Updates weights and biases using Contrastive Divergence.

---

## **Training**
- **Parameters**:
  - Number of epochs: 10.
  - Batch size: 100.
  - Contrastive Divergence: 10 steps.
- **Procedure**:
  - For each epoch:
    - Perform forward pass (positive phase) to compute hidden probabilities.
    - Perform reconstruction (negative phase) with Contrastive Divergence.
    - Update weights and biases using the difference between the positive and negative phases.
- **Loss Function**:
  - Mean absolute error between the original and reconstructed visible nodes.

---

## **Testing**
- **Procedure**:
  - Predict ratings for each user in the test set using the trained RBM.
  - Compute mean absolute error between predicted and actual ratings for rated movies.
- **Output**:
  - Final test loss (mean absolute error across all users).

---

## **Key Results**
- The RBM learns to reconstruct user preferences based on movie ratings.
- Test loss provides a measure of how well the RBM predicts unseen data.

---

## **How to Run**
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo-name.git
   cd your-repo-name
   ```

2. Install dependencies:
   ```bash
   pip install numpy pandas torch
   ```

3. Place the dataset files (`movies.dat`, `users.dat`, `ratings.dat`, `u1.base`, `u1.test`) in the working directory.

4. Run the script:
   ```bash
   python Boltzmann_Machines.py
   ```

---

## **Directory Structure**
```
├── Boltzmann_Machines.py       # Main implementation
├── README.md                   # Project documentation
├── ml-1m/                      # Dataset directory
│   ├── movies.dat
│   ├── users.dat
│   ├── ratings.dat
├── ml-100k/                    # Dataset splits
│   ├── u1.base
│   ├── u1.test
```

---

## **Dependencies**
- Python 3.x
- PyTorch
- NumPy
- Pandas

---

## **Acknowledgment**
This project is based on the implementation from the [Udemy Deep Learning A-Z™ Course](https://www.udemy.com/course/deeplearning/learn/lecture/8376018#overview).

