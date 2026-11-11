## 2024-11-11 - File I/O Optimization in Parallel Workers
**Learning:** In LLM evaluation scripts like `run_stateful_gsm_symbolic.py` that use thread pools (`ThreadPoolExecutor`) for concurrent agent creation, reading static prompt text directly from files inside loops without caching causes redundant file I/O operations and performance degradation, specially noticeable at a large scale.
**Action:** Use `functools.lru_cache(maxsize=None)` to cache the content of static prompt files when they are heavily requested by concurrent workers to reduce I/O bottlenecks.
