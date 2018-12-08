Глобальные настройки
-

- Указание имени 
```sh
git config --global user.name "Yauheni Sliaptsou"
git config user.name "Yauheni Sliaptsou"
```

- Указание email
```sh
git config --global user.email j.sliapcou@abcmobile.com
git config user.email j.sliapcou@abcmobile.com
```

- Алиас для git. В конец файла `C:\Program Files\Git\etc\bash.bashrc` вставить строки
```sh
#alias for Git
alias g='git'
```

- Присвоение алиаса команде
```sh
git config --global alias.cob "checkout -b"
git config --global alias.pud "pull upstream dev"
git config --global alias.cod "checkout dev"
git config --global alias.st status
git config --global alias.d diff
git config --global alias.cma "commit -a"
git config --global alias.cmm "commit --amend"
git config --global alias.pso "push origin"
git config --global alias.brd "branch -D"
git config --global alias.pod "push origin --delete"
git config --global alias.df "diff --staged"
git config --global alias.sth "stash"
git config --global alias.stha "stash apply"
git config --global alias.pum "pull upstream master"
git config --global alias.rmc "rm --cached"
git config --global alias.ls "log --stat"
git config --global alias.lolg "log --oneline --graph"
git config --global alias.rpo "remote prune origin"
? git config --global alias.lpf "log --pretty=format:"%h - %an, %ar : %s""

git config --global alias.co checkout
git config --global alias.cm commit
git config --global alias.ps push
git config --global alias.br branch
git config --global alias.ft fetch
git config --global alias.mr merge
```

- Задать шаблон для коммитов по умолчанию
```sh
git config --global commit.template C:/ABC/.git-commit-template.txt
```

- Включить подпись gpg ключом
```
git config --global commit.gpgsign true
```

- Проверка настроек
```sh
git config --list
```

- Сделать `Nano` редактором по умолчанию
```sh
git config --global core.editor "nano"
```

- Сделать `Notepad++` редактором по умолчанию
```sh
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```

- В PHPStorm `Tools > Terminal` впиши
```sh
"C:\Program Files\Git\bin\sh.exe" --login -i
```

Основы
-

- Добавление файла 'file_name.ext' в индексацию
```sh
git add file_name.ext
```

- Добавление всех файлов с расширением 'ext' в индексацию
```sh
git add *.ext
```

- Состояние файлов
```sh
git status
```

- Узнать что изменено, но не проиндексировано
```sh
git diff
```

- Узнать что из проиндексированого войдёт в следующий коммит
```sh
git diff --staged
```

- Чтобы сделать коммит (например, исправление ошибки) в ветке «А», работая в ветке «Б»,
```sh
# Сначала необходимо переключиться на ветку с коммитом, скопировать commit-id, а потом перейти обратно в свою ветку. Затем выполните следующую команду, чтобы получить коммит в рабочей ветке:
git cherry-pick <commit-id>
```

- Временное скрытие изменений
```sh
git stash
```

- Извлечение несохраненных изменений
```sh
git stash apply
```

- Создание коммита с комментарием
```sh
git commit -m "commit comment"
```

- Создание коммита с добавлением файлов в индексацию
```sh
git commit -a -m 'commit comment'
```

- Добавление изменений к коммиту. Второй коммит заменяет результат первого
```sh
git commit --amend -m "сообщение"
git commit --amend --no-edit #не добавлять ещё одно сообщение
git push origin <имя ветки> -f # код запушен в удаленный репозиторий и нужно изменить сообщение
```

- Отменить последний коммит
```sh
git reset --hard <commit hash>
```

- Отмена проиндексированных изменений (перед коммитом) 'file_name.ext' (файл не войдёт в коммит)
```sh
git reset HEAD file_name.ext
```

- **(Warning)** Отмена внесенных изменени в файл 'file_name.ext'
```sh
git checkout -- file_name.ext
```

