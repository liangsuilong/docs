---
create_date: "2018-02-25 14:23:29"
update_date: "2018-04-21 18:25:34"
title: "开发约定规则"
type: "guide"
---

## 目录
-----

* [说明](#coc)
* [提交指南](#submit)
* [代码风格](#rules)
* [Commit信息指南](#commit)
* [语义化版本](#version)
* [协作](#work-together)

## <a name="coc"></a> 说明
-----

所有参与开发的人员都 **必须** 遵循统一的约定规则

开发人员需要熟悉git的使用，如果命令行不熟，可以使用一些工具来操作。([gitkraken](https://www.gitkraken.com/), [tower](https://www.git-tower.com/), [sourcetree](https://www.sourcetreeapp.com/))

  - [git-tips](https://github.com/git-tips/tips)
  - [git-scm](https://git-scm.com/book/zh/v2)
  - [猴子都能懂的git教程](http://backlogtool.com/git-guide/cn/)
  - [git-flow](https://github.com/nvie/gitflow)
  - [git-flow-cheatsheet](https://danielkummer.github.io/git-flow-cheatsheet/index.zh_CN.html)

### 「能源动词」说明

文档中包含一些「能源动词」，对应解释如下：

  - `必须(MUST)`：绝对，严格遵循
  - `一定不可以(MUST NOT)`：禁令，严令禁止
  - `应该(SHOULD)`：强烈建议这样做，但不强求
  - `不该(SHOULD NOT)`：强烈建议不这样做，但不强求
  - `可以(MAY)`：可选

> 详细可以看 [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt)

## <a name="submit"></a> 提交指南
-----
### <a name="submit-issue"></a> 如何提交Issue

在你提交一个issue之前，先看issues列表中有没有存在相同的issue，有的话直接在上面留言。<br>
提交的问题确认后会根据紧急程度标记版本里程碑，并会尽快的修复。<br>

提交问题的人麻烦提交尽量详细的信息：

  - 比如系统或浏览器信息，什么系统类型android还是iOS
  - 想要进行的操作
  - 本来应该的结果是怎样
  - 实际的结果是怎样
  - 有截图那就最好
  - **可以**使用gitlab的标签标注 [详细看这](#work-together)

**一句话的问题会被无视。**

```
啊，不能登录了。。。
```

### <a name="submit-pr"></a> 提交Pull Request (PR)

在gitlab上发起PR后都 **不该** 自行关闭，需要更新也在当前的PR中更新。<br>
在你提交一个PR之前，请遵循下列步骤：

1. 在对应的issue中回复说明你正在处理这个issue
2. 使用最新的develop分支创建新的分支，如果是预发布的情况会有个`release-*`分支
3. 遵循下面的[编程规则](#rules)
4. 完成后推送到gitlab上
5. 在gitlab上发起合并请求到对应的分支，feature -> (develop/release-\*)，hotfix -> master

提交后如果需要修改：

  - 按需求更新代码
  - 确保更新代码后，需要提交的功能没有错误
  - rebase你的分支和强推到gitlab，PR会自动更新

    ```
    git rebase develop -i
    git push -f
    ```

提交的PR合并后，删除分支别留在gitlab上，同时记得更新本地的项目

## <a name="rules"></a> 编程规则
-----
- 所有开发类文档都 **应该** 使用 `Markdown` 文件格式
- **必须** 安装`editorconfig`插件使用统一的编辑器配置 [Link](http://editorconfig.org/)
- **必须** 遵循统一的代码风格：

  - PHP使用`PSR2`或者`Symfony` [Link](https://www.php-fig.org/psr/psr-2/)
  - Javascript使用`standard` [Link](https://standardjs.com/)

- 代码中 **可以** 使用一些关键字 `TODO` `FIXME` `NOTE` 等等
- 项目代码 **必须** 存放在`gitlab`，项目命名除了专有名字，其他全使用小写，单词使用`-`符号间隔。比如：`dcshop-server` `dcshop-iOS`
- 使用自定义的`git-flow`工作流迭代项目，会同时维护两个长分支`master`和`develop`

  - `hotfix-` 补丁分支基于`master`分支建立，需要修复生产环境`master`出现的问题的情况下建立
  - `release-` 预发布版本分支基于`master`分支建立，建立预发布版本后，属于这个版本的issues的PR都已这个分支为目标分支
  - 其它分支、功能开发或者bug修复，都已该分支实际的作用命名。比如：`fix-array-parse-error` `add-some-feature`

- 使用`standard-version`生成版本日志，并遵循语义化版本递增规则
- **项目的迭代围绕下个发布版本优先处理任务，会用gitlab的milestone标记在需要版本内处理的issue**
- 开发人员能动手的功能和bug都必须在issues上有记录，一般通过`help wanted`标签领取

## <a name="commit"></a> Commit信息指南
-----
`commit`提交信息 **必须** 遵守格式规范，每个`commit`都只处理单纯的一个问题

### Commit信息格式

名词说明：

- 页头：`type(scope?): subject`
- 类型：`type`
- 作用域: `scope`
- 主题: `subject`
- 内容: `body`
- 页脚：`footer`

每个commit信息包含一个 **页头**，一个 **内容** 和一个 **页脚**。**页头** 有一个特定的格式包含一个 **类型**，一个 **作用域** 和一个 **主题**:

```
type(scope?): subject
空行
body?
空行
footer?
```

页头必填，除了 **作用域** 选填

如果有需要[关闭某个issues](https://help.github.com/articles/closing-issues-using-keywords/)，在页脚 **footer** 中填写

例子：

```
feat: 添加google登录功能
```

或者：

```
fix(login): 修复cookies引起用户不能登录

巴拉巴拉，快速登录时cookies会导致用户无法登录。。。
```

### Revert回退

如果需要回退之前的commit，页头 **应该** 已`revert:`开头，后面跟已经回退的那个commit的页头信息，在内容中带上回退的commit的hash值。
*gitkraken的revert功能会自动commit，没有revert开头，带有hash值*

### Type类型

页头中的类型 **必须** 是下列其中一个：

  - chore: 杂事，不会显示到log
  - fix: 修复bug
  - feat: 新的功能
  - docs: 文档更新
  - ci: 更新CI配置和脚本的时候
  - perf: 更新代码提高性能
  - refactor: 重构，更新代码既不是修复bug也不是添加新功能
  - test: 添加新的测试或更新现有的
  - style: 更新风格而且不影响代码功能（空格，格式，引号等）
  - build: 更新构建系统或其它依赖库（gulp, composer, npm等）

### Scope作用域

作用域应该是一些库和模块定义的名词

  - 模块名称，使用项目中模块文件夹或类的名称
  - 第三方库的名词，使用包管理工具上的名词，怎么安装的用怎么名字
  - 一些类型可以留空，比如`style`,`test`和`refactor`的更新可能涉及到所有的模块

### Subject主题

主题尽量简短的描述清楚提交的内容，不要使用标点符号，可以使用 `\`` 符号

### Body内容

如需要提交内容信息，内容中需要描述清楚和更改之前有什么更新。

如果这个提交改了很多东西，比如改了接口会直接让其他模块或用户无法使用。需要在内容开始加`BREAKING CHANGE:`，字母全大写。

### Footer页脚

页脚的带一些需要关联的gitlab任务，或者需要关闭的任务。（比如：close, fix, fixes, resolve...)

详情可以看关闭任务的关键字 [closing-issues-using-keywords](https://help.github.com/articles/closing-issues-using-keywords/)

### 为什么要规范提交

- 自动生成日志
- 自动遵守语义化版本规范
- 传达准确的信息给其他开发人员
- 掌握开发和发布的过程
- 通过浏览提交的历史信息结构，让其他人更容易加入到项目

## <a name="version"></a> 语义化版本
-----
[语义化版本 SemVer](https://semver.org/lang/zh-CN/)

## <a name="work-together"></a> 协作
-----

### Gitlab

咱们有自建的gitlab服务，开发人员的帐号在入职后由主管创建 <br>
目前项目的开发任务都在gitlab中跟踪，以后会根据情况迁移到redmine统一处理

- `help wanted` 在版本内有这个label的优先处理，如果准备处理就去掉`help wanted`然后 **留言**
- `enhancement` 一些增强功能，属于`feat`或者`perf`类型
- `bug` 出现的错误，属于`fix`类型
- `documentation` 文档，属于`docs`类型
- `suggestion` 意见或建议
- `discussion` 待定

### Telegram

开发部门使用telegram沟通，git的更新会通过bot通知到群组，工作时间的交流也在群中