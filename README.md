# Mechanistic Interpretability: Vowel Detector

Tiny models can still hide surprisingly rich internal structure. This repo contains my submission for the AIPI 590 mechanistic interpretability assignment in which I trained and dissected a miniature MLP that decides whether a four-letter word contains a vowel.

---

## Project Snapshot
- **Task:** Predict if a 4-letter uppercase word includes a vowel (A, E, I, O, U)
- **Model:** 2-layer MLP (104 → 12 → 1) with ReLU + sigmoid
- **Data:** Fully synthetic, generated on-the-fly so no dataset download is needed
- **Runtime:** < 1 minute on CPU / seconds on GPU
- **Notebook:** `mechanistic_interpretability.ipynb` (runs in Colab or locally)

---

## Assignment Mapping
| Assignment Part | What’s in the Notebook |
| --- | --- |
| Part 1 – Setup | Data generator, model definition, and training loop for the vowel task |
| Part 2 – Explore | Activation statistics, letter selectivity probe, position tuning, and ablations |
| Part 3 – Explain | Narrative + plots describing the “vowel detector” neuron and supporting evidence |
| Part 4 – Reflect | Reflection on findings, surprises, and possible next experiments |

---

## Key Findings
1. **Neuron specialization:** One hidden neuron reliably spiked for vowels across positions, behaving as a position-invariant vowel detector.
2. **Redundancy:** Ablating individual neurons barely affected accuracy, indicating the model distributes the vowel feature across several units.
3. **Weight evidence:** Incoming weights for the key neuron concentrated on vowel columns at every position, mirroring the activation-based probes.

---

## Reproducing Results
### Option A: Google Colab (recommended)
1. Open the notebook directly in Colab: `mechanistic_interpretability.ipynb`.
2. Runtime → Run all. Everything (data creation, training, plots) happens in one pass.

### Option B: Local execution
1. Clone the repo:
   ```bash
   git clone https://github.com/lindsaygross/Mechanistic-Interpretability.git
   cd Mechanistic-Interpretability
   ```
2. Create a virtual environment and install dependencies (PyTorch, NumPy, Matplotlib):
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install torch numpy matplotlib
   ```
3. Launch Jupyter or VS Code and run `mechanistic_interpretability.ipynb` start-to-finish.

---

## File Guide
| File | Purpose |
| --- | --- |
| `mechanistic_interpretability.ipynb` | Full workflow: data generation, training, probing, plots, explanation, reflection |
| `mechanistic_interp_starter.ipynb` | Provided starter template from the course (left untouched for reference) |
| `README.md` | You are here—project overview and reproduction instructions |

---

## Reflection (TL;DR)
The project reinforced that even tiny networks form meaningful intermediates: a single neuron encoded “is there a vowel anywhere?” without caring about position. What surprised me was the resilience of the model when that neuron was ablated, hinting that redundancy emerges quickly. Next, I want to test variants where “Y” sometimes counts as a vowel or where the hidden layer is shrunk to see if interpretability becomes even clearer.

---

#### Used ChatGPT5 at 2:29 pm on Nov 6th 2025 to help format this README.md Script; updated with fresh details on Nov 7th 2025.
