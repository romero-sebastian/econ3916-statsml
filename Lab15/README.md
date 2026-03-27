This notebook investigates the bias-variance tradeoff through two datasets: synthetic sine-wave data (n=50 training, n=200 test) and the Ames Housing dataset (1,460 observations, 80 features). Using polynomial regression of increasing degree,
I demonstrate how training error monotonically decreases while test error forms a U-shape — the complexity curve —
revealing the sweet spot between underfitting and overfitting. Key findings: polynomial degrees 3–5 were optimal for the synthetic 
data; 5-fold cross-validation selected the same optimal degree as the true test error, confirming CV as a reliable model selection 
tool without requiring a held-out set; and on real housing data, a parsimonious 5-feature linear model outperformed a kitchen-sink model
using all numeric features in CV RMSE, despite lower training R², illustrating variance-driven overfitting in a realistic setting. 
Tools used: Python, NumPy, scikit-learn (PolynomialFeatures, LinearRegression, cross_val_score, make_pipeline), and Matplotlib.

