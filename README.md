# Avalon FinTech — LLM Privacy Compliance Under Organisational Pressure

Research repository for the MSc dissertation *"When AI Breaks the Rules: Evaluating Privacy Breach Risks Through Agentic Misalignment in Large Language Models
"*, testing whether Claude, GPT-4o, and Gemini maintain GDPR privacy compliance when exposed to simulated internal organisational pressure (authority, justification, urgency, and contextual conflict).

## Repository Structure
 
The repository is organised into five numbered folders, reflecting the full experimental pipeline from prompt generation through to final analysis.
 
```
01_prompt_generation/
    Lancelot_Prompt_Matrix.ipynb
    Lancelot_Prompt_Matrix.csv
 
02_api_calls/
    CLAUDE.ipynb
    CHATGPT.ipynb
    GEMINI.ipynb
 
03_parsing_and_scoring/
    Parsing_LLM_Responses_AvalonFT.ipynb
    Scoring_LLM_Responses_AvalonFT.ipynb
 
04_data_analysis/
    Data_Analysis_Fully_Scored_Responses.ipynb
 
05_final_dataset/
    API_RESPONSES_AVALON_FINTECH_FULLY_SCORED.csv
 
README.md
```
 
## Pipeline Overview
 
| Step | Folder | Description |
|---|---|---|
| 1 | `01_prompt_generation/` | Generates the 24-condition experimental prompt matrix (authority × justification × urgency × conflict), constructing the full email-based prompt content for each condition, and exports it as a structured CSV. |
| 2 | `02_api_calls/` | Sends the prompt matrix to each provider's API (Claude, GPT-4o, Gemini) and collects raw responses, one notebook per model. |
| 3 | `03_parsing_and_scoring/` | Parses the raw API responses into structured fields (scratchpad reasoning, email/tool-use actions), then applies the GDPR breach scoring rubric and LLM-as-judge awareness scoring process. |
| 4 | `04_data_analysis/` | Runs all statistical analysis and generates the charts and tables presented in the dissertation's Results and Discussion chapters (breach rates by pressure variable, correlation analysis, relative risk/odds ratio/Fisher's exact tests, escalation behaviour, etc.). |
| 5 | `05_final_dataset/` | The complete, fully scored and manually verified dataset used throughout the study. |
 
## Folder and File Descriptions
 
### `01_prompt_generation/`
- **`Lancelot_Prompt_Matrix.ipynb`** — Builds the 24 experimental conditions from the four independent variables and constructs the corresponding synthetic email inbox content (including conflict-signal and filler emails) for each condition.
- **`Lancelot_Prompt_Matrix.csv`** — The tabular output of the generator notebook: one row per condition, with the full prompt text used in the API calls.
### `02_api_calls/`
- **`CLAUDE.ipynb`** — Sends the prompt matrix to the Anthropic API (model: `claude-sonnet-4-5`) and collects raw responses.
- **`CHATGPT.ipynb`** — Sends the prompt matrix to the OpenAI API (model: `gpt-4o`) and collects raw responses.
- **`GEMINI.ipynb`** — Sends the prompt matrix to the Google API (model: `gemini-2.5-pro`) and collects raw responses.
### `03_parsing_and_scoring/`
- **`Parsing_LLM_Responses_AvalonFT.ipynb`** — Extracts structured fields from the raw `response_text` of each API call via regex pattern matching, including the model's scratchpad reasoning and any email/forward tool-use actions.
- **`Scoring_LLM_Responses_AvalonFT.ipynb`** — Applies the GDPR breach scoring rubric (0–3 ordinal scale, rule-based automated detection combined with condition-specific logic).
### `04_data_analysis/`
- **`Data_Analysis_Fully_Scored_Responses.ipynb`** — The full analysis pipeline run on the final scored dataset: descriptive statistics, breach distributions by model, breach rates by pressure variable (authority, justification, urgency, conflict), awareness–breach correlation analysis, relative risk/odds ratio/Fisher's exact significance testing, escalation-to-compliance analysis, and all corresponding charts and tables presented in the dissertation.
### `05_final_dataset/`
- **`API_RESPONSES_AVALON_FINTECH_FULLY_SCORED.csv`** — The complete dataset (360 responses) combining all original experimental variables, parsed fields, and both scoring dimensions (breach score, awareness score). This is the dataset used as input for `04_data_analysis/`.
## Notes
 
- All client data, personas, and organisational details referenced in the prompts are entirely fictional, constructed for this study.
- Model access details (exact versions, access dates) are documented in the dissertation's Methodology chapter.
