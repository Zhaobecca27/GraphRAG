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
