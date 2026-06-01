---
layout: post
title: AI for biology
---

As AI (that is to say, LLM-based technology, until the current trend drastically changes) continues to mature and develop, it's interesting to think about its impact on different domains beyond software engineering. My domain is biology and certainly there have been significant developments there. Given the pace of LLM development, this post will likely remain perpetually out of date.

### Answering biomedical questions

Since the most popular implementation of AI is chatbots, it's hardly surprising that there have been many attempts to implement AI biology expert systems. [Med-PaLM and its follow-up Med-PaLM 2](https://sites.research.google/gr/med-palm/) can answer medical questions drawn from the US Medical Licensing Exam (USMLE). [Heidi](https://www.heidihealth.com/en-us/evidence) can answer clinical questions.

### Biological foundation models

Analogous to foundation large language models, there are _biological_ foundation models trained on biological sequences. Evo was trained on bacterial genomes and [Evo 2](https://github.com/arcinstitute/evo2) was trained on all domains of life. Models for more specific tasks involving DNA or protein sequences are then built upon these foundation models.

### Modeling biological processes using AI

Deep learning have been applied to H&E slides to predict mutations ([DeepPATH](https://github.com/ncoudray/DeepPATH)), molecular phenotypes ([PACpAInt](https://github.com/owkin/pacpaint)), transcriptomic levels ([HE2RNA](https://github.com/owkin/HE2RNA_code)) and patient outcomes ([MesoNet](https://pubmed.ncbi.nlm.nih.gov/31591589/)).

For histology there is [H0-mini](https://huggingface.co/bioptimus/H0-mini), a distillation of U-Optimus and M-Optimus foundational models.

Modeling cell surface receptors, such as [Trex](https://github.com/BorchLab/Trex) for T cells and [Ibex](https://github.com/BorchLab/Ibex) for B cells.

For designing mRNA sequence there is [mRNABERT](https://github.com/yyly6/mRNABERT).

For protein-ligand docking there are [DiffDock](https://github.com/gcorso/DiffDock), [IsoDDE](https://www.isomorphiclabs.com/articles/the-isomorphic-labs-drug-design-engine-unlocks-a-new-frontier), [Boltz-2](https://github.com/jwohlwend/boltz), [ESMFold](https://github.com/facebookresearch/esm).
