## 2024-11-11 - File I/O Bottleneck in Multi-Agent Evaluation
**Learning:** The prompt fetching function `get_prompt_text` was repeatedly performing disk I/O to read static files for every processed example and agent, leading to unnecessary overhead especially when using ThreadPoolExecutor for concurrent agent processing.
**Action:** Use `functools.lru_cache` on functions reading static configuration or prompt files to prevent redundant disk I/O in parallel execution scenarios.
