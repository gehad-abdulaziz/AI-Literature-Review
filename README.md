
# Autonomous AI Literature Review Studio 📚⚡

An end-to-end multi-agent research assistant built with **LangGraph**, **Groq**, **arXiv API**, and **Gradio**. This system automates deep academic literature discovery, comparative analysis, gap synthesis, and claim verification while maintaining human-in-the-loop (HITL) control.

---

## 🌟 Key Features

* **Dynamic Intent Routing:** An Orchestrator node intelligently routes requests between full research rounds and cross-round follow-up inquiries.
* **Parallel Fan-Out/Fan-In Execution:** Parallel single-paper analysis using LangGraph's `Send` API for accelerated multi-paper processing.
* **State Persistence & Memory:** Thread-level state persistence powered by `SqliteSaver` (SQLite Checkpointer) supporting state pause/resume capabilities.
* **Interactive Human-in-the-Loop (HITL):** Built-in native `interrupt` mechanisms for paper candidate selection and query clarification before execution.
* **Verification & Epistemic Safeguards:** Dedicated citation checking node to eliminate hallucinations and epistemic labeling to tag research gap support levels (`directly_supported`, `hypothesis`, etc.).
* **Prompt Injection Defense:** Strict isolation of paper abstracts as untrusted external data within system prompts.
* **Self-Correcting Search Loops:** Automatic fallback query expansion if candidate paper volume falls below defined relevance thresholds.
* **Real-time Streaming UI:** Custom Gradio execution visualizer displaying pipeline execution state and streamed outputs.

---

## 🛠️ Architecture & Workflow

```
<img width="687" height="1373" alt="output" src="https://github.com/user-attachments/assets/74b7be87-cb12-4527-987a-a9958d268762" />

```

---

## 💻 Tech Stack

* **Orchestration & Agents:** LangGraph, LangChain
* **LLM Engine:** Groq API
* **Data Sources:** arXiv API
* **State Persistence:** SQLite (`SqliteSaver`)
* **Frontend UI:** Gradio
* **Programming Language:** Python 3.10+

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.10 or higher installed.

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/your-username/literature-review-studio.git
cd literature-review-studio

```


2. **Create a virtual environment:**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

```


3. **Install dependencies:**
```bash
pip install -r requirements.txt

```


4. **Environment Configuration:**
Create a `.env` file in the root directory and add your API keys:
```env
GROQ_API_KEY=your_groq_api_key_here

```



---

## 🎛️ Usage

Run the Gradio cell :

Open your browser and navigate to `http://localhost:7860` to start interacting with the Literature Review Studio.

---

## 🛡️ Trust & Safety Safeguards

* **Untrusted Data Containment:** Paper text extracted from external APIs is wrapped in containment blocks to prevent indirect prompt injection attacks.
* **Certainty Hedging:** Automated filters prevent overconfident or definitive claim generation (e.g., flagging "definitely novel" phrases).
* **Citation Verification:** Every synthesized insight is cross-checked against source papers before presentation.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request or open an Issue for feature requests and bug reports.
