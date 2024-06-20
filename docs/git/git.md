

## Git 基础用法

```bash
git init #创建新的仓库
git remote origin add https://XXXXX.github.io
或者
git clone https://XXXXX.github.io # 相当于上面两步

## 第一次修改文件后
git add .
git commit -m "备注"
git push origin main

## 之后每次修改文件后
git pull ## 多的这一步防止代码冲突。多人协作使用git fetch & git merge, 先不用在意
git add .
git commit -m "备注"
git push origin main
```

## Git回滚

### 1. 使用 `git reset`

你可以使用 `git reset` 命令来将 HEAD 指针移动到之前的提交，从而撤销之后的提交。在使用 `git reset` 时，有三种模式可以选择：

- `--soft`：仅移动 HEAD 指针，保留更改在暂存区中。
- `--mixed`：移动 HEAD 指针，并重置暂存区，但保留更改在工作区中。
- `--hard`：移动 HEAD 指针，并重置暂存区和工作区，丢弃所有未提交的更改。

```bash
git log  # 查看提交历史，找到你想要回滚到的提交的哈希值
git reset --hard <commit-hash>  # 使用 --hard 模式回滚
```

### 2. 使用 `git revert`

另一种方法是使用 `git revert` 命令来创建一个新的提交，撤销之前的提交的更改。这种方法会保留提交历史。

```bash
git log  # 查看提交历史，找到你想要撤销的提交的哈希值
git revert <commit-hash>  # 创建一个新的提交来撤销之前的提交的更改
```

### 3. 使用 `git checkout`

如果你只是想要撤销工作区的更改，可以使用 `git checkout` 命令。

```bash
git checkout -- <file>  # 撤销指定文件的更改
```

或者，如果你想要撤销所有更改，可以使用：

```bash
git checkout .
```

这会撤销所有未暂存的更改，但不会影响已经暂存的更改或提交。

无论你选择哪种方法，都要记得在进行任何回滚操作之前先进行备份或者确认，以避免意外丢失重要更改。