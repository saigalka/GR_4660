# GR_4660

# Инструкция для работы с Git

## Что такое Git?

**Git** - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.

Если проще то - это консольная утилита, для отслеживания и ведения истории изменения файлов, в вашем проекте. Чаще всего его используют для кода, но можно и для других файлов. Например, для картинок - полезно для дизайнеров.


## Репозитории

*Репозиторием* называют хранилище вашего кода и историю его изменений. Git работает локально и все ваши репозитории хранятся в определенных папках на жестком диске. Так же ваши репозитории можно хранить и в интернете. Обычно для этого используют три сервиса:

1. [GitHub](https://github.com/)
2. [Bitbucket](https://bitbucket.org/)
3. [GitLab](https://gitlab.com/)

### Настройка

Обязательное действие для того чтобы когда вы создавали commit, указывался автор, кто его создал.

Установим имя для вашего пользователя.
Вместо <ваше_имя> можно ввести, например, Grisha_Popov.
Кавычки оставляем.

    *git config --global user.name "<ваше_имя>"*

*Теперь установим email. Принцип тот же.*

    git config --global user.email "<адрес_почты@email.com>"


### Подготовка репозитория

Для создание репозитория необходимо создать папку и выполнить команду 
    
    *git init*  

в папке с репозиторием и у Вас создаться репозиторий (появится скрытая папка .git).



## Основные комманды GIT

### Commit

Каждая точка сохранения вашего проекта носит название коммит - **commit**. У каждого commit-a есть **hash** (уникальный id) и комментарий. Из таких commit-ов собирается *ветка*.

Если посмотреть на картинку, то становиться чуть проще с пониманием. Каждый кружок, это **commit**. Стрелочки показывают направление, из какого **commit** сделан следующий. Например C3 сделан из С2 и т. д. Все эти **commit** находятся в ветке под названием **main**. Это основная ветка, чаще всего ее называют **master** . Прямоугольник __main__ показывает в каком **commit** мы сейчас находимся, проще говоря указатель.

![пример как выглядит ветка в графике](main.png)

### Git add
Для добавления измений в коммит используется команда *git add*. Чтобы использовать команду *git add* напишите 

    git add <имя файла>
   
 или чтобы добавить все файля в папке репозитория 

    git add *


### Просмотр состояния репозитория

Для того, чтобы посмотреть состояние репозитория используется команда 

    git status
   
Для этого необходимо в папке с репозиторием написать *git status*, и Вы увидите были ли измения в файлах которые сейчас открыты, или их не было.

### Создание коммитов
Для того, чтобы создать коммит(сохранение) необходимо выполнить команду *git commit*. Выполняется она так: 

    git commit -m "<сообщение к коммиту>

Все файлы для коммита должны быть ***ДОБАВЛЕНЫ*** и сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

### Перемещение между сохранениями

Для того, чтобы перемещаться между коммитами, используется команда *git checkout*. Используется она в папке с пепозиторием следующим образом: 

    git checkout <номер коммита>

Для возврата на послейдний коммит (в котором идёт основная работа) используем комманду: 

    git checkout master

Так же эта комманда используется при возврате в основную ветку проекта, но это ниже.

### Журнал изменений
Для того, чтобы посмтреть все сделанные изменения в репозитории, используется команда:

    git log
 
Для этого достаточно выполнить команду *git log* в папке с репозиторием.

И для более краткого вывода информации:

    git log --oneline

Если же используется несколько веток, то чтобы увидель их наглядно используется комманда:

    git log --graph


## Ветки в Git

**Ветка** - это набор *commit* (кружок), которые идут друг за другом. У ветки есть название, основную ветку чаще всего называют *master* (или *main*) . Если говорить простыми словами, то ветка *master* - это наш проект.

![пример как выглядит ветка в графике](main.png)

### Создание ветки

Для того, чтобы создать ветку, используется команда *git branch*. Делается это следующим образом в папке с репозиторием: 

    git branch <название новой ветки> 

Переключаться между ветками можно такой командой: 

    git checkout <название ветки>

Т.е. мы создаём новую ветку - переключаемся на неё и работаем в ней, дабы не нарушить работу основной ветви.

### Слияние веток

Для того чтобы дабавить ветку **в** **_текущую ветку_** используется команда:

    git merge <name branch>

при удачном завершении работы, нашу ветку можно слить *в master*. 

***Важно!*** 
Для этого нужно переключиться в ветку *master* и выполнить следующие команды:

    1. **git checkout master** 
    2. **git merge <название_ветки>** 

1. *Этим мы Переключаемся в ветку master*
1. *Делаем merge нашей ветки, в ветку в которой вы находитесь. В данном примере это master*

![очередной пример как выглядит процесс слияния в графике](main_branch.png)

### Удаление веток
Для удаления уже слитой ветки (ненужной) или веки которая никак не влияет на *master* ветку, ввести команду:

    git branch -d <name branch>

Для удаления ветки с конфликтами ввести команду:

    git branch -D <name branch>

### Переименование веток

Чтобы *переименовать* текущую локальную ветку, используйте команду:

    git branch -m <новое_имя>

Чтобы переименовать локальную ветку находясь внутри другой, используйте команду:


    git branch -m <текщее_имя> <новое_имя>

## Вспомогательные команды

Просмотреть изменения относительно двух веток можно командой: 

    git diff <исходная_ветка> <целевая_ветка>


Помощь по популярным командам:

    git help

Или по конкретной команде: 

    git help <название_команды>


# Git и удалённые репозитории

## 1. Что такое удаленный репозиторий

Во-первых - это своего рода резервная копия вашего проекта, предоставляющая возможность безболезненной работы в команды, хранящийся в облаке, на стороннем сервисе, специально созданном для работы с git. А еще в таком репозитории можно пользоваться дополнительными возможностями хостинга. К примеру - визуализацией истории или возможностью разрабатывать вашу программу непосредственно в веб-интерфейсе.

### Клонирование

Клонирование - это когда вы копируете удаленный репозиторий к себе на локальный ПК. Это то, с чего обычно начинается любой проект. При этом вы переносите себе все файлы и папки проекта, а также всю его историю с момента его создания. Чтобы склонировать проект, сперва, необходимо узнать где он расположен и скопировать ссылку на него. 

    git clone https://github.com/CinemaStyle/GR_4660.git

При клонировании в текущий каталог, там будет создана папка, в которую поместятся все проектные файлы и скрытая директория .git, с самим репозиторием, или с необходимой информацией о нем. В такой ситуации, для клонируемого репозитория, по умолчанию, будет создана папка с одноименным названием, но его можно залить и в другую директорию, например:

    git clone https://github.com/CinemaStyle/GR_4660.git new_folder

Вместо **git clone** можно было бы создать пустой локальный git-репозиторий, выполнив команду **git init**. Затем подключить наш удаленный репозиторий командой 

    git remote add origin https://github.com/CinemaStyle/GR_4660.git

 После чего вручную загрузить изменения с удаленного репозитория командой **git pull**.


## 2. Подключение к удаленному репозиторию

Чтобы загрузить что-нибудь в удаленный репозиторий, сначала нужно к нему подключиться.
Чтобы связать наш локальный репозиторий с репозиторием на GitHub, выполним следующую команду в терминале. Обратите внимание, что нужно обязательно изменить URI репозитория на свой.

    git remote add origin https://github.com/CinemaStyle/GR_4660.git

Проект может иметь несколько удаленных репозиториев одновременно. Чтобы их различать, мы дадим им разные имена. Обычно главный репозиторий называется **origin**.

## 3. Отправка изменений на сервер

Сейчас самое время переслать наш локальный коммит на сервер. Этот процесс происходит каждый раз, когда мы хотим обновить данные в удаленном репозитории.
Команда, предназначенная для этого - **push**. Она принимает два параметра: *имя удаленного репозитория* (мы назвали наш origin) и ветку, в которую необходимо внести изменения (**master или main** — это ветка по умолчанию для всех репозиториев).

    $ git push origin main

Эта команда немного похожа на **git fetch**, с той лишь разницей, что при помощи **fetch** мы импортируем коммиты в локальную ветку, а применив **push**, мы экспортируем их из локальной в удаленную. Если вам необходимо настроить удаленную ветку используйте **git remote**. 

    Однако пушить надо осторожно, ведь рассматриваемая команда перезаписывает безвозвратно все изменения. 

В большинстве случаев, ее используют, чтобы опубликовать выгружаемые локальные изменения в центральный репозиторий. А еще ее применяют для того, чтобы поделиться, внесенными в локальный репозиторий, нововведениями, с коллегами или другими удаленными участниками разработки проекта. 

Подытожив сказанное, можно назвать **git push** - командой выгрузки, а **git pull** и **git fetch** - командами загрузки или скачивания. После того как вы успешно запушили измененные данные, их необходимо внедрить или интегрировать, при помощи команды слияния **git merge**.

## 4. Запрос изменений с сервера

Если вы сделали изменения в вашем удаленном репозитории, другие пользователи могут скачать изменения при помощи команды **pull**.

Команда **git pull** используется для синхронизации локальной рабочей копии и всех ссылочных объектов с удаленным репозиторием.

Локальный репозиторий получает изменения из переданного удаленного репозитория и обновляет рабочую копию в соответствии с удаленным репозиторием. По умолчанию слияние удаленной ветки с локальной происходит именно в fast-forward режиме, так что включать его специально не требуется


    $ git pull origin master

На самом деле, новых команд здесь нет. Команда **git pull** это просто сокращение последовательного применения **git fetch** и **git merge**. Но используется **git pull** намного чаще.

## 5. Создание форка репозитория на GitHub. Пулл-реквесты.

Одной из самых важных частей GitHub является создание форков.
**Форк** (*от англ. __fork__ – вилка*) – точная копия репозитория, но в вашем аккаунте. Форки нужны, чтобы вносить свои изменения в проект, к репозиторию которого у вас нет прямого доступа.

*Пулл-реквест* (_от англ. **pull-request** – запрос **pull**_) – функция GitHub, позволяющая попросить владельца репозитория, от которого мы сделали форк, загрузить наши изменения обратно в свой репозиторий.

Если коротко, форки и пулл-реквесты нужны, чтобы любой пользователь мог внести свой вклад в любой открытый проект, репозиторий которого есть на GitHub. Кроме того, перед тем как влить ваши изменения в основной репозиторий, ответственные обязательно проверят ваш код на наличие ошибок и уязвимостей.

1. Для начала зайдем на страницу репозитория проекта. Нажимаем на **кнопку Fork**, как показано на картинке. После этого Git создаст точную копию этого репозитория в вашем аккаунте.

2. Клонируем репозиторий к себе на компьютер командой **git clone**. Создадим файл README.md с описанием проекта, чтобы другим пользователям было понятно, в чем отличие этой реализации от остальных.

3. Сделаем коммит и выполним **git push**, чтобы загрузить наши изменения в удаленный репозиторий.

4. Теперь GitHub подсказывает нам, что наша ветка опережает ветку исходного репозитория на один коммит и предлагает сделать **пулл-реквест**.

5. Нажимаем на кнопку **Compare** на подсказке GitHub, либо переходим на вкладку **Pull Requests** и нажимаем **New pull request**.

6. Перед нами откроется страница создания пулл-реквеста. Здесь мы можем просмотреть внесенные изменения и выбрать две ветки: одну в исходном репозитории, на нее будут залиты наши изменения, вторую – в нашем репозитории, с нее будут скачаны изменения. Как только мы выбрали ветки и убедились, что не внесли никаких лишних изменений, нажимаем кнопку **Create pull request**.

7. Теперь мы попадаем на страницу описания наших изменений. Здесь необходимо описать, что за изменения вы внесли и почему они были необходимы. Сообщение, которое оставили мы, видно на картинке. Оно отражает суть и необходимость внесенных изменений. Как только мы закончили с описанием, можно нажимать кнопку **Create pull request**.

8. Теперь мы попадаем на страницу уже созданного пулл-реквеста в изначальном репозитоии. 

После того, как владелец репозитория просмотрит наши изменения и убедится, что они не имеют вредоносный характер, он сможет принять наш пулл-реквест. Тогда все изменения, добавленные в этот пулл-реквест нами, будут залиты в исходный репозиторий







