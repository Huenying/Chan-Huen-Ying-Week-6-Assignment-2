# Simple Sentiment Scorer (heuristic-based)

## What the Tool Does
This project provides a simple, heuristic-based sentiment analysis tool for business and news text. 

The tool, implemented in `tool.py`, uses keyword matching to classify input text as positive, negative, or neutral, and provides a normalized sentiment score. It is designed for quick, interpretable analysis of financial reports, press releases, or news articles.

A demo script (`demo.py`) integrates this tool with a simple agent that uses the DeepSeek API (OpenAI-compatible) to decide when to call the sentiment scorer, demonstrating both successful and error-handling scenarios.

## How to Run the Demo
1. **Install dependencies** in your virtual environment:
   ```sh
   pip install -r requirements.txt
   # or manually:
   pip install openai python-dotenv
   ```
2. **Set your DeepSeek API key** in a `.env` file:
   ```
   DEEPSEEK_API_KEY=your_deepseek_api_key_here
   ```
3. **Run the demo script:**
   ```sh
   python demo.py
   # or to save output:
   python demo.py > output.txt
   ```
   - Four test cases are included in demo.py. Replace them with your own test cases.

4. **Outcome of test cases**
```
--- Case 1: Successful Execution (Positive)---
Agent decided to call tool: sentiment_scorer
With arguments: {'text': 'Our company delivered excellent quarterly results with strong profit growth across all divisions. The successful product launch exceeded expectations, and we are pleased to announce an upgrade to our guidance. Customer feedback remains overwhelmingly positive, reflecting the great work of our dedicated team and the strong momentum in our business.'}
Tool Success: {'sentiment': 'positive', 'score': 0.9126689115327974}
```

```
--- Case 2: Successful Execution (Negative) ---
Agent decided to call tool: sentiment_scorer
With arguments: {'text': 'The company reported poor quarterly results with significant losses and declining revenues across key divisions. The failed product launch missed expectations, forcing us to announce a downgrade to our guidance. Customer feedback has been overwhelmingly negative, reflecting serious problems with our operations and increased risk factors ahead.'}
Tool Success: {'sentiment': 'negative', 'score': 0.2816745904875445}
```

agent.analyze_text("")
```
--- Case 3: Empty Input ---
Empty Input or Invalid input type. Please provide a non-empty string.
```

agent.analyze_text(123)
```
--- Case 4: Invalid Input (Non-string) ---
Empty Input or Invalid input type. Please provide a non-empty string.
```

## Design Decisions and Limitations
- **Heuristic Approach:** The sentiment scorer uses simple keyword lists for positive and negative words. This makes it fast and interpretable, but less accurate than machine learning models for nuanced language.
- **No External NLP Libraries:** Only standard Python and OpenAI-compatible APIs are used for maximum portability and simplicity.
- **Error Handling:** The agent and tool handle empty input and non-string input with clear error messages.

- **Limitations:**
  - The tool does not handle sarcasm or complex sentiment.
  - The keyword lists are not exhaustive and may miss domain-specific terms.
  - The demo might not be suitable for production-grade sentiment analysis.

---
