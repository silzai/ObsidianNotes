```mermaid
graph LR
    User[User Input (Mobile App)]
    Gateway[API Gateway]
    Embed[Query Embedding Service]
    VectorSearch[Vector Search Service]
    VectorDB[Vector Database]
    LLM[LLM Inference Service]
    Response[Response Delivery Service]

    User -->|Text/Image Query| Gateway
    Gateway --> Embed
    Embed --> VectorSearch
    VectorSearch --> VectorDB
    VectorDB --> VectorSearch
    VectorSearch --> LLM
    LLM --> Response
    Response -->|Generated Response| User
```