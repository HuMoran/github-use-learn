# github-use-learn

### GitHub 使用规范
#### 分支管理规范：
- master分支:
  - master为主分支，存放测试通过，正式发布的release版本代码
  - master分支只能通过develop分支合并，不能直接提交代码
  - master分支上的BUG原则上通过发布下一个版本来修复，如果有需要紧急修复的BUG，可视情况通过发布热补丁或从master分支上checkout出一个hotfix分支修复，最后在合并到master和develop分支
 
- develop分支：
  - dev为开发分支，存放功能开发、自测完，待测试人员测试的最新代码
  - dev分支只能通过其他分支合并，不能直接提交代码
  - 测试分为三个阶段：Alpha（α）、Beta（β）、Release Candidate（RC），每个阶段可视情况发布一次或多次版本，直至测试通过
  - 测试流程：
    1. 研发发布版本
    2. 根据版本拉取代码构建
    3. 部署
    3. 测试
    4. 结果反馈
   - RC测试通过后，合并到master分支，并正式发布
 
- hotfix分支：
  - 修复BUG时临时checkout出来的分支，修复完成后，合并入主分，并删除此hotfix分支
- feature分支:
  - 当有新的feature需要开发时，从dev分支checkout出一个分支，分支名称使用feature命名，feature开发测试完成后，合并入develop分支，并删除feature分支
- 分支合并：
  - 如果代码需要合并到master或者develop分支，首先需要在github上面发起一个pull request请求，然后通知组内的另外成员，进行代码Review，Review通过后，由该成员完成合并请求
  - 合并时，请先使用`git rebase -i`合并develop或者master分支代码，在提交pull request请求
  - 如果发起pull request请求的分支commit信息过多，请先合并commit信息后，在发起pull request请求

参考文章：[实际项目中如何使用Git做分支管理 - ShuSheng007的专栏 - CSDN博客](https://blog.csdn.net/shusheng0007/article/details/80791849)
 
#### 版本命名规范：
- 主版本号：一般是软件出现大的功能或者架构调整，才会变动此版本号
- 子版本号：根据RoadMap升级版本号
- 阶段版本号：小功能或者BUG修复
- 测试阶段（可选）
- 阶段测试版本号（可选）
- **eg:**  0.9.1-alpha8、0.9.1-beta1、0.9.1-rc1、1.0.0

#### git add规范：
- 禁止使用`git add .`命令，只能单个依次添加自己修改的文件
- 推荐使用vsCode的Git功能，依次确认要添加的文件和修改的内容是否正确
- 所有修改的代码，必须通过代码静态检查后，才能提交（nodejs：eslint、c：linter）
- 提交的代码中，应取出多余的打印信息

#### git commit规范：
参考文章：[Commit message 和 Change log 编写指南 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)

#### Issues提交规范：
- 当有新的feature或者BUG时，可以直接在github上提交issue，issue标题请遵守以下格式：
    > feature: `[RFC]title`

    > BUG:`[BUG]title`

- 提交的issue由负责人确认，确认后打上对应标签，并指派对应的开发人员解决
- 开发人员提交代码时，指明对应的issue，issue自动关闭，issue提交人确认是否正确，如不正确，重开issue

