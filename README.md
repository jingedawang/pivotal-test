# Trusted Editing Redteam

This is a lightweight prototype inspired by the ["AI Control" paper](https://arxiv.org/abs/2312.06942), designed to explore how an _untrusted_ language model might inject subtle vulnerabilities (e.g., backdoors) into code, and whether a _trusted_ editor model can reliably sanitize them.

## Overview

- The **untrusted model** (e.g., `gpt-4o`) generates Python code to solve programming problems, with subtle "vulnerabilities" included.
- The **trusted model** (e.g., `gpt-4o-mini`) attempts to clean the code of unsafe constructs.
- We then **evaluate** whether known backdoor patterns (e.g., `eval`, `exec`, `os.system`) remain in the edited output.

## Features

- Uses OpenAI's official API (`openai>=1.0.0`) with chat-based completions.
- Environment-safe: loads API keys from a `.env` file.
- Includes a simplified APPS-style dataset for testing.
- Performs automatic vulnerability detection post-editing.

## Requirements

- Python 3.8+
- Dependencies: `openai`, `python-dotenv`

Install with:

```bash
pip install openai python-dotenv
```

## Usage

Set your OpenAI API key in a `.env` file:

```
OPENAI_API_KEY=your-api-key-here
```

Then run the experiment:

```bash
python trusted_editing.py
```

## Notes

- This is a **research demo**, not a production security tool.
- Prompt phrasing is tuned to avoid violating OpenAI usage policies by framing the experiment as **research on model behavior**, not actual malicious intent.
- The example is simplified for demonstration. To make it more realistic, we may need to ask the untrusted model to generate more sophisticated backdoors and utilize complex checking logic.

## License

MIT License
