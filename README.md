# Шпаргалка по Git. Работа в терминале

## Навигация

1. Вывести путь к текущей директории (папке):
```bash
pwd
```
2. Изменить текущую рабочую директорию на ту, которая указана в качестве параметра:
```bash
cd %имя-папки%
``` 
3. Переход к домашней директории: 
```bash 
cd ~
``` 
4. Возврат в родительскую директорию, т.е. на уровень выше: 
```bash
cd .. %.. вместо названия папки%
``` 
5. Переместиться сразу через несколько директорий: 
```bash
cd %папка/другая папка/ещё папка%
```
6. Отобразить файлы и папки текущей директории:
```bash
ls
``` 
7. Вывести расширенный список текущей директории со скрытыми файлами:
```bash 
ls -a 
```
8. Вывести содержимое домашней директории: 
```bash 
ls ~
```    
9. Вывести содержимое родительской директории: 
```bash
ls ..
``` 

## Работа с файлами и папками 

### Создание

1. Создать файл в текущей папке. P.S. Лучше сразу указывать расширение файла:
```bash
touch %имя-файла%
```
2. Создать файл ***file.txt*** на две папки выше по иерархии: 
```bash 
touch ../../file.txt 
```
3. Если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел: 
```bash
touch index.html style.css script.js
``` 
4. Создать директорию (папку):
```bash
mkdir %имя-папки%
```
5. Создать целую структуру директорий одной командой:
```bash 
mkdir -p
``` 

Пример: 
```bash
mkdir -p dir1/dir-inside/dir-deeper-inside. 
```
6. Создать папку в домашней директории:
```bash 
mkdir ~ 
```
7. Создать папку в родительской директории:
```bash 
mkdir .. 
```

### Копирование и перемещение

1. Копировать файл в место, указанное в параметре:
```bash
cp %что-копируем% %куда-копируем% 
```

Можно указать сразу несколько файлов: 
```bash
cp %что_копируем% %что_копируем% %что_копируем% %куда_копируем%
```

Пример: 
```bash 
cp index.html style.css script.js src/. index.html, style.css, script.js %скопировать в папку src%
```
2. Переместить файл(ы) или папку(и) в нужную директорию:
```bash
mv %что_переместить% %куда_переместить% 
```

### Чтение

1. Чтение (распечатка в консоли) текстового файла:
```bash 
cat %имя-файла%   
```

### Удаление

1. Удалить файл: 
```bash
rm %имя-файла%
``` 
2. Удалить пустую папку:
```bash 
rmdir %имя-папки% 
```  
3. Удалить папку со всем её содержимым:
```bash
rm –r %имя-папки% 
```

## Установка и базовая настройка git (.gitconfig)

1. Показать версию git. Так можно проверить, установлен ли git на устройстве:
```bash
git version
```
2. Настройка параметра имени:
```bash
git config --global user.name "ваше имя" 
```
3. Настройка параметра электронной почты:
```bash
git config --global user.email ваш-адрес-эл.почты 
```
4. Чтобы проверить содержимое файла конфигурации Git. Например, что указано в **user.name** и **user.email**:
```bash
cat ~/.gitconfig %или% git config --list
```

## Создание репозитория

Инициализация репозитория в папке, в которой мы сейчас находимся:
```bash
git init 
```
 
## Удаление («разгитивание») репозитория

Удалить скрытую подпапку **.git**:
```bash
rm -rf .git 
```

## Проверка статуса, состояния репозитория

```bash
git status
```

## Добавление файлов в репозиторий и их сохранение, просмотр истории коммитов

1. Подготовить файл к сохранению:
```bash
git add
``` 
2. Подготовить к сохранению сразу все файлы:
```bash
git add --all 
```
3. Подготовить к сохранению текущую папку со всеми файлами:
```bash
git add .
```
4. Сохранить файл и сделать коммит с сообщением:
```bash
git commit -m 
``` 