- **(Warning)** Отмена последнего коммита ([подробнее](https://githowto.com/ru/undoing_committed_changes))
```sh
git revert HEAD
```

Работа с ветками
-----------

- Создание ветки `fix-bug` с последующим автоматическим переходом в неё
```sh
git checkout -b fix-bug
```

- Отправка ветки `fix-bug` на удаленный сервер `origin`
```sh
git push origin fix-bug
```

- Слияние c текущей веткой ветки `master` с удаленного сервер `upstream`
```sh
git merge upstream/master
```

- Получение с удаленной ветки всех изменений и её слияние в текущую
```sh
git pull
```

- Удалить ссылки на ветки удаленного репозитория, которых больше не существует ([подробнее](https://ru.stackoverflow.com/questions/577369/%D0%9A%D0%B0%D0%BA-%D1%83%D0%B4%D0%B0%D0%BB%D0%B8%D1%82%D1%8C-%D0%BB%D0%BE%D0%BA%D0%B0%D0%BB%D1%8C%D0%BD%D1%83%D1%8E-%D1%81%D1%81%D1%8B%D0%BB%D0%BA%D1%83-%D0%BD%D0%B0-%D0%BD%D0%B5%D1%81%D1%83%D1%89%D0%B5%D1%81%D1%82%D0%B2%D1%83%D1%8E%D1%89%D1%83%D1%8E-%D1%83%D0%B6%D0%B5-%D1%83%D0%B4%D0%B0%D0%BB%D0%B5%D0%BD%D1%83%D1%8E-%D0%B2%D0%B5%D1%82%D0%BA%D1%83))
```sh
git remote prune origin
```

- Удаление ветки `fixbug` c удаленного сервера `origin` ([подробнее](https://git-scm.com/book/ru/v2/%D0%92%D0%B5%D1%82%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B2-Git-%D0%A3%D0%B4%D0%B0%D0%BB%D1%91%D0%BD%D0%BD%D1%8B%D0%B5-%D0%B2%D0%B5%D1%82%D0%BA%D0%B8))
```sh
git push origin --delete fixbug
```

- Удаление локальной ветки `fixbug` ([подробнее](https://git-scm.com/book/ru/v2/%D0%92%D0%B5%D1%82%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B2-Git-%D0%A3%D0%B4%D0%B0%D0%BB%D1%91%D0%BD%D0%BD%D1%8B%D0%B5-%D0%B2%D0%B5%D1%82%D0%BA%D0%B8))
```sh
git branch -d fixbug
```

- Переименование локальной ветки
```sh
git branch -m <старое имя ветки> <новое имя ветки>
```

- Переименование текущей локальной ветки
```sh
git branch -m <новое имя ветки>
```

- Переименование удаленной ветки
```sh
git push <имя удаленной ветки> --delete <старое имя ветки>
git push <имя удаленной ветки> <новое имя ветки>
#Если имя локальной ветки не совпадает с именем ветки в репозитории
git push <имя удаленной ветки> <локальное имя ветки>:<имя удаленной ветки>
```

- Отслеживание удаленной ветки `origin/fixbug` текущей локальной веткой.
```sh
git branch -u origin/serverfix
```

- Отслеживание удаленной ветки `origin/fixbug` локальной веткой `fixbug` после клонирования репозитория
```sh
git checkout --track fixbug origin/fixbug
```

Работа с репозиториями
-----------

- Добавление удаленного репозитория `Cheatsheets` на удаленном сервере `origin`
```sh
git remote add origin git@github.com:sliaptsou/Cheatsheets.git
```

- Клонирование репозитория 
```sh
git clone git@github.com:ABCMobilecom/SP.git
```

- Клонирование репозитория в папку `repodir`
```sh
git clone git@github.com:ABCMobilecom/SP.git repodir
```

- URL адреса удаленных репозиториев
```sh
git remote -v
```

- Добавление удаленного репозитория `git@github.com:ABCMobilecom/SP.git` под именем `sp`
```sh
git remote add sp git@github.com:ABCMobilecom/SP.git
```

- Получение данных из удаленного репозитория `git@github.com:ABCMobilecom/SP.git` под именем `sp`. В отличие от `git pull` не выполняет автоматическое слияние.
```sh
git remote fetch sp
```

- Отправка данных в удаленный репозиторий `origin` из локальной ветки `master`
```sh
git push origin master
```

- Просмотр удаленного репозитория `origin`
```sh
git remote show origin
```

- Переименование удаленного репозитория `sp` в `spnew`
```sh
git remote rename sp spnew
```

- Удаление удаленного репозитория `sp`
```sh
git remote rm sp
```


Работа с файлами
-----------
- **(Warning)** Удалить файл 'file_name.ext' из проекта и из Git
```sh
git rm -f file_name.ext
```

- Удалить файл 'file_name.ext' из области индексирования, но не из проекта
```sh
git rm --cached file_name.ext
```

- Переименование файла из 'file_name.ext' в 'file_name_new.ext'
```sh
git mv file_name.ext file_name_new.ext
```

Просмотр истории версий
-----------
- Просмотр истории версий
```sh
git log
```

- Просмотр разницы между коммитами, ограничивающуюся последними двумя записями
```sh
git log -p -2
```

- Краткая статистика по каждой версии
```sh
git log --stat
```

- Информация о коммитах в одну строку
```sh
git log --pretty=oneline
```

- Информация о коммитах в формате (параметры команды в [документации](https://git-scm.com/docs/git-log))
```sh
git log --pretty=format:"%h - %an, %ar : %s"
```

- Ограничение вывода log коммитами за последние 2 дня (параметры команды в [документации](https://git-scm.com/docs/git-log))
```sh
git log --since=2.days
```

- Вывод log для функции `function_name`
```sh
git log -S 'function_name'
```
