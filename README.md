# llm-training-data-eval
Example code for the demonstration conducted in "Third-party evaluation to identify risks in LLMs’ training data".

This is composed of two notebooks, `AI_Owner` and `Researcher`, wearing the two hats of the personas involved:
- The represenative of a fictionary AI Lab that manages the private data and the AI Lab's infrastructure for private access running PySyft
- A third-party evaluator who would like to do AI Safety research

We will jump between the two notebooks as we illustrate the flow and this approach to address the external access problem.

## What is the external access problem?
Meaningful research on AI systems sometimes require access to proprietary AI models and datasets. Conventional approaches to giving external access typically are:
   - *Open Access*: requires revealing the data
   - *Onsite Access*: storing the assets in a secured facility, and have researchers travel to conduct their study in-person, which is limited to the time spent on-site and expensive
   - *API Access*: restricted to pre-defined APIs and difficult to expand due to the risk of data/assets being extracted

Third-party access for researchers to study proprietary LLMs are typically denied due to **competitive, trust & safety, security, privacy, and legal concerns**, resulting in limited means to address, or even identify, AI safety issues. As a result, answering questions like the one below is difficult.

**Does the model's knowledge include the creation of pathogens and deadly chemicals?**

PySyft proposes a paradigm where a third-party researchers can answer approved questions, whilst the private assets never leave the premises of the AI Lab. To ensure security, we will be using an air-gapped deployment composed of two servers:
- Low-side: can be accessed by the researchers. However, it does not store any private assets, but fake counterparts that "mimic" the private assets.
- High-side: a server inside the internal AI Lab's network that contains the private assets. The private assets cannot be accessed by any outside parties.

A representative of the AI Lab is responsible for reviewing, approving and forwarding computational results back from high side to low side.

![image-2.png](attachment:image-2.png)

## Pre-requisites

To run this tutorial, you will need to install PySyft as follows

```bash
pip install syft==0.9.1
```