Пример: 
```bash
git commit -m 'Мой первый коммит!'
```
5. Просмотр полной истории коммитов:

```bash
git log 
```

6. Просмотр сокращённой истории коммитов:

```bash
git log --oneline
```

## Генерация и проверка наличия SSH-ключей

1. Вывести список созданных ключей. Обычно они находятся в домашней директории:
```bash
ls -la .ssh/ 
```
2. Первый вариант генерации SSH-ключей:
```bash
ssh-keygen -t ed25519 -C "электронная почта, к которой привязан аккаунт на GitHub" 
```
3. Второй вариант генерации SSH-ключей, если в первом возникла ошибка:
```bash
ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан аккаунт на GitHub" 
```
4. Чтобы проверить, действительно ли сгенерировались ключи:
```bash
ls -a ~/.ssh 
```

## Скопировать в буфер обмена

```bash
clip
``` 

Например: 
```bash 
clip < ~/.ssh/id_ed25519.pub %«Скопируй в буфер обмена всё содержимое файла ~/.ssh/id_ed25519.pub»% 
```

Если clip не сработает, можно использовать: 
```bash
cat ~/.ssh/id_ed25519.pub 
```

И далее скопировать вывод в буфер обмена из консоли.

## Проверка правильности ключа, указанного на GitHub

```bash 
ssh –T git@github.com 
```

## Связка удаленного и локального репозиториев

1. Чтобы связать локальный репозиторий с удалённым:
```bash 
git remote add %нужно передавать два параметра: имя удаленного репозитория и его URL%
``` 

Пример: 
```bash 
git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git
```
2. Чтобы убедиться, что репозитории связаны:
```bash 
git remote -v 
```

## Отправить изменения на удаленный репозиторий

```bash 
git push 
```

В первый раз нужно будет дописывать флаг ```-u``` (связывает локальную ветку с одноимённой удаленной) и 
параметры ```origin``` (имя удаленного репозитория) и **main** или **master** (название текущей ветки). 

Пример: 

```bash 
$ git push -u origin master
```

В последующие разы можно писать просто: 

```bash 
git push
```

## Полезности

* С помощью ```&&``` можно выполнить несколько команд сразу — одну за другой.
* Команды, которые выполнялись в консоли, попадают в историю. 
Можно перемещаться по этой истории при помощи стрелок ```↑↓```.
* При нажатии на ```Tab``` (дважды для поиска команд и один раз для автозаполнения) консоль предложит 
несколько вариантов продолжения команды.

## Немного о хеше (уникальный идентификатор коммита)

Пример, как выглядит хеш:

```bash
commit 51b4eac98af84251c4ea43be6cbb444dc0e2c450
```

Основные моменты:

* Каждый хеш всегда уникален; 
* Git преобразует информацию о коммите с помощью алгоритма **SHA-1**; 
* С помощью хеша можно узнать всю информацию о коммите (автора, дату, содержимое 
закоммиченных файлов); 
* Хеши хранятся в скрытой папке ```.git```. 

## Элементы описания коммита, ```git log``` 

Описание коммита состоит из следующих элементов:

* Хеш коммита (строка из цифр и латинских букв после слова ```commit```);
* Author — имя автора и его электронная почта;
* Date — дата и время создания коммита;
* Сообщение коммита. 

## Сокращённое описание коммита, ```git log --oneline```

Будет показан сокращённый хеш и сообщение коммита. 

P.S. Если после ввода ```git log```/```git log --oneline``` выход из 
просмотра описания коммита не произошёл автоматически, нужно нажать ```Q``` на клавиатуре.

## HEAD

Это один из служебных файлов папки ```.git```. Он указывает на коммит, 
сделанный последним (т.е. на самый новый).

Вместо хеша последнего коммита можно написать слово ```HEAD``` — Git поймёт, 
что речь именно о последнем коммите.

## Статусы файлов, ```git status```

