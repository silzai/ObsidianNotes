# Image encoder architectures
## Dubey, A., Jauhri, A., Pandey, A., Kadian, A., Al-Dahle, A., Letman, A., ... & Ganapathy, R. (2024). The llama 3 herd of models. _arXiv preprint arXiv:2407.21783_.
- ==note by me==: we read the 90 page llama paper and saw how they experimented in creating MLLMs in the following point.
- We perform a series of experiments in which we incorporate visual-recognition capabilities into Llama 3 via a compositional approach that consists of two main stages. First, we compose a pre-trained image encoder (Xu et al., 2023) and the pre-trained language model by introducing and training a set of cross-attention layers between the two models (Alayrac et al., 2022) on a large number of image-text pairs.
## Radford, A., Kim, J. W., Hallacy, C., Ramesh, A., Goh, G., Agarwal, S., ... & Sutskever, I. (2021, July). Learning transferable visual models from natural language supervision. In _International conference on machine learning_ (pp. 8748-8763). PMLR.
- CLIP-ViT performed better than CLIP-ResNet
## Xu, X., Wu, C., Rosenman, S., Lal, V., Che, W., & Duan, N. (2023, June). Bridgetower: Building bridges between encoders in vision-language representation learning. In _Proceedings of the AAAI Conference on Artificial Intelligence_ (Vol. 37, No. 9, pp. 10637-10647).
- found from the video about multi-modal rag sent by prof catal. where they used LLaVA as the LVLM (large vision language model, it uses CLIP for image encoding and LLaMA for the text (but we can integrate any LLM, it is allowable))..
- use it to embed image-caption pairs in a multi-modal semantic space
## interVL
## LLaVa
## Pixtral
## MVLM
# Non-image encoder architectures (they are all-in-one)
## SOLO
## https://www.adept.ai/blog/fuyu-8b
- On the architecture side, other multimodal models involve a separate image encoder, the output of which tends to be connected to an existing LLM via either cross-attention or through some kind of adapter that feeds directly into the LLM’s embedding-space. [PALM-e](https://arxiv.org/pdf/2303.03378.pdf), [PALI-X](https://arxiv.org/pdf/2305.18565.pdf), [QWEN-VL](https://arxiv.org/pdf/2308.12966.pdf), [LLaVA 1.5](https://arxiv.org/abs/2310.03744), and [Flamingo](https://www.deepmind.com/blog/tackling-multiple-tasks-with-a-single-visual-language-model) all look more-or-less like this. These models also tend to work on a fixed image resolution. At inference time, all images at greater resolution than this must be downsampled, and all images whose aspect ratio doesn’t match must be padded or distorted.
## Li, B., Zhang, P., Yang, J., Zhang, Y., Pu, F., & Liu, Z. (2023). Otterhd: A high-resolution multi-modality model. _arXiv preprint arXiv:2311.04219_.
- Building upon Fuyu, we introduce OtterHD-8B, an advanced instruction-tuned model to handle larger and various image resolutions. OtterHD-8B is open-sourced and the instruction tuning process is specifically designed to accommodate a wide range of image resolutions up to 1024×1024 pixels. Such elasticity allows users to choose the input resolution given their inference budget and task nature.
- Our OtterHD-8B is a model instruction-tuned from Fuyu-8B, aiming at examining the impact of increasing resolutions on the performance of downstream tasks.
- Our work is motivated by the Fuyu-8B model [5], which elegantly sidesteps these limitations by removing the vision encoder altogether and directly incorporating pixel-level information into the language decoder. The model leverages its native position embeddings to comprehend different image sizes, obviating the need for separate high and low-resolution training stages as seen in the PaLI series.
# recommendation by chatgpt-4o
- **If symptoms are localized** (e.g., visible spots, lesions, or discoloration confined to certain areas of the plant), and you need to know both **where** and **what** the disease is, use **YOLO**. YOLO’s object detection capabilities will help you detect these regions and classify them.
- **If the symptoms are diffuse or spread across the entire plant** (e.g., general discoloration, wilting, or texture changes), and your primary goal is to classify the disease, use a **Vision Transformer (ViT)**. ViT will handle the task well by capturing global patterns across the image for classification.
# past related sdp project
- Project ID = SDP2324 CS F 29