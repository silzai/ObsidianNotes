
# 1) Bot Detection for Arabic Social Media
# Introduction
This project aims to develop a bot detection system specifically for Arabic social media platforms. Our research unit is creating an Arabic Social Media Index to analyze trends, patterns, and extract information from Arabic social media spaces. To achieve this, we have established a data collection framework targeting various entities in the Arab world, such as universities, hospitals, NGOs, syndicates, and more, across different social media platforms. Given the importance of data integrity, our objective is to identify and manage bot-generated content effectively. Detecting bots within our collected data will enhance the quality and reliability of our Arabic Social Media Index.
## Previous Work
There are various existing tools and datasets in the literature on bot-detection. Botometer, for example, is a widely used tool that assesses the likelihood of a Twitter account being a bot. Additionally, bot-detection datasets like the TwiBot datasets provide extensive labeled data for training and evaluating bot detection models. Common features used in these datasets include account metadata, posts content, and network interactions features. Both traditional machine learning models, such as Random Forests, and advanced deep learning methods, like Graph Convolutional Networks, have been employed in bot-detection before.
## Objectives
1. Investigate existing datasets, identify those including Arabic social media accounts, and compile a comprehensive dataset.
2. Identify and select features to use for the model.
3. Develop the bot detection model using the selected features.
4. Evaluate the model's performance and validate its effectiveness using appropriate metrics and validation techniques.
5. Integrate this bot detection module into our existing data collection framework.
# 2) Contributing towards Arabic data processing modules
## Introduction
Our research unit is dedicated to developing a comprehensive data processing tool for Arabic text. This tool encompasses multiple pre-processing submodules designed for various applications, including training datasets. Our goal is to enhance each submodule individually, integrate them into a CLI tool, and release it as an open-source project.
## Current Progress
We have successfully implemented and the following modules:
- Deduplication across documents
- Readability Analysis with two implemented metrics (OSMAN and FLESCH)
- Ranking based on metrics
- Quality Checking
- Light Stemming
- Tokenization
- Splitting
## Objectives
- Re-write the Readability Analysis module in Rust/Python.
- Re-write the Deduplication module in Rust/Python.
- Merge Quality Checking with Light Stemming functionalities to adhere to the DRY principle.
- Implement global hashmap checkpointing in Deduplication.
- Establish robust logging levels for each module.
- Develop a general CLI module to interface across data processing steps.
# 3) Benchmarking Large Language Models for Arabic on multiple subjects/topics (Up to 3 members to assign)
- there will be a benchmark for cultural alignments of different topics like history, plitics or geography
- intern will create a benchmark to test
# 4) Task Orchestrator across Linux Environments
- parallel across linux machines
- in the Arabic social media index, data collection -> data extraction -> visualization
- for the data collection: 
	- will crawl manually by executing the scripts
	- task orchestrator will handle by 
- data extraction:
	- given a data source, will write process to aggregate the data and execute tasks on them
- visualization:
# 5) Crawling historical social media data from Internet archives
## Introduction
This is a new project where you will be developing a robust system for scraping social media data from internet archives, ensuring the process is efficient, maintainable, and well-documented.
## Objectives
- Research and list the possible archives to scrape social media data from. Some examples are:
	- [Wayback Machine](https://wayback-api.archive.org/)
	-  [archive.today](https://archive.ph/)
- Evaluate the list on some criteria, such as:
	- Data completeness
	- Accessibility
	- Frequency of updates
	- Legal considerations
- Write clean and reusable code to accommodate our needs in the future.
- Document all the steps and methodologies you used to choose the archives and scrape the data.
# 6) Creating Mastodon Bots Powered by LLM with RAG
## Introduction  
This project aims to develop Mastodon bots that utilize a Language Model (LLM) integrated with a Retrieval-Augmented Generation (RAG) system. The primary goal is to feed the LLM and RAG system with the works of a specific author to create a bot that can answer questions about the author and their literature. This will provide users with an interactive way to explore and learn about various authors and their contributions to literature.
## Available Resources.
Currently at our disposal is a comprehensive collection of digitized books by selected authors.
## Objectives
Our objective is to make literature more accessible and engaging by leveraging the power of LLMs and RAG systems.
- Preprocess, clean the data
- Create a module to ingest the author's works and related content.
- Train the LLM to understand and generate responses based on the author's literature.
- Implement the RAG System to retrieve relevant information from the database.
- Build the Mastodon Bot Framework: Develop a framework to use and manage Mastodon bots.
# 7) "Waseet": WhatsApp bot to provide services.