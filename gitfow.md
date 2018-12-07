Gitflow
-
- Инициализация
```sh
git flow init
```

- Начало новой фичи
```sh
git flow feature start <feature_name>
```

- Публикация фичи
```sh
git flow feature publish <feature_name>
```

- Начало багфикса (по умолчанию от ветки `dev`)
```sh
git flow bugfix start <bugfix_name>
```

- Публикация багфикса (по умолчанию в ветку `dev`)
```sh
git flow bugfix publish <bugfix_name>
```

__Хотфикс__

- Начать слежение за удалённой веткой `hotfix/x.y`
```sh
git flow hotfix track <x.y>
```

- Начать хотфикс `fixname` от ветки `hotfix/x.y`
```sh
git flow bugfix start <fixname> <hotfix/x.y>
```

- Публикация хотфикса `fixname`
```sh
git flow bugfix publish <fixname>
```

__Локальный хотфикс, если релиз вытянут на локальную машину__

- Начало хотфикса (по умолчанию от релиза `release_name/x.y`)
```sh
git flow hotfix start <hotfix_name> <release_name/x.y>
```

- Публикация хотфикса (по умолчанию в релиз `release_name/x.y`)
```sh
git flow hotfix publish <hotfix_name> <release_name/x.y>
```
