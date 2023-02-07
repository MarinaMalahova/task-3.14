##GIT DIFF
___
Команда **git diff** используется для вычисления разницы между любыми двумя Git деревьями. Это может быть разница между вашей рабочей копией и индексом (собственно git diff), разница между индексом и последним коммитом (git diff --staged), или между любыми двумя коммитами (git diff master branchB).
Если вы хотите понять что конкретно поменялось, а не только какие файлы были изменены — вы можете использовать команду **git diff**. Git diff показывает вам непосредственно добавленные и удалённые строки — патч как он есть.


Допустим, вы снова изменили и проиндексировали файл README, а затем изменили файл CONTRIBUTING.md без индексирования. Если вы выполните команду git status, вы опять увидите что-то вроде:

    $ git status
    On branch master
    Your branch is up-to-date with 'origin/master'.
    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

         modified:   README

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md

Чтобы увидеть, что же вы изменили, но пока не проиндексировали, наберите **git diff** без аргументов:

    $ git diff
    diff --git a/CONTRIBUTING.md b/CONTRIBUTING.md
    index 8ebb991..643e24f 100644
    --- a/CONTRIBUTING.md
    +++ b/CONTRIBUTING.md
    @@ -65,7 +65,8 @@ branch directly, things can get messy.
     Please include a nice description of your changes when you submit your PR;
    if we have to read the whole diff to figure out why you're contributing
    in the first place, you're less likely to get feedback and have your change
    -merged in.
    +merged in. Also, split your changes into comprehensive chunks if you patch is
    +longer than a dozen lines.

    If you are starting to work on a particular area, feel free to submit a PR
    that highlights your work in progress (and note in the PR title that it's

Эта команда сравнивает содержимое вашего рабочего каталога с содержимым индекса. Результат показывает ещё не проиндексированные изменения.

Если вы хотите посмотреть, что вы проиндексировали и что войдёт в следующий коммит, вы можете выполнить **git diff --staged**. Эта команда сравнивает ваши проиндексированные изменения с последним коммитом:

    $ git diff --staged
    diff --git a/README b/README
    new file mode 100644
    index 0000000..03902a1
    --- /dev/null
    +++ b/README
    @@ -0,0 +1 @@
    +My Project

Важно отметить, что git diff сама по себе не показывает все изменения сделанные с последнего коммита — только те, что ещё не проиндексированы. Такое поведение может сбивать с толку, так как если вы проиндексируете все свои изменения, то git diff ничего не вернёт.

Другой пример: вы проиндексировали файл CONTRIBUTING.md и затем изменили его, вы можете использовать git diff для просмотра как проиндексированных изменений в этом файле, так и тех, что пока не проиндексированы. Пример:

    $ git add CONTRIBUTING.md
    $ echo '# test line' >> CONTRIBUTING.md
    $ git status
    On branch master
    Your branch is up-to-date with 'origin/master'.
    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

    modified:   CONTRIBUTING.md

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md

Используйте **git diff** для просмотра непроиндексированных изменений

    $ git diff
    diff --git a/CONTRIBUTING.md b/CONTRIBUTING.md
    index 643e24f..87f08c8 100644
    --- a/CONTRIBUTING.md
    +++ b/CONTRIBUTING.md
    @@ -119,3 +119,4 @@ at the
    ## Starter Projects

    See our [projects list](https://github.com/libgit2/libgit2/blob/development/PROJECTS.md).
    +# test line

а так же **git diff --cached** для просмотра проиндексированных изменений (--staged и --cached синонимы):

    $ git diff --cached
    diff --git a/CONTRIBUTING.md b/CONTRIBUTING.md
    index 8ebb991..643e24f 100644
    --- a/CONTRIBUTING.md
    +++ b/CONTRIBUTING.md
    @@ -65,7 +65,8 @@ branch directly, things can get messy.
    Please include a nice description of your changes when you submit your PR;
    if we have to read the whole diff to figure out why you're contributing
    in the first place, you're less likely to get feedback and have your change
    -merged in.
    +merged in. Also, split your changes into comprehensive chunks if you patch is
    +longer than a dozen lines.

     If you are starting to work on a particular area, feel free to submit a PR
    that highlights your work in progress (and note in the PR title that it's

[<Вернуться к содержанию](/readme.md)
[<Перейти к предыдущей странице](/git%20status.md)
[Перейти к следующей странице>](/git%20difftool.md)