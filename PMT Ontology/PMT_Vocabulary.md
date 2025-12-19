## 产品营销 本体词汇表（Ontology Vocabulary）

- 版本: 1.0
- 命名空间（base IRI）: `http://asiainfo.com/example-owl#`
- 本体名称: `ex:Product_marketing`（产品营销）
- 创建日期: 2025-12-19
- 简述: 定义产品营销（Product Marketing）语义模型的核心类、对象属性、数据属性与可调用逻辑/行动，用于描述产品、用户、渠道、营销活动、历史营销记录及画像与行为特征等要素及其关系。

### 前缀（Prefixes）

- `rdf`: `http://www.w3.org/1999/02/22-rdf-syntax-ns#`
- `rdfs`: `http://www.w3.org/2000/01/rdf-schema#`
- `owl`: `http://www.w3.org/2002/07/owl#`
- `xsd`: `http://www.w3.org/2001/XMLSchema#`
- `prov`: `http://www.w3.org/ns/prov#`
- `dcterms`: `http://purl.org/dc/terms/`
- `ex`: `http://asiainfo.com/example-owl#`

---

## 目录
- [产品营销 本体词汇表（Ontology Vocabulary）](#产品营销-本体词汇表ontology-vocabulary)
  - [前缀（Prefixes）](#前缀prefixes)
- [目录](#目录)
- [概览与适用范围](#概览与适用范围)
- [IRI 后缀（Local Names）](#iri-后缀local-names)
- [类（Classes）](#类classes)
  - [核心与抽象](#核心与抽象)
  - [领域对象](#领域对象)
    - [用户与画像：`ex:UserInfo`、`ex:UserProfile`、`ex:UserBehavior`](#用户与画像exuserinfoexuserprofileexuserbehavior)
    - [产品与策略：`ex:ProductCatalog`、`ex:ProductStrategy`](#产品与策略exproductcatalogexproductstrategy)
    - [渠道与触达：`ex:ChannelInfo`、`ex:ContactRecord`](#渠道与触达exchannelinfoexcontactrecord)
    - [活动与历史：`ex:Campaign`、`ex:HistoricalMarketingData`、`ex:MarketingContent`](#活动与历史excampaignexhistoricalmarketingdataexmarketingcontent)
  - [本体名称](#本体名称)
  - [行动与逻辑](#行动与逻辑)
    - [行动（Actions）](#行动actions)
    - [逻辑函数（Logics）](#逻辑函数logics)
- [对象属性（Object Properties）](#对象属性object-properties)
  - [绑定属性：`bindAction`/`bindLogic`/`hasParameter`](#绑定属性bindactionbindlogichasparameter)
  - [关系分组：拥有/属于/引用/关联](#关系分组拥有属于引用关联)
  - [详细对象属性表](#详细对象属性表)
- [数据属性（Datatype Properties）](#数据属性datatype-properties)
  - [标识与元数据](#标识与元数据)
  - [营销活动与渠道](#营销活动与渠道)
  - [营销文案与内容效果](#营销文案与内容效果)
  - [历史营销与收益](#历史营销与收益)
  - [用户信息与画像特征](#用户信息与画像特征)
  - [产品配置与权益](#产品配置与权益)
  - [按类拆分（Domain→Properties）](#按类拆分domainproperties)
- [命名个体与枚举（Named Individuals & Enums）](#命名个体与枚举named-individuals--enums)
- [建模约束与规则（Axioms）](#建模约束与规则axioms)
- [示例绑定（Examples）](#示例绑定examples)
- [修订记录](#修订记录)

---

## 概览与适用范围
- 目标: 为产品营销业务构建统一的语义模型，覆盖用户、产品、渠道、活动、历史记录等对象，以及推荐/匹配/评估等逻辑函数与执行触达/记录历史等行动。
- 对齐标准: 复用 `PROV-O`（`prov:Entity`/`prov:Activity`），抽象类 `ex:Entity` 与 `ex:Action`/`ex:Logic` 与 PROV-O 对齐；通用关系模式沿用 CEM 本体中的 `ex:custom_relation`、`ex:domainAttribute`、`ex:rangeAttribute` 等注解设计。

---

## IRI 后缀（Local Names）
以下列出常用类、对象属性与数据属性的 IRI 后缀（即本体命名空间 `http://asiainfo.com/example-owl#` 之后的本地名）。

- 命名空间前缀：`ex:` → `http://asiainfo.com/example-owl#`

### 类（Classes）后缀
- 抽象与核心：`Entity`、`Object`、`Action`、`Logic`、`Parameter`、`ListType`、`DictType`、`ontologyName`
- 领域对象：`Campaign`、`ChannelInfo`、`ContactRecord`、`HistoricalMarketingData`、`MarketingContent`、`ProductCatalog`、`ProductStrategy`、`UserBehavior`、`UserInfo`、`UserProfile`

### 对象属性（Object Properties）后缀
- 绑定与参数：`bindAction`、`bindLogic`、`hasParameter`、`paramTypeNode`、`hasMiddleObject`
- 通用关系：`custom_relation`
- 业务关系：`isReferencedBy`、`BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL`、`belonged_to`、`TransmissionResourceData_belongsTo`、`was_owned`、`has`、`ComprehensiveManagementData_belongsTo`、`isPartOf`、`is_linked_to`、`linkedWith`

### 数据属性（Datatype Properties）后缀（节选）
- 键注解：`hasPrimaryKey`、`hasTitle`、`domainAttribute`、`rangeAttribute`
- 活动与渠道：`活动ID`、`活动名称`、`渠道ID`、`渠道名`、`活动状态`、`预算金额`、`开始时间`、`结束时间`、`目标用户数`、`触达用户数`、`转化用户数`、`AI推荐`
- 文案与内容：`文案ID`、`文案名称`、`标题`、`副标题`、`正文`、`按钮文字`、`按钮链接`、`内容标签`、`文案类型`、`AB测试组`、`适用人群`、`适用产品`、`展示数`、`点击数`、`点击率`、`转化数`、`转化率`
- 历史记录：`实际触达数`、`实际转化数`、`平均匹配分`、`总成本`、`总收入`、`投资回报率`、`目标受众特征`
- 用户与画像：`用户ID`、`电话号码`、`年龄`、`性别`、`存量用户星级`、`手机账户余额`、`当月使用流量` 等画像行为度量
- 产品与权益：`产品ID`、`产品名称`、`产品类型`、`产品原价`、`产品现价`、`产品标签`、`赠送金额`、`产品专用流量`、`产品本地流量`、`会员等级`、`音乐应用`、`视频应用`、`体育应用` 等
- 通用元数据：`创建时间`、`更新时间`、`分区字段`、`日期`

---

## 类（Classes）

### 核心与抽象

| 术语 | 继承自 | 标签 | 简述 |
|---|---|---|---|
| `ex:Entity` | `prov:Entity` | 实体 | 所有领域对象的抽象上位类 |
| `ex:Object` | `ex:Entity` | 本体对象 | 可持久化的业务对象（表级/宽表） |
| `ex:Action` | `prov:Activity` | 行动 | 可执行动作（带副作用） |
| `ex:Logic` | `prov:Activity` | 决策/逻辑函数 | 纯逻辑/评分/推荐等函数 |
| `ex:Parameter` | - | 函数参数 | 行动/逻辑的参数节点 |
| `ex:ListType` | - | 列表类型 | 参数复杂类型：列表 |
| `ex:DictType` | - | 字典类型 | 参数复杂类型：字典 |
| `ex:ontologyName` | - | 本体名称 | 用于标识本体实例（如 `ex:Product_marketing`） |

### 领域对象

| 术语 | 继承自 | 标签 | 简述 |
|---|---|---|---|
| `ex:Campaign` | `ex:Object` | 营销活动 | 记录营销活动的配置与执行统计 |
| `ex:ChannelInfo` | `ex:Object` | 渠道 | 渠道静态属性与业务规则 |
| `ex:ContactRecord` | `ex:Object` | 渠道记录 | 用户营销接触明细数据 |
| `ex:HistoricalMarketingData` | `ex:Object` | 营销记录 | 历史营销活动执行及转化结果 |
| `ex:MarketingContent` | `ex:Object` | 营销文案 | 文案模板与内容配置 |
| `ex:ProductCatalog` | `ex:Object` | 产品 | 产品目录与资源配置 |
| `ex:ProductStrategy` | `ex:Object` | 产品画像 | 产品策略与商务规则宽表 |
| `ex:UserBehavior` | `ex:Object` | 用户行为 | 浏览、查询、接触行为数据 |
| `ex:UserInfo` | `ex:Object` | 用户 | 用户基础信息 |
| `ex:UserProfile` | `ex:Object` | 用户画像 | 用户价值/资源/偏好画像宽表 |

#### 用户与画像：`ex:UserInfo`、`ex:UserProfile`、`ex:UserBehavior`
上述三类用于承载用户基础信息、价值画像与行为明细：
- `ex:UserInfo`：用户静态档案，如性别、年龄、星级、终端类型等；
- `ex:UserProfile`：用户消费与资源使用画像，如账户余额、通用流量、当月使用流量、权益订购情况等；
- `ex:UserBehavior`：用户在各渠道上的浏览/查询/接触行为统计。

#### 产品与策略：`ex:ProductCatalog`、`ex:ProductStrategy`
- `ex:ProductCatalog`：产品目录对象，描述产品类型、价格、资源包、权益范围、适用人群等静态配置；
- `ex:ProductStrategy`：产品策略对象，记录各类营销策略、优惠价格、是否可兑换等策略维度。

#### 渠道与触达：`ex:ChannelInfo`、`ex:ContactRecord`
- `ex:ChannelInfo`：渠道配置信息，如渠道类型（短信/APP/弹窗/外呼）、是否可办理、是否推送、是否重复等；
- `ex:ContactRecord`：渠道接触记录，记录每次触达的时间、是否接收、是否成功、是否订单、通话时长、市场人员等。

#### 活动与历史：`ex:Campaign`、`ex:HistoricalMarketingData`、`ex:MarketingContent`
- `ex:Campaign`：活动配置对象，记录活动名称、内容ID、预算、起止时间、状态等；
- `ex:HistoricalMarketingData`：历史营销执行记录，包含目标用户数、触达数、办理数、转化率、成本/收入等；
- `ex:MarketingContent`：具体文案对象，包括标题、副标题、正文、按钮文字/链接、AB 测试组、适用客群与统计指标。

### 本体名称
- `ex:Product_marketing a ex:ontologyName`，标签为“产品营销”。

### 行动与逻辑

| 术语 | 继承自 | 标签 | 简述 |
|---|---|---|---|
| `ex:evaluate_campaign` | `ex:Logic` | 营销方案评估 | 预测营销方案转化率并给出风险与优化建议 |
| `ex:match_product_to_users` | `ex:Logic` | 产品筛选用户群 | 按产品与画像筛选目标用户并创建活动 |
| `ex:recommend_products` | `ex:Logic` | 用户推荐产品 | 基于用户画像推荐产品并选择最优渠道 |
| `ex:ExecuteTouchAction` | `ex:Action` | 执行触达动作 | 按活动批量对用户执行 10086 弹窗触达 |
| `ex:RecordContactHistory` | `ex:Action` | 回填渠道历史信息 | 批量写入用户接触历史到 `ex:ContactRecord` |
| `ex:UpdateConversionStatus` | `ex:Action` | 更新用户办理状态 | 更新办理状态并同步统计到活动与历史数据 |

- 逻辑/行动参数通过 `ex:hasParameter` 声明，参数具名、类型（`xsd:string`/`xsd:double`/`xsd:integer`/`xsd:boolean` 等）与是否可选；复杂参数通过 `ex:paramTypeNode` 指向 `ex:ListType`/`ex:DictType`。

#### 行动（Actions）
`ex:ExecuteTouchAction`、`ex:RecordContactHistory`、`ex:UpdateConversionStatus` 等。

#### 逻辑函数（Logics）
`ex:evaluate_campaign`、`ex:match_product_to_users`、`ex:recommend_products` 等。

---

## 对象属性（Object Properties）

以下列出主要对象属性，含域（Domain）、值域（Range）与说明。大部分对象属性为 `ex:custom_relation` 的子属性，用于表达领域关系；同时使用 `ex:domainAttribute`/`ex:rangeAttribute` 注解关系两端连接所用的数据属性。

基本绑定属性：
- `ex:bindAction`（Domain: `ex:Object`，Range: `ex:Action`）— 对象绑定可执行行动；
- `ex:bindLogic`（Domain: `ex:Object`，Range: `ex:Logic`）— 对象绑定可调用逻辑；
- `ex:hasParameter`（Domain: `ex:Logic`/`ex:Action`，Range: `ex:Parameter`）— 逻辑/行动拥有的参数。

#### 绑定属性：`bindAction`/`bindLogic`/`hasParameter`
- `ex:Campaign ex:bindAction ex:ExecuteTouchAction`；
- `ex:ContactRecord ex:bindAction ex:RecordContactHistory`、`ex:ContactRecord ex:bindAction ex:UpdateConversionStatus`；
- `ex:UserProfile`、`ex:UserInfo`、`ex:ProductStrategy`、`ex:ProductCatalog`、`ex:ChannelInfo`、`ex:ContactRecord` 等对象均通过 `ex:bindLogic` 绑定上述推荐/评估函数。

#### 关系分组：拥有/属于/引用/关联
典型分组示例：
- 拥有/被拥有：`ex:has`（产品/用户信息/活动对策略/画像/记录的拥有关系）与 `ex:was_owned`；
- 属于/被属于：`ex:isPartOf`、`ex:belonged_to`（画像与行为、活动与历史数据之间的所属关系）；
- 引用/被引用：`ex:BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL` 与 `ex:isReferencedBy`（行为/记录/渠道之间的引用关系）；
- 关联/被关联：`ex:linkedWith` 与 `ex:is_linked_to`（产品与接触记录之间的业务关联）。

### 详细对象属性表

| 属性 | 标签 | Domain | Range | 逆属性 | 子属性于 | 桥接对象 `ex:hasMiddleObject` | 键注解（Domain/Range） | 说明 |
|---|---|---|---|---|---|---|---|---|
| `ex:bindAction` | 绑定行动 | `ex:Object` | `ex:Action` | - | - | - | - | 对象可执行的行动绑定 |
| `ex:bindLogic` | 绑定逻辑 | `ex:Object` | `ex:Logic` | - | - | - | - | 对象可调用的逻辑函数绑定 |
| `ex:hasParameter` | 拥有参数 | `ex:Action`/`ex:Logic` | `ex:Parameter` | - | - | - | - | 逻辑/行动的参数声明 |
| `ex:isReferencedBy` | 被引用 | `ex:ContactRecord` | `ex:UserBehavior` | `ex:BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:用户ID`；`ex:rangeAttribute`=`ex:用户ID` | 渠道接触记录被行为记录引用 |
| `ex:BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL` | 引用 | `ex:UserBehavior` | `ex:ContactRecord` | `ex:isReferencedBy` | `ex:custom_relation` | - | 同上 | 用户行为引用接触记录 |
| `ex:BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL` | 引用 | `ex:ContactRecord` | `ex:ChannelInfo` | `ex:isReferencedBy` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:ID`；`ex:rangeAttribute`=`ex:渠道ID` | 接触记录引用渠道配置 |
| `ex:isReferencedBy` | 被引用 | `ex:ChannelInfo` | `ex:ContactRecord` | `ex:BUSINESSOBJECTATTRIBUTEVALUE__INJECTIONLABEL` | `ex:custom_relation` | - | 同上 | 渠道被接触记录引用 |
| `ex:belonged_to` | 被属于 | `ex:MarketingContent` | `ex:Campaign` | `ex:TransmissionResourceData_belongsTo` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:文案ID`；`ex:rangeAttribute`=`ex:内容ID` | 文案被活动引用 |
| `ex:TransmissionResourceData_belongsTo` | 属于 | `ex:Campaign` | `ex:MarketingContent` | `ex:belonged_to` | `ex:custom_relation` | - | 同上 | 活动关联具体文案 |
| `ex:was_owned` | 被拥有 | `ex:ProductStrategy` | `ex:ProductCatalog` | `ex:has` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:产品ID`；`ex:rangeAttribute`=`ex:产品ID` | 策略被对应产品拥有 |
| `ex:has` | 拥有 | `ex:ProductCatalog` | `ex:ProductStrategy` | `ex:was_owned` | `ex:custom_relation` | - | 同上 | 产品拥有一个或多个策略画像 |
| `ex:was_owned` | 被拥有 | `ex:UserProfile` | `ex:UserInfo` | `ex:has` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:用户ID`；`ex:rangeAttribute`=`ex:用户ID` | 用户画像被用户拥有 |
| `ex:has` | 拥有 | `ex:UserInfo` | `ex:UserProfile` | `ex:was_owned` | `ex:custom_relation` | - | 同上 | 用户拥有画像宽表 |
| `ex:isPartOf` | 属于 | `ex:UserProfile` | `ex:UserBehavior` | `ex:belonged_to` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:用户ID`；`ex:rangeAttribute`=`ex:用户ID` | 画像属于行为数据视角 |
| `ex:belonged_to` | 被属于 | `ex:UserBehavior` | `ex:UserProfile` | `ex:isPartOf` | `ex:custom_relation` | - | 同上 | 行为从画像视角被关联 |
| `ex:belonged_to` | 被属于 | `ex:HistoricalMarketingData` | `ex:Campaign` | `ex:ComprehensiveManagementData_belongsTo` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:活动ID`；`ex:rangeAttribute`=`ex:活动ID` | 历史营销记录被活动聚合 |
| `ex:ComprehensiveManagementData_belongsTo` | 属于 | `ex:Campaign` | `ex:HistoricalMarketingData` | `ex:belonged_to` | `ex:custom_relation` | - | 同上 | 活动关联历史执行记录 |
| `ex:is_linked_to` | 被关联 | `ex:ContactRecord` | `ex:ProductCatalog` | `ex:linkedWith` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:产品ID`；`ex:rangeAttribute`=`ex:产品ID` | 接触记录被产品关联 |
| `ex:linkedWith` | 关联 | `ex:ProductCatalog` | `ex:ContactRecord` | `ex:is_linked_to` | `ex:custom_relation` | - | 同上 | 产品关联接触记录 |
| `ex:has` | 拥有 | `ex:ContactRecord` | `ex:Campaign` | `ex:was_owned` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:活动ID`；`ex:rangeAttribute`=`ex:活动ID` | 接触记录指向所属活动 |
| `ex:was_owned` | 被拥有 | `ex:Campaign` | `ex:ContactRecord` | `ex:has` | `ex:custom_relation` | - | 同上 | 活动拥有多条接触记录 |

---

## 数据属性（Datatype Properties）

- 键注解：`ex:hasPrimaryKey`（类级主键数据属性）、`ex:hasTitle`（类级标题数据属性）。
- 键关联注解：`ex:domainAttribute`、`ex:rangeAttribute`（用于关系两端通过哪一数据属性进行键匹配）。

### 标识与元数据
- 通用标识：`ex:ID`（多对象的自增主键）、`ex:自增主键`（画像与策略类主键）。
- 活动与文案：`ex:活动ID`、`ex:活动名称`、`ex:内容ID`、`ex:文案ID`、`ex:文案名称`。
- 渠道与用户：`ex:渠道ID`、`ex:渠道名`、`ex:用户ID`、`ex:电话号码`。
- 时间元数据：`ex:创建时间`、`ex:更新时间`、`ex:开始时间`、`ex:结束时间`、`ex:日期`（分区字段）、`ex:分区字段` 等。

### 营销活动与渠道
- 活动配置：`ex:预算金额`（`xsd:decimal`）、`ex:AI推荐`（`xsd:int`）、`ex:当前转化率`（`xsd:decimal`）、`ex:活动状态`（`xsd:string`，如 CREATED/RUNNING/FINISHED 等）。
- 目标与结果：`ex:目标用户数`、`ex:触达用户数`、`ex:转化用户数`（均为 `xsd:int`）。
- 渠道属性：`ex:渠道类型`（短信/APP/弹窗/外呼等）、`ex:是否有效`、`ex:是否推送`、`ex:是否手动`、`ex:是否有序`、`ex:是否重复`、`ex:近7日统计`、`ex:近3日统计`、`ex:渠道统计` 等。

### 营销文案与内容效果
- 文案基础：`ex:标题`、`ex:副标题`、`ex:正文`、`ex:内容标签`、`ex:文案类型`、`ex:AB测试组`、`ex:适用人群`、`ex:适用产品`、`ex:模板变量`。
- 审批流程：`ex:审批状态`、`ex:审批人`、`ex:审批时间`、`ex:状态`（文案状态）。
- 效果指标：`ex:展示数`、`ex:点击数`、`ex:点击率`、`ex:转化数`、`ex:转化率` 等。

### 历史营销与收益
- 历史执行统计：`ex:实际触达数`、`ex:实际转化数`、`ex:平均匹配分`、`ex:目标用户数`。
- 财务指标：`ex:总成本`、`ex:总收入`、`ex:投资回报率`（`(总收入-总成本)/总成本`）。
- 受众特征：`ex:目标受众特征`（JSON 存储筛选条件）。

### 用户信息与画像特征
- 用户基本信息：`ex:年龄`、`ex:性别`、`ex:存量用户星级`、`ex:是否5G资费用户`、`ex:终端机型品牌`、`ex:终端机型网络类型`、`ex:终端价位段`、`ex:终端机型操作系统` 等。
- 用户价值与余额：`ex:手机账户余额`、`ex:近3月平均ARPU`（如在画像中出现）、`ex:当月使用流量`、`ex:可用通用流量总额度` 等。
- 行为记录：`ex:联系时间`、`ex:通话时长`、`ex:是否尝试推荐`、`ex:联系成功`、`ex:是否订单`、`ex:是否接收`、`ex:是否成功`、`ex:是否智能推荐策划`、`ex:序列号`、`ex:呼叫人员`、`ex:推荐原因`、`ex:执行活动ID`、`ex:策略时间`、`ex:成功时间` 等。

### 产品配置与权益
- 产品标识：`ex:产品ID`、`ex:产品名称`、`ex:产品类型`、`ex:产品业务线条`。
- 价格与优惠：`ex:产品原价`、`ex:产品现价`、`ex:产品办理价格`、`ex:产品原始价格`、`ex:产品优惠价`、`ex:产品优惠价格`、`ex:赠送金额`、`ex:赠送话费金额`、`ex:赠送话费时间` 等。
- 资源权益：`ex:产品专用流量`、`ex:产品本地流量`、`ex:产品国际语音`、`ex:产品包含语音资源`、`ex:产品包含流量资源` 等。
- 会员与场景：`ex:会员等级`、`ex:音乐应用`、`ex:视频应用`、`ex:体育应用`、`ex:阅读应用`、`ex:老人专属`、`ex:学生专属`、`ex:区域限制`、`ex:可叠加`、`ex:可兑换`、`ex:是否可在积分商城中兑换`、`ex:试用会员`、`ex:权益体验时间` 等。

### 按类拆分（Domain→Properties）
下表仅列出主要对象类的代表性数据属性（非穷尽枚举）：

- `ex:Campaign`：`ex:活动ID`、`ex:活动名称`、`ex:内容ID`、`ex:AI推荐`、`ex:预算金额`、`ex:目标用户数`、`ex:触达用户数`、`ex:转化用户数`、`ex:活动状态`、`ex:开始时间`、`ex:结束时间`、`ex:创建时间`、`ex:更新时间` 等。
- `ex:ChannelInfo`：`ex:渠道ID`、`ex:渠道名`、`ex:渠道类型`、`ex:渠道描述`、`ex:是否有效`、`ex:是否主动`、`ex:是否手动`、`ex:是否有序`、`ex:是否推送`、`ex:是否重复`、`ex:近7日统计`、`ex:近3日统计`、`ex:渠道统计`、`ex:创建时间`、`ex:更新时间` 等。
- `ex:MarketingContent`：`ex:文案ID`、`ex:文案名称`、`ex:标题`、`ex:副标题`、`ex:正文`、`ex:内容标签`、`ex:文案类型`、`ex:AB测试组`、`ex:适用人群`、`ex:适用产品`、`ex:按钮文字`、`ex:按钮链接`、`ex:展示数`、`ex:点击数`、`ex:点击率`、`ex:转化数`、`ex:转化率`、`ex:审批状态`、`ex:审批人`、`ex:审批时间`、`ex:状态`、`ex:创建人`、`ex:生效开始时间`、`ex:生效结束时间` 等。
- `ex:HistoricalMarketingData`：`ex:ID`、`ex:活动ID`、`ex:活动名称`、`ex:产品ID`、`ex:渠道ID`、`ex:目标用户数`、`ex:实际触达数`、`ex:实际转化数`、`ex:转化率`、`ex:平均匹配分`、`ex:总成本`、`ex:总收入`、`ex:投资回报率`、`ex:目标受众特征`、`ex:开始时间`、`ex:结束时间`、`ex:创建时间`、`ex:更新时间` 等。
- `ex:ContactRecord`：`ex:ID`、`ex:活动ID`、`ex:活动名称`、`ex:用户ID`、`ex:产品ID`、`ex:渠道ID`、`ex:联系时间`、`ex:通话时长`、`ex:是否尝试推荐`、`ex:联系成功`、`ex:是否接收`、`ex:是否订单`、`ex:是否成功`、`ex:是否智能推荐策划`、`ex:市场人员`、`ex:职位`、`ex:推荐原因`、`ex:执行活动ID`、`ex:策略时间`、`ex:成功时间`、`ex:序列号`、`ex:创建时间`、`ex:更新时间` 等。
- `ex:ProductCatalog`：`ex:ID`、`ex:产品ID`、`ex:产品名称`、`ex:产品类型`、`ex:产品标签`、`ex:产品原价`、`ex:产品现价`、`ex:产品办理价格`、`ex:产品专用流量`、`ex:产品本地流量`、`ex:产品国际语音`、`ex:赠送金额`、`ex:赠送话费时间`、`ex:可叠加`、`ex:可兑换`、`ex:老人专属`、`ex:学生专属`、`ex:本地地址`、`ex:会员等级`、`ex:音乐应用`、`ex:视频应用`、`ex:体育应用`、`ex:阅读应用`、`ex:区域限制`、`ex:创建时间`、`ex:更新时间` 等。
- `ex:ProductStrategy`：`ex:自增主键`、`ex:产品ID`、`ex:产品业务线条`、`ex:产品原始价格`、`ex:产品办理价格`、`ex:产品优惠价格`、`ex:赠送话费金额`、`ex:是否可在积分商城中兑换`、`ex:体验权益类型`、`ex:权益体验时间`、`ex:创建时间`、`ex:更新时间` 等。
- `ex:UserInfo`：`ex:自增主键`、`ex:用户ID`、`ex:电话号码`、`ex:年龄`、`ex:性别`、`ex:存量用户星级`、`ex:是否5G资费用户`、`ex:终端机型品牌`、`ex:终端机型网络类型`、`ex:终端价位段`、`ex:终端机型操作系统`、`ex:创建时间`、`ex:更新时间` 等。
- `ex:UserProfile`：`ex:自增主键`、`ex:用户ID`、`ex:手机账户余额`、`ex:可用通用流量总额度`、`ex:当月使用流量`、`ex:是否设置视频彩铃`、`ex:是否视频彩铃当月到期` 等画像与资源相关属性。
- `ex:UserBehavior`：`ex:自增主键`、`ex:用户ID`、`ex:分区字段`、各类浏览/查询/触达行为计数属性（具体依宽表字段定义）。

---

## 命名个体与枚举（Named Individuals & Enums）
- 本体中未显式定义以 `owl:NamedIndividual` 形式出现的枚举个体。
- 状态与类型多通过数据属性的允许值体现，例如：
  - 渠道类型：`ex:渠道类型`（允许值如 `SMS`、`APP`、`10086_POPUP`、`OUTBOUND` 等）；
  - 文案/审批状态：`ex:审批状态`（`PENDING`/`APPROVED`/`REJECTED`）、`ex:状态`（`DRAFT`/`ACTIVE`/`INACTIVE`/`ARCHIVED`）；
  - 活动状态：`ex:活动状态`（如 `CREATED`、`RUNNING` 等）。

---

## 建模约束与规则（Axioms）
- 继承与对齐：`ex:Entity ⊑ prov:Entity`；`ex:Action`、`ex:Logic ⊑ prov:Activity`；所有领域对象均继承 `ex:Object`。
- 键注解：对象类通过 `ex:hasPrimaryKey` 指定其主键数据属性，通过 `ex:hasTitle` 指定显示标题数据属性（如 `ex:Campaign` 的主键 `ex:活动ID` 与标题 `ex:活动名称`）。
- 关系键匹配：对象关系子属性通过 `ex:domainAttribute` 与 `ex:rangeAttribute` 指示以何数据属性进行两端键关联；多对多场景可通过 `ex:hasMiddleObject` 指明桥接对象（本本体中主要使用直接键关联）。
- 逻辑/行动参数：通过 `ex:hasParameter` 声明，参数可为基础类型（`xsd:string` 等）或复杂类型（通过 `ex:paramTypeNode` 指向 `ex:ListType`/`ex:DictType`）。

---

## 示例绑定（Examples）
- 对象绑定逻辑：
  - `ex:ProductCatalog ex:bindLogic ex:match_product_to_users`、`ex:ProductCatalog ex:bindLogic ex:evaluate_campaign`、`ex:ProductCatalog ex:bindLogic ex:recommend_products`；
  - `ex:UserProfile ex:bindLogic ex:recommend_products`、`ex:UserProfile ex:bindLogic ex:match_product_to_users`；
  - `ex:UserInfo ex:bindLogic ex:recommend_products`、`ex:UserInfo ex:bindLogic ex:match_product_to_users`；
  - `ex:ProductStrategy ex:bindLogic ex:recommend_products`、`ex:ProductStrategy ex:bindLogic ex:match_product_to_users`、`ex:ProductStrategy ex:bindLogic ex:evaluate_campaign`；
  - `ex:HistoricalMarketingData ex:bindLogic ex:evaluate_campaign`、`ex:ContactRecord ex:bindLogic ex:evaluate_campaign`、`ex:ContactRecord ex:bindLogic ex:match_product_to_users`、`ex:ChannelInfo ex:bindLogic ex:match_product_to_users`。
- 对象绑定行动：
  - `ex:Campaign ex:bindAction ex:ExecuteTouchAction`；
  - `ex:ContactRecord ex:bindAction ex:RecordContactHistory`、`ex:ContactRecord ex:bindAction ex:UpdateConversionStatus`。

---

## 修订记录
- 1.0（2025-12-19）: 初始版本发布（依据 `product_marketing.owl` 结构整理）。

