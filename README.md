# GraphRAG
survey for GraphRAG
## microsoft
* [1][GraphRAG: New tool for complex data discovery now on GitHub ](https://www.microsoft.com/en-us/research/blog/graphrag-new-tool-for-complex-data-discovery-now-on-github/)
  * [Github](https://github.com/microsoft/graphrag)
  * [GraphRAG Accelerator](https://github.com/Azure-Samples/graphrag-accelerator/?tab=readme-ov-file)
  * [dataset](https://github.com/yixuantt/MultiHop-RAG/)_
* [2][GraphRAG: Unlocking LLM discovery on narrative private data](https://www.microsoft.com/en-us/research/blog/graphrag-unlocking-llm-discovery-on-narrative-private-data/)  
* [3][From Local to Global: A Graph RAG Approach to Query-Focused Summarization](https://www.microsoft.com/en-us/research/publication/from-local-to-global-a-graph-rag-approach-to-query-focused-summarization/)

# BaselineRAG VS GraphRAG
## 存在的问题
  * Baseline RAG 很难将各个点连接起来。当回答问题需要通过共享属性遍历不同的信息片段以提供新的综合见解时，就会发生这种情况。
  * 当被要求全面理解大型数据集甚至单个大型文档中的总结语义概念时，Baseline RAG 表现不佳。
## 例子：
  * 数据集：暴力事件数据集
### Query: “What is Novorossiya?” （什么是“新俄罗斯”）
| Baseline RAG | GraphRAG |
|:-------------|:---------|
| The term “Novorossiya” is not mentioned in the provided context. However, to provide some information, Novorossiya, or New Russia, is a historical term referring to a region in the south of Ukraine that was conquered by the Russian Empire in the 18th century. In recent years, the term has been revived by Russian-backed separatists in Eastern Ukraine to refer to the territories they claim, but it is not officially recognized as a separate entity by international bodies. | Novorossiya, also known as New Russia, is a term with historical and contemporary significance. Historically, it referred to a region in the southern part of the Russian Empire that is now part of Ukraine. In the contemporary context, it has been used by pro-Russian separatists to refer to certain areas of Ukraine [Data: Entities (6494, 912, 6493)]. The term Novorossiya has been used in the context of a political movement in Ukraine, particularly by Russian nationalists. This movement has been associated with efforts to destabilize Ukraine and create a so-called “Novorossiya” [Data: Entities (912); Relationships (15211, 15206)]. The term has also been used to denote a separatist state in Ukraine, known as the Federal Republic of Novorossiya (FRN) [Data: Entities (7690)]. |
| 在提供的上下文中没有提到“新俄罗斯”一词。但是，为了提供一些信息，新俄罗斯是一个历史术语，指的是乌克兰南部的一个地区，该地区于 18 世纪被俄罗斯帝国征服。近年来，俄罗斯支持的乌克兰东部分离主义者重新使用这个词来指代他们声称拥有的领土，但它并未被国际机构正式承认为一个独立实体。 | 新俄罗斯，又称新俄罗斯，是一个具有历史和当代意义的术语。从历史上看，它指的是俄罗斯帝国南部的一个地区，现在是乌克兰的一部分。在当代背景下，亲俄分裂分子用它来指代乌克兰的某些地区 [数据：实体 (6494, 912, 6493)]。新俄罗斯一词曾用于乌克兰的政治运动，尤其是俄罗斯民族主义者。这场运动与破坏乌克兰稳定和建立所谓的“新俄罗斯”的努力有关 [数据：实体 (912)；关系 (15211, 15206)]。该术语还被用来表示乌克兰的一个分离主义国家，即新俄罗斯联邦共和国 (FRN) [数据：实体 (7690)]。 |

### Query: “What has Novorossiya done?” （“新俄罗斯”做了什么）
| Baseline RAG | GraphRAG |
|:-------------|:---------|
|The text does not provide specific information on what Novorossiya has done.|Novorossiya, a political movement in Ukraine, has been involved in a series of destructive activities, particularly targeting various entities in Ukraine [Entities (6494, 912)]. The movement has been linked to plans to destroy properties of several Ukrainian entities, including Rosen, the Odessa Canning Factory, the Odessa Regional Radio Television Transmission Center, and the National Television Company of Ukraine [Relationships (15207, 15208, 15209, 15210)]. In addition to these, Novorossiya has also been associated with plans to destroy properties of Roshen, the Odessa Conservatory Factory, the Odesa Regional Radio Television Transmission Center, and the National Telecommunications Company of Ukraine [Relationships (8329, 8330, 8331, 8332)]. Furthermore, Novorossiya has been implicated in plans to blow up ATMs of PrivatBank, the largest state bank in Ukraine [Relationships (8335, 8335)].  The Office of the General Prosecutor in Ukraine has reported on the creation of Novorossiya, indicating the government’s awareness and potential concern over the activities of this movement [Relationships (8264, 8264)]. The destructive activities of Novorossiya have had significant impacts on the targeted entities and have likely contributed to the ongoing tensions and conflicts in the region.  In summary, Novorossiya has been involved in a series of destructive activities targeting various entities in Ukraine. These activities have had significant impacts on the targeted entities and have likely contributed to the ongoing tensions and conflicts in the region. The Ukrainian government, through the Office of the General Prosecutor, has acknowledged the existence and activities of Novorossiya, indicating a level of concern over the movement’s actions. |
|文中没有提供新俄罗斯所做之事的具体信息。 |乌克兰的一个政治运动组织新俄罗斯参与了一系列破坏活动，特别是针对乌克兰的各种实体 [实体 (6494, 912)]。该运动与破坏乌克兰多个实体财产的计划有关，包括罗森、敖德萨罐头厂、敖德萨地区广播电视传输中心和乌克兰国家电视公司 [关系 (15207, 15208, 15209, 15210)]。除此之外，新俄罗斯还与破坏罗森、敖德萨音乐学院工厂、敖德萨地区广播电视传输中心和乌克兰国家电信公司的财产的计划有关 [关系 (8329, 8330, 8331, 8332)]。此外，新俄罗斯还涉嫌炸毁乌克兰最大国有银行 PrivatBank 的 ATM 机 [关系 (8335, 8335)]。 乌克兰总检察长办公室报告了新俄罗斯的成立，表明政府对该运动活动的认识和潜在担忧 [关系 (8264, 8264)]。新俄罗斯的破坏性活动对目标实体产生了重大影响，并可能加剧了该地区持续的紧张局势和冲突。 总而言之，新俄罗斯参与了一系列针对乌克兰各实体的破坏性活动。这些活动对目标实体产生了重大影响，并可能加剧了该地区持续的紧张局势和冲突。乌克兰政府通过总检察长办公室承认了新俄罗斯的存在和活动，表明对该运动的行为感到一定程度的担忧。|

* ![image](https://github.com/user-attachments/assets/de9cf46b-6d41-4e5e-ae33-7ce5fe93c8ab)
* 图1: Baseline RAG召回的结果
* ![image](https://github.com/user-attachments/assets/c5aa87ff-854e-48fc-854d-7370b17b8284)
* 图2: GraphRAG的由来

* 基线 RAG 无法回答这个问题。查看插入上下文窗口的源文档（图 1），没有任何文本段讨论 Novorossiya，导致此失败。相比之下，GraphRAG 方法在查询 Novorossiya 中发现了一个实体。这允许 LLM 将自身置于图中，并通过指向原始支持文本的链接产生包含出处的更优答案。例如，下面的图 2 显示了 LLM 用于 LLM 生成的声明“Novorossiya 涉嫌炸毁 ATM 机的计划”的确切内容。我们看到原始源文档（经过英文翻译）中的片段，LLM 使用该片段通过图中两个实体之间存在的关系来支持特定银行是 Novorossiya 的目标的断言。

### Query: “What are the top 5 themes in the data?“ （“数据中的前 5 个主题是什么？）
| Baseline RAG | GraphRAG |
|:-------------|:---------|
|1. Improving the quality of life in cities and urban development.<br>   2. The meeting between Vladimir Putin and the President of the United Arab Emirates, Mohammed bin Zayed Al Nahyan. <br>  3. The National Rating of the Investment Climate in the Regions of Russia.  <br> 4. The state of the Russian economy and the growth of domestic brands. <br>  5. The discussion on the meaning of life and the role of science in understanding it. <br> |The data presents a wide range of themes, but the top five most prevalent themes can be identified as follows: <br> 1. Conflict and Military Activity: A significant portion of the data revolves around the ongoing conflict in Ukraine, with numerous reports detailing military activities, occupations, and attacks by various entities. This theme includes the actions of the Ukrainian military, Russian forces, and various other military units and entities [Data: Reports (513, 241, 151, 493, 343, +more)]. <br>  2. Political and Governmental Entities: Many reports focus on political figures and governmental entities, highlighting their roles, relationships, and actions in the context of the current situation. This includes entities like the Kremlin, the President of Ukraine, the US State Department, and various regional administrations [Data: Reports (98, 493, 265, 129, 196, +more)].<br>  3. Infrastructure and Environmental Concerns: Several reports highlight potential environmental impacts and infrastructure threats. These include potential environmental damage due to industrial activities, flooding crises, and threats to infrastructure due to military conflicts [Data: Reports (308, 154, 201, 348, 216, +more)]. <br>  4. Community Analysis and Threat Assessment: Several reports provide detailed analyses of specific communities, often centered around a particular location or entity. These analyses typically discuss the key entities within the community, their relationships, and any associated threats. Many reports also include assessments of potential threats associated with the entities or situations they discuss [Data: Reports (323, 596, 518, 583, 179, +more)].  <br> 5. Health, Humanitarian Concerns, and Emergency Situations: Some reports focus on health and humanitarian issues, such as the Shereshevsky-Turner Syndrome community and the potential risk of intestinal diseases in the Odessa region. The data also covers emergency situations, including natural disasters, accidents, and attacks [Data: Reports (204, 149, 372, 154, 532, +more)].  <br> These themes provide a comprehensive overview of the current situation, highlighting the complexity and interconnectedness of the issues at hand. |
|1. 改善城市生活质量和城市发展。 <br> 2. 弗拉基米尔·普京与阿联酋总统穆罕默德·本·扎耶德·阿勒纳哈扬会晤。<br> 3. 俄罗斯各地区投资环境全国评级。<br>  4. 俄罗斯经济状况和国内品牌增长。<br>  5. 讨论生命的意义以及科学在理解生命中的作用。<br> |数据呈现了广泛的主题，但可以确定的五个最普遍的主题如下：<br> 1. 冲突和军事活动：很大一部分数据围绕着乌克兰持续的冲突，许多报告详细介绍了各种实体的军事活动、占领和袭击。这一主题包括乌克兰军队、俄罗斯军队和其他各种军事单位和实体的行动 [数据：报告（513、241、151、493、343，+更多）]。<br> 2. 政治和政府实体：许多报告关注政治人物和政府实体，强调他们在当前局势下的角色、关系和行动。这包括克里姆林宫、乌克兰总统、美国国务院和各地区行政部门等实体 [数据：报告（98、493、265、129、196，+更多）]。<br> 3. 基础设施和环境问题：多份报告强调了潜在的环境影响和基础设施威胁。其中包括工业活动造成的潜在环境破坏、洪水危机以及军事冲突对基础设施造成的威胁 [数据：报告（308、154、201、348、216 等）]。<br>  4. 社区分析和威胁评估：多份报告对特定社区进行了详细分析，通常以特定地点或实体为中心。这些分析通常讨论社区内的关键实体、它们之间的关系以及任何相关威胁。许多报告还包括对与其讨论的实体或情况相关的潜在威胁的评估 [数据：报告（323、596、518、583、179 等）]。<br> 5. 健康、人道主义关切和紧急情况：一些报告重点关注健康和人道主义问题，例如 Shereshevsky-Turner 综合征社区和敖德萨地区肠道疾病的潜在风险。数据还涵盖紧急情况，包括自然灾害、事故和袭击 [数据：报告（204、149、372、154、532 等）]。<br>  这些主题全面概述了当前局势，突出了当前问题的复杂性和相互关联性。|

* 查看基线 RAG 的结果，我们发现列出的主题与两国之间的战争没有太大关系。正如预期的那样，向量搜索检索到不相关的文本，这些文本被插入到 LLM 的上下文窗口中。包含的结果很可能与“主题”一词有关，导致对数据集中发生的事情的评估不太有用。
* 观察 GraphRAG 的结果，我们可以清楚地看到，结果与整个数据集中发生的事情更加一致。答案提供了五个主要主题以及在数据集中观察到的支持细节。引用的报告由 LLM 为 GraphRAG 中的每个语义集群预先生成，反过来，它们提供了对原始源材料的出处。

# GraphRAG方法
* Our approach uses an LLM to build a graph-based text index in two stages: first to derive an entity knowledge graph from the source documents, then to pregeneratcommunity summaries for all groups of closely-related entities.
* 我们的方法使用 LLM 分两个阶段构建基于图的文本索引： 首先从源文档中得出实体知识图，然后为所有密切相关的实体组预生成社区摘要。
* <img width="793" alt="image" src="https://github.com/user-attachments/assets/2370149e-8e1f-4bdf-93ac-acb87efbb714">
*	文本分块（Text Chunks）: 从源文档中提取文本并进行分块处理。
*	元素实例化（Element Instances）: 使用LLM从每个文本块中提取实体和关系实例。
*	元素摘要（Element Summaries）: 将提取的实例转换为单一的描述性文本块。
*	图社区检测（Graph Communities）: 利用Leiden算法检测图中的社区结构。
*	社区摘要（Community Summaries）: 为每个社区生成报告式的摘要。
*	问答生成: 通过多阶段处理生成最终答案，包括社区答案和全局答案。
















## Ant
*[Vector | Graph：蚂蚁首个开源Graph RAG框架设计解读](https://developer.aliyun.com/article/1540097)
* ![image](https://github.com/user-attachments/assets/5cd8f853-6b00-4b56-b264-d65440f160ca)
* Graph RAG的核心链路分如下三个阶段：
  * 索引（三元组抽取）：通过LLM服务实现文档的三元组提取，写入图数据库。
  * 检索（子图召回）：通过LLM服务实现查询的关键词提取和泛化（大小写、别称、同义词等），并基于关键词实现子图遍历（DFS/BFS），搜索N跳以内的局部子图。
  * 生成（子图上下文）：将局部子图数据格式化为文本，作为上下文和问题一起提交给大模型处理。
###  技术选型
* 要构建一个完整的开源Graph RAG链路，离不开三个重要的子系统：一个可以支持RAG的AI工程框架，一个知识图谱系统和一个图存储系统。而作为蚂蚁首个对外开源的Graph RAG框架，我们采用蚂蚁全自主的开源产品：DB-GPT + OpenSPG + TuGraph。
#### AI工程框架（@DB-GPT）
* DB-GPT是一个开源的AI原生数据应用开发框架，目的是构建大模型领域的基础设施，通过开发多模型管理(SMMF)、Text2SQL效果优化、RAG框架以及优化、Multi-Agents框架协作、AWEL(智能体工作流编排)等多种技术能力，让围绕数据库构建大模型应用更简单，更方便
![image](https://github.com/user-attachments/assets/faba84d3-1d7c-4d80-81a0-c568cddbe74b)

#### 知识图谱（@OpenSPG）
* OpenSPG是蚂蚁集团结合多年金融领域多元场景知识图谱构建与应用业务经验的总结，并与OpenKG联合推出的基于SPG(Semantic-enhanced Programmable Graph)框架研发的知识图谱引擎。
* ![image](https://github.com/user-attachments/assets/b9550b98-650e-45cd-93db-26e34cd961d3)

#### 图数据库（@TuGraph）
* TuGraph是蚂蚁集团与清华大学联合研发的大规模图处理系统，构建了包含图数据库、图计算引擎、图机器学习、图研发平台的完善图技术体系。支持海量多源的关联数据的实时处理，显著提升数据分析效率，支撑了蚂蚁支付、安全、社交、公益、数据治理等300多个场景应用，多次打破图数据库性能基准测试LDBC-SNB世界纪录，并跻身IDC中国图数据库市场领导者象限。
* ![image](https://github.com/user-attachments/assets/2e7cbb92-2770-4af2-9f12-c2aa52d841ba)


### 开源技术方案
#### 1. 索引
* 索引加工的统一抽象是TransformerBase接口，目前提供了嵌入、抽取、翻译三类转换器。而图索引的构建，则通过三元组提取器TripletExtractor来实现。
* ![image](https://github.com/user-attachments/assets/579e9951-1535-45cd-9f9c-9bb311c78395)

* ExtractorBase接口负责信息提取的职责，当下已有的三元组提取器和关键词提取器都依赖了大模型能力，所以抽象类LLExtractor负责与LLM交互的公共逻辑，具体的实现类只需要提供提示词模板和结果解析即可。三元组提取器TripletExtractor的提示词模板（受LlamaIndex启发），核心理念是通过few-shot样本引导大模型生成三元组结构。

```  TRIPLET_EXTRACT_PT = (
    "Some text is provided below. Given the text, "
    "extract up to knowledge triplets as more as possible "
    "in the form of (subject, predicate, object).\n"
    "Avoid stopwords.\n"
    "---------------------\n"
    "Example:\n"
    "Text: Alice is Bob's mother.\n"
    "Triplets:\n(Alice, is mother of, Bob)\n"
    ...TL;DR...
    "Text: Philz is a coffee shop founded in Berkeley in 1982.\n"
    "Triplets:(Philz, is, coffee shop)\n(Philz, founded in, Berkeley)\n(Philz, founded in, 1982)\n"
    "---------------------\n"
    "Text: {text}\n"
    "Triplets:\n"
)
```

* 大模型让三元组抽取变成了一件非常简单的事情，但是要提高三元组的抽取质量也不是一件容易的事情。最简单的是通过提示词工程不断优化提示词模板，让通用大模型给出更理想的答案。另外使用专有的知识抽取大模型（如OneKE）可以取得更好的效果，这部分工作还在进行中，我们期望看到OnekeExtractor的社区贡献早日发布。

#### 2. 存储
* 索引存储的统一抽象是IndexStoreBase接口，目前提供了向量、图、全文三类索引实现。知识图谱接口KnowledgeGraphBase是Graph RAG的存储底座，目前DB-GPT内置 BuiltinKnowledgeGraph实现就是基于文本大模型能力构建的，OpenSPG的接入工作已经在逐步推进。IndexStoreBase接口的继承树
![image](https://github.com/user-attachments/assets/3cc2fb21-6454-45c5-817e-15eec15a95b7)

* 知识图谱提供了和向量数据库同样的接口，让知识的存取过程透明化。文档内容经过三元组解析器_triplet_extractor解析后，直接写入图存储_graph_store。

async def aload_document(self, chunks: List[Chunk]) -> List[str]:
    """Extract and persist triplets to graph store.
    Args:
        chunks: List[Chunk]: document chunks.
    Return:
        List[str]: chunk ids.
    """
    for chunk in chunks:
        triplets = await self._triplet_extractor.extract(chunk.content)
        for triplet in triplets:
            self._graph_store.insert_triplet(*triplet)
        logger.info(f"load {len(triplets)} triplets from chunk {chunk.chunk_id}")
    return [chunk.chunk_id for chunk in chunks]
图存储接口GraphStoreBase提供统一的图存储抽象，目前内置了MemoryGraphStore和TuGraphStore的实现，分别用于本地测试和生产部署，并预留了Neo4jStore的扩展点。
GraphStoreBase接口的继承树

具体的图存储提供了三元组写入的实现，一般会调用图数据库的查询语言来完成。例如TuGraphStore会根据三元组生成具体的Cypher语句并执行。

def insert_triplet(self, subj: str, rel: str, obj: str) -> None:
    """Add triplet."""
    ...TL;DR...
    subj_query = f"MERGE (n1:{self._node_label} {{id:'{subj}'}})"
    obj_query = f"MERGE (n1:{self._node_label} {{id:'{obj}'}})"
    rel_query = (
        f"MERGE (n1:{self._node_label} {{id:'{subj}'}})"
        f"-[r:{self._edge_label} {{id:'{rel}'}}]->"
        f"(n2:{self._node_label} {{id:'{obj}'}})"
    )
    self.conn.run(query=subj_query)
    self.conn.run(query=obj_query)
    self.conn.run(query=rel_query)
5.3 检索
接口ExtractorBase的另一个实现则是关键词抽取器KeywordExtractor，负责提取用户问题中涉及的实体关键词，它也是借助大模型的能力实现的，同样继承于LLExtractor，提示词模板如下。

KEYWORD_EXTRACT_PT = (
    "A question is provided below. Given the question, extract up to "
    "keywords from the text. Focus on extracting the keywords that we can use "
    "to best lookup answers to the question.\n"
    "Generate as more as possible synonyms or alias of the keywords "
    "considering possible cases of capitalization, pluralization, "
    "common expressions, etc.\n"
    "Avoid stopwords.\n"
    "Provide the keywords and synonyms in comma-separated format."
    "Formatted keywords and synonyms text should be separated by a semicolon.\n"
    "---------------------\n"
    "Example:\n"
    "Text: Alice is Bob's mother.\n"
    "Keywords:\nAlice,mother,Bob;mummy\n"
    "Text: Philz is a coffee shop founded in Berkeley in 1982.\n"
    "Keywords:\nPhilz,coffee shop,Berkeley,1982;coffee bar,coffee house\n"
    "---------------------\n"
    "Text: {text}\n"
    "Keywords:\n"
)
关键词的抽取涉及到文本中实体识别技术，在构造提示词时需要考虑单词的大小写、别称、同义词等情况，这部分还有很大的优化空间。另外，借助于模型微调直接翻译自然语言到图查询语句也是值得探索的方向。

图存储接口GraphStoreBase提供了基于关键词的探索接口 explore，会根据抽取的关键词召回局部子图。

@abstractmethod
def explore(
    self,
    subs: List[str],
    direct: Direction = Direction.BOTH,
    depth: Optional[int] = None,
    fan: Optional[int] = None,
    limit: Optional[int] = None,
) -> Graph:
    """Explore on graph."""
这里对接口含义做补充说明：

subs：子图搜索的起点列表。
direct：搜索方向，默认双向搜索，即同时探索引用和被引用关系。
depth：搜索深度，控制图搜索的最大跳数，默认不做限制。
fan：扇出限制，控制每一跳的最大邻居数，避免数据热点问题，默认不做限制。
limit：结果边数限制，默认不做限制。
返回值：Graph接口类型，表示搜索结果子图，提供了便捷的点边更新API。
TuGraph的explore接口实现核心逻辑是将上述参数转化为Cypher查询语句，形如：

query = (
    f"MATCH p=(n:{self._node_label})"
    f"-[r:{self._edge_label}*1..{depth}]-(m:{self._node_label}) "
    f"WHERE n.id IN {subs} RETURN p LIMIT {limit}"
)
5.4 生成
和其他向量数据库类似，BuiltinKnowledgeGraph同样实现了IndexStoreBase的相似性查询接口。

```  async def asimilar_search_with_scores(
    self,
    text,
    topk,
    score_threshold: float,
    filters: Optional[MetadataFilters] = None,
) -> List[Chunk]:
    """Search neighbours on knowledge graph."""
    if not filters:
        logger.info("Filters on knowledge graph not supported yet")
    # extract keywords and explore graph store
    keywords = await self._keyword_extractor.extract(text)
    subgraph = self._graph_store.explore(keywords, limit=topk)
    logger.info(f"Search subgraph from {len(keywords)} keywords")

    content = (
        "The following vertices and edges data after [Subgraph Data] "
        "are retrieved from the knowledge graph based on the keywords:\n"
        f"Keywords:\n{','.join(keywords)}\n"
        "---------------------\n"
        "You can refer to the sample vertices and edges to understand "
        "the real knowledge graph data provided by [Subgraph Data].\n"
        "Sample vertices:\n"
        "(alice)\n"
        "Sample edges:\n"
        "(alice)-[reward]->(alice)\n"
        "---------------------\n"
        f"Subgraph Data:\n{subgraph.format()}\n"
    )
    return [Chunk(content=content, metadata=subgraph.schema())]` 
关键词通过关键词抽取器_keyword_extractor完成，抽取到的关键词传递给图存储对象_graph_store进行子图探索，探索结果子图直接格式化到提示词上下文字符串content内。

细心的读者可以发现，子图探索的结果直接封装为Graph接口类型，我们甚至还提供了一个MemoryGraph工具类实现。这样实现图探索接口时，就无需将查询结果转化为Path/Table等内存不友好的格式了，同时也降低了提示词中编码子图数据的token开销。当然这是建立大模型对Graph数据结构原生的理解基础上，我们相信这是当下主流大模型的基本能力。
Graph接口的核心API

