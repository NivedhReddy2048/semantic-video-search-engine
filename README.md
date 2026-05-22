# 🎬 Full-Stack AI Semantic Video Search

## An end-to-end, multimodal AI search engine that allows users to upload any video, dynamically index its frames, and search for specific moments using natural language queries—with zero manual tagging required.

## **🔴 Live Demo:** [Click here to test the app](https://huggingface.co/spaces/NivedhReddy/semantic-video-search)  
### *(Note: Running on a free CPU tier, processing new videos takes ~2 minutes)*

![App Screenshot](https://github.com/NivedhReddy2048/semantic-video-search-engine/blob/main/User_Interface.png?raw=true)

## 🧠 The Problem & Solution
## Traditional video search relies on humans manually watching footage and typing out metadata tags (e.g., "0:25 - Dog appears"). 

## This project completely automates that pipeline using **Generative AI and Vector Databases**. By converting video frames and user text into high-dimensional mathematical vectors (embeddings), the engine calculates the cosine similarity between the visual data and the text query, instantly pinpointing the exact timestamp of the requested action.

## ⚙️ Tech Stack
### **Computer Vision:** `OpenCV` (for dynamic frame extraction and processing).
### **AI/Embeddings:** OpenAI CLIP (`clip-vit-base-patch32`) via Hugging Face `transformers`.
### **Vector Database:** `Qdrant` (In-Memory) for high-dimensional vector storage and similarity search.
### **Frontend/UI:** `Gradio` (Blocks API) for a responsive, two-column SaaS-style web interface.
### **Framework:** `PyTorch`.

## ✨ Key Engineering Features
### 1. **Dynamic Processing Pipeline:** Users can upload any `.mp4`. The backend automatically wipes the database, extracts frames at 1 FPS, generates fresh tensor embeddings, and indexes them on the fly.
### 2. **Multimodal Search:** Maps text queries to image data using a shared 512-dimensional embedding space.
### 3. **Algorithmic Confidence Thresholding:** Implemented threshold logic (`score < 0.22`) to prevent the AI from returning hallucinated results when a requested item does not actually exist in the video.
### 4. **Instant Visual Feedback:** Extracts and serves the exact matching RGB frame back to the UI, proving the model's accuracy to the user.

## 🚀 How It Works Under the Hood
### 1. **Extraction:** OpenCV reads the video stream and pulls one frame per second to balance compute load and accuracy.
### 2. **Vectorization:** The CLIP vision encoder evaluates the RGB frames and converts them into mathematical vectors.
### 3. **Indexing:** Vectors are stored in a Qdrant collection alongside their timestamp payload.
### 4. **Querying:** The CLIP text encoder converts the user's natural language input into a vector. Qdrant performs a cosine similarity search to find the closest visual match in the database.

## 💻 Run It Locally
### Want to test the code on your own machine? 

## 1. Clone the repository:
   ```bash
   git clone [https://github.com/NivedhReddy2048/semantic-video-search-engine](https://github.com/NivedhReddy2048/semantic-video-search-engine)

```

## 2. Install the required dependencies:
```bash
pip install gradio opencv-python torch transformers qdrant-client Pillow

```


## 3. Run the application:
```bash
python app.py

