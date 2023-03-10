##GIT ADD
____
Команда **git add** — это первая команда в цепочке операций, предписывающей Git *«сохранить»* снимок текущего состояния проекта в истории коммитов. Когда git add используется как отдельная команда, она переносит ожидающие изменения из рабочего каталога в раздел проиндексированных файлов.

Команда git add добавляет содержимое рабочего каталога в индекс (staging area) для последующего коммита. По умолчанию git commit использует лишь этот индекс, так что вы можете использовать git add для сборки слепка вашего следующего коммита.

Чтобы начать отслеживание файла README, вы можете выполнить следующее:

    $ git add README

Если вы выполните команду status, то увидите, что файл README теперь отслеживаемый и добавлен в индекс:

    $ git status
    On branch master
    Your branch is up-to-date with 'origin/master'.
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)

         new file:   README

Вы можете видеть, что файл проиндексирован, так как он находится в секции «Changes to be committed». Если вы выполните коммит в этот момент, то версия файла, существовавшая на момент выполнения вами команды git add, будет добавлена в историю снимков состояния. Команда git add принимает параметром путь к файлу или каталогу, если это каталог, команда рекурсивно добавляет все файлы из указанного каталога в индекс.


Чтобы добавить отслеживание новых файлов, необходимо использовать команду для добавления нескольких файлов по имени.

     git add <filename> </filename> 
    
В случае если у вас много файлов для добавления, можно воспользоваться командой **git add**., которая добавляет отслеживание для всех новых файлов из текущей директории.

 А команда **git add -A** добавляет ещё и удалённые файлы, не только из текущей директории, но и из всего локального репозитория.

 

Если вы выполните **git add** с опцией **-i** или **--interactive**, Git перейдёт в интерактивный консольный режим, отобразив что-то подобное:

    $ git add -i
           staged     unstaged path
    1:    unchanged        +0/-1 TODO
    2:    unchanged        +1/-1 index.html
    3:    unchanged        +5/-1 lib/simplegit.rb

    *** Commands ***
    1: [s]tatus     2: [u]pdate      3: [r]evert     4: [a]dd untracked
    5: [p]atch      6: [d]iff        7: [q]uit       8: [h]elp
    What now>

Вы можете видеть, что эта команда показывает вашу область подготовленных изменений в уникальном представлении — вообще говоря, ту же информацию вы получите с помощью команды git status, но несколько более сжато и информативно. Эта команда показывает проиндексированные изменения слева, а непроиндексированные — справа.

Затем следует раздел со списком команд. С их помощью вы можете выполнить множество вещей — добавить или исключить файлы из индекса, добавить в индекс части файлов, добавить в индекс неотслеживаемые файлы и просмотреть проиндексированные изменения.

[<Вернуться к содержанию](/readme.md)
[<Перейти к предыдущей странице](/comands%20git.md)
[Перейти к следующей странице>](/git%20status.md)