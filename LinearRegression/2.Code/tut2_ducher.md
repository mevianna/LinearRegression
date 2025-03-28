## Linear Regression on the Boston Housing Dataset (Scikit-Learn)

The **Boston Housing** dataset was widely used for regression learning. However, it has been discontinued in Scikit-Learn due to ethical concerns, so we will use **California Housing** as an alternative.

---

### **1. Import Libraries**
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.datasets import fetch_california_housing  # Alternative to Boston Housing
def sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
```

---

### **2. Load the Dataset**
```python
# Load dataset
data = fetch_california_housing()
X = pd.DataFrame(data.data, columns=data.feature_names)
y = data.target  # House price (in hundreds of thousands of dollars)

# Display first rows
display(X.head())
print(y[:5])
```

---

### **3. Split Data into Training and Testing Sets**
```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

---

### **4. Create and Train the Linear Regression Model**
```python
# Create linear regression model
model = LinearRegression()

# Train the model
model.fit(X_train, y_train)
```

---

### **5. Make Predictions**
```python
y_pred = model.predict(X_test)
```

---

### **6. Evaluate the Model**
```python
mae = mean_absolute_error(y_test, y_pred)
mse = mean_squared_error(y_test, y_pred)
rmse = np.sqrt(mse)
r2 = r2_score(y_test, y_pred)

print(f'MAE: {mae:.2f}')
print(f'MSE: {mse:.2f}')
print(f'RMSE: {rmse:.2f}')
print(f'R²: {r2:.2f}')
```

---

### **7. Visualize the Results**
```python
plt.scatter(y_test, y_pred, alpha=0.5)
plt.xlabel("Actual Values")
plt.ylabel("Predicted Values")
plt.title("Linear Regression: Actual vs Predicted Values")
plt.show()
```

---

### **Explanation**
- **MAE (Mean Absolute Error):** Measures the average absolute error between actual and predicted values.
- **MSE (Mean Squared Error):** Penalizes larger errors due to squaring.
- **RMSE (Root Mean Squared Error):** Similar interpretation to MAE but more sensitive to outliers.
- **R² (Coefficient of Determination):** Measures the proportion of variance explained by the model (closer to 1 is better).
