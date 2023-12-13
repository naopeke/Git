# Git/GitHub Commands

**Configuración de GIT**
```
git config --global user.name "John Doe"
```
```
git config --global user.email johndoe@example.com
```

**Configución de GIT**
```
git config --list<br>user.name=Scott Chacon useremail=schacon@gmail.com
```
```
git help config
```

**GIT INIT**
```
git init
```
```
git clone https://github.com/username/repository_name.git
```

**COMMANDS**
```
git add .
```
```
git commit -m "write your comment here"
```
```
git push
```
```
git pull https://github.com/username/repository_name.git
```

**RESET**
```
git reset --soft HEAD~
```
```
git reset --mixed HEAD~
```
```
git reset --hard HEAD~
```

**GIT BRANCH**
```
git branch new_branch_name
```
```
git branch
```
```
git checkout branch_name
```

**GIT MERGE**
```
git checkout main
```
```
git merge new_branch_name
```

**GIT IGNORE**
```
touch .git ignore
```
```
git status
```
```
vi .gitignore
```
shift:wq (write & quit)


# This branch is X commits behind main
dia1 ブランチが main ブランチに比べてXつのコミットで遅れているという意味です。  
1. ローカルリポジトリを最新の状態に更新
```
git checkout main
```
```
git pull origin main
```
2. dia1 ブランチに切り替えて main ブランチの変更を取り込む
```
git checkout dia1
```
```
git merge main
```
リベースを使用する場合
```
git checkout dia1
```
```
git rebase main
```
3. 変更をプッシュ
```
git push origin dia1
```
リベースを行った場合は、リモートブランチに強制的にプッシュする必要があります。
```
git push origin dia1 --force
```
# This branch is X commits ahead of main
現在のブランチ（例えば dia1）が main ブランチよりも前に進んでいることを示しています。  
**Margeを使う**  
1.main ブランチに切り替える:
```
git checkout main
```
2.リモートリポジトリから最新の変更を取得
```
git pull origin main
```
3.dia1 ブランチの変更を main にマージ
```
git merge dia1
```
4.変更をリモートの main ブランチにプッシュ
```
git push origin main
```
**Rebaseを使う**
1.dia1 ブランチに切り替える
```
git checkout dia1
```
2.main ブランチからの変更をリベース
```
git rebase main
```
3.リベース後、dia1 ブランチを main にマージ
```
git checkout main
```
```
git merge dia1
```
4.変更をリモートにプッシュ
```
git push origin main
```
