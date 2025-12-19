## PMT：产品营销本体（Product Marketing Ontology）

### 简介
Product Marketing Ontology（产品营销本体）是一套面向电信产品营销场景的语义模型，聚焦“产品—用户—渠道—活动”全链路。该本体通过本体论方法系统化定义：
- 领域对象：营销活动（Campaign）、渠道（ChannelInfo）、渠道接触记录（ContactRecord）、历史营销数据（HistoricalMarketingData）、营销文案（MarketingContent）、产品目录（ProductCatalog）、产品策略/画像（ProductStrategy）、用户基础信息（UserInfo）、用户画像（UserProfile）、用户行为（UserBehavior）等；
- 核心关系：拥有（ProductCatalog↔ProductStrategy / UserInfo↔UserProfile / UserInfo↔UserBehavior / ProductCatalog↔Campaign / Campaign↔ContactRecord）、属于/被属于（Campaign↔MarketingContent / Campaign↔HistoricalMarketingData / UserProfile↔UserBehavior）、关联（ProductCatalog↔ContactRecord）、引用/被引用（UserBehavior↔ContactRecord / ContactRecord↔ChannelInfo）等；
- 数据属性：标识与时间分区（活动ID、产品ID、渠道ID、用户ID、日期、分区字段等）、活动与营销效果指标（预算、目标用户数、触达数、转化数、转化率、ROI等）、渠道与文案配置（渠道类型、规则、统计，文案标题/正文/模板变量/适用人群等）、产品与权益属性（价格、合约期、流量/语音资源、权益与会员应用等）、用户基础&画像&行为标签（终端/资费、客群、兴趣偏好、消费与缴费行为等）；
- 可调用函数：逻辑函数（Logic）与行动（Action），并通过函数参数对象统一描述参数名、类型、是否可选及复杂类型（列表/字典）。

模型复用并对齐 PROV‑O（`prov:Entity`/`prov:Activity`），以 `ex:Entity` 抽象实体、以 `ex:Action`/`ex:Logic` 抽象活动；对象关系键联动通过 `ex:domainAttribute`/`ex:rangeAttribute` 及 `ex:custom_relation` 的子属性建模，必要时可引入中间对象配合 `ex:hasMiddleObject` 支持多对多关联。

### 版本
- 命名空间（base IRI）：`http://asiainfo.com/example-owl#`
- 本体名称类：`ex:Product_marketing a ex:ontologyName`
- 当前版本：1.0（与 `product_marketing_Vocabulary.md` / `product.md` 保持一致）

### 快速开始
1) 阅读 `product_marketing_Vocabulary.md`（或 `product.md`）  
   - 了解产品营销本体中的类（Campaign/ChannelInfo/ProductCatalog/UserInfo 等）、对象属性（拥有/属于/关联/引用等关系）与数据属性分组（活动指标、用户画像、产品权益等），以及各 IRI 后缀（Local Names）。
2) 将 `product_marketing.owl` 导入三元组库  
   - 如 Neo4j+RDF、Jena、GraphDB 等，或在应用内加载作为统一语义模型；  
   - 建议结合 CEM 本体一起加载，以实现“客户体验+产品营销”的一体化语义视图。
3) 按需实例化对象并建立关系  
   - 典型对象：Campaign、ChannelInfo、MarketingContent、ProductCatalog、ProductStrategy、UserInfo、UserProfile、UserBehavior、ContactRecord、HistoricalMarketingData 等；  
   - 使用关系子属性（`has`、`was_owned`、`belonged_to`、`isPartOf`、`linkedWith`、`is_linked_to`、`isReferencedBy`、`BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL`、`TransmissionResourceData_belongsTo`、`ComprehensiveManagementData_belongsTo` 等）结合 `domainAttribute`/`rangeAttribute` 所指示的数据属性（活动ID/产品ID/用户ID/渠道ID）进行建模与查询。
4) 绑定逻辑与行动  
   - 利用 `ex:bindLogic` 把推荐/匹配/评估函数（如 `recommend_products`、`match_product_to_users`、`evaluate_campaign`）绑定到相应对象视图（UserProfile、ProductCatalog、ContactRecord 等）；  
   - 利用 `ex:bindAction` 绑定可执行动作（如 `ExecuteTouchAction`、`RecordContactHistory`、`UpdateConversionStatus`），并通过 `ex:Parameter` 统一描述调用参数。

### 文件总览
- `product_marketing.owl`：产品营销核心本体（OWL/RDF）。  
  - 定义类：`ex:Campaign`、`ex:ChannelInfo`、`ex:ContactRecord`、`ex:HistoricalMarketingData`、`ex:MarketingContent`、`ex:ProductCatalog`、`ex:ProductStrategy`、`ex:UserInfo`、`ex:UserProfile`、`ex:UserBehavior` 等；  
  - 对象属性：  
    - 语义绑定类：`ex:bindAction`、`ex:bindLogic`、`ex:hasParameter`、`ex:paramTypeNode` 等；  
    - 业务关系类（均为 `ex:custom_relation` 的子属性）：`ex:has`、`ex:was_owned`、`ex:belonged_to`、`ex:isPartOf`、`ex:linkedWith`、`ex:is_linked_to`、`ex:isReferencedBy`、`ex:BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL`、`ex:TransmissionResourceData_belongsTo`、`ex:ComprehensiveManagementData_belongsTo` 等，配合 `ex:domainAttribute`/`ex:rangeAttribute` 完成基于键的对象关联。  
  - 逻辑与行动：定义 `ex:evaluate_campaign`、`ex:match_product_to_users`、`ex:recommend_products` 等逻辑函数，以及 `ex:ExecuteTouchAction`、`ex:RecordContactHistory`、`ex:UpdateConversionStatus` 等行动，并通过 `ex:Parameter` 描述参数结构。
- `product_marketing_Vocabulary.md`：人类可读的产品营销本体词汇表，完整说明各类、对象属性、数据属性（分主题与按类拆分）、建模约束与示例绑定。
- `product.md`：基于产品营销本体的精简版/聚焦版词汇文档，偏重用户侧（UserInfo/UserProfile/UserBehavior）属性与关系，可用于用户画像&推荐场景的快速对接说明。

### 标准对齐
Product_Marketing 复用并对齐：
- PROV‑O：`prov:Entity`/`prov:Activity` 分别对应 `ex:Entity` 与 `ex:Action`/`ex:Logic`，统一行动与逻辑函数的抽象语义；
- XSD：数据属性值域类型使用 `xsd` 基本类型（string、int、decimal、date、dateTime 等），便于在不同实现平台间保持一致；
- 与 CEM 本体互补：在同一命名空间下，与 `CEM` 本体中客户体验相关对象（客户、事件、工单、网络、终端等）协同建模，实现从“体验”到“营销”的完整语义闭环。

## 参与贡献
欢迎通过 Issue/PR 提出新的类/属性、报告问题或完善文档与本体模型，也欢迎补充具体业务场景的建模案例（如具体产品包、渠道策略、客群标签等）。

### 许可协议
请在仓库根目录添加或复用 `LICENSE` 文件，并在此声明协议。
