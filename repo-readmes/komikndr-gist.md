# What it is
This is my OpenCode setup for local models, mainly using a customized llama.cpp configuration.

For Qwen 3.8, DeepSeek V4, and Glimmer, the models are already trained to support reasoning effort levels. Depending on the model, these may be exposed as `low`, `medium`, `high`, `xhigh`, or as `low`, `high`, and `max`.

For models that support reasoning but were not trained with explicit reasoning-effort levels, such as the Qwen 3.5 and 3.6 variants, I use a token budget to limit the amount of reasoning.

Although Qwen 3.8 has built-in reasoning-effort levels, I still apply a maximum reasoning-token cap for each effort level.

Although the llama.cpp CLI flags specify `preserve_thinking` and a default reasoning budget, these can still be overridden through the API, so this works fine for my setup.

Yes, there is also an `xhigh-no-preserve` variant. In this mode, the model uses its reasoning as a scratchpad without preserving it in the conversation history. I use this when I do not want the reasoning output to unnecessarily consume the context window.

Most of the time, I use `low` reasoning.

## Example: None vs Low
<img width="1367" height="812" alt="image" src="img/komikndr-gist/09e5cbbb-3aa4-40bd-9849-a620a0993443_2" />

## Example: Xhigh no preserve, As per setup, it succesfully forgot the reasoning
<img width="1493" height="927" alt="image" src="img/komikndr-gist/05026885-26ec-4b20-8673-3a79abdbd160_2" />
<img width="1491" height="523" alt="image" src="img/komikndr-gist/c252189c-458b-4790-a690-c04daaca87cc_2" />

# Llamacpp Conf (b10472)

```bash
/home/USER/llama.cpp/llama-server \
  --model /mnt/d/MODEL_STORE/LLM_SETUP/Qwen3.8-27B/Qwen3.8-27B-UD-Q5_K_XL.gguf \
  --alias Qwen3.8-27B \
  --host 0.0.0.0 \
  --chat-template-file /mnt/d/MODEL_STORE/LLM_SETUP/Qwen3.8-27B/chat_template.jinja \
  --no-context-shift \
  --metrics \
  --kv-unified \
  --cache-ram 16384 \
  --ctx-size 81920 \
  --port 8001 \
  --cache-type-k q8_0 \
  --cache-type-v q8_0 \
  --flash-attn on \
  --temp 1.0 \
  --top-p 0.95 \
  --top-k 20 \
  --min-p 0.0 \
  --presence-penalty 0.0 \
  --repeat-penalty 1.0 \
  --jinja \
  --chat-template-kwargs '{"preserve_thinking": true}' \
  --spec-type draft-mtp \
  --spec-draft-n-max 2 \
  --reasoning-budget 8192 \
  -np 1 \
  -ub 256
  ```
# Froggeric Qwen Fix for the Jinja
https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates

# Opencode Conf
`nvim ~/.config/opencode/opencode.json`
  
