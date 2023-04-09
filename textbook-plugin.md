## From OpenAI Docs

Personalisation 
1.  Edit the data models: Edit the DocumentMetadata and DocumentMetadataFilter data models in models.py to add custom metadata fields.
2. Update the OpenAPI schema in openapi.yaml accordingly. To update the OpenAPI schema more easily, you can run the app locally, then navigate to http://0.0.0.0:8000/sub/openapi.json and copy the contents of the webpage. Then go to Swagger Editor and paste in the JSON to convert it to a YAML format. You could also replace the openapi.yaml file with an openapi.json file in the .well-known folder.


## Questions

- how does the API look like? - .well-known/openapi.yaml
- how to change `extract_metadata_from_document` - no that looks like just a utility
- how is query APi implemented - 

## Features

- edit `.well-known/openapi.yaml`
- edit `.well-known/ai-plugin.json`
- add book as a document format
- add index of books

## Use Cases

- general knowledge - this would mostly solve the "source" issue
    - what is justice according to plato? with and without plato republic
    - deep learning questions answered from deep learning book
- chat with a book - this is someone already reading the book
    - what are the most important part of the book to prepare my exam
    - where does the book explain this and that concept

