# multimodal-braille-haptic-assist
# An Electromechanical Display with Tactile Feedback Using Multimodal CNN–BiLSTM Learning

This project presents a multimodal deep learning system that converts image–text inputs into semantic tactile feedback for non-visual communication.

##  Deep Learning Architecture

The proposed architecture consists of three main stages:

**1. Visual Feature Extraction — Lightweight CNN**
- The input image is resized to 224×224 pixels and normalized.
- A custom lightweight CNN extracts spatial and semantic visual features.
- The CNN acts as a feature extractor rather than performing standalone classification.

**2. Textual Feature Extraction — BERT + BiLSTM**
- Associated text/captions are tokenized using a BERT tokenizer.
- Pre-trained BERT embeddings provide contextual word representations.
- A Bidirectional LSTM (BiLSTM) processes the embedding sequence to capture contextual and sequential dependencies.

**3. Multimodal Fusion — Feature Concatenation + MLP**
- Visual and textual feature vectors are concatenated:
  
  `f = [v || t]`
  
- The fused representation is passed through a Multilayer Perceptron (MLP).
- A softmax layer classifies the input into three semantic categories:
  - **Instruction**
  - **Alert**
  - **Information**

### Architecture

`Image → Lightweight CNN ─┐`
  
`                       ├→ Feature Concatenation → MLP → Semantic Class`
  
`Text → BERT → BiLSTM ───┘`

The predicted semantic class is then mapped to a distinct vibration pattern and generated using an Arduino-controlled electromechanical tactile interface.

##  Results

- **Test Accuracy:** 91%
- **Precision:** 0.90
- **Recall:** 0.91
- **F1-Score:** 0.90
- **Tactile Interpretation Accuracy:** 92%

##  Hardware

- Arduino Uno
- 5V ERM vibration motors
- NPN transistors
- Flyback diodes
- Current-limiting resistors

The system combines lightweight multimodal learning with low-cost electromechanical hardware to provide near real-time tactile communication.
