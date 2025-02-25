
# Ecommerce Product Recommendation System

## Overview
The **Ecommerce Product Recommendation System** is a machine learning-based solution designed to enhance the shopping experience by providing **personalized product recommendations** to users based on their browsing and purchase history. This system leverages **collaborative filtering** and **content-based filtering** techniques to analyze user interactions and generate relevant recommendations. The primary goal is to improve user engagement, increase sales, and optimize the overall e-commerce experience.

---

## Dataset
The system utilizes an **Amazon dataset** containing user ratings for electronic products. Since the dataset lacks headers, each **user** and **product** is assigned a unique identifier to prevent biases.

🔗 **Dataset Link:** [Amazon Electronics Rating Dataset](https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation/download?datasetVersionNumber=1)

🔗 **Additional Datasets:** [Amazon Product Data](https://jmcauley.ucsd.edu/data/amazon/)

---

## Approach
The recommendation system is built using three key methodologies:

### **1) Rank-Based Product Recommendation**
#### **Objective:**
- Recommend products with the highest number of ratings.
- Target new customers by suggesting the most popular products.
- Address the **Cold Start Problem** ([Learn More](https://github.com/jpb2022/jpb2022-Ecommerce-product-recommendation-system/blob/main/Ecommerce-product-recommendation-system-main/%20Cold%20Start%20Problem%20in%20Recommender%20Systems%20%20.md)).

#### **Implementation Steps:**
1. Calculate the **average rating** for each product.
2. Compute the **total number of ratings** for each product.
3. Create a **DataFrame** and sort products based on their average rating.
4. Define a function to fetch the **top 'n' products** with a specified minimum number of interactions.

#### **Output:**
- List of **top 5 products** with a minimum of **50 or 100 ratings**.

---

### **2) Similarity-Based Collaborative Filtering**
#### **Objective:**
- Provide **personalized recommendations** by identifying similar users.

#### **Implementation Steps:**
1. Convert `user_id` values into an **integer index** for efficient computation.
2. **Find similar users**:
   - Compute **cosine similarity** scores between users.
   - Sort users based on similarity scores.
   - Exclude the original user and return the most similar users.
3. **Recommend products**:
   - Identify products interacted with by similar users.
   - Exclude products already interacted with by the target user.
   - Recommend the top 'n' products based on similar users' interactions.

#### **Output:**
- List of **top 5 recommended products** based on interactions of similar users.

---

### **3) Model-Based Collaborative Filtering**
#### **Objective:**
- Provide **personalized recommendations** based on user behavior while addressing **sparsity and scalability** challenges.

#### **Implementation Steps:**
1. Convert the **user-product interaction matrix** into a **Compressed Sparse Row (CSR) matrix** for memory efficiency.
2. Apply **Singular Value Decomposition (SVD)** to extract latent features and reduce dimensionality.
3. Compute **predicted ratings** using the decomposed matrices (U, Σ, Vt).
4. Store the **predicted ratings** in a DataFrame.
5. Define a function to generate product recommendations:
   - Extract **user's actual ratings**.
   - Retrieve **predicted ratings** from the model.
   - Filter out products already rated by the user.
   - Recommend the **top 'n' products** based on highest predicted ratings.

#### **Evaluation Metrics:**
- Calculate the **Root Mean Squared Error (RMSE)** to measure prediction accuracy.
- RMSE is computed as:
- RMSE = sqrt( (1/N) * Σ (y_actual - y_predicted)² )

where:

- N is the total number of observations,
- y_actual represents the actual values,
- y_predicted represents the predicted values,
- denotes summation over all observations,
- sqrt represents the square root function.

  > The `mean_squared_error` function is used with `squared=False` to compute RMSE instead of MSE.

#### **Output:**
- List of **top 5 product recommendations** for a specific user.
- **RMSE score** to evaluate model performance.

---

## Conclusion
The **Ecommerce Product Recommendation System** successfully enhances the online shopping experience by implementing **rank-based, similarity-based, and model-based collaborative filtering techniques**. These approaches help tackle challenges such as **cold start problems, sparsity, and scalability**, ultimately driving user engagement and increasing sales for e-commerce businesses.

🚀 **Next Steps:**
- Integrate **real-time recommendation updates**.
- Experiment with **deep learning models (e.g., Autoencoders, Neural Collaborative Filtering)**.
- Optimize **hybrid models** combining content-based and collaborative filtering techniques.

📌 **Stay tuned for further improvements and optimizations!**

