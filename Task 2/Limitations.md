# Limitations and Possible Improvements

Although the RAG chatbot successfully retrieves information from uploaded documents and generates context-aware responses, it has several limitations that can be improved in future versions.

## 1. Supports Only PDF Files

### Limitation

The current implementation only accepts PDF documents as input. Users cannot upload other commonly used document formats such as Word documents (.docx), PowerPoint presentations (.pptx), text files (.txt), or spreadsheets.

### Possible Improvement

Support for additional file formats can be added using appropriate document loaders available in LangChain. This would make the system more flexible and useful in real-world scenarios where information is stored in multiple formats.

---

## 2. Answers Only from Uploaded Documents

### Limitation

The chatbot is designed to answer questions strictly using the retrieved document context. As a result, it cannot answer general knowledge questions or questions about the documents themselves that are not explicitly contained within the retrieved text.

For example, if a user asks:

* "Summarize the overall purpose of this document."
* "What topics are covered across all uploaded PDFs?"

the system may fail if the required information is not present in the retrieved chunks.

### Possible Improvement

A hybrid approach can be implemented where the system combines document retrieval with the model's general knowledge. Additional document-level summarization and metadata generation can also be incorporated to answer broader questions about the uploaded files.

---

## 3. Conversation History Is Lost on Refresh

### Limitation

Conversation history is stored only in memory during the current session. If the application is refreshed or restarted, all previous conversations are lost.

### Possible Improvement

Chat history can be stored in a database such as SQLite, PostgreSQL, or MongoDB. This would allow conversations to persist across sessions and improve the user experience.

---

## 4. Fixed Retrieval Count (k = 3)

### Limitation

The retriever is configured to always return the top 3 document chunks. While this works well for many queries, some questions may require more context than three chunks can provide.

### Possible Improvement

The value of k can be increased or made dynamic based on the complexity of the user's question. This would allow the system to retrieve a larger amount of relevant information when necessary.

---

## 5. Retrieves the Top 3 Chunks, Not Necessarily the Best 3

### Limitation

The system retrieves the three highest-ranked chunks based on similarity scores. However, the highest-ranked chunks are not always the most useful chunks for answering a specific question. Important context may exist in lower-ranked chunks that are never retrieved.

### Possible Improvement

A reranking mechanism can be introduced after retrieval. This would evaluate the retrieved chunks more carefully and select the most relevant ones before passing them to the language model. Advanced retrieval techniques such as hybrid search or cross-encoder reranking can further improve answer quality.

---

## 6. Hardcoded PDF File Names

### Limitation

The current implementation uses hardcoded PDF file paths in the source code. To add or remove documents, the code must be modified manually.

### Possible Improvement

Users should be allowed to upload documents dynamically through the Streamlit interface. The system can automatically detect, process, and index uploaded files without requiring code changes, making the application more scalable and user-friendly.

---

## Future Scope

Future versions of the project can include support for multiple file formats, persistent conversation memory, dynamic document uploads, improved retrieval techniques, document summarization capabilities, and cloud deployment. These enhancements would make the chatbot more robust, scalable, and suitable for real-world business applications.
