## CEM 本体词汇表（Ontology Vocabulary）

- 版本: 1.0
- 命名空间（base IRI）: `http://asiainfo.com/example-owl#`
- 本体名称: `ex:CEM`（客户感知分析）
- 创建日期: 2025-11-27
- 简述: 定义客户感知分析（Customer Experience Management, CEM）语义模型的核心类、对象属性、数据属性与可调用逻辑/行动，用于描述客户、网络、产品、事件、工单、修复策略与行为特征等要素及其关系。

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
- [CEM 本体词汇表（Ontology Vocabulary）](#cem-本体词汇表ontology-vocabulary)
	- [前缀（Prefixes）](#前缀prefixes)
- [目录](#目录)
- [概览与适用范围](#概览与适用范围)
- [IRI 后缀（Local Names）](#iri-后缀local-names)
- [类（Classes）](#类classes)
	- [核心与抽象](#核心与抽象)
	- [领域对象](#领域对象)
		- [网络对象：`ex:broadbandnetwork`、`ex:wirelessnetwork`](#网络对象exbroadbandnetworkexwirelessnetwork)
		- [客户与画像：`ex:customer`、`ex:customerbehavior`](#客户与画像excustomerexcustomerbehavior)
		- [产品与终端：`ex:packageproduct`、`ex:valueaddedproduct`、`ex:terminal`](#产品与终端expackageproductexvalueaddedproductexterminal)
		- [事件与工单：`ex:event`、`ex:workorder`](#事件与工单exeventexworkorder)
		- [感知与评估：`ex:perception`、`ex:perceptionevaluation`](#感知与评估experceptionexperceptionevaluation)
		- [修复策略：`ex:remediationstrategy`](#修复策略exremediationstrategy)
		- [中间对象（桥接类）](#中间对象桥接类)
	- [本体名称](#本体名称)
	- [行动与逻辑](#行动与逻辑)
		- [行动（Actions）](#行动actions)
		- [逻辑函数（Logics）](#逻辑函数logics)
- [对象属性（Object Properties）](#对象属性object-properties)
	- [绑定属性：`bindAction`/`bindLogic`/`hasParameter`](#绑定属性bindactionbindlogichasparameter)
	- [关系分组：订购/依赖/使用/指派/发起/引用/关联/拥有](#关系分组订购依赖使用指派发起引用关联拥有)
	- [详细对象属性表](#详细对象属性表)
- [数据属性（Datatype Properties）](#数据属性datatype-properties)
	- [标识与元数据](#标识与元数据)
	- [账单与费用](#账单与费用)
	- [使用与饱和度](#使用与饱和度)
	- [语音与通话](#语音与通话)
	- [消息/视频/网页体验](#消息视频网页体验)
	- [网络质量与RSRP](#网络质量与rsrp)
	- [投诉/咨询/申告](#投诉咨询申告)
	- [宽带/ITV/天翼/权益](#宽带itv天翼权益)
	- [画像/地域/栅格](#画像地域栅格)
	- [时间与系统标识](#时间与系统标识)
	- [按类拆分（Domain→Properties）](#按类拆分domainproperties)
- [命名个体与枚举（Named Individuals & Enums）](#命名个体与枚举named-individuals--enums)
	- [事件类型（投诉/咨询/故障）](#事件类型投诉咨询故障)
	- [工单类型（网优/装维/万号）](#工单类型网优装维万号)
- [建模约束与规则（Axioms）](#建模约束与规则axioms)
- [示例绑定（Examples）](#示例绑定examples)
- [修订记录](#修订记录)

---

## 概览与适用范围
- 目标: 为客户体验管理构建统一的语义模型，覆盖对象（客户、网络、产品等）、事件与工单、感知评估与修复策略、逻辑函数与行动，以及大量客户行为度量属性。
- 对齐标准: 复用 `PROV-O`（`prov:Entity`/`prov:Activity`），抽象类 `ex:Entity` 与 `ex:Action`/`ex:Logic` 与 PROV-O 对齐。

---

## IRI 后缀（Local Names）
以下列出常用类、对象属性与数据属性的 IRI 后缀（即本体命名空间 `http://asiainfo.com/example-owl#` 之后的本地名）。

- 命名空间前缀：`ex:` → `http://asiainfo.com/example-owl#`

### 类（Classes）后缀
- 抽象与核心：`Entity`、`Object`、`Action`、`Logic`、`Parameter`、`ListType`、`DictType`、`ontologyName`
- 领域对象：`broadbandnetwork`、`wirelessnetwork`、`customer`、`customerbehavior`、`employee`、`event`、`workorder`、`packageproduct`、`valueaddedproduct`、`terminal`、`perception`、`perceptionevaluation`、`remediationstrategy`
- 桥接对象示例：`customer_valueaddedproduct_RC`、`customer_packageproduct_Ar`、`valueaddedproduct_wirelessnetwork_ND`、`packageproduct_broadbandnetwork_OO`、`terminal_wirelessnetwork_9A`、`broadbandnetwork_terminal_Ee`、`workorder_employee_C9`、`customer_event_yf`

### 对象属性（Object Properties）后缀
- 绑定与参数：`bindAction`、`bindLogic`、`hasParameter`、`custom_relation`、`hasMiddleObject`、`domainAttribute`、`rangeAttribute`
- 关系分组：`order`、`be_ordered`、`depends_on`、`support`、`use`、`used`、`assign`、`be_assigned`、`initiate_`、`be_created`、`References`、`isReferencedBy`、`linkedWith`、`is_linked_to`、`has`、`isPartOf`

### 数据属性（Datatype Properties）后缀（选摘）
- 标识与系统：`network_id`、`customer_id`、`work_order_id`、`event_id`、`terminal_id`、`统计月份`、`开通日期`、`系统处理时间`
- 客户基础：`客户ID`、`姓名`、`年龄`、`教育水平`、`收入水平`、`地域分布`、`偏好套餐类型`、`联系方式`、`手机号`
- 使用与通话：`月均流量使用`、`流量饱和度`、`语音时长`、`主叫次数`、`被叫次数`、`本月通话总时长`
- 体验指标：`本月消息接收/发送成功率`、`本月视频播放成功率`、`本月网页显示/响应成功率`、`本月视频播放卡顿总次数`
- 网络质量：`本月RSRP优良率` 及相关 MR 计数（如 `MR计数_≥-105`、`MR计数_≥-115`、`MR计数_<-105`、`MR计数_<-115`）
- 投诉与咨询：`本月投诉次数`、`近3个月投诉次数`、`本月咨询次数`
- 资源拥有：`宽带数`、`ITV数`、`天翼卡数`、`权益产品数`
- 产品与工单：`产品ID`、`产品名称`、`价格`、`工单类型`、`工单状态`、`工单优先级`、`工单内容`、`创建时间`、`关闭时间`
- 感知与评估：`感知ID`、`感知时间`、`感知分析算法`、`感知维度`、`感知评估ID`、`评估描述`、`评估得分`


## 类（Classes）

下表列出主要类，包含继承关系与中文标签。

### 核心与抽象

| 术语 | 继承自 | 标签 | 描述 |
|---|---|---|---|
| `ex:Entity` | `prov:Entity` | 实体 | 与 PROV-O 对齐的通用实体上位类 |
| `ex:Object` | `ex:Entity` | 本体对象 | 需继承此类以声明领域对象 |
| `ex:Action` | `prov:Activity` | 行动 | 可执行的业务行动（如分配工单） |
| `ex:Logic` | `prov:Activity` | 决策/逻辑函数 | 可调用的逻辑函数（如计算满意度） |
| `ex:Parameter` |  | 函数参数 | 逻辑/行动函数的参数对象 |
| `ex:ListType` |  | 列表类型 | 参数类型辅助类 |
| `ex:DictType` |  | 字典类型 | 参数类型辅助类 |
| `ex:ontologyName` |  | 本体名称 | 本体的名称类型 |

### 领域对象

| 术语 | 继承自 | 标签 | 描述 |
|---|---|---|---|
| `ex:broadbandnetwork` | `ex:Object` | 宽带网络 | 宽带接入网络对象 |
| `ex:wirelessnetwork` | `ex:Object` | 无线网络 | 蜂窝/无线接入网络对象 |
| `ex:customer` | `ex:Object` | 客户 | 客户主体对象 |
| `ex:customerbehavior` | `ex:Object` | 客户行为 | 客户的行为与使用特征 |
| `ex:employee` | `ex:Object` | 员工 | 处理工单的员工 |
| `ex:event` | `ex:Object` | 客户事件 | 投诉/咨询/故障等事件 |
| `ex:workorder` | `ex:Object` | 工单 | 各类服务/故障处理工单 |
| `ex:packageproduct` | `ex:Object` | 套餐产品 | 移动/宽带套餐产品 |
| `ex:valueaddedproduct` | `ex:Object` | 增值产品 | 增值/权益类产品 |
| `ex:terminal` | `ex:Object` | 终端 | 终端设备对象 |
| `ex:perception` | `ex:Object` | 感知分析 | 感知分析算法/过程对象 |
| `ex:perceptionevaluation` | `ex:Object` | 感知评估 | 感知评估结果与说明 |
| `ex:remediationstrategy` | `ex:Object` | 修复策略 | 面向低分行为属性的修复策略 |

- 复合/中间对象（用于多对多关系的桥接）示例：`ex:customer_valueaddedproduct_RC`、`ex:valueaddedproduct_wirelessnetwork_ND`、`ex:packageproduct_broadbandnetwork_OO` 等，皆继承 `ex:Object`。

#### 网络对象：`ex:broadbandnetwork`、`ex:wirelessnetwork`
上述两类用于承载宽带/无线网络拓扑与运行元数据。

#### 客户与画像：`ex:customer`、`ex:customerbehavior`
客户主体与行为画像/使用特征的承载类。

#### 产品与终端：`ex:packageproduct`、`ex:valueaddedproduct`、`ex:terminal`
套餐/增值产品与终端设备对象。

#### 事件与工单：`ex:event`、`ex:workorder`
服务事件（投诉/咨询/故障）与处理工单对象。

#### 感知与评估：`ex:perception`、`ex:perceptionevaluation`
感知分析过程与评估结果对象。

#### 修复策略：`ex:remediationstrategy`
针对低分行为属性生成的修复策略对象。

#### 中间对象（桥接类）
用于多对多关系桥接的对象类集合（如 `ex:customer_valueaddedproduct_RC` 等）。

### 本体名称
- `ex:CEM a ex:ontologyName`，标签为“客户感知分析”。

### 行动与逻辑

| 术语 | 继承自 | 标签 | 简述 |
|---|---|---|---|
| `ex:assign_order_to_employee` | `ex:Action` | 分配工单 | 根据工单与员工ID分配工单 |
| `ex:create_work_order` | `ex:Action` | 创建工单 | 按服务类型与感知维度创建工单 |
| `ex:calculate_customer_satisfaction` | `ex:Logic` | 计算客户的满意度 | 输入客户ID与感知ID，输出满意度分数 |
| `ex:generate_remediation_strategy` | `ex:Logic` | 生成修复策略 | 基于低分行为属性生成修复方案 |
| `ex:get_network_logs` | `ex:Logic` | 获取网络工作日志 | 输入网络ID，返回日志数据 |
| `ex:is_low_satisfaction` | `ex:Logic` | 判断是否属于低满意度 | 输入分数，输出布尔判断 |

- 逻辑/行动与对象的绑定：`ex:bindLogic`、`ex:bindAction`（对象到逻辑/行动）。如 `ex:customerbehavior ex:bindLogic ex:calculate_customer_satisfaction`、`ex:workorder ex:bindAction ex:create_work_order`。

#### 行动（Actions）
`ex:assign_order_to_employee`、`ex:create_work_order` 等。

#### 逻辑函数（Logics）
`ex:calculate_customer_satisfaction`、`ex:generate_remediation_strategy`、`ex:get_network_logs`、`ex:is_low_satisfaction` 等。

---

## 对象属性（Object Properties）

以下列出主要对象属性，含域（Domain）、值域（Range）与说明。多数对象属性为 `ex:custom_relation` 的子属性，用于表达领域关系；部分关系使用 `ex:hasMiddleObject` 指明多对多桥接对象；`ex:domainAttribute`/`ex:rangeAttribute`用于声明以何数据属性建立两端的关联键。

- `ex:bindAction`（Domain: `ex:Object`，Range: `ex:Action`）— 对象绑定可执行行动。
- `ex:bindLogic`（Domain: `ex:Object`，Range: `ex:Logic`）— 对象绑定可调用逻辑。
- `ex:hasParameter`（Domain: `ex:Logic`/`ex:Action`，Range: `ex:Parameter`）— 函数拥有的参数。
- `ex:custom_relation` — 自定义对象间关系的上位属性。

#### 绑定属性：`bindAction`/`bindLogic`/`hasParameter`
对象到行动/逻辑的绑定与参数关联。

关系示例（均为 `ex:custom_relation` 子属性）：
- 关联/被关联：`ex:linkedWith`（客户→工单）、`ex:is_linked_to`（工单→客户）；`ex:linkedWith`（事件→工单）、`ex:is_linked_to`（工单→事件）。
- 订购/被订购：`ex:order`（客户→套餐/增值产品）/`ex:be_ordered`（产品→客户），含中间对象 `ex:customer_packageproduct_Ar` 或 `ex:customer_valueaddedproduct_RC`。
- 依赖/支持：`ex:depends_on`（产品→网络）/`ex:support`（网络→产品），中间对象如 `ex:valueaddedproduct_broadbandnetwork_Qx`、`ex:valueaddedproduct_wirelessnetwork_ND`、`ex:packageproduct_wirelessnetwork_xJ`、`ex:packageproduct_broadbandnetwork_OO`。
- 使用/被使用：`ex:use`（终端→网络）/`ex:used`（网络→终端），桥接 `ex:terminal_wirelessnetwork_9A`；另有宽带网络与终端间的 `ex:broadbandnetwork_terminal_Ee`。
- 指派/被指派：`ex:assign`（工单→员工）/`ex:be_assigned`（员工→工单），桥接 `ex:workorder_employee_C9`。
- 发起/被创建：`ex:initiate_`（客户→事件）/`ex:be_created`（事件→客户），桥接 `ex:customer_event_yf`。
- 引用/被引用：`ex:References`（工单→修复策略）/`ex:isReferencedBy`（修复策略→工单）。
- 拥有/属于：`ex:has`（客户→终端）/`ex:isPartOf`（终端→客户）。

#### 关系分组：订购/依赖/使用/指派/发起/引用/关联/拥有
上列分组便于检索具体子属性与桥接对象。

### 详细对象属性表

下表按单条关系列出域/值域、逆属性、桥接对象与键注解，便于对照 ODLM 的细粒度枚举。

| 属性 | 标签 | Domain | Range | 逆属性 | 子属性于 | 桥接对象 `ex:hasMiddleObject` | 键注解（Domain/Range） | 说明 |
|---|---|---|---|---|---|---|---|---|
| `ex:bindAction` | 绑定行动 | `ex:Object` | `ex:Action` | - | - | - | - | 对象可执行的行动绑定 |
| `ex:bindLogic` | 绑定逻辑 | `ex:Object` | `ex:Logic` | - | - | - | - | 对象可调用的逻辑函数绑定 |
| `ex:hasParameter` | 拥有参数 | `ex:Action`/`ex:Logic` | `ex:Parameter` | - | - | - | - | 行动/逻辑的形参声明 |
| `ex:order` | 订购 | `ex:customer` | `ex:packageproduct`/`ex:valueaddedproduct` | `ex:be_ordered` | `ex:custom_relation` | 例：`ex:customer_packageproduct_Ar`、`ex:customer_valueaddedproduct_RC` | `ex:domainAttribute`=`ex:客户ID`；`ex:rangeAttribute`=`ex:产品ID` | 客户与产品的订购关系，多对多用桥接对象 |
| `ex:be_ordered` | 被订购 | `ex:packageproduct`/`ex:valueaddedproduct` | `ex:customer` | `ex:order` | `ex:custom_relation` | 同上 | 同上 | 订购关系的逆 |
| `ex:depends_on` | 依赖 | `ex:packageproduct`/`ex:valueaddedproduct` | `ex:broadbandnetwork`/`ex:wirelessnetwork` | `ex:support` | `ex:custom_relation` | 例：`ex:valueaddedproduct_wirelessnetwork_ND`、`ex:packageproduct_broadbandnetwork_OO` | `ex:rangeAttribute`=`ex:network_id` | 产品对网络的依赖 |
| `ex:support` | 支持 | `ex:broadbandnetwork`/`ex:wirelessnetwork` | `ex:packageproduct`/`ex:valueaddedproduct` | `ex:depends_on` | `ex:custom_relation` | 同上 | `ex:domainAttribute`=`ex:network_id` | 网络对产品的支撑 |
| `ex:use` | 使用 | `ex:terminal` | `ex:wirelessnetwork`/`ex:broadbandnetwork` | `ex:used` | `ex:custom_relation` | 例：`ex:terminal_wirelessnetwork_9A`、`ex:broadbandnetwork_terminal_Ee` | 终端/网络的标识属性 | 终端与网络的使用关联 |
| `ex:used` | 被使用 | `ex:wirelessnetwork`/`ex:broadbandnetwork` | `ex:terminal` | `ex:use` | `ex:custom_relation` | 同上 | 同上 | 使用关系的逆 |
| `ex:assign` | 指派 | `ex:workorder` | `ex:employee` | `ex:be_assigned` | `ex:custom_relation` | `ex:workorder_employee_C9` | `ex:domainAttribute`=`ex:工单ID`；`ex:rangeAttribute`=`ex:员工ID` | 工单到员工的指派 |
| `ex:be_assigned` | 被指派 | `ex:employee` | `ex:workorder` | `ex:assign` | `ex:custom_relation` | 同上 | 同上 | 指派关系的逆 |
| `ex:initiate_` | 发起 | `ex:customer` | `ex:event` | `ex:be_created` | `ex:custom_relation` | `ex:customer_event_yf` | `ex:domainAttribute`=`ex:客户ID`；`ex:rangeAttribute`=`ex:事件ID` | 客户发起事件 |
| `ex:be_created` | 被创建 | `ex:event` | `ex:customer` | `ex:initiate_` | `ex:custom_relation` | 同上 | 同上 | 发起关系的逆 |
| `ex:References` | 引用 | `ex:workorder` | `ex:remediationstrategy` | `ex:isReferencedBy` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:工单ID` | 工单引用修复策略 |
| `ex:isReferencedBy` | 被引用 | `ex:remediationstrategy` | `ex:workorder` | `ex:References` | `ex:custom_relation` | - | `ex:rangeAttribute`=`ex:工单ID` | 修复策略被工单引用 |
| `ex:linkedWith` | 关联 | `ex:customer`/`ex:event` | `ex:workorder` | `ex:is_linked_to` | `ex:custom_relation` | - | 以业务ID关联 | 客户或事件与工单的业务关联 |
| `ex:is_linked_to` | 被关联 | `ex:workorder` | `ex:customer`/`ex:event` | `ex:linkedWith` | `ex:custom_relation` | - | 以业务ID关联 | 关联关系的逆 |
| `ex:has` | 拥有 | `ex:customer` | `ex:terminal` | `ex:isPartOf` | `ex:custom_relation` | - | `ex:domainAttribute`=`ex:客户ID`；`ex:rangeAttribute`=`ex:终端ID` | 客户拥有终端 |
| `ex:isPartOf` | 属于 | `ex:terminal` | `ex:customer` | `ex:has` | `ex:custom_relation` | - | 同上 | 终端属于客户 |

---

## 数据属性（Datatype Properties）

- 键注解：`ex:hasPrimaryKey`（类级主键数据属性）、`ex:hasTitle`（类级标题数据属性）。
- 键关联注解：`ex:domainAttribute`、`ex:rangeAttribute`（用于关系两端通过哪一数据属性进行键匹配）。

典型标识类属性：
- 客户相关：`ex:客户ID`、`ex:姓名`、`ex:年龄`、`ex:教育水平`、`ex:收入水平`、`ex:地域分布`、`ex:偏好套餐类型`。
- 员工相关：`ex:员工ID`、`ex:姓名`、`ex:职位`、`ex:所属部门`、`ex:负责服务类型`。
- 网络相关：`ex:网络ID`、`ex:基站类型`、`ex:工作频段`、`ex:运行状态`、`ex:光纤长度单位为公里`。
- 事件与工单：`ex:事件ID`、`ex:事件类型`（投诉/咨询/故障）、`ex:事件状态`、`ex:发生时间`；`ex:工单ID`、`ex:工单类型`（网优/装维/万号）、`ex:工单状态`、`ex:工单优先级`、`ex:工单内容`、`ex:联系方式`、`ex:创建时间`、`ex:关闭时间`、`ex:感知维度ID`、`ex:建议方案`。
- 产品与终端：`ex:产品ID`、`ex:产品名称`、`ex:产品描述`、`ex:价格`、`ex:套餐产品名称`、`ex:套餐内容`、`ex:计费周期`；`ex:终端ID`、`ex:终端号`、`ex:终端类型`、`ex:终端价格`。
- 感知与评估：`ex:感知ID`、`ex:感知时间`、`ex:感知分析算法`、`ex:感知分析算法原理描述`、`ex:感知维度`；`ex:感知评估ID`、`ex:评估描述`、`ex:评估得分`。

客户行为度量（部分示例，实际属性集更丰富）：

#### 标识与元数据
客户/员工/网络/事件/工单/产品/终端等的主键与基本元数据。

#### 账单与费用
- 账单/费用类：`ex:月均账单金额`、`ex:本月出账收入`、`ex:本月缴费总次数`、`ex:总欠费金额`、`ex:当月流量溢出费用`、`ex:当月语音溢出费用`、`ex:流量包费用`、`ex:月最低消费金额`、`ex:税前套餐费用`、`ex:实收套餐费用`。

#### 使用与饱和度
- 使用/饱和度类：`ex:月均流量使用`、`ex:本月使用流量`、`ex:流量饱和度`、`ex:语音时长`、`ex:语音饱和度`、`ex:手机上网时长`、`ex:套内包含通用流量`、`ex:套内包含定向流量`、`ex:套内国内语音`。

#### 语音与通话
- 语音/通话类：`ex:主叫次数`、`ex:被叫次数`、`ex:被叫时长`、`ex:近3个月均主叫通话时长`、`ex:本月通话总时长`、`ex:本月主叫通话总时长`、`ex:卡类型`、`ex:是否超长通话用户`。

#### 消息/视频/网页体验
- 消息/视频/网页体验类：`ex:短信条数`、`ex:翼留言数`、`ex:本月消息接收/发送成功率`、`ex:本月消息异常话单总次数`、`ex:视频彩铃数`、`ex:本月视频播放成功率`、`ex:本月视频异常话单总次数`、`ex:本月视频播放卡顿总次数`、`ex:本月视频播放等待总时长`、`ex:本月视频下载优良率`、`ex:本月最大视频播放卡顿频次`、`ex:本月最大视频卡顿时长占比`、`ex:本月每兆流量视频播放卡顿次数超过门限次数`、`ex:本月网页显示/响应成功率`、`ex:本月访问主流网站的网页显示/响应成功率`、`ex:本月网页异常话单总次数`。

#### 网络质量与RSRP
- 网络质量/RSRP类：`ex:本月RSRP优良率`、`ex:本月RSRP优良率负115`、`ex:本月最小RSRP优良率`、`ex:本月最小RSRP优良率负115`、RSRP相关MR计数（≥-105/≥-115/<-105/<-115），以及“低于80%天数”统计属性。

#### 投诉/咨询/申告
- 投诉/咨询/申告类：`ex:本月投诉次数`、`ex:本月在途投诉次数`、`ex:本月在途超时投诉次数`、`ex:近3个月投诉次数`、`ex:6个月内投诉不满意次数`、`ex:近1-6个月申告次数`、`ex:本月客户申告次数`、`ex:咨询次数`、`ex:本月咨询次数`、`ex:本月咨询不满意次数`、`ex:投诉期间来电次数`、`ex:超时投诉期间来电次数`、`ex:本月不满意来话次数`、各类重复来电/投诉/报障次数。

#### 宽带/ITV/天翼/权益
- 宽带/天翼/ITV等资源类：`ex:宽带数`、`ex:新装宽带数`、`ex:固话数`、`ex:新装固话数`、`ex:ITV数`、`ex:新装ITV数`、`ex:天翼卡数`、`ex:新装天翼卡数`、`ex:终端类智家数`、`ex:活跃宽带数`、`ex:活跃ITV数`、`ex:活跃天翼数`、`ex:活跃云产品数`、`ex:云产品数`、`ex:优品包数`、`ex:权益产品数`、`ex:其他权益数`。

#### 画像/地域/栅格
- 画像/分群/地域类：`ex:客户星级`、`ex:客户战略分群`、`ex:本地网标识`、`ex:省份标识`、`ex:网格支局编码/名称`、居住地/工作地TOP驻留小区。

#### 时间与系统标识
- 时间/标识类：`ex:统计月份`、`ex:套餐到期时间`、`ex:开通日期`、`ex:系统处理时间`、`ex:客户标识`、`ex:产品实例标识`、`ex:手机号`、`ex:network_id`、`ex:customer_id`、`ex:work_order_id`、`ex:event_id`、`ex:terminal_id`。

### 按类拆分（Domain→Properties）

为提升与 ODLM 的一致性，以下按 Domain 类逐条枚举常见数据属性，并标注值域类型（示例以 `xsd` 类型表示；若 CEM.owl 中未给出，以下为可推断的常用类型）。

#### `ex:customer`
- 主键：`ex:客户ID`（`xsd:string`）；标题：`ex:姓名`（`xsd:string`）
- 画像与基础：`ex:年龄`（`xsd:int`）、`ex:教育水平`（`xsd:string`）、`ex:收入水平`（`xsd:string`）、`ex:地域分布`（`xsd:string`）、`ex:偏好套餐类型`（`xsd:string`）
- 分群与星级：`ex:客户星级`（`xsd:string`）、`ex:客户战略分群`（`xsd:string`）
- 联系信息：`ex:联系方式`（`xsd:string`）、`ex:手机号`（`xsd:string`）

#### `ex:customerbehavior`
- 使用与饱和度：`ex:月均流量使用`（`xsd:decimal`）、`ex:本月使用流量`（`xsd:decimal`）、`ex:流量饱和度`（`xsd:decimal`）、`ex:语音时长`（`xsd:int`）、`ex:语音饱和度`（`xsd:decimal`）、`ex:手机上网时长`（`xsd:int`）
- 通话计数：`ex:主叫次数`（`xsd:int`）、`ex:被叫次数`（`xsd:int`）、`ex:被叫时长`（`xsd:int`）、`ex:近3个月均主叫通话时长`（`xsd:int`）、`ex:本月通话总时长`（`xsd:int`）、`ex:本月主叫通话总时长`（`xsd:int`）
- 消息/视频/网页体验：`ex:短信条数`（`xsd:int`）、`ex:本月消息接收/发送成功率`（`xsd:decimal`）、`ex:本月视频播放成功率`（`xsd:decimal`）、`ex:本月视频异常话单总次数`（`xsd:int`）、`ex:本月视频播放卡顿总次数`（`xsd:int`）、`ex:本月网页显示/响应成功率`（`xsd:decimal`）
- RSRP与网络质量：`ex:本月RSRP优良率`（`xsd:decimal`）及相关 MR 计数属性（`xsd:int`）
- 投诉/咨询：`ex:本月投诉次数`（`xsd:int`）、`ex:近3个月投诉次数`（`xsd:int`）、`ex:本月咨询次数`（`xsd:int`）等
- 资源拥有：`ex:宽带数`（`xsd:int`）、`ex:ITV数`（`xsd:int`）、`ex:天翼卡数`（`xsd:int`）、`ex:权益产品数`（`xsd:int`）等
- 时间标识：`ex:统计月份`（`xsd:gYearMonth`）

#### `ex:broadbandnetwork` / `ex:wirelessnetwork`
- 主键：`ex:network_id`（`xsd:string`）；标题：`ex:运行状态`（`xsd:string`）
- 技术参数：`ex:基站类型`（`xsd:string`）、`ex:工作频段`（`xsd:string`）、`ex:光纤长度单位为公里`（`xsd:decimal`）
- 质量指标：网络质量相关统计（如优良率，`xsd:decimal`）

#### `ex:event`
- 主键：`ex:event_id`（`xsd:string`）；类型：`ex:事件类型`（`xsd:string`，允许值：投诉/咨询/故障）
- 状态与时间：`ex:事件状态`（`xsd:string`）、`ex:发生时间`（`xsd:dateTime`）
- 关联键：`ex:客户ID`（`xsd:string`，用于与客户发起关系）

#### `ex:workorder`
- 主键：`ex:work_order_id`（`xsd:string`）；类型：`ex:工单类型`（`xsd:string`，允许值：网优/装维/万号）
- 状态与优先级：`ex:工单状态`（`xsd:string`）、`ex:工单优先级`（`xsd:string`）
- 内容与时间：`ex:工单内容`（`xsd:string`）、`ex:创建时间`（`xsd:dateTime`）、`ex:关闭时间`（`xsd:dateTime`）
- 关联键：`ex:员工ID`（`xsd:string`，指派关系）、`ex:感知维度ID`（`xsd:string`）

#### `ex:packageproduct` / `ex:valueaddedproduct`
- 主键：`ex:产品ID`（`xsd:string`）；标题：`ex:产品名称`（`xsd:string`）
- 计费信息：`ex:价格`（`xsd:decimal`）、`ex:计费周期`（`xsd:string`）
- 套餐细节：`ex:套餐产品名称`（`xsd:string`）、`ex:套餐内容`（`xsd:string`）

#### `ex:terminal`
- 主键：`ex:terminal_id`（`xsd:string`）；标题：`ex:终端号`（`xsd:string`）
- 规格与价格：`ex:终端类型`（`xsd:string`）、`ex:终端价格`（`xsd:decimal`）

#### `ex:perception`
- 主键：`ex:感知ID`（`xsd:string`）
- 算法信息：`ex:感知分析算法`（`xsd:string`）、`ex:感知分析算法原理描述`（`xsd:string`）
- 时间与维度：`ex:感知时间`（`xsd:dateTime`）、`ex:感知维度`（`xsd:string`）

#### `ex:perceptionevaluation`
- 主键：`ex:感知评估ID`（`xsd:string`）
- 结果：`ex:评估描述`（`xsd:string`）、`ex:评估得分`（`xsd:decimal`）

#### `ex:remediationstrategy`
- 主键：`ex:建议方案`（`xsd:string`）
- 关联：可与 `ex:workorder` 通过 `ex:References` 关联（工单键：`ex:工单ID`）

---

## 命名个体与枚举（Named Individuals & Enums）
- 事件类型（数据属性约束描述中给出允许值）：“投诉”、“咨询”、“故障”。
- 工单类型（数据属性约束描述中给出允许值）：“网优”、“装维”、“万号”。

（CEM.owl 未显式定义枚举个体为命名个体，多数以数据属性的允许值说明给出）

---

## 建模约束与规则（Axioms）
- 继承与对齐：`ex:Entity ⊑ prov:Entity`，`ex:Action`/`ex:Logic ⊑ prov:Activity`；所有领域对象均继承 `ex:Object`。
- 键注解：对象类通过 `ex:hasPrimaryKey` 指定其主键数据属性，通过 `ex:hasTitle` 指定显示标题数据属性。
- 关系键匹配：对象关系子属性通过 `ex:domainAttribute` 与 `ex:rangeAttribute` 指示以何数据属性进行两端键关联；多对多场景通过 `ex:hasMiddleObject` 指明桥接对象。
- 逻辑/行动参数：通过 `ex:hasParameter` 声明，参数具名、类型、是否可选；复杂类型可通过 `ex:paramTypeNode` 指向 `ex:ListType`/`ex:DictType`。

---

## 示例绑定（Examples）
- 对象绑定逻辑：`ex:customerbehavior ex:bindLogic ex:calculate_customer_satisfaction`；`ex:remediationstrategy ex:bindLogic ex:generate_remediation_strategy`；`ex:wirelessnetwork` 相关日志查询：`ex:get_network_logs`。
- 对象绑定行动：`ex:workorder ex:bindAction ex:assign_order_to_employee`、`ex:workorder ex:bindAction ex:create_work_order`。

---

## 修订记录
- 1.0（2025-11-27）: 初始版本发布（依据 `CEM.owl` 结构整理）。
