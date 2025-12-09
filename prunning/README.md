# Model Compression — Threshold-Based Weight Pruning (Visual Analysis)

This repository provides a complete visual exploration of **threshold pruning** in neural networks.  
All plots inside `prunning/static/` show how pruning reshapes the **distribution of model weights** at different stages of training.

---

# 📁 Repository Structure

All images below are rendered directly from:

https://github.com/ajheshbasnet/model-compression/tree/main/prunning/static

---

# 1. Initialization Weight Distributions

## **1.1 Classification Head Initialization**
![Initialization CLS Head](./static/initialization-cls-head.png)

## **1.2 FFNN Initialization**
![Initialization FFNN](./static/initialization-ffnn.png)

These depict the raw weight histograms immediately after model construction.

---

# 2. Weight Distribution After Training (Before Pruning)

## **2.1 Classification Head — Before Pruning**
![Before Pruning CLS Head](./static/before-pruning-distribution-cls-head.png)

## **2.2 FFNN — Before Pruning**
![Before Pruning FFNN](./static/before-pruning-distribution-ffnn.png)

Shows how training reshapes magnitude distribution.

---

# 3. Threshold Applied Inside Training Loop

## **3.1 CLS Head — Pruning During Training**
![Threshold Inside Training Loop CLS](./static/threshold-inside-the-training-loop-cls.png)

## **3.2 FFNN — Pruning During Training**
![Threshold Inside Training Loop FFNN](./static/threshold-inside-the-training-loop-ffnn.png)

Visualizes the “live” pruning effect while gradients continue updating weights.

---

# 4. Post-Training Manual Pruning (τ = 0.4)

## **4.1 CLS Head — After Pruning (τ = 0.4)**
![At Prune 0.4 CLS Head](./static/at-prune-0.4-cls-head.png)

## **4.2 FFNN — After Pruning (τ = 0.4)**
![At Prune 0.4 FFNN](./static/at-prune-0.4-ffnn.png)

Shows how a fixed pruning threshold affects weight sparsity after full training.

---

# 5. Summary

The full pruning lifecycle illustrated:

1. **Initialization:**  
   Dense, symmetric distribution.

2. **After Training:**  
   Broader distribution with many near-zero values.

3. **During Training Pruning:**  
   Strong zero-spike due to repeated thresholding.

4. **Post-Training Pruning:**  
   Most low-magnitude weights eliminated → sparse model.

These visualizations reveal pruning behavior, layer sensitivity, and sparsity formation patterns.

---

# 6. Directory Link

All raw images are stored here:

https://github.com/ajheshbasnet/model-compression/tree/main/prunning/static
