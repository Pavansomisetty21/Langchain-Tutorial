LangChain can be used to build any sort of complex app around LLMs is because
of agents. Agents enable the development of a diverse range of customized apps, from being as
simple as a Q&A bot to as complex as AutoGPT AI agent. We will first start by explaining what an
agent is.
An agent can be taken as an extension of chains where we can equip the LLM with a variety of 3rd
party tools or even APIs like Google Search and get our task done by following multiple actions. If
you remember, even chains can handle 3rd party tools and follow a sequence of actions.
#### How are Agents different from Chains?
The actions in a chain are hardcoded and need to follow a predefined sequence but in the case of
an agent, there exists no sequence and the LLM decides what to do next and which tool to use.
Hence, chains are more rigid compared to agents. Let’s understand with an example:
Assume we have a chain that can fetch data from the internet and prepare fake csv files. The course
of action every time this chain is executed would look like this:
a. Understand the data required from the input.
b. Hit the internet and fetch data.
c. Preprocess this raw data.
d. Organize in a csv and store.
Now, if someone inputs a ‘Hi dude’ prompt, such a chain might break as following the above steps is
not possible. Assume that we have a similar use case for an agent, it won’t be following a strict chain
of action but will decide using an LLM what to do and should output ‘Hello’ rather than breaking down.
This makes agents more flexible and less error-prone.
One more advantage agents have over chains is they are more versatile as compared to chains and
scaling to new functionalities is easier. Adding any custom utility is extremely easy.
If you're looking for an app that is adaptable and dynamic, agents provide a superior choice.
However, if your use case remains consistent, chains can be employed.
As we now understand what an agent is capable of, let’s understand what are tools and other
related concepts:

1. Tools are functions that agents can use for 3rd party utilities. These tools can be generic
utilities, other chains, or even other agents. For example, a custom tool could be a search utility
that enables an agent to retrieve information from the internet. Or a write file tool that enables
file creation by an agent.

2. LangChain even has ToolKits, which is a combination of multiple related tools. Say CSV toolkit
which provides all the facilities to analyze a CSV file which may include reading the file, data
manipulation, etc.

3. The AgentExecutor in LangChain is a component that serves as the runtime for an agent. It
plays a crucial role in the execution of agents by calling them, executing the actions they
choose and passing the outputs of those actions back to the system.

The AgentExecutor is responsible for managing the execution flow of these agents ensuring the
agent handles scenarios of selecting a tool that doesn't exist or errors occur and managing
instances where the agent generates output that can't be parsed for tool use. It involves maintaining
comprehensive logs and observability across various levels, including agent decisions and tool
calls, directing them to standard output

Let’s quickly brief a few important pre-defined tools:

#### 1. ArxivQueryRun,PubmedQueryRun,WikipediaQueryRun,WolframAlphaQueryRun:
Toolsdedicated to querying and retrieving data from specific sources like Arxiv, PubMed, Wikipedia
and WolframAlpha.
#### 2. AzureCogsFormRecognizerTool,AzureCogsImageAnalysisTool,AzureCogsSpeech2TextTool,AzureCogsText2SpeechTool:
Tools utilizing various Azure Cognitive Services for tasks like form recognition, image analysis, speech-to-text and text-to-speech.
#### 3. GoogleSearchResults, BingSearchResults, DuckDuckGoSearchResults: 
Tools interacting with search engines and providing search results.
#### 4. GooglePlacesTool:
Interacting with Google Places API for location-based data.
#### 5. GmailCreateDraft, GmailGetMessage, GmailGetThread, GmailSearch, GmailSendMessage:
Tools for interacting with Gmail API, enabling actions like creating drafts, fetching messages,searching and sending messages.
#### 6. SceneXplainTool:
Assists in explaining or describing scenes.
#### 7. SteamshipImageGenerationTool:
Related to generating images or visuals connected to Steamship.
#### 8. StructuredTool:
Supports structured data handling or organization within the LangChainenvironment.
#### 9. AINAppOps, AINOwnerOps, AINRuleOps, AINTransfer, AINValueOps: 
These tools involve operations related to the AIN (Artificial Intelligence Network) such as managing apps,ownership, rules, transfers and values within the network.
#### 10. AIPluginTool:
Assists in integrating AI plugins into the LangChain ecosystem.
Rather, at times you may wish to use toolkits. To know all available toolkits, you can use the below
```
import langchain.agents.agent_toolkits
print(langchain.agents.agent_toolkits.__all__)
```
#### Output:
['AINetworkToolkit','AmadeusToolkit','AzureCognitiveServicesToolkit',
'FileManagementToolkit', 'GmailToolkit', 'JiraToolkit',...]
Below are some major toolkits and what tools they have:
1. AINetworkToolkit: Involves tools for managing operations and interactions within the AIN
(Artificial Intelligence Network)
2. AzureCognitiveServicesToolkit: Provides tools to integrate and utilize Azure Cognitive Services
within LangChain.
3. FileManagementToolkit: Tools dedicated to managing files within the LangChain environment.
4. GmailToolkit, O365Toolkit, SlackToolkit: Involves tools to interact with and manage data
related to Gmail, Office 365 and Slack APIs respectively
5. PowerBIToolkit: Provides tools for integrating and utilizing Power BI functionalities within
LangChain.
6. SparkSQLToolkit, SQLDatabaseToolkit: These toolkits offer tools to interact with and manage
Spark SQL and SQL databases within the LangChain ecosystem.
7. VectorStoreToolkit, VectorStoreRouterToolkit: Toolkits for handling data and routing within
VectorStore, likely managing and processing vector-based information.
8. create_openapi_agent, create_json_agent: Tools to create agents specifically tailored for
OpenAPI and JSON data handling.


### Types of Agents
Depending upon how the agent thought process works, we have different types of agents in
LangChain:
#### 1. Zero-Shot ReAct: 
This versatile agent, utilizing the ReAct framework, dynamically selecting tools solely based on their descriptions. It accommodates any
number of tools, emphasizing the necessity of describing each tool. Notably, it is the most
general-purpose action agent.
#### 2. Structured Input ReAct:
Geared for handling multi-input tools, this agent differs from others by
utilizing a tools' argument schema to structure action inputs. This capability proves beneficial
for intricate tool usage, such as precise navigation within a browser.
#### 3. OpenAI Functions: 
Tailored for certain OpenAI models, like GPT-3.5-turbo and GPT-4, this agent
is explicitly fine-tuned to detect when a function should be invoked. It responds by providing the
necessary inputs for the function, aligning with the specific features of these models.
#### 4. Conversational:
Designed for interactive and conversational scenarios, this agent employs the
ReAct framework to determine the appropriate tool to use. Notably, it leverages memory to
recall and build upon previous interactions in the ongoing conversation.
#### 5. Self-ask with Search: 
Operating with a single tool named "Intermediate Answer," this agent
excels at looking up factual answers to questions. It mirrors the concept of the original self-ask
with search paper, where a Google search API served as the tool.
#### 6. ReAct Document Store: 
Interacting with a doc-store or vector db, this agent utilizes the ReAct
framework and requires two specific tools: Search and Lookup tools. The Search tool searches
for a document, while the Lookup tool looks up a term within the most recently found
document. This mirrors the original ReAct paper.
