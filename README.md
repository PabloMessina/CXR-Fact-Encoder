# CXR-Fact-Encoder

This the official main repository for the paper [Extracting and Encoding: Leveraging Large Language Models and Medical Knowledge to Enhance Radiological Text Representation](https://arxiv.org/abs/2407.01948) accepted at Findings of ACL 2024.

[Presentation Video](https://youtu.be/Hh1Avz-Dkfs)

[Slides](https://docs.google.com/presentation/d/1ztuO_PwfHrWFvjeKC4aDrdvl2yiCAk1BcLQtSq7hhfY/edit?usp=sharing)

[Poster](https://drive.google.com/file/d/1cMgEzYDtipbl4Mrdpv0Hr86l1E5J36QV/view?usp=sharing)

## Abstract

Advancing representation learning in specialized fields like medicine remains challenging due to the scarcity of expert annotations for text and images. To tackle this issue, we present a novel two-stage framework designed to extract high-quality factual statements from free-text radiology reports in order to improve the representations of text encoders and, consequently, their performance on various downstream tasks. In the first stage, we propose a *Fact Extractor* that leverages large language models (LLMs) to identify factual statements from well-curated domain-specific datasets. In the second stage, we introduce a *Fact Encoder* (CXRFE) based on a BERT model fine-tuned with objective functions designed to improve its representations using the extracted factual data. Our framework also includes a new embedding-based metric (CXRFEScore) for evaluating chest X-ray text generation systems, leveraging both stages of our approach. Extensive evaluations show that our fact extractor and encoder outperform current state-of-the-art methods in tasks such as sentence ranking, natural language inference, and label extraction from radiology reports. Additionally, our metric proves to be more robust and effective than existing metrics commonly used in the radiology report generation literature.

## Fact Extraction

![Imgur](https://imgur.com/1kYUht6)

Pretrained T5 Fact Extractor model available on HuggingFace: https://huggingface.co/pamessina/T5FactExtractor

## Fact Encoding

Pretrained Fact Encoder model (CXRFE) available on HuggingFace: https://huggingface.co/pamessina/CXRFE

## CXRFEScore

![Imgur](https://imgur.com/UZDBRgs)

## TODO

- [ ] Publish CXRFEScore as a pip package on PyPi. (NOTE: We are working on it right now. In the meantime, feel free to play around with a prototype version available on Google Colab [here](https://colab.research.google.com/drive/1L0D5eWlVr2NNau5Hd9O38UaFOgDD8c8a))
- [ ] Publish all the data used in the paper on PhysioNet: https://physionet.org/
- [ ] Publish training scripts for the Fact Extractor and Fact Encoder models. (NOTE: Technically, all the code is already available in my PhD thesis repository [here](https://github.com/PabloMessina/MedVQA). However, that repository includes way too many things beyond the scope of this paper, so I'm planning to release a more focused version of the code here in the near future.)
- [ ] Release multiple pretrained versions of CXR Fact Encoder (CXRFE) on HuggingFace matching the description in the paper. (NOTE: Right now you can use https://huggingface.co/pamessina/CXRFE, which is a version trained with slightly more NLI data than the best model in the paper. I'm planning to release the exact models from the paper soon.)

