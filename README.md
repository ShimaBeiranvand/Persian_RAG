# Persian_RAG

Project Overview : 
This project is designed to retrieve the most relevant data in response to a given question, extract the appropriate answer from the text, and present it in a clear, well-structured sentence.

Dataset : 
A PDF containing information about tourism at a distinctive cave known as Sohoolan Cave in Iran.

Methodology:
The text is extracted from a PDF about Sohoolan Cave using pdfplumber. The extracted text is then semantically chunked using a custom-built algorithm. Sentence boundaries are identified using sentence-transformers/LaBSE, and cosine similarity is applied to group semantically similar sentences into the same paragraph. When the similarity score drops below a certain threshold, a new paragraph is started. These chunks are saved into a file for future use.

Next, FAISS and BM25 libraries are integrated to build the retriever. The user’s question is converted into a numerical representation, and the saved text chunks are similarly transformed. Both BM25 and FAISS rank the chunks from most to least relevant. Their rankings are combined, and the top 3 chunks are selected.

These selected chunks, along with the original question, are then passed to the "MehdiHosseiniMoghadam/AVA-Llama-3-V2" LLaMA-based language model, which extracts and presents the relevant sentences. Persian digits are also normalized as part of the post-processing.

The system’s performance was evaluated using both human judgment and automatic metrics (BLEU and ROUGE). The retriever successfully identified the document containing the answer 86.67% of the time, and the LLaMA model generated the correct answer in 100% of those retrieved cases.

Finally, a simple and user-friendly interface was developed using Gradio.

Result : 
The retriever correctly identified documents containing the answer 86.67% of the time.
The LLaMA LLM generated the answer correctly 100.00% of the time (out of retrieved cases).

How to run : 
Many different libraries have been used in this code , some of them have version conflict to eachother . therefore , the pdf extraction part should be done separately and then the output of this step should be saved in a file. then next steps libraries should be installed and every time that is said in the code or in the result of installing a library , the code should be restarted. all of these points have been considered in the code . you can just run cell by cell and be careful!