```json
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": [
    "@tarquinen/opencode-dcp@latest"
  ],
  "provider": {
    "openai": {
      "options": {
        "headerTimeout": 60000,
        "timeout": 600000,
        "chunkTimeout": 60000
      }
    },
    "local-vllm": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "vLLM (Local)",
      "options": {
        "baseURL": "http://localhost:8000/v1"
      },
      "models": {
        "cyankiwi/Nemotron-Orchestrator-8B-AWQ-4bit": {
          "name": "cyankiwi/Nemotron-Orchestrator-8B-AWQ-4bit",
          "max_tokens": 40960
        }
      }
    },
    "local-llamacpp": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "llama.cpp (Local)",
      "options": {
        "baseURL": "http://localhost:8001/v1"
      },
      "models": {
        "Qwen3.6-35B": {
          "name": "Qwen3.6-35B",
          "max_tokens": 131072,
          "modalities": {
            "input": [
              "image",
              "text"
            ],
            "output": [
              "text"
            ]
          },
          "variants": {
            "none": {
              "chat_template_kwargs": {
                "enable_thinking": false
              }
            },
            "low": {
              "reasoning_budget_tokens": 512
            },
            "medium": {
              "reasoning_budget_tokens": 2048
            },
            "xhigh": {
              "reasoning_budget_tokens": 8192
            },
            "xhigh-no-preserve": {
              "reasoning_budget_tokens": 8192,
              "chat_template_kwargs": {
                "preserve_thinking": false
              }
            }
          }
        },
        "Qwen3.8-27B": {
          "name": "Qwen3.8-27B",
          "max_tokens": 81920,
          "modalities": {
            "input": [
              "image",
              "text"
            ],
            "output": [
              "text"
            ]
          },
          "variants": {
            "none": {
              "reasoningEffort": "none"
            },
            "low": {
              "reasoningEffort": "low",
              "reasoning_budget_tokens": 512
            },
            "medium": {
              "reasoningEffort": "medium",
              "reasoning_budget_tokens": 2048
            },
            "xhigh": {
              "reasoningEffort": "xhigh",
              "reasoning_budget_tokens": 8192
            },
            "xhigh-no-preserve": {
              "reasoningEffort": "xhigh",
              "reasoning_budget_tokens": 8192,
              "chat_template_kwargs": {
                "preserve_thinking": false
              }
            }
          }
        },
        "Muse-Glimmer-30B": {
          "name": "Muse-Glimmer-30B",
          "max_tokens": 81920,
          "modalities": {
            "input": [
              "image",
              "text"
            ],
            "output": [
              "text"
            ]
          },
          "variants": {
            "low": {
              "reasoningEffort": "low",
              "reasoning_budget_tokens": 512
            },
            "medium": {
              "reasoningEffort": "medium",
              "reasoning_budget_tokens": 2048
            },
            "high": {
              "reasoningEffort": "high",
              "reasoning_budget_tokens": 4096
            },
            "xhigh": {
              "reasoningEffort": "xhigh",
              "reasoning_budget_tokens": 8192
            }
          }
        },
        "DeepSeek-V4-Flash-0731": {
          "name": "DeepSeek-V4-Flash-0731",
          "max_tokens": 81920,
          "variants": {
            "low": {
              "reasoningEffort": "low",
              "reasoning_budget_tokens": 512
            },
            "high": {
              "reasoningEffort": "high",
              "reasoning_budget_tokens": 4096
            },
            "max": {
              "reasoningEffort": "max",
              "reasoning_budget_tokens": 8192
            }
          }
        },
        "Omnicoder-2-9B": {
          "name": "Omnicoder-2-9B",
          "max_tokens": 131072,
          "modalities": {
            "input": [
              "image",
              "text"
            ],
            "output": [
              "text"
            ]
          },
          "variants": {
            "none": {
              "chat_template_kwargs": {
                "enable_thinking": false
              }
            },
            "low": {
              "reasoning_budget_tokens": 512
            },
            "medium": {
              "reasoning_budget_tokens": 2048
            },
            "xhigh": {
              "reasoning_budget_tokens": 8192
            },
            "xhigh-no-preserve": {
              "reasoning_budget_tokens": 8192,
              "chat_template_kwargs": {
                "preserve_thinking": false
              }
            }
          }
        },
        "Ornith-9B": {
          "name": "Ornith-9B",
          "max_tokens": 131072,
          "modalities": {
            "input": [
              "image",
              "text"
            ],
            "output": [
              "text"
            ]
          },
          "variants": {
            "none": {
              "chat_template_kwargs": {
                "enable_thinking": false
              }
            },
            "low": {
              "reasoning_budget_tokens": 512
            },
            "medium": {
              "reasoning_budget_tokens": 2048
            },
            "xhigh": {
              "reasoning_budget_tokens": 8192
            },
            "xhigh-no-preserve": {
              "reasoning_budget_tokens": 8192,
              "chat_template_kwargs": {
                "preserve_thinking": false
              }
            }
          }
        }
      }
    },
    "local-ninfer": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Ninfer (Windows)",
      "options": {
        "baseURL": "http://localhost:10909/v1"
      },
      "models": {
        "qwen3.8-27b": {
          "name": "Qwen3.8-27B",
          "max_tokens": 81920,
          "variants": {
            "none": {
              "reasoningEffort": "none"
            },
            "low": {
              "reasoningEffort": "low"
            },
            "medium": {
              "reasoningEffort": "medium"
            },
            "xhigh": {
              "reasoningEffort": "xhigh"
            }
          }
        }
      }
    }
  }
}
```

