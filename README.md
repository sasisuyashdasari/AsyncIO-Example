# AsyncIO-Example

Examples comparing synchronous and asynchronous Python, from basic `asyncio` concepts up to a real-world image pipeline that downloads and processes images concurrently.

## Contents

| File | What it shows |
| --- | --- |
| `example_1.py` | Synchronous baseline: two `time.sleep` calls run one after the other. |
| `example_2.py` | Coroutines awaited in sequence with `async` / `await` and `asyncio.run`. |
| `example_3.py` | Concurrency with `asyncio.create_task`. |
| `example_4.py` | Same as example 3, awaiting the tasks in reverse order. |
| `example_5.py` | Pitfall: a blocking `time.sleep` inside a coroutine stops the event loop. |
| `example_6.py` | Running blocking functions with `asyncio.to_thread` and `ProcessPoolExecutor`. |
| `example_7.py` | Task scheduling with `create_task`, `asyncio.gather`, and `return_exceptions`. |
| `real_world_example_sync_v1.py` | Baseline: download and process images one at a time with `requests` and Pillow. |
| `real_world_example_async_v1.py` | Earlier async version of the same pipeline, using `asyncio` with `requests`. |
| `real_world_example_async_v2.py` | Async version with `aiofiles`, `httpx`, and a process pool for image processing. |
| `real_world_example_async_v3.py` | Final version: bounded concurrent downloads with a semaphore, `TaskGroup`, and CPU-bound edge detection offloaded to a process pool. |

The `real_world_example_*` scripts download 12 images into `original_images/` and write edge-detected versions into `processed_images/`. Running them prints timing for the download and processing stages so the versions can be compared.

## Requirements

- Python 3.11+ (the async v3 script uses `asyncio.TaskGroup`, added in 3.11)
- Packages listed in `requirements.txt`

## Setup

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Running

```bash
python example_1.py
python real_world_example_sync_v1.py
python real_world_example_async_v3.py
```

Run the real-world scripts from the repository root, since they write to relative `original_images/` and `processed_images/` paths.

## License

No license has been specified yet.
