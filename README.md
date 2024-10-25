

---

# 📹 **MultiModal RAG App for Video Processing With LlamaIndex and LanceDB**

## Introduction

Welcome to the **MultiModal RAG App**! In a world where video content is increasingly prevalent, understanding and extracting valuable information from these resources can be challenging. This application addresses that challenge by providing a streamlined way to derive insights from videos.

The **MultiModal RAG App** combines video processing techniques with advanced natural language processing capabilities to offer users a comprehensive tool for analyzing video content. Here’s what you can do with this app:

- **📥 Download Videos:** Easily retrieve video content from platforms like YouTube, making it simple to work with your preferred material.
  
- **🎤 Audio Extraction and Transcription:** Convert the audio track of the video into text using OpenAI’s Whisper, allowing you to capture spoken content accurately and efficiently.

- **🖼️ Image Generation:** Extract images from video frames, providing visual context that complements the textual information.

- **📂 Multimodal Indexing:** Organize and store the extracted data into a multimodal index. This index enables users to manage and retrieve information effectively, enhancing the overall usability of the application.

- **❓ Intelligent Querying:** By leveraging OpenAI's large language model (LLM), users can pose questions related to the video content. The app retrieves relevant information and images from the multimodal index, offering precise and contextual answers.

---

## 🛠️ Setup Instructions

To get started with the **MultiModal RAG App**, follow these steps:

1. **🔧 Install Required Libraries**: Ensure you have Python installed and run the following commands to install the necessary packages:

   ```bash
   %pip install llama-index-vector-stores-lancedb
   %pip install llama-index-multi-modal-llms-openai
   %pip install llama-index-embeddings-clip
   %pip install git+https://github.com/openai/CLIP.git
   !pip install llama-index-readers-file
   %pip install llama_index
   %pip install -U openai-whisper
   %pip install lancedb
   %pip install moviepy
   %pip install pytube
   %pip install pydub
   %pip install SpeechRecognition
   %pip install ffmpeg-python
   %pip install soundfile
   %pip install torch torchvision
   %pip install matplotlib scikit-image
   %pip install ftfy regex tqdm
   ```

2. **🔑 Set Up OpenAI API Key**: Obtain your OpenAI API key and set it in your environment. You can do this by adding the following line to your script:

   ```python
   os.environ["OPENAI_API_KEY"] = "your_api_key_here"
   ```

3. **▶️ Run the Application**: Once you have everything installed and your API key set up, you can start using the app to download videos, extract data, and query the multimodal index.

---

## ⚙️ Technologies Used

The **MultiModal RAG App** utilizes the following technologies to provide its functionality:

- **📚 LlamaIndex**: A framework for indexing and retrieving multimodal data efficiently.
- **📊 LanceDB**: A vector database for storing and managing extracted data.
- **🎙️ OpenAI Whisper**: An automatic speech recognition (ASR) model that transcribes audio into text.
- **🎥 MoviePy**: A Python library for video editing that facilitates audio and frame extraction.
- **📥 Pytube**: A lightweight library for downloading videos from YouTube.
- **🤖 OpenAI GPT-4**: A powerful language model used for generating contextual answers based on the extracted information.

---


---

## ✨ Multimodal Indexing

```python
text_store = LanceDBVectorStore(uri="lancedb", table_name="text_collection")
image_store = LanceDBVectorStore(uri="lancedb", table_name="image_collection")
storage_context = StorageContext.from_defaults(vector_store=text_store, image_store=image_store)
documents = SimpleDirectoryReader(output_folder).load_data()
index = MultiModalVectorStoreIndex.from_documents(documents, storage_context=storage_context)
```

### Heres how its working:

1. **LanceDB Vector Store Initialization for Text**:
   - `text_store = LanceDBVectorStore(uri="lancedb", table_name="text_collection")`
   - Initializes a vector store specifically for text data extracted from the video, providing a structured way to store and retrieve text information.

2. **LanceDB Vector Store Initialization for Images**:
   - `image_store = LanceDBVectorStore(uri="lancedb", table_name="image_collection")`
   - Initializes a vector store for image data, ensuring that extracted images are managed separately from text data.

3. **Creating the Storage Context**:
   - `storage_context = StorageContext.from_defaults(vector_store=text_store, image_store=image_store)`
   - Establishes a storage context that integrates both the text and image stores, allowing for efficient access and management of multimodal data.

4. **Loading Documents**:
   - `documents = SimpleDirectoryReader(output_folder).load_data()`
   - Uses a `SimpleDirectoryReader` to load all documents (text files and images) from the specified output folder where they were stored after processing the video.

5. **Creating the Multimodal Index**:
   - `index = MultiModalVectorStoreIndex.from_documents(documents, storage_context=storage_context)`
   - Constructs a multimodal index using the loaded documents and the storage context, organizing both text and image data for quick and efficient retrieval based on user queries.

--- 

## Result 📥 
In the below screenshot, you can see the retrieval part where the textual context outputs wiht image outputs from the user's query can be seen. The screenshots demonstrate how the relevant parts of the video are showcased as output:

![image](https://github.com/user-attachments/assets/53d355e8-ffb1-4766-8a2e-93b90ee79fac)

---

## Author 🧑‍💻

**Aditya Sagar**  
[![LinkedIn Logo](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/adityasagarr)  

---
