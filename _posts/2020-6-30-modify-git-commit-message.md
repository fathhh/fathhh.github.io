---
title: 修改提交记录的信息
layout: post
tags:
  - git

---



> 刚才打开github，发现新版的contributors多了两个人，于是查看了一下提交历史，多出的两项应该是我的另外两台电脑配置错误。于是查找修改commit的办法

常用的修改最近一次的 commit

```bash
git commit --amend --author="fat <fat@gmail.com>"
```

对于提交历史中的办法，我找到了rebase

rebase有个参数i，r:reword,可以修改commit message。然后还不止reword，p/r/e/s/f/x/d，这里需要用到e:edit.

找到要修改的commit开始的位置5f653f9，使用 rebase 的交互模式

```bash
git rebase -i -p 5f653f9
```

在打开的 git-rebase-todo 文件中，将 pick 都修改成 edit 关键词 ：wq 保存退出

rebase 开始进行 commit 依次信息确认

```bash
Stopped at 5f653f9... Add images to about page
You can amend the commit now, with 
    git commit --amend 
Once you are satisfied with your changes, run 
    git rebase --continue
```

现在我们只需要在每个信息确认时，对用户名和邮箱进行修改

```bash
$ git commit --amend --author="fat <fat@gmail.com>"
$ git rebase --continue
```

[Reference]: https://www.jianshu.com/p/72717f1a1e90