# Replace N-Gram layers from Q4XS into Q8_0, bolted.py
Just run it with python bolted.py
```python
import fcntl
import gc
import os
import shutil
import struct
from dataclasses import dataclass
from pathlib import Path

try:
    from gguf import GGUFReader
except ImportError as exc:
    raise SystemExit(
        "GGUFReader is not installed. Install the required packages with:\n"
        "  python3 -m pip install --upgrade numpy gguf"
    ) from exc


TENSOR_NAME = "per_layer_token_embd.weight"
SOURCE_NAME = "Qwen3.8-Flash-Next-Q8_0-00003-of-00006.gguf"
TARGET_NAMES = (
    "Qwen3.8-Flash-Next-UD-IQ4_XS-00001-of-00003.gguf",
    "Qwen3.8-Flash-Next-UD-IQ4_XS-00002-of-00003.gguf",
    "Qwen3.8-Flash-Next-UD-IQ4_XS-00003-of-00003.gguf",
)
OUTPUT_DIRECTORY_NAME = "Qwen3.8-Flash-Next-Q8-Token-Embed"
COPY_BUFFER_SIZE = 16 * 1024 * 1024
SPACE_MARGIN = 1024 * 1024 * 1024
EXPECTED_SHAPE = (160, 320001536)
EXPECTED_SOURCE_TENSOR_BYTES = 54_400_261_120
EXPECTED_TARGET_TENSOR_BYTES = 28_800_138_240


@dataclass(frozen=True)
class TensorLayout:
    name: object
    shape: object
    type_name: object
    type_id: object
    n_bytes: object
    data_offset: object
    relative_offset: object
    type_field_offset: object
    offset_field_offset: object


@dataclass(frozen=True)
class FileLayout:
    path: object
    file_size: object
    data_offset: object
    alignment: object
    split_no: object
    split_count: object
    split_tensor_count: object
    tensors: object
    stat_signature: object


class InputLocks:
    def __init__(self, paths):
        self.paths = paths
        self.files = []

    def __enter__(self):
        try:
            for path in self.paths:
                file = path.open("rb")
                try:
                    fcntl.flock(file.fileno(), fcntl.LOCK_SH | fcntl.LOCK_NB)
                except BaseException:
                    file.close()
                    raise
                self.files.append(file)
        except BaseException:
            self.__exit__(None, None, None)
            raise
        return self

    def __exit__(self, _exc_type, _exc_value, _traceback):
        for file in reversed(self.files):
            try:
                fcntl.flock(file.fileno(), fcntl.LOCK_UN)
            finally:
                file.close()
        self.files.clear()


class Progress:
    def __init__(self, label, total):
        self.label = label
        self.total = total
        self.completed = 0
        self.next_report = 0

    def advance(self, amount):
        self.completed += amount
        if self.completed >= self.next_report or self.completed == self.total:
            completed_gib = self.completed / (1024**3)
            total_gib = self.total / (1024**3)
            print(f"\r{self.label}: {completed_gib:.1f}/{total_gib:.1f} GiB", end="", flush=True)
            self.next_report = self.completed + 1024**3

    def finish(self):
        print()


def stat_signature(path):
    stat = path.stat()
    return stat.st_dev, stat.st_ino, stat.st_size, stat.st_mtime_ns


def require_unchanged(layout):
    if stat_signature(layout.path) != layout.stat_signature:
        raise OSError(f"input changed after inspection: {layout.path}")


def metadata_integer(reader, key):
    field = reader.get_field(key)
    if field is None:
        raise ValueError(f"missing required GGUF metadata key: {key}")
    return int(field.contents())


def inspect_gguf(path):
    if not path.is_file():
        raise FileNotFoundError(f"required input does not exist: {path}")

    initial_signature = stat_signature(path)
    reader = GGUFReader(str(path), mode="r")
    if reader.endianess.name != "LITTLE":
        raise ValueError(f"only little-endian GGUF files are supported: {path}")

    tensors = []
    for tensor in reader.tensors:
        name_bytes = tensor.name.encode("utf-8")
        dimension_count = len(tensor.shape)
        type_field_offset = tensor.field.offset + 8 + len(name_bytes) + 4 + 8 * dimension_count
        offset_field_offset = type_field_offset + 4
        relative_offset = int(tensor.field.parts[5][0])

        if int(tensor.data_offset) != int(reader.data_offset) + relative_offset:
            raise ValueError(f"inconsistent tensor offset for {tensor.name} in {path}")

        tensors.append(
            TensorLayout(
                name=tensor.name,
                shape=tuple(int(value) for value in tensor.shape),
                type_name=tensor.tensor_type.name,
                type_id=int(tensor.field.parts[4][0]),
                n_bytes=int(tensor.n_bytes),
                data_offset=int(tensor.data_offset),
                relative_offset=relative_offset,
                type_field_offset=type_field_offset,
                offset_field_offset=offset_field_offset,
            )
        )

    layout = FileLayout(
        path=path,
        file_size=path.stat().st_size,
        data_offset=int(reader.data_offset),
        alignment=int(reader.alignment),
        split_no=metadata_integer(reader, "split.no"),
        split_count=metadata_integer(reader, "split.count"),
        split_tensor_count=metadata_integer(reader, "split.tensors.count"),
        tensors=tuple(tensors),
        stat_signature=initial_signature,
    )

    del reader
    gc.collect()
    require_unchanged(layout)
    return layout


def only_named_tensor(layout, name):
    matches = [tensor for tensor in layout.tensors if tensor.name == name]
    if len(matches) != 1:
        raise ValueError(f"expected one {name!r} tensor in {layout.path}, found {len(matches)}")
    return matches[0]


def validate_inputs(source, targets):
    if (source.split_no, source.split_count, source.split_tensor_count) != (2, 6, 1224):
        raise ValueError(
            "unexpected source split metadata: "
            f"no={source.split_no}, count={source.split_count}, tensors={source.split_tensor_count}"
        )

    for expected_no, target in enumerate(targets):
        actual = (target.split_no, target.split_count, target.split_tensor_count)
        expected = (expected_no, 3, 1224)
        if actual != expected:
            raise ValueError(f"unexpected split metadata in {target.path}: expected {expected}, found {actual}")

    if sum(len(target.tensors) for target in targets) != 1224:
        raise ValueError("the IQ4 shards do not contain the expected total of 1224 tensors")

    source_tensor = only_named_tensor(source, TENSOR_NAME)
    target_matches = [tensor for target in targets for tensor in target.tensors if tensor.name == TENSOR_NAME]
    if len(target_matches) != 1:
        raise ValueError(f"expected one {TENSOR_NAME!r} tensor across the IQ4 shards, found {len(target_matches)}")
    target_tensor = target_matches[0]

    if target_tensor not in targets[1].tensors:
        raise ValueError(f"the target tensor is not in IQ4 shard 2: {targets[1].path}")
    if source_tensor.type_name != "Q8_0":
        raise ValueError(f"source tensor must be Q8_0, found {source_tensor.type_name}")
    if target_tensor.type_name != "IQ4_NL":
        raise ValueError(f"target tensor must be IQ4_NL, found {target_tensor.type_name}")
    if source_tensor.shape != target_tensor.shape or source_tensor.shape != EXPECTED_SHAPE:
        raise ValueError(
            f"unexpected tensor shapes: source={source_tensor.shape}, target={target_tensor.shape}, "
            f"expected={EXPECTED_SHAPE}"
        )
    if source_tensor.n_bytes != EXPECTED_SOURCE_TENSOR_BYTES:
        raise ValueError(
            f"unexpected source tensor size: expected {EXPECTED_SOURCE_TENSOR_BYTES}, found {source_tensor.n_bytes}"
        )
    if target_tensor.n_bytes != EXPECTED_TARGET_TENSOR_BYTES:
        raise ValueError(
            f"unexpected target tensor size: expected {EXPECTED_TARGET_TENSOR_BYTES}, found {target_tensor.n_bytes}"
        )
    if source_tensor.data_offset + source_tensor.n_bytes > source.file_size:
        raise ValueError("source tensor extends beyond its GGUF file")
    if target_tensor.data_offset + target_tensor.n_bytes > targets[1].file_size:
        raise ValueError("target tensor extends beyond its GGUF file")

    delta = source_tensor.n_bytes - target_tensor.n_bytes
    if delta <= 0 or delta % targets[1].alignment != 0:
        raise ValueError(f"invalid aligned replacement size delta: {delta}")

    target_start = target_tensor.relative_offset
    target_end = target_start + target_tensor.n_bytes
    for tensor in targets[1].tensors:
        if tensor == target_tensor:
            continue
        tensor_start = tensor.relative_offset
        tensor_end = tensor_start + tensor.n_bytes
        if max(target_start, tensor_start) < min(target_end, tensor_end):
            raise ValueError(f"target tensor overlaps {tensor.name} in IQ4 shard 2")

    return source_tensor, target_tensor, delta


def copy_region(source, destination, offset, length, progress):
    source.seek(offset)
    remaining = length
    while remaining:
        chunk = source.read(min(COPY_BUFFER_SIZE, remaining))
        if not chunk:
            raise OSError(f"unexpected end of file after copying {length - remaining} of {length} bytes")
        destination.write(chunk)
        remaining -= len(chunk)
        progress.advance(len(chunk))


def copy_file_atomic(source, destination):
    partial = destination.with_name(destination.name + ".partial")
    progress = Progress(f"Copying {source.path.name}", source.file_size)
    try:
        require_unchanged(source)
        with source.path.open("rb") as source_file, partial.open("xb") as destination_file:
            copy_region(source_file, destination_file, 0, source.file_size, progress)
            destination_file.flush()
            os.fsync(destination_file.fileno())
        require_unchanged(source)
        if partial.stat().st_size != source.file_size:
            raise OSError(f"copied size mismatch for {source.path}")
        partial.rename(destination)
        progress.finish()
    except BaseException:
        if partial.exists():
            partial.unlink()
        raise


def rebuild_middle_shard(
    source,
    target,
    source_tensor,
    target_tensor,
    delta,
    destination,
):
    partial = destination.with_name(destination.name + ".partial")
    expected_size = target.file_size + delta
    progress = Progress(f"Rebuilding {target.path.name}", expected_size)

    try:
        require_unchanged(source)
        require_unchanged(target)
        with target.path.open("rb") as target_file:
            header = bytearray(target_file.read(target.data_offset))
        if len(header) != target.data_offset:
            raise OSError(f"could not read the complete GGUF header from {target.path}")

        struct.pack_into("<I", header, target_tensor.type_field_offset, source_tensor.type_id)
        for tensor in target.tensors:
            new_offset = tensor.relative_offset
            if tensor.relative_offset > target_tensor.relative_offset:
                new_offset += delta
            struct.pack_into("<Q", header, tensor.offset_field_offset, new_offset)

        old_tensor_end = target_tensor.data_offset + target_tensor.n_bytes
        suffix_length = target.file_size - old_tensor_end

        with (
            target.path.open("rb") as target_file,
            source.path.open("rb") as source_file,
            partial.open("xb") as destination_file,
        ):
            destination_file.write(header)
            progress.advance(len(header))
            copy_region(
                target_file,
                destination_file,
                target.data_offset,
                target_tensor.relative_offset,
                progress,
            )
            copy_region(
                source_file,
                destination_file,
                source_tensor.data_offset,
                source_tensor.n_bytes,
                progress,
            )
            copy_region(target_file, destination_file, old_tensor_end, suffix_length, progress)
            destination_file.flush()
            os.fsync(destination_file.fileno())

        require_unchanged(source)
        require_unchanged(target)
        if partial.stat().st_size != expected_size:
            raise OSError(f"rebuilt size mismatch: expected {expected_size}, found {partial.stat().st_size}")
        partial.rename(destination)
        progress.finish()
    except BaseException:
        if partial.exists():
            partial.unlink()
        raise


def validate_output_shard(
    output,
    original,
    source_tensor,
    target_tensor,
    delta,
):
    if output.data_offset != original.data_offset:
        raise ValueError(f"output data section moved unexpectedly in {output.path}")
    if len(output.tensors) != len(original.tensors):
        raise ValueError(f"output tensor count changed unexpectedly in {output.path}")

    for produced, old in zip(output.tensors, original.tensors, strict=True):
        if produced.name != old.name or produced.shape != old.shape:
            raise ValueError(f"output tensor descriptor changed unexpectedly near {old.name}")

        expected_type = source_tensor.type_name if old.name == target_tensor.name else old.type_name
        expected_size = source_tensor.n_bytes if old.name == target_tensor.name else old.n_bytes
        expected_offset = old.relative_offset + (delta if old.relative_offset > target_tensor.relative_offset else 0)
        if produced.type_name != expected_type:
            raise ValueError(f"wrong output type for {produced.name}: {produced.type_name}")
        if produced.n_bytes != expected_size:
            raise ValueError(f"wrong output byte size for {produced.name}: {produced.n_bytes}")
        if produced.relative_offset != expected_offset:
            raise ValueError(f"wrong output offset for {produced.name}: {produced.relative_offset}")


def main():
    source_dir = Path(__file__).resolve().parent
    source_path = source_dir / SOURCE_NAME
    target_paths = tuple(source_dir / name for name in TARGET_NAMES)
    output_dir = source_dir / OUTPUT_DIRECTORY_NAME
    staging_dir = output_dir.with_name(output_dir.name + ".partial")
    input_paths = (source_path, *target_paths)

    if output_dir.exists() or staging_dir.exists():
        raise SystemExit(f"refusing to overwrite existing output or staging directory: {output_dir}")

    with InputLocks(input_paths):
        print("Inspecting GGUF headers...")
        source = inspect_gguf(source_path)
        targets = tuple(inspect_gguf(path) for path in target_paths)
        source_tensor, target_tensor, delta = validate_inputs(source, targets)

        expected_middle_size = targets[1].file_size + delta
        required_space = targets[0].file_size + expected_middle_size + targets[2].file_size
        free_space = shutil.disk_usage(source_dir).free
        if free_space < required_space + SPACE_MARGIN:
            raise OSError(
                f"not enough free space: need at least {(required_space + SPACE_MARGIN) / (1024**3):.1f} GiB, "
                f"found {free_space / (1024**3):.1f} GiB"
            )

        print(f"Output: {output_dir}")
        print(f"Required output space: {required_space / (1024**3):.1f} GiB")
        staging_created = False
        try:
            staging_dir.mkdir()
            staging_created = True
            staging_paths = tuple(staging_dir / name for name in TARGET_NAMES)

            copy_file_atomic(targets[0], staging_paths[0])
            rebuild_middle_shard(
                source,
                targets[1],
                source_tensor,
                target_tensor,
                delta,
                staging_paths[1],
            )
            copy_file_atomic(targets[2], staging_paths[2])

            print("Validating generated GGUF headers...")
            outputs = tuple(inspect_gguf(path) for path in staging_paths)
            if outputs[0].file_size != targets[0].file_size or outputs[2].file_size != targets[2].file_size:
                raise ValueError("an unchanged output shard has the wrong file size")
            if outputs[1].file_size != expected_middle_size:
                raise ValueError("rebuilt output shard has the wrong file size")
            validate_output_shard(outputs[1], targets[1], source_tensor, target_tensor, delta)

            del outputs
            gc.collect()
            staging_dir.rename(output_dir)
        except BaseException:
            if staging_created and staging_dir.exists():
                shutil.rmtree(staging_dir)
            raise

    print("Output headers validated successfully.")
    print(f"New model: {output_dir / TARGET_NAMES[0]}")
    return 0


if __name__ == "__main__":
    try:
        raise SystemExit(main())
    except KeyboardInterrupt:
        raise SystemExit("Cancelled by user") from None
    except (OSError, ValueError) as exc:
        raise SystemExit(f"ERROR: {exc}") from exc
```

