# Что нужно делать, чтобы отправить проект в  GitHUB?

## Создаем локальный репозиторий на своем ПК

### Для того чтобы создать локальный репозиторий на своем ПК
### нужно скачать GIT. Для этого переходим на сайт [Download Git](https://git-scm.com/download/win "Reference for downloading Git for desktop")
### Далее скачиваем нужный вариант установщика.
### Запускаем и устанаввливаем Git вместе с Git Bash-командной строкой Linux для взаимодействия с Git.
После установки делаем рестарт ПК, далее в поиске Windows находим Git Bash и запускаем.

## Работа с Git Bash
### По умолчанию терминал открывается в домашней директории тек4ущего пользователя.
чтобы это проверить нужно ввести в терминале:
pwd и нажать Enter.

### мы увидим ответ типа  /c/Users/User Name
Это и есть домашняя директория.
для перемещения по директориям используются команды в терминале:

cd directory/
cd directory/subDirectory/
cd directory/subDirectory/sub-sub-directory/
или в обратном порядке:
cd с/
cd ..  переводит нас на уровень выше

## Создание Директорий и файлов
###
touch filename.fileextension   создание файла в текущей директории
mkdir nameDirectory/    создание новой директории
mkdir -p cd directory/subDirectory/sub-sub-directory/ создаем целую структуту директорий

cd directory/subDirectory/sub-sub-directory/ && mkdir nameDirectory/ двойная команда: переход в директорию по пути directory/subDirectory/sub-sub-directory/ и создание в ней новой директории с именем nameDirectory

## Перемещение и копирование файлов и папок
### mv filename destFolder
### mv test.txt c/User/newDir/destDir

Копирование 
cp filename destFolder
cp ../test.txt c/User/newDir/destDir


Для просмотра файлов в текущей директории служит команда:

ls
ls -a  покажет все файлы, включая скрытые

## Создание локального репозитория
### Для создания локального репозитория следут выполнить команды:
cd~ 
pwd
mkdir GitPractice создали в до машней директории папку /GitPractice
cd GitPractice перешли в неё
git init инициализируем директорию как Гит репозиторий
ls -a прооверяем что в ней появилась скрытая папка .git
Локальный репосзиторий создан!

# Создание аккаунта на сайте GitHUB

### Переходим на сайт [GitHUB](https://github.com)
Регистрируем логин и пароль.
Входим под ним
Теперь можно создать удаленный репозиторий на сайте GitHUB. Для этого нажимаем NEW и вводим имя, лучше если оно будет совпадать. В нашем случае назовем его '''GitPractice'''.

Удаленный репозиторий создан)!!!

# Связываем локальный репозиторий с удаленным

### в Git Bash нужно сгенерировать ssh ключи: Публичный и приватный. Публичный служит для связи между сайтом и нашим репозиторием, а приватный для шифрования и расшифровки сообщений.
Для этого переходим в домашнюю директорию
cd ~
проверяем есть ли уже ключи на нашем ПК:   
$ ls -la .ssh/ # вывели список созданных ключей

Если таких нет, то генерируем новые:
$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"

снова проверяем наличие ключей:
ls -a ~/.ssh

Создается 2 файла .pub и без расширения.
читаем публичный .pub 
cat ed25519.pub
копируем его содержимое, затем переходим на сайт GitHUB, Settings, SSH & GPG Keys
Добавляем New SSH Keys и вставляем его в соотв окно.
Заполняем 2 оставшихся поля


В Bash проверяем правильность ключа
$ ssh -T git@github.com


## Связь репозиториев
В GitHUB переходим в наш репозиторий и копируем путь к нему 
В Bash переходим в наш каталог с локальным репозиторием:

$ cd ~/dev/first-project

 и вводим команду:

$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git

Убеждаемся что они связаны:

$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)

Все готово. Осталось добавить файлы, сделать локальные снимки - коммиты, и топравить их в удаленный репозиторий. Для этого:

перейдем в наш локальный репозиторий
cd ~/GitPractice/
touch gitest.txt   создаем текстовый файл теста

теперь проверяем с помошью git что у нас есть в репозитории:
git status проверка файлов для добавления
git add gitest.txt добавление файла(ов) для отслеживания Гитом
git commit -m 'First commit(created gitest.txt file)'  Делаем снимок текущего состояния файла.

Теперь осталось отправить коммит на ГитХАБ
в Bash 
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master.
Все готово!!!
Теперь идентичные версии файла ддолжны быть как в локальном репозитории, так и в удаленном.
В локальном можно долго накапливать изменения, а потом запушить их в удаленный.





