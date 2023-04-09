## From OpenAI Docs

Personalisation 
1.  Edit the data models: Edit the DocumentMetadata and DocumentMetadataFilter data models in models.py to add custom metadata fields.
2. Update the OpenAPI schema in openapi.yaml accordingly. To update the OpenAPI schema more easily, you can run the app locally, then navigate to http://0.0.0.0:8000/sub/openapi.json and copy the contents of the webpage. Then go to Swagger Editor and paste in the JSON to convert it to a YAML format. You could also replace the openapi.yaml file with an openapi.json file in the .well-known folder.


## Questions

- how does the API look like? - .well-known/openapi.yaml
- how to change `extract_metadata_from_document` - no that looks like just a utility

### How is query API implemented 


![]("./textbook-plugin-design.png")

```datastore.query
query_texts = [query.query for query in queries]
query_embeddings = get_embeddings(query_texts)
# hydrate the queries with embeddings
queries_with_embeddings = [
    QueryWithEmbedding(**query.dict(), embedding=embedding)
    for query, embedding in zip(queries, query_embeddings)
]
return await self._query(queries_with_embeddings)
```

- where is the topk done? - somewhere in pinecone
- description: Accepts search query objects array each with query and optional filter. Break down complex questions into sub-questions. Refine results by criteria, e.g. time / source, don't do this often. Split queries if ResponseTooLargeError occurs. - this are the instructions on how to use the query, the instructions are not for humans but for LLMs!

## Features

P1
- /query-textbook
    - edit `.well-known/openapi.yaml`
    - edit `.well-known/ai-plugin.json`
    - add book as a document format
    - where to add available textbooks with name and summary?

P2
- /chapters-for-textbook
- /available-textbooks-for-topic - add topic <-> books mapping?  k, is this is a hardcoded or ML feature? hardcoded would be "give me textbooks for a given topic"
- book object metadata - Book Content Description Chatpers ... - can work on this after looking what plugins are around

## Use Cases

- general knowledge - this would mostly solve the "source" issue
    - what is justice according to plato? with and without plato republic
    - deep learning questions answered from deep learning book
- chat with a book - this is someone already reading the book
    - what are the most important part of the book to prepare my exam
    - where does the book explain this and that concept

