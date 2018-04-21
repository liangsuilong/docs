---
create_date: "2018-04-20 15:59:45"
update_date: "2018-04-21 18:25:53"
title: "Project Development (Draft)"
type: "guide"
---

### 「能源动词」说明

文档中包含一些「能源动词」，对应解释如下：

  - `必须(MUST)`：绝对，严格遵循
  - `一定不可以(MUST NOT)`：禁令，严令禁止
  - `应该(SHOULD)`：强烈建议这样做，但不强求
  - `不该(SHOULD NOT)`：强烈建议不这样做，但不强求
  - `可以(MAY)`：可选

## 项目开发（开发部门篇）

1. 其他部门需要开发部门协助*（系统开发、系统搭建、服务器相关）*，都**必须**提前通知开发主管

    - 没有提前通知，开发部门可以不提供及时的协助，根据工作排序
    - 需求方**一定不可以**直接对接开发部门，传达的信息视为无效

2. 开发部门根据需求和初步收集资料，给出开发*（时间和人力）*成本后**应该**得出该需求的结果*（立项、延后或者放弃）*。延后或放弃则将资料整理存档，立项则进入正常开发流程
3. 产品经理除了需要跟需求方交流确定业务流程和功能，**必须**确定版本功能和上线时间并出文档，开发和交付都**必须**依据文档
4. 开发部门**必须**在有产品文档的情况下，才能进行开发，产品经理**必须**在当前版本开发结束前确定下版本功能和时间并出文档
5. 产品文档**必须**保证唯一性，**一定不可以**以聊天软件发送的为准，所以项目的资源都**必须**在Google Drive项目文件夹下统一管理
6. 项目进行开发步骤（编码-测试-部署-交付）期间：

    - 功能如果需要调整只能做减法，不做加法，确保版本按时或提前上线
    - 根据版本*（主版本号，次版本号）*交付时间，**必须**提前2天到一周时间*（甚至更长）*进行系统流程穿透测试
    - **一定不可以**上线当前版本文档外的新功能，开发部门**必须**拒绝这个要求

7. 系统发现的bug，**应该**及时修复，直接影响运营的**必须**马上进行修复

    - 开发部门有责任保证系统正常运行
    - 修复bug的时间不算在版本开发时间中
    - 提交bug信息**必须**尽可能提供信息，无法定位的信息开发部门可以拒绝接受，可以看[如何提交Issue](/guide#submit)

8. 开发部门**必须**遵守[开发约定规则](/guide)