В Git есть следующие статусы файлов:

* **untracked** — неотслеживаемый. Git знает, что файл существует,
но не следит за изменениями в нём. У таких файлов нет предыдущих версий, 
зафиксированных в коммитах или через команду ```git add```;
* **staged** — подготовленный для коммита. Если изменить файл после использования команды 
```git add```, статус **staged** изменится на **modified**;
* **tracked** — отслеживаемый. Противоположность **untracked**. Статус получают файлы 
после использования команды ```git add``` (у них ещё и статус **staged**) 
и команды ```git commit```. 
То есть все файлы, в которых Git так или иначе отслеживает изменения;
* **modified** — измененный. Git сравнил содержимое файла с последней сохранённой 
версией и нашёл отличия. Например, файл был закоммичен и после этого изменён. 

Наглядная схема жизненного цикла файла в Git:

```mermaid
graph LR;
   untracked -- "git add" --> staged;
   staged -- "git commit" --> tracked/commited;  
   staged -- "Изменения" --> modified; 
   tracked/commited -- "Изменения" --> modified;
   modified -- "git add" --> staged;	
```

Команда ```git status``` показывает следующие состояния:

* **staged** (```Changes to be committed``` в выводе ```git status```);
* **modified** (```Changes not staged for commit```);
* **untracked** (```Untracked files```).

Если в выводе команды ```git status``` у файла не отображены никакие состояния, 
значит он имеет состояние **tracked**.

## Оформление сообщений к коммитам

В выводе команды ```git log --oneline``` умещается максимум 72 первых символа сообщения, 
поэтому лучше не указывать сообщения длиннее.

Для сообщений на русском языке часто рекомендуют использовать инфинитивы. 
Например: ```Добавить тесты для CatService```, ```Исправить ошибку #123``` и т.д.

Для сообщений на английском рекомендуется использовать повелительное 
наклонение. Например: ```Use library mega_lib_300```, ```Fix exit button``` и т.д.

**Общие рекомендации** по тому, как правильно составить сообщение. Оно должно быть:

* Относительно коротким, чтобы его легко можно было прочитать;
* Информативным. 

Примеры **хороших** коммитов:

* ```Оптимизировать загрузку фотографий в галерее```;
* ```Исправить ошибку #123 для пользователей без отчества```;
* ```Добавить сортировку по полю «Сумма»```;
* ```Кнопку «Выход» сделать синей```.

### Популярные подходы к оформлению сообщений коммитов

#### Корпоративный

Связана с применением **Jira** (система для организации проектов и задач). 
У каждой задачи в **Jira** есть идентификатор из нескольких заглавных латинских букв и номера. 

В корпоративном стиле в начале сообщения обычно указывают **Jira-ID**, а после — текст сообщения. 
Например:

```bash
git commit -m "LGS-239: Добавить функцию отслеживания трекера посылок"
```

#### Conventional Commits («соглашение о коммитах»)

Подходит для репозиториев с исходным кодом программ. Предлагает следующий формат коммита:

```<type>: <сообщение>```. **Type** - тип изменений. Таких типов достаточно много. Например:
* **feat** — для новой функциональности;
* **fix** — для исправленных ошибок.

Пример:

```bash
git commit -m "feat: добавить калькулятор подсчёта стоимости заказов за неделю" 
```

Ещё больше типов можно увидеть на [сайте с описанием этого стиля](https://www.conventionalcommits.org/ru/v1.0.0-beta.4/#спецификация).

#### GitHub-стиль

GitHub можно использовать ещё и для ведения списка задач. Если коммит «закрывает» или 
«решает» какую-то задачу, то в его сообщении удобно указывать ссылку на неё. 
Для этого в любом месте сообщения нужно указать ```#<номер задачи>```. Например:

```bash
git commit -m "Исправить #123, добавить график перерывов на смене"
```

Так GitHub свяжет коммит и задачу. 



