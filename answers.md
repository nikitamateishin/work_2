1. git commit - создаёт коммит, а git commit c флагом --amend заменяет текущий.
Может быть опасен когда мы изменили изменения с рабочим кодом на коммит с нерабочим.

2. -d - безопасное удаление. -D - удаление, не безопаасное, удаляет в любом случаи
в том числе и замёрдженные бранчи

3. git checkout <branch> - переключает на ветку, а git checkout <commit> - определённый
коммит.«detached HEAD» - указывает на текущее состояние коммита.

4. --soft - индекс не сбрасывается и все изменения остаются в индексе.
--mixed - индекс сбрасывается до состояния коммита. Изменения остаются в файлах
--hard - все изменения в файлах откатываются

5. git revert - создаёт новый коммит с откатыними изменениями.
git reset - откатывает коммит на выбраный и удаляет коммиты из истории

6.git merge --no-ff - Принудительно создает новый замёрдженный коммит,
даже если возможен fast-forward.
git merge --squash - Объединяет все изменения из feature-ветки в один новый
коммит на текущей ветке.

7. git rebase <base> - "перемещает" коммит до base и начинает последовательность после
него. git rebase --abort

8. git cherry-pick c1 c2 c3. 
Флаг -n Применяет изменения из коммита в рабочую директорию и индекс.
Флаг -x добовляет строку в сообщении коммита
-e редактирует сообщение коммита.

9. --abort
10.  10.одители merge-коммита это два коммита которыми этот коммит был замёрджен.
git revert -m нужен если мы хотим выбрать какой именно родитель будет создан.

ЧАСТЬ B:

git checkout -b feature/header git branch -m feature/header feat/header git branch -d feature/header git branch -vv echo "header section" >> app.txt git add app.txt git commit -m "h1: add header" git checkout main echo "footer section" >> app.txt git commit -m "c3: add footer" git add app.txt git add answers.md git log --oneline --decorate --graph --all -- app.txt merge --no-ff feat/header -m "merge: bring header" git add answers.md app.txt git commit -m "Save local changes before merge" git merge --no-ff feat/header git log --oneline --graph --decorate git revert HEAD -m "revert: remove footer" git reflog git reset --hard a8a35eb c98a639 (HEAD -> main) HEAD@{0}: reset: moving to HEAD^ a8a35eb HEAD@{1}: commit (merge): Save local changes before merge c98a639 (HEAD -> main) HEAD@{2}: commit: Save local changes before merge c4ac381 (tag: c2) HEAD@{3}: merge feat/header: updating HEAD c4ac381 (tag: c2) HEAD@{4}: merge feat/header: updating HEAD c4ac381 (tag: c2) HEAD@{5}: checkout: moving from feat/header to main c8b835c (feat/header) HEAD@{6}: commit: h1: add header fc16e96 (tag: c1) HEAD@{7}: checkout: moving from feat/header to feat/header fc16e96 (tag: c1) HEAD@{8}: Branch: renamed refs/heads/feature/header/promo to refs/heads/feat/header fc16e96 (tag: c1) HEAD@{10}: checkout: moving from main to feature/header/promo c4ac381 (tag: c2) HEAD@{11}: checkout: moving from feature/promo to main 1e9af35 (tag: p1, feature/promo) HEAD@{12}: commit: p1: add promo banner fc16e96 (tag: c1) HEAD@{13}: checkout: moving from feature/login to feature/promo 8eafd5e (tag: f2, feature/login) HEAD@{14}: commit: f2: login validation 1b91ebb HEAD@{15}: commit: f1: add login block c4ac381 (tag: c2) HEAD@{16}: checkout: moving from feature/menu to feature/login 229e497 (tag: m1, feature/menu) HEAD@{17}: commit: m1: menu greeting fc16e96 (tag: c1) HEAD@{18}: checkout: moving from main to feature/menu c4ac381 (tag: c2) HEAD@{19}: commit: c2: tweak greeting on main fc16e96 (tag: c1) HEAD@{20}: commit (amend): c1:initial app a109178 HEAD@{21}: commit (initial): c1:initial app git merge feature/menu git status git commit -m "merge: accept menu greeting" cat app.txt
Hello from main menu greeting accepted git checkout feature/promo
git cherry-pick f21..f2
git status
nano app.txt nano answers.md git add answers.md git add app.txt git cherry-pick -x f21..f2 it cherry-pick --continue it log --oneline --decorate --graph feature/promo git checkout feature/promo git rebase -i HEAD~3 rebase --continue git checkout feature/login rebase --onto main c4ac38112 git rebase --continue
git checkout main
git commit -m "fix: urgent patch" git checkout feature/promo git cherry-pick f600 git cherry-pick --continue git checkout main
git revert f600
git log --oneline --graph --decorate --all
