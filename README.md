# Malawi-Public-Health-System-LLM

### The Task
This is my approach to build an AI assistant capable of providing knowledge contained in the Malawi Technical Guidelines for Integrated Disease Surveillance and Response (TGs for IDSR).
The objective is to traub a Large Language Model(LLM) to answer context-specific questions about Malawian public health processes, case definitions and guidelines, with training done on a dataset derived from the Malawi TGs for IDSR. The challenge and data are hosted <a href="https://zindi.africa/competitions/malawi-public-health-systems-llm-challenge">here</a>.

### The Approach
We use Meta's Llama model as the foundational LLM for the system. A simple, raw LLM when used for this task without given context will not perform well, since it has no knowledge about this specialized/use-case specific task. One approach to solve this issue can be fine-tuning the LLM for the given task to improve performance by adding context and refining the model. 
LLMs are trained on massive amounts of text data, but they can still struggle with factual consistency and sometimes generate incorrect or misleading information. Retrieval Augmented Generation(RAG), is a technique used to improve the accuracy and reliability of LLMs. RAG helps address this by incorporating external/relevant knowledge sources into the generation process. 
Hence, we use the RAG approach to solve the task. Here's how it works:
* Retrieval: When you ask an LLM a question or give it a prompt, RAG first retrieves relevant information from the Public Health Vector Database created with the 6 textbooks. 
* Augmentation: This retrieved information is then combined with the original prompt to provide the LLM with additional context and factual grounding.
* Generation: Finally, the LLM uses this augmented prompt to generate its response. This response would be more accurate and reliable because it's based on both the LLM's internal knowledge and the retrieved factual information. 

### Possible Improvements

* Using a much better LLM: There are a bunch of top-performing models that are still relatively small in size.
* Finetuning the LLM: You can try a trained LLM on the train set Q/A pairs instead of RAG.
* Finetuning + RAG: Research has shown that this is a much better approach than a standalone solution. 
* Prompt Engineering: Introduce your prompt for the LangChain QA Chain. We used the default from LangChain. 
