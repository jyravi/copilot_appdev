# Development


After completing the recommended courses from the previous section, you will have a solid understanding of application development with LLMs.  In this section want to add more clarity on how to develop applications with LLMs.

> ### Shift from Algorithmic to Heuristic Software
> Application development leveraging LLM offers a shift from algorithmic approaches to heuristic methods. Heuristic methods utilize available data to solve problems, rather than relying on predefined solutions. While heuristic solutions may not always be provable or completely accurate, they are often sufficient for solving small-scale problems within a larger context.
> **Heuristics vs. Algorithms.**  Algorithms provide step-by-step instructions for solving a specific problem in a finite number of steps. The outcome of an algorithm is predictable and can be reliably reproduced with the same input. On the other hand, heuristic outcomes are educated guesses. They cannot be predicted or reproduced reliably.

## SDKs / Frameworks


When developing solutions that utilize Large Language Models (LLMs), you have the choice of using API Libraries or SDKs/Frameworks. API Libraries are used to build requests, execute and parse requests to LLM endpoints. On the other hand, SDKs/Frameworks provide additional convenient features for developers while internally using API libraries.

While it is feasible to solely rely on API libraries, leveraging SDKs/Frameworks can expedite solution development and reduce code complexity. Therefore, it is recommended to utilize SDKs/Frameworks whenever possible.

> **Important Note:** Code-related educational material can quickly become obsolete due to the constant evolution of libraries and SDKs. It is recommended for learners to focus on application development patterns rather than specific syntax, as patterns are more resistant to change. Refer to official tutorials and documentation for the most up-to-date information.


|                     | [OpenAI](https://platform.openai.com/docs/libraries/python-library)  | [Azure Open AI](https://learn.microsoft.com/en-us/azure/ai-services/openai/supported-languages) | [Semantic Kernel](https://learn.microsoft.com/en-us/semantic-kernel/overview/) | [LangChain](https://www.langchain.com/)       | [LlamaIndex](https://www.llamaindex.ai/)      |
| ------------------- | ----------- | ----------------- | --------------- | --------------- | --------------- |
|                     | API Library | API Library / Service SDK | SDK / Framework | SDK / Framework | SDK / Framework |
| Open Source              | yes         | yes               | yes             | yes             | yes             |
| OpenAI and Azure OpenAI models | yes         | yes               | yes             | yes             | yes             |
|                     |             |                   |                 |                 |                 |
| Framework Features (Memory, Orchestration, Agents...) |  -        |  -                | yes             | yes             | yes             |
|                     |             |                   |                 |                 |                 |
| - C#                  | yes         | yes               | yes             |  -              |  -              |
| - Python              | yes         | yes               | yes             | yes             | yes             |
| - JS                  | yes         | yes               |  -              | yes             | yes             |

The table above shows only three languages, but API Libraries are available for many more languages.  It is also important to note that updates in models are first reflected in API Libraries and later SDKs/Frameworks.

Traditionally Python has the biggest list of AI related libraries due to the largest AI research and development community. However, the C# AI community is rapidly growing thanks to the Semantic Kernel and C# API Libarires. On the other hand, JavaScript, despite being a popular language, currently lacks a string community around LLM.

When working with customers, we have observed that the most important factor in choosing an SDK/Framework is the team's expertise as most Libraries and SDKs are very similar in terms of functionality and performance.

If your team plans using c# then check out the comprehensive resource on Semantic Kernel - [Dive into the World of AI with the Semantic Kernel Cookbook](https://techcommunity.microsoft.com/t5/educator-developer-blog/dive-into-the-world-of-ai-with-the-semantic-kernel-cookbook/ba-p/4032668?WT.mc_id=academic-0000-abartolo).

### Code Samples
This repo contains samples for the following SDKs:

- [Semantic Kernel, C#, .NET 8](/samples/CSharp/)
- [LangChain, Python](/samples/LangChain/)


### Recomendations regarding Performance, Stability and Cost

- Latency is a significant challenge for solutions like a call centers where AI-powered virtual agents assist human agents.  Customers sometimes have to wait longer for a responce that's comming from LLM.  To mitigate such wait time during the call develops fill the wait time with the call-waiting messages like: "Mm,s" or leyboar typing.
- LLM latency in UI interfaces can be masked by leveraging Streaming. For more information, refer to the [OpenAI Streaming](https://platform.openai.com/docs/api-reference/streaming) and [Azure Open AI API reference](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#:~:text=stream) documentation.
- LangChain and LlamaIndex provide caching Functionality. LlamaIndex also offers ability to leferage remote cache like remote Redis. This feature offers two advantages: it can help reduce costs by minimizing the number of API calls to the LLM provider and improve responsiveness.
- While building SaaS/Multitenant solution it's recomened to review [Multitenancy and Azure OpenAI Service](https://learn.microsoft.com/azure/architecture/guide/multitenant/service/openai) article.  It's provides guidance on how to implement multitenancy with Azure OpenAI Service.
- Putting API Management in front of two or more Azure OpenAI services can increase the number of tokens per minute (TPM) and improve stability by implementing retry logic for failed requests. You can refer to the sample code for implementing [Azure OpenAI Service Load Balancing with Azure API Management](https://learn.microsoft.com/en-us/samples/azure-samples/azure-openai-apim-load-balancing/azure-openai-service-load-balancing-with-azure-api-management/).  More advanced implementaion based on NGINX and AKS can be found in the article - [Azure OpenAI Service Multitenant Load Balancing and Token Per Minute Tracking via Prometheus Metrics](https://techcommunity.microsoft.com/t5/fasttrack-for-azure/azure-openai-service-multitenant-load-balancing-and-token-per/ba-p/3980163)

## Orchestrators 

(To do)
