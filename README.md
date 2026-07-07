# Auto-Tagging-Support-Tickets-Using-LLM

## Objective
Automatically tag free-text support tickets into categories using a large language model (LLM), without any manual labeling or training.

## Dataset
**Free-text Support Ticket Dataset** — a small custom dataset of 10 realistic support ticket messages covering common issue types (billing, technical, account access, delivery, cancellation).

## Approach

1. **Model Used**
   - `facebook/bart-large-mnli` via Hugging Face `transformers` — a free, open-source zero-shot classification model (no API key or billing required).

2. **Candidate Tags**
   - Billing Issue
   - Technical Issue
   - Account Access
   - Delivery Problem
   - Cancellation Request

3. **Zero-Shot Classification**
   - Each ticket was passed directly to the model along with the candidate tags.
   - The model returned a probability score for every tag, without seeing any labeled examples beforehand.

4. **Few-Shot Learning**
   - A short prompt containing 3 solved example tickets (with their correct tags) was prepended before each new ticket.
   - This "few-shot" context helped guide the model's classification for new, unseen tickets.

5. **Zero-Shot vs Few-Shot Comparison**
   - Every ticket was classified using both methods.
   - Results (predicted tag + confidence score) were compared side by side in a single table to evaluate differences in predictions and confidence.

6. **Top-3 Tag Output**
   - For each ticket, the top 3 most probable tags (with confidence scores) were generated and displayed, ranked from most to least likely.

## Skills Demonstrated
- Prompt engineering
- LLM-based text classification
- Zero-shot and few-shot learning
- Multi-class prediction and ranking

## Tools & Libraries
- Python, Google Colab
- Hugging Face `transformers`
- Pandas

## How to Run
1. Open the notebook in Google Colab.
2. Run the cells in order — the notebook installs `transformers`, loads the zero-shot classification pipeline, creates the sample ticket dataset, and runs both zero-shot and few-shot classification.
3. View the final comparison table and top-3 tag outputs at the end of the notebook.

## Possible Improvements
- Use a larger, real-world support ticket dataset.
- Fine-tune a smaller LLM on labeled ticket data for higher accuracy.
- Expand the few-shot examples to cover more tag categories.
