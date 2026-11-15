# Controlled Industrial Product Design Generation using Stable Diffusion and LLM Prompting

## Overview

This project explores how Large Language Models (LLMs) and controlled
text-to-image generation can turn an industrial component specification
into a presentation-ready **2D product mockup**.

Instead of sending raw engineering specifications directly to an
image-generation model, the system first interprets the specification,
converts it into structured information and visual descriptions,
prepares prompts, and uses an automatically generated outline to guide
image generation.

## Problem Statement

Creating industrial product visuals from specification sheets can
require manual sketching and repeated prompt adjustments. A
text-to-image model may produce an attractive image but fail to
represent important component details such as rings, holes, feature
arrangement, or proportions. The result can also depend heavily on the
user's prompt-writing skill.

## Project Objectives

-   Parse free-text industrial product specifications into structured
    data.
-   Convert dimensions and component features into visual descriptions.
-   Generate positive and negative prompts suitable for product-style
    images.
-   Create a simplified parametric outline from the parsed component
    information.
-   Guide image generation using Stable Diffusion and ControlNet.
-   Evaluate generated images and refine prompts when important features
    are missing.

## How the System Works

1.  **Specification input** -- The user provides the component type,
    dimensions, material, and required features.
2.  **LLM specification parsing** -- An instruction-following language
    model extracts the specification into structured fields.
3.  **Layout and prompt generation** -- The system plans visible
    component features and creates positive and negative prompts.
    Numeric dimensions are translated into visual proportions where
    appropriate.
4.  **Outline rendering** -- A simplified parametric drawing represents
    features such as rings and holes. The drawing is converted into an
    edge map.
5.  **Controlled image generation** -- Stable Diffusion generates the
    image, while ControlNet uses the edge map as structural guidance.
6.  **Evaluation and refinement** -- Image-text similarity and feature
    checks help identify possible mismatches. The prompt or layout can
    be refined and the image regenerated.

## Technologies Used

-   **Python** -- Main implementation language
-   **Google Colab** -- Notebook-based development and execution
-   **Hugging Face Transformers** -- Loading and running the language
    model
-   **Qwen2.5-1.5B-Instruct** -- Specification interpretation and prompt
    assistance
-   **Stable Diffusion 1.5** -- Text-to-image generation
-   **ControlNet (Canny)** -- Structural guidance using an edge map
-   **OpenCV / PIL** -- Image and outline processing
-   **CLIP** -- Image-text similarity evaluation

> Exact package versions and runtime requirements should be taken from
> the notebook environment used for the project.

## Example

**Input specification:** 6204 deep-groove ball bearing, steel, sealed;
bore 20 mm, outer diameter 47 mm, width 14 mm, chrome finish.

The system interprets the specification, prepares a
product-catalog-style prompt, creates a simplified outline, and uses
that outline to guide the generated image.

## Repository Structure

A suggested repository structure is:

``` text
project/
├── IP_LLM.ipynb
├── README.md
└── requirements.txt
```

Add other files or folders (such as sample specifications, generated
images, or helper scripts) if they exist in your repository.

## How to Run

1.  Open `IP_LLM.ipynb` in Google Colab.
2.  Select a runtime with GPU support if available.
3.  Run the notebook cells in order.
4.  Install any dependencies requested by the notebook.
5.  Provide an industrial component specification when prompted.
6.  Review the generated prompts, outline, image, and evaluation output.

The notebook is the main implementation entry point. Some stages,
especially Stable Diffusion and ControlNet generation, require
substantial memory and may run slowly without a suitable GPU.

## Scope and Limitations

-   The output is a **2D concept/mockup image**, not a CAD model or
    manufacturing drawing.
-   Visual proportions are approximate; the image generator does not
    guarantee exact dimensional accuracy.
-   Similarity scores and automated feature checks are indicators, not
    proof that every engineering requirement is satisfied.
-   Final engineering decisions must be verified against the original
    specification and appropriate CAD or engineering tools.

## Future Improvements

-   Add a user-friendly Gradio or Streamlit interface.
-   Expand the component dataset and feature templates.
-   Improve feature detection and dimensional consistency checks.
-   Compare raw prompts, LLM-engineered prompts, and outline-guided
    generation systematically.
-   Add reference-image comparison and human evaluation.

## Team

Project team: **Pavan, Vilas, Vivek, and Meharajuddin**

Department: **Artificial Intelligence and Machine Learning (AIML)**

Guide: **Prof. Chetana Shrinivasan**

------------------------------------------------------------------------

*This repository contains an academic project prototype for
specification-guided industrial product mockup generation.*
