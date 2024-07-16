# GraphRAG
survey for GraphRAG
## microsoft
* [1][GraphRAG: New tool for complex data discovery now on GitHub ](https://www.microsoft.com/en-us/research/blog/graphrag-new-tool-for-complex-data-discovery-now-on-github/)
  * [Github](https://github.com/microsoft/graphrag)
  * [GraphRAG Accelerator](https://github.com/Azure-Samples/graphrag-accelerator/?tab=readme-ov-file)
  * [dataset](https://github.com/yixuantt/MultiHop-RAG/)_
* [2][GraphRAG: Unlocking LLM discovery on narrative private data](https://www.microsoft.com/en-us/research/blog/graphrag-unlocking-llm-discovery-on-narrative-private-data/)  
* [3][From Local to Global: A Graph RAG Approach to Query-Focused Summarization](https://www.microsoft.com/en-us/research/publication/from-local-to-global-a-graph-rag-approach-to-query-focused-summarization/)

### BaselineRAG VS GraphRAG
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


 













## Ant
*[Vector | Graph：蚂蚁首个开源Graph RAG框架设计解读](https://developer.aliyun.com/article/1540097)
