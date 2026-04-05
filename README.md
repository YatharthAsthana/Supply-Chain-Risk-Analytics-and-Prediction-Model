# Supply-Chain-Risk-Analytics-and-Prediction-Model
The global supply chain industry is a high-stakes, low-margin environment where a 24-hour delay in a Tier-2 supplier can halt a Tier-1 production line thousands of miles away. During my research, I became fascinated by the "Butterfly Effect" in logistics: how minor fluctuations in energy consumption or a subtle shift in a supplier’s "Parameter Change Magnitude" could be a leading indicator of a systemic collapse.
Traditional supply chain management is often reactive—fixing a break after it occurs. My motivation was to shift this paradigm toward Proactive Resilience. I wanted to understand the "intricacies" of the industry—such as the difference between a "Standard Delay" and an "Anomalous Lag"—and build a mathematical engine capable of distinguishing the two. This project allowed me to bridge the gap between raw data science and the operational realities of diverse industries like Pharma, Electronics, and Textiles.

**Data Engineering & The Velocity of Risk**
A critical realization in this project was that static reliability scores are deceptive. A supplier with 90% reliability who suddenly drops to 80% is statistically more dangerous than one consistently at 80%. To capture this "velocity," I moved beyond raw features to engineered intelligence:
**Lead-Time Volatility:** I calculated the deviation of lead times relative to the Product Category average. This isolated true disruptions from standard industry-specific wait times.
**Supplier Risk Ratio:** This weighted historical disruptions against total operational volume ($Total\_Disruptions / Total\_Records$), providing a "Density of Failure" metric.
**Cost-Time Interaction:** I created a feature that prioritized the financial exposure of delayed high-value shipments.Peer-Group Normalization: I engineered the Shipping Lag Score, which identifies how "weird" a specific shipment is compared to others using the same Shipping Mode.

**Methodological Evolution: The Architecture of Accuracy**
I navigated a rigorous "Model Maturity Curve" to ensure the results were not just high, but statistically honest.

**Phase 1: Addressing Data Leakage**
Early EDA revealed 100% accuracy due to "Lagging Indicators" (features recorded after a disruption). I proactively purged these to ensure the model utilized only Leading Indicators available at the moment of order placement.

**Phase 2: Hybrid Resampling (SMOTE-ENN)**
Supply chain data is inherently imbalanced (disruptions are rare). I implemented SMOTE-ENN—a hybrid technique that generates synthetic "Risk" samples while simultaneously using Tomek Links to delete "ambiguous" data points that blur the decision boundary.

**Phase 3: The "Symmetric Tree" Engine (CatBoost)**
I transitioned to CatBoost, an advanced Gradient Boosting library designed for tabular data.
**James-Stein Encoding:** Used "shrinkage" math to encode categorical variables, preventing the model from over-fitting to small categories.
**Symmetric Trees:** Unlike standard boosters, CatBoost builds balanced trees that are natively resistant to the "Prediction Shift" caused by sudden changes in supplier behavior.

I was able to achieve a decent accuracy of 90.8% and an F1-score of 0.9. Overall, it was an insightful learning experience.
