# CXR-Fact-Encoder

[![Paper](https://img.shields.io/badge/ACL-Findings%202024-b31b1b.svg)](https://aclanthology.org/2024.findings-acl.236/)
[![arXiv](https://img.shields.io/badge/arXiv-2407.01948-b31b1b.svg)](https://arxiv.org/abs/2407.01948)
[![PyPI](https://img.shields.io/pypi/v/cxrfescore.svg)](https://pypi.org/project/cxrfescore/)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/PabloMessina/CXR-Fact-Encoder/blob/main/notebooks/cxrfescore_demo.ipynb)
[![Hugging Face — CXRFE](https://img.shields.io/badge/HuggingFace-CXRFE-yellow?logo=huggingface)](https://huggingface.co/pamessina/CXRFE)
[![Presentation](https://img.shields.io/badge/YouTube-Presentation-FF0000?logo=youtube)](https://youtu.be/Hh1Avz-Dkfs)
[![Slides](https://img.shields.io/badge/Google-Slides-F4B400?logo=googledrive)](https://docs.google.com/presentation/d/1ztuO_PwfHrWFvjeKC4aDrdvl2yiCAk1BcLQtSq7hhfY/edit?usp=sharing)
[![Poster](https://img.shields.io/badge/Google-Poster-0F9D58?logo=googledrive)](https://drive.google.com/file/d/1cMgEzYDtipbl4Mrdpv0Hr86l1E5J36QV/view?usp=sharing)

**Official companion repository for the paper** [*Extracting and Encoding: Leveraging Large Language Models and Medical Knowledge to Enhance Radiological Text Representation*](https://aclanthology.org/2024.findings-acl.236/) (Findings of ACL 2024).

This repo is the **paper hub**: models, metric demos, and links. The installable CXRFEScore metric lives in a separate package:

- **Package repo:** [PabloMessina/CXRFEScore](https://github.com/PabloMessina/CXRFEScore)
- **PyPI:** [`pip install cxrfescore`](https://pypi.org/project/cxrfescore/)

## Abstract

Advancing representation learning in specialized fields like medicine remains challenging due to the scarcity of expert annotations for text and images. To tackle this issue, we present a novel two-stage framework designed to extract high-quality factual statements from free-text radiology reports in order to improve the representations of text encoders and, consequently, their performance on various downstream tasks. In the first stage, we propose a *Fact Extractor* that leverages large language models (LLMs) to identify factual statements from well-curated domain-specific datasets. In the second stage, we introduce a *Fact Encoder* (CXRFE) based on a BERT model fine-tuned with objective functions designed to improve its representations using the extracted factual data. Our framework also includes a new embedding-based metric (CXRFEScore) for evaluating chest X-ray text generation systems, leveraging both stages of our approach. Extensive evaluations show that our fact extractor and encoder outperform current state-of-the-art methods in tasks such as sentence ranking, natural language inference, and label extraction from radiology reports. Additionally, our metric proves to be more robust and effective than existing metrics commonly used in the radiology report generation literature.

## Highlights

- **Findings of ACL 2024:** fact extraction + fact encoding for radiological text representation, plus CXRFEScore for report generation evaluation.
- **Pretrained models on Hugging Face:** [T5 Fact Extractor](https://huggingface.co/pamessina/T5FactExtractor) and [CXRFE](https://huggingface.co/pamessina/CXRFE).
- **CXRFEScore on PyPI:** `pip install cxrfescore` — see the [package README](https://github.com/PabloMessina/CXRFEScore) for API, caching, and supported encoders.
- **Interactive demo:** [notebooks/cxrfescore_demo.ipynb](notebooks/cxrfescore_demo.ipynb) (local Jupyter or [Open in Colab](https://colab.research.google.com/github/PabloMessina/CXR-Fact-Encoder/blob/main/notebooks/cxrfescore_demo.ipynb)).

## Fact Extraction

![Fact extraction overview](https://github.com/user-attachments/assets/cdcbd036-27dd-49dd-823b-dcdc14386ca9)

Pretrained T5 Fact Extractor: [`pamessina/T5FactExtractor`](https://huggingface.co/pamessina/T5FactExtractor)

## Fact Encoding

Pretrained Fact Encoder (CXRFE): [`pamessina/CXRFE`](https://huggingface.co/pamessina/CXRFE)

## CXRFEScore

![CXRFEScore overview](https://github.com/user-attachments/assets/00ab2361-0315-42f5-a211-a8559c98cb8b)

CXRFEScore extracts factual statements from reports, embeds them with CXRFE (or compatible CXR-BERT encoders), and scores hypothesis/reference pairs via soft bipartite matching of fact embeddings.

### Install

```bash
pip install cxrfescore
```

Optional visualization support:

```bash
pip install "cxrfescore[viz]"
```

### Quick start

```python
from cxrfescore import CXRFEScore

metric = CXRFEScore(device="cuda")  # or "cpu"
result = metric(hypotheses, references)
print(result["mean_similarity"])
print(result["per_pair_similarity"])
```

### Demo notebook

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/PabloMessina/CXR-Fact-Encoder/blob/main/notebooks/cxrfescore_demo.ipynb)

The notebook covers scoring, adversarial pairs, `extract_facts` / `embed_facts`, caching, fact-similarity heatmaps, and a side-by-side CXRFE vs SRR-BERT-Leaves visualization.

- Full API docs & examples: https://github.com/PabloMessina/CXRFEScore  
- PyPI: https://pypi.org/project/cxrfescore/  
- Paper: https://aclanthology.org/2024.findings-acl.236/

## Citation

If you use this work or CXRFEScore, please cite:

> Pablo Messina, Rene Vidal, Denis Parra, Alvaro Soto, and Vladimir Araujo. 2024. [Extracting and Encoding: Leveraging Large Language Models and Medical Knowledge to Enhance Radiological Text Representation](https://aclanthology.org/2024.findings-acl.236/). In *Findings of the Association for Computational Linguistics: ACL 2024*, pages 3955–3986, Bangkok, Thailand. Association for Computational Linguistics.

```bibtex
@inproceedings{messina-etal-2024-extracting,
    title = "Extracting and Encoding: Leveraging Large Language Models and Medical Knowledge to Enhance Radiological Text Representation",
    author = "Messina, Pablo  and
      Vidal, Rene  and
      Parra, Denis  and
      Soto, Alvaro  and
      Araujo, Vladimir",
    editor = "Ku, Lun-Wei  and
      Martins, Andre  and
      Srikumar, Vivek",
    booktitle = "Findings of the Association for Computational Linguistics: ACL 2024",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.findings-acl.236/",
    doi = "10.18653/v1/2024.findings-acl.236",
    pages = "3955--3986"
}
```

Paper: [ACL Anthology](https://aclanthology.org/2024.findings-acl.236/) · [PDF](https://aclanthology.org/2024.findings-acl.236.pdf) · [arXiv](https://arxiv.org/abs/2407.01948)

## TODO

- [x] Publish CXRFEScore as a pip package on PyPI — [`cxrfescore`](https://pypi.org/project/cxrfescore/) · [package repo](https://github.com/PabloMessina/CXRFEScore)
- [ ] Publish all the data used in the paper on PhysioNet: https://physionet.org/
- [ ] Publish training scripts for the Fact Extractor and Fact Encoder models. (NOTE: Technically, all the code is already available in my PhD thesis repository [here](https://github.com/PabloMessina/MedVQA). However, that repository includes way too many things beyond the scope of this paper, so I'm planning to release a more focused version of the code here in the near future.)
- [ ] Release multiple pretrained versions of CXR Fact Encoder (CXRFE) on HuggingFace matching the description in the paper. (NOTE: Right now you can use https://huggingface.co/pamessina/CXRFE, which is a version trained with slightly more NLI data than the best model in the paper. I'm planning to release the exact variants of CXRFE from the paper soon.)
- [ ] Improve documentation of released models on HuggingFace.
