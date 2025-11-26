# Hi, I'm Shalini 👋

### Backend Engineer · Distributed Systems & ML
I am a Backend Engineer building infrastructure for large-scale applications.

My research interests lie in **operationalizing uncertainty in distributed systems**. I build systems that accept stochastic signals—such as carbon forecasts, LLM token probabilities, and noisy sensor readings—and convert them into deterministic, reliable scheduling decisions.

Currently, I bridge the gap between **System Reliability** (determinism) and **Machine Learning** (probability) by designing schedulers and pipelines that treat risk as a first-class citizen.

---

### 🔬 Research Focus & Implementation

#### 1. [Carbon-Aware SQL Execution Engine](https://github.com/Shalini180/energy-ml-project)
* **Research Problem:** Standard schedulers optimize for latency/throughput but treat environmental cost as a constant, failing to account for forecast error in grid carbon intensity.
* **Uncertainty Mechanism:** Modeled **forecast variance** (aleatoric uncertainty) using time-dependent prediction intervals (expected value plus/minus one standard deviation). Implemented a conservative lower-bound selector to defer jobs only when the *worst-case* future carbon is strictly better than current conditions.
* **Systems Complexity:**
    * **Concurrency:** Handled queue saturation via Celery backpressure mechanisms.
    * **Profiling:** Implemented statistical energy profiling (N=5 runs) to distinguish signal from OS noise, falling back to TDP estimation when RAPL hardware counters are unavailable.
* **Evaluation:** Reduced carbon footprint by **~15%** compared to a greedy scheduler on a **24-hour replay of real grid traces and synthetic OLAP jobs**.

#### 2. [Distributed Hybrid AI Code Reviewer](https://github.com/Shalini180/ai-code-reviewer)
* **Research Problem:** Automated code review suffers from a precision/recall trade-off. Static tools have high recall but high noise; LLMs have high semantic understanding but hallucinate (epistemic uncertainty).
* **Uncertainty Mechanism:** Implemented a **Hybrid Fusion** engine. Static analysis results are injected into the LLM's context window as "ground truth" priors, forcing the model to act as a verifier rather than a generator.
* **Systems Complexity:**
    * **Architecture:** Event-driven, non-blocking pipeline using Redis for state management and deduplication of high-throughput GitHub webhooks.
    * **Fault Tolerance:** Designed graceful degradation paths—if the LLM API times out, the system falls back to static-only mode without crashing the worker.
* **Evaluation:** Benchmarked against raw Semgrep on **internal historical pull requests**, observing a **consistent reduction** in False Positive Rate (FPR) by filtering syntax-correct but logically irrelevant warnings.

#### 3. [Explainable Misinformation Detection](https://github.com/Shalini180/fake-news-detection)
* **Research Problem:** Black-box NLP models lack calibration and external context verification.
* **Uncertainty Mechanism:** Combined **Semantic Embeddings** (RoBERTa) with **Graph-based Credibility Scores** to weight predictions based on source history.
* **Evaluation:** Achieved **0.89 F1 Score** (vs. 0.75 Baseline LSTM). Improved model calibration on **out-of-distribution news articles** by heavily weighting domain credibility over text features.

---

### 🛠️ Technical Stack
* **Probabilistic Modeling:** Python, PyTorch (Transformer fine-tuning, statistical profiling), Scikit-learn.
* **Systems Infrastructure:** C++ (Performance-critical components), Redis (Distributed locking, Queues), Docker (Containerization).
* **Distributed Computing:** Celery (Async task orchestration), AWS (Cloud deployment), DuckDB (Embedded OLAP).
* **Hardware Interface:** Intel RAPL (Energy measurement), Linux Powercap.

---

### 🔭 Open Research Questions
*I am currently exploring how my work on uncertainty extends to broader systems:*
* **Risk-Aware Autoscaling:** Can we use the prediction intervals from my carbon scheduler to better predict request arrival bursts and prevent cold-start latency?
* **Consensus in Noisy Systems:** How do distributed consensus algorithms (like Raft) behave when leader election relies on probabilistic health checks rather than binary heartbeats?

---

### 📈 Industry Experience
* **Amazon (Fire TV):** Debugged nondeterministic race conditions in OS boot sequences. Designed state-preservation checkpoints to mitigate crash variance across Android/Vega OS transitions, measurably improving boot reliability in production.
* **Standard Chartered:** Engineered high-throughput financial pipelines. Optimized query paths in heterogeneous data systems to eliminate latency bottlenecks during peak trading load.

---
*Connect with me on [LinkedIn](https://www.linkedin.com/in/shalini-annadurai/)*
