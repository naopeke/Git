# Git/GitHub Commands
[Configuration](#configuration) | [Init](#init) | [Commands](#commands) | [Reset](#reset) | [Branch](#branch) | [Merge](#merge) | [Ignore](#ignore)  
[This branch is X commits behind main](#this-branch-is-x-commits-behind-main)
 | [This branch is Y commits ahead of main](#this-branch-is-y-commits-ahead-of-main) | [Revert](#revert) | [upstream](#upstream) | [Clone Branch](#clone-branch)

## Configuration
```
git config --global user.name "John Doe"
```
```
git config --global user.email johndoe@example.com
```
```
git config --list<br>user.name=Scott Chacon useremail=schacon@gmail.com
```
```
git help config
```

## Init
```
git init
```
```
git clone https://github.com/username/repository_name.git
```

## Commands
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

## Reset
```
git reset --soft HEAD~
```
```
git reset --mixed HEAD~
```
```
git reset --hard HEAD~
```

## Branch
```
git branch new_branch_name
```
```
git branch
```
```
git checkout branch_name
```

## Merge
```
git checkout main
```
```
git merge new_branch_name
```

## Ignore
```
touch .gitignore
```
```
git status
```
```
vi .gitignore
```
shift:wq (write & quit)
```
# Node.js
node_modules/

# Logs
logs
*.log

# Dependency directories
pids
*.pid
*.seed
*.pid.lock

# Optional npm cache directory
.npm

# Optional eslint cache
.eslintcache

# Output of 'npm pack'
*.tgz

# Yarn
yarn-error.log
yarn-debug.log
yarn.lock
!yarn.lock.example

# dotenv environment variables file
.env

# OS generated files
.DS_Store
Thumbs.db

```


## This branch is X commits behind main
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
## This branch is Y commits ahead of main
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

## Revert
Main, dia1, dia2, dia3, dia4, dia5のブランチがあり、dia4をmainにマージしたい場合  
```
commit a7ff81dcbfa11312ac73abbfad6ea7ef5c92d14a (HEAD -> main, origin/main, origin/dia5, dia6, dia5)
Author: naopeke
Date:   Wed Dec 27 15:58:01 2023 +0100

    first commit

commit 365f962c4d96647c26be4b0aeba640fc01a498d0 (origin/dia4, dia4-2, dia4)
Author: naopeke
Date:   Thu Dec 21 11:55:54 2023 +0100

    Reto1,2 done
```
```
git checkout main
```
```
git revert -m 1 <commit-hash-of-dia5>
git revert -m 1 a7ff81dcbfa11312ac73abbfad6ea7ef5c92d14a
```
```
git merge dia4
```
```
git push origin main
```
エラー表示：git revert コマンドが実行しようとしている変更が、現在の作業ディレクトリに未コミットの変更があるために失敗  
```
User
╰─ git revert -m 1 a7ff81dcbfa11312ac73abbfad6ea7ef5c92d14a                  
error: Los cambios locales de los siguientes archivos serán sobrescritos al fusionar:
        src/app/app-routing.module.ts
        src/app/app.module.ts
        src/app/components/header/header.component.html
Por favor, confirma tus cambios o aguárdalos antes de fusionar.
Abortando
fatal: falló al revertir
```
これらの変更を先にコミットするか、一時的にセーブするかしてから、git revert を再度実行  
```
git stash save "Temporary changes"
```
```
git revert -m 1 a7ff81dcbfa11312ac73abbfad6ea7ef5c92d14a
```
```
git merge dia4
```
```
git push origin main
```
一時的にセーブした変更を戻す
```
git stash pop
```
## upstream
```
git push --set-upstream origin dia2
```

## Clone Branch
```
git clone -b Dia6 --single-branch <GitHubのリポジトリURL>
```
リモートリポジトリの確認（オプション）:  
もしリモートリポジトリの変更があるか確認する場合は、以下のコマンドを実行して、リモートリポジトリの情報を更新
```
git fetch origin
```
```
git checkout Dia6
```
```
git pull origin Dia6
```
  
## Change the repo to push
```
git remote set-url origin <新しいリモートのURL>
```
```
git remote set-url origin https://github.com/naopeke/NewRepository.git
```
