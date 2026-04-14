# AI Code Evaluation Framework

A structured framework for evaluating AI-generated code across multiple dimensions including instruction following, code quality, tool usage, testing, and communication clarity.

## Overview

This project provides tools and utilities for conducting **side-by-side (SxS) evaluations** of AI model outputs on real-world coding tasks. Designed for researchers and engineers working on improving AI coding assistants.

## Features

- **Prompt Generator**: Create complex, single-turn coding prompts grounded in real repositories
- **Model Evaluator**: Execute prompts across multiple AI model instances
- **SxS Comparator**: Structured side-by-side comparison with scoring rubrics
- **Report Generator**: Generate detailed evaluation reports with justifications

## Evaluation Dimensions

| Dimension | Description |
|-----------|-------------|
| Instruction Following | Does the output match the prompt requirements? |
| Code Quality | Readability, efficiency, best practices |
| Tool Usage | Correct use of APIs, libraries, frameworks |
| Testing & Validation | Test coverage, edge cases, error handling |
| Communication | Clarity of explanations and documentation |

## Installation

```bash
pip install -r requirements.txt
```

## Quick Start

```python
from evaluator import CodeEvaluator, PromptGenerator

# Generate a coding prompt from a repository
generator = PromptGenerator(repo_path="path/to/repo")
prompt = generator.create_prompt(
    task_type="refactor",
    complexity="hard",
    language="python"
)

# Evaluate model outputs
evaluator = CodeEvaluator()
results = evaluator.evaluate_sxs(
    prompt=prompt,
    model_a_output=response_a,
    model_b_output=response_b,
    dimensions=["instruction_following", "code_quality", "testing"]
)

# Generate report
evaluator.generate_report(results, output="evaluation_report.md")
```

## Project Structure

```
ai-code-eval/
├── evaluator/
│   ├── __init__.py
│   ├── core.py              # Core evaluation engine
│   ├── prompt_generator.py  # Prompt creation from repositories
│   ├── comparator.py        # Side-by-side comparison logic
│   ├── rubrics.py           # Scoring rubrics and criteria
│   └── report.py            # Report generation
├── prompts/
│   ├── python/              # Python coding prompts
│   ├── javascript/          # JavaScript coding prompts
│   └── multi_lang/          # Multi-language prompts
├── tests/
│   ├── test_evaluator.py
│   ├── test_prompt_gen.py
│   └── test_comparator.py
├── examples/
│   ├── basic_evaluation.py
│   └── batch_comparison.py
├── requirements.txt
├── setup.py
└── README.md
```

## Supported Languages

- Python
- JavaScript / TypeScript
- Java
- Go
- C++

## Usage Examples

### Creating Prompts from Real Codebases

```python
from evaluator import PromptGenerator

gen = PromptGenerator(repo_url="https://github.com/pandas-dev/pandas")
prompt = gen.create_prompt(
    task_type="bug_fix",
    target_file="pandas/core/frame.py",
    complexity="medium"
)
print(prompt.description)
print(prompt.expected_behavior)
```

### Batch Evaluation

```python
from evaluator import BatchEvaluator

batch = BatchEvaluator(models=["model_a", "model_b", "model_c"])
results = batch.run(
    prompts=prompt_suite,
    dimensions=["instruction_following", "code_quality", "testing", "communication"]
)
batch.export_results("results.json")
```

## Scoring Rubric

Each dimension is scored on a 1-5 scale:

| Score | Label | Description |
|-------|-------|-------------|
| 5 | Excellent | Exceeds expectations, production-ready |
| 4 | Good | Meets requirements with minor issues |
| 3 | Acceptable | Functional but needs improvement |
| 2 | Poor | Significant issues, partially functional |
| 1 | Failing | Does not meet requirements |

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

MIT License - see [LICENSE](LICENSE) for details.

## Author

**Ansar Ahmad** — Senior Data Scientist & AI Evaluation Specialist

- Email: anasalig44@gmail.com
