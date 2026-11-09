# Multimodal Evaluation Lab

A framework for comparing multimodal embedding models across image classification, image retrieval, visual question answering, and visual grounding tasks.

## Project status

**Current:** Small pilot comparison of CLIP ViT-B/32 and Qwen3-VL-Embedding-2B using MMEB task categories.

**Next:** Expand the sample size, standardize model input protocols where possible, add repeatable task-specific metrics, and track experiment configurations. The framework and expanded benchmark are planned work.

## Research questions

- Where do dual-encoder and MLLM-based embedding approaches behave differently?
- How do visual-text alignment, OCR, compositional understanding, and spatial grounding affect task performance?
- Which failure modes are specific to a model, task, or evaluation setup?

## Initial pilot

The notebook records 10 queries per category and 50 candidates per query.

| Task category | CLIP | Qwen3-VL |
|---|---:|---:|
| Image classification | 8/10 | 10/10 |
| Image retrieval | 8/10 | 10/10 |
| Document VQA | 1/10 | 10/10 |
| Visual grounding | 9/10 | 10/10 |

These are pilot observations, not benchmark-wide scores or statistically conclusive comparisons. The models' input interfaces differ, so comparisons must document the exact inputs and scoring protocol.

## Planned architecture

```text
MMEB task datasets
    -> dataset adapters
    -> standardized model adapters
    -> embedding/inference runner
    -> task-specific metrics
    -> experiment tracking
    -> failure-case analysis
    -> comparison report
```

## Repository layout

```text
configs/              Model, dataset, and experiment configurations
docs/                 Evaluation protocol and architecture notes
src/models/           CLIP and MLLM model adapters
src/datasets/         MMEB task loaders and preprocessing
src/metrics/          Task-specific metrics
src/runners/          Reproducible evaluation orchestration
src/analysis/         Aggregate analysis and visualizations
experiments/          Experiment manifests and results
failure_cases/        Curated examples and error taxonomy
reports/              Generated evaluation reports
tests/                Adapter, metric, and data validation tests
```

## Planned evaluation improvements

1. Increase query counts beyond the initial 10 examples per category.
2. Document candidate construction, positive labels, and model-specific input formats.
3. Separate classification, retrieval, VQA, and grounding metrics.
4. Add repeated runs or confidence intervals where appropriate.
5. Categorize failures such as fine-grained visual confusion, OCR, compositional mismatch, spatial grounding, and semantic mismatch.
6. Track model revisions, preprocessing, prompt templates, hardware, and inference settings.

## Models and dataset

- Dataset: [TIGER-Lab/MMEB-eval](https://huggingface.co/datasets/TIGER-Lab/MMEB-eval)
- Baseline dual encoder: [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32)
- MLLM-based embedder: [Qwen/Qwen3-VL-Embedding-2B](https://huggingface.co/Qwen/Qwen3-VL-Embedding-2B)

## Scope

This project evaluates pretrained embedding models; it does not claim to train or fine-tune either model. Keep model comparison claims tied to the documented sample and evaluation protocol.
