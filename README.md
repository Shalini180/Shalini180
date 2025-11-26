# Hi, I'm Shalini 👋

### Backend Engineer · Systems & ML
I am a Backend Engineer in fintech building high-reliability infrastructure.

My work has shifted from building **deterministic systems** (that assume perfect inputs) to **robust systems** (that survive noisy ones). I am motivated by infrastructure that fails quietly: schedulers that trust bad forecasts and developer tools that surface hallucinations without verification.

My goal for graduate study is to formalize how distributed systems can quantify risk to make better resource allocation decisions under uncertainty.

---

### 📄 Academic Research (Foundational)
**Learning-Based Adaptive Image Denoising**
<br>*Undergraduate Capstone Thesis | Vellore Institute of Technology*

* **The Problem:** Traditional denoising applies a single algorithm globally. I investigated whether local image complexity could serve as a proxy for “uncertainty” when dynamically selecting filters.
* **Methodology:**
    * Modeled image patches using a **6-factor complexity vector** (quantifying spatial variance and spectral density).
    * Trained a Random Forest classifier to map patch complexity to the optimal denoising kernel (BM3D vs. Bilateral vs. NLM).
* **Empirical Analysis:** The model approached an oracle-style baseline (93% agreement), with modest PSNR improvements (0.33–0.56 dB). *Crucially, the system's failure under non-stationary sensor noise highlighted the limitation of static complexity features, motivating my interest in adaptive systems that model distributional shift.*

---

### 🛠️ Systems Engineering Prototypes (Research-Inspired)
*Self-directed implementations exploring reliability under uncertainty.*

#### 1. [Carbon-Aware SQL Execution Engine](https://github.com/Shalini180/energy-ml-project)
* **Objective:** To build a job scheduler that handles uncertainty in grid carbon intensity forecasts.
* **Mechanism:** Calculated a **prediction interval** ($E \pm \sigma$) for carbon intensity. Implemented a lower-bound heuristic to defer jobs only when the future scenario was conservatively estimated to be cleaner.
* **Simulation Result:** In a **simulated replay** of ISO-NE grid traces (~200 synthetic jobs), the scheduler reduced estimated carbon footprint by **~15%** compared to a FIFO baseline.
* **Research Insight:** *This architecture revealed a key limitation: modeling uncertainty with symmetric bounds ($E \pm \sigma$) ignored tail risk. Additionally, the lack of real-world latency SLOs and regional grid bias in the simulation motivated my exploration of Bayesian scheduling formulations.*

#### 2. [Event-Driven Hybrid AI Code Reviewer](https://github.com/Shalini180/ai-code-reviewer)
* **Objective:** To mitigate the "precision vs. recall" trade-off in automated code review using a hybrid approach.
* **Mechanism:** Fused deterministic static analysis with semantic analysis. Static findings are injected into the LLM prompt as **structured context**, constraining the model to a verification task to reduce hallucination.
* **Engineering Trade-off:** *Latency was the primary bottleneck. I implemented a fail-open mechanism where the worker degrades to static-only mode if inference exceeds 500ms. A remaining limitation is the potential for false negatives, as the system relies on static analysis to trigger the LLM review.*

---

### 🔭 Current Research Questions
*I am actively thinking about:*
1.  How can schedulers be formally modeled to account for **asymmetric risk and tail events** without sacrificing throughput?
2.  How should probabilistic model outputs be integrated into **reliability-critical developer tools** without violating safety or latency constraints?

---

### 🏆 Engineering Validation (Selected Work Under Constraints)
*Applied engineering projects validating system design skills.*

**Blockchain-Based P2P Payment Settlement (CryptRidez)**
* **System Constraint:** Designed an idempotent smart contract layer to handle Ethereum transaction failures and reorgs without double-spending.
* **Verification:** [Devfolio](https://devfolio.co/projects/cryptridez-0f47) · [GitHub](https://github.com/Shalini180/IEEECS-HackHub-2022)

**IPL Score Prediction Pipeline**
* **System Constraint:** Built a low-latency inference pipeline to serve predictions during match intervals in a hackathon setting.
* **Verification:** [Official Article](https://chennai.vit.ac.in/vit-students-won-award-ibm-hack-challenge-2021/) · [GitHub](https://github.com/VaishnaviVV/IPL-Analytics-Prediction-IBMHC2021)

---

### 🎓 Academic Highlights
**B.Tech in Computer Science and Engineering**
<br>*Vellore Institute of Technology (VIT) | 2019 – 2023*

* **CGPA:** **9.19 / 10.0** (161 Credits)
* **Capstone:** CSE1904 Capstone Project (Grade: **A**)

**Relevant Coursework:**
* **Systems:** Parallel & Distributed Computing (**A**), Operating Systems (**A**).
* **Data & Math:** Machine Learning (**S**), Large Scale Data Processing (**S**), Applied Linear Algebra (**S**), Statistics for Engineers (**A**).
*(Note: 'S' denotes Superior grade, the highest possible rating).*

---

### 💻 Concepts & Skills
* **Systems Concepts:** Forecast-Aware Scheduling (Prototype-level), Backpressure-Aware Queueing, Event-Driven Architecture.
* **Languages:** Python (Primary), C++ (Academic usage).
* **Infrastructure:** Containerized Services, In-Memory Data Stores (Redis), Asynchronous Job Queues (Celery).
* **Tooling:** Intel RAPL, Linux Powercap.

---
*Connect with me on [LinkedIn](https://www.linkedin.com/in/shalini-annadurai/)*
