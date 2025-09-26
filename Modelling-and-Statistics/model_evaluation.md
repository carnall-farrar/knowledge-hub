Yes, you're exactly right — **for a random classifier**, the **Area Under the Precision-Recall Curve (AUPRC)** is equal to the **prevalence of the positive class**, i.e., the **proportion of positive examples** in the dataset.

---

### So in your example:

* You're predicting **type 1 diabetes**, with a prevalence of **1 in 350**.

* That means the positive class proportion is:

  $$
  \text{Prevalence} = \frac{1}{350} \approx 0.002857
  $$

* Therefore, a **random model's expected AUPRC ≈ 0.002857**.

---

### Why is this the case?

* The Precision-Recall curve plots **precision vs. recall** as the decision threshold changes.
* For a **random classifier**, precision at any point is roughly the **prevalence of the positive class**, since it guesses blindly.
* Integrating over all recall levels results in an area (AUPRC) equal to the prevalence.

---

### Implication for your model evaluation

* An AUPRC significantly **above 0.002857** would indicate your model is doing **better than random**.
* This is especially useful in **highly imbalanced datasets** like yours, where metrics like AUC-ROC can be misleading.

Let me know if you'd like help computing or visualizing AUPRC for a specific model.
