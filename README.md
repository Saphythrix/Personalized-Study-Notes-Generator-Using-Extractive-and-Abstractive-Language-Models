# Personalized-Study-Notes-Generator-Using-Extractive-and-Abstractive-Language-Models
Personalized Study Notes Generator Using Extractive and Abstractive Language Models
Project Description
Overview
This project presents an intelligent, AI-powered system designed to address one of the most common challenges faced by students — the overwhelming task of converting lengthy textbook chapters, lecture transcripts, and educational articles into concise, exam-ready study notes. By leveraging three distinct Natural Language Processing (NLP) approaches, the system not only automates note generation but also provides a rigorous comparative evaluation of each method's effectiveness.
The pipeline integrates extractive summarization via TextRank, abstractive summarization via a custom LSTM Encoder–Decoder, and transfer learning via the pretrained T5 transformer model — offering a complete spectrum of modern summarization techniques within a single, unified framework.

Motivation
Students frequently face information overload when preparing for exams. Manually condensing dense educational material is time-consuming and inconsistent. This system automates that process, enabling learners to receive structured, readable summaries tailored to the content at hand — saving time and improving retention.

Methodology
The system implements and compares three fundamentally different summarization strategies:
1. TextRank (Extractive Summarization)
TextRank uses a graph-based ranking algorithm to identify and extract the most statistically significant sentences from the source document. Because it preserves the original author's language, it is linguistically reliable and executes rapidly — making it suitable for quick reference generation. However, as seen in the ROUGE evaluation, it produces longer outputs (approximately 400 words / 2,300+ characters) with a compression ratio of only ~4%, which can limit its utility for concise notes.
2. LSTM Encoder–Decoder (Abstractive Summarization)
A sequence-to-sequence LSTM model was custom-trained on the project's dataset to generate novel, human-like summaries by understanding and rephrasing source content. While this demonstrates the end-to-end trainability of recurrent architectures, the model's performance was constrained by a limited training corpus of 15 pairs, resulting in very short and low-quality outputs (e.g., "cnns are") and the lowest ROUGE scores across all three methods. This highlights a key lesson in deep learning: data volume is critical for abstractive generation quality.
3. Pretrained T5 Transformer (Transfer Learning)
The T5 (Text-to-Text Transfer Transformer) model, pretrained on 750GB of diverse text, delivered the strongest overall performance. It produced coherent, grammatically sound abstractive summaries (e.g., "a convolutional neural network (CNN) is a type of feedforward neural network that learns features vi...") and achieved the highest ROUGE-1 F1 score (~0.19) and ROUGE-L score (~0.14) among all three methods. Its balanced precision–recall profile on ROUGE-1 further confirms its robustness as a summarization backbone.

Evaluation Results
The system was evaluated using ROUGE metrics (ROUGE-1, ROUGE-2, ROUGE-L), which measure the overlap between generated summaries and reference summaries across unigrams, bigrams, and longest common subsequences.
MethodROUGE-1 F1ROUGE-2 F1ROUGE-L F1Summary LengthTextRank~0.11~0.00~0.06~400 wordsLSTM~0.02~0.00~0.02~2 wordsT5~0.19~0.03~0.14~45 words
T5 emerged as the clear winner across all ROUGE metrics, producing summaries that strike the best balance between brevity and informativeness. TextRank performed moderately well on ROUGE-1 but failed to compress content meaningfully. The LSTM model, while architecturally sound, was limited entirely by insufficient training data.

Key Findings

T5 is the most effective method for automated study note generation, combining transfer learning's linguistic richness with strong ROUGE performance.
TextRank is the fastest and most reliable for preserving factual accuracy, but struggles with compression — producing outputs closer to excerpts than notes.
LSTM has significant potential but requires substantially more training data (hundreds to thousands of document–summary pairs) to become competitive with pretrained models.
The precision–recall asymmetry observed in LSTM's ROUGE-1 scores (high precision ~0.50, near-zero recall ~0.01) reveals that while its few generated tokens can be relevant, it fails to capture the breadth of information from the source.


Technical Pipeline
Input Text (Textbook / Article / Lecture Transcript)
        ↓
  Text Preprocessing
  (tokenization, cleaning, normalization)
        ↓
  Sentence Segmentation
        ↓
  ┌─────────────────────────────────────┐
  │  TextRank │  LSTM Seq2Seq │  T5     │
  └─────────────────────────────────────┘
        ↓
  Generated Summaries
        ↓
  ROUGE Evaluation & Visualization
        ↓
  Best Summary Presented as Study Notes

Skills Demonstrated
This project demonstrates practical competency across a broad range of ML and NLP concepts, including text preprocessing and tokenization, graph-based NLP algorithms, sequence-to-sequence deep learning with LSTMs, fine-tuning and inference with pretrained transformer models, automated evaluation using ROUGE metrics, and data visualization for model comparison.

Conclusion
The Personalized Study Notes Generator successfully demonstrates that transfer learning with T5 is currently the most practical and effective approach for automated educational summarization. The project also serves as a valuable case study in understanding the trade-offs between extractive and abstractive methods — a distinction that sits at the heart of modern NLP research and real-world text summarization systems.
