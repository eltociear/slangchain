# Examples
<br>

## Autonomous Agents

<br>

### Persistent BabyAGI

[PersistentBabyAGI](../../slangchain/autonomous_agents/baby_agi.py) that is build on top of [BabyAgi](https://github.com/hwchase17/langchain/blob/master/docs/use_cases/autonomous_agents/baby_agi_with_agent.ipynb).

In a nutshell, PersistentBabyAGI extends the functionality for BabyAGI, allowing you to persist the task and task results in the form of Vectorstores. You can pick up where you left off by saving/loading the task and task results Vectorstores.

The notebook can be found [here](./autonomous_agents/examples/baby_agi.ipynb).

<br>

### Persistent BabyAGI - Tools, Context Compression Searches and Constrained Zero Agents

This notebook showcases integrating tools and agents with [PersistentBabyAGI](../../slangchain/autonomous_agents/baby_agi.py) that is build on top of [BabyAgi](https://github.com/hwchase17/langchain/blob/master/docs/use_cases/autonomous_agents/baby_agi_with_agent.ipynb). PersistentBabyAGI extends the functionality for BabyAGI, allowing you to persist the task and task results in the form of Vectorstores. You can pick up where you left off by saving/loading the task and task results Vectorstores.

I added functionality to [ZeroShotAgent](https://github.com/hwchase17/langchain/blob/master/langchain/agents/mrkl/base.py) to address unexpected agent terminations when the agent's instruction narratives exceeded OpenAI's API token limit (~4000). This typically occurs during longer running actions that creates longer instructions when a larger number of tools is made available to the agent. The Open AI error occurs when the instructions attain the said limit.

[ConstrainedZeroShotAgent ](../../slangchain/agents/constrained_mrkl/base.py) works around OpenAI's API token limit by removing the oldest observations from the agent scratch pad so that the instructions parsed to OpenAI's API is below the set agent_scratchpad_token_limit parameter threshold.

The notebook can be found [here](./autonomous_agents/examples/baby_agi_and_constrained_agents.ipynb).

<br>


## Chains

<br>

### URL Contextual Compressions Retriever

[UrlCompressedDocSearchChain](../../slangchain/chains/url_compressed_doc_search/base.py) loads url web content of various types (i.e. html, pdf or json), and retrives the chunks of text that are most relevant to a search query.

The search uses [LangChain](https://github.com/hwchase17/langchain) [DocumentCompressorPipeline](https://github.com/hwchase17/langchain/blob/master/docs/modules/indexes/retrievers/examples/contextual-compression.ipynb). The core idea is simple: given a specific query, we should be able to return only the documents relevant to that query, and only the parts of those documents that are relevant.

The notebook can be found [here](./chains/examples/url_compressed_doc_search.ipynb).

<br>

### Wikipedia Contextual Compressions Retriever

[WikipediaDocSearchChain](../../slangchain/chains/wikipedia_doc_search/base.py) loads Wikipedia pages based on a search query, and retrives the chunks of text that are most relevant to a search query.

The search uses [LangChain](https://github.com/hwchase17/langchain) [WikipediaLoader](https://github.com/hwchase17/langchain/blob/master/docs/modules/indexes/document_loaders/examples/wikipedia.ipynb) to retrieve pages most relevant to the search query and [DocumentCompressorPipeline](https://github.com/hwchase17/langchain/blob/master/docs/modules/indexes/retrievers/examples/contextual-compression.ipynb) to return parts of those documents that are relevant.

The notebook can be found [here](./chains/examples/wikipedia_doc_search.ipynb).

<br>

### URL HREF URL Retriever

[UrlUrlsDocSearchChain](../../slangchain/chains/url_urls_doc_search/base.py) loads web pages, and retrives the href urls that are most relevant to a search query.

The core idea is simple: given a specific query, we should be able to return only the documents relevant to that query, and only the parts of those documents that are relevant.

The notebook can be found [here](./chains/examples/url_urls_doc_search.ipynb).

<br>

## Callbacks

<br>

### DynamoDB Callback

The notebook showcases how to use the [StreamingDynamoDBCallbackHandler](../../slangchain/callbacks/streaming_aws_ddb.py) class. The functionality streams callbacks to a AWS DyanmoDB table.

[LangChain](https://github.com/hwchase17/langchain) provides a callback system that allows you to hook into the various stages of your LLM application. This is useful for logging, [monitoring](https://python.langchain.com/en/latest/tracing.html), [streaming](https://python.langchain.com/en/latest/modules/models/llms/examples/streaming_llm.html), and other tasks.

The notebook can be found [here](./callbacks/examples/streaming_aws_ddb.ipynb).

<br>

## Document Loaders

<br>

### Web Content Document Loader

[UnstructuredURLFileLoader](../../document_loaders/url_file.py) loads url web content of various types (i.e. html, pdf or json)

The notebook can be found [here](./document_loaders/examples/url_file.ipynb)


## NLP

<br>

### BYO Knowledge Graph Demo


The [notebook](knowledge_graph/examples/byo_knowledge_graph.ipynb) shows the use of open source APIs to create knowledge graph and key phrase metadata for [LangChain](https://github.com/hwchase17/langchain) [Document](https://github.com/hwchase17/langchain/blob/1ff7c958b0a84b08c84eebba958b5b3fb0e6e409/langchain/schema.py#L269). 

More details of the code can be found below:

- [**EntityExtractor**](../../slangchain/nlp/ner/entity_extractor.py): Uses [Spacy](https://spacy.io/) to extract [named entities](https://machinelearningknowledge.ai/named-entity-recognition-ner-in-spacy-library/) in text.

- [**KnowledgeGraph**](../../slangchain/nlp/ner/knowledge_graph.py): Heavily inspired by [knowledge graph generation](https://medium.com/nlplanet/building-a-knowledge-base-from-texts-a-full-practical-example-8dbbffb912fa) using HuggingFace's [Bablescape model](https://huggingface.co/Babelscape/rebel-large).

- [**KeyPhraseExtractor**](../../slangchain/nlp/ner/phrase_extractor.py): Uses HuggingFace [ml6team's key phrase extractor model](https://huggingface.co/ml6team/keyphrase-extraction-distilbert-inspec) to extract important key phrases from the text.

<br>

### LangGraph


The [notebook](graphs/examples/anthropic/agent_supervisor.ipynb) is inspired by [LangChain](https://github.com/hwchase17/langchain) [Agent Supervisor](https://github.com/langchain-ai/langgraph/blob/main/examples/multi_agent/agent_supervisor.ipynb), The notebook showcases an AgentSupervisor powered by [Anthropic's Claude](https://www.anthropic.com/news/claude-3-family).

<br>

### Web Browser Navigator

Inspired by [Richard He's](https://twitter.com/RealRichomie) [repository](https://github.com/richardyc/Chrome-GPT/blob/main/README.md), this [notebook](tools/examples/anthropic/selenium.ipynb) presents a demonstration of web browser navigation ([SeleniumWrapper](../../slangchain/tools/selenium/tool.py)) powered by [Anthropic](https://www.anthropic.com/) [Claude](https://www.anthropic.com/claude), showcasing the integration of natural language processing and computer vision with web browsing functionality. By leveraging Claude's capabilities, users can interact with the browser using conversational commands.

<br>

### ReCaptcha Solver

This [notebook](tools/examples/selenium_recaptcha.ipynb) presents a demonstration of a ReCaptcha solver ([GoogleRecaptchaWrapper](../../slangchain/tools/selenium/tool.py)) powered by Mutlimodal LLMs, showcasing the integration of natural language processing and computer vision with web browsing functionality.
