# Week 1: Overview of LLMs

> **Goal:** Ramp up your understanding of LLMs, their learning methods, neural network basics, and scaling laws.

---

## 📋 Topics Covered

- **Neural Networks** — Parameters, Backpropagation, Loss, Activation Functions
- **Learning Paradigms** — Supervised, Self-supervised, Contrastive Learning, Reinforcement Learning
- **Scaling Laws in LLMs**
- **🧪 Coding Assignment:** MNIST digit classification

---

## 🗺️ Learning Path

### Step 1: Understand What Neural Networks Are

A neural network is a function approximator — it learns to map inputs to outputs by adjusting millions of parameters during training. Before diving into LLMs, you need to deeply understand how these building blocks work.

**Core concepts to master:**
- **Parameters (Weights & Biases):** The learnable values that the network adjusts during training
- **Forward Pass:** How input data flows through the network to produce output
- **Loss Functions:** How we measure "how wrong" the network is (MSE, Cross-Entropy)
- **Backpropagation:** The algorithm that computes gradients — how much each parameter contributed to the error
- **Gradient Descent:** Using gradients to update parameters in the direction that reduces loss
- **Activation Functions:** Non-linear functions (ReLU, Sigmoid, Tanh, GELU) that give networks the ability to learn complex patterns

| Resource | Type | Duration | Link |
|---|---|---|---|
| Neural Networks — 3Blue1Brown | 📹 Video Series | ~1h | [Watch](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) |
| Build Micrograd from Scratch — Andrej Karpathy | 📹 Video | 2.5h | [Watch](https://www.youtube.com/watch?v=VMj-3S1tku0) |
| Neural Networks — StatQuest (Full Series) | 📹 Video Series | ~3h | [Watch](https://www.youtube.com/playlist?list=PLblh5JKOoLUIxGDQs4LFFD--41Vzf-ME1) |
| Deep Learning Book — Ch 6: Deep Feedforward Networks | 📖 Free Book | ~2h read | [Read](https://www.deeplearningbook.org/contents/mlp.html) |
| Interactive Neural Network Playground | 🧪 Interactive | Self-paced | [Try](https://playground.tensorflow.org/) |

> **📄 Research Paper:** [Backpropagation Applied to Handwritten Zip Code Recognition — LeCun, 1989](http://yann.lecun.com/exdb/publis/pdf/lecun-89e.pdf) — The foundational paper on neural networks for digit recognition (directly relevant to your MNIST assignment).

---

### Step 2: Learning Paradigms

Understanding *how* models learn is as important as understanding *what* they learn. LLMs are primarily trained with self-supervised learning, but other paradigms play crucial roles.

**Supervised Learning:**
- Labeled data (input → correct output)
- Classic classification & regression
- Example: Image classification, spam detection

**Self-Supervised Learning:**
- The model creates its own labels from data (e.g., "predict the next word")
- This is how GPT models are pre-trained
- Example: Masked language modeling (BERT), next-token prediction (GPT)

**Contrastive Learning:**
- Learn by comparing similar vs. dissimilar examples
- Used in embedding models (CLIP, sentence-transformers)
- Example: "This image and text are related" vs "These are unrelated"

**Reinforcement Learning:**
- Learn by trial and error with rewards/penalties
- Used in RLHF (Reinforcement Learning from Human Feedback) for ChatGPT
- Example: Model generates response → human rates it → model improves

| Resource | Type | Duration | Link |
|---|---|---|---|
| Supervised vs Unsupervised vs Reinforcement — IBM | 📹 Video | 10min | [Watch](https://www.youtube.com/watch?v=1FZ0A1QCMWc) |
| Self-Supervised Learning — Yann LeCun (Meta) | 📹 Video | 1h | [Watch](https://www.youtube.com/watch?v=x4gdFMQIXBs) |
| Contrastive Learning Explained | 📹 Video | 20min | [Watch](https://www.youtube.com/watch?v=_1eKr4rbgRI) |
| Google ML Crash Course — ML Concepts | 📚 Course | ~3h | [Start](https://developers.google.com/machine-learning/crash-course) |
| Intro to Machine Learning — Kaggle | 📚 Micro-course | ~3h | [Start](https://www.kaggle.com/learn/intro-to-machine-learning) |

> **📄 Research Paper:** [A Simple Framework for Contrastive Learning (SimCLR) — Chen et al., 2020](https://arxiv.org/abs/2002.05709) — Foundational paper on contrastive learning.

---

### Step 3: Scaling Laws in LLMs

Scaling laws help us predict how model performance improves as we increase model size, dataset size, and compute. This is why GPT-4 is better than GPT-3 — and the science behind deciding whether to make a model bigger or train it longer.

**Key concepts:**
- **Chinchilla Scaling Laws:** For a given compute budget, there's an optimal balance between model size and training data
- **Power-law relationships:** Performance improves predictably as a function of parameters, data, and FLOPs
- **Emergence:** Some capabilities only appear in models above a certain size

| Resource | Type | Duration | Link |
|---|---|---|---|
| Scaling Laws for Neural Language Models — Kaplan et al. | 📄 Paper | ~1h read | [Read](https://arxiv.org/abs/2001.08361) |
| Chinchilla Paper Explained — Yannic Kilcher | 📹 Video | 30min | [Watch](https://www.youtube.com/watch?v=UbBPInGsBX4) |
| AI Scaling Laws — Leopold Aschenbrenner | 📖 Blog | ~30min | [Read](https://situational-awareness.ai/) |
| Emergent Abilities of Large Language Models | 📄 Paper | ~1h read | [Read](https://arxiv.org/abs/2206.07682) |

---

### Step 4: Essential Math Refresher

If your math foundations are rusty, work through these in parallel with the above topics:

| Resource | Type | Duration | Link |
|---|---|---|---|
| Essence of Linear Algebra — 3Blue1Brown | 📹 Video Series | ~3h | [Watch](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) |
| Essence of Calculus — 3Blue1Brown | 📹 Video Series | ~3h | [Watch](https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr) |
| Statistics & Probability — Khan Academy | 📚 Course | Self-paced | [Start](https://www.khanacademy.org/math/statistics-probability) |
| Mathematics for Machine Learning — Book | 📖 Free Book | Reference | [Read](https://mml-book.github.io/) |

---

## 🧪 Coding Assignment: MNIST

Build a neural network that classifies handwritten digits (0–9) from the MNIST dataset.

### Requirements:
1. Load the MNIST dataset
2. Build a simple feedforward neural network
3. Train it and achieve >95% accuracy
4. Visualize training loss and accuracy curves

### Resources:
| Resource | Link |
|---|---|
| PyTorch MNIST Tutorial (official) | [Tutorial](https://pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html) |
| MNIST from scratch with NumPy — Samson Zhang | [Watch](https://www.youtube.com/watch?v=w8yWXqWQYmU) |
| Kaggle MNIST Dataset | [Dataset](https://www.kaggle.com/datasets/hojjatk/mnist-dataset) |

### Stretch Goals:
- [ ] Implement a neural network from scratch using only NumPy (no PyTorch)
- [ ] Try different activation functions and compare results
- [ ] Add dropout and batch normalization
- [ ] Achieve >99% accuracy with a CNN

---

## 📚 Full Courses (For Deeper Dives)

These cover much more than Week 1, but you can start them now and continue through the program:

| Course | Provider | Link |
|---|---|---|
| Practical Deep Learning for Coders | fast.ai | [Start](https://course.fast.ai/) |
| Deep Learning Specialization (YouTube) | Andrew Ng | [Watch](https://www.youtube.com/playlist?list=PLkDaE6sCZn6Ec-XTbcX1uRg2_u4xOEky) |
| Stanford CS229 — Machine Learning | Stanford | [Watch](https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU) |
| Neural Networks: Zero to Hero | Andrej Karpathy | [Watch](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ) |

---

## ✅ Week 1 Checklist

- [ ] Watch 3Blue1Brown Neural Networks series
- [ ] Watch Karpathy's Micrograd video (code along!)
- [ ] Understand all 4 learning paradigms
- [ ] Read about scaling laws (at least the Chinchilla video)
- [ ] Complete the MNIST coding assignment
- [ ] Push your code to the `week-01/` folder

---

**➡️ Next: [Week 2: Tokenization, Vectorization & Attention](../week-02/README.md)**
