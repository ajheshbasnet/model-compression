

Each image corresponds to a specific moment in the pruning lifecycle.

---

# 1. Motivation

Threshold pruning removes weights whose absolute value is below some value **τ**, producing a sparse model.  
Although the concept is simple, its real impact is best understood through **visualizing weight distributions**.

This repository answers:

- What do weights look like at initialization?  
- How does training reshape the distribution?  
- How does pruning change the distribution globally and per-layer?  
- What happens when pruning is done inside the training loop vs after training?

---

# 2. Visualizations Included

Each PNG file represents a histogram of layer weights at a specific stage.

---

## **2.1 Initialization Distributions**

Files:

- `initialization-cls-head.png`
- `initialization-ffnn.png`

These show the raw weight distributions directly after model initialization.  
Characteristics:

- Symmetric around zero  
- Typically Gaussian-like  
- No sparsity present  

Useful for confirming correct initialization behavior.

---

## **2.2 Before Pruning (After Full Training)**

Files:

- `before-pruning-distribution-cls-head.png`
- `before-pruning-distribution-ffnn.png`

These show weight magnitude **after training but before pruning**.

Observations:

- Many weights remain near zero → pruning candidates  
- A long-tail of large-magnitude weights emerges  
- The distribution widens relative to initialization  

This stage represents the baseline model prior to compression.

---

## **2.3 Threshold Applied Inside Training Loop**

Files:

- `threshold-inside-the-training-loop-cls.png`
- `threshold-inside-the-training-loop-ffnn.png`

Pruning is applied **during training**, not afterward.

Effects:

- Strong spike of weights exactly at zero  
- Training repeatedly tries to regrow some weights  
- Clear “push-and-pull” dynamics between gradient updates and pruning  

These images reveal how live pruning influences training stability.

---

## **2.4 Post-Training Manual Pruning (τ = 0.4)**

Files:

- `at-prune-0.4-cls-head.png`
- `at-prune-0.4-ffnn.png`

This is pruning applied **after** training using a fixed threshold of 0.4.

Characteristics:

- A large dead-zone around zero (sparsity)
- Only large-magnitude weights survive
- Distribution becomes truncated and often bimodal

This is the final compressed model.

---

# 3. What These Visuals Reveal

Across all phases, the transformation is:

1. **Initialization:**  
   Uniform, symmetric, dense distribution.

2. **After training:**  
   Distribution widens; low-magnitude cluster forms.

3. **Pruning during training:**  
   Zero-spike grows; distribution becomes asymmetric.

4. **Post-training pruning:**  
   Sharp cut-off at threshold; sparsity increases dramatically.

These transitions help diagnose:

- Under-pruning (threshold too small)  
- Over-pruning (threshold too large)  
- Layer-specific sensitivity  
- Training stability under live pruning  

---

# 4. Purpose of This Repository

The static images serve as a visual reference for:

- Understanding pruning behavior  
- Teaching model compression concepts  
- Debugging pruning strategies  
- Comparing pruning intensities  
- Presenting pruning effects in research or lectures  

---

# 5. Directory Link

All images are located here:

**https://github.com/ajheshbasnet/model-compression/tree/main/prunning/static**

---

# 6. License

This project is released for educational and research purposes.

