#How to Leverage LLMs for Building Various Copilot Applications 

##Base Model Knowledge: The LLM base models are trained on millions of data available publicly and hence can be used as-is for building copilots for many of the use cases. This is possible by the technique of prompt engineering – with simple prompts or with few shot learning (providing examples) 

Few of the possibilities (but not limited to) of building your own copilots that can do: 

- Code generation:  

Generate code snippets or complete functions based on natural language queries or specifications. 

Provide general programming syntax and logic, while the user data can provide domain-specific details and preferences. 

Check for time complexity of the code. 

Generate documentation for the code. 

- Content creation:  

Create engaging and informative content for blogs, websites, social media, or newsletters based on keywords, topics, or prompts.  

Generate content with linguistic fluency and diversity, while the user can provide style, tone, and audience awareness. 

- Data analysis:  

Execute data analysis tasks such as data cleaning, visualization, exploration, or modeling based on natural language commands or questions.  

Provide general statistical analysis and report generation from the structured data provided by the user along with suitable prompting. 

- Text mining:  

Extract relevant entities, concepts, relations, or events from a given text or document, such as names, dates, locations, topics, sentiments, or opinions.  

 

- Text Categorization & Summarization: 

Execute tasks like summarizing text data like reviews about products and services, categorization into different segments based on the description/text data associated and so on. 

 

##LLM On/With your data 

###RAG pattern: 

The RAG (Retrieval-Augmented Generation) pattern used with Large Language Models (LLMs) like GPT-3.5, GPT-4 is an approach that enhances the knowledge of generative models by combining with additional knowledge without training. This technique allows the LLM to access a broader range of information than what is contained in its training data, improving its performance in tasks that require specific, detailed, or up-to-date knowledge.

#### Approach 1
** RAG stages **

![rag](content/imgs/rag.png)

**1. Loading**

Loading is the initial stage in the RAG pattern, where data/text is obtained from various sources and formats before it is chunked and stored in a Vector DB.

LangChain provides loading capabilities from different sources and formats. Initially, Semantic Kernel had this feature, but it was later extracted to [Kernel Memory](https://github.com/microsoft/kernel-memory).

**2. Chunking / Splitting**
Automatic chunking is challenging when dealing with documents of different formats. Some customers have manually converted important PDFs to text and then chunked them to achieve better retrieval and completion results.

> Chunking is a crucial stage in the RAG pattern. It involves considering not only the size of the chunk but also its content. For example, if a document has 100 pages and only 1 paragraph is relevant to the question, it should be chunked in a way that separates the relevant paragraph into its own chunk. This allows for specific retrieval and prompt generation.

The quality of retrieval heavily relies on the quality of chunking. There is ongoing experimentation to achieve optimal and intelligent chunking.

**3. Embedding and Storage to Vector DB**

Embeding data and storing to vector DB is the next stage in the RAG pattern.  Some Vector DBs automatically generate embeddings as you save data. For more information, refer to the [Weaviate DB Course](https://learn.deeplearning.ai/vector-databases-embeddings-applications).

To ensure optimal retrieval and completion results, it is crucial to use the same model for creating embeddings of both chunks and questions. However, organizations may face challenges if the original embedding model becomes outdated or unavailable. To address this, consider the following options:

- Choose an embedding model with a distant deprecation date.
- Save the raw text of chunks along with their vectors, allowing for regeneration of embeddings using a newer model if necessary (although this may increase costs).
- Download the embedding model and host it on your own infrastructure, ensuring continued use even after deprecation (but incurring additional costs).



**4. Retrieval**

There are different strategies for retrieval. Some DBs provide configurable hybrid retrieval strategies. The retrieval practices are evolving, and we see that VectorDBs are taking ownership over this stage as it makes sense to filter data as close to the data source as possible. They are adding more and more features to support different retrieval strategies.  Retrieval is also an active space for research and development.


Here are some resources for advanced retrieval tactics:

- [Advanced Retrieval tactics using LlamaIndex](https://towardsdatascience.com/advanced-rag-01-small-to-big-retrieval-172181b396d4).  Article Discusses "Smaller Child Chunks Referring to Bigger Parent Chunks" and "Sentence Window Retrieval" taktics.
- [Advanced Retrieval for AI with Chroma and OpenAI SDK](https://learn.deeplearning.ai/advanced-retrieval-for-ai).  This course covers the [Query Expansion](https://arxiv.org/abs/2305.03653) and Re-ranking strategies to improve retrieval results:
    - Advanced Retrieval strategy: Query Expansion by Prompting Large Language Models     
    [<img src="content/imgs/QueryExpansion.png" width="250">](content/imgs/QueryExpansion.png)

    - Advanced Retrieval strategy: Query Expansion by Prompting Large Language Models     
    [<img src="content/imgs/QueryExpansionWithMultp.png" width="250">](content/imgs/QueryExpansionWithMultp.png)

    - Re-Ranking     
    [<img src="content/imgs/ReRanking.png" width="250">](content/imgs/ReRanking.png)
- LangChain has also implemented multiple [retrieval strategies](https://python.langchain.com/docs/modules/data_connection/retrievers/).


**Choice of Search types in RAG:**

The choice of the search types – **Text, Vector search** or **Hybrid Search** will depend on the use case.

- **Text Search:** Also known as keyword search where search is executed by matching keywords. The scoring is mostly done using BM25similarity which is based on TF-IDF (Term Frequency-Inverse Document Frequency and ranking by popular algorithm, BM25.
    
    This type of search is quite useful where:

    1. Exact keyword matching is required.
    2. [proximity search](https://en.wikipedia.org/wiki/Proximity_search_(text)) where documents are searched in which the keyword occur within a specified distance with another keyword irrespective of the order.

- **Vector Search:** Vector search involves encoding data and search queries as numerical vectors and using geometric or algebraic operations to determine similarity. It allows for semantic search by finding the closest data vectors to a query vector in a high-dimensional space, using measures like cosine similarity.
    
    This is useful where:

    1. Retrieval of relevant results based on meaning and context is required e.g. In the case of natural language processing, recommendation systems etc.
    2. Can handle situations where multiple forms of data like text, image and audio must be interpreted and then retrieve information. E.g.: retrieval of text and images in a search query.

- **Hybrid Search:** Hybrid search allows you to take advantage of multiple scoring algorithms such as BM25 and ANN vector similarity so you can get the benefits of both keyword search and semantic search.
    
    This type of search is useful in situations where the different scenarios mentioned in Text Search and Vector Search are required together.


**5. Prompting**

For a comprehensive list of strategies and tactics for prompting, you can refer to the [Prompt Engineering by OpenAI](https://platform.openai.com/docs/guides/prompt-engineering) guide. Additionally, you can find a compilation of prompting techniques in one place at the [Prompt Engineering Guide](https://www.promptingguide.ai/).
 

#### Using Function Calling (To do) 

### Fine-tuning (To do) 

####Full finetuning (To do)

####Parameter efficient Fine- tuning (To do)

### Hybrid approach (RAG + Fine-tuning) (To do) 
