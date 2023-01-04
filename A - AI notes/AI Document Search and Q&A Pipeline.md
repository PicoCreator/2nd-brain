1. Get various document raw
   - Splitting large documents into smaller documents 
   - Summarize, or process the document into a resonable format (maybe with an AI)
     (Aim for 500 tokens)
   - Point form is generally the best 
2. With the collection of documents, we build and embedded model
   - https://beta.openai.com/docs/guides/embeddings
   - using the embedded model we can perform search and ranking
3. Given a question. (and/or chat history)
   - We ask the instructGPT, what kind of information it needs
   - For each major information point
      - We can ask the embedding model, what is the most relevent document
  - We ask instructGPT the question, with the relevent document involved.
  - And we get the answer