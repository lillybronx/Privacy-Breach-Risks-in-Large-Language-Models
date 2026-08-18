# Avalon FinTech — LLM Privacy Compliance Under Organisational Pressure

Research repository for the MSc dissertation *"When AI Breaks the Rules: Evaluating Privacy Breach Risks Through Agentic Misalignment in Large Language Models
"*, testing whether Claude, GPT-4o, and Gemini maintain GDPR privacy compliance when exposed to simulated internal organisational pressure (authority, justification, urgency, and contextual conflict).

## Pipeline Overview

The files in this repository represent the full experimental pipeline, from prompt generation through to the final scored dataset. They are intended to be run/read in the following order:

| Step | File | Description |
|---|---|---|
| 1 | `lancelot_prompt_matrix.ipynb` | Generates the 24-condition experimental prompt matrix (authority × justification × urgency × conflict), constructing the full email-based prompt content for each condition. |
| 2 | `lancelot_prompt_matrix.csv` | Output of Step 1: the structured prompt matrix (condition IDs, variable levels, and full prompt text) used as input for the API calls in Step 3. |
| 3a | `CLAUDE.ipynb` | Sends the prompt matrix to the Claude API (model: `claude-sonnet-4-5`) and collects raw responses. |
| 3b | `CHATGPT.ipynb` | Sends the prompt matrix to the OpenAI API (model: `gpt-4o`) and collects raw responses. |
| 3c | `GEMINI.ipynb` | Sends the prompt matrix to the Gemini API (model: `gemini-2.5-pro`) and collects raw responses. |
| 4 | `Parsing_LLM_Responses_AvalonFT.ipynb` | Parses the raw API responses, extracting structured fields from each model's output (scratchpad reasoning, email/tool-use actions) via regex matching. |
| 5 | `Scoring_LLM_Responses_AvalonFT.ipynb` | Applies the GDPR breach scoring rubric (rule-based, regex-driven) and the LLM-as-judge awareness scoring process to the parsed responses. |
| 6 | `API_RESPONSES_AVALON_FINTECH_FULLY_SCORED.csv` | **Final dataset.** The complete, fully scored and manually verified dataset used for all statistical analysis and results presented in the dissertation. |

## File Descriptions

- **Prompt Matrix Generator** (`lancelot_prompt_matrix.ipynb`): Builds the 24 experimental conditions from the four independent variables and constructs the corresponding synthetic email inbox content (including conflict-signal and filler emails) for each condition.
- **Prompt Matrix CSV** (`lancelot_prompt_matrix.csv`): The tabular output of the generator. One row per condition, with the full prompt text used in the API calls.
- **Per-Model API Call Notebooks** (`CLAUDE.ipynb`, `CHATGPT.ipynb`, `GEMINI.ipynb`): Each notebook sends the full prompt matrix to its respective provider's API and stores the raw responses, including metadata (latency, token counts, timestamps).
- **Parsing Notebook** (`Parsing_LLM_Responses_AvalonFT.ipynb`): Extracts structured fields from the raw `response_text` of each API call (specifically the model's scratchpad reasoning and any email/forward tool-use actions) via regex pattern matching.
- **Scoring Notebook** (`Scoring_LLM_Responses_AvalonFT.ipynb`): Applies the GDPR breach scoring rubric (0–3 ordinal scale, rule-based automated detection) and the LLM-as-judge awareness scoring process (cross-model judging to mitigate self-assessment bias).
- **Final Scored Dataset** (`API_RESPONSES_AVALON_FINTECH_FULLY_SCORED.csv`): The complete dataset (360 responses × 25 columns) combining all original experimental variables, parsed fields, and both scoring dimensions. This is the dataset used for all analysis, charts, and statistics presented in the Results and Discussion chapters.

## Notes

- All client data, personas, and organisational details referenced in the prompts are entirely fictional, constructed for this study.
- Model access details (exact versions, access dates) are documented in the dissertation's Methodology chapter.