# OpenCode Astra + Q27 3.8
```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "orchestrator": {
      "description": "Primary planning, routing, and code-review agent. Understand the user request, inspect relevant code, create a plan, split work into tasks, and delegate implementation. Do not edit files directly. Delegate all code implementation, patches, refactors, and file writes to builder. Delegate testing, runtime validation, debugging, integration checks, and independent verification to general. Use code_search for targeted read-only repository investigation when useful. After builder completes implementation and general completes testing, review the changed code yourself for correctness, regressions, architecture consistency, edge cases, and whether the implementation actually satisfies the original request. If review finds problems, send precise corrective instructions back to builder and repeat validation as needed. Keep cloud/API usage minimal.",
      "model": "openai/gpt-6-astra",
      "tools": {
        "write": false,
        "edit": false,
        "bash": false
      }
    },

    "builder": {
      "description": "Primary implementation agent. Use for code edits, patches, file writes, refactors, debugging, scripts, configuration changes, and general implementation work. This model is comparable to SOTA coding models on well-scoped, isolated core tasks, but is weaker at broad codebase-wide reasoning and long-range architectural understanding. Give it clear goals, relevant files or components when known, expected behavior, constraints, and interfaces that must be preserved. Avoid vague repo-wide tasks when possible. After completion, require a concise report of changed files, what was changed, assumptions, and unresolved risks so the orchestrator can review the result.",
    
      "mode": "subagent",
      "model": "local-vllm/Qwen3.8-27b",
      "reasoningEffort": "xhigh",
      "temperature": 1.0,
      "top_p": 0.95,
      "top_k": 20,
      "presence_penalty": 0.0,
      "frequency_penalty": 0.0,
      "repetition_penalty": 1.0,
      "min_p": 0.0,
      "permission": {
        "edit": "allow",
        "bash": "allow",
        "webfetch": "allow"
      },
      "tools": {
        "write": true,
        "edit": true,
        "bash": true
      }
    },

    "code_search": {
      "description": "Read-only repository investigation agent. Use for targeted code search, locating implementations, tracing symbols, understanding interfaces, finding call sites, identifying relevant files, and gathering context before implementation. Strong at isolated, well-scoped code investigation. Do not modify files or run commands. Give explicit search questions and targets. Return relevant file paths, symbols, relationships, findings, and uncertainties to the orchestrator.",
      "mode": "subagent",
      "model": "local-vllm/Qwen3.8-27b",
      "temperature": 0.3,
      "tools": {
        "write": false,
        "edit": false,
        "bash": false
      }
    },

    "general": {
      "description": "Independent testing, debugging, and validation agent. Use after implementation to run tests, inspect runtime behavior, reproduce bugs, validate fixes, check integrations, investigate failures, and perform cross-file reasoning when necessary. Prefer verification over implementation. Do not routinely modify source files. If testing discovers a defect, explain the failure, likely cause, affected files, reproduction steps, and recommended fix to the orchestrator; builder should perform the actual code change. General may create temporary diagnostic artifacts when necessary, but permanent implementation changes belong to builder. Report tests executed, results, failures, remaining risks, and confidence in the implementation.",
      "mode": "subagent",
      "model": "openai/gpt-5.6-terra",
      "permission": {
        "edit": "deny",
        "bash": "allow",
        "webfetch": "allow"
      },
      "tools": {
        "write": false,
        "edit": false,
        "bash": true
      }
    }
  }
}
```

