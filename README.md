# **Real-Time AI Translation Overlay for On-Screen Content**

A real-time, on-device translation system that overlays translations directly onto screen content, eliminating the need to switch apps or use disruptive tools. This project leverages on-device OCR and NMT to provide seamless, private, and context-aware translations across any application.

## **📖 Table of Contents**

* [Problem Statement](https://www.google.com/search?q=%23-problem-statement)  
* [✨ Key Features](https://www.google.com/search?q=%23-key-features)  
* [⚙️ How It Works](https://www.google.com/search?q=%23%EF%B8%8F-how-it-works)  
* [🛠️ Technology Stack](https://www.google.com/search?q=%23%EF%B8%8F-technology-stack)  
* [📊 Performance Metrics](https://www.google.com/search?q=%23-performance-metrics)  
* [🚀 Future Work](https://www.google.com/search?q=%23-future-work)  
* [👥 Authors](https://www.google.com/search?q=%23-authors)  
* [🔗 Project Links](https://www.google.com/search?q=%23-project-links)

## **🎯 Problem Statement**

In an increasingly multilingual digital world, users face significant friction when encountering foreign languages. Conventional translation tools disrupt user workflows by forcing context switches—opening separate apps, taking screenshots, or using camera-based solutions that don't work for on-screen text. This project addresses these gaps by providing an end-to-end translation overlay that operates directly on the user's display, offering instantaneous translations without network dependency, while preserving user privacy and the original application's look-and-feel.

## **✨ Key Features**

* **Screen-Capture-First Pipeline**: Directly captures the device display, ensuring compatibility with all applications, system UIs, and even protected video streams.  
* **On-Device, Low-Latency Processing**: Utilizes lightweight, TFLite-optimized models for both OCR and Neural Machine Translation (NMT), achieving sub-600 ms end-to-end latency without relying on the cloud.  
* **Adaptive UI & Typography**:  
  * **Layout Mirroring**: Automatically adjusts layouts for right-to-left (RTL) scripts like Arabic and Hebrew to ensure a natural reading experience.  
  * **Dynamic Styling**: Samples the background color and typography of the source text to apply matching font size, weight, and color to the overlay, preserving the original UI's aesthetics.  
* **Privacy by Design**: All processing, including screen capture, OCR, and translation, occurs entirely on the user's device. No data is ever sent to external servers.  
* **Broad Language Support**: Supports over 50 languages for translation, including both Left-to-Right (LTR) and Right-to-Left (RTL) scripts.

## **⚙️ How It Works**

The system operates in a continuous, real-time pipeline:

1. **Screen Capture**: The Android MediaProjection API captures the screen content as a series of frames.  
2. **Text Recognition (OCR)**: Each frame is passed to an on-device TensorFlow Lite model (google\_mlkit\_text\_recognition) which detects text and extracts it along with its bounding box coordinates.  
3. **Text Translation (NMT)**: The extracted text is sent to a lightweight, on-device translation model (google\_mlkit\_translate) which returns the translated text.  
4. **UI Adaptation**: A custom module analyzes the source text's styling (font, color) and layout direction (LTR/RTL) to prepare the translated text for rendering.  
5. **Overlay Rendering**: The styled, translated text is rendered on the screen directly over the original text's location using flutter\_overlay\_window, creating a seamless and non-intrusive experience.

This entire process repeats at a configurable interval to balance responsiveness and performance.

## **🛠️ Technology Stack**

* **Framework**: Flutter  
* **Native Development**: Kotlin (for Android-specific APIs)  
* **Screen Capture**: Android MediaProjection API  
* **Machine Learning**:  
  * **OCR**: Google ML Kit Text Recognition (TFLite)  
  * **Translation**: Google ML Kit Translate (TFLite)  
* **UI Overlay**: flutter\_overlay\_window package

## **📊 Performance Metrics**

The system was evaluated on several key metrics to validate its real-world effectiveness.

| Metric | Value | Description |
| :---- | :---- | :---- |
| **End-to-End Latency** | **\~591.5 ms / frame** | Measured on an emulator; performance is expected to be faster on actual mid-range devices. |
| **Translation Accuracy** | **BLEU Score: 0.94** | For common language pairs (e.g., English → French), indicating high-quality translations. |
| **Alignment Accuracy** | **IoU: 0.26** | Intersection over Union between original and overlayed text. Future work aims to improve this. |

## **🚀 Future Work**

While the current system is robust, we have identified several areas for future enhancement:

* **Improved Translation Coherence**: Implement block-level translation to better preserve the semantic flow of multi-sentence paragraphs.  
* **Enhanced Overlay Alignment**: Refine coordinate mapping to achieve a higher IoU score, ensuring the translated text perfectly covers the source text.  
* **Multimodal Interaction**: Integrate text-to-speech (TTS) for audio feedback and explore gesture-based controls.  
* **Privacy-Preserving Personalization**: Investigate on-device fine-tuning and federated learning to improve model accuracy based on user corrections without compromising privacy.  
* **Chatbot Integration**: Embed a conversational AI to assist users with custom translations, error reporting, and guidance.

## **👥 Authors**

This project was developed by:

* **Akshat Gian** (IIIT Delhi)  
* **Ashwin Verma** (IIIT Delhi)  
* **Shashwat Chandra** (IIIT Delhi)

## **🔗 Project Links**

* **Personas**: [Canva Link](https://www.canva.com/)  
* **Empathy Mapping**: [Canva Link](https://www.canva.com/)  
* **How Might We (HMW)**: [Canva Link](https://www.canva.com/)  
* **Low-Fidelity Prototype**: [Figma Link](https://www.figma.com/)  
* **Mid-Fidelity Prototype**: [Figma Link](https://www.figma.com/)

