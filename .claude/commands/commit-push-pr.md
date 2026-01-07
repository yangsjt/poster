# /commit-push-pr
1. 执行 `git status` 和 `git diff` 分析所有未提交的更改。
2. 自动生成一段简洁、准确的 commit message。
3. 执行 `git add .` 和 `git commit -m "[message]"`。
4. 执行 `git push origin [current_branch]`。
5. 成功后，询问我是否需要执行 `gh pr create --fill` 创建 Pull Request。