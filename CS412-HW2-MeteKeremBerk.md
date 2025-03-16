---
header-includes:
  - \usepackage{graphicx}
---

# CS412 - Machine Learning: Homework 2

**Notebook Link:** [Google Colab Notebook](https://colab.research.google.com/drive/1z6nvCxZrjGWHxwvHDtL61cI2t_oLFcah?usp=sharing)

## Title: Linear and Polynomial Regression Analysis

**Name:** Mete Kerem Berk  
**Student ID:** 30933  
**Course:** CS412 - Machine Learning  
**Homework Number:** HW2  
**Submission Date:** March 16, 2025

\pagebreak

## 1. Generate Data for Regression

- Created a dataset of (x, y) pairs where y is generated from a linear function with added Gaussian noise.
- Saved the dataset for further use in regression tasks.

## 2. 50% Train 50% Validation Split

- The dataset was split into 50% training and 50% validation sets to evaluate model performance effectively.

## 3. Make a Scatter Plot of the Data

**Scatter Plot of Dataset 1:**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/dataset1_scatter.png}
\caption{Scatter Plot of Dataset 1}
\label{fig:scatter1}
\end{figure}

**Scatter Plot of Dataset 2:**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/dataset2_scatter.png}
\caption{Scatter Plot of Dataset 2}
\label{fig:scatter2}
\end{figure}

## 4. Function for Plotting the MSE Loss

- Implemented a function to visualize the loss curve during training for gradient descent.

## 5. Part 1: Linear Regression on Dataset 1

### Part 1.a - Scikit-Learn’s Linear Regression

- Utilized `LinearRegression` from `sklearn.linear_model`.
- Trained the model on Dataset 1 and evaluated predictions on the validation set.

**Regression Line Fit (Scikit-Learn):**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/linear_sklearn.png}
\caption{Regression Line Fit (Scikit-Learn)}
\label{fig:linear_sklearn}
\end{figure}

### Part 1.b - Ordinary Least Squares (OLS)

- Implemented OLS manually using matrix computations.
- Computed coefficients and used them for prediction.

**Regression Line Fit (OLS):**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/linear_ols.png}
\caption{Regression Line Fit (OLS)}
\label{fig:linear_ols}
\end{figure}

### Part 1.c - Gradient Descent

- Implemented gradient descent to iteratively optimize weights.
- Used a learning rate of 0.1 and 1000 iterations.
- Converged to optimal parameters and evaluated performance.

**Regression Line Fit (Gradient Descent):**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/linear_gd.png}
\caption{Regression Line Fit (Gradient Descent)}
\label{fig:linear_gd}
\end{figure}

**Loss Curve for Gradient Descent:**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/gd_loss.png}
\caption{Loss Curve for Gradient Descent}
\label{fig:gd_loss}
\end{figure}

## 6. Part 2: Polynomial Regression on Dataset 2

### Part 2 - Data Generation

- Loaded Dataset 2 from `.npy` files.
- Splitted the dataset into training and validation sets.

### Part 2.a - Polynomial Regression using Scikit-Learn

- Applied `PolynomialFeatures` from `sklearn.preprocessing` to generate polynomial features of degrees 1, 3, 5, and 7.
- Fitted linear regression models to the transformed data and computed validation MSE.
- Found the best degree for the given data as 5.

**Polynomial Regression Fit (Degree 5):**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/poly_deg5.png}
\caption{Polynomial Regression Fit (Degree 5)}
\label{fig:poly_deg5}
\end{figure}

### Part 2.b - Manual Polynomial Regression

- Implemented polynomial regression manually for degree 3.
- Constructed the polynomial feature matrix and applied the OLS method.

**Manual Polynomial Regression Fit (Degree 3):**

\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{images/poly_manual_deg3.png}
\caption{Manual Polynomial Regression Fit (Degree 3)}
\label{fig:poly_manual_deg3}
\end{figure}

## 7. Results & Discussion

### Part 1: Comparison of Gradient Descent with Other Methods

- The gradient descent solution is very close to the solutions obtained using Scikit-Learn’s Linear Regression and the manually implemented Ordinary Least Squares (OLS) method.
- Any small discrepancies can be attributed to:
  - The number of iterations chosen for gradient descent.
  - The learning rate, which affects how quickly the model converges.
  - Possible stopping conditions that might have been met before full convergence.
- If the gradient descent solution differs significantly, it may indicate insufficient iterations or a learning rate that is too high or too low.

### Part 2: Effect of the Degree Parameter in Polynomial Regression

- When the polynomial degree is too small (e.g., degree 1), the model underfits the data and fails to capture the nonlinear relationships.
- When the polynomial degree is too large (e.g., degree 7), the model overfits, capturing noise as if it were part of the underlying pattern.
- The optimal polynomial degree balances bias and variance. Based on the MSE values, degree 5 appears to provide the best trade-off, achieving a low validation error while avoiding excessive overfitting.

### Performance Comparison (MSE Analysis)

| Method                         | MSE                 |
| ------------------------------ | ------------------- |
| Scikit-Learn Linear Regression | 0.00795462682779033 |
| Manual OLS                     | 0.00795462682779037 |
| Gradient Descent               | 0.00527514849082713 |
| Polynomial (Degree 1)          | 0.06362852709262727 |
| Polynomial (Degree 3)          | 0.01205922374286829 |
| Polynomial (Degree 5)          | 0.00747546307928118 |
| Polynomial (Degree 7)          | 0.01154922783882886 |

---

## 8. Conclusion

This homework provided hands-on experience in implementing and analyzing regression methods. Key takeaways:

- Linear regression methods performed well on dataset 1.
- Polynomial regression effectively captured nonlinearity in dataset 2, but higher degrees led to overfitting.
- Gradient descent, while powerful, required careful tuning.

Overall, this assignment reinforced the importance of selecting appropriate models based on data characteristics and balancing bias-variance tradeoffs.
