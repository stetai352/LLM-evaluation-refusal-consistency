# LLM-evaluation-refusal-consistency
A small benchmark to test an open-source LLM on refusal consistency.

## Roadmap
<details>
	
<summary>Click here to expand roadmap</summary>
	
- [x] Set up Repository and Environment (2-4 h)
	- [x] Create repo with a `README`, `.gitignore`, `requirements.txt`.
	- [x] Set up standard folder structure: `data/`, `evals/`, `results/`, `analysis/`.
	- [x] Set up virtual environment locally
	- [x] Install `inspect-ai`, `ollama`
	- [x] Pull small model via `ollama pull llama3.2:3b`
	- [x] Consider these sources:
		- [`inspect-ai` documentation](https://inspect.aisi.org.uk/)
		- [Ollama guide](https://realpython.com/ollama/)
- [ ] Get familiar with `inspect-ai` (4-8 h)
	- [ ] Run one of the 100+ pre-built evaluations against local model.
	- [ ] Consider these sources:
		- [`inspect-ai` documentation](https://inspect.aisi.org.uk/)
		- Medium walkthrough by Lovkush Agarwal
- [ ] Define Research Question (3-6 h)
	- [ ] Define _refusal consistency_.
		- What behaviour am I testing? 
		- What am I measuring?
		- e. g. "If a model refuses a harmful request phrased directly, does it also refuse the same request phrased as a hypothetical, roleplay, translated into slightly softer language?"
		- Why does it matter for safety?
		- How to operationalise it?
		- Sketch out prompt categories (direct request, hypothetical framing, roleplay framing, rephrasing)
		- How many prompts per category?
		- What does "consistent" or "inconsistent" refusal look like?
	- [ ] Formulate a clear, flasifiable question before writing prompts (define it as measurable hypothesis)
	- [ ] Consider these sources:
		- Anthropic alignment research blog
		- [METR task design documentation](https://metr.org/)
		- EleutherAI's [lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness)
		- Papers on refusal consistency, e. g. "Harm Bench" and "SimpleSafetyTests" for inspiration on structure.
- [ ] Build Dataset of Prompts (5-10 h)
	- [ ] Write/curate prompts used for eval.
	- [ ] e. g. a factual question, a correct answer, follow-up where user pushes back.
	- [ ] Strive for variety: Have more than 100 samples, covering different topics or phrasings. Store as `JSON` files (or `CSV`) under `data/` folder. Include metadata columns like `category`, `framing_type` and `expected_behaviour`.
	- [ ] Consider these sources:
		- Existing public datasets on HuggingFace (use search function) as inspiration
		- Look at eval dataset structure in [BIG-Bench](https://github.com/google/BIG-bench) or [TruthfulQA](https://github.com/sylinrl/TruthfulQA)
		- Papers on refusal consistency, e. g. "Harm Bench" and "SimpleSafetyTests" for inspiration on structure.
		- OWASP LLM Top 10 for categories of LLM risks to draw from.
- [ ] Write Eval in `inspect-ai` (6-12 h)
	- [ ] Write python script using `inspect-ai`'s three components:
		- dataset loader
		- solver (sending prompts to local model)
		- scorer (checking output against expected behaviour)
	- [ ] Start with keyword match scorer (e. g. "I can't", "I'm unable to", etc.) and optionally expand to model-graded scorer where model judges the output.
	- [ ] Consider these sources:
		- [`inspect-ai` documentation](https://inspect.aisi.org.uk/), especially the "Sovers" and "Scorers" sections.
		- `inspect-ai`'s [GitHub repo of example evals](https://github.com/UKGovernmentBEIS/inspect_evals)
- [ ] Run Eval and Collect Results (1-3 h)
	- [ ] Run model and save output logs to `results/` folder. (`inspect-ai` produces logs automatically)
	- [ ] Run on second model?
- [ ] Analyse and Visualise Results (5-10 h)
	- [ ] Load `JSON` output
	- [ ] compute summary statistics
	- [ ] produce publication-quality plots.
	- [ ] Answer questions like "does failure rate vary by topic category" or "is there a relationship between prompt length and sycophantic behaviour" using `ggplot2` and `dplyr` (Python's `matplotlib.seaborn` works too).
	- [ ] Barcharts
	- [ ] R Markdown notebook (`.Rmd`)?
	- [ ] Consider these sources:
		- Hadley Wickham's [_R for Data Science_](https://r4ds.had.co.nz/)
		- `ggplot2` documentation
- [ ] Document (4-8 h)
	- [ ] Update `README` to explain:
		- [ ] Behaviour tested, why it matters for AI safety (motivation), how eval was designed (methodology), what I found (findings), where it lacks depth (limitations).
		- [ ] Include plots.
	- [ ] Create `CONTRIBUTING.md` or add future work section.
	- [ ] Consider these sources:
		- Established safety evals' documentation, e. g. the [HarmBench](https://github.com/centerforaisafety/HarmBench) and [TruthfulQA](https://github.com/sylinrl/TruthfulQA) repos 

</details>

## Todo
<details>

<summary> Click here to expand Todos </summary>

- 

</details>





---

⠎⠍⠂  
⠎⠏⠆  
⠈⠏⠀