# VLLM Qwen 27B 3.8 (Just remove or add flag as you like)
```bash
export VLLM_WSL2_ENABLE_PIN_MEMORY=1 

vllm serve /Qwen3.8-27B-int4-AutoRound \
  --served-model-name Qwen3.8-27b \
  --chat-template /Qwen3.8-27B/chat_template_froggeric.jinja \
  --dtype bfloat16 \
  --tensor-parallel-size 1 \
  --max-model-len 147456 \
  --gpu-memory-utilization 0.9475 \
  --max-num-seqs 1 \
  --max-num-batched-tokens 1024 \
  --long-prefill-token-threshold 1024 \
  --kv-cache-dtype fp8_e4m3 \
  --language-model-only \
  --trust-remote-code \
  --enable-prefix-caching \
  --enable-chunked-prefill \
  --mamba-cache-mode align \
  --prefix-match-unit 16 \
  --reasoning-parser qwen3 \
  --enable-auto-tool-choice \
  --tool-call-parser qwen3_coder \
  --host somethinghost \
  --port somethingport
  ```

# System Spec:
- 3090
- WSL2 Ubuntu 24.04
- 6.18.33.2-microsoft-standard-WSL2
- E5 2690v4
- 48G RAM (For WSL2), Total 96G, DDR4 2400 ECC

# Speed:
- Qwen 3.8 27B KV Q8:Q8 81920 : 30 tok/s
- Qwen 3.6 35B A3B KV Q8:Q8 180224: 75 tok/s
- DSv4 Flash KV Q8:Q8 65536: 6 tok/s

