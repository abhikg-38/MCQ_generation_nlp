For the task of MCQ generation, I used the following methods and approaches:

-Extracted text from the odf materials with the help of fitz library

-Tokenized extracted text with the help of spaCy

-Organized these tokens into paragraphs by detecting newline character

-Grouped some of these paragraphs together in case they were too short

-Applied named entity recognition(NER) for every such extracted paragraph

-Proceeded with keyword extraction using Term frequency Inverse Document Frequency approach(TF-IDF), the top 5 words having the highest TF IDF scores were taken
-Used T5 LLM for MCA generation

-I first encoded the context parameter to convert into its corresponding IDs and attention masks

-I used these IDs to generate questions. I applied early stopping and returned 5 sequences for every context. No of parallel beams were 5
-Decoded these sequences and converted to text data. Generated options using the entities calculated in NER coupled with the extracted keywords

-Used the TFT5ForConditionalGeneration instance with t5-small model. Used T5Tokenizer
