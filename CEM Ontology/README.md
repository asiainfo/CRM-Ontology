## CEM：客户服务本体（Customer Experience Management Ontology）

### 简介
CEM（客户服务本体）是一套面向通信业务场景的语义模型，聚焦客户体验（Customer Experience）相关的对象、事件、工单、网络、产品与终端。CEM 通过本体论方法系统化定义：
- 领域对象：客户、客户行为画像、网络（宽带/无线）、产品（套餐/增值）、终端、感知分析、感知评估、修复策略、事件、工单、员工等；
- 核心关系：订购（客户↔产品）、依赖/支持（产品↔网络）、使用（终端↔网络）、指派（工单↔员工）、发起（客户↔事件）、引用（工单↔修复策略）、关联（客户/事件↔工单）、拥有（客户↔终端）；
- 数据属性：标识、账单/费用、使用/饱和度、语音/通话、消息/视频/网页体验、网络质量/RSRP、投诉/咨询/申告、宽带/ITV/天翼/权益、画像/地域/栅格、时间与系统标识等；
- 可调用函数：行动（Action）与逻辑（Logic），并通过参数对象统一描述形参与复杂类型。

模型复用并对齐 PROV‑O（`prov:Entity`/`prov:Activity`），以 `ex:Entity` 抽象实体、以 `ex:Action`/`ex:Logic` 抽象活动；关系键联动通过 `ex:domainAttribute`/`ex:rangeAttribute` 与桥接对象（`ex:hasMiddleObject`）实现多对多关联。

### 版本
- 命名空间（base IRI）：`http://asiainfo.com/example-owl#`
- 本体名称类：`ex:CEM a ex:ontologyName`
- 当前版本：1.0（与 `CEM_Vocabulary.md` 保持一致）

### 快速开始
1) 阅读 `CEM_Vocabulary.md` 了解对象、关系与数据属性分组及 IRI 后缀。
2) 将 `CEM.owl` 导入三元组库（如 Neo4j+RDF、Jena 或 GraphDB），或在应用内加载作语义模型。
3) 按需实例化客户/网络/产品/终端/事件/工单等对象，并使用关系子属性（如 `order`、`depends_on`、`use`、`assign`、`initiate_`、`References`、`linkedWith`、`has`）进行业务建模与查询。

### 文件总览
- `CEM.owl`：CEM 核心本体（OWL/RDF）。定义 `ex:customer`、`ex:customerbehavior`、`ex:broadbandnetwork`、`ex:wirelessnetwork`、`ex:packageproduct`、`ex:valueaddedproduct`、`ex:terminal`、`ex:event`、`ex:workorder`、`ex:employee`、`ex:perception`、`ex:perceptionevaluation`、`ex:remediationstrategy` 等类；对象属性包含 `bindAction`、`bindLogic`、`hasParameter`、`custom_relation` 及其子属性（`order`、`depends_on`、`use`、`assign`、`initiate_`、`References`、`linkedWith`、`has` 等），并以 `hasMiddleObject` 支持桥接对象，辅以 `domainAttribute`/`rangeAttribute` 键注解。
- `CEM_Vocabulary.md`：人类可读的词汇参考，细化类、对象属性（含详细枚举表）、数据属性（分主题与按类拆分）、命名个体/枚举（如事件类型、工单类型）、以及 IRI 后缀（Local Names）。


### 标准对齐
CEM 复用并对齐：
- PROV‑O：`prov:Entity`/`prov:Activity` 对应 `ex:Entity` 与 `ex:Action`/`ex:Logic`，并沿用活动-实体的通用抽象。
- XSD：数据属性值域类型使用 `xsd` 基本类型（string、int、decimal、dateTime、gYearMonth 等）。

## 参与贡献
欢迎通过 Issue/PR 提出新的类/属性、报告问题或完善文档与本体模型。也欢迎补充示例与最佳实践文档。

### 许可协议
请在仓库根目录添加 `LICENSE` 文件并在此声明协议